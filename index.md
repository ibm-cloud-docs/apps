---

copyright:
  years: 2017, 2018
lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Getting started tutorial
{: #create}

In {{site.data.keyword.Bluemix}}, you can build enterprise-level mobile and web applications and take advantage of cloud extensions hosted by {{site.data.keyword.Bluemix_notm}}. You can use the {{site.data.keyword.Bluemix}} console and command line tools to build, run and deploy your apps. You can get started in one of two ways: create a project with a starter kit that manages the process for you, or if you know what you want, build your app with the resources you need.
{:shortdesc}

You can use a starter kit to quickly get your app started and prepare it for future development. Choose a starter kit and programming language, create a project, and then download the code for immediate inspection. You can also create a DevOps toolchain to deploy your app quickly.

Starter kits are available in many categories, including:

* [Watson](https://console.bluemix.net/developer/watson){:new_window}
* [Apple developer console](https://console.bluemix.net/developer/appledevelopment)
* [Mobile](https://console.bluemix.net/developer/mobile){:new_window}
* [Web App](https://console.bluemix.net/developer/appservice){:new_window}
* [Security](https://console.bluemix.net/developer/security){:new_window}
<!--* [Watson Data Platform developer console](https://console.bluemix.net/developer/dataplatform)-->
* [Finance](https://console.bluemix.net/developer/finance){:new_window}

## Before you begin

[Sign up](https://console.bluemix.net){: new_window} for an {{site.data.keyword.cloud_notm}} account. Enter your email, name, company, region, and phone number. You don't need a credit card to sign up for a free account.

## Step 1: Create a project
{: #project}

1. Click the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg) > **Web Apps**.

2. Click **Get Started** in the **Start from the Web** section.

3. Select a starter kit of your choice, read the details, and click **Create project**.

  To view what's included in the starter kit, expand the tile on the App Service Starter Kits dashboard.
  {: tip}

4. Name your project, select your language, and click **Create Project**.

Great start! You just created an app.

To inspect your code, click **Download Code** on the project details page. Check the `README.md` file in the downloaded compressed file to find out whether you need to take more actions to get your starter app running.
{: tip}

## Step 2: Add resources
{: #addResources}

In most cases, resources are automatically provisioned for you. You can also manually add new or existing resources to your app by clicking **Add Resource** on the project details page.

To develop and run your app locally, use the [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html)
{: tip}

## Step 3: Deploy to {{site.data.keyword.cloud_notm}}
{: #deploy}

Click **Deploy to Cloud** on the project details page, select a deployment method (for example Kubernetes Cluster or Cloud Foundry App), and click **Create**. {{site.data.keyword.cloud_notm}} automatically creates an open toolchain that's complete with a Git repository and continuous delivery pipeline. View the pipeline component of your new toolchain to start the initial build and deploy process so that you can view your new app running in minutes.

You're now set for iterative development and continuous delivery.
