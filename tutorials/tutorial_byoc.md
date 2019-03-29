---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: byoc, code repository, continuous delivery, cli, deploy, create app custom repo, custom repo, existing repo, custom code

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Creating apps from your own code repository
{: #tutorial-byoc}

You can create an application in {{site.data.keyword.cloud}} by using your existing application repository. Simply provide the web link to your repository during application creation, continue adding resources, and then connect a DevOps toolchain to your application for deployment.
{: shortdesc}

## Before you begin
{: #prereqs-byoc}

Be sure that you have the following prerequisites ready to go:

 * Install the [{{site.data.keyword.dev_cli_long}} command-line interface (CLI)](/docs/cli?topic=cloud-cli-ibmcloud-cli).
 * See [What makes a good app?](/docs/apps?topic=creating-apps-best-practice) for best practices for creating apps.
 * You must have a Git source code repository from any of the following providers: GitHub, GitHub Enterprise, Git lab, BitBucket, or Rational.
 * If you plan to deploy your app to [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), you must [prepare your {{site.data.keyword.cloud_notm}} account](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Step 1. Create an app with an existing repository
{: #create-byoc}

To create an app and connect it with your source repo, complete these steps:

1. From  your [dashboard](https://{DomainName}){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon"), click **Create an app** in the **Apps** tile.
2. Name your app, select a resource group, and optionally provide tags to classify your app. For more information, see [Working with tags](/docs/resources?topic=resources-tag).
3. Select **Bring your own code**, and provide the URL to your Git repository. Your app and Docker image must be located in the same repo.
4. Click **Create**. The **App details** page is displayed.
5. Optional. [Add services](/docs/apps?topic=creating-apps-add-resource) to your app.
6. Optional. If you provided tags when you created the app, you can edit them by clicking the **Edit** icon ![Edit icon](../../icons/edit-tagging.svg) that's next to the displayed tags.
7. Optional. View your repo by clicking **View repo.**

## Step 2. Deploy your app
{: #toolchain-byoc}

Establishing a link between your app, toolchain, and repo is a step toward organizing your product assets. It also helps aggregate a view of your source with your DevOps workflow, your running app instances, and dependent services across all of your deployment targets. For more information, see [Creating toolchains](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

You can configure continuous delivery for your app by using either the {{site.data.keyword.cloud_notm}} console or the CLI.

### Using the console
{: #console-byoc-toolchain}

  1. On the **App details** page, connect your app to a DevOps toolchain by clicking **Configure continuous delivery**. The **Deploy my app** page is displayed.
  2. If you don't have an existing toolchain, click **Create a toolchain**. After you create the toolchain, use the breadcrumbs to return to the **App details** page, which indicates that continuous delivery is configured.
  3. If you have an existing toolchain, select it, and then click **Enable deployment**. The **App details** page is displayed, indicating that continuous delivery is configured.

### Using the CLI

You can use the `ibmcloud dev enable` command to generate a DevOps toolchain template that you check into your repository as the instruction set for what the DevOps toolchain is to create. 

  1. On the **App details** page, click **View repo** to work with your code locally.
  2. Run the following command:
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

For more information, see [Creating and deploying apps by using the CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli).

