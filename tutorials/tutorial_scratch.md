---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Creating an app from scratch
{: #tutorial-scratch}

You can create a custom application from scratch by using services and a runtime. 
{: shortdesc}

## Before you begin
{: #prereqs-scratch}

* Install the [{{site.data.keyword.dev_cli_long}}](/docs/cli/index.html), which include Docker. 
* Create a Docker account, run the Docker app, and sign in. Docker must be running for the build commands to work.
* If you plan to deploy your app to [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about), you must [prepare your {{site.data.keyword.cloud_notm}} account](/docs/cloud-foundry/prepare-account.html#prepare).

## Creating your app
{: #create-scratch}

1. From your [{{site.data.keyword.cloud_notm}} dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://cloud.ibm.com), click **Create an app** in the Apps widget.

  You can also create a custom app from the [Starter Kits ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/developer/appservice/starter-kits/) page in the {{site.data.keyword.dev_console}}.
  {: tip}

2. Enter a name for your app. For this tutorial, type `CustomProject`.
3. Enter a unique host name, for example, `abc-devhost`. The host name is used for your app's route, for example, `abc-devhost.cloud.ibm.com`
4. You can optionally provide tags to classify your app. For more information, see [Working with tags](/docs/resources/tagging_resources.html#tag).
5. Select your language and framework. Some starter kits might be available in only one language.
6. Select your pricing plan. You can use the free option for this tutorial.
7. Click **Create**.

## Adding resources (optional)
{: #resources-scratch}

You can add resources that enhance your app with the cognitive power of Watson, add mobile services, or security services. For this tutorial, you can add a place to manage your data.

1. From the App Service window, select click **Add Resource**.
2. Select the kind of service you want. For example, select **Data** > **Next** > **Cloudant** > **Next**.
3. Select your pricing plan. You can use the free option for this tutorial.
4. Click **Create**.

## Building and running the app locally
{: #build-run-scratch}

You can also build the app locally for testing before you deploy it to the cloud.

1. From the App Service window, click **Download Code** or **Clone your repo** to work with your code locally.
2. Import the app to your integrated development environment.
3. Modify the code.
4. Set up [Git authentication](/docs/services/ContinuousDelivery/git_working.html#git_authentication) by adding a personal access token.
5. Log in to the {{site.data.keyword.cloud_notm}} command-line interface (CLI). If your organization uses federated logins, use the `-sso` option, for example:

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Run the following command to set your org and space targets.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. Run the following command to retrieve the credentials.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Make sure that Docker is running, and run the following command to build your app in a local development container from the directory.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Run the following command to run your app in a local development container.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. Go to `http://localhost:3000` in your browser. Your port number might be different depending on your chosen runtime.

## Deploying your app
{: #deploy-scratch}

You can deploy your app to {{site.data.keyword.cloud_notm}} several ways, but a DevOps toolchain is the best way to deploy production apps. With a DevOps toolchain, you can easily automate deployments to lots of environments and quickly add monitoring, logging, and alert services to help manage your app as it grows.

Enabling a toolchain creates a team-based development environment for your app. When you create a toolchain, the app service creates a Git repository, where you can view source code, clone your app, and create and manage issues. You also have access to a dedicated Git lab environment and a continuous delivery pipeline. They're customized to the deployment environment you choose, whether it's [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about), or [Virtual Server (VSI)](/docs/vsi/vsi_index.html).

All toolchains that are created from an {{site.data.keyword.cloud_notm}} Developer dashboard are configured for automatic deployment.
{: note}

### Manual deployment with a DevOps toolchain

With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the Master branch in your repo. 

You can also manually deploy your app from your DevOps toolchain:

1. From the App Details window, click **View Toolchain**.
2. Click **Delivery pipeline** where you can start builds, manage deployment and view logs and history.

Continuous delivery is enabled for some applications. You can enable continuous delivery to automate builds, tests, and deployments through the Delivery Pipeline and GitHub.

For more information, see:
* [Building and deploying](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy) with Continuous Delivery.
* [Creating toolchains](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started) from a template.

### Automatic deployment with a DevOps toolchain

1. From the App Details page, click **Deploy to Cloud**.
2. Select a deployment method. Set up your deployment method according to the instructions for the method you choose:
  * **Deploy to [Kubernetes](/docs/apps/deploying/containers.html#containers)**. This option creates a cluster of hosts, called worker nodes, to deploy and manage highly available application containers. You can create a cluster or deploy to an existing cluster.
  * **Deploy to Cloud Foundry**. This option deploys your cloud-native app without you needing to manage the underlying infrastructure. If your account has access to {{site.data.keyword.cfee_full_notm}}, you can select a deployer type of either **[Public Cloud](/docs/cloud-foundry-public/about-cf.html#about-cf)** or **[Enterprise Environment](/docs/cloud-foundry-public/cfee.html#cfee)**, which you can use to create and manage isolated environments for hosting Cloud Foundry applications exclusively for your enterprise.
  * **Deploy to a [Virtual Server](/docs/apps/vsi-deploy.html#vsi-deploy)**. This option provisions a virtual server instance, loads an image that includes your app, creates a DevOps toolchain, and initiates the first deployment cycle for you.

Deploying your app to the cloud in the last step creates a toolchain automatically. The toolchain creates a Git repository for your app where you can find the code. 

### Deploy by using the {{site.data.keyword.dev_cli_short}}
{: #deploy-scratch-cli}

To deploy your app to Cloud Foundry, enter the following command:
```
ibmcloud dev deploy
```
{: pre}

To deploy your app to a Kubernetes cluster, enter the following command:
```
ibmcloud dev deploy --target <container>
```
{: pre}

## Verifying that your app is running
{: #verify-scratch}

After you deploy your app, the Delivery Pipeline or command line points you to the URL for your app.

1. From your DevOps toolchain, click **Delivery Pipeline**, and then select **Deploy Stage**.
2. Click **View logs and history**.
3. In the log file, find the application URL:

    At the end of the log file, search for the word `urls` or `view`. For example, you might see a line in the log file that's similar to `urls: my-app-devhost.cloud.ibm.com` or `View the application health at: http://<ipaddress>:<port>/health`.

4. Go to the URL in your browser. If the app is running, a message that includes `Congratulations` or `{"status":"UP"}` is displayed.

If you are using the command line, run the [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) command to view the URL of your app. Then, go to the URL in your browser.
