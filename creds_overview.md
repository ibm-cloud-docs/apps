---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-25"

keywords: apps, credentials, service, add service credentials, environment, deployment

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# Adding service credentials to your deployment environment
{: #credentials_overview}

Learn how to manually add service credentials to your deployment environment.
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

In general, you want your application logic to acquire sensitive service credentials, such as database API keys or passwords, from the environment in which your application runs. That way, you don't keep credentials in your source code repository. Databases in your continuous integration, pre-production, and production environments are quarantined from each other.

If you create an app by using a starter kit template, the environment is prepared for you automatically. No matter if your deployment target is:
<!-- Add links to the new topics in the /docs/resources repo when available-->
  * Kubernetes
  * Cloud Foundry Public or Cloud Foundry Enterprise Environment
  * Virtual Server Instance (also local docker)
  
The steps are provided for how to configure the environment. Starter kits generate code that uses a dependent library to make the code portable to run on any of the deployment targets. Lastly, no branch logic is used to detect in which deployment target the application is running.

The administrator or DevOps engineer is then responsible for preparing the environments with the proper access controls and configurations to make the values that are required by your application available to it.

"Configure continuous delivery" is a one-time step that does the following key tasks:
 * Prepares your deployment target with services, resources, and credentials.
 * Creates a DevOps toolchain to build and deploy your app into that environment, by using code that correctly references the credentials in the environment.

However, you must prepare the deployment target in any of the following scenarios:
 * You bring your own code.
 * You start from a blank starter kit template.
 * You add a service to a starter kit-based app after it was deployed.

Environment preparation is always performed for all credentials for all services that are associated with an app, and all `services` are listed in the `manifest.yml`, but not all credential references are placed in the `mappings.json` file. In these cases, you're required to place such references yourself. After you decide on a deployment target, and don't need the abstraction of the `IBMCloudEnv` library, refer to the "Your code + (deployment target)" section that fits with your decision.
{: important}

Some starter kits don't include the reference to the `IBMCloudEnv` dependency, the `manifest.yml`, or the `mappings.json` files at all.
{: important}
