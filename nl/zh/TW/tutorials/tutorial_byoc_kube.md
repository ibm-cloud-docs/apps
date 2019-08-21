---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-05"

keywords: apps, deploy, deploy to kubernetes, cluster, delivery pipeline, toolchain, kube, deployment, custom code, kubernetes

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 將您自己的程式碼部署至 Kubernetes 叢集
{: #tutorial-byoc-kube}

瞭解如何使用現有應用程式儲存庫，在 {{site.data.keyword.cloud}} 中建立應用程式。您可以連接現有的 DevOps 工具鏈或建立一個，並持續將應用程式遞送至 Kubernetes 叢集裡的安全容器。本指導教學協助您設定 Continuous Integration DevOps 管線，以自動建置變更，並傳播直到您在 Kubernetes 叢集裡部署的應用程式。
{: shortdesc}

當您已有的原始碼儲存庫具有工作中後端應用程式的程式碼庫時，{{site.data.keyword.cloud_notm}} 會協助您將此資產組織成對於整個產品所涵蓋之所有資產的聚集視圖。當您使用 DevOps 工具鏈特性時，{{site.data.keyword.cloud_notm}} 能讓您開始可擴充的 DevOps 工作流程。本指導教學協助經驗豐富的開發人員或 DevOps 工程師獲得並配置目標 {{site.data.keyword.containerlong}}，以及配置並執行 DevOps 工具鏈，一切都在雲端最佳作法的指引下進行。

_叢集_ 是一組資源、工作者節點、網路及儲存裝置，這些讓應用程式保持高可用性。建立叢集之後，您可以在容器中部署應用程式。
{: tip}

## 開始之前
{: #prereqs-byoc-kube}

* [從自己的程式碼儲存庫建立應用程式](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc)。
* 從 [{{site.data.keyword.cloud_notm}} 主控台 ](https://{DomainName}){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")，按一下**功能表**圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg)，然後選取**容器**以[配置 Kubernetes 叢集](/docs/containers?topic=containers-getting-started)。
* 確認應用程式在 Docker 中執行。下列指令是範例，不一定是您應用程式中存在的步驟：
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install`
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* 然後，移至您的 URL，例如 `http://localhost/springboothelloworld/sayhello`。按 Ctrl+C 以停止 Docker 執行。

## 將服務新增至應用程式（選用）
{: #resources-byoc-kube}

建立應用程式之後，您可以從**應用程式詳細資料**頁面，將服務新增至您的應用程式。{{site.data.keyword.cloud_notm}} 會為您建立服務實例。不同類型的服務，佈建處理程序可能不同。例如，資料庫服務會建立資料庫，而行動應用程式的推送通知服務則會產生配置資訊。{{site.data.keyword.cloud_notm}} 會使用服務實例，將服務資源提供給應用程式。服務實例可以在 Web 應用程式之間共用。

此處理程序會佈建服務實例、建立資源金鑰（認證），並將它連結至應用程式。如需相關資訊，請參閱[將服務新增至應用程式](/docs/apps?topic=creating-apps-add-resource)。

將服務新增至應用程式之後，您必須[將服務的認證複製到部署環境](/docs/apps?topic=creating-apps-credentials_overview)。

## 準備應用程式以進行部署
{: #deploy-byoc-kube}

在此步驟中，您將 DevOps 工具鏈連接至應用程式，並將它配置為部署至 {{site.data.keyword.containerlong}} 中管理的 Kubernetes 叢集。

DevOps 工具鏈有足夠的彈性，容許以受管理的方式執行 Shell Script 執行的任意階段。換言之，您幾乎可以使用 DevOps 工具鏈執行任何動作。本節的範圍著重於在 Kubernetes 叢集部署應用程式，同時謹記使擴充的 DevOps 及雲端最佳作法「不過時」。

建立應用程式、工具鏈與儲存庫之間的鏈結，是邁向組織產品資產的一步。它也有助於用 DevOps 工作流程、執行中的應用程式實例，以及跨所有部署目標的相依服務，聚集您原始碼儲存庫的視圖。

### 連接現有的 DevOps 工具鏈

如果您已經有 DevOps 工具鏈，請完成下列步驟：

1. 在**應用程式詳細資料**頁面上，按一下**配置持續交付**。即會顯示**部署應用程式**頁面。
2. 選取您要連接至應用程式的工具鏈，然後按一下**啟用部署**。即會顯示**應用程式詳細資料**頁面，這表示持續交付已配置。

如果您不想要從頭開始建立 DevOps 工具鏈，則可以使用 [`ibmcloud dev enable` 指令](/docs/cli/idt?topic=cloud-cli-idt-cli#enable)來啟用現有程式碼的雲端功能。這個指令會產生 DevOps 工具鏈範本，您可以將它移入至儲存庫。然後，您可以使用該範本作為 DevOps 工具鏈所建立項目的指示集。如需相關資訊，請參閱 [CLI 文件](/docs/apps?topic=creating-apps-create-deploy-app-cli#byoc-cli)。
{: tip}

### 建立 DevOps 工具鏈

如果您想要完全控制 DevOps 工具鏈的建立而不變更程式碼儲存庫，請從頭開始建立工具鏈。您也可以建立所有整合，以建置應用程式並將其部署至 Kubernetes 叢集。 

1. 在**應用程式詳細資料**頁面上，按一下**建立 DevOps 工具鏈**。即會顯示**建立工具鏈**頁面。
2. 選取**建置您自己的工具鏈**範本。
3. 在**建置您自己的工具鏈**頁面上，輸入工具鏈的名稱、選取地區和資源群組 (default)，然後按一下**建立**。
4. 在瀏覽器視窗中使用瀏覽途徑可回到**應用程式詳細資料**頁面，這表示持續交付已配置。
5. 在**應用程式詳細資料**頁面上，按一下**檢視工具鏈**，以配置新的 DevOps 工具鏈。

### 新增 GitHub 整合
{: #github-byoc-kube}

使用工具鏈 GitHub 儲存庫整合來配置 DevOps 工具鏈。這會在您的儲存庫中設定一個 Webhook，以便讓該儲存庫中的取回要求及程式碼推送傳送 POST 給工具鏈。

1. 在空的 DevOps 工具鏈範本中，按一下**新增工具**。
2. 選取 **GitHub**（如果儲存庫是在公用 GitHub 上，或在 Enterprise GitHub 上）。
3. 選取或輸入 GitHub 伺服器 URL。
4. 可能會顯示 `Unauthorized on GitHub` 訊息。如果是，請按一下**授權**。然後，在「授權 IBM Cloud 工具鏈」頁面上，按一下**授權 IBM-Cloud**，再輸入 GitHub 密碼。
5. 在「配置整合」頁面上，選取**現有**作為儲存庫類型，讓 DevOps 工具鏈可以使用 Webhook 來配置儲存庫，而不會分出 (fork) 或複製儲存庫。
6. 輸入儲存庫 URL，例如 `https://github.com/yourrepo/spring-boot-hello-world`。
7. 等待一下，系統可能會提示您授權 GitHub 以授與 DevOps 工具鏈許可權，以便使用 GitHub ReST API，以觸發工具鏈所需的 Webhook 來配置儲存庫。
8.  按一下**建立整合**。

您可以從儲存庫設定檢視新的 Webhook。

### 新增交付管線
{: #pipeline-byoc-kube}

1. 按一下**新增工具**。
2. 選取 **Delivery Pipeline**。
3. 輸入 `Continuous Integration` 作為管線名稱，然後按一下**建立整合**。

### 配置管線階段
{: #pipelineconfig-byoc-kube}

配置管線階段，將輸入（GitHub 儲存庫內容）引導至正確目的地。因為本指導教學假設您已有一個 GitHub 儲存庫，它會產生可運作的 Docker 映像檔，並將 {{site.data.keyword.containerlong}} 設為目標，所以您會建立管線階段，其中具有達成此目標的輸入、Shell Script 及輸出。

1. 配置 `build and publish` 管線階段。
  1. 選取您您建立的交付管線，然後按一下**新增階段**。
  2. 按一下**輸入**標籤，並完成欄位，如下所示：
    * 輸入 `build and publish Docker image` 作為階段名稱。
    * 選取 **Git 儲存庫**作為輸入類型。
    * 選取 GitHub 儲存庫。
    * 選取您用於持續整合的分支。
  3.  按一下**工作**標籤，然後按一下**新增工作 '+'**，並完成欄位，如下所示：
    * 選取**建置**作為工作類型。
    * 輸入 `build and publish` 作為名稱。
    * 選取 **Container Registry** 作為建置器類型。
    * 選取 Kubernetes 叢集所在的地區。
    * 選取**輸入現有 API 金鑰**。如果您沒有 API 金鑰，請參閱[建立 API 金鑰](/docs/iam?topic=iam-userapikey#create_user_key)。 
    * 輸入 Container Registry 名稱空間（按一下**功能表**圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg)，然後選取**容器** > **登錄** > **名稱空間**，即可找到它）。
    * 針對 Docker 映像檔名稱，輸入 `continuous`，因為此管線建置階段是用於持續建置儲存庫的持續整合分支。
    * 編輯建置 Script，在第一行 `#!/bin/bash` 之後，新增一行以上。例如，對於使用 maven 建置的儲存庫，您可能會新增幾行，類似下列範例：

      ```bash
      export JAVA_HOME=/opt/IBM/java8
      # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
      export MAVEN_OPTS="-  
      Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
      mvn -B clean verify
      ```
      {: codeblock}
  4. 按一下**儲存**。 
2. 按一下**播放**圖示，直到建置成功，藉此測試 `build and publish` 管線階段。綠色的階段指出建置成功。 
3. 配置 `deploy to cluster` 管線階段，以將 Docker 映像檔部署至 Kubernetes 叢集。 
  1. 在 Delivery Pipeline 頁面上，按一下**新增階段**。
  2. 按一下**輸入**標籤，並完成欄位，如下所示：
    * 輸入 `deploy to cluster` 作為名稱。
    * 選取**建置構件**作為輸入類型。
    * 選取 **Build & Publish Docker Image** 作為階段。
    * 選取 **Build & Publish** 作為工作。
    * 因為這是持續整合管線，所以請接受階段觸發程式的預設選項。
  3. 按一下**工作**標籤，然後按一下**新增工作 '+'**，並完成欄位，如下所示：
    * 輸入 `deploy to continuous integration cluster` 作為名稱。
    * 選取 **Kubernetes** 作為部署者類型。
    * 選取 Kubernetes 叢集所在的地區。
    * 輸入現有 API 金鑰。 
  4. 按一下**儲存**。
4. 按一下**播放**圖示，直到建置成功，藉此測試 `deploy to cluster` 管線階段。綠色的階段指出建置成功。

## 驗證應用程式正在執行
{: #verify-byoc-kube}

Delivery Pipeline 或指令行會將您指向應用程式的 URL。

1. 從 DevOps 工具鏈中，按一下 **Delivery Pipeline**，然後選取**部署階段**。
2. 按一下**檢視日誌和歷程**。
3. 在日誌檔中，尋找應用程式 URL。在日誌檔結尾，搜尋單字 `urls` 或 `view`。例如，您可能會看到日誌檔中有一行類似於 `urls: my-app-devhost.mybluemix.net`，或 `View the application health at: http://<ipaddress>:<port>/health`。
4. 在瀏覽器中移至 URL。如果應用程式正在執行，則會顯示包含 `Congratulations` 或 `{"status":"UP"}` 的訊息。

如果您使用指令行，請執行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 指令，在預設瀏覽器中開啟已手動部署之應用程式的頁面。

## 相關資訊

 * [建立工具鏈](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)
 * [配置 Git 儲存庫及問題追蹤](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#grit)
 * [配置 GitHub](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#github)
 * [配置 GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab)
