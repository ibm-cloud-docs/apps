---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-30"

keywords: scratch, developer tools, custom app, app tutorial, verify app running, run app local

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
3. 您可以選擇性地提供標記來分類應用程式。如需相關資訊，請參閱[使用標籤](/docs/resources?topic=resources-tag)。
4. 選取語言及架構。部分入門範本套件可能只提供一種語言。
5. 選取定價方案。您可以針對本指導教學使用免費選項。
6. 按一下**建立**。

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

按一下**應用程式詳細資料**頁面上的**配置持續交付**，選取部署目標，然後按一下**建立**。{{site.data.keyword.cloud_notm}} 會自動建立開放式工具鏈，此工具鏈會完整地具備 Git 儲存庫及持續交付管線。

啟用工具鏈會為您的應用程式建立一個以團隊為基礎的開發環境。建立工具鏈時，應用程式服務會建立 Git 儲存庫，您可以在其中檢視原始碼、複製應用程式以及建立和管理問題。您也可以存取專用的 GitLab 環境，以及持續交付管線。它們是根據您所選取的部署目標（[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虛擬伺服器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers)）進行自訂。

在選取部署目標之後，請開啟新工具鏈的管線元件，以開始起始建置和部署處理程序，讓您可以在幾分鐘內看到新的應用程式。

從「{{site.data.keyword.cloud_notm}} 開發人員」儀表板建立的所有工具鏈，都會針對自動部署進行配置。
{: note}

若要使用指令行來部署應用程式，請使用 `ibmcloud dev deploy`。如需相關資訊，請參閱[使用 CLI 建立及部署應用程式](/docs/apps?topic=creating-apps-create-deploy-app-cli)。

如需部署應用程式的相關資訊，請參閱[部署應用程式](/docs/apps?topic=creating-apps-deploying-apps)。

## 驗證應用程式正在執行
{: #verify-scratch}

部署應用程式之後，Delivery Pipeline 或指令行會將您指向應用程式的 URL。

1. 從 DevOps 工具鏈中，按一下 **Delivery Pipeline**，然後選取**部署階段**。
2. 按一下**檢視日誌和歷程**。
3. 在日誌檔中，尋找應用程式 URL：

   在日誌檔結尾，搜尋單字 `urls` 或 `view`。例如，您可能會看到日誌檔中有一行類似於 `urls: my-app-devhost.mybluemix.net`，或 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在瀏覽器中移至 URL。如果應用程式正在執行，則會顯示包含 `Congratulations` 或 `{"status":"UP"}` 的訊息。

如果您要使用指令行，請執行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 指令來檢視應用程式的 URL。然後，在瀏覽器中移至 URL。

