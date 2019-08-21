---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-17"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# 使用入門範本套件建立應用程式
{: #tutorial-starterkit}

您可以使用入門範本套件，快速讓您的應用程式啟動，並準備它以便未來進行開發。選取入門範本套件和程式設計語言、建立應用程式，然後設定 DevOps 工具鏈，以自動部署應用程式。
{: shortdesc}

您可以從一群精選的入門範本套件建立應用程式，這其中包括基本入門範本套件（如果您想要自己自訂建置選項的話）。無論哪一種方法，都會自動建立 DevOps 工具鏈來部署應用程式。您也可以下載程式碼以便立即進行檢驗。

{{site.data.keyword.cloud_notm}} 有不同興趣領域（例如 Watson）或數位頻道（例如行動或 Web 應用程式）的開發人員入口網站。您可以從**功能表**圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) 存取這些入口網站。

每個開發人員入口網站都提供與該入口網站焦點區域相關的入門範本套件。入口網站提供一致的直覺式工作流程，以在幾分鐘內建立一個工作中的可正式作業應用程式。

入門範本套件有許多種類，其中包括：
* [Watson ](https://{DomainName}/developer/watson/dashboard){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")
* [Apple ](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")
* [行動 ](https://{DomainName}/developer/mobile/dashboard){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")
* [Web 應用程式 ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")

如需相關資訊，請參閱[何謂入門範本套件？](/docs/apps?topic=creating-apps-starter-kits)。

## 步驟 1. 安裝工具
{: #prereqs-starterkit}

* 安裝[開發人員工具](/docs/cli?topic=cloud-cli-getting-started)。
* Docker 會安裝為開發人員工具的一部分。Docker 必須在執行中，建置指令才能運作。您必須建立 Docker 帳戶、執行 Docker 應用程式，然後登入。
* 如果您計劃將應用程式部署至 {{site.data.keyword.cfee_full}}，則必須[準備 {{site.data.keyword.cloud_notm}} 帳戶](/docs/cloud-foundry?topic=cloud-foundry-prepare)。

## 步驟 2. 建立應用程式
{: #create-starterkit}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}} 中的入門範本套件有許多語言及架構。您可以使用語言及類型這類種類過濾器，以縮小選取範圍。

1. 從 {{site.data.keyword.dev_console}} 主控台的[入門範本套件](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示") 頁面中，選取入門範本套件，然後按一下**建立應用程式**。 

    若要查看入門範本套件中所包含的內容，請選取磚，並閱讀詳細資料。如果您要使用基本入門範本套件，並自訂您的應用程式，請選取**建立應用程式**磚。
    {: tip}

2. 命名應用程式，並選取資源群組。

3. 選用。提供標記以分類應用程式。如需相關資訊，請參閱[使用標籤](/docs/resources?topic=resources-tag)。

4. 選取語言及架構。部分入門範本套件可能只提供一種語言。

5. 按一下**建立**。

很棒的開始！您剛剛已建立應用程式！

若要在新增服務或設定持續交付之前檢查程式碼，請按一下「應用程式詳細資料」頁面上的**下載程式碼**。請檢查所下載壓縮檔中的 `README.md` 檔案，以找出您是否需要採取更多動作，以讓應用程式啟動並執行。
{: tip}

## 步驟 3. 新增服務（選用）
{: #resources-starterkit}

如果入門範本套件需要特定的服務，則自動佈建的服務實例會自動建立並連接至應用程式。

您也可以新增服務，藉由 Watson 的認知能力加強您的應用程式，也可以新增行動服務或安全服務。針對本指導教學，請新增工作區以便管理您的資料。

1. 在「應用程式詳細資料」頁面上，按一下**建立服務**或**連接現有的服務**（視是否已有要連接至此應用程式的服務而定）。
2. 選取您要的服務類型，並遵循將現有服務新增至應用程式或建立服務實例的提示。

您要的所有服務在新增之後，就會顯示在「應用程式詳細資料」頁面中。

## 步驟 4. 選取部署目標以及配置持續交付
{: #target-starterkit}

當您選取部署目標時，會為應用程式自動建立 DevOps 工具鏈。此工具鏈包括可指出應用程式部署狀態的 Delivery Pipeline。所產生的新應用程式會推送至為此工具鏈一部分的 GitLab 儲存庫。

啟用 DevOps 工具鏈會為您的應用程式建立一個以團隊為基礎的開發環境。建立工具鏈時，應用程式服務會建立 Git 儲存庫，您可以在其中檢視原始碼、複製應用程式以及建立和管理問題。您也可以存取專用的 GitLab 環境，以及持續交付管線。它們是根據您所選取的部署目標（[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虛擬伺服器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial)）進行自訂。

從「{{site.data.keyword.cloud_notm}} 開發人員」儀表板建立的所有工具鏈，都會針對自動部署進行配置。
{: note}

若要選取部署目標以及配置持續交付，請完成這些步驟：

1. 在「應用程式詳細資料」頁面上，按一下**配置持續交付**。
2. 選取一個部署目標。根據您所選目標的指示設定部署目標：
  * **部署至 [IBM Kubernetes Service](/docs/containers?topic=containers-app)**。此選項會建立主機（稱為工作者節點）的叢集，以部署及管理高可用性的應用程式容器。您可以建立叢集或部署至現有的叢集。
  * **部署至 Cloud Foundry**。此選項會部署雲端原生應用程式，而您不需要管理基本基礎架構。如果您的帳戶可以存取 {{site.data.keyword.cfee_full_notm}}，則可以選取**[公用雲端](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)**或**[企業環境](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**的部署者類型，用來建立及管理用於管理專供您企業使用的 Cloud Foundry 應用程式的隔離環境。
  * **部署至虛擬伺服器**。此選項會佈建虛擬伺服器實例、載入包含您應用程式的映像檔、建立 DevOps 工具鏈，以及為您起始第一個部署週期。如需相關資訊，請參閱[將應用程式部署至虛擬伺服器](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server)。

    部分入門範本套件可以進行 VSI 部署。若要使用此特性，請移至 [{{site.data.keyword.cloud_notm}} 儀表板](https://{DomainName})，然後在**應用程式**磚按一下**建立應用程式**。
    {: note}

在您選取及配置部署目標之後，「應用程式詳細資料」頁面會指出已配置持續交付。您可以按一下**檢視儲存庫**，以檢視包含應用程式原始碼的儲存庫。

## 步驟 5. 部署應用程式
{: #deploy-starterkit}

從 {{site.data.keyword.cloud_notm}} 開發人員儀表板建立的 DevOps 工具鏈，都會針對自動部署進行配置。
{: note}

在選取部署目標之後，請開啟新工具鏈的管線元件，以開始起始建置和部署處理程序，讓您可以在幾分鐘內看到新的應用程式。

1. 在「應用程式詳細資料」頁面上按一下**檢視工具鏈**。
2. 按一下 **Delivery Pipeline**，您可以在其中啟動建置、管理部署，以及檢視日誌和歷程。

使用適當配置的工具鏈，建置-部署的循環會自動開始，並且全都合併到您儲存庫的主要分支。如需相關資訊，請參閱[建置並部署](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)。

您可以從指令行執行 [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) 指令，以部署應用程式。如需相關資訊，請參閱[使用 CLI 部署應用程式](/docs/apps?topic=creating-apps-deploying-apps#deploy-cli)。

## 步驟 6. 驗證應用程式正在執行
{: #verify-starterkit}

部署應用程式之後，Delivery Pipeline 或指令行會將您指向應用程式的 URL。

1. 從 DevOps 工具鏈中，按一下 **Delivery Pipeline**，然後選取**部署階段**。
2. 按一下**檢視日誌和歷程**。
3. 在日誌檔中，尋找應用程式 URL：

    在日誌檔結尾，搜尋單字 `urls` 或 `view`。例如，您可能會看到日誌檔中有一行類似於 `urls: my-app-devhost.mybluemix.net`，或 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在瀏覽器中移至 URL。如果應用程式正在執行，則會顯示包含 `Congratulations` 或 `{"status":"UP"}` 的訊息。

如果您要使用指令行，請執行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 指令來檢視應用程式的 URL。然後，在瀏覽器中移至 URL。
