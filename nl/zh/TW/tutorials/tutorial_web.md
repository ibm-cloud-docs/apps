---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-30"

keywords: basic web app tutorial, apps, web app, starter kit, App Service, developer tools, DevOps toolchain, basic app, create basic web app

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用入門範本套件來建立基本 Web 應用程式
{: #tutorial-webapp}

{{site.data.keyword.cloud}} 提供許多入門範本套件來協助您快速撰寫程式碼。請從「應用程式服務入門範本套件」中選取語言、架構及工具，以開始使用預先配置的自訂應用程式。在本指導教學中，您會逐步了解安裝所需的工具、在本端建置並執行應用程式，然後將它部署至雲端的步驟。
{: shortdesc}

## 步驟 1. 安裝工具
{: #prereqs-webapp}

安裝[開發人員工具](/docs/cli?topic=cloud-cli-ibmcloud-cli)。

Docker 會安裝為開發人員工具的一部分。Docker 必須在執行中，建置指令才能運作。您必須建立 Docker 帳戶、執行 Docker 應用程式，然後登入。

## 步驟 2. 選取入門範本套件
{: #create-webapp}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}} 中的入門範本套件有許多語言及架構。請選取最適合您專案的語言來著手。

1. 從 {{site.data.keyword.dev_console}} 的[入門範本套件 ](https://{DomainName}/developer/appservice/starter-kits/){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示") 頁面，選取您語言的入門範本套件。
2. 選用。提供標記以分類應用程式。如需相關資訊，請參閱[使用標籤](/docs/resources?topic=resources-tag)。
3. 選取語言及架構。部分入門範本套件可能只提供一種語言。
4. 選取定價方案。有免費選項，您可以用於本指導教學。
5. 按一下**建立**。

## 步驟 3. 新增服務（選用）
{: #resources-webapp}

您可以新增服務，藉由 Watson 的認知能力加強您的應用程式，也可以新增行動服務或安全服務。針對本指導教學，請新增工作區以便管理您的資料。

1. 在**應用程式詳細資料**頁面上，按一下**新增服務**。
2. 選取您要的服務類型。例如，選取**資料** > **下一步** > **Cloudant** > **下一步**。
3. 選取定價方案。有免費選項，您可以用於本指導教學。
4. 按一下**建立**。

## 步驟 4. 建立 DevOps 工具鏈
{: #toolchain-webapp}

啟用工具鏈會為您的應用程式建立一個以團隊為基礎的開發環境。建立工具鏈時，應用程式服務會建立 Git 儲存庫，您可以在其中檢視原始碼、複製應用程式以及建立和管理問題。您也可以存取專用的 GitLab 環境，以及持續交付管線。它們是根據您所選取的部署目標（[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虛擬伺服器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers)）進行自訂。

已針對部分應用程式啟用持續交付。您可以啟用持續交付，以透過 Delivery Pipeline 及 GitHub 自動建置、測試及部署。

按一下**應用程式詳細資料**頁面上的**配置持續交付**，選取部署目標，然後按一下**建立**。{{site.data.keyword.cloud_notm}} 會自動建立開放式工具鏈，此工具鏈會完整地具備 Git 儲存庫及持續交付管線。

在選取部署目標之後，請開啟新工具鏈的管線元件，以開始起始建置和部署處理程序，讓您可以在幾分鐘內看到新的應用程式。

如需相關資訊，請參閱[建立工具鏈](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)。

## 步驟 5. 在本端建置及執行應用程式
{: #build-run-webapp}

在前一個步驟中將應用程式部署至雲端時，已經建立了工具鏈。工具鏈會為您的應用程式建立 Git 儲存庫，您可以在該處找到程式碼。請遵循下列步驟來存取您的儲存庫。您可以在本端建置應用程式以進行測試，然後才將它推送至雲端。

1. 在**應用程式詳細資料**頁面上，按一下**下載程式碼**或**複製儲存庫**，以在本端使用程式碼。
2. 將應用程式匯入至整合開發環境。
3. 修改程式碼。
4. 新增個人存取記號來設定 [Git 鑑別](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication)。
5. 登入 {{site.data.keyword.cloud_notm}} 指令行介面。如果您的組織使用聯合登入，請使用 `-sso` 選項。

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. 設定您的組織及空間目標。

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. 取得認證。

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. 確定 Docker 在執行中，然後在本端開發容器中從目錄建置應用程式。

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. 在本端開發容器中執行應用程式。

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. 使用瀏覽器開啟 `http://localhost:3000`。您的埠號可能會根據選擇的運行環境而不同。

## 步驟 6. 部署應用程式
{: #deploy-webapp}

### 使用工具鏈進行部署
{: #deploy-webapp-toolchain}

您有數種方式可以將應用程式部署至 {{site.data.keyword.cloud_notm}}，但 DevOps 工具鏈是部署正式作業應用程式的最佳方法。使用 DevOps 工具鏈，您可以輕鬆地自動部署到許多環境，並快速新增監視、記載和警示服務，以協助您在應用程式成長時進行管理。

使用適當配置的工具鏈，建置-部署的循環會自動開始，並且全都合併到您儲存庫的主要分支。從 {{site.data.keyword.cloud_notm}} 開發人員儀表板建立的所有工具鏈都會針對自動部署進行配置。


您也可以從 DevOps 工具鏈手動部署應用程式：

1. 在**應用程式詳細資料**頁面上，按一下**檢視工具鏈**。
2. 按一下 **Delivery Pipeline**，您可以在其中啟動建置、管理部署，以及檢視日誌和歷程。

如需相關資訊，請參閱[建置並部署](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)。

### 使用 {{site.data.keyword.dev_cli_short}} 進行部署
{: #deploy-webapp-cli}

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

如需部署應用程式的相關資訊，請參閱[部署應用程式](/docs/apps?topic=creating-apps-deploying-apps)。

## 步驟 7. 驗證應用程式在執行中
{: #verify-webapp}

部署應用程式之後，Delivery Pipeline 或指令行會將您指向應用程式的 URL。

1. 從 DevOps 工具鏈中，按一下 **Delivery Pipeline**，然後選取**部署階段**。
2. 按一下**檢視日誌和歷程**。
3. 在日誌檔中，尋找應用程式 URL：

    在日誌檔結尾，搜尋單字 `urls` 或 `view`。例如，您可能會看到日誌檔中有一行類似於 `urls: my-app-devhost.mybluemix.net`，或 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在瀏覽器中移至 URL。如果應用程式正在執行，則會顯示包含 `Congratulations` 或 `{"status":"UP"}` 的訊息。

如果您要使用指令行，請執行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 指令來檢視應用程式的 URL。然後，在瀏覽器中移至 URL。
