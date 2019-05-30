---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-30"

keywords: getting started apps, create app tutorial, add services, deploy apps, create app, app tutorial

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Getting started tutorial
{: #tutorial-getting-started}

You can build enterprise-ready mobile and web applications in {{site.data.keyword.cloud}} and take advantage of cloud extensions that are hosted by {{site.data.keyword.cloud_notm}}. You have several options for getting started. Create an app with a starter kit that manages the process for you, or if you know what you want, start from scratch and build your app with the resources you need, or use your existing repository and bring your own code.
{: shortdesc}

Whether you have [existing code](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc) that you want to modernize and bring to the cloud, or you're developing a [brand new application](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit), you can tap into the rapidly growing ecosystem of available services and runtime frameworks in {{site.data.keyword.cloud_notm}}.

Do you need help with deciding where to start? The following diagram provides an overview for creating apps, whether you use a starter kit or bring your own code to {{site.data.keyword.cloud_notm}}.

![Developer experience overview](images/dev-journey.png "Overview of creating apps in {{site.data.keyword.cloud_notm}}")

Figure 1. Overview of creating apps in {{site.data.keyword.cloud_notm}}

## Before you begin
{: #prereqs-getting-started}

You can create your app by using the {{site.data.keyword.cloud_notm}} console or the command-line interface (CLI). If you want to use the CLI, see the [installing steps](/docs/cli?topic=cloud-cli-ibmcloud-cli).

## Step 1. Create your app
{: #create-getting-started}

Create an app by selecting one of the following entry points:

* [Starter kits](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit) are use-case-specific and produce production-ready apps in various programming languages and architectural patterns.
* [IBM Developer code patterns ![External link icon](../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/patterns/){:new_window} help you quickly create your app and deploy it to {{site.data.keyword.cloud_notm}}. For more information, see [Code patterns](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern).
* [Bring your own code](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc) by linking to your own existing content repository. Your app and Docker image must be located in the same repo.
* If you know what you want, build a [custom app](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch) from scratch with the services that you need by using a blank starter kit.
* Create and deploy a custom or starter kit app by using the [CLI and developer tools](/docs/apps?topic=creating-apps-create-deploy-app-cli).
* Browse or search the [{{site.data.keyword.cloud_notm}} catalog](https://{DomainName}/catalog){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") for apps and services that you can create and start using today.

## Step 2. Add services
{: #resources-getting-started}

When you use a starter kit to create your app, the mandatory services are automatically created for you. You can connect more services to your app in the console from the **App details** page, which is displayed as soon as you create the app.

If you want to add services after your app is created, go to the [{{site.data.keyword.cloud_notm}} dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}), locate your app, and then click your app's name. The **App details** page is displayed, and you can create a service instance or connect existing services.

Or, you can run the following command to add a service to your app by using the CLI. You can select an existing service that is already enabled on your account, or you can add a service.
```
ibmcloud dev edit
```
{: codeblock}

For more information, see [Adding a service to your app](/docs/apps?topic=creating-apps-add-resource).

## Step 3. Deploy your app
{: #deploy-getting-started}

You can deploy your app by using the console or the CLI.

### Using the console
{: #console-getting-started}

To deploy your app by using the console, complete the following steps:

1. On the **App details** page, click **Configure continuous delivery**.
2. Select a deployment target, select the toolchain settings, and click **Create**. {{site.data.keyword.cloud_notm}} automatically creates an open toolchain complete with a Git repository and continuous delivery pipeline.
3. Open the pipeline stage of your new toolchain to view the build and deployment process so that you can view your new app in minutes.

For more information, see the table of contents for various deployment topics in the "Deploying and integrating apps" section.

### Using the CLI
{: #cli-getting-started}

To deploy your app by using the CLI, run the `ibmcloud dev deploy` command. For more information, see [Creating and deploying apps by using the CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli).

Now you're set for iterative development and continuous delivery.

For more information about deploying your app, see [Deploying apps](/docs/apps?topic=creating-apps-deploying-apps).

## Related information
{: #related-getting-started}

[Programming guides](https://{DomainName}/docs/home/build){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") are available per language to help you get up and running. You have many options for hosting your apps with {{site.data.keyword.cloud_notm}} infrastructure from {{site.data.keyword.baremetal_short}} to running as a serverless function.
