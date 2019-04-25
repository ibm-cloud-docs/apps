---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-25"

keywords: apps, microservice, developer tools, Node.js, Java, Python, DevOps toolchain, toolchain, cli, create microservice, microservice tutorial

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Creating a microservice
{: #tutorial-microservice}

You can create an application from a Microservice Basic Starter. Use these starters to build a microservice backend for Node, Java, or Python with a choice of web frameworks. You can see how to install the tools you need, build, and run the app locally and deploy it to the cloud.
{: shortdesc}

## Step 1. Install the tools
{: #prereqs-microservice}

* Install the [developer tools](/docs/cli?topic=cloud-cli-ibmcloud-cli).
* Docker is installed as part of the developer tools. Docker must be running for the build commands to work. You must create a Docker account, run the Docker app, and sign in.
* If you plan to deploy your app to [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), you must [prepare your {{site.data.keyword.cloud_notm}} account](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Step 2. Create an app
{: #create-microservice}

Create an app in the {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}:

1. From the [Starter Kits](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon") page in the {{site.data.keyword.dev_console}}, select a Starter Kit for your language. For example, for a Node.js application, go to **Express.js Microservice** and click **Select Starter Kit**.
2. Enter your app name. For this tutorial, use `MicroserviceProject`.
3. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/resources?topic=resources-tag).
4. Select your language and framework. Some starter kits might be available only in one language.
5. Select your pricing plan. There is a free option that you can use for this tutorial.
6. Click **Create**.

## Step 3. Add services (Optional)
{: #resources-microservice}

You can add services that enhance your app with the cognitive power of Watson, add mobile services, or security services. For this tutorial, add a place to manage your data.

1. On the **App details** page, click **Add service**.
2. Select the kind of service you want. For example, select **Data** > **Next** > **Cloudant** > **Next**.
3. Select your pricing plan. There is a free option that you can use for this tutorial.
4. Click **Create**.

## Step 4. Create a DevOps toolchain
{: #toolchain-microservice}

Enabling a toolchain creates a team-based development environment for your app. When you create a toolchain, the app service creates a Git repository, where you can view source code, clone your app, and create and manage issues. You also have access to a dedicated Git lab environment and a continuous delivery pipeline. They're customized to the deployment target you choose, whether it's [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about), or [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers).

All toolchains that are created from an {{site.data.keyword.cloud_notm}} Developer dashboard are configured for automatic deployment.
{: note}

1. On the **App details** page, click **Configure continuous delivery**.
2. Select a deployment target. Set up your deployment target according to the instructions for the method you choose:
  * **Deploy to [IBM Kubernetes Service](/docs/apps/deploying?topic=creating-apps-containers-kube)**. This option creates a cluster of hosts, called worker nodes, to deploy and manage highly available application containers. You can create a cluster or deploy to an existing cluster.
  * **Deploy to Cloud Foundry**. This option deploys your cloud-native app without you needing to manage the underlying infrastructure. If your account has access to {{site.data.keyword.cfee_full_notm}}, you can select a deployer type of either **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)** or **[Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**, which you can use to create and manage isolated environments for hosting Cloud Foundry applications exclusively for your enterprise.
  * **Deploy to a [Virtual Server](/docs/apps?topic=creating-apps-vsi-deploy)**. This option provisions a virtual server instance, loads an image that includes your app, creates a DevOps toolchain, and initiates the first deployment cycle for you.

## Step 5. Build and run the app locally
{: #build-run-microservice}

Deploying your app to the cloud in the last step created a toolchain. A toolchain creates a Git repository for your app where you can find the code there. Follow these steps to access your repo. You can build the app locally for testing before you push it to the cloud.

1. On the **App details** page, click **Download code** or **Clone your repo** to work with your code locally.
2. Import the app to your integrated development environment.
3. Modify the code.
4. Set up [Git authentication](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) by adding a personal access token.
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

7.  Get the credentials.

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

10.  Open your browser to `http://localhost:3000`. Your port number might be different depending on your chosen runtime.

## Step 6. Deploy your app
{: #deploy-microservice}

### Deploy by using a toolchain
{: #deploy-microservice-toolchain}

You can deploy your app to {{site.data.keyword.cloud_notm}} several ways, but a DevOps toolchain is the best way to deploy production apps. With a DevOps toolchain, you can easily automate deployments to lots of environments and quickly add monitoring, logging, and alert services to help manage your app as it grows.

With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the Master branch in your repo. All toolchains that are created from an {{site.data.keyword.cloud_notm}} developer dashboard are configured for automatic deployment.

You can also manually deploy your app from your DevOps toolchain:

1. On the **App details** page, click **View toolchain**.

2. Click **Delivery Pipeline** where you can start builds, manage deployment and view logs and history.

### Deploy by using the {{site.data.keyword.dev_cli_short}}
{: #deploy-microservice-cli}

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

## Step 7. Verify that your app is running
{: #verify-microservice}

After you deploy your app, the Delivery Pipeline or command line points you to the URL for your app.

1. From your DevOps toolchain, click **Delivery Pipeline**, and then select **Deploy Stage**.
2. Click **View logs and history**.
3. In the log file, find the application URL:

    At the end of the log file, search for the word `urls` or `view`. For example, you might see a line in the log file that's similar to `urls: my-app-devhost.mybluemix.net` or `View the application health at: http://<ipaddress>:<port>/health`.

4. Go to the URL in your browser. If the app is running, a message that includes `Congratulations` or `{"status":"UP"}` is displayed.

If you are using the command line, run the [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.