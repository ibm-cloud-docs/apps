---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-22"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creating a custom application
{: #tutorial}

You can create a custom application using services and a runtime. You can see how to install the tools you need, build and run the app locally and deploy it to the cloud.
{: shortdesc}

## Step 1: Install the tools
{: #before-you-begin}

Install the [developer tools ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.

## Step 2: Create an app
{: #create-devex}

Create a app in the {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}:

1. From the [Starter Kits ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) page in the {{site.data.keyword.dev_console}}, select **Create** to create a custom application.

2. Enter your app name. For this tutorial, use `CustomProject`.   

3. Enter a unique host name, such as your initials plus `-devhost`. For example:

	```
	abc-devhost
	```

	This host name is your app's route. For example, `abc-devhost.mybluemix.net`

4. Select your language platform. For this tutorial, use `Node.js`.

5. (Optional) You can start the scaffolding of your backend from an OpenAPI document. This is useful for a backend developer who already has their client and backend integration contract defined in a Swagger document. File types of **.yaml** and **.json** are supported. Click **Add file** to upload your document.

6. Click **Create**.

## Optional: Add resources
{: #add-services}

1. From the **App Details** view, select click **Add Resource**.

2. Select the kind of service you want. For this tutorial, select **Data** > **Next** > **Cloudant NoSQL DB** > **Next**.

3. Click **Create**.

## Optional: Create DevOps toolchain
{: #add-toolchain}

Enabling a toolchain creates a team-based development environment for your app. When you create a toolchain, the App Service will provision a Git repository, where you can view source code, clone your app and create and manage issues. You also have access to a dedicated Gitlab environment and a continuous Delivery Pipeline that is customized to the deployment platform you choose, such as Kubernetes or Cloud Foundry.

Continuous delivery is enabled for some applications. You may want to enable continuous delivery to automate builds, tests, and deployments through the Delivery Pipeline and GitHub.

1. Select your app in the **Apps** page.

2. Click **Deploy to Cloud**.

3. Select a deployment method. You may choose to either:

	* Deploy to a Kubernetes Cluster. Provision a cluster of hosts, called worker nodes, to deploy and manage highly available application containers. You can create a cluster or deploy to an existing cluster.

	* Deploy using Cloud Foundry, where you don’t need to manage the underlying infrastructure.

## Step 3: Generate your app code
{: #generate-code}

If you created a toolchain in the previous step, a Git repository was created for your app, and you can find the code there. Follow these steps to access your repo:

1. Select your app in the **Apps** page.

2. Click **View Toolchain**.

3. Click the **Git** card under the heading **CODE** to open your repository, where you can view source code and clone your app.

If a toolchain isn’t enabled, you can access your code by downloading the source directly from the App Details view.

1. Select your app in the **Apps** page.

2. Click **Download Code** to download your app archive.

## Step 4: Begin working on your app
{: #code}

Begin working with your downloaded app:

1. Expand the archived file.

2. Import the app to your IDE.

3. Modify the code.

4. Use the {{site.data.keyword.dev_cli_notm}} to build and run your code locally.


## Step 5: Build and run the app locally
{: #build-run}

Add your own code, build, and run the app. You can run the application locally on your host system if you install the necessary build tools, or by using the available container support in the {{site.data.keyword.dev_cli_notm}}.

### Using the {{site.data.keyword.dev_cli_short}}

1. To build the app in your current app directory, enter the following command:

  ```
  ibmcloud dev build
  ```
  {: codeblock}

2. To run the app in your current app directory, enter the following command:

  ```
  ibmcloud dev run
  ```
  {: codeblock}

3. Open your browser to `http://localhost:3000` (your port number may be different depending on the chosen runtime).


## Step 6: Deploy to the cloud
{: #deploy}

### Deploy using a toolchain
There are several ways to deploy your app to {{site.data.keyword.cloud_notm}} but using a DevOps toolchain is the best way to deploy production apps. A DevOps toolchain allows you to easily automate deployments to multiple environments and to quickly add monitoring, logging, and alerting services to help manage your app as it grows.

With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the Master branch in your repo. All toolchains created from an {{site.data.keyword.cloud_notm}} developer dashboard are configured for automatic deployment.

You can also manually deploy your app from your DevOps toolchain:

1. Select your app in the **Apps** page.

2. Click **View Toolchain**.

3. View your delivery pipeline where you can start builds, manage deployment and view logs and history.

### Deploy using {{site.data.keyword.dev_cli_short}}
If you choose not to use a toolchain, you can also deploy using the {{site.data.keyword.dev_cli_short}}.

To deploy your app to Cloud Foundry, enter the following command:

  ```
  ibmcloud dev deploy
  ```
  {: codeblock}

To deploy your app to a Kubernetes cluster, enter the following command:

```
ibmcloud dev deploy --target <container>
```
{: codeblock}

### See your app running
Once the application is deployed, you’ll see a URL similar to `abc-devhost.mybluemix.net` in the DevOps pipeline or in the terminal (if you’re using command line). Visit that URL in your browser.
