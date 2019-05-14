---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, mobile, mobile application, starter kit, developer tools, DevOps toolchain, toolchain, create mobile app, mobile starter kit

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 使用入門範本套件來建立行動應用程式
{: #tutorial-mobile}

{{site.data.keyword.cloud}} 提供行動入門範本套件，以協助您快速建立行動應用程式。請從「應用程式服務入門範本套件」中選取語言、架構及工具，以開始使用預先配置的自訂應用程式。在本指導教學中，您可以了解如何安裝所需的工具、在本端建置並執行應用程式，然後將它部署至雲端。
{: shortdesc}

## 步驟 1. 開始之前
{: #prereqs-mobile}

* 安裝 [{{site.data.keyword.dev_cli_short}}](/docs/cli?topic=cloud-cli-ibmcloud-cli)。
* Docker 會安裝為開發人員工具的一部分。Docker 必須在執行中，建置指令才能運作。您必須建立 Docker 帳戶、執行 Docker 應用程式，然後登入。
* 如果您計劃將應用程式部署至 [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about)，則必須[準備 {{site.data.keyword.cloud_notm}} 帳戶](/docs/cloud-foundry?topic=cloud-foundry-prepare)。

## 步驟 2. 使用 {{site.data.keyword.dev_console}} 建立應用程式
{: #create-mobile}

1. 在 {{site.data.keyword.cloud_notm}} 中建立 {{site.data.keyword.dev_console}} 應用程式。
2. 從 {{site.data.keyword.dev_console}} 的[入門範本套件 ](https://{DomainName}/developer/appservice/starter-kits/){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示") 頁面，根據您要的特性選取入門範本套件。例如，若為 Watson 語言應用程式，請選取 **Swift Kitura**。
3. 輸入應用程式名稱。針對本指導教學，請使用 `WatsonApp`。
4. 選用。提供標記以分類應用程式。如需相關資訊，請參閱[使用標籤](/docs/resources?topic=resources-tag)。
5. 選取語言平台。針對本指導教學，請使用 `Swift`。
6. 選取語言及架構。部分入門範本套件可能只提供一種語言。
7. 選取定價方案。有免費選項，您可以用於本指導教學。
8. 按一下**建立**。

## 步驟 3. 新增服務（選用）
{: #resources-mobile}

您可以新增服務，藉由 Watson 的認知能力加強您的應用程式，也可以新增行動服務或安全服務。針對本指導教學，請新增工作區以便管理您的資料。

1. 在**應用程式詳細資料**頁面上，按一下**新增服務**。
2. 選取您要的服務類型。例如，選取**資料** > **下一步** > **Cloudant** > **下一步**。
3. 選取定價方案。有免費選項，您可以用於本指導教學。
4. 按一下**建立**。

## 步驟 4. 建立 DevOps 工具鏈
{: #toolchain-mobile}

啟用工具鏈會為您的應用程式建立一個以團隊為基礎的開發環境。建立工具鏈時，應用程式服務會建立 Git 儲存庫，您可以在其中檢視原始碼、複製應用程式以及建立和管理問題。您也可以存取專用的 GitLab 環境，以及持續交付管線。它們是根據您所選取的部署目標（[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html) 或[虛擬伺服器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers)）進行自訂。

從「{{site.data.keyword.cloud_notm}} 開發人員」儀表板建立的所有工具鏈，都會針對自動部署進行配置。
{: note}

1. 在**應用程式詳細資料**頁面上，按一下**配置持續交付**。
2. 選取一個部署目標。根據您所選目標的指示設定部署目標：
  * **部署至 [IBM Kubernetes Service](/docs/apps/deploying?topic=creating-apps-containers-kube)**。此選項會建立主機（稱為工作者節點）的叢集，以部署及管理高可用性的應用程式容器。您可以建立叢集或部署至現有的叢集。
  * **部署至 Cloud Foundry**。此選項會部署雲端原生應用程式，而您不需要管理基本基礎架構。如果您的帳戶可以存取 {{site.data.keyword.cfee_full_notm}}，則可以選取**[公用雲端](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)**或**[企業環境](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**的部署人員類型，用來建立及管理用於管理專供您企業使用的 Cloud Foundry 應用程式的隔離環境。
  * **部署至[虛擬伺服器](/docs/apps?topic=creating-apps-vsi-deploy)**。此選項會佈建虛擬伺服器實例、載入包含您應用程式的映像檔、建立 DevOps 工具鏈，以及為您起始第一個部署週期。

如需部署應用程式的相關資訊，請參閱[部署應用程式](/docs/apps?topic=creating-apps-deploying-apps)。

## 步驟 5. 在本端建置及執行應用程式
{: #build-run-mobile}

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

7.  取得認證。

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

10.  使用瀏覽器開啟 `http://localhost:3000`。您的埠號可能會根據選擇的運行環境而不同。

### 在 Xcode 中執行 Swift 應用程式
{: #run_swift}

1. 在 Markdown 檢視器中開啟 `README.md` 檔案，以檢閱配置應用程式的步驟。
2. 開啟您的終端機並導覽至應用程式資料夾，然後執行下列指令：
    1. 如果您需要設定 CocoaPods 儲存庫，請執行 `pod setup`。
    2. 如果您需要更新現有的 Pod，請執行 `pod update`。
    3. 執行 `pod install` 來安裝應用程式的 Pod。
3. 開啟您的 `<appname>.xcworkspace` Xcode 工作區。
4. 執行應用程式。

### 在 Xcode 中執行 Cordova 應用程式
{: #run_cordova_xcode}

如果您選擇使用 Cordova 作為您的實作語言，請遵循這些指示。

1. 在 Markdown 檢視器中開啟 `README.md` 檔案，以配置應用程式。
2. 在 Xcode 中開啟 `platforms/ios` 應用程式。
3. 執行應用程式。

### 在 Android Studio 中執行 Cordova 應用程式
{: #run_cordova_studio}

如果您選擇使用 Cordova 作為行動應用程式的平台，請使用本小節。

1. 解壓縮 `BasicProject-Cordova.zip` 檔案。
2. 在 Markdown 檢視器中開啟 `README.md` 檔案，以配置應用程式。
3. 在 Android Studio 中開啟 `platforms/android` 應用程式。
4. 執行應用程式。

### 在 Android Studio 中執行 Android 應用程式
{: #run_android}

如果您選擇使用 Android 作為行動應用程式的平台，請使用本小節。

1. 在 Markdown 檢視器中開啟 `README.md` 檔案，以配置應用程式。
2. 在 Android Studio 中開啟 `BasicProject-Android` 應用程式。
3. 執行應用程式。

## 步驟 6. 部署應用程式
{: #deploy-mobile}

### 使用工具鏈進行部署
{: #deploy-mobile-toolchain}

您有數種方式可以將應用程式部署至 {{site.data.keyword.cloud_notm}}，但 DevOps 工具鏈是部署正式作業應用程式的最佳方法。使用 DevOps 工具鏈，您可以輕鬆地自動部署到許多環境，並快速新增監視、記載和警示服務，以協助您在應用程式成長時進行管理。

使用適當配置的工具鏈，會自動開始建置並部署的循環，並且全都合併到您儲存庫的主要分支。從 {{site.data.keyword.cloud_notm}} 開發人員儀表板建立的所有工具鏈都會針對自動部署進行配置。


您也可以從 DevOps 工具鏈手動部署應用程式：

1. 在**應用程式詳細資料**頁面上，按一下**檢視工具鏈**。

2. 按一下 **Delivery Pipeline**，您可以在其中啟動建置、管理部署，以及檢視日誌和歷程。

### 使用 {{site.data.keyword.dev_cli_short}} 進行部署
{: #deploy-mobile-cli}

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

## 步驟 7. 驗證應用程式在執行中
{: #verify-mobile}

部署應用程式之後，Delivery Pipeline 或指令行會將您指向應用程式的 URL。

1. 從 DevOps 工具鏈中，按一下 **Delivery Pipeline**，然後選取**部署階段**。
2. 按一下**檢視日誌和歷程**。
3. 在日誌檔中，尋找應用程式 URL：

    在日誌檔結尾，搜尋單字 `urls` 或 `view`。例如，您可能會看到日誌檔中有一行類似於 `urls: my-app-devhost.mybluemix.net`，或 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在瀏覽器中移至 URL。如果應用程式正在執行，則會顯示包含 `Congratulations` 或 `{"status":"UP"}` 的訊息。

如果您要使用指令行，請執行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 指令來檢視應用程式的 URL。然後，在瀏覽器中移至 URL。
