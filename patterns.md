---

copyright:
  years: 2016, 2023
lastupdated: "2023-01-27"

keywords: supported architecture, supported languages cloud, web app, microservices, mobile, programming languages, app types, common architecture, cloud app, developer console, app service

subcollection: apps

---

{{site.data.keyword.attribute-definition-list}}

# Common architectures for cloud apps
{: #patterns}

The {{site.data.keyword.cloud}} starter kits are deprecated. As of 18 February 2023, new applications cannot be created, and the starter kits will be removed from the catalog. For current users, existing apps will continue to operate and will be supported until the End of Support date on 31 March 2023. On this date, the Applications Details page will no longer be accessible, but you will still be able to access your application code and toolchains through your [{{site.data.keyword.cloud_notm}} Resource List](https://cloud.ibm.com/resources). For more information, see the [deprecation announcement](https://www.ibm.com/cloud/blog/announcements/deprecation-of-ibm-cloud-starter-kits){: external}.
{: deprecated}

Starter kits on {{site.data.keyword.cloud}} help you produce applications with a proven architecture. Apps are all different, but when you base your app on a known architectural pattern, it's easier to get a reliable result quickly. When you create an app from a starter kit, you’re choosing one of several different pattern types along with components to populate the pattern.
{: shortdesc}

## Web apps
{: #web}

The web app starter kits produce backend apps that serve web content such as HTML, JavaScript, and stylesheets to the web server. {{site.data.keyword.cloud_notm}} offers several web app starter kits.

* Basic - serves a static `index.html` file, default and empty stylesheet, and JavaScript file.
* React - a rich framework to build user interfaces. The source files are in `src/client/app`, and are compiled with WebPack and served in the public directory.

You can find starter kits on the [{{site.data.keyword.cloud_notm}} App Development console](/developer/appservice/starter-kits){: external}.

For more information, see [Creating an app with a starter kit](/docs/apps?topic=apps-tutorial-starterkit).

If you want to create a web app that you can customize, see [Creating a custom app from a basic starter kit](/docs/apps?topic=apps-tutorial-scratch).

## Microservice apps
{: #microservice}

Microservice apps provide the foundation for building backend microservices, including a basic health endpoint and REST API. Generated apps include all the dependencies required both for the microservice itself, and for any attached cloud service.

Select a microservice starter kit for your language and framework requirements. You can find starter kits on the [{{site.data.keyword.cloud_notm}} App Development console](/developer/appservice/starter-kits){: external}.

For more information, see [Creating microservice apps](/docs/apps?topic=apps-tutorial-microservice).

## Mobile apps
{: #mobile}

Mobile apps are different from the other patterns because they have a significant client-side component. The pattern might include direct connection to mobile services like push notifications, authentication, and mobile analytics. Mobile services are known as Mobile Backend as a Service or MBaaS pattern. They also might have a dedicated Backend-for-frontend.

{{site.data.keyword.cloud_notm}} offers mobile starter kits for iOS Swift and Android. You can find starter kits on the [{{site.data.keyword.cloud_notm}} App Development console](/developer/appservice/starter-kits){: external}.

Additionally, you can create a custom mobile app by using a basic starter kit and selecting the mobile app type.

For more information, see [Creating mobile apps](/docs/apps?topic=apps-tutorial-mobile).

## Language-based apps
{: #languages}

The starter kits that {{site.data.keyword.cloud_notm}} provides are available in various languages and frameworks. For example, cloud microservice starter kits that are closely related to data analysis might include Python.

|Programming language | Description | Development frameworks |
|-----|-----|-----|
|Python | [Python](https://github.com/IBM/python-django-app){: external} is a general-purpose, interpreted programming language that emphasizes readability. Python allows programmers to implement functions with fewer lines of code than might be required in other languages. Features in the language make it possible to write object-oriented, functional, or imperative code. Python is commonly used for processing of natural language tasks. | Flask, Django |
{: caption="Table 1. Languages that are used in starter kits" caption-side="top"}
