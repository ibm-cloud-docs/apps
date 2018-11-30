---

copyright:
  years: 2018
lastupdated: "2018-11-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Creating apps from your own code repository
{: #code-repo}

You can create an application in {{site.data.keyword.cloud}} by using your existing application repository. Simply provide the web link to your repository during application creation, continue adding resources, and then connect a DevOps toolchain to your application for deployment.
{: shortdesc}

## Before you begin
{: #prereqs}

Be sure that you have the following prerequisites ready to go:

 * Install the [{{site.data.keyword.dev_cli_long}} command-line interface (CLI)](/docs/cli/index.html).
 * See [What makes a good app?](/docs/apps/best-practice.html) for best practices for creating apps.
 * You must have a Git source code repository from any of the following providers: GitHub, GitHub Enterprise, Git lab, BitBucket, or Rational.

## Step 1. Create an app with an existing repository
{: #create}

To create an app and connect it with your source repo, complete these steps:

1. From  your [dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}){: new_window}, click **Create an app** in the **Apps** tile.
2. Name your app, and select a resource group.
3. Select **Bring your own code**, and provide the URL to your Git repository. Your app and Docker image must be located in the same repo.
4. Click **Create**.

The **App Details** page is displayed. From here, you can:
* [Add resources](/docs/apps/reqnsi.html) (optional).
* Connect your app to a DevOps toolchain by clicking **Connect to DevOps toolchain**. If you don't already have a toolchain, the **Connect DevOps Toolchain** page opens. Click **Create DevOps toolchain**. At that point, the [Create a Toolchain](https://{DomainName}/devops/create) page in the [DevOps dashboard](https://{DomainName}/devops/) opens in a new tab in your browser. After you create and configure your toolchain in that tab, you must go back to the **Connect a toolchain** page in your app and refresh the page. For more information, see [Connect your app to a new toolchain](#create_toolchain).
* View your repo by clicking **View repo.**
* Learn more about toolchains or the app creation experience by clicking any of the related links on the **App Details** page.

## Step 2. Connect your app to a DevOps toolchain
{: #connect_toolchain}

Establishing a link between your app, toolchain, and repo is a step toward organizing your product assets. It also helps aggregate a view of your source with your DevOps workflow, your running app instances, and dependent services across all of your deployment targets. For more information, see [Connect your app to a new toolchain](/docs/services/ContinuousDelivery/toolchains_working.html).

You can connect your app to a DevOps toolchain by using either the {{site.data.keyword.cloud_notm}} console or the CLI. 

### Using the console

  1. Connect your app to a DevOps toolchain by clicking **Connect to DevOps toolchain**. 
  
    If you don't have an existing toolchain, click **Create DevOps toolchain**. 
    
  2. After you create and configure your toolchain, go back to the Connect a toolchain page in your app and refresh the page. 

### Using the CLI

You can use the `ibmcloud dev enable` command to generate a Devops Toolchain template that you check into your repository as the instruction set for what the Devops Toolchain is to create. 

  1. From the App Service window, click **Download Code** or **Clone your repo** to work with your code locally.
  2. Run the following command:
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

For more information, see [Creating and deploying apps by using the CLI](/docs/apps/create-deploy-cli.html#developing).

## Step 3. Deploy your app
{: #deploy_app}

After you attach a DevOps toolchain to your app, complete the following steps to deploy it to {{site.data.keyword.cloud_notm}}: 

1. From the App Details page, click **Deploy to Cloud**.
2. Select a deployment method. 

    * [Deploy to a Kubernetes cluster](/docs/apps/tutorials/tutorial_byoc_kube.html).  Create a cluster of hosts, called worker nodes, to deploy and manage highly available application containers. You can create a cluster or deploy to an existing cluster.
    * Deploy with Cloud Foundry, where you don’t need to manage the underlying infrastructure.
    * Deploy to a [virtual server instance](/docs/apps/vsi-deploy.html).


