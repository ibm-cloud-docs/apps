---

copyright:
  years: 2016, 2019
lastupdated: "2019-07-17"

keywords: supported architecture, supported languages cloud, web app, microservices, mobile, programming languages, app types, common architecture, cloud app, developer console, app service

subcollection: creating-apps

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

您可以在 [{{site.data.keyword.cloud_notm}} 應用程式服務開發人員主控台](https://{DomainName}/developer/appservice/dashboard){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 上找到適用於 Web 應用程式模式的入門範本套件。

## 微服務應用程式
{: #microservice}

「微服務」應用程式提供建置後端微服務的基礎（包括基本性能端點及 REST API）。產生的應用程式包含微服務本身及任何附加之雲端服務所需的所有相依關係。

請針對您的語言及架構需求選擇微服務入門範本套件。您可以在 [{{site.data.keyword.cloud_notm}} 應用程式服務開發人員儀表板](https://{DomainName}/developer/appservice/dashboard){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 上找到適用於「微服務」模式的入門範本套件。

## 行動應用程式
{: #mobile}

行動應用程式與其他模式不同，因為它們具有重大用戶端元件。該模式可能包括與行動服務（例如推送通知、鑑別及行動分析）的直接連線。行動服務稱為「行動後端即服務」，或 MBaaS 模式。它們也有專用的 Backend-for-frontend。

{{site.data.keyword.cloud_notm}} 提供適用於 iOS Swift 及 Android 的數個行動入門範本套件。您可以在 [{{site.data.keyword.cloud_notm}} Mobile 開發人員主控台](https://{DomainName}/developer/mobile/dashboard){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 上找到適用於「行動」模式的入門範本套件。

此外，您還可以使用基本入門範本套件並選取行動應用程式類型，來建立自訂行動應用程式。如需相關資訊，請參閱[建立行動應用程式](/docs/apps?topic=creating-apps-tutorial-mobile)。

## 以語言為基礎的應用程式
{: #languages}

{{site.data.keyword.cloud_notm}} 提供的入門範本套件有各種語言及架構。例如，雲端微服務入門範本套件提供 Node.js 選項，而與資料分析緊密相關的入門範本套件可能包括 Python 或 Go。已討論 {{site.data.keyword.cloud_notm}} 入門範本套件中使用的部分常用語言。

|程式設計語言 | 說明                                                  |開發架構 |
|-----|-----|-----|
|Java | [Java](/docs/runtimes/liberty?topic=liberty-getting-started) 很適合用來建置企業級應用程式。但是，Java 8 中的新特性與更輕量型的運行環境（例如 Liberty）及架構（例如 Spring Boot）搭配使用，表示 Java 也很適合用來建置微服務。Java 也是 Android 應用程式的熱門程式設計語言。|Spring、Liberty、Android |
|Swift|[Swift](/docs/runtimes/swift?topic=Swift-getting-started) 是在 2014 所建立的現代化程式設計語言，其設計目的是要取代 Objective C，並在 2015 年 12 月公開開放程式碼。現在，它是用來在使用 x86、ARM 或 z/Architecture 的 Linux 及 macOS 作業系統上建置 iOS、macOS、Web 服務及系統軟體。它的撰寫方式類似 Script 語言，但會進行編譯以獲得類似 C 語言的低處理器用量與高效能。它極適合雲端運行環境。它會使用您在 Java 中看到的強式及靜態類型系統，而不是您在 JavaScript 中看到的功能性樣式及非同步常式。它的效能極高，而且原始檔會編譯成使用 LLVM 編譯器工具鏈的原生程式碼。它可以輕鬆地使用來自其他語言且以 C 語言撰寫的系統檔案庫。因為 Swift 可以用來撰寫用戶端及伺服器端應用程式的程式碼，所以開發人員會在需要將功能從用戶端輕鬆地移轉至伺服器（以及反方向）時使用 Swift。|Kitura、iOS|
|Node.js |[Node.js](/docs/runtimes/nodejs?topicid=Nodejs-getting-started) 是一種 JavaScript 運行環境，使用事件驅動、非封鎖 I/O 模型讓它更為輕量且更具效率。它對於 Web 應用程式、Backend for Frontend 模式及微服務的產量及可擴充性最有幫助。Node.js 的套件登錄 npm 可存取大量的開放程式碼模組。它提供廣泛的特性來加速應用程式開發。| Express|
|Python| [Python](/docs/runtimes/python?topic=Python-getting_started) 是通用解譯程式設計語言，它強調可讀性。Python 容許程式設計師實作的功能程式碼行少於其他語言可能需要的程式碼行。語言中的特性可讓您寫入物件導向、功能或命令程式碼。Python 常用來處理自然語言作業。|Flask、Django|
{: caption="表 1. 入門範本套件中使用的語言" caption-side="top"}
