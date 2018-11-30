---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creating an app with a starter kit
{: #create_starterkit}

You can use a starter kit to quickly get your app started and prepare it for future development. Choose a starter kit and programming language, create an app, and then set up a DevOps toolchain to automatically deploy your app. You can also download the code for immediate inspection.
{: shortdesc}

You can create an app from a selection of starter kits, including a blank one if you would like to customize build options yourself. Either way, a DevOps toolchain is automatically created for deploying your app. You can also download the code for immediate inspection.

Starter kits are available in many categories, including:
* [Watson ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/developer/watson/dashboard){:new_window}
* [Apple ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/developer/appledevelopment/dashboard){:new_window}
* [Mobile ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/developer/mobile/dashboard){:new_window}
* [Web App ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/developer/appservice/dashboard){:new_window}
* [Security ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/developer/security/dashboard){:new_window}
* [Finance ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/developer/finance/dashboard){:new_window}

## Step 1. Create an app
{: #create-app}

1. From the [{{site.data.keyword.cloud}} dashboard](https://{DomainName}), click the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg) > **Web Apps**.

2. Click **Get Started** in the **Start from the Web** section.

3. Select a starter kit of your choice, read the details, and click **Create**.
    
    To see what is included in the starter kit, expand the tile on the [App Service Starter Kits ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/developer/appservice/starter-kits){:new_window} dashboard. The "Create App" starter kit option can be used as a blank starter app and customized further to match your needs.
    {: tip}

4. Name your app, select your language, and click **Create**.
    
    Great start! You just created an app.

To inspect your code, click **Download Code** on the app details page. Check the `README.md` file in the downloaded compressed file to find out whether you need to take more actions to get your starter app up and running.
{: tip}

For more information, see [Creating a basic web app with a starter kit](/docs/apps/tutorials/tutorial_web.html).

## Step 2. Adding resources
{: #add-services}

You can add resources that enhance your app with the cognitive power of Watson, add mobile services, or security services. For this tutorial, add a place to manage your data.

1. From the app service window, select click **Add Resource**.
2. Select the kind of service you want. For example, select **Data** > **Next** > **Cloudant** > **Next**.
3. Select your pricing plan. There is a free option that you can use for this tutorial.
4. Click **Create**.

## Step 3. Deploy to {{site.data.keyword.cloud_notm}}
{: #deploy}

Click **Deploy to Cloud** on the App Details page, select a deployment method, for example Kubernetes Cluster or Cloud Foundry App, and click **Create**. {{site.data.keyword.cloud_notm}} automatically creates an open toolchain complete with a Git repository and continuous delivery pipeline. Open the pipeline component of your new toolchain to start the initial build and deploy process so that you can see your new app in minutes.

To deploy your app with the command line, use `ibmcloud dev deploy`. For more information, see [Creating and deploying apps by using the CLI](/docs/apps/create-deploy-cli.html).
