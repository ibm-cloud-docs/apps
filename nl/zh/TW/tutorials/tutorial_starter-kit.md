---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-15"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 使用入門範本套件建立應用程式
{: #tutorial-starterkit}

您可以使用入門範本套件，快速讓您的應用程式啟動，並準備它以便未來進行開發。選擇入門範本套件和程式設計語言、建立應用程式，然後設定 DevOps 工具鏈，以自動部署應用程式。您也可以下載程式碼以便立即進行檢驗。
{: shortdesc}

您可以從一群精選的入門範本套件建立應用程式，這其中包括空白的入門範本套件（如果您想要自己自訂建置選項的話）。無論哪一種方法，都會自動建立 DevOps 工具鏈來部署應用程式。您也可以下載程式碼以便立即進行檢驗。

{{site.data.keyword.cloud_notm}} 有多種不同領域的開發人員入口網站（例如，Watson、「安全」或「財務」）或數位通路（例如，「行動裝置」或「Web 應用程式」）。您可以從**功能表**圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) 存取這些入口網站。

每個開發者入口網站都提供與該入口網站焦點區域相關的入門範本套件。入口網站提供一致的直覺式工作流程，以在幾分鐘內建立一個工作中的可正式作業應用程式。

入門範本套件有許多種類，其中包括：
* [Watson ](https://{DomainName}/developer/watson/dashboard){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")
* [Apple ](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")
* [行動 ](https://{DomainName}/developer/mobile/dashboard){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")
* [Web 應用程式 ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")
* [安全 ](https://{DomainName}/developer/security/dashboard){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")
* [財務 ](https://{DomainName}/developer/finance/dashboard){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")

[進一步瞭解](/docs/apps?topic=creating-apps-starter-kits)入門範本套件。

## 步驟 1. 建立應用程式
{: #create-starterkit}

1. 從 [{{site.data.keyword.cloud}} 儀表板](https://{DomainName}){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")，按一下**功能表**圖示 ![「功能表」圖示](../../icons/icon_hamburger.svg) > **Web 應用程式**。

2. 按一下**從 Web 開始**區段中的**開始使用**。

3. 選取您選擇的入門範本套件、閱讀詳細資料，然後按一下**建立**。
    
    若要查看入門範本套件中所包含的內容，請展開[應用程式服務入門範本套件 ](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示") 儀表板上的磚。「建立應用程式」入門範本套件選項可以用來作為空白的入門範本應用程式，並可進一步自訂以符合您的需求。
    {: tip}

4. 為您的應用程式命名、選取資源群組、選擇性地提供標記、選取語言，然後按一下**建立**。
    
    很棒的開始！您剛剛建立了應用程式。

若要檢查您的程式碼，請按一下**應用程式詳細資料**頁面上的**下載程式碼**。請檢查所下載壓縮檔中的 `README.md` 檔，以找出您是否需要採取更多動作，以讓入門範本應用程式啟動並執行。
{: tip}

如需相關資訊，請參閱下列主題：
 * [使用入門範本套件來建立基本 Web 應用程式](/docs/apps/tutorials?topic=creating-apps-tutorial-webapp)
 * [使用標籤](/docs/resources?topic=resources-tag)

## 步驟 2. 新增服務
{: #resources-starterkit}

您可以新增服務，藉由 Watson 的認知能力加強您的應用程式，也可以新增行動服務或安全服務。針對本指導教學，請新增工作區以便管理您的資料。

1. 在**應用程式詳細資料**頁面上，按一下**新增服務**。
2. 選取您要的服務類型。例如，選取**資料** > **下一步** > **Cloudant** > **下一步**。
3. 選取定價方案。有免費選項，您可以用於本指導教學。
4. 按一下**建立**。

## 步驟 3. 部署至 {{site.data.keyword.cloud_notm}}
{: #deploy-starterkit}

按一下**應用程式詳細資料**頁面上的**配置持續交付**，選取部署目標，然後按一下**建立**。{{site.data.keyword.cloud_notm}} 會自動建立開放式工具鏈，此工具鏈會完整地具備 Git 儲存庫及持續交付管線。

啟用工具鏈會為您的應用程式建立一個以團隊為基礎的開發環境。建立工具鏈時，應用程式服務會建立 Git 儲存庫，您可以在其中檢視原始碼、複製應用程式以及建立和管理問題。您也可以存取專用的 GitLab 環境，以及持續交付管線。它們針對您所選擇的部署環境（[Kubernetes](/docs/containers?topic=containers-container_index)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虛擬伺服器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers)）經過自訂。

在選取部署目標之後，請開啟新工具鏈的管線元件，以開始起始建置和部署處理程序，讓您可以在幾分鐘內看到新的應用程式。

從「{{site.data.keyword.cloud_notm}} 開發人員」儀表板建立的所有工具鏈，都會針對自動部署進行配置。
{: note}

若要使用指令行來部署應用程式，請使用 `ibmcloud dev deploy`。如需相關資訊，請參閱[使用 CLI 建立及部署應用程式](/docs/apps?topic=creating-apps-create-deploy-app-cli)。
