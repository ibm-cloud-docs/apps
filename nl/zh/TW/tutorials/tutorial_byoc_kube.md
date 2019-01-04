---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 將您自己的程式碼部署至 Kubernetes 叢集
{: #tutorial}

了解如何使用現有的應用程式儲存庫，在 {{site.data.keyword.cloud}} 中建立應用程式。您可以連接現有的 DevOps 工具鏈或建立一個，並持續將應用程式遞送至 Kubernetes 叢集裡的安全容器。本指導教學協助您設定 Continuous Integration DevOps 管線，以自動建置變更，並傳播直到您在 Kubernetes 叢集裡部署的應用程式。
{: shortdesc}

當您已有的原始碼儲存庫具有工作中後端應用程式的程式碼庫時，{{site.data.keyword.cloud_notm}} 會協助您將此資產組織成對於整個產品所涵蓋之所有資產的聚集視圖。當您使用 DevOps 工具鏈特性時，{{site.data.keyword.cloud_notm}} 能讓您開始可擴充的 DevOps 工作流程。本指導教學協助經驗豐富的開發人員或 DevOps 工程師獲得並配置目標 {{site.data.keyword.cloud_notm}} Kubernetes 叢集，以及配置並執行 DevOps 工具鏈，一切都在雲端最佳作法的指引下進行。

_叢集_ 是一組資源、工作者節點、網路及儲存裝置，這些讓應用程式保持高可用性。建立叢集之後，您可以在容器中部署應用程式。
{: tip}

## 開始之前
{: #prereqs}

* 遵循[從您自己的程式碼儲存庫建立應用程式](/docs/apps/tutorials/tutorial_byoc.html)中的步驟來建立應用程式。
* 從 [{{site.data.keyword.cloud_notm}} 儀表板 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}){: new_window}，按一下**功能表**圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg)，然後選取**容器**以[配置 Kubernetes 叢集](/docs/containers/container_index.html)。
* 若要確認應用程式在 Docker 中執行，請執行下列指令：
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install`
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* 然後，造訪您的 URL，例如 `http://localhost/springboothelloworld/sayhello`。   
按 `Ctrl+C`，以停止 Docker 執行。

## 選用。將資源新增至應用程式
{: #add_resources}

將服務資源新增至應用程式，而 {{site.data.keyword.cloud_notm}} 會為您建立服務。不同類型的服務，佈建處理程序可能不同。例如，資料庫服務會建立資料庫，而行動應用程式的推送通知服務則會產生配置資訊。
{{site.data.keyword.cloud_notm}} 會透過使用服務實例，將服務資源提供給應用程式。服務實例可以在 Web 應用程式之間共用。

此處理程序會佈建服務實例、建立資源金鑰（認證），並將它連結至應用程式。如需相關資訊，請參閱[將服務新增至應用程式](/docs/apps/reqnsi.html)。

### 將服務認證複製到環境

將服務資源新增至應用程式之後，請注意，該服務的認證會顯示在**認證**方框中。您必須將認證複製到部署環境。

如需將認證複製到環境的相關資訊，請參閱[將認證新增至 Kubernetes 環境](/docs/apps/creds_kube.html)。


## 使用 DevOps 工具鏈準備應用程式以進行部署
{: #connect_toolchain}

在此步驟中，您將 DevOps 工具鏈連接至應用程式，並將它配置為部署至 {{site.data.keyword.cloud_notm}} Kubernetes 服務中管理的 Kubernetes 叢集。

DevOps 工具鏈有足夠的彈性，容許以受管理的方式執行 Shell Script 執行的任意階段。換言之，您幾乎可以使用 DevOps 工具鏈執行任何動作。本節的範圍著重於在 Kubernetes 叢集部署應用程式，同時謹記使擴充的 DevOps 及雲端最佳作法「不過時」。

建立應用程式、工具鏈與儲存庫之間的鏈結，是邁向組織產品資產的一步。它也有助於用 DevOps 工作流程、執行中的應用程式實例，以及跨所有部署目標的相依服務，聚集您原始碼儲存庫的視圖。

在「連接工具鏈」頁面中，您有幾個選項：

* 將應用程式連接至現有工具鏈。
* 將應用程式連接至不包含儲存庫的現有工具鏈。稍後，再將工具鏈連接至儲存庫。
* 將應用程式連接至新的工具鏈。

### 將應用程式連接至現有工具鏈
{: #connect_toolchain_repo}

如果您有一個以上的 DevOps 工具鏈已連接至應用程式建立期間指定的 Git 儲存庫，這些工具鏈會顯示在**具有儲存庫**表格中。工具鏈必須配置為從您在應用程式中定義的相同儲存庫中擷取原始檔。您很可能想要選取其中一個工具鏈來連接至應用程式。

### 將應用程式連接至不包含儲存庫的現有工具鏈
{: #connect_toolchain_notrepo}

如果您有一個以上與帳戶相關聯的 DevOps 工具鏈，但它們未連接至您在應用程式建立期間指定的 Git 儲存庫，則那些工具鏈會顯示在標示**沒有儲存庫**的表格中。您可以選取其中一個工具鏈並將其連接至應用程式，但也必須手動將儲存庫新增至該工具鏈。

如需將儲存庫新增至工具鏈的相關資訊，請參閱：

 * [配置 Git 儲存庫及問題追蹤](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitbluemix)
 * [配置 GitHub](/docs/services/ContinuousDelivery/toolchains_integrations.html#github)
 * [配置 GitLab](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitlab)


### 將應用程式連接至新的工具鏈
{: #create_toolchain}

您可以使用以下選項將應用程式連接至新的工具鏈：
* 如果您不想要從頭開始建立 DevOps 工具鏈，則可以使用 [`ibmcloud dev enable` 指令](/docs/cli/idt/commands.html#enable)來啟用現有程式碼的雲端功能。這個指令會產生 DevOps 工具鏈範本，您可以將它移入至儲存庫。然後，您可以使用該範本作為 DevOps 工具鏈所建立項目的指示集。如需相關資訊，請參閱 [CLI 文件](/docs/apps/create-deploy-cli.html#byoc)。
* 在主控台內，從頭開始建立 DevOps 工具鏈。如果您想要完全控制 DevOps 工具鏈的建立而不變更程式碼儲存庫，請從頭開始建立工具鏈。如需相關資訊，請參閱[從頭開始建立 DevOps 工具鏈](#create_toolchain_scratch)。

#### 從頭開始建立 DevOps 工具鏈
{: #create_toolchain_scratch}

如果您想要從頭開始建立工具鏈，並將其連接至應用程式，請完成下列步驟。您也可以建立所有整合，以建置應用程式並將其部署至 Kubernetes 叢集。DevOps 工具鏈特性會提供範本，但這些步驟顯示如何從頭開始設定 DevOps 工具鏈。

當您選擇從新的應用程式建立工具鏈時，[DevOps 儀表板](https://{DomainName}/devops/)中的[建立工具鏈](https://{DomainName}/devops/create)頁面會在瀏覽器的新標籤中開啟。在該標籤中建立並配置工具鏈之後，您必須回到應用程式中的**連接工具鏈**頁面，然後重新整理頁面。
{:tip}

1. 在**建立工具鏈**頁面上，按一下**建置您自己的工具鏈**範本。
2. 在**建置您自己的工具鏈**頁面上，輸入工具鏈的名稱、選取地區和資源群組 (default)，然後按一下**建立**。

即會建立沒有預先配置工具或整合的空工具鏈。完成剩餘步驟來繼續配置並測試新的工具鏈。

## 新增 GitHub 整合

您可以使用下列步驟，以 GitHub 整合配置 DevOps 工具鏈：

1. 在 DevOps 工具鏈範本中，按一下**新增工具**。
2. 選取 **GitHub**（如果儲存庫的確是在公用 GitHub 上，或在 Enterprise GitHub 上）。
3. 在 GitHub 的**配置整合**頁面上，完成下列步驟：
  * 選取（或輸入）**GitHub 伺服器** URL。
  * 如果您看到「在 GitHub 上未獲授權」的訊息，請按一下**授權**。然後，在**授權 IBM Cloud 工具鏈**上，按一下**授權 IBM-Cloud**。然後，輸入 GitHub 密碼。
  * 在**配置整合**頁面上，選取**現有**作為**儲存庫類型**，讓 DevOps 工具鏈可以使用 Webhook 來配置儲存庫，而_不會_ 分出 (fork) 或複製儲存庫。
  * 輸入**儲存庫 URL**。（例如，`https://github.com/yourrepo/spring-boot-hello-world`。）
  * 等待一下，系統可能會提示您授權 GitHub 以授與 DevOps 工具鏈許可權，以便使用 GitHub ReST API，以觸發工具鏈所需的 Webhook 來配置儲存庫。
  * 按一下**建立整合**。

您已用 GitHub 儲存庫的整合來配置此 DevOps 工具鏈。這樣做可讓工具鏈在您的儲存庫中設定一個 Webhook，如此該儲存庫中的取回要求及程式碼推送便可對工具鏈觸發 POST。您可以查看儲存庫的設定，即可看見新的 Webhook。

## 新增 Delivery Pipeline 以建置、測試及部署應用程式

Delivery Pipeline 是工作發生的位置。

1. 按一下**新增工具**。
2. 選取 **Delivery Pipeline**。
3. 在 Delivery Pipeline 的**配置整合**頁面上，完成下列步驟：
 * 輸入 "Continuous Integration" 作為管線名稱。
 * 按一下**建立整合**。

您已建立空的 Delivery Pipeline。接下來，您可以定義管線階段，將輸入（GitHub 儲存庫內容）引導至其目的地。因為本指導教學假設您已有一個 GitHub 儲存庫，它會產生可運作的 Docker 映像檔，並將 IBM Containers Kubernetes 叢集設為目標，所以您會建立管線階段，其中具有達成此目標的輸入、Shell Script 及輸出。

### 配置「建置並發佈」管線階段

1. 按一下您所建立的 Delivery Pipeline。
2. 在 Delivery Pipeline 頁面上，按一下**新增階段**。
3. 在**階段配置**頁面的**輸入**標籤上完成欄位，如下所示：
  * 對於階段名稱，鍵入 **Build & Publish Docker Image**。
  * **輸入類型**：選取 **Git 儲存庫**。
  * **Git 儲存庫**：選取 GitHub 儲存庫。
  * **分支**：選取您用於 Continuous Integration 的分支。
4. 按一下**工作**標籤，並完成欄位，如下所示：
  * 按一下**新增工作 '+'** 圖示，然後選取**建置**作為工作類型。
  * 輸入名稱，例如 **Build & Publish**。
  * **建置器類型**：選取 **Container Registry**。
  * **IBM Cloud 地區**：選取 Kubernetes 叢集所在的地區。
  * **API 金鑰**：選取**輸入現有 API 金鑰**。如果您沒有金鑰或不知道您的 API 金鑰，則可以開啟個別瀏覽器視窗，並導覽至**管理** > **安全** > **平台 API 金鑰**，以[取得 API 金鑰](https://{DomainName}/iam/#/apikeys)。請務必將此金鑰保存在安全的地方。
  * **帳戶名稱**：當您輸入 API 金鑰時，這個欄位會自動完成。
  * **Container Registry 名稱空間**：輸入 [Container Registry 名稱空間](https://{DomainName}/containers-kubernetes/registry/namespaces)（按一下**功能表**圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg)，然後選取**容器** > **登錄** > **名稱空間**，即可找到它）。
  * **Docker 映像檔名稱**：輸入 **continuous**，因為此管線建置階段是用於持續建置儲存庫的 Continuous Integration 分支。
  * **建置 Script**：請注意 Shell Script。它缺少_您的_ 儲存庫的應用程式建置指示。您需要在第一行 `#!/bin/bash` 之後，新增一行以上。例如，對於使用 maven 建置的儲存庫，您可能會新增幾行，類似下列範例：

    ```bash
    export JAVA_HOME=/opt/IBM/java8
    # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
    export MAVEN_OPTS="-Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
    mvn -B clean verify
    ```
    {: codeblock}
5. 按一下**儲存**。您的「建置並發佈」管線階段現在會出現在工具鏈中。

### 測試「建置並發佈」管線階段

按一下**播放**圖示，直到建置成功。當階段變成綠色時，您便知道它可以運作，而 Script 輸出會確認您的預期。此階段中的目標是將 Docker 映像檔發佈至映像檔登錄。如果此 Script 不足以讓您放心，您可以按一下**功能表**圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg)，然後選取**容器** > **登錄** > **專用儲存庫**，來查看映像檔登錄以確認發佈。然後，確認列出結尾為名稱 `/continuous` 的儲存庫。（記住，這先前是映像檔名稱。）

### 配置「部署至叢集」管線階段

到目前為止，您已將 Docker 映像檔發佈至專用 Docker 映像檔登錄。現在是時候建立一個階段，將該映像檔部署至 Kubernetes 叢集了。

1. 在 Delivery Pipeline 頁面上，按一下**新增階段**。
2. 在**階段配置**頁面的**輸入**標籤上，完成欄位，如下所示：
  * **名稱**：鍵入 **Deploy**。
  * **輸入類型**：選取**建置構件**。
  * **階段**：選取 **Build & Publish Docker Image**。
  * **工作**：選取 **Build & Publish**。
  * **階段觸發程式**：因為這是 Continuous Integration 管線，所以選取預設值，即**執行工作，然後完成前一個階段**。
3. 按一下**工作**標籤，並完成欄位，如下所示：
  * 按一下**新增工作 '+'** 圖示，然後選取**部署**作為工作類型。
  * 輸入名稱，例如 **Deploy to Continuous Integration Cluster**。
  * **部署器類型**：選取 **Kubernetes**。
  * **IBM Cloud 地區**：選取 Kubernetes 叢集所在的地區。
  * **API 金鑰**：選取**輸入現有 API 金鑰**。如果您沒有金鑰或不知道您的 API 金鑰，則可以開啟個別瀏覽器視窗，並導覽至**管理** > **安全** > **平台 API 金鑰**，以[取得 API 金鑰](https://{DomainName}/iam/#/apikeys)。請務必將此金鑰保存在安全的地方。
  * 接受其餘的預設值。
4. 按一下**儲存**。您的「部署」管線階段現在會出現在工具鏈中。

### 測試「部署至叢集」管線階段

按一下**播放**圖示，直到建置成功。當階段變成綠色時，您便知道它可以運作，而 Script 輸出會確認您的預期。您可以檢視階段的日誌。在日誌尾端附近，尋找一個可按一下的鏈結，以連接至執行中的應用程式。不過，只有_您_ 知道應用程式的環境定義根目錄及路徑。請附加正確的路徑，以確認它在執行中。
