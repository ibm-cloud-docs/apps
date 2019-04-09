---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-08"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creating an app with a starter kit
{: #tutorial-starterkit}

You can use a starter kit to quickly get your app started and prepare it for future development. Choose a starter kit and programming language, create an app, and then set up a DevOps toolchain to automatically deploy your app. You can also download the code for immediate inspection.
{: shortdesc}

You can create an app from a selection of starter kits, including a blank one if you would like to customize build options yourself. Either way, a DevOps toolchain is automatically created for deploying your app. You can also download the code for immediate inspection.

{{site.data.keyword.cloud_notm}} has developer portals in different areas of interest (like Watson, Security, or Finance) or a digital channel (like Mobile or Web Apps). You can access these portals from the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg).

Each developer portal provides starter kits that are relevant to the portals's focus area. The portals offers consistent, intuitive workflows for creating a working production-ready app in minutes.

Starter kits are available in many categories, including:
* [Watson](https://{DomainName}/developer/watson/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")
* [Apple](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")
* [Mobile](https://{DomainName}/developer/mobile/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")
* [Web App](https://{DomainName}/developer/appservice/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")
* [Security](https://{DomainName}/developer/security/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")
* [Finance](https://{DomainName}/developer/finance/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")

## Step 1. Create an app
{: #create-starterkit}

1. From the [{{site.data.keyword.cloud}} dashboard](https://{DomainName}){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon"), click the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg) > **Web Apps**.

2. Click **Get Started** in the **Start from the Web** section.

3. Select a starter kit of your choice, read the details, and click **Create**.
    
    To see what is included in the starter kit, expand the tile on the [App Service Starter Kits](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon") dashboard. The "Create App" starter kit option can be used as a blank starter app and customized further to match your needs.
    {: tip}

4. Name your app, select a resource group, optionally provide tags, select your language, and click **Create**.
    
    Great start! You just created an app.

To inspect your code, click **Download code** on the **App details** page. Check the `README.md` file in the downloaded compressed file to find out whether you need to take more actions to get your starter app up and running.
{: tip}

For more information, see the following topics:
 * [Creating a basic web app with a starter kit](/docs/apps/tutorials?topic=creating-apps-tutorial-webapp)
 * [Working with tags](/docs/resources?topic=resources-tag)

## Step 2. Add services
{: #resources-starterkit}

You can add services that enhance your app with the cognitive power of Watson, add mobile services, or security services. For this tutorial, add a place to manage your data.

1. On the **App details** page, click **Add service**.
2. Select the kind of service you want. For example, select **Data** > **Next** > **Cloudant** > **Next**.
3. Select your pricing plan. There is a free option that you can use for this tutorial.
4. Click **Create**.

## Step 3. Deploy to {{site.data.keyword.cloud_notm}}
{: #deploy-starterkit}

Click **Configure continuous delivery** on the **App details** page, select a deployment target, and click **Create**. {{site.data.keyword.cloud_notm}} automatically creates an open toolchain complete with a Git repository and continuous delivery pipeline.

Enabling a toolchain creates a team-based development environment for your app. When you create a toolchain, the app service creates a Git repository, where you can view source code, clone your app, and create and manage issues. You also have access to a dedicated Git lab environment and a continuous delivery pipeline. They're customized to the deployment environment you choose, whether it's [Kubernetes](/docs/containers?topic=containers-container_index), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about), or [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers).

After you select your deployment target, open the pipeline component of your new toolchain to start the initial build and deployment process so that you can see your new app in minutes.

All toolchains that are created from an {{site.data.keyword.cloud_notm}} Developer dashboard are configured for automatic deployment.
{: note}

To deploy your app with the command line, use `ibmcloud dev deploy`. For more information, see [Creating and deploying apps by using the CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli).
