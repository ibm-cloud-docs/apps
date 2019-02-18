---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-04"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Getting started tutorial
{: #tutorial-getting-started}

You can build enterprise-ready mobile and web applications in {{site.data.keyword.cloud}} and take advantage of cloud extensions that are hosted by {{site.data.keyword.cloud_notm}}. You have several options for getting started. Create an app with a starter kit that manages the process for you, or if you know what you want, start from scratch and build your app with the resources you need, or use your existing repository and bring your own code.
{: shortdesc}

## Before you begin
{: #prereqs-getting-started}

You can create your app by using the {{site.data.keyword.cloud_notm}} console or the command-line interface (CLI). If you want to use the CLI, see [Getting started with the {{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html) for installation details.

## Step 1. Create your app
{: #create-getting-started}

Create an app by selecting one of the following entry points:
* [Starter kit](/docs/apps/tutorials/tutorial_starter-kit.html#tutorial-starterkit): Create an app from a selection of App Service starter kits that manage the process for you.
* [Custom](/docs/apps/tutorials/tutorial_scratch.html#tutorial-scratch): If you know what you want, build a custom app from scratch with the resources you need by using a blank starter kit.
* [Bring your own code](/docs/apps/tutorials/tutorial_byoc.html#tutorial-byoc): Bring your own code by linking to your own existing content repository. Your app and Docker image must be located in the same repo.
* [CLI](/docs/apps/create-deploy-cli.html#create-deploy-app-cli): Create and deploy a custom or starter kit app by using the CLI and Developer tools.
* [Code patterns](/docs/apps/tutorials/tutorial_code-pattern.html#tutorial-codepattern): Use an IBM Developer code pattern as a basis for creating your app.
* [{{site.data.keyword.cloud_notm}} catalog ![External link icon](../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com/catalog){: new_window}: You can browse or search the catalog for apps and services that you can create and start using today.

## Step 2. Add resources
{: #resources-getting-started}

When you use a starter kit to create your app, your resources are automatically created for you. You can associate more resources with your app by clicking **Add Resource** on the app details page in the console.

To add resources by using the CLI, run the following command to add a service to your app. You can select an existing service from one already enabled on your account, or add a new service. 
```
ibmcloud dev edit
```
{: codeblock}

For more information, see [Adding a service to your app](/docs/apps/reqnsi.html#add-resource).

## Step 3. Deploy your app
{: #deploy-getting-started}

You can deploy your app by using the console or the command line.

### Using the console
{: #console-getting-started}

To deploy your app by using the console, complete the following steps:

1. On the **App details** page, click **Deploy to cloud**.
2. Select a deployment method, and click **Create**. {{site.data.keyword.cloud_notm}} automatically creates an open toolchain complete with a Git repository and continuous delivery pipeline.
3. Open the pipeline stage of your new toolchain to view the build and deployment process so that you can view your new app in minutes.

For more information, see the table of contents for various deployment topics in the "Deploying and integrating apps" section.

### Using the command line
{: #cli-getting-started}

To deploy your app by using the command line, run the `ibmcloud dev deploy` command. For more information, see [Creating and deploying apps by using the CLI](/docs/apps/create-deploy-cli.html#create-deploy-app-cli).

Now you're set for iterative development and continuous delivery.
