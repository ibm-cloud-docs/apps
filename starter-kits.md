---

copyright:
  years: 2019
lastupdated: "2019-04-25"

keywords: developer tools, building apps, developer entry point, get started coding, starter kit

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# What are starter kits?
{: #starter-kits}

A starter kit is a production-ready pattern that can be integrated with a set of services to generate a production-ready asset that can be deployed directly into a DevOps pipeline and a Kubernetes cluster.
{:shortdesc}

## What can you do with a starter kit?
{: #starter-overview}

Starter kits are great for dynamically assembling a skeleton production application in the language of your choice that's ready for cloud deployment. 

A starter kit contains descriptive metadata that provides the user with enough information to know what the kit is and does. It also contains instructions that tell {{site.data.keyword.cloud_notm}} what to produce. The output is production-ready out of the box, and can be iterated on for further enhancements, based on {{site.data.keyword.cloud_notm}} best practices. Starter kit content isn’t as complex as a demonstration and not as trivial as a snippet or sample. Apps are dynamically created based on the developer’s requirements.

Each starter kit includes a language, a framework, and a pattern for a specific use case. You can reuse code rather than reinvent it. If a starter kit requires specific services, no problem. With auto-provisioned services, {{site.data.keyword.cloud_notm}} automatically creates instances for those services when you create your app. You can access starter kits from the {{site.data.keyword.cloud_notm}} dashboard or command-line interface.

Check out the instructions for [creating an app with a starter kit](/docs/apps?topic=creating-apps-tutorial-starterkit).

## How are starter kits different from samples?
Starter kits are production-ready and focus on demonstrating a key pattern implementation by using a runtime (for example, Node.js and Express). In some cases, starter kits offer a simple user experience to highlight the integration of the service. In other cases, starter kits represent a customizable implementation of a sophisticated use case.

* A snippet is a few lines of code that is often presented in an IDE. Snippets help a developer integrate with a programming language syntax or support integration with a defined API.
* A demonstration is usually high in quality and fidelity and uses a range of services and integration points. It often requires setup time and is used to prove a business problem or demonstrate a platform feature. You can use it for evaluating stages of cloud adoption. Sometimes it's code that is included in production code.
* A sample is a small example of a specific feature, function, service, or user journey. You can reuse a sample or include it in a production application. It's typically used to show technical capabilities and a possible approach to solving a technical problem.

## Portable code
{: #portable-code}

Creating an app from a starter kit automatically creates code for you that has consistent format and isn't dependent on the runtime. You can deploy the code into your target of choice, such as Kubernetes or Cloud Foundry, without making changes.

You can get a quick look at your app code by clicking **Download code** on the **App details** page of your app. Your code is downloaded as a `.zip` file that contains the complete app code structure. You can easily extract the file and run the code locally by using the {{site.data.keyword.dev_cli_notm}}, or add it to your code management repository.

### What code is created?
{: #what-code}

When you create an app directly or with help from a starter kit, the app contains portable code. Portable code contains cloud enablement code for multiple cloud environments. You can then produce code in four foundational areas:
* Code that follows best practices for a specific language
* Code that enables the app to run on the cloud
* Code that's initialized to connect to cloud services
* Code that's specific to a use case

Generating these components saves you valuable time and ensures that you’re using best-in-class architecture.

* Use case logic provides functions for the core function of a particular use case. Examples might be code for a Watson Conversation chat bot, or code for a mobile visual recognition app.
* Language components are code components and files specific to the programming language you select for your starter kit. For example, node.js programmers need a package.json file for dependency management, and this file is automatically created for you.
* Service enablement is code that enables your app to connect to and use the services you add. Credential management, initialization code, and service-specific SDKs are examples of service enablement items.
* Cloud enablement is code that enables your app to run on {{site.data.keyword.cloud_notm}}. For example, Helm charts that enable your app to run on an {{site.data.keyword.cloud_notm}} Kubernetes cluster.

When you create an app from an {{site.data.keyword.cloud_notm}} starter kit, your app starts with proven architecture that also reflects best practices for the language you selected.

Each app includes a readme file that contains technical details of the app and explains what is needed to get your app running if it doesn’t run out-of-the-box.
{: tip}
