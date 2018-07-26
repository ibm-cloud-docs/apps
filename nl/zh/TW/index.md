---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-12"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 入門指導教學
{: #create}

在 {{site.data.keyword.Bluemix}} 中，您可以建置企業層級行動及 Web 應用程式，以及充分運用 {{site.data.keyword.Bluemix_notm}} 所管理的雲端延伸規格。您可以使用 {{site.data.keyword.Bluemix}} 主控台及指令行工具來建置、執行及部署應用程式。請使用下列兩種方法開始：使用為您管理處理程序的入門套件來建立應用程式，或者如果您知道想要的項目，則使用所需的資源來建置應用程式。
{:shortdesc}

您可以使用入門範本套件來快速開始處理您的應用程式，並準備它以便未來進行開發。選擇入門範本套件和程式設計語言、建立應用程式，然後設定 DevOps 工具鏈，以自動部署應用程式。您也可以下載程式碼進行立即檢驗。

入門範本套件有許多種類，其中包括：

* [Watson ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/developer/watson/dashboard){:new_window}
* [Apple ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/developer/appledevelopment/dashboard){:new_window}
* [Mobile ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/developer/mobile/dashboard){:new_window}
* [Web App ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/developer/appservice/dashboard){:new_window}
* [Security ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/developer/security/dashboard){:new_window}
<!--* [Watson Data Platform developer console](https://console.bluemix.net/developer/dataplatform)-->
* [Finance ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/developer/finance/dashboard){:new_window}

## 開始之前

[註冊 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net){: new_window} {{site.data.keyword.cloud_notm}} 帳戶。輸入電子郵件、名稱、公司、地區和電話號碼。

您不需要信用卡就可以註冊一個免費帳戶。但輸入信用卡可讓您存取更多資源，您也能更輕鬆地掌握 {{site.data.keyword.cloud_notm}} 提供的所有內容。

## 步驟 1：建立應用程式
{: #project}

1. 按一下**功能表**圖示 ![功能表圖示](../icons/icon_hamburger.svg) > **Web 應用程式**。

2. 按一下**從 Web 開始**區段中的**開始使用**。

3. 選取您選擇的入門範本套件、閱讀詳細資料，然後按一下**建立**。

   若要檢視入門範本套件中所包含的內容，請展開 App Service Starter Kits 儀表板上的磚。
   {: tip}

4. 為您的應用程式命名、選取語言，然後按一下**建立**。

   很棒的開始！您剛剛建立了應用程式。

   若要檢查您的程式碼，請按一下應用程式詳細資料頁面上的**下載程式碼**。請檢查所下載壓縮檔中的 `README.md` 檔，以找出您是否需要採取更多動作以讓入門範本應用程式啟動並執行。
   {: tip}

## 步驟 2：新增資源
{: #addResources}

大部分入門範本套件會指示 {{site.data.keyword.cloud_notm}} 為您自動佈建資源。您也可以在應用程式詳細資料頁面上按一下**新增資源**，使更多資源與您的應用程式相關聯。

若要在本端開發及執行您的應用程式，請使用 [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html)。
{: tip}

## 步驟 3：部署至 {{site.data.keyword.cloud_notm}}
{: #deploy}

按一下應用程式詳細資料頁面上的**部署至雲端**、選取部署方法（例如 Kubernetes Cluster 或 Cloud Foundry 應用程式），然後按一下**建立**。{{site.data.keyword.cloud_notm}} 會自動建立開放式工具鏈，此工具鏈會完整地具備 Git 儲存庫及持續交付管線。請開啟新工具鏈的管線元件，以開始起始的建置及部署處理程序，以便您可以在數分鐘內看到您的新應用程式。

現在，您已準備好進行反覆運算式開發及持續交付。
