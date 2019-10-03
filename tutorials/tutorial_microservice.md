---

copyright:
  years: 2016, 2019
lastupdated: "2019-09-27"

keywords: apps, microservice, developer tools, Node.js, Java, Python, DevOps toolchain, toolchain, cli, create microservice, microservice tutorial

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Creating microservice apps
{: #tutorial-microservice}

You can create an application from a Microservice Basic Starter. Use these starters to build a microservice backend for Node, Java, or Python with a choice of web frameworks. You can see how to install the tools you need, build, and run the app locally and deploy it to the cloud.
{: shortdesc}

## Installing the tools
{: #prereqs-microservice}

* Install the [developer tools](/docs/cli?topic=cloud-cli-getting-started).
* Docker is installed as part of the developer tools. Docker must be running for the build commands to work. You must create a Docker account, run the Docker app, and sign in.
* If you plan to deploy your app to [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-what-is-cloud-foundry), you must [prepare your {{site.data.keyword.cloud_notm}} account](/docs/cloud-foundry?topic=cloud-foundry-permissions).
* If you plan to deploy your app to a Kubernetes or OpenShift cluster, you must create a cluster. For more information, see [Deploying apps to Kubernetes clusters](/docs/containers?topic=containers-app) or [Deploying apps in OpenShift clusters](/docs/openshift?topic=openshift-openshift_apps).
* If you plan to deploy your app with Knative, you must first ensure that Knative is installed, and you must create a cluster. For more information, see [Setting up Knative in your cluster](/docs/containers?topic=containers-serverless-apps-knative#knative-setup).

## Creating your app
{: #create-microservice}

You can use a starter kit to create a microservice app, such as Python Microservice with Flask. To locate the starter kits and create an app, complete these steps:

1. Go to the [App Service Starter Kits](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") page in the {{site.data.keyword.dev_console}} console, and select a starter kit for your language. For example, for a Node.js app, go to **Express.js Microservice** and click **Select Starter Kit**.
2. Type `microservice` in the search bar to filter the list of starter kits.
3. Select a microservice starter kit, such as Python Microservice with Flask.
4. In the App details page for the starter kit, name your app, and select a resource group.
5. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/resources?topic=resources-tag).
7. Optional. To inspect your code before you add services or deploy your app, click **View source code**. The app code includes a `README.md` file that contains technical details about the app. Check the `README.md` file to find out whether you need to take more actions to get your app up and running.
8. Click **Create**.

Great start! You just created an app!

## Adding services (optional)
{: #resources-microservice}

If a starter kit requires specific services, the auto-provisioned service instances are automatically created and connected to your app. You can add services that enhance your app with the cognitive power of Watson, add mobile services, or security services.

If you want to create a new service instance or connect any existing services to your app, complete these steps:

1. On the App details page, click **Create service** or **Connect existing services**, depending on whether you already have services that you want to connect to this app.
2. Select the kind of service you want, and follow the prompts to either add an existing service to your app or create a service instance.

After you add all the services that you want, the services are displayed in the App details page.

## Selecting a deployment target and configuring continuous delivery
{: #toolchain-microservice}

When you select a deployment target, a DevOps toolchain is automatically created for your app. The toolchain includes a Delivery Pipeline that indicates your app’s deployment status. The new app that is generated is pushed to a GitLab repo that is part of the toolchain.

Enabling a DevOps toolchain creates a team-based development environment for your app. When you create a toolchain, the app service creates a Git repository, where you can view source code, clone your app, and create and manage issues. You also have access to a dedicated GitLab environment and a continuous delivery pipeline. They're customized to the deployment target that you select.

All toolchains that are created from an {{site.data.keyword.cloud_notm}} Developer dashboard are configured for automatic deployment.
{: note}

To select your deployment target and configure continuous delivery, complete these steps:

1. On the App details page, click **Configure continuous delivery**.
2. Select a deployment target. Set up your deployment target according to the instructions for the target that you select:
  * **Deploy to IBM Kubernetes Service**. With this option, you can create a cluster or deploy to an existing cluster. For more information, see [Deploying apps to Kubernetes clusters](/docs/containers?topic=containers-app) or [Deploying apps in OpenShift clusters](/docs/openshift?topic=openshift-openshift_apps). Select a deployment type of **Helm**, **Knative**, or **OpenShift**. The **Knative** type is available only if Knative is installed. For more information, see [Deploying serverless apps with Knative](/docs/containers?topic=containers-serverless-apps-knative).
  * **Deploy to Cloud Foundry**. This option deploys your cloud-native app without you needing to manage the underlying infrastructure. If your account has access to {{site.data.keyword.cfee_full_notm}}, you can select a deployer type of either **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** or **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**, which you can use to create and manage isolated environments for hosting Cloud Foundry apps exclusively for your enterprise.
  * **Deploy to a Virtual Server**. This option provisions a virtual server instance, loads an image that includes your app, creates a DevOps toolchain, and initiates the first deployment cycle for you. For more information, see [Deploying apps to a virtual server](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server).

    VSI deployment is available for some starter kits. To use this feature, go to the [{{site.data.keyword.cloud_notm}} dashboard](https://{DomainName}), and click **Create an app** in the **Apps** tile.
    {: note}

After you select and configure the deployment target, the App details page indicates that continuous delivery is configured. You can view the repo that contains the generated code for your app by clicking **View repo**.

## Building and running your app locally
{: #build-run-microservice}

You can view your app code by clicking **Download code** on the App details page of your app. Your code is downloaded as a `.zip` file that contains the complete app code structure. You can extract the file and run the code locally by using the {{site.data.keyword.dev_cli_notm}}, or add it to your code management repository.

The app code includes a `README.md` file that contains technical details about the app. Check the `README.md` file to find out whether you need to take more actions to get your app up and running.
{: tip}

If you want to build the app locally for testing before you deploy it to the cloud, complete these steps:

1. On the **App details** page, click **Download code** to work with your code locally.
2. Import the app to your integrated development environment.
3. Modify the code.
4. Set up [Git authentication](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) by adding a personal access token.
5. Log in to the {{site.data.keyword.cloud_notm}} command-line interface (CLI). If your organization uses federated logins, use the `-sso` option; for example:

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
{: #deploy-microservice}

DevOps toolchains that are created from the {{site.data.keyword.cloud_notm}} developer dashboard are configured for automatic deployment.
{: note}

After you select your deployment target, open the pipeline component of your new toolchain to start the initial build and deployment process so that you can see your new app in minutes.

1. On the App details page, click **View toolchain**.
2. Click **Delivery Pipeline** where you can start builds, manage deployment, and view logs and history.

With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the master branch in your repo. For more information, see [Building and deploying](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

You can deploy your app from the command line by running the [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) command. For more information, see [Deploying apps with the CLI](/docs/apps?topic=creating-apps-deploying-apps#deploy-cli).

### Deploying by using a toolchain
{: #deploy-microservice-toolchain}

You can deploy your app to {{site.data.keyword.cloud_notm}} several ways, but a DevOps toolchain is the best way to deploy production apps. With a DevOps toolchain, you can easily automate deployments to lots of environments and quickly add monitoring, logging, and alert services to help manage your app as it grows.

With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the Master branch in your repo. All toolchains that are created from an {{site.data.keyword.cloud_notm}} developer dashboard are configured for automatic deployment.

You can also manually deploy your app from your DevOps toolchain:

1. On the **App details** page, click **View toolchain**.

2. Click **Delivery Pipeline** where you can start builds, manage deployment and view logs and history.

### Deploying by using the {{site.data.keyword.dev_cli_short}}
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

For more information about deploying your app, see [Deploying apps](/docs/apps?topic=creating-apps-deploying-apps).

## Verifying that your app is running
{: #verify-microservice}

After you deploy your app, the Delivery Pipeline or command line points you to the URL for your app.

1. From your DevOps toolchain, click **Delivery Pipeline**, and then select **Deploy Stage**.
2. Click **View logs and history**.
3. In the log file, find the app's URL:

    At the end of the log file, search for the word `urls` or `view`. For example, you might see a line in the log file that's similar to `urls: my-app-devhost.mybluemix.net` or `View the application health at: http://<ipaddress>:<port>/health`.

4. Go to the URL in your browser. If the app is running, a message that includes `Congratulations` or `{"status":"UP"}` is displayed.

If you are using the command line, run the [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.