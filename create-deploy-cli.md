---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, create, build, deploy, cli, web app, microservice

subcollection: creating-apps

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Creating and deploying apps by using the CLI
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

1. Run the [`ibmcloud dev create`](/docs/cli/idt/commands.html#create) command in the directory of your choice.
2. Select **Backend Service / Web App** as the application type.
3. Select **Node** as the language type.
4. Select **Node.js Web App with Express.js (Web App)** as the starter kit to use.
5. Enter a name for your app, and select the resource group that you want to use (if necessary). Don't add services for now.
6. Select the **IBM DevOps, using Cloud Foundry** option to create a DevOps toolchain. You might need to set up SSH keys to complete this step.
  If you set a passphrase for your SSH key, you are required to enter this code.
  {: note}
7. Enter a unique host name; for example, `abc-devhost`. This host name is your app's route; for example, `abc-devhost.mybluemix.net`.

The default shared domain is `mybluemix.net`, but `appdomain.cloud` is another domain option that you can use. For more information about migrating to `appdomain.cloud`, see [Updating your domain](/docs/apps/tutorials?topic=creating-apps-update-domain).
{: tip}

Creating the app and toolchain takes a few seconds to complete.

## Generating deployment and cloud enablement assets
{: #byoc-cli}

This option can be used if you already have an existing codebase and want to generate deployment and cloud enablement assets for a single microservice or web app by using [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable). Note that this command is in Beta, and not all languages and/or app structures are supported. The following instructions illustrate how to use this functionality with a sample repository, but the steps are roughly the same for your own codebase.

1. Log in to {{site.data.keyword.cloud_notm}} by running `ibmcloud login`, and then target an org and space.
2. Clone the [Hello World sample app](https://github.com/IBM-Cloud/node-helloworld) by running the following command in the directory of your choice.

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

3. Navigate to the directory where you cloned the sample app, and run the [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable) command.
4. Select to continue without committing changes for now (if necessary).
5. Select to continue when you're prompted to proceed with the Node language that is detected.
6. Select the resource group that you want to use (if necessary). 
7. Select the option to create a new {{site.data.keyword.cloud_notm}} app that is linked to this Git repository. See **Important Notes** for details.
8. Don't add services for now.
9. Wait a few seconds for the operations to complete. 
10. After the operations are completed, manually merge the deployment and cloud enablement files that are saved to the app directory. Merge new files marked `.merge` by using `git diff` or a similar tool.

### Important Notes
 - If you already created an {{site.data.keyword.cloud_notm}} app by using the {{site.data.keyword.cloud_notm}} console, follow steps 2 - 5 in the previous section in your app directory. For step 6, you can select the option to connect your local code to an existing app.
 - You can also choose to generate deployment and cloud enablement files without connecting to an {{site.data.keyword.cloud_notm}} app by running [`ibmcloud dev enable --no-create`](/docs/cli/idt/commands.html#enable).
 - To manually configure a toolchain and deployment files, follow [the tutorial](/docs/apps/tutorials/tutorial_byoc_kube.html). This can be useful if you're trying to configure a Continuous Delivery toolchain for more than one interrelated web apps or microservices.
 - If your existing codebase isn't already in a Git repository, follow steps 2 - 5 in the previous section in your app directory. For step 6, you can select the option create a new {{site.data.keyword.cloud_notm}} app, and deploy it to a DevOps toolchain (which has a newly created GitLab repository).

## Building your app and running it locally
{: #build-run-app-cli}

Regardless of which option you used to create your app, you can now build it and run it locally.

1. Navigate to your application directory, and ensure that Docker is running on your system.
2. Run the [`ibmcloud dev build`](/docs/cli/idt/commands.html#build) command to build your app.
3. Run the [`ibmcloud dev run`](/docs/cli/idt/commands.html#run) command to begin running your app locally.
4. View your app that is running locally at `http://localhost:3000` or a similar URL.
5. Press the **Ctrl+C** keys to stop your app.

You can also use [compound commands](/docs/cli/idt/commands.html#compound) like `ibmcloud dev build/run` to sequentially issue a build followed by a run.
{: tip}

## Adding a service and modify the code
{: #resources-app-cli}

Now that your app can run locally, you can add a service and modify some code. 

1. Run the [`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit) command.
2. Follow the prompts to create and connect a new data-related service to your app, such as {{site.data.keyword.cloudant_short_notm}}. You might need to select a region and plan for the service.
3. You can choose to manually merge the configuration files that are saved to your app directory when you create the service. Or you can skip this step for now.
4. Update your code. For example, modify the `/public/index.html` file or a similar file. If you're using the sample `ExpressJS` application, you can change the `Congratulations!` string to something like `Hello World!`.
5. Save any files that you modified.

## Deploying to {{site.data.keyword.cloud_notm}}
{: #deploy-app-cli}

You can deploy your {{site.data.keyword.cloud_notm}} app in one of two ways, depending on how your app is configured. 

### Deploying your app by using a DevOps toolchain
If you haven't yet created a DevOps toolchain for your app and your app isn't yet in a Git repository, you can run the [`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit) command. Follow the prompts for "Configure DevOps" and deploy to a new toolchain (and create a new GitLab repository).

After you create a DevOps toolchain for your app, deploying a new build is as simple as committing and pushing your code to the repository in your toolchain. 

1. Run the `git add .` command.
2. Run the `git commit -m "made changes"` command to commit changes.
3. Run the `git push origin master` command to push to the master branch.
4. View the DevOps toolchain for your app from the {{site.data.keyword.cloud_notm}} console. You can view toolchain details from the **App details** page in the {{site.data.keyword.cloud_notm}} console by running the [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) command from the app directory.
5. View the pipeline within the toolchain to verify that a new build started.

### Manually deploying your app

You can manually deploy your app by using the [`deploy`](/docs/cli/idt/commands.html#deploy) command. For example, use the following steps to manually deploy your app to Kubernetes.

1. Ensure that you [created a Kubernetes cluster](https://{DomainName}/containers-kubernetes/overview).
2. Run the [`ibmcloud dev deploy -t container`](/docs/cli/idt/commands.html#deploy) command.
3. When prompted, confirm the cluster and container image name to use.
4. Wait a few minutes for the deployment to complete.

## Viewing your app
{: #view-app-cli}

1. To view the URL of your app that's running on {{site.data.keyword.cloud_notm}}, run the [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) command.
2. To view details about your app's credentials, services, and toolchain from the {{site.data.keyword.cloud_notm}} console, run the [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) command. 

**To report issues or provide feedback, you can use the [{{site.data.keyword.cloud_notm}} Tech's Slack - #developer-tools channel](https://ibm-cloud-tech.slack.com). Request team access [here](https://slack-invite-ibm-cloud-tech.mybluemix.net/).**
