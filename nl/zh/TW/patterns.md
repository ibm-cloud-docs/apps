---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-07-12"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# 雲端應用程式的一般架構
{: #patterns}

{{site.data.keyword.cloud_notm}} 上的入門範本套件能協助您利用經過驗證的架構來產生應用程式。應用程式都是不同的，但當您的應用程式以已知的架構模式為基礎時，更容易快速取得可靠的結果。當您從入門範本套件建立應用程式時，您選擇了數種不同模式類型的其中一種以及元件（例如運行環境）來移入模式。
{:shortdesc}

## Web 應用程式
{: #web}

Web 應用程式模式會產生應用程式，以提供 web 內容（例如 HTML、JavaScript 和樣式表）給 Web 伺服器。{{site.data.keyword.cloud_notm}} 提供數個 Web 應用程式入門範本套件。

* 基本 - 提供靜態 `index.html` 檔、預設和空的樣式表，以及 JavaScript 檔。
* React - Rich 架構，用來建置使用者介面。原始檔位於 `src/client/app`，並使用 WebPack 進行編譯，且在公用目錄中提供。

您可以在 [{{site.data.keyword.cloud_notm}} 應用程式服務開發人員儀表板](https://console.bluemix.net/developer/appservice/dashboard)上找到 Web 應用程式模式的入門範本套件。

## Backend for Frontend
{: #bff}

Backendf for Frontend 模式 (BFF) 可協助建立後端程式碼，以符合特定應用程式通道（例如行動或 Web）之使用者預期的方式來公開商業資料及服務。例如，行動裝置上的使用者可能會使用語音控制，而 Web 瀏覽器使用者則偏好點按方式。您可以建置兩個 BFF：一個適用於包含 [{{site.data.keyword.conversationfull}} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/conversation.html) 這類服務的行動，一個則適用於具有更準確使用者介面的 Web。

在 {{site.data.keyword.cloud_notm}} 中，您可以使用多國語言程式設計方式來建置 BFF。您可以使用 Node.js、Swift、Java 或 Python，並以具有容器服務的模式或使用無伺服器功能的模式來執行它們。

BFF 會使用下列高價值的服務管理資料持續性、快取及整合。

* [{{site.data.keyword.ibmwatson}} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=watson)
* [{{site.data.keyword.iot_short_notm}} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=iot)
* [{{site.data.keyword.weather_short}} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/weather-company-data?taxonomyNavigation=apps)
* [{{site.data.keyword.sparks}} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/apache-spark?taxonomyNavigation=apps)。

BFF 會公開最常使用 REST 模式的 API，但您可以設計 BFF，從使用 {{site.data.keyword.messagehub}} 的傳訊架構工作。

請針對您的語言及架構需求選擇 BFF 入門範本套件。您可以在 [{{site.data.keyword.cloud_notm}} 應用程式服務開發人員儀表板](https://console.bluemix.net/developer/appservice/dashboard)上找到 BFF 模式的入門範本套件。

## 微服務
{: #microservice}

「微服務」應用程式提供建置後端微服務的基礎（包括基本性能端點及 REST API）。產生的應用程式包含微服務本身及任何附加之雲端服務所需的所有相依關係。

請針對您的語言及架構需求選擇微服務入門範本。您可以在 [{{site.data.keyword.cloud_notm}} 應用程式服務開發人員儀表板](https://console.bluemix.net/developer/appservice/dashboard)上找到「微服務」模式的入門範本套件。

## 行動
{: #mobile}

行動應用程式與其他模式不同，因為它們具有重大用戶端元件。該模式可能包括與行動服務（例如推送通知、鑑別及行動分析）的直接連線。行動服務稱為「行動後端即服務」，或 MBaaS 模式。它們也有專用的 [Backend for Frontend](#bff)。

{{site.data.keyword.cloud_notm}} 提供適用於 iOS Swift、Android 及 Cordova 的數個行動入門範本套件。您可以在 [{{site.data.keyword.cloud_notm}} Mobile 開發人員儀表板](https://console.bluemix.net/developer/mobile/dashboard)上找到「行動」模式的入門範本套件。

## 語言
{: #languages}

各種語言及架構都具有提供的入門範本套件 {{site.data.keyword.cloud_notm}}。例如，雲端微服務入門範本套件提供 Node.js 選項，而與資料分析緊密相關的入門範本套件可能包括 Python 或 Go。已討論 {{site.data.keyword.cloud_notm}} 入門範本套件中使用的部分常用語言。

|程式設計語言 |說明|開發架構 |
|-----|-----|-----|
|Java | [Java](../runtimes/liberty/getting-started.html) 很適合用來建置企業級應用程式。但是，Java 8 中的新特性與更輕量型的運行環境（例如 Liberty）及架構（例如 Spring Boot）搭配使用，表示 Java 也很適合用來建置微服務。Java 也是 Android 應用程式的熱門程式設計語言。|Spring、Liberty、Android |
|Swift|[Swift](../runtimes/swift/getting-started.html) 是在 2014 所建立的現代化程式設計語言，其設計目的是要取代 Objective C，並在 2015 年 12 月公開開放程式碼。現在，它是用來在使用 x86、ARM 或 z/Architecture 的 Linux 及 macOS 作業系統上建置 iOS、macOS、Web 服務及系統軟體。它的撰寫方式類似 Script 語言，但會進行編譯以獲得類似 C 語言的低處理器用量與高效能。它極適合雲端運行環境。它會使用您在 Java 中看到的強式及靜態類型系統，而不是您在 JavaScript 中看到的功能性樣式及非同步常式。它的效能極高，而且原始檔會編譯成使用 LLVM 編譯器工具鏈的原生程式碼。它可以輕鬆地使用來自其他語言且以 C 語言撰寫的系統檔案庫。因為 Swift 可以用來編寫用戶端及伺服器端應用程式的程式碼，所以開發人員會在需要將功能從用戶端輕鬆地移轉至伺服器（以及反方向）時使用 Swift。|Kitura、iOS|
|Node.js |[Node.js](../runtimes/nodejs/getting-started.html) 是一種 JavaScript 運行環境，使用事件驅動、非封鎖 I/O 模型讓它更為輕量且更具效率。它對於 Web 應用程式、Backend for Frontend 模式及微服務的產量及可擴充性最有幫助。Node.js 的套件登錄 npm 可存取大量的開放程式碼模組。它提供廣泛的特性來加速應用程式開發。| Express|
|JavaScript|JavaScript 會在網頁中建立互動式效果。JavaScript 與 HTML 及 CSS 是大部分網頁的基礎。包裝 Cordova 外掛程式時，JavaScript 程式碼可以完整善用原生裝置功能。具有 Web 技能的開發人員可以輕鬆地建立行動應用程式，而且可在該處於 Web 及行動之間重複使用適當的應用程式碼。|Cordova|
|Python| [Python](../runtimes/python/getting-started.html) 是通用解譯程式設計語言，它強調可讀性。Python 容許程式設計師實作的功能程式碼行少於其他語言可能需要的程式碼行。語言中的特性可讓您寫入物件導向、功能或命令程式碼。Python 常用來處理自然語言作業。|Flask、Django|


