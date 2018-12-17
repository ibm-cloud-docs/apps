---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-12-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Creating an app from scratch
{: #tutorial}

You can create a custom application from scratch by using services and a runtime. You can see how to install the tools you need, build, and run the app locally and deploy it to the cloud.
{: shortdesc}

## Step 1. Install the tools
{: #install-tools}

Install the [{{site.data.keyword.dev_cli_long}}](/docs/cli/index.html).

Docker is installed as part of the Developer Tools. Docker must be running for the build commands to work. You must create a Docker account, run the Docker app, and sign in.

## Step 2. Create an app from scratch
{: #create-devex}

Create a custom app in the {{site.data.keyword.cloud}} dashboard:

1. From the [{{site.data.keyword.cloud_notm}} dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}), select **Create** to create a custom application.

  You can also create a custom app from the [Starter Kits ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/developer/appservice/starter-kits/) page in the {{site.data.keyword.dev_console}}, select **Create** to create a custom application.
  {: tip}

2. Enter your app name. For this tutorial, use `CustomProject`.
3. Enter a unique host name, for example, `abc-devhost`. This host name is your app's route, `abc-devhost.cloud.ibm.com`
4. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/resources/tagging_resources.html).
5. Select your language and framework. Some starter kits might be available only in one language.
6. Select your pricing plan. You can use the free option for this tutorial.
7. Click **Create**.

## Step 3. Add resources (Optional)
{: #add-services}

You can add resources that enhance your app with the cognitive power of Watson, add mobile services, or security services. For this tutorial, add a place to manage your data.

1. From the App Service window, select click **Add Resource**.
2. Select the kind of service you want. For example, select **Data** > **Next** > **Cloudant** > **Next**.
3. Select your pricing plan. You can use the free option for this tutorial.
4. Click **Create**.

## Step 4. Building and running the app locally
{: #build-run}

You can also build the app locally for testing before you push it to the cloud.

1. From the App Service window, click **Download Code** or **Clone your repo** to work with your code locally.
2. Import the app to your integrated development environment.
3. Modify the code.
4. Set up [Git authentication](/docs/services/ContinuousDelivery/git_working.html#git_authentication) by adding a personal access token.
5. Log in to the {{site.data.keyword.cloud_notm}} command line interface. If your organization uses federated logins, use the `-sso` option.

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Set your org and space targets.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. Get the credentials.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Make sure that Docker is running and build your app in a local development container from the directory.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Run your app in a local development container.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. Open your browser to `http://localhost:3000`. Your port number might be different depending on your chosen runtime.

## Step 5. Deploy your app
{: #deploy}

You can deploy your app to {{site.data.keyword.cloud_notm}} several ways, but a DevOps toolchain is the best way to deploy production apps. With a DevOps toolchain, you can easily automate deployments to lots of environments and quickly add monitoring, logging, and alert services to help manage your app as it grows.

Enabling a toolchain creates a team-based development environment for your app. When you create a toolchain, the app service creates a Git repository, where you can view source code, clone your app, and create and manage issues. You also have access to a dedicated Git lab environment and a continuous delivery pipeline. They're customized to the deployment platform you choose, whether it's Kubernetes or Cloud Foundry.

All toolchains that are created from an {{site.data.keyword.cloud_notm}} Developer dashboard are configured for automatic deployment.
{: note}

### Manual deployment with a DevOps toolchain

With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the Master branch in your repo. 

You can also manually deploy your app from your DevOps toolchain:

1. From the App Details window, click **View Toolchain**.
2. Click **Delivery pipeline** where you can start builds, manage deployment and view logs and history.

Continuous delivery is enabled for some applications. You can enable continuous delivery to automate builds, tests, and deployments through the Delivery Pipeline and GitHub.

For more information, see:
* [Building and deploying](/docs/services/ContinuousDelivery/pipeline_build_deploy.html) with Continuous Delivery.
* [Creating toolchains](/docs/services/ContinuousDelivery/toolchains_working.html) from a template.

### Automatic deployment with a DevOps toolchain

1. From the App Details page, click **Deploy to Cloud**.
2. Select a deployment method. Set up your deployment method according to the instructions for the method you choose:
  * Deploy to a Kubernetes Cluster. Create a cluster of hosts, called worker nodes, to deploy and manage highly available application containers. You can create a cluster or deploy to an existing cluster.
  * Deploy with Cloud Foundry, where you don’t need to manage the underlying infrastructure.
  * Deploy to a Virtual Server Instance.

Deploying your app to the cloud in the last step creates a toolchain automatically. The toolchain creates a Git repository for your app where you can find the code. 

### Deploy by using the {{site.data.keyword.dev_cli_short}}

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

## Step 6. Verify that your app is running
{: #verify}

After you deploy your app, the DevOps pipeline or command line points you to the URL for your app, for example `abc-devhost.cloud.ibm.com`. Go to that URL in your browser.
