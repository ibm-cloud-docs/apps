---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-10"

keywords: getting started apps, create app tutorial, add resources, deploy apps, create app, app tutorial

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 入門指導教學
{: #tutorial-getting-started}

您可以在 {{site.data.keyword.cloud}} 中建置企業已可使用的行動及 Web 應用程式，以及充分運用 {{site.data.keyword.cloud_notm}} 所管理的雲端延伸規格。您有數個開始使用選項。使用為您管理處理程序的入門範本套件來建立應用程式，或者，如果您知道想要的項目，則請從頭開始並使用所需的資源來建置應用程式，或使用現有儲存庫並自帶程式碼。
{: shortdesc}

不論您是有想要現代化且進入雲端的[現有程式碼](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc#tutorial-byoc)，或是您正在開發[全新的應用程式](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit)，您都可以利用 {{site.data.keyword.cloud_notm}} 可用服務和運行環境架構中，快速成長的生態系統。

您需要協助來決定要從何處開始嗎？請參閱此圖表以瞭解構想！

![開發人員經驗概觀](images/dev-journey.png "開發人員經驗概觀")

## 開始之前
{: #prereqs-getting-started}

您可以使用 {{site.data.keyword.cloud_notm}} 主控台或指令行介面 (CLI) 來建立應用程式。如果您要使用 CLI，請參閱[安裝步驟](/docs/cli?topic=cloud-cli-ibmcloud-cli)。

## 步驟 1. 建立應用程式
{: #create-getting-started}

選取下列其中一個進入點，以建立應用程式：

* [入門範本套件](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit)是使用案例專用的，並在各種程式設計語言和架構型樣中產生可正式作業的應用程式。
* [IBM Developer 程式碼型樣![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://developer.ibm.com/patterns/){:new_window} 可協助您快速建立應用程式並將其部署至 {{site.data.keyword.cloud_notm}}。如需相關資訊，請參閱[程式碼型樣](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern)。
* [自帶程式碼](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc)，方法為鏈結至您自己的現有內容儲存庫。您的應用程式及 Docker 映像檔必須位於相同的儲存庫中。
* 如果知道您的期望，則請使用空白入門範本套件，以您需要的服務來從頭開始建置[自訂應用程式](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch)。
* 使用 [CLI 及開發人員工具](/docs/apps?topic=creating-apps-create-deploy-app-cli)，來建立及部署自訂或入門範本套件應用程式。
* 針對您今天就可以建立並開始使用的應用程式和服務，瀏覽或搜尋 [{{site.data.keyword.cloud_notm}} 型錄](https://{DomainName}/catalog){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。

## 步驟 2. 新增服務
{: #resources-getting-started}

當您使用入門範本套件建立應用程式時，會自動為您建立服務。您可以在主控台的**應用程式詳細資料**頁面上，按一下**建立服務**，來建立其他服務與應用程式的關聯。

執行下列指令，以使用 CLI 將服務新增至應用程式。您可以從帳戶上已啟用的服務中選取現有服務，或是新增一個服務。 
```
ibmcloud dev edit
```
{: codeblock}

如需相關資訊，請參閱[將服務新增至應用程式](/docs/apps?topic=creating-apps-add-resource)。

## 步驟 3. 部署應用程式
{: #deploy-getting-started}

您可以使用主控台或 CLI 來部署應用程式。

### 使用主控台
{: #console-getting-started}

若要使用主控台部署應用程式，請完成下列步驟：

1. 在**應用程式詳細資料**頁面上，按一下**配置持續交付**。
2. 選取部署目標，選取工具鏈設定，然後按一下**建立**。{{site.data.keyword.cloud_notm}} 會自動建立開放式工具鏈，此工具鏈會完整地具備 Git 儲存庫及持續交付管線。
3. 開啟新工具鏈的管線階段，以檢視建置及部署處理程序，讓您可以在數分鐘內檢視新的應用程式。

如需相關資訊，請參閱「部署及整合應用程式」小節中各種部署主題的目錄。

### 使用 CLI
{: #cli-getting-started}

若要使用 CLI 來部署應用程式，請執行 `ibmcloud dev deploy` 指令。如需相關資訊，請參閱[使用 CLI 建立及部署應用程式](/docs/apps?topic=creating-apps-create-deploy-app-cli)。

現在，您已準備好進行反覆運算式開發及持續交付。

## 相關資訊
{: #related-getting-started}

每個語言都有[程式設計手冊](https://{DomainName}/docs/home/build){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")，可協助您開始進行。您有許多選項，可用來從 {{site.data.keyword.baremetal_short}} 管理具有 {{site.data.keyword.cloud_notm}} 基礎架構的應用程式，以當作無伺服器功能來執行。
