---

copyright:
  years: 2018
lastupdated: "2018-07-05"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# App development
{: #intro}

The {{site.data.keyword.cloud_notm}} Developer Console helps developers create apps from starter kits, provision and connect key {{site.data.keyword.cloud_notm}}-optimized services, and then quickly download working code or set up for continuous delivery. You can create, view, configure, and manage your app and download your app's code. Using starter kits helps you to quickly evaluate, and test {{site.data.keyword.cloud_notm}} services with a sample app.
{:shortdesc}

## What is a starter kit?
{: #starter_kits}

Starter kits are great for dynamically assembling a skeleton production app in the language of your choice that's ready for cloud deployment. Each starter kit contains a language, a framework, and a pattern for a specific real-world use case that allows reusing code rather than re-inventing it.

### Comparing samples and starter kits

Developers often rely on pre-written code like snippets, demos, and samples. How are these different from {{site.data.keyword.cloud_notm}} starter kits?

* **snippet** - A few lines of code that is often presented in an IDE. Snippets help a developer integrate with a programming language syntax or support integration with a defined API.

* **demo** - Code that is usually high quality, high fidelity, and uses a range of services and integration points. It often requires setup, and is used to prove a business problem or demonstrate a platform feature. It is used for evaluating stages of cloud adoption. Sometimes its code is included in production code.

* **sample** - Code that is a small example of a specific feature, function, service, or user journey. A sample can be reused or included in a production application. It is typically used to show technical capabilities, and a possible approach to solving a technical problem.

* **{{site.data.keyword.cloud_notm}} starter kit** - Starter kits are production-ready patterns that you can integrate with a set of services to generate a production-ready asset and deploy directly to a devops pipeline and a Kubernetes cluster. A starter kit contains descriptive metadata that provides you enough information to know what the kit is and does. It also contains instructions that tell {{site.data.keyword.cloud_notm}} what to produce. The output can be enhanced further. Starter kit content is not as complex as a demo and not as trivial as a snippet or sample. They are dynamically created based on your requirements.

  Starter kits focus on demonstrating a key pattern implementation by using a runtime, for example Swift and Kitura. In some cases, starter kits offer a simple user experience to highlight the integration of the service. In other cases, stater kits represent a customizable implementation of a sophisticated use case.

  Starter kits contain instructions that allow {{site.data.keyword.cloud_notm}} to automatically produce scaffolded app projects with portable code, and specify resources to be auto-provisioned when you create a project from the starter kit.

## Auto-provisioned resources
{: #auto_privisioned_resources}

If a starter kit specifies required resources, {{site.data.keyword.cloud_notm}} automatically creates instances of those resources when you create your project. You can manually provision resources or select existing resource instances to augment your project after it is created. You can see a list of service instances that are associated with your project in the *Project Details* view, along with credentials in case you need them.

## Generating portable code
{: #portable_code}

Creating an app from a starter kit automatically produces code for you that has consistent format and is runtime agnostic. You can deploy the code in your environment of choice, for example, Kubernetes or Cloud Foundry, without making changes.

The project includes a `README` file that contains technical details of the project, and explains what is needed to get your app to run if it does not run out-of-the-box.

For more information, see the [{{site.data.keyword.cloud_notm}} developer console for Apple learning resources](https://console.bluemix.net/developer/appledevelopment/learning-resources).
{: tip}

### What app content is produced?
{: #content}

The code that is produced from an {{site.data.keyword.cloud_notm}} starter kit has four fundamental components: use case logic, language components, service enablement, and cloud enablement. Generating these components saves you valuable time and ensures that you are using best-in-class architecture.

* **Use case logic** is the code for a particular use case. Examples include code for a Watson Conversation chat bot, or code that is for a mobile visual recognition app.
* **Language components** are code components, and files specific to the language you select for your starter kit. For example, node.js programmers need a `package.json` file for dependency management, and this file is automatically created by the {{site.data.keyword.cloud_notm}} Developer Experience.
* **Service enablement** is code that allows your app to connect your project and use the services that you added to it. Examples of service enablement items are credential management, initialization code, and service-specific SDKs.
* **Cloud enablement** is code that enables your app to run on {{site.data.keyword.cloud_notm}}. For example, Helm charts allow your app to run on an {{site.data.keyword.cloud_notm}} Kubernetes cluster would fall in the cloud enablement category.

The app that is produced by {{site.data.keyword.cloud_notm}} is not only architecturally proven, but also reflects best practices for the language you chose for your project. To see details on the files and structure of an app project, see the *Project contents* topic in the Reference section of this document.
