---

copyright:
  years: 2016, 2019
lastupdated: "2019-11-07"

keywords: scratch, developer tools, custom app, app tutorial, basic starter kit, language, backend, mobile

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Creating a custom app from a basic starter kit
{: #tutorial-scratch}

You can create a custom application by using a basic starter kit and selecting the app type (mobile or backend), language, and framework. adding services, and selecting your deployment target. 
{: shortdesc}

The basic starter kit is a versatile tool that you can use to create custom apps that you define by language, app type, framework, and services. Then, you set up continuous delivery and select the deployment target of your choice.

## Before you begin
{: #prereqs-scratch}

* Install the [{{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-getting-started), which include Docker. 
* Create a Docker account, run the Docker app, and sign in. Docker must be running for the build commands to work.
* If you plan to deploy your app to {{site.data.keyword.cfee_full}}, you must [prepare your {{site.data.keyword.cloud_notm}} account](/docs/cloud-foundry?topic=cloud-foundry-permissions).
* If you plan to deploy your app to a Kubernetes or OpenShift cluster, you must create a cluster. For more information, see [Deploying apps to Kubernetes clusters](/docs/containers?topic=containers-app) or [Deploying apps in OpenShift clusters](/docs/openshift?topic=openshift-openshift_apps).
* If you plan to deploy your app by using Knative:
  * Create a paid Kubernetes cluster with at least three worker nodes with 16GM RAM each.
  * Ensure that the Knative and Istio addons are installed into your Kubernetes cluster. For more information, see [Setting up Knative in your cluster](/docs/containers?topic=containers-serverless-apps-knative#knative-setup).

## Creating your app
{: #create-scratch}

1. From your [{{site.data.keyword.cloud_notm}} dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}), click **Create an app** in the Apps tile.

  You can also create a custom app from the [Starter Kits ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}/developer/appservice/starter-kits) page in the {{site.data.keyword.dev_console}}.
  {: tip}

2. On the App details page, enter a name for your app. For this tutorial, type `CustomApp`.
3. You can optionally provide tags to classify your app. For more information, see [Working with tags](/docs/resources?topic=resources-tag).
4. Select the **Create a new app** tile.
5. Select an app type of **Backend**.
  If you select **Mobile** as the app type, see [Creating a custom mobile app](docs/apps/tutorials?topic=creating-apps-tutorial-mobile#create-mobile-basic) for instructions.
  {: tip}
6. Select the language and framework that you want to use for your app. Some starter kits might be available in only one language.
7. Click **Create**.

Great start! You just created an app!

## Adding services (optional)
{: #resources-scratch}

You can add services that enhance your app with the cognitive power of Watson, add mobile services, or security services.

If you want to create a new service instance or connect any existing services to your app, complete these steps:

1. On the App details page, click **Create service** or **Connect existing services**, depending on whether you already have services that you want to connect to this app.
2. Select the kind of service you want, and follow the prompts to either add an existing service to your app or create a service instance. For example, select **Data** > **Next** > **Cloudant** > **Next**.
3. Select your pricing plan. You can use the free option for this tutorial.
4. Click **Create**.

After you add all the services that you want, the services are displayed in the App details page.

## Deploying your app
{: #deploy-scratch}

To deploy your app, you must select your deployment target and configure continuous delivery. This process automatically creates a toolchain and starts the app deployment.

To deploy your app, complete the following steps:

1. On the App details page, click **Configure continuous delivery**.
2. Select a deployment target and complete the information according to the instructions for the target that you select:
  * **Deploy to IBM Kubernetes Service**. With this option, you can create a cluster or deploy to an existing cluster. For more information, see [Deploying apps to Kubernetes clusters](/docs/containers?topic=containers-app) or [Deploying apps in OpenShift clusters](/docs/openshift?topic=openshift-openshift_apps). Select a deployment type of **Helm**, **Knative**, or **OpenShift**. The **Knative** type is available only if Knative is installed. For more information, see [Deploying serverless apps with Knative](/docs/containers?topic=containers-serverless-apps-knative).
  * **Deploy to Cloud Foundry**. This option deploys your cloud-native app without you needing to manage the underlying infrastructure. If your account has access to {{site.data.keyword.cfee_full_notm}}, you can select a deployer type of either **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** or **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**, which you can use to create and manage isolated environments for hosting Cloud Foundry apps exclusively for your enterprise.
  * **Deploy to a Virtual Server**. This option provisions a virtual server instance, loads an image that includes your app, creates a DevOps toolchain, and initiates the first deployment cycle for you. For more information, see [Deploying apps to a virtual server](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server).
    VSI deployment is available for some starter kits. To use this feature, go to the [{{site.data.keyword.cloud_notm}} dashboard](https://{DomainName}), and click **Create an app** in the **Apps** tile.
    {: note}
3. Click **Next**.
4. On the Configure toolchain page, provide the required information, and click **Create**.

The DevOps toolchain is created, and the app deployment starts automatically. The App details page indicates that continuous delivery is configured.

  You can deploy your app from the command line by running the [**ibmcloud dev deploy**](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) command. For more information, see [Deploying apps with the CLI](/docs/apps?topic=creating-apps-deploying-apps#deploy-cli).
  {: note}

For more information about deploying your app, see [Deploying apps](/docs/apps?topic=creating-apps-deploying-apps).

## Checking the deployment status
{: #status-scratch}

The DevOps toolchain for your app includes a Delivery Pipeline tool where you can check the deployment status, start builds, manage deployment, and view logs and history.

To check the deployment status of your app, complete the following steps:

1. On the App details page, click **View toolchain**.
2. From your DevOps toolchain, click **Delivery Pipeline**.

The Build Stage and Deploy Stage tiles indicate the status.

## Verifying that your app is running
{: #verify-scratch}

After your app is built and deployed, you can view the app's URL to make sure that it's running.

### Apps that are deployed to a Kubernetes cluster
{: #view-kube-app-scratch}

For apps that are deployed to a Kubernetes cluster, you can view the app's URL in either the Delivery Pipeline or the command line.

1. On the App details page, click **View toolchain**.
1. From your DevOps toolchain, click **Delivery Pipeline**, and then select **Deploy Stage**.
2. Click **View logs and history**.
3. In the log file, find the app's URL:

    At the end of the log file, search for the word `urls` or `view`. For example, you might see a line in the log file that's similar to `urls: my-app-devhost.mybluemix.net` or `View the application health at: http://<ipaddress>:<port>/health`.

4. Go to the URL in your browser. If the app is running, a message that includes `Congratulations` or `{"status":"UP"}` is displayed.

If you are using the command line, run the [**ibmcloud dev view**](/docs/cli/idt?topic=cloud-cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

### Viewing your app's Kubernetes cluster
{: #view-kube-cluster-scratch}

If you want to view the cluster where your app is deployed, click **View Kubernetes cluster** on the App details page.

### Apps that are deployed to Cloud Foundry
{: #view-cf-app-scratch}

For apps that are deployed to Cloud Foundry, you can view the app's URL from the App details page by clicking **Visit App URL**. If the app is running, a message that includes `Congratulations` is displayed.

If you are using the command line, run the [**ibmcloud dev view**](/docs/cli/idt?topic=cloud-cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

## Next steps
{: #scratch-next-steps}

* Download your app for local development where you can easily build, test, and deploy by using the {{site.data.keyword.cloud}} CLI. This is useful for debugging issues, and adding features or services, and when you are ready, you can re-deploy your app to the cloud. For more information, see [Developing apps locally](/docs/apps?topic=creating-apps-local-app-development).
