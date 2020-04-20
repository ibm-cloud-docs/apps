---

copyright:
  years: 2016, 2020
lastupdated: "2020-04-20"

keywords: supported architecture, supported languages cloud, web app, microservices, mobile, programming languages, app types, common architecture, cloud app, developer console, app service

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}
{:external: target="_blank" .external}

# Common architectures for cloud apps
{: #patterns}

Starter kits on {{site.data.keyword.cloud}} help you produce applications with a proven architecture. Apps are all different, but when you base your app on a known architectural pattern, it's easier to get a reliable result quickly. When you create an app from a starter kit, you’re choosing one of several different pattern types along with components to populate the pattern.
{: shortdesc}

## Web apps
{: #web}

The web app starter kits produce backend apps that serve web content such as HTML, JavaScript, and stylesheets to the web server. {{site.data.keyword.cloud_notm}} offers several web app starter kits.

* Basic - serves a static `index.html` file, default and empty stylesheet, and JavaScript file.
* React - a rich framework to build user interfaces. The source files are in `src/client/app`, and are compiled with WebPack and served in the public directory.

You can find starter kits on the [{{site.data.keyword.cloud_notm}} App Development console](https://{DomainName}/developer/appservice/starter-kits){: external}.

For more information, see [Creating an app with a starter kit](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit).

If you want to create a web app that you can customize, see [Creating a custom app from a basic starter kit](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch).

## Microservice apps
{: #microservice}

Microservice apps provide the foundation for building backend microservices, including a basic health endpoint and REST API. Generated apps include all the dependencies required both for the microservice itself, and for any attached cloud service.

Select a microservice starter kit for your language and framework requirements. You can find starter kits on the [{{site.data.keyword.cloud_notm}} App Development console](https://{DomainName}/developer/appservice/starter-kits){: external}.

For more information, see [Creating microservice apps](/docs/apps/tutorials?topic=creating-apps-tutorial-microservice).

## Mobile apps
{: #mobile}

Mobile apps are different from the other patterns because they have a significant client-side component. The pattern might include direct connection to mobile services like push notifications, authentication, and mobile analytics. Mobile services are known as Mobile Backend as a Service or MBaaS pattern. They also might have a dedicated Backend-for-frontend.

{{site.data.keyword.cloud_notm}} offers mobile starter kits for iOS Swift and Android. You can find starter kits on the [{{site.data.keyword.cloud_notm}} App Development console](https://{DomainName}/developer/appservice/starter-kits){: external}.

Additionally, you can create a custom mobile app by using a basic starter kit and selecting the mobile app type.

For more information, see [Creating mobile apps](/docs/apps?topic=creating-apps-tutorial-mobile).

## Language-based apps
{: #languages}

The starter kits that {{site.data.keyword.cloud_notm}} provides are available in various languages and frameworks. For example, cloud microservice starter kits offer a Node.js option, while starter kits that are closely related to data analysis might include Python or Go. Some common languages that are used in {{site.data.keyword.cloud_notm}} starter kits are discussed.

|Programming language | Description | Development frameworks |
|-----|-----|-----|
|Go | [Go](/docs/go?topic=go-getting-started), also known as Golang, is a fast, statically typed, compiled programming language that is syntactically similar to C, but with memory safety, garbage collection, structural typing, and CSP-style concurrency. Go is expressive, concise, clean, and efficient. Its concurrency mechanisms make it easy to write programs that get the most out of multi-core and networked machines, while its novel type system enables flexible and modular program construction. Go compiles quickly to machine code, has the convenience of garbage collection, and the power of run time reflection. | Gin |
|Java&trade; | [Java](/docs/java?topic=java-getting-started) is great for building enterprise-grade apps. But new features in Java 8, combined with lighter weight runtimes like Liberty and frameworks like Spring Boot, mean that Java is great for building microservices too. Java is a popular programming language for Android apps. | Spring, Liberty, Android |
|Node.js | [Node.js](/docs/node?topic=nodejs-getting-started) is a JavaScript runtime that uses an event-driven, non-blocking I/O model, making it lightweight and efficient. It excels in throughput and scalability for web apps, backend-for-front-end patterns, and microservices. Node.js' package registry, `npm`, provides access to a large collection of open source modules. It provides a wide range of features to accelerate your app development. | Express|
|Python | [Python](/docs/cloud-foundry-public?topic=cloud-foundry-getting-started-python) is a general-purpose, interpreted programming language that emphasizes readability. Python allows programmers to implement functions with fewer lines of code than might be required in other languages. Features in the language make it possible to write object-oriented, functional, or imperative code. Python is commonly used for processing of natural language tasks. | Flask, Django |
|Swift | [Swift](/docs/swift?topic=swift-getting-started) is a modern programming language that was created in 2014 that was designed to replace Objective C and open-sourced in December of 2015. Today, it’s used to build iOS, macOS, web services, and systems software on Linux&trade; and macOS operating systems that use the x86, ARM, or z/Architecture. It writes like a scripting language but is compiled to gain C-like high performance with low processor usage. It's ideal for cloud runtimes. It uses a strong and static type system that you see in Java but the functional style and asynchronous routines that you see in JavaScript. It performs well, and the source compiles to native code that uses the LLVM compiler toolchain. It can use system libraries from other languages that are written in C easily. Since Swift can be used to code both client-side and server-side apps, developers use Swift when they need to easily migrate functions from the client to the server and back. | Kitura, iOS|
{: caption="Table 1. Languages that are used in starter kits" caption-side="top"}
