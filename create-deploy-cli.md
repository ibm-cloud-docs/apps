---
copyright:

  years: 2018

lastupdated: "2018-10-02"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}

# Creating and deploying apps by using the CLI
{: #developing}

You can use the {{site.data.keyword.Bluemix}} command-line interface (CLI) to create and deploy your app. 
{:shortdesc}

## Before you begin
{: #prereqs}

Install the {{site.data.keyword.Bluemix_notm}} CLI, the {{site.data.keyword.dev_cli_notm}} CLI plug-in, and other recommended plug-ins and tools. For more information, see [Getting started with the IBM Cloud CLI](/docs/cli/index.html). 

## Creating your app
{: #create}

You can either create a new app from scratch or create a cloud-enabled app by using your existing code. 

### Creating an app from scratch

1. Run the [`ibmcloud dev create`](/docs/cli/idt/commands.html#create) command in the directory of your choice.
2. Select **Backend Service / Web App** as the application type.
3. Select **Node** as language the language type.
4. Select **Express.js Basic (Web App)** as the starter kit to use.
5. Enter a name for your app and select the resource group you want to use (if necessary). Do not add services for now.
6. Select the **IBM DevOps, using Cloud Foundry** option to create a DevOps toolchain. You might need to set up SSH keys to complete this step.
7. Enter a unique host name, for example, `abc-devhost`. This host name is your app's route, `abc-devhost.mybluemix.net`.

Creating the app and toolchain takes a few seconds to complete. You can monitor the status in the command prompt.

### Creating an app by using existing code

1. Clone the [Hello World sample app](https://github.com/IBM-Cloud/node-helloworld) by running the following command in the directory of your choice.

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

2. Navigate to the directory where you cloned the sample app, and run the [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable) command.
3. Select to continue without committing changes to GitHub for now.
4. Select to continue when you're prompted to proceed with the Node language that is detected.
5. Select the resource group you want to use (if necessary). Do not add services for now.
6. Wait a few seconds for the app to be created. 
7. You can choose to manually merge the deployment and configuration files that are saved to the app directory when you create the app. Or you can skip this step for now.

## Building your app and running it locally
{: #build-run}

Regardless of which option you used to create your app, you can now build it and run it locally.

1. Navigate to your application directory, and ensure that Docker is running on your system.
2. Run the [`ibmcloud dev build`](/docs/cli/idt/commands.html#build) command to build your app.
3. Run the [`ibmcloud dev run`](/docs/cli/idt/commands.html#run) command to begin running your app locally.
4. View your apprunning locally at `http://localhost:3000` or a similar URL.
5. Press the **Ctrl+C** keys to stop your app.

You can also use [compound commands](/docs/cli/idt/commands.html#compound) like `ibmcloud dev build/run` to sequentially issue a build followed by a run.
{: tip}

## Adding a service and modify the code
{: #add-service}

Now that your app can run locally, you can add a service and modify some code. 

1. Run the [`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit) command.
2. Follow the prompts to create and connect a new data-related service to your app, such as {{site.data.keyword.cloudant_short_notm}}. You might need to select a region and plan for the service.
3. You can choose to manually merge the deployment and configuration that are saved to your app directory when you create the service. Or you can skip this step for now.
4. Make a change in your code. For example, modify the `/public/index.html` file or a similar file. If you're using the sample `ExpressJS` application, you can change the `Congratulations!` string to something like `Hello World!`.
5. Save any files that you modified.

## Deploying to {{site.data.keyword.Bluemix_notm}}
{: #deploy}

You can deploy your app {{site.data.keyword.Bluemix_notm}} in one of two ways, depending on how your app is configured. 

### Deploying your app by using a DevOps toolchain

If you previously created a DevOps toolchain for your app, deploying a new build is as simple as committing and pushing your code to the repository in your toolchain. 

1. Run the `git add` command.
2. Run the `git commit -m "made changes"` command to commit changes.
3. Run the `git push origin master` command to push to the master branch.
4. View the DevOps toolchain for your app from the {{site.data.keyword.Bluemix_notm}} console. You can view the toolchain in a web browser by running the [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) command from the app directory and clicking **View Toolchain**.
5. View the pipeline within the toolchain to verify that a new build started.

### Manually deploying your app

You can manually deploy your app by using the [`deploy`](/docs/cli/idt/commands.html#deploy) command. For example, use the following steps to manually deploy your app to Kubernetes.

1. Ensure you [created a Kubernetes cluster](https://console.bluemix.net/containers-kubernetes/overview).
2. Run the [`ibmcloud dev deploy -t container`](/docs/cli/idt/commands.html#deploy) command.
3. When prompted, confirm the cluster and container image name to use.
4. Wait a few minutes for the deployment to complete.

## Viewing your app

1. To view the URL of your app that's running on {{site.data.keyword.Bluemix_notm}}, run the [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) command.
2. To view details about your app's credentials, services, and toolchain from the {{site.data.keyword.Bluemix_notm}} console, run the [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) command. 

