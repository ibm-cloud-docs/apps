---

copyright:
  years: 2018, 2020
lastupdated: "2020-09-10"

keywords: getting started apps, create app tutorial, add services, deploy apps, create app, app tutorial

subcollection: apps
content-type: tutorial
account-plan: lite
completion-time: 15m

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:script: data-hd-video='script'}
{:external: target="_blank" .external}
{:step: data-tutorial-type='step'}

# Getting started tutorial
{: #getting-started}
{: toc-content-type="tutorial"}
{: toc-completion-time="15m"}

You can build enterprise-ready mobile and web applications in {{site.data.keyword.cloud}} and take advantage of cloud extensions that are hosted by {{site.data.keyword.cloud_notm}}. You have several options for getting started. Create an app with a starter kit that manages the process for you, or if you know what you want, start from scratch and build your app with the resources you need. Or, use your existing repository and bring your own code.
{: shortdesc}

Whether you have [existing code](/docs/apps/tutorials?topic=apps-tutorial-byoc) that you want to modernize and bring to the cloud, or you're developing a [brand new application](/docs/apps/tutorials?topic=apps-tutorial-starterkit), you can tap into the rapidly growing ecosystem of available services and runtime frameworks in {{site.data.keyword.cloud_notm}}.

Do you need help with deciding where to start? The following diagram provides an overview for creating apps, whether you use a starter kit or bring your own code to {{site.data.keyword.cloud_notm}}.

You can create your app by using the {{site.data.keyword.cloud_notm}} console or the command-line interface (CLI). If you want to use the CLI, see the [installing steps](/docs/cli?topic=cli-getting-started).

![Developer experience overview](images/dev-journey.png "Overview of creating apps in {{site.data.keyword.cloud_notm}}"){: caption="Figure 1. Overview of creating apps in {{site.data.keyword.cloud_notm}}" caption-side="bottom"}

## Before you begin
{: #prereqs-getting-started}

* Depending on your [{{site.data.keyword.cloud}} account type](https://{DomainName}/registration), access to certain resources might be limited or constrained. Depending on your plan limits, certain capabilities that are required by some toolchains might not be available. For more information, see [Setting up your IBM Cloud account](/docs/account?topic=account-account-getting-started).
* Install the [{{site.data.keyword.cloud_notm}} Command Line Interface (CLI)](/docs/cli?topic=cli-getting-started), which includes the {{site.data.keyword.dev_cli_short}} (`ibmcloud dev`) commands.
* Create a Docker account, run the Docker app, and sign in. Docker is installed as part of the developer tools. Docker must be running for the build commands to work.

## Create your app
{: #create-getting-started}
{: step}

Create an app by selecting one of the following entry points:

* [Preconfigured starter kits](/docs/apps/tutorials?topic=apps-tutorial-starterkit) are use-case-specific and give you production-ready apps in various programming languages and architectural patterns.
* [Blank starter kits](/docs/apps/tutorials?topic=apps-tutorial-scratch) build apps based on your selection for type of app (mobile or backend), language and framework, services, and deployment target.
* [Bring your own code](/docs/apps/tutorials?topic=apps-tutorial-byoc) by linking to your own existing content repository. Your app and Docker image must be located in the same repo.
* [{{site.data.keyword.cloud_notm}} (CLI)](/docs/apps?topic=apps-create-deploy-app-cli) creates and deploys your apps by using the {{site.data.keyword.dev_cli_short}} (`ibmcloud dev`) commands.
* Browse or search the [{{site.data.keyword.cloud_notm}} catalog](https://{DomainName}/catalog){: external} for apps and services that you can create and use today.
* [IBM Developer code patterns](https://developer.ibm.com/patterns/){: external} help you quickly create your app and deploy it to {{site.data.keyword.cloud_notm}}.

## Add services
{: #resources-getting-started}
{: step}

When you use a starter kit to create your app, the required services are automatically created and provisioned for you. You can connect more services to your app in the {{site.data.keyword.cloud_notm}} console from the App details page, which is displayed as soon as you create the app.

If you want to create a new service instance or connect any existing services to your app, complete the following steps:

1. On the App details page, click **Create service** or **Connect existing services**, depending on whether you already have services that you want to connect to this app.
2. Select the kind of service you want, and follow the prompts to either add an existing service to your app or create a service instance.

After you add all the services that you want, the services are displayed in the App details page.

After you connect a service to your app, you can navigate to the service documentation and API references. Simply click the links within the **Services** card to view the related docs.

For more information, see [Adding a service to your app](/docs/apps?topic=apps-add-service).

## Deploy your app
{: #deploy-getting-started}
{: step}

You can deploy your app by using the {{site.data.keyword.cloud_notm}} console or the CLI.

### Using the {{site.data.keyword.cloud_notm}} console
{: #console-getting-started}

To deploy your app by using the console, complete the following steps:

1. On the App details page, click **Deploy your app**.
2. Select a deployment target, select the toolchain settings, and click **Create**. {{site.data.keyword.cloud_notm}} automatically creates an open toolchain complete with a Git repository and continuous delivery pipeline.
3. Open the pipeline stage of your new toolchain to view the build and deployment process so that you can view your new app in minutes.

For more information, see [Deploying apps](/docs/apps?topic=apps-deploying-apps).

### Using the {{site.data.keyword.cloud_notm}} CLI
{: #cli-getting-started}

To deploy your app by using the CLI, run the [**ibmcloud dev deploy**](/docs/cli?topic=cli-idt-cli#deploy) command. For more information, see [Creating and deploying apps by using the CLI](/docs/apps?topic=apps-create-deploy-app-cli).

Now you're set for iterative development and continuous delivery.

For more information, see [Deploying apps](/docs/apps?topic=apps-deploying-apps).

## Related information
{: #related-getting-started}

[Programming guides](https://{DomainName}/docs/home/build){: external} are available per language to help you get up and running. You have many options for hosting your apps with {{site.data.keyword.cloud_notm}} infrastructure.
