---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-02"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# Common architectures For cloud apps
{: #patterns}

Starter kits on {{site.data.keyword.cloud_notm}} help you produce apps with a proven architecture. Apps are all different, but when you base your app on a known architectural pattern, it's easier to get a reliable result quickly. When you create an app from a starter kit, you’re choosing one of several different pattern types along with components, like a runtime, to populate the pattern.
{:shortdesc}

## Web App
{: #web}

The Web App pattern produces apps that serve web content such as HTML, JavaScript, and stylesheets to the web server. There are several Web App starter kits.

* Basic - serves a static `index.html` file, default and empty stylesheet, and JavaScript file.
* React - a rich framework to build user interfaces. The source files are in `src/client/app`, and are compiled with WebPack and served in the public directory.

You can find starter kits for Web App pattern on the [{{site.data.keyword.cloud_notm}} App Service developer dashboard](https://console.bluemix.net/developer/appservice/dashboard).

## Backend for Frontend
{: #bff}

Backend for Frontend pattern (BFF) helps create backend code that exposes business data and services in a way that matches user expectations for a specific app channel, such as mobile or web. For example, users on a mobile device might use voice control, while users who consume your app through web browser prefer point and click. You can build two BFFs, one for mobile that includes services like [{{site.data.keyword.conversationfull}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/conversation.html) and one for web that has a more sophisticated user interface.

In {{site.data.keyword.cloud_notm}}, you can build a BFF with polyglot programming approach. You can use Node.js, Swift, Java, or Python and running them in a pattern with container services or that use serverless functions.

The BFF manages data persistence, caching, and integration with high-value services like [{{site.data.keyword.ibmwatson}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=watson), [{{site.data.keyword.iot_short_notm}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=iot), [{{site.data.keyword.weather_short}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/weather-company-data?taxonomyNavigation=apps), and [{{site.data.keyword.sparks}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/catalog/services/apache-spark?taxonomyNavigation=apps).

The BFF exposes an API most commonly by using a REST pattern, but you can design your BFF to work from a messaging architecture that uses {{site.data.keyword.messagehub}}.

There are several BFF starter kits that you can choose from depending on your language and framework requirements. You can find starter kits for BFF pattern on the [{{site.data.keyword.cloud_notm}} App Service developer dashboard](https://console.bluemix.net/developer/appservice/dashboard).

## Microservice
{: #microservice}

Microservice apps provide the foundation for building backend microservices, including a basic health endpoint and REST API. Generated apps contain all the dependencies required both for the microservice itself, as well as for any attached cloud service.

There are several micro-service starter kits that you can choose from depending on your language and framework requirements.  You can find starter kits for Microservice pattern on the [{{site.data.keyword.cloud_notm}} App Service developer dashboard](https://console.bluemix.net/developer/appservice/dashboard).

## Mobile
{: #mobile}

Mobile apps are different from the other patterns because they have a significant client-side component. The pattern might include direct connection to mobile services like push notifications, authentication, and mobile analytics, which are known as Mobile Backend as a Service or MBaaS pattern, or might have a dedicated [Backend for Frontend](#bff).

{{site.data.keyword.cloud_notm}} offers several mobile starter kits for iOS Swift, Android, and Cordova. You can find starter kits for Mobile pattern on the [{{site.data.keyword.cloud_notm}} Mobile developer dashboard](https://console.bluemix.net/developer/mobile/dashboard).

## Languages
{: #languages}

The starter kits {{site.data.keyword.cloud_notm}} provides are available in various languages and frameworks. For example, cloud microservice starter kits offer a Node.js option, while starter kits closely related to data analysis might include Python or Go. Some common languages that are used in {{site.data.keyword.cloud_notm}} starter kits are discussed.


|Programming language | Description | Development frameworks |
|-----|-----|-----|
|Java | [Java](../runtimes/liberty/getting-started.html) has proven capabilities for building enterprise-grade applications. But new capabilities in Java 8, combined with lighter weight runtimes like Liberty and frameworks like Spring Boot, make Java perfectly suited for building microservices too.  In addition, Java is a popular programming language for Android apps. | Spring, Liberty, Android |
|Swift | [Swift](../runtimes/swift/getting-started.html) is a modern programming language created by Apple in 2014 that was designed to replace the use of Objective C and open-sourced in December of 2015. Today, it’s used to build iOS, macOS, web services, and systems software on Linux and macOS operating systems that use the x86, ARM, or z/Architecture. It writes like a scripting language but is compiled to gain C-like high performance with low overhead that make it ideal for cloud runtimes. It uses a strong and static type system that you see in Java but the functional style and asynchronous routines that you see in JavaScript. It’s very performant, and the source compiles to native code that uses the LLVM compiler toolchain and can use foreign system libraries that are written in C easily. Since Swift can be used to code both client-side and server-side apps, developers use Swift when they need to easily migrate functions from the client to the server and vice versa. | Kitura, iOS|
|Node.js | [Node.js](../runtimes/nodejs/getting-started.html) is a JavaScript runtime that uses an event-driven, non-blocking I/O model, making it lightweight and efficient, excelling in throughput and scalability for Web applications, backend-for-front-end patterns, and microservices. Node.js' package ecosystem, npm, provides access to a large collection of open source modules, providing a wide range of capabilities to accelerate your application development. | Express|
|JavaScript|JavaScript creates interactive effects in web pages. JavaScript along with HTML and CSS is the basis of most web pages. When wrapped with a Cordova plug-in, JavaScript code can take full advantage of native device functions. Developers with web skills can easily create mobile apps, and where appropriate app code can be reused across web and mobile.|Cordova|
|Python | [Python](../runtimes/python/getting-started.html) is a general-purpose, interpreted programming language that puts emphasis on readability. Python allows programmers implement functions with fewer lines of code than might be required in other languages. Features in the language make it possible to write object-oriented, functional, or imperative code. Python is commonly used for processing of natural language tasks. | Flask, Django|

