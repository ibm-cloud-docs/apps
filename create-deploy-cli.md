---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-06"

keywords: apps, create, build, deploy, cli, web app, microservice, deploy cli, build app local, developer tools, ibmcloud dev create

subcollection: creating-apps

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Creating apps by using the CLI
{: #create-deploy-app-cli}

You can use the {{site.data.keyword.cloud}} command-line interface (CLI) to create and deploy your application. 

You can either create a starter app from scratch or cloud-enable your existing app code. 
{: note}

## Before you begin
{: #prereqs-app-cli}

You must install the {{site.data.keyword.cloud_notm}} CLI, the {{site.data.keyword.dev_cli_notm}} CLI plug-in, and other recommended plug-ins and tools. For more information, see [Getting started with the IBM Cloud CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli). 

## Creating a starter app from scratch
{: #create-app-cli}

Creating an app from scratch is useful if you don't already have existing code to begin with and would rather start from a language or a framework starter template.

1. Run the [`ibmcloud dev create`](/docs/cli/idt?topic=cloud-cli-idt-cli#create) command in the directory of your choice.
2. Select **Backend Service / Web App** as the application type.
3. Select **Node** as the language type.
4. Select **Node.js Web App with Express.js (Web App)** as the starter kit to use.
5. Enter a name for your app, and select the resource group that you want to use (if necessary). Don't add services for now.
6. Select the **IBM DevOps, deploy to Cloud Foundry buildpacks** option to create a DevOps toolchain. You might need to set up SSH keys to complete this step.
  If you set a passphrase for your SSH key, you are required to enter this code.
  {: note}
7. Follow the remaining prompts to:
  * Select a region for your toolchain.
  * Enter a name for the DevOps toolchain name.
  * Enter a name for the host name.

Creating the app and toolchain takes a few seconds to complete.

## Generating deployment and cloud enablement assets
{: #byoc-cli}

This option can be used if you already have an existing codebase and want to generate deployment and cloud enablement assets for a single microservice or web app by using [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable). This command is in Beta, and not all languages and/or app structures are supported. The following instructions illustrate how to use this function with a sample repository, but the steps are roughly the same for your own codebase.

1. Log in to {{site.data.keyword.cloud_notm}} by running `ibmcloud login`, and then target an org and space.
2. Clone the [Hello World sample app](https://github.com/IBM-Cloud/node-helloworld){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") by running the following command in the directory of your choice.

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

3. Navigate to the directory where you cloned the sample app, and run the [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable) command.
4. Select to continue without committing changes for now (if necessary).
5. Select to continue when you're prompted to proceed with the Node language that is detected.
6. Select the resource group that you want to use (if necessary). 
7. Select the option to create a new {{site.data.keyword.cloud_notm}} app that is linked to this Git repository. See **Important Notes** for details.
8. Don't add services for now.
9. Wait a few seconds for the operations to complete. 
10. After the operations are completed, manually merge the deployment and cloud enablement files that are saved to the app directory. Merge new files marked `.merge` by using `git diff` or a similar tool.

### Important Notes
 - If you already created an {{site.data.keyword.cloud_notm}} app by using the {{site.data.keyword.cloud_notm}} console, follow steps 2 - 5 in the previous section in your app directory. For step 6, you can select the option to connect your local code to an existing app.
 - You can also choose to generate deployment and cloud enablement files without connecting to an {{site.data.keyword.cloud_notm}} app by running [`ibmcloud dev enable --no-create`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable).
 - To manually configure a toolchain and deployment files, follow [the tutorial](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc-kube). This tutorial can be useful if you're trying to configure a Continuous Delivery toolchain for more than one interrelated web apps or microservices.
 - If your existing codebase isn't already in a Git repository, follow steps 2 - 5 in the previous section in your app directory. For step 6, you can select the option create a new {{site.data.keyword.cloud_notm}} app, and deploy it to a DevOps toolchain (which has a newly created GitLab repository).

## Building your app and running it locally
{: #build-run-app-cli}

Regardless of which option you used to create your app, you can now build it and run it locally.

1. Navigate to your application directory, and ensure that Docker is running on your system.
2. Run the [`ibmcloud dev build`](/docs/cli/idt?topic=cloud-cli-idt-cli#build) command to build your app.
3. Run the [`ibmcloud dev run`](/docs/cli/idt?topic=cloud-cli-idt-cli#run) command to begin running your app locally.
4. View your app that is running locally at `http://localhost:3000` or a similar URL.
5. Press Ctrl+C to stop your app.

You can also use [compound commands](/docs/cli/idt?topic=cloud-cli-idt-cli#compound) like `ibmcloud dev build/run` to sequentially issue a build followed by a run.
{: tip}

## Adding a service and modifying the code
{: #resources-app-cli}

Now that your app can run locally, you can add a service and modify some code. 

1. Run the [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit) command.
2. Follow the prompts to create and connect a new data-related service to your app, such as {{site.data.keyword.cloudant_short_notm}}. You might need to select a region and plan for the service.
3. You can choose to manually merge the configuration files that are saved to your app directory when you create the service. Or you can skip this step for now.
4. Update your code. For example, modify the `/public/index.html` file or a similar file. If you're using the sample `ExpressJS` application, you can change the `Congratulations!` string to something like `Hello World!`.
5. Save any files that you modified.

## Deploying your app
{: #deploy-app-cli}

You can deploy your app to {{site.data.keyword.cloud_notm}} from the CLI in one of two ways, depending on how your app is configured. For more information, see these topics:

* [Automatically deploying your app](/docs/apps?topic=creating-apps-deploy-cli-auto)
* [Manually deploying your app](/docs/apps?topic=creating-apps-deploy-cli-manual)

## Viewing your app
{: #view-app-cli}

1. To view the URL of your app that's running on {{site.data.keyword.cloud_notm}}, run the [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) command. Then, go to the URL in your browser.
2. To view details about your app's credentials, services, and toolchain from the {{site.data.keyword.cloud_notm}} console, run the [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) command. 

**To report issues or provide feedback, you can use the [{{site.data.keyword.cloud_notm}} Tech's Slack - #developer-tools channel](https://ibm-cloud-tech.slack.com/){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon"). Request team access [here](https://slack-invite-ibm-cloud-tech.mybluemix.net/){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").**
