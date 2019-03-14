---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-14"

keywords: apps, credentials

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# Credentials overview
{: #credentials_overview}

Learn how to manually add service credentials to your deployment environment.
{: shortdesc}

In general, you want your application logic to acquire sensitive service credentials, such as database API keys or passwords, from the environment in which your application runs. That way, you don't keep credentials in your source code repository. Databases in your continuous integration, pre-production, and production environments are quarantined from each other.

If you create an app by using a starter kit template, the environment is prepared for you automatically. No matter if your deployment target is:
  * [Kubernetes](/docs/apps/creds_kube.html#add-credentials-kube)
  * [Cloud Foundry Public or Cloud Foundry Enterprise Environment](/docs/apps/creds_cf.html#add-credentials-cf)
  * [Virtual Server Instance (also local docker)](/docs/apps/creds_vsi.html#add-credentials-vsi)
  
The steps are provided for how to configure the environment. Starter kits generate code that uses a dependent library to make the code portable to run on any of the deployment targets. Lastly, no branch logic is used to detect in which deployment target the application is running.

The administrator or DevOps engineer is then responsible for preparing the environments with the proper access controls and configurations to make the values that are required by your application available to it.

"Deploy to cloud" is a one-time step that does the following key tasks:
 * Prepares your target deployment environment with services, resources, and credentials.
 * Creates a DevOps toolchain to build and deploy your app into that environment, by using code that correctly references the credentials in the environment.

However, you must prepare the target deployment environment in any of the following scenarios:
 * You bring your own code.
 * You start from a blank starter kit template.
 * You add a service to a starter kit-based app after it was deployed.




