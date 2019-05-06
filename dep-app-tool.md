---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-06"

keywords: apps, deploy, deploying apps, toolchain, cli, cloud, devops, deployment, git, push

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

You can deploy your application to {{site.data.keyword.cloud}} by using a DevOps toolchain. With a DevOps toolchain, you can automate deployments to many environments and quickly add monitoring, logging, insights, and alert services to help manage your app as it grows. You can configure continuous delivery and deploy your app by using either the {{site.data.keyword.cloud_notm}} web console or the command-line interface (CLI).
{: shortdesc}

A DevOps toolchain provides a team-based development environment for your app. When you create a toolchain, the app service creates a Git repository, where you can view source code, clone your app, and create and manage issues. You also have access to a dedicated GitLab environment and a continuous delivery pipeline. They're customized to the deployment target that you select, whether it's [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about), or [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers).

All toolchains that are created from the {{site.data.keyword.cloud_notm}} Developer dashboard are configured for automatic deployment.
{: note}

## Using the {{site.data.keyword.cloud_notm}} console
{: deploy-console}

{{site.data.keyword.cloud_notm}} provides a web console where you can configure continous delivery and deploy your app by using a DevOps toolchain.

### Before you begin
{: deploy-console-before}

Before you begin, use the [{{site.data.keyword.cloud_notm}} dashboard](https://{DomainName}){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") to [create your app](/docs/apps?topic=creating-apps-tutorial-getting-started#create-getting-started) and [add services](/docs/apps?topic=creating-apps-tutorial-getting-started#resources-getting-started).

### Automatically deploying your app
{: deploy-console-auto}

1. On the **App details** page, click **Configure continuous delivery**.
2. Select a deployment target. Set up your deployment target according to the instructions for the target that you select:
  * **Deploy to IBM Kubernetes Service**. This option creates a cluster of hosts, called worker nodes, to deploy and manage highly available application containers. You can create a cluster or deploy to an existing cluster. For more information, see [Deploying apps to Kubernetes clusters](/docs/containers?topic=containers-app).
  * **Deploy to Cloud Foundry**. This option deploys your cloud-native app without you needing to manage the underlying infrastructure. If your account has access to {{site.data.keyword.cfee_full_notm}}, you can select a deployer type of either **Public Cloud** or **Enterprise Environment**, which you can use to create and manage isolated environments for hosting Cloud Foundry applications exclusively for your enterprise. For more information, see [Deploying apps to Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps) and [Deploying apps to {{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps).
  * **Deploy to a Virtual Server**. This option provisions a virtual server instance, loads an image that includes your app, creates a DevOps toolchain, and initiates the first deployment cycle for you. For more information, see [Deploying apps to a virtual server](/docs/apps?topic=creating-apps-vsi-deploy).

### Manually deploying your app
{: deploy-console-manual}

With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the master branch in your repo. 

You can also manually deploy your app from your DevOps toolchain:

1. On the **App details** page, click **View toolchain**.
2. Click **Delivery Pipeline** where you can start builds, manage deployment, and view logs and history.

Continuous delivery is automatically enabled for some applications. You can enable continuous delivery to automate builds, tests, and deployments through the Delivery Pipeline and GitHub.

For more information, see:
* [Building and deploying](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)
* [Creating toolchains](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)

## Using the {{site.data.keyword.dev_cli_short}} CLI
{: #deploy-cli}

{{site.data.keyword.cloud_notm}} provides a robust CLI and plugins to help simplify the developer's workflow. You can deploy your {{site.data.keyword.cloud_notm}} app in one of two ways, depending on how your app is configured.

### Before you begin
{: #deploy-cli-before}

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

  4. Log in to the {{site.data.keyword.cloud_notm}} CLI with your IBMid. If you have multiple accounts, you are prompted to select which account to use. If you do not specify a region with the `-r` flag, you must also select a region.
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    If your credentials are rejected, you might be using a federated ID. To log in with a federated ID, use the `--sso` flag. For more information, see [Logging in with a federated ID](/docs/iam/federated_id?topic=iam-federated_id#federated_id).
    {: tip}

### Automatically deploying your app
{: #deploy-cli-auto}

If you didn't create a DevOps toolchain for your app and your app isn't yet in a Git repository, you can run the [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit) command. Follow the prompts for "Configure DevOps" and deploy to a new toolchain (and create a new GitLab repository).

After you create a DevOps toolchain for your app, deploying a new build is as simple as committing and pushing your code to the repository in your toolchain. 

1. Prepare the changes to be committed.
    ```
    git add .
    ```
2. Commit the changes with a brief message.
    ```
    git commit -m "made changes"
    ```
3. Push the commits on the master branch to the remote repository.
    ```
    git push origin master
    ```
4. View the DevOps toolchain for your app from the {{site.data.keyword.cloud_notm}} console. You can view toolchain details from the **App details** page in the {{site.data.keyword.cloud_notm}} console by running the [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) command from the app directory.
5. View the pipeline within the toolchain to verify that a new build started.

### Manually deploying your app
{: #deploy-cli-manual}

You can manually deploy your app to {{site.data.keyword.cloud_notm}} by using the [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) command.

  ```
  ibmcloud dev deploy <APP_NAME>
  ```
  {: codeblock}

### Related information
{: #deploy-cli-related}

For more information about deploying your app to {{site.data.keyword.cloud_notm}} by using the CLI, see:

* [Deploying to IBM Cloud Environments with {{site.data.keyword.dev_cli_short}} CLI](https://www.ibm.com/blogs/bluemix/2019/01/deploying-to-ibm-cloud-environments-with-ibm-cloud-developer-tools-cli/){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon")
