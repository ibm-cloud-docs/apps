---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-12"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Getting started tutorial
{: #create}

In {{site.data.keyword.Bluemix}}, you can build enterprise-level mobile and web applications and take advantage of cloud extensions that are hosted by {{site.data.keyword.Bluemix_notm}}. You can use the {{site.data.keyword.Bluemix}} console and command line tools to build, run, and deploy your apps. Get started in two ways: create an app with a starter kit that manages the process for you, or if you know what you want, build your app with the resources you need.
{:shortdesc}

You can use a starter kit to quickly get your app started and prepare it for future development. Choose a starter kit and programming language, create an app, and then set up a DevOps toolchain to automatically deploy your app. You can also download the code for immediate inspection.

Starter kits are available in many categories, including:

* [Watson ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/developer/watson/dashboard){:new_window}
* [Apple ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/developer/appledevelopment/dashboard){:new_window}
* [Mobile ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/developer/mobile/dashboard){:new_window}
* [Web App ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/developer/appservice/dashboard){:new_window}
* [Security ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/developer/security/dashboard){:new_window}
<!--* [Watson Data Platform developer console](https://console.bluemix.net/developer/dataplatform)-->
* [Finance ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/developer/finance/dashboard){:new_window}

## Before you begin

[Sign up ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net){: new_window} for an {{site.data.keyword.cloud_notm}} account. Enter your email, name, company, region, and phone number.

You don't need a credit card to sign up for a free account. But entering a credit card gives you access to more resources and makes it easier for you to get all {{site.data.keyword.cloud_notm}} offers.

## Step 1: Creating an app
{: #project}

1. Click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg) > **Web Apps**.

2. Click **Get Started** in the **Start from the Web** section.

3. Select a starter kit of your choice, read the details, and click **Create**.

   To view what's included in the starter kit, expand the tile on the App Service Starter Kits dashboard.
   {: tip}

4. Name your app, select your language, and click **Create**.

   Great start! You just created an app.

   To inspect your code, click **Download Code** on the app details page. Check the `README.md` file in the downloaded compressed file to find out whether you need to take more actions to get your starter app up and running.
   {: tip}

## Step 2: Adding resources
{: #addResources}

Most starter kits instruct {{site.data.keyword.cloud_notm}} to automatically provision resources for you. You can also associate more resources with your app by clicking **Add Resource** on the app details page.

To develop and run your app locally, use the [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html)
{: tip}

## Step 3: Deploying to {{site.data.keyword.cloud_notm}}
{: #deploy}

Click **Deploy to Cloud** on the app details page, select a deployment method, for example Kubernetes Cluster or Cloud Foundry App, and click **Create**. {{site.data.keyword.cloud_notm}} automatically creates an open toolchain complete with a Git repository and continuous delivery pipeline. Open the pipeline component of your new toolchain to start the initial build and deploy process so that you can see your new app in minutes.

You're now set for iterative development and continuous delivery.
