---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-07-22"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# 云应用程序的常用体系结构
{: #patterns}

{{site.data.keyword.cloud_notm}} 上的初学者工具包可帮助您使用成熟的体系结构来生成应用程序。应用程序各不相同，但如果将应用程序基于已知的体系结构模式，可以更轻松地快速获得可靠的结果。通过初学者工具包创建应用程序时，您需要从多种不同的模式类型中选择一种模式，还需要选择用于填充该模式的组件，如运行时。
{:shortdesc}

## Web 应用程序
{: #web}

“Web 应用程序”模式生成的应用程序用于向 Web 服务器提供 HTML、JavaScript 和样式表等 Web 内容。{{site.data.keyword.cloud_notm}} 提供了多个 Web 应用程序入门模板工具包。

* 基本 - 提供静态 `index.html` 文件、缺省和空白样式表以及 JavaScript 文件。
* 反应 - 用于构建用户界面的丰富框架。源文件位于 `src/client/app` 中，这些文件使用 WebPack 进行编译并在公共目录中提供。

您可以在 [{{site.data.keyword.cloud_notm}} App Service 开发者仪表板](https://console.bluemix.net/developer/appservice/dashboard)上找到“Web 应用程序”模式的入门模板工具包。

## 服务于前端的后端
{: #bff}

“服务于前端的后端”(BFF) 模式用于帮助创建后端代码，以通过符合用户对特定应用程序通道（如移动或 Web）的期望的方式来公开业务数据和服务。例如，移动设备上的用户可能会使用语音控件，而 Web 浏览器用户更偏好即点即选。您可以构建两个 BFF，一个用于包含服务（如 [{{site.data.keyword.conversationfull}} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://www.ibm.com/watson/ai-assistant/)）的移动，一个用于具有更复杂用户界面的 Web。

在 {{site.data.keyword.cloud_notm}} 中，可以使用多语言编程方法来构建 BFF。您可以使用 Node.js、Swift、Java 或 Python，并以使用容器服务的模式或使用无服务器功能来运行。

BFF 可管理数据持久性、高速缓存以及与以下高价值服务的集成。

* [{{site.data.keyword.ibmwatson}} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=watson)
* [{{site.data.keyword.iot_short_notm}} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=iot)
* [{{site.data.keyword.weather_short}} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/services/weather-company-data?taxonomyNavigation=apps)
* [{{site.data.keyword.sparks}} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://console.bluemix.net/catalog/services/apache-spark?taxonomyNavigation=apps)。

BFF 最常使用 REST 模式来公开 API，但您也可以将 BFF 设计为通过使用 {{site.data.keyword.messagehub}} 的消息传递体系结构来运行。

根据您的语言和框架需求选择 BFF 入门模板工具包。您可以在 [{{site.data.keyword.cloud_notm}} App Service 开发者仪表板](https://console.bluemix.net/developer/appservice/dashboard)上找到 BFF 模式的入门模板工具包。

## 微服务
{: #microservice}

微服务应用程序会提供用于构建后端微服务的基础，包括基本运行状况端点和 REST API。生成的应用程序包含微服务本身以及任何连接的云服务都需要的所有依赖项。

根据您的语言和框架需求选择微服务入门模板工具包。您可以在 [{{site.data.keyword.cloud_notm}} App Service 开发者仪表板](https://console.bluemix.net/developer/appservice/dashboard)上找到“微服务”模式的初学者工具包。

## 移动
{: #mobile}

移动应用程序不同于其他模式，其具有一个重要的客户机端组件。此模式可能包含与移动服务（如推送通知、认证和移动分析）的直接连接。移动服务称为“移动后端即服务”(MBaaS) 模式。还可能有专用的[服务于前端的后端](#bff)。

{{site.data.keyword.cloud_notm}} 针对 iOS Swift、Android 和 Cordova 提供了多个移动初学者工具包。您可以在 [{{site.data.keyword.cloud_notm}} Mobile 开发者仪表板](https://console.bluemix.net/developer/mobile/dashboard)上找到“移动”模式的初学者工具包。

## 语言
{: #languages}

{{site.data.keyword.cloud_notm}} 提供的初学者工具包有适用于多种语言和框架的不同版本。例如，云微服务初学者工具包提供了 Node.js 选项，而与数据分析密切相关的初学者工具包可能包含 Python 或 Go。下面将讨论 {{site.data.keyword.cloud_notm}} 入门模板工具包中使用的一些常用语言。

|编程语言|描述
|开发框架|
|-----|-----|-----|
|Java|[Java](../runtimes/liberty/getting-started.html) 非常适用于构建企业级应用程序。但是 Java 8 中的新功能在与更轻量级的运行时（如 Liberty）和框架（如 Spring Boot）组合使用时，Java 也非常适用于构建微服务。Java 是用于 Android 应用程序的常用编程语言。|Spring、Liberty 和 Android|
|Swift|[Swift](../runtimes/swift/getting-started.html) 是在 2014 年创建的现代编程语言，旨在取代 Objective C，并已于 2015 年 12 月开放源代码。目前，Swift 用于构建 iOS、macOS、Web Service，以及在使用 x86、ARM 或 z/Architecture 的 Linux 和 macOS 操作系统上构建系统软件。它以类似于脚本语言的方式进行编写，但经过编译后，能以较低的处理器使用率获得类似于 C 语言的高性能。它非常适合云运行时。Swift 使用了 Java 中具备的强类型和静态类型系统，但却使用了 JavaScript 中具备的功能样式和异步例程。Swift 的性能良好，源代码编译为使用 LLVM 编译器工具链的本机代码。它可以轻松使用以 C 语言编写的其他语言中的系统库。由于 Swift 可用于对客户机端和服务器端应用程序进行编码，因此开发人员需要将功能从客户机轻松迁移到服务器或从服务器迁移到客户机时，可使用 Swift。|Kitura 和 iOS|
|Node.js|[Node.js](../runtimes/nodejs/getting-started.html) 是一种 JavaScript 运行时，使用由事件驱动的非阻塞性 I/O 模型，从而成为轻量级且高效的运行时。它在 Web 应用程序的吞吐量和可扩展性方面以及服务于前端的后端模式和微服务中表现卓越。Node.js 的软件包注册表 npm 提供对大量开放式源代码模块的访问。同时还提供各种功能来加速应用程序开发。|Express|
|JavaScript|JavaScript 在 Web 页面中创造交互效果。JavaScript 与 HTML 和 CSS 一起构成了大多数 Web 页面的基础。JavaScript 代码使用 Cordova 插件进行包装时，可以充分利用本机设备功能。具有 Web 技能的开发者可以轻松创建移动应用程序，并且可以视情形在 Web 和移动设备之间复用应用程序代码。|Cordova|
|Python|[Python](../runtimes/python/getting-started.html) 是一种通用的解释型编程语言，着重于提高可读性。程序员使用 Python 来实现函数时，所使用的代码行数要少于使用其他语言时可能需要的代码行数。利用该语言的特性，可以编写面向对象的代码、功能性代码或命令式代码。Python 通常用于处理自然语言任务。|Flask 和 Django|


