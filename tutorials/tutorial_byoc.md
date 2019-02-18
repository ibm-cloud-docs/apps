---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

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

 * Install the [{{site.data.keyword.dev_cli_long}} command-line interface (CLI)](/docs/cli/index.html).
 * See [What makes a good app?](/docs/apps/best-practice.html#best-practice) for best practices for creating apps.
 * You must have a Git source code repository from any of the following providers: GitHub, GitHub Enterprise, Git lab, BitBucket, or Rational.
 * If you plan to deploy your app to [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about), you must [prepare your {{site.data.keyword.cloud_notm}} account](/docs/cloud-foundry/prepare-account.html#prepare).

## Step 1. Create an app with an existing repository
{: #create-byoc}

To create an app and connect it with your source repo, complete these steps:

1. From  your [dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}){: new_window}, click **Create an app** in the **Apps** tile.
2. Name your app, select a resource group, and optionally provide tags to classify your app. For more information, see [Working with tags](/docs/resources/tagging_resources.html#tag).
3. Select **Bring your own code**, and provide the URL to your Git repository. Your app and Docker image must be located in the same repo.
4. Click **Create**.

The **App Details** page is displayed. From here, you can:
* [Add resources](/docs/apps/reqnsi.html#add-resource) (optional).
* If you provided tags when you created the app, you can edit them by clicking the **Edit** icon ![Edit icon](../../icons/edit-tagging.svg) that's next to the displayed tags.
* Connect your app to a DevOps toolchain by clicking **Connect to DevOps toolchain**. If you don't already have a toolchain, the **Connect DevOps Toolchain** page opens. Click **Create DevOps toolchain**. At that point, the [Create a Toolchain](https://{DomainName}/devops/create) page in the [DevOps dashboard](https://{DomainName}/devops/) opens in a new tab in your browser. After you create and configure your toolchain in that tab, you must go back to the **Connect a toolchain** page in your app and refresh the page.
* View your repo by clicking **View repo.**
* Learn more about toolchains or the app creation experience by clicking any of the related links on the **App Details** page.

## Step 2. Connect your app to a DevOps toolchain
{: #toolchain-byoc}

Establishing a link between your app, toolchain, and repo is a step toward organizing your product assets. It also helps aggregate a view of your source with your DevOps workflow, your running app instances, and dependent services across all of your deployment targets. For more information, see [Creating toolchains](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

You can connect your app to a DevOps toolchain by using either the {{site.data.keyword.cloud_notm}} console or the CLI.

### Using the console
{: #console-byoc-toolchain}

  1. Connect your app to a DevOps toolchain by clicking **Connect to DevOps toolchain**. 
  
    If you don't have an existing toolchain, click **Create DevOps toolchain**. 
    
  2. After you create and configure your toolchain, go back to the Connect a toolchain page in your app and refresh the page. 

### Using the CLI

You can use the `ibmcloud dev enable` command to generate a DevOps Toolchain template that you check into your repository as the instruction set for what the DevOps Toolchain is to create. 

  1. From the App Service window, click **Download Code** or **Clone your repo** to work with your code locally.
  2. Run the following command:
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

For more information, see [Creating and deploying apps by using the CLI](/docs/apps/create-deploy-cli.html#create-deploy-app-cli).

## Step 3. Deploy your app
{: #deploy-byoc}

After you attach a DevOps toolchain to your app, complete the following steps to deploy it to {{site.data.keyword.cloud_notm}}: 

1. From the App Details page, click **Deploy to cloud**.
2. Select a deployment method. Set up your deployment method according to the instructions for the method you choose:
  * **Deploy to [Kubernetes](/docs/apps/deploying/containers.html#containers)**. This option creates a cluster of hosts, called worker nodes, to deploy and manage highly available application containers. You can create a cluster or deploy to an existing cluster.
  * **Deploy to Cloud Foundry**. This option deploys your cloud-native app without you needing to manage the underlying infrastructure. If your account has access to {{site.data.keyword.cfee_full_notm}}, you can select a deployer type of either **[Public Cloud](/docs/cloud-foundry-public/about-cf.html#about-cf)** or **[Enterprise Environment](/docs/cloud-foundry-public/cfee.html#cfee)**, which you can use to create and manage isolated environments for hosting Cloud Foundry applications exclusively for your enterprise.
  * **Deploy to a [Virtual Server](/docs/apps/vsi-deploy.html#vsi-deploy)**. This option provisions a virtual server instance, loads an image that includes your app, creates a DevOps toolchain, and initiates the first deployment cycle for you.


