---

copyright:
  years: 2016, 2019
lastupdated: "2019-08-23"

keywords: supported architecture, supported languages cloud, web app, microservices, mobile, programming languages, app types, common architecture, cloud app, developer console, app service

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Common architectures for cloud apps
{: #patterns}

Starter kits on {{site.data.keyword.cloud_notm}} help you produce applications with a proven architecture. Apps are all different, but when you base your app on a known architectural pattern, it's easier to get a reliable result quickly. When you create an app from a starter kit, you’re choosing one of several different pattern types along with components to populate the pattern.
{: shortdesc}

## Web apps
{: #web}

The web app pattern produces backend apps that serve web content such as HTML, JavaScript, and stylesheets to the web server. {{site.data.keyword.cloud_notm}} offers several web app starter kits.

* Basic - serves a static `index.html` file, default and empty stylesheet, and JavaScript file.
* React - a rich framework to build user interfaces. The source files are in `src/client/app`, and are compiled with WebPack and served in the public directory.

You can find starter kits for web app pattern on the [{{site.data.keyword.cloud_notm}} App Service developer console](https://{DomainName}/developer/appservice/dashboard){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").

For more information, see [Creating an app with a starter kit](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit).

If you want to create a web app that you can customize, see [Creating a custom app from a basic starter kit](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch).

## Microservice apps
{: #microservice}

Microservice apps provide the foundation for building backend microservices, including a basic health endpoint and REST API. Generated apps include all the dependencies required both for the microservice itself, and for any attached cloud service.

Select a microservice starter kit for your language and framework requirements. You can find starter kits for the Microservice pattern on the [{{site.data.keyword.cloud_notm}} App Service developer console](https://{DomainName}/developer/appservice/dashboard){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").

For more information, see [Creating microservice apps](/docs/apps/tutorials?topic=creating-apps-tutorial-microservice).

## Mobile apps
{: #mobile}

Mobile apps are different from the other patterns because they have a significant client-side component. The pattern might include direct connection to mobile services like push notifications, authentication, and mobile analytics. Mobile services are known as Mobile Backend as a Service or MBaaS pattern. They also might have a dedicated Backend-for-frontend.

{{site.data.keyword.cloud_notm}} offers several mobile starter kits for iOS Swift and Android. You can find starter kits for the Mobile patterns on the [{{site.data.keyword.cloud_notm}} Mobile developer console](https://{DomainName}/developer/mobile/dashboard){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").

Additionally, you can create a custom mobile app by using a basic starter kit and selecting the mobile app type.

For more information, see [Creating mobile apps](/docs/apps?topic=creating-apps-tutorial-mobile).

## Language-based apps
{: #languages}

The starter kits that {{site.data.keyword.cloud_notm}} provides are available in various languages and frameworks. For example, cloud microservice starter kits offer a Node.js option, while starter kits that are closely related to data analysis might include Python or Go. Some common languages that are used in {{site.data.keyword.cloud_notm}} starter kits are discussed.

|Programming language | Description | Development frameworks |
|-----|-----|-----|
|Java&trade; | [Java](/docs/runtimes/liberty?topic=liberty-getting-started) is great for building enterprise-grade apps. But new features in Java 8, combined with lighter weight runtimes like Liberty and frameworks like Spring Boot, mean that Java is great for building microservices too. Java is a popular programming language for Android apps. | Spring, Liberty, Android |
|Swift | [Swift](/docs/runtimes/swift?topic=Swift-getting-started) is a modern programming language that was created in 2014 that was designed to replace Objective C and open-sourced in December of 2015. Today, it’s used to build iOS, macOS, web services, and systems software on Linux&trade; and macOS operating systems that use the x86, ARM, or z/Architecture. It writes like a scripting language but is compiled to gain C-like high performance with low processor usage. It's ideal for cloud runtimes. It uses a strong and static type system that you see in Java but the functional style and asynchronous routines that you see in JavaScript. It performs well, and the source compiles to native code that uses the LLVM compiler toolchain. It can use system libraries from other languages that are written in C easily. Since Swift can be used to code both client-side and server-side apps, developers use Swift when they need to easily migrate functions from the client to the server and back. | Kitura, iOS|
|Node.js | [Node.js](/docs/runtimes/nodejs?topicid=Nodejs-getting-started) is a JavaScript runtime that uses an event-driven, non-blocking I/O model, making it lightweight and efficient. It excels in throughput and scalability for web apps, backend-for-front-end patterns, and microservices. Node.js' package registry, `npm`, provides access to a large collection of open source modules. It provides a wide range of features to accelerate your app development. | Express|
|Python | [Python](/docs/runtimes/python?topic=Python-getting_started) is a general-purpose, interpreted programming language that emphasizes readability. Python allows programmers to implement functions with fewer lines of code than might be required in other languages. Features in the language make it possible to write object-oriented, functional, or imperative code. Python is commonly used for processing of natural language tasks. | Flask, Django |
{: caption="Table 1. Languages that are used in starter kits" caption-side="top"}
