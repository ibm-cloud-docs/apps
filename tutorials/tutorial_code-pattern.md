---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, code pattern, DevOps, toolchain, service credentials

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creating an app with a code pattern
{: #tutorial-codepattern}

You can use a code pattern to quickly create your application and deploy it to {{site.data.keyword.cloud}}. You can either view the code in GitHub or create and build an app on {{site.data.keyword.cloud_notm}}, where you can use a DevOps toolchain to automatically deploy your app.
{: shortdesc}

## Step 1. Create an app
{: #create-codepattern}

1. Go to [IBM Developer ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/patterns/){:new_window} and select the code pattern that you want. For example, you can select the [Build a MEAN Web App ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://developer.ibm.com/patterns/build-a-mean-web-app/){:new_window} code pattern.

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

You can deploy your app to {{site.data.keyword.cloud_notm}} several ways, but a DevOps toolchain is the best way to deploy production apps. With a DevOps toolchain, you can easily automate deployments to lots of environments and quickly add monitoring, logging, and alert services to help manage your app as it grows.

Enabling a toolchain creates a team-based development environment for your app. When you create a toolchain, the app service creates a Git repository, where you can view source code, clone your app, and create and manage issues. You also have access to a dedicated Git lab environment and a continuous delivery pipeline. They're customized to the deployment target you choose, whether it's [Kubernetes](/docs/containers?topic=containers-container_index), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about), or [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers).

1. On the **App details** page, click **Configure continuous delivery**.
2. Select a deployment target, and click **Create**. {{site.data.keyword.cloud_notm}} automatically creates an open toolchain complete with a Git repository and continuous delivery pipeline.
3. Open the pipeline stage of your new toolchain to view the build and deployment process so that you can view your new app in minutes.

For more information about deployment targets, builds, and pipelines, see [Building and deploying](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).
