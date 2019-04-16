---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, create apps, add resources, deploy apps

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

## 開始之前
{: #prereqs-getting-started}

您可以使用 {{site.data.keyword.cloud_notm}} 主控台或指令行介面 (CLI) 來建立應用程式。如果您要使用 CLI，請參閱[安裝步驟](/docs/cli?topic=cloud-cli-ibmcloud-cli)。

## 步驟 1. 建立應用程式
{: #create-getting-started}

選取下列其中一個進入點，以建立應用程式：
* [入門範本套件](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit)：從為您管理處理程序的 App Service 入門範本套件選項中建立應用程式。
* [自訂](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch)：如果您知道想要的內容，則請使用空白入門範本套件，從頭開始使用您需要的資源來建置自訂應用程式。
* [自帶程式碼](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc)：鏈結至您自己的現有內容儲存庫，以自帶程式碼。您的應用程式及 Docker 映像檔必須位於相同的儲存庫中。
* [CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli)：使用 CLI 及 Developer 工具，以建立及部署自訂或入門範本套件。
* [程式碼型樣](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern)：使用 IBM Developer 程式碼型樣作為用於建立應用程式的基準。
* [{{site.data.keyword.cloud_notm}} 型錄 ](https://cloud.ibm.com/catalog){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")：您可以瀏覽或搜尋型錄中可立即建立並開始使用的應用程式及服務。

## 步驟 2. 新增資源
{: #resources-getting-started}

當您使用入門範本套件建立應用程式時，會自動為您建立服務。您可以在主控台的**應用程式詳細資料**頁面上按一下**新增服務**，來建立其他服務與應用程式的關聯。

若要使用 CLI 新增服務，請執行下列指令，以將服務新增至應用程式。您可以從帳戶上已啟用的服務選取現有服務，或是新增一個服務。 
```
ibmcloud dev edit
```
{: codeblock}

如需相關資訊，請參閱[將服務新增至應用程式](/docs/apps?topic=creating-apps-add-resource)。

## 步驟 3. 部署應用程式
{: #deploy-getting-started}

您可以使用主控台或指令行來部署應用程式。

### 使用主控台
{: #console-getting-started}

若要使用主控台部署應用程式，請完成下列步驟：

1. 在**應用程式詳細資料**頁面上，按一下**配置持續交付**。
2. 選取部署目標，選取工具鏈設定，然後按一下**建立**。{{site.data.keyword.cloud_notm}} 會自動建立開放式工具鏈，此工具鏈會完整地具備 Git 儲存庫及持續交付管線。
3. 開啟新工具鏈的管線階段，以檢視建置及部署處理程序，讓您可以在數分鐘內檢視新的應用程式。

如需相關資訊，請參閱「部署及整合應用程式」小節中各種部署主題的目錄。

### 使用指令行
{: #cli-getting-started}

若要使用指令行部署應用程式，請執行 `ibmcloud dev deploy` 指令。如需相關資訊，請參閱[使用 CLI 建立及部署應用程式](/docs/apps?topic=creating-apps-create-deploy-app-cli)。

現在，您已準備好進行反覆運算式開發及持續交付。
