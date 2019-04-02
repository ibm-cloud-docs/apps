---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-02"

keywords: apps, deploy, deploying apps, toolchains, cli, cloud

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Deploying apps
{: #deploying-apps}

You can deploy your applications with a DevOps toolchain or the command-line interface (CLI). A DevOps toolchain is a set of tool integrations. The CLI is a simple way to deploy your apps and service instances.
{: shortdesc}

## Deploying apps by using DevOps toolchains
{: #toolchain-deploy-apps}

Open toolchains are available in the Public and Dedicated environments on {{site.data.keyword.Bluemix}}. With a properly configured toolchain, deploying your app is easy. A build-deploy cycle automatically starts with each merge to the master branch in your repo.

You can create a toolchain in these ways:
* Create a toolchain from an app. For more information, see [Deploying your app](/docs/apps?topic=creating-apps-tutorial-scratch#deploy-scratch).
* Use a template to create a toolchain. For more information, see [Creating toolchains](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## Deploying apps by using the CLI
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}} provides a robust CLI and plug-ins and developer tool extensions that integrate with the CLI.

Before you begin, [download and install the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli).

The CLI isn’t supported by Cygwin. Use the tool in a window other than the Cygwin command-line window.
{: important}

  1. Download the code for your app to a new directory to set up your development environment.

  2. Change to the directory where your code is located.

  3.  Update your app code. For example, if you're using an {{site.data.keyword.cloud_notm}} sample application and your app contains the `src/main/webapp/index.html` file, you can modify it and edit the `Thanks for creating ...` line. Ensure that the app runs locally before you deploy it to {{site.data.keyword.cloud_notm}}.

    Take note of the `manifest.yml` file. When you deploy your app to {{site.data.keyword.cloud_notm}}, this file is used to determine your application’s URL, memory allocation, number of instances, and other crucial parameters.

    Also review the `README.md` file, which contains details, such as build instructions.

    If your application is a Liberty app, you must build it before you deploy it again.
    {: note}

  4. Log in to the {{site.data.keyword.cloud_notm}} CLI with your IBMid. If you have multiple accounts, you are prompted to select which account to use. If you do not specify a region with the `-r` flag, you must also choose a region.
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    If your credentials are rejected, you might be using a federated ID. To log in with a federated ID, use the `--sso` flag. For more information, see [Logging in with a federated ID](/docs/iam/federated_id?topic=iam-federated_id#federated_id).
    {: tip}

  5. From your new directory, deploy your app to {{site.data.keyword.cloud_notm}} by using the [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) command.
    ```
    ibmcloud dev deploy <APP_NAME>
    ```
    {: codeblock}

  6. Access your app by running the [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.
