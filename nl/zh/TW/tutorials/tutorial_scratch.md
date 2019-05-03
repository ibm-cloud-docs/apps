---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-15"

keywords: apps, scratch, developer tools

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# 從頭開始建立應用程式
{: #tutorial-scratch}

您可以使用服務及運行環境，來從頭開始建立自訂應用程式。
{: shortdesc}

## 開始之前
{: #prereqs-scratch}

* 安裝 [{{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli)，其中包括 Docker。 
* 建立 Docker 帳戶，並執行 Docker 應用程式，然後登入。Docker 必須在執行中，建置指令才能運作。
* 如果您計劃將應用程式部署至 {{site.data.keyword.cfee_full}}，則必須[準備 {{site.data.keyword.cloud_notm}} 帳戶](/docs/cloud-foundry?topic=cloud-foundry-prepare)。

## 建立應用程式
{: #create-scratch}

1. 從 [{{site.data.keyword.cloud_notm}} 儀表板 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}) 中，按一下「應用程式」小組件中的**建立應用程式**。

  您也可以從 {{site.data.keyword.dev_console}} 的[入門範本套件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/appservice/starter-kits/) 頁面中，建立自訂應用程式。
  {: tip}

2. 輸入應用程式的名稱。針對本指導教學，請鍵入 `CustomProject`。
3. 輸入唯一的主機名稱，例如 `abc-devhost`。主機名稱用於應用程式的路徑，例如，`abc-devhost.mybluemix.net`。
4. 您可以選擇性地提供標記來分類應用程式。如需相關資訊，請參閱[使用標籤](/docs/resources?topic=resources-tag)。
5. 選取語言及架構。部分入門範本套件可能只提供一種語言。
6. 選取定價方案。您可以針對本指導教學使用免費選項。
7. 按一下**建立**。

預設共用網域是 `mybluemix.net`，而 `appdomain.cloud` 是您可以使用的另一個網域選項。如需移轉至 `appdomain.cloud` 的相關資訊，請參閱[更新網域](/docs/apps/tutorials?topic=creating-apps-update-domain)。
{: tip}

## 新增服務（選用）
{: #resources-scratch}

您可以新增服務，藉由 Watson 的認知能力加強您的應用程式，也可以新增行動服務或安全服務。針對本指導教學，您可以新增工作區以便管理您的資料。

1. 在**應用程式詳細資料**頁面上，按一下**新增服務**。
2. 選取您要的服務類型。例如，選取**資料** > **下一步** > **Cloudant** > **下一步**。
3. 選取定價方案。您可以針對本指導教學使用免費選項。
4. 按一下**建立**。

## 在本端建置及執行應用程式
{: #build-run-scratch}

您也可以先在本端建置應用程式以進行測試，再將它部署至雲端。

1. 在**應用程式詳細資料**頁面上，按一下**下載程式碼**或**複製儲存庫**，以在本端使用程式碼。
2. 將應用程式匯入至整合開發環境。
3. 修改程式碼。
4. 新增個人存取記號來設定 [Git 鑑別](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication)。
5. 登入 {{site.data.keyword.cloud_notm}} 指令行介面 (CLI)。如果您的組織使用聯合登入，請使用 `-sso` 選項；例如：

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. 執行下列指令，以設定您的組織及空間目標。

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. 執行下列指令，以擷取認證。

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. 確定 Docker 正在執行，並執行下列指令，以在本端開發容器中從目錄建置應用程式。

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. 執行下列指令，以在本端開發容器中執行應用程式。

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. 在瀏覽器中移至 `http://localhost:3000`。您的埠號可能會根據選擇的運行環境而不同。

## 部署應用程式
{: #deploy-scratch}

您有數種方式可以將應用程式部署至 {{site.data.keyword.cloud_notm}}，但 DevOps 工具鏈是部署正式作業應用程式的最佳方法。使用 DevOps 工具鏈，您可以輕鬆地自動部署到許多環境，並快速新增監視、記載和警示服務，以協助您在應用程式成長時進行管理。

啟用工具鏈會為您的應用程式建立一個以團隊為基礎的開發環境。建立工具鏈時，應用程式服務會建立 Git 儲存庫，您可以在其中檢視原始碼、複製應用程式以及建立和管理問題。您也可以存取專用的 GitLab 環境，以及持續交付管線。它們針對您所選擇的部署環境（[Kubernetes](/docs/containers?topic=containers-container_index)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虛擬伺服器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers)）經過自訂。

從「{{site.data.keyword.cloud_notm}} 開發人員」儀表板建立的所有工具鏈，都會針對自動部署進行配置。
{: note}

### 使用 DevOps 工具鏈進行手動部署

使用適當配置的工具鏈，會自動開始建置並部署的循環，並且全都合併到您儲存庫的主要分支。 

您也可以從 DevOps 工具鏈手動部署應用程式：

1. 在「應用程式詳細資料」頁面上按一下**檢視工具鏈**。
2. 按一下 **Delivery Pipeline**，您可以在其中啟動建置、管理部署，以及檢視日誌和歷程。

已針對部分應用程式啟用持續交付。您可以啟用持續交付，以透過 Delivery Pipeline 及 GitHub 自動建置、測試及部署。

如需相關資訊，請參閱：
* [使用 Continuous Delivery 進行建置及部署](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)。
* [從範本建立工具鏈](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)。

### 使用 DevOps 工具鏈進行自動部署

1. 在**應用程式詳細資料**頁面上，按一下**配置持續交付**。
2. 選取一個部署目標。根據您所選目標的指示設定部署目標：
  * **部署至 IBM Kubernetes Service**。此選項會建立主機（稱為工作者節點）的叢集，以部署及管理高可用性的應用程式容器。您可以建立叢集或部署至現有的叢集。
  * **部署至 Cloud Foundry**。此選項會部署雲端原生應用程式，而您不需要管理基本基礎架構。如果您的帳戶可以存取 {{site.data.keyword.cfee_full_notm}}，則可以選取**公用雲端**或**企業環境**的部署人員類型，用來建立及管理用於管理專供您企業使用的 Cloud Foundry 應用程式的隔離環境。
  * **部署至虛擬伺服器**。此選項會佈建虛擬伺服器實例、載入包含您應用程式的映像檔、建立 DevOps 工具鏈，以及為您起始第一個部署週期。

在前一個步驟中將應用程式部署至雲端時，會自動建立工具鏈。此工具鏈會為您的應用程式建立 Git 儲存庫，您可以在其中尋找程式碼。 

### 使用 {{site.data.keyword.dev_cli_short}} 進行部署
{: #deploy-scratch-cli}

若要將應用程式部署至 Cloud Foundry，請輸入下列指令：
```
ibmcloud dev deploy
```
{: pre}

若要將應用程式部署至 Kubernetes 叢集，請輸入下列指令：
```
ibmcloud dev deploy --target <container>
```
{: pre}

## 驗證應用程式正在執行
{: #verify-scratch}

部署應用程式之後，Delivery Pipeline 或指令行會將您指向應用程式的 URL。

1. 從 DevOps 工具鏈中，按一下 **Delivery Pipeline**，然後選取**部署階段**。
2. 按一下**檢視日誌和歷程**。
3. 在日誌檔中，尋找應用程式 URL：

    在日誌檔結尾，搜尋單字 `urls` 或 `view`。例如，您可能會看到日誌檔中有一行類似於 `urls: my-app-devhost.mybluemix.net` 或 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在瀏覽器中移至 URL。如果應用程式正在執行，則會顯示包含 `Congratulations` 或 `{"status":"UP"}` 的訊息。

如果您要使用指令行，請執行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 指令來檢視應用程式的 URL。然後，在瀏覽器中移至 URL。
