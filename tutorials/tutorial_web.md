---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-01"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creating a basic web app with a starter kit
{: #tutorial-webapp}

{{site.data.keyword.cloud}} offers many starter kits to help you get coding quickly. Choose a language, framework, and tools from the App Service starter kits to start working with a pre-configured custom app. In this tutorial, you walk through the steps to install the tools you need, and then build and run the app locally and deploy it to the cloud.
{: shortdesc}

## Step 1. Install the tools
{: #prereqs-webapp}

Install the [developer tools](/docs/cli/index.html#overview).

Docker is installed as part of the developer tools. Docker must be running for the build commands to work. You must create a Docker account, run the Docker app, and sign in.

## Step 2. Select a starter kit
{: #create-webapp}

Starter kits are available in many languages and frameworks in the {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}. Select the language that's best for your project to get started.

1. From the [starter kits ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/developer/appservice/starter-kits/) page in the {{site.data.keyword.dev_console}}, select a starter kit for your language.
2. Enter your app name and a unique host name, for example, `abc-devhost`. This host name is your app's route, `abc-devhost.cloud.ibm.com`
3. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/resources/tagging_resources.html#tag).
4. Select your language and framework. Some starter kits might be available only in one language.
5. Select your pricing plan. There is a free option that you can use for this tutorial.
6. Click **Create**.

## Step 3. Add resources (Optional)
{: #resources-webapp}

You can add resources that enhance your app with the cognitive power of Watson, add mobile services, or security services. For this tutorial, add a place to manage your data.

1. From the app service window, select click **Add Resource**.
2. Select the kind of service you want. For example, select **Data** > **Next** > **Cloudant** > **Next**.
3. Select your pricing plan. There is a free option that you can use for this tutorial.
4. Click **Create**.

## Step 4. Create a DevOps toolchain
{: #toolchain-webapp}

Enabling a toolchain creates a team-based development environment for your app. When you create a toolchain, the app service creates a Git repository, where you can view source code, clone your app, and create and manage issues. You also have access to a dedicated Git lab environment and a continuous delivery pipeline. They're customized to the deployment environment you choose, whether it's [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about), or [Virtual Server (VSI)](/docs/vsi/vsi_index.html).

Continuous delivery is enabled for some applications. You can enable continuous delivery to automate builds, tests, and deployments through the Delivery Pipeline and GitHub.

Click **Deploy to Cloud** on the App details page, select a deployment environment, and click **Create**. {{site.data.keyword.cloud_notm}} automatically creates an open toolchain complete with a Git repository and continuous delivery pipeline.

After you select your deployment environment, open the pipeline component of your new toolchain to start the initial build and deployment process so that you can see your new app in minutes.

For more information, see [Creating toolchains](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

## Step 5. Build and run the app locally
{: #build-run-webapp}

Deploying your app to the cloud in the last step created a toolchain. A toolchain creates a Git repository for your app where you can find the code there. Follow these steps to access your repo. You can build the app locally for testing before you push it to the cloud.

1. From the app service window, click **Download Code** or **Clone your repo** to work with your code locally.
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

## Step 6. Deploy your app
{: #deploy-webapp}

### Deploy by using a toolchain
{: #deploy-webapp-toolchain}

You can deploy your app to {{site.data.keyword.cloud_notm}} several ways, but a DevOps toolchain is the best way to deploy production apps. With a DevOps toolchain, you can easily automate deployments to lots of environments and quickly add monitoring, logging, and alert services to help manage your app as it grows.

With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the Master branch in your repo. All toolchains that are created from an {{site.data.keyword.cloud_notm}} developer dashboard are configured for automatic deployment.

You can also manually deploy your app from your DevOps toolchain:

1. From the App Details window, click **View Toolchain**.
2. Click **Delivery pipeline** where you can start builds, manage deployment and view logs and history.

For more information, see [Building and deploying](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy).

### Deploy by using the {{site.data.keyword.dev_cli_short}}
{: #deploy-webapp-cli}

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
{: #verify-webapp}

After you deploy your app, the DevOps pipeline or command line points you to the URL for your app, for example `abc-devhost.cloud.ibm.com`. Go to that URL in your browser.
