---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-03-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creating a custom application
{: #tutorial}

You can create a custom application using services and a runtime. You can see how to install the tools you need, build and run the project locally and deploy it to the cloud.
{: shortdesc}

## Step 1: Install the tools
{: #before-you-begin}

Install the [developer tools ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.

## Create a project
{: #create-devex}

Create a project in the {{site.data.keyword.Bluemix}} {{site.data.keyword.dev_console}}:

1. From the [**Starter Kits** ![External link icon](../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) page in the {{site.data.keyword.dev_console}}, select **Create Project** to create a custom application.

2. Enter your project name. For this tutorial, use `CustomProject`.   

3. Enter a unique host name, such as your initials plus `-devhost`. For example:

	```
	abc-devhost
	```

	This host name is your project's route. For example, `abc-devhost.mybluemix.net`

4. Select your language platform. For this tutorial, use `Node.js`.

5. (Optional) You can start the scaffolding of your backend from an OpenAPI document. This is useful for a backend developer who already has their client and backend integration contract defined in a Swagger document. File types of **.yaml** and **.json** are supported. Click **Add file** to upload your document.

6. Click **Create Project**.

## Optional: Add services
{: #add-services}

1. Select your project in the **Projects** page.

2. Click **Add Service**.

3. Select the kind of service you want. For this tutorial, select **Data** > **Next** > **Cloudant NoSQL DB** > **Next**.

4. Enter your service name and click **Create**.

## Optional: Create DevOps toolchain
{: #add-toolchain}

Enabling a toolchain creates a team-based development environment for your project. When you create a toolchain, the App Service will provision a Git repository, where you can view source code, clone your project and create and manage issues. You also have access to a dedicated Gitlab environment and a continuous Delivery Pipeline that is customized to the deployment platform you choose, such as Kubernetes or Cloud Foundry.

Continuous delivery is enabled for some applications. You may want to enable continuous delivery to automate builds, tests, and deployments through the Delivery Pipeline and GitHub.

1. Select your project in the **Projects** page.

2. Click **Create Toolchain**.

3. Select a deployment method. You may choose to either:

	1. Deploy using Cloud Foundry, where you don't need to manage the underlying infrastructure.

	2. Deploy to a Kubernetes Cluster. Provision a cluster of hosts, called worker nodes, to deploy and manage highly available application containers. You may create a cluster or deploy to an existing cluster.

## Generate your project code
{: #generate-code}

If you created a toolchain in the previous step, a Git repository was created for your project. Follow these steps to access your repo:

1. Select your project in the **Projects** page.

2. Click **View Toolchain**.

3. Click the **Git** card under the heading **CODE** to open your repository, where you can view source code and clone your project.

If a toolchain isn’t enabled, you can access your code by downloading the source directly from the App Service.

1. Select your project in the **Projects** page.

2. Click **Download Code** to download your project archive.


## Begin working on your app
{: #code}

Begin working with your downloaded project:

1. Expand the archived file.

2. Navigate to the new project directory.

3. Use the {{site.data.keyword.dev_cli_notm}} to proceed.


## Build and run the app locally
{: #build-run}

Add your own code, build, and run the project. You can run the application locally on your host system if you install the necessary build tools, or by using the available container support in the {{site.data.keyword.dev_cli_notm}}.

### Using the {{site.data.keyword.dev_cli_short}}

1. To build the project in your current project directory, enter the following command:

  ```
  bx dev build
  ```
  {: codeblock}

2. To run the project in your current project directory, enter the following command:

  ```
  bx dev run
  ```
  {: codeblock}

5. Open your browser to `http://localhost:3000` (your port number may be different depending on the chosen runtime).


## Deploy to the cloud
{: #deploy}

### Deploy using a toolchain
There are several ways to deploy your app to {{site.data.keyword.cloud_notm}} but using a DevOps toolchain is the best way to deploy production apps.  A DevOps toolchain allows you to easily automate deployments to multiple environments and to quickly add monitoring, logging, and alerting services to help manage your app as it grows.

To deploy from your DevOps toolchain:

1. Select your project in the **Projects** page.

2. Click **View Toolchain**.

3. View your delivery pipeline where you can start builds, manage deployment and view logs and history.

### Deploy using {{site.data.keyword.dev_cli_short}}
If you choose not to use a toolchain, you can also deploy using the {{site.data.keyword.dev_cli_short}}.

To deploy your project to Cloud Foundry, enter the following command:

  ```
  bx dev deploy
  ```
  {: codeblock}

To deploy your project to a Kubernetes cluster, enter the following command:

```
bx dev deploy --target <container>
```
{: codeblock}

### See your app running
Once the application is deployed, you’ll see a URL similar to `abc-devhost.mybluemix.net` in the DevOps pipeline or in the terminal (if you’re using command line). Visit this URL in your browser.