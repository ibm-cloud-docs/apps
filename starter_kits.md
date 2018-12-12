---

copyright:
  years: 2018
lastupdated: "2018-11-14"

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

Starter kits are great for dynamically assembling a skeleton production app in the language of your choice that's ready for cloud deployment. Each starter kit has a language, a framework, and a pattern for a specific real-world use case. You can reuse code rather than reinvent it.

### Comparing samples and starter kits

Developers often rely on pre-written code such as snippets, demonstrations, and samples. How can you tell the difference between snippets, demonstrations, and samples and {{site.data.keyword.cloud_notm}} starter kits?

* **Snippet** - A few lines of code that is often presented in an IDE. Snippets help a developer integrate with a programming language syntax or support integration with a defined API.

* **Demonstration** - Code that is usually high quality, high fidelity, and uses a range of services and integration points. It often requires setup, and is used to prove a business problem or demonstrate a platform feature. Demonstrations can evaluate stages of cloud adoption. Sometimes, its code is included in production code.

* **Sample** - Code that is a small example of a specific feature, function, service, or user journey. A sample can be reused or included in a production application. You can use samples to show technical capabilities and possible approaches to solving technical problems.

* **{{site.data.keyword.cloud_notm}} starter kit** - Starter kits are production-ready patterns that you can integrate with a set of services to generate a production-ready asset. Then, you can deploy them directly to a DevOps pipeline and a Kubernetes cluster. A starter kit has descriptive metadata that provides you enough information to know what the kit is and does. It also has instructions that tell {{site.data.keyword.cloud_notm}} what to produce. The output can be enhanced further. Starter kit content isn't as complex as a demonstration and not as trivial as a snippet or sample. Starter kits are dynamically created based on your requirements.

  Starter kits show key pattern implementation with a runtime, for example Swift and Kitura. They can include a simple user experience to highlight the integration of the service. Starter kits are customizable implementations of a sophisticated use case.

  Starter kits include instructions that allow {{site.data.keyword.cloud_notm}} to automatically produce scaffolded app projects with portable code. They also specify resources to be auto-provisioned when you create a project.

## Auto-provisioned resources
{: #auto_privisioned_resources}

If a starter kit specifies required resources, {{site.data.keyword.cloud_notm}} automatically creates instances of those resources when you create your project. You can manually provision resources or select existing resource instances to augment your project after it is created. You can see a list of service instances that are associated with your project in the *Project Details* view, along with credentials in case you need them.

## Generating portable code
{: #portable_code}

Creating an app from a starter kit automatically produces code for you that has consistent format and is runtime independent. You can deploy the code in your environment of choice, for example, Kubernetes or Cloud Foundry, without making changes.

The project includes a `README` file that has technical details of the project and explains what you need to get your app ready to run.

For more information, see the [{{site.data.keyword.cloud_notm}} developer console for Apple learning resources](https://cloud.ibm.com/developer/appledevelopment/learning-resources).
{: tip}

### What app content is produced?
{: #content}

The code the {{site.data.keyword.cloud_notm}} starter kit produces has four fundamental components: use case logic, language components, service enablement, and cloud enablement. Generating these components saves you valuable time and ensures that you're using best-in-class architecture.

* **Use case logic** is the code for a particular use case. Examples include code for a Watson Conversation chat bot, or code that is for a mobile visual recognition app.
* **Language components** are code components, and files specific to the language you select for your starter kit. For example, node.js programmers need a `package.json` file for dependency management, and this file is automatically created by the {{site.data.keyword.cloud_notm}} Developer Experience.
* **Service enablement** is code that allows your app to connect your project and use the services that you added to it. Examples of service enablement items are credential management, initialization code, and service-specific SDKs.
* **Cloud enablement** is code that enables your app to run on {{site.data.keyword.cloud_notm}}. For example, Helm charts allow your app to run on an {{site.data.keyword.cloud_notm}} Kubernetes cluster would fall in the cloud enablement category.

The app that {{site.data.keyword.cloud_notm}} produces is architecturally sound and models best practices for the language you chose for your project. To see details on the files and structure of an app project, see the following topics.

* [Java app files](/docs/apps/projects/java_project_contents.html)
* [Node.js app files](/docs/apps/projects/node_project_contents.html)
* [Python app files](/docs/apps/projects/python_project_contents.html)
* [Swift app files](/docs/apps/projects/swift_project_contents.html).