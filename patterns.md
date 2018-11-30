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

# Common architectures for cloud apps
{: #patterns}

Starter kits on {{site.data.keyword.cloud_notm}} help you produce apps with a proven architecture. Apps are all different, but when you base your app on a known architectural pattern, it's easier to get a reliable result quickly. When you create an app from a starter kit, you’re choosing one of several different pattern types along with components, like a runtime, to populate the pattern.
{:shortdesc}

## Web App
{: #web}

The web app pattern produces apps that serve web content such as HTML, JavaScript, and stylesheets to the web server. {{site.data.keyword.cloud_notm}} offers several web app starter kits.

* Basic - serves a static `index.html` file, default and empty stylesheet, and JavaScript file.
* React - a rich framework to build user interfaces. The source files are in `src/client/app`, and are compiled with WebPack and served in the public directory.

You can find starter kits for web app pattern on the [{{site.data.keyword.cloud_notm}} App Service developer dashboard](https://{DomainName}/developer/appservice/dashboard).

## Backend-for-frontend
{: #bff}

Backendf-for-frontend pattern (BFF) helps create backend code that exposes business data and services in a way that matches user expectations for a specific app channel, such as mobile or web. For example, users on a mobile device might use voice control, while web browser users prefer point and click. You can build two BFFs, one for mobile that includes services like [{{site.data.keyword.conversationfull}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/ai-assistant/) and one for web that has a more sophisticated user interface.

In {{site.data.keyword.cloud_notm}}, you can build a BFF with polyglot programming approach. You can use Node.js, Swift, Java, or Python and running them in a pattern with container services or that use serverless functions.

The BFF manages data persistence, caching, and integration with the following high-value services.

* [{{site.data.keyword.ibmwatson}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=watson)
* [{{site.data.keyword.iot_short_notm}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=iot)
* [{{site.data.keyword.weather_short}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}/catalog/services/weather-company-data?taxonomyNavigation=apps)
* [{{site.data.keyword.sparks}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://{DomainName}/catalog/services/apache-spark?taxonomyNavigation=apps).

The BFF exposes an API most commonly by using a REST pattern, but you can design your BFF to work from a messaging architecture that uses {{site.data.keyword.messagehub}}.

Choose a BFF starter kit for your language and framework requirements. You can find starter kits for BFF pattern on the [{{site.data.keyword.cloud_notm}} App Service developer dashboard](https://{DomainName}/developer/appservice/dashboard).

## Microservice
{: #microservice}

Microservice apps provide the foundation for building backend microservices, including a basic health endpoint and REST API. Generated apps include all the dependencies required both for the microservice itself, and for any attached cloud service.

Choose a micro-service starter kit for your language and framework requirements. You can find starter kits for Microservice pattern on the [{{site.data.keyword.cloud_notm}} App Service developer dashboard](https://{DomainName}/developer/appservice/dashboard).

## Mobile
{: #mobile}

Mobile apps are different from the other patterns because they have a significant client-side component. The pattern might include direct connection to mobile services like push notifications, authentication, and mobile analytics. Mobile services are known as Mobile Backend as a Service or MBaaS pattern. They also might have a dedicated [Backend-for-frontend](#bff).

{{site.data.keyword.cloud_notm}} offers several mobile starter kits for iOS Swift, Android, and Cordova. You can find starter kits for Mobile pattern on the [{{site.data.keyword.cloud_notm}} Mobile developer dashboard](https://{DomainName}/developer/mobile/dashboard).

## Languages
{: #languages}

The starter kits {{site.data.keyword.cloud_notm}} provides are available in various languages and frameworks. For example, cloud microservice starter kits offer a Node.js option, while starter kits closely related to data analysis might include Python or Go. Some common languages that are used in {{site.data.keyword.cloud_notm}} starter kits are discussed.

|Programming language | Description | Development frameworks |
|-----|-----|-----|
|Java | [Java](../runtimes/liberty/getting-started.html) is great for building enterprise-grade applications. But new features in Java 8, combined with lighter weight runtimes like Liberty and frameworks like Spring Boot, mean that Java is great for building microservices too. Java is a popular programming language for Android apps. | Spring, Liberty, Android |
|Swift | [Swift](../runtimes/swift/getting-started.html) is a modern programming language that was created in 2014 that was designed to replace Objective C and open-sourced in December of 2015. Today, it’s used to build iOS, macOS, web services, and systems software on Linux and macOS operating systems that use the x86, ARM, or z/Architecture. It writes like a scripting language but is compiled to gain C-like high performance with low processor usage. It's ideal for cloud runtimes. It uses a strong and static type system that you see in Java but the functional style and asynchronous routines that you see in JavaScript. It performs well, and the source compiles to native code that uses the LLVM compiler toolchain. It can use system libraries from other languages that are written in C easily. Since Swift can be used to code both client-side and server-side apps, developers use Swift when they need to easily migrate functions from the client to the server and back. | Kitura, iOS|
|Node.js | [Node.js](../runtimes/nodejs/getting-started.html) is a JavaScript runtime that uses an event-driven, non-blocking I/O model, making it lightweight and efficient. It excels in throughput and scalability for web applications, backend-for-front-end patterns, and microservices. Node.js' package registry, npm, provides access to a large collection of open source modules. It provides a wide range of features to accelerate your application development. | Express|
|JavaScript|JavaScript creates interactive effects in web pages. JavaScript along with HTML and CSS is the basis of most web pages. When wrapped with a Cordova plug-in, JavaScript code can take full advantage of native device functions. Developers with web skills can easily create mobile apps, and where appropriate app code can be reused across web and mobile.|Cordova|
|Python | [Python](../runtimes/python/getting-started.html) is a general-purpose, interpreted programming language that emphasizes readability. Python allows programmers to implement functions with fewer lines of code than might be required in other languages. Features in the language make it possible to write object-oriented, functional, or imperative code. Python is commonly used for processing of natural language tasks. | Flask, Django|

