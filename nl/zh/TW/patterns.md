---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-03-16"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# 雲端應用程式的一般架構
{: #patterns}

{{site.data.keyword.cloud_notm}} 上的入門範本套件能協助您利用經過驗證的架構來產生應用程式。應用程式都是不同的，但當您的應用程式以已知的架構型樣為基礎時，更容易快速取得可靠的結果。當您從入門範本套件建立專案時，您選擇了數種不同型樣類型的其中一種以及元件（例如執行時期）來移入型樣。
{:shortdesc}

## Web 應用程式
{: #web}

Web 應用程式型樣會產生專案，以提供 Web 內容（例如 HTML、JavaScript 和樣式表）給 Web 伺服器。有數個 Web 應用程式入門範本套件。

* 基本 - 提供靜態 `index.html` 檔、預設和空的樣式表，以及 JavaScript 檔。
* React - Rich 架構，用來建置使用者介面。原始檔位於 `src/client/app`，並使用 WebPack 進行編譯，且在公用目錄中提供。

您可以在 [{{site.data.keyword.cloud_notm}} 應用程式服務開發人員儀表板](https://console.bluemix.net/developer/appservice/dashboard)上找到「Web 應用程式」型樣的入門範本套件。

## Backend for Frontend
{: #bff}

Backend for Frontend 型樣 (BFF) 可協助建立後端程式碼，以符合特定應用程式通道（例如行動式或 Web）之使用者預期的方式來公開商業資料及服務。例如，行動式裝置上的使用者可能會使用語音控制，而透過 Web 瀏覽器使用應用程式的使用者偏好點按方式。您可以建置兩個 BFF：一個適用於包含 [{{site.data.keyword.conversationfull}} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.ibm.com/watson/developercloud/conversation.html) 這類服務的行動式，一個則適用於具有更準確使用者介面的 Web。

在 {{site.data.keyword.cloud_notm}} 中，您可以使用多國語言程式設計方式來建置 BFF。您可以使用 Node.js、Swift、Java 或 Python，並以具有容器服務的型樣或使用無伺服器功能的型樣來執行它們。

BFF 管理資料持續性、快取以及與高價值服務的整合，例如 [{{site.data.keyword.ibmwatson}} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=watson)、[{{site.data.keyword.iot_short_notm}} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=iot)、[{{site.data.keyword.weather_short}} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/weather-company-data?taxonomyNavigation=apps) 及 [{{site.data.keyword.sparks}} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://console.bluemix.net/catalog/services/apache-spark?taxonomyNavigation=apps)。

BFF 會公開最常使用 REST 型樣的 API，但您可以設計 BFF，利用 {{site.data.keyword.messagehub}} 來從傳訊架構運作。

根據語言及架構需求，有數個您可以從中選擇的 BFF 入門範本套件。您可以在 [{{site.data.keyword.cloud_notm}} 應用程式服務開發人員儀表板](https://console.bluemix.net/developer/appservice/dashboard)上找到 BFF 型樣的入門範本套件。

## 微服務
{: #microservice}

「微服務」專案提供建置後端微服務的基礎（包括基本性能端點及 REST API）。產生的專案包含微服務本身及任何附加之雲端服務所需的所有相依關係。

根據語言及架構需求，有數個您可以從中選擇的微服務入門範本套件。您可以在 [{{site.data.keyword.cloud_notm}} 應用程式服務開發人員儀表板](https://console.bluemix.net/developer/appservice/dashboard)上找到「微服務」型樣的入門範本套件。

## 行動式
{: #mobile}

行動式專案與其他型樣不同，因為它們具有重大用戶端元件。該型樣可能包括與行動式服務（例如推送通知、鑑別及行動式分析）的直接連線，稱為「行動式後端即服務」或 MBaaS 型樣，或者可能有專用 [Backend for Frontend](#bff)。  

{{site.data.keyword.cloud_notm}} 提供適用於 iOS Swift、Android 及 Cordova 的數個行動式入門範本套件。您可以在 [{{site.data.keyword.cloud_notm}} Mobile 開發人員儀表板](https://console.bluemix.net/developer/mobile/dashboard)上找到「行動式」型樣的入門範本套件。

## 語言
{: #languages}

各種語言及架構都具有提供的入門範本套件 {{site.data.keyword.cloud_notm}}。例如，雲端微服務入門範本套件提供 Node.js 選項，而與資料分析緊密相關的入門範本套件可能包括 Python 或 Go。已討論 {{site.data.keyword.cloud_notm}} 入門範本套件中使用的部分常用語言。


|程式設計語言 | 說明
| 開發架構 |
|-----|-----|-----|
|Java | [Java](../runtimes/liberty/getting-started.html) 具有經過驗證的功能可建置企業級應用程式。但是，Java 8 中的新功能與更輕量型的執行時期（例如 Liberty）及架構（例如 Spring Boot）搭配使用，也可讓 Java 更完美地適用於建置微服務。此外，Java 也是 Android 應用程式的熱門程式設計語言。| Spring、Liberty、Android |
|Swift| [Swift](../runtimes/swift/getting-started.html) 是 Apple 在 2014 所建立的現代化程式設計語言，其設計目的是要取代 Objective C 的使用，並在 2015 年 12 月公開開放程式碼。現在，它是用來在使用 x86、ARM 或 z/Architecture 的 Linux 及 macOS 作業系統上建置 iOS、macOS、Web 服務及系統軟體。它的撰寫方式類似 Script 語言，但會進行編譯以獲得類似 C 語言的低額外負擔與高效能，讓它更適用於雲端執行時期。它會使用您在 Java 中看到的強式及靜態類型系統，而不是您在 JavaScript 中看到的功能性樣式及非同步常式。它的效能極高，而且原始檔會使用 LLVM 編譯器工具鏈編譯成原生程式碼，並且可以輕鬆地運用使用 C 所撰寫的外部系統程式庫。因為 Swift 可以用來編寫用戶端及伺服器端應用程式的程式碼，所以開發人員會在需要將功能從用戶端輕鬆地移轉至伺服器（反之亦然）時使用 Swift。| Kitura、iOS|
|Node.js | [Node.js](../runtimes/nodejs/getting-started.html) 是一種 JavaScript 執行時期，使用事件驅動、非封鎖 I/O 模型讓它更為輕量且更具效率，對於 Web 應用程式、Backend for Frontend 型樣及微服務的產量及可擴充性最有幫助。Node.js 的套件生態系統 npm 可存取大量的開放程式碼模組，並提供廣泛的功能來加速應用程式開發。| 簡易版|
|JavaScript|JavaScript 會在網頁中建立互動式效果。JavaScript 與 HTML 及 CSS 是大部分網頁的基礎。包裝 Cordova 外掛程式時，JavaScript 程式碼可以完整善用原生裝置功能。具有 Web 技能的開發人員可以輕鬆地建立行動式應用程式，而且可在該處於 Web 及行動式之間重複使用適當的應用程式碼。|Cordova|
|Python| [Python](../runtimes/python/getting-started.html) 是通用解譯程式設計語言，其大大地強調了可讀性。Python 容許程式設計師實作的功能程式碼行少於其他語言可能需要的程式碼行。語言中的特性可讓您寫入物件導向、功能或命令程式碼。Python 常用來處理自然語言作業。| Flask、Django|

