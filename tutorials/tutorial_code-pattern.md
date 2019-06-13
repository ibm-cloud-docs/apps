---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-13"

keywords: apps, code pattern, DevOps, toolchain, service credentials, create app code pattern, app pattern

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# Creating an app with a code pattern
{: #tutorial-codepattern}

You can use a code pattern to quickly create your application and deploy it to {{site.data.keyword.cloud}}. You can either view the code in GitHub or create and build an app on {{site.data.keyword.cloud_notm}}, where you can use a DevOps toolchain to automatically deploy your app.
{: shortdesc}

## Step 1. Create an app
{: #create-codepattern}

1. Go to [IBM Developer](https://developer.ibm.com/patterns/){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon") and select the code pattern that you want. For example, you can select the [Build a MEAN Web App](https://developer.ibm.com/patterns/build-a-mean-web-app/){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon") code pattern.

2. Read the code pattern's description, and view the GitHub repository and `README.md` file. To view the repo, click **Get the code**, which opens the GitHub repo for the code pattern.

3. Start creating an app by using either of the following options. Either option opens the **Create app** page for the code pattern.
    * On the code pattern's page, click the link for building an app on {{site.data.keyword.cloud_notm}}. 
    * In the `README.md` file in the GitHub repo, click the link for using a starter kit to create the app. 

4. On the **Create app** page, name your app, select a resource group, optionally provide tags, and click **Create**. For more information about tags, see [Working with tags](/docs/resources?topic=resources-tag).

  To go back to the code pattern, click **View code pattern**. Check the `README.md` file in the repository to find out whether you need to take more actions to get your app up and running.
  {: tip}

## Step 2. Adding services
{: #resources-codepattern}

You can add services that enhance your app with the cognitive power of Watson, add mobile services, or security services. This process creates a service instance, creates a resource key (credentials), and binds it to your app. For this tutorial, add a place to manage your data.

1. On the **App details** page, click **Add service**.
2. Select the kind of service that you want. 
3. Select your pricing plan. A lite option is available.
4. Click **Create**.

## Step 3. Copying service credentials to your environment

After you add a service to your app, or if any services are required for your app, notice that the credentials for that service are displayed in the **Credentials** box. You must manually copy the credentials to your deployment environment.

For more information about copying credentials to your environment, see [Credentials overview](/docs/apps?topic=creating-apps-credentials_overview#credentials_overview).

## Step 4. Deploying to {{site.data.keyword.cloud_notm}}
{: #deploy-codepattern}

When you select a deployment target, a DevOps toolchain is automatically created for your app. The toolchain includes a Delivery Pipeline that indicates your app’s deployment status. The new app that is generated is pushed to a GitLab repo that is part of the toolchain.

Enabling a DevOps toolchain creates a team-based development environment for your app. When you create a toolchain, the app service creates a Git repository, where you can view source code, clone your app, and create and manage issues. You also have access to a dedicated GitLab environment and a continuous delivery pipeline. They're customized to the deployment target that you select, whether it's [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about), or [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

All toolchains that are created from an {{site.data.keyword.cloud_notm}} Developer dashboard are configured for automatic deployment.
{: note}

To select your deployment target and configure continuous delivery, complete these steps:

1. On the App details page, click **Configure continuous delivery**.
2. Select a deployment target. Set up your deployment target according to the instructions for the target that you select:
  * **Deploy to [IBM Kubernetes Service](/docs/containers?topic=containers-app)**. This option creates a cluster of hosts, called worker nodes, to deploy and manage highly available app containers. You can create a cluster or deploy to an existing cluster.
  * **Deploy to Cloud Foundry**. This option deploys your cloud-native app without you needing to manage the underlying infrastructure. If your account has access to {{site.data.keyword.cfee_full_notm}}, you can select a deployer type of either **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** or **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**, which you can use to create and manage isolated environments for hosting Cloud Foundry apps exclusively for your enterprise.
  * **Deploy to a Virtual Server**. This option provisions a virtual server instance, loads an image that includes your app, creates a DevOps toolchain, and initiates the first deployment cycle for you. For more information, see [Deploying apps to a virtual server](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server).

    VSI deployment is available for some starter kits. To use this feature, go to the [{{site.data.keyword.cloud_notm}} dashboard](https://{DomainName}), and click **Create an app** in the **Apps** tile.
    {: note}

After you select and configure the deployment target, the App details page indicates that continuous delivery is configured. You can view the repo that contains the source code for your app by clicking **View repo**.

For more information about deploying your app, see [Deploying apps](/docs/apps?topic=creating-apps-deploying-apps).

For more information about deployment targets, builds, and pipelines, see [Building and deploying](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).
