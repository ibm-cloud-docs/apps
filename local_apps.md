---

copyright:
  years: 2020
lastupdated: "2020-04-20"

keywords: apps, local, build, run, deploy, download app, ibmcloud dev code

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:external: target="_blank" .external}

# Developing apps locally
{: #local-app-development}

Download your app for local development where you can easily build, test, and deploy by using the {{site.data.keyword.cloud}} CLI. This is useful for debugging issues, and adding features or services, and when you are ready, you can re-deploy your app to the cloud.
{: shortdesc}

## Before you begin

* Install the [{{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-getting-started) command-line interface (CLI), which includes the {{site.data.keyword.dev_cli_short}} `ibmcloud dev` commands.
* Set up [Git authentication](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) by adding a personal access token.
* Log in to the {{site.data.keyword.cloud_notm}} CLI. If your organization uses federated logins, use the `-sso` option; for example:
  ```bash
  ibmcloud login -sso
  ```
  {: codeblock}

* If you plan to deploy your app to Cloud Foundry, run the following command to set your org and space targets.
  ```bash
  ibmcloud target --cf
  ```
  {: codeblock}

* Run the following command to retrieve the credentials.
  ```bash
  ibmcloud dev get-credentials
  ```
  {: codeblock}

## Downloading your app
{: #download-app-local}

You can download an app directly from the {{site.data.keyword.cloud}} console, or by using the {{site.data.keyword.cloud_notm}} command-line interface (CLI).

### Downloading with the {{site.data.keyword.cloud_notm}} console
{: #download-with-console}

You can view your app code by clicking **Download code** on the App details page of your app. Your code is downloaded as a `.zip` file that contains the complete app code structure. You can extract the file and run the code locally by using the {{site.data.keyword.dev_cli_notm}} `ibmcloud dev` commands, or add it to your code management repository.

The app code includes a `README.md` file that contains technical details about the app. Check the `README.md` file to find out whether you need to take more actions to get your app up and running.
{: tip}

### Downloading with the {{site.data.keyword.cloud_notm}} CLI
{: #download-with-cli}

* From the command line, run the [**ibmcloud dev code <APPNAME>**](/docs/cli?topic=cloud-cli-idt-cli#code) command to download your app code.
* If you are unsure of the app name or want to download another app, you can list all the {{site.data.keyword.cloud_notm}} apps that are in a space by running the [**ibmcloud dev list**](/docs/cli?topic=cloud-cli-idt-cli#list) command.

## Building, running, and viewing your app locally
{: #use-cli-locally}

After you download your app, you can quickly have it up and running in a local development environment. You can build your app locally, modify it, and test it before you deploy it to the cloud.

If you want to build the app locally for testing before you deploy it to the cloud, complete the following steps:

1. Import the app to your integrated development environment.
2. Modify the code.
3. Make sure that Docker is running, and run the following command to build your app in a local development container:
  ```bash
  ibmcloud dev build
  ```
  {: pre}

4. Now you can run the following command to run your app in a local development container:
  ```bash
  ibmcloud dev run
  ```
  {: pre}

5. Go to `http://localhost:3000` in your browser. Your port number might be different depending on your chosen runtime.

You can also use [compound commands](/docs/cli?topic=cloud-cli-idt-cli#compound), such as **ibmcloud dev build/run**, to sequentially start a build followed by a run.
{: tip}

## Adding a service and modifying the code
{: #add-services-locally}

Now that your app can run locally, you can add a service and modify some code. 

1. Run the [**ibmcloud dev edit**](/docs/cli?topic=cloud-cli-idt-cli#edit) command.
2. Follow the prompts to create and connect a new data-related service to your app, such as {{site.data.keyword.cloudant_short_notm}}. You might need to select a region and plan for the service.
3. You can choose to manually merge the configuration files that are saved to your app directory when you create the service. Or you can skip this step for now.
4. Update your code. For example, modify the `/public/index.html` file or a similar file. If you're using the sample `ExpressJS` app, you can change the `Congratulations!` message to something like `Hello World!`.
5. Save any files that you modified.

## Deploying your app to the cloud
{: #deploy-cli-cloud}

You can deploy your app to {{site.data.keyword.cloud_notm}} from the CLI. For more information, see the following topics:

* [Automatically deploying your app](/docs/apps?topic=creating-apps-deploy-cli-auto#deploy-console-auto)
* [Manually deploying your app](/docs/apps?topic=creating-apps-deploy-cli-manual#deploy-console-manual)