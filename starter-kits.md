---

copyright:
  years: 2019, 2023
lastupdated: "2023-01-20"

keywords: developer tools, building apps, developer entry point, get started coding, starter kit

subcollection: apps

---

{{site.data.keyword.attribute-definition-list}}

# What are starter kits?
{: #starter-kits}

The {{site.data.keyword.cloud}} starter kits are deprecated. As of 18 February 2023, new applications cannot be created, and the starter kits will be removed from the catalog. For current users, existing apps will continue to operate and will be supported until the End of Support date on 31 March 2023. On this date, the Applications Details page will no longer be accessible, but you will still be able to access your application code and toolchains through your [{{site.data.keyword.cloud_notm}} Resource List](https://cloud.ibm.com/resources). For more information, see the [deprecation announcement](https://www.ibm.com/cloud/blog/announcements/deprecation-of-ibm-cloud-starter-kits){: external}.
{: deprecated}

A starter kit is an application pattern that can be integrated with services to generate a production-ready asset, which can be deployed directly into a DevOps pipeline and a Kubernetes cluster. Starter kits are great for dynamically assembling a skeleton production application in the language of your choice that's ready for cloud deployment. 
{: shortdesc}

A starter kit contains metadata that describes what the kit is and does. It also contains information that informs {{site.data.keyword.cloud_notm}} what to produce. The output is production-ready out of the box, and can be iterated on for further enhancements based on {{site.data.keyword.cloud_notm}} best practices. Starter kit content isn’t as complex as a demonstration and not as trivial as a snippet or sample. Apps are dynamically created based on the developer’s requirements.

Each starter kit includes a language, a framework, and a pattern for a specific use case. You can reuse code rather than reinvent it. If a starter kit requires specific services, the auto-provisioned service instances are automatically created and connected to your app.

## How are starter kits different from samples?
{: #compare}

Starter kits are production-ready and focus on demonstrating a key pattern implementation by using a runtime (for example, Node.js and Express). In some cases, starter kits offer a simple user experience to highlight the integration of the service. In other cases, starter kits represent a customizable implementation of a sophisticated use case.

A snippet is a few lines of code that is often presented in an IDE. Snippets help a developer integrate with a programming language syntax or support integration with a defined API. A demonstration is usually high in quality and fidelity and uses a range of services and integration points. It often requires setup time and is used to prove a business problem or demonstrate a platform feature. You can use it for evaluating stages of cloud adoption. Sometimes it's code that is included in production code. A sample is a small example of a specific feature, function, service, or user journey. You can reuse a sample or include it in a production app. Samples are typically used to show technical capabilities and a possible approach to solving a technical problem.

## Portable code
{: #portable-code}

Creating an app from a starter kit automatically creates code for you that has consistent format and isn't dependent on the runtime. You can deploy the code into your target of choice without making changes.

Portable code contains cloud enablement code for multiple cloud environments. You can produce code that follows best practices for a specific language and is specific to a use case. 

* Use case logic provides functions for the core function of a particular use case. Examples might be code for a Watson Conversation chat bot.
* Language components are code components and files specific to the programming language you select for your starter kit. For example, node.js programmers need a package.json file for dependency management, and this file is automatically created for you.
* Service enablement is code that enables your app to connect to and use the services you add. Credential management, initialization code, and service-specific SDKs are examples of service enablement items.
* Cloud enablement is code that enables your app to run on {{site.data.keyword.cloud_notm}}. For example, Helm charts that enable your app to run on an {{site.data.keyword.cloud_notm}} Kubernetes cluster.

You can view your app code by clicking **View source code** on the App details page of your app.

Each app includes a readme file that contains technical details of the app and explains what is needed to get your app started if it doesn't already start successfully.
{: tip}
