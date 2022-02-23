---

copyright:
  years: 2016, 2022
lastupdated: "2022-02-23"

keywords: scratch, developer tools, custom app, app tutorial, basic starter kit, blank starter kit, language, backend, mobile, blank starter kit
content-type: tutorial
services: apps
account-plan: lite
completion-time: 30m

subcollection: apps

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:external: target="_blank" .external}
{:step: data-tutorial-type='step'}

# Creating a custom app from a blank starter kit
{: #tutorial-scratch}
{: toc-content-type="tutorial"} 
{: toc-services="apps"} 
{: toc-completion-time="30m"}

Use this tutorial to create a custom application by using a blank starter kit. When you create the app, you specify the type (mobile or backend), language, framework, and services, and you select your deployment target. 
{: shortdesc}

## Objectives
{: #objectives-scratch}

* Create an app with a blank starter kit.
* Add services to the app (optional).
* Deploy the app.
* Verify the app.

## Before you begin
{: #prereqs-scratch}

### For all deployment targets
{: #prereq-scratch-deploy-all}

For all deployment targets, ensure that you're aware of the following requirements:

* Depending on your [{{site.data.keyword.cloud_notm}} account type](/registration){: external}, access to certain resources might be limited or constrained. Depending on your plan limits, certain capabilities that are required by some toolchains might not be available. For more information, see [Setting up your IBM Cloud account](/docs/account?topic=account-account-getting-started).
* Install the [{{site.data.keyword.cloud_notm}} Command Line Interface (CLI)](/docs/cli?topic=cli-getting-started), which includes the {{site.data.keyword.dev_cli_short}} (`ibmcloud dev`) commands.
* Create a Docker account, run the Docker app, and sign in. Docker is installed as part of the developer tools. Docker must be running for the build commands to work.

### For specific deployment targets
{: #prereq-scratch-deploy-specific}

For more information about requirements for specific deployment targets, see the following table.

| Deployment target | Prerequisites | 
|--------|---------------|
| {{site.data.keyword.cloud_notm}} Foundry | Ensure that you have access to a [Cloud Foundry org and space](/account/cloud-foundry){: external}. [Learn more](/docs/account?topic=account-orgsspacesusers) or [create a Cloud Foundry org](/account/cloud-foundry){: external}. |
| {{site.data.keyword.cloud_notm}} Kubernetes Service / Helm | Create a free or paid cluster. One free Kubernetes cluster is available per account. For more information, see [Deploying apps to Kubernetes clusters](/docs/containers?topic=containers-app). Helm is a package manager for Kubernetes that allows you to package, configure, and deploy apps and services to {{site.data.keyword.cloud_notm}} Kubernetes Service. With either paid or free account plans, select this option to experiment with your starter kit in a Kubernetes environment. |
| Red Hat OpenShift on {{site.data.keyword.cloud_notm}} | OpenShift is available only through a standard cluster, which requires you to have a billable account. [Learn more](/docs/openshift?topic=openshift-getting-started) or [create an OpenShift cluster](/kubernetes/overview){: external}.|
| {{site.data.keyword.codeenginefull}} | Ensure that you have either a Pay-As-You-Go account or a Subscription account to use {{site.data.keyword.codeengineshort}} as your deployment target. If you are using a free Lite account, upgrade it before you use {{site.data.keyword.codeengineshort}}. [Learn more about accounts.](/docs/account) |

## Creating your app
{: #create-scratch}
{: step}

1. From the [{{site.data.keyword.cloud_notm}} App Development console](/developer/appservice/starter-kits){: external}, click **Get a Starter Kit**.
2. Click the **Create App** tile, and then select the **Create** tab.
3. On the App details page, enter a name your app, and select a resource group. If a resource group doesn't exist, you must [create one](/account/resource-groups){: external}.
4. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/account?topic=account-tag).
5. Select **Create a new app** as a starting point.
6. Select **Backend** as the app type.
   If you select **Mobile** as the app type, see [Creating a custom mobile app](/docs/apps?topic=apps-tutorial-mobile#create-mobile-basic) for instructions.
   {: tip}

7. Select the language and framework that you want to use for your app. Some starter kits might be available in only one language.
8. Click **Create**.

You can view your app code before you deploy it by clicking **Download code** on the App details page. Your code is downloaded as a `.zip` file that contains the complete app code structure. You can extract the file and run the code locally by using the {{site.data.keyword.dev_cli_notm}} (`ibmcloud dev`) commands, or add it to your code management repository.

The app code includes a `README.md` file that contains technical details about the app. Check the `README.md` file to find out whether you need to take more actions to get your app up and running.
{: tip}

## Adding services (optional)
{: #resources-scratch}
{: step}

You can add services that enhance your app with the cognitive power of Watson, add mobile services, or security services.

If you want to create a new service instance or connect any existing services to your app, complete the following steps:

1. On the App details page, click **Create service** or **Connect existing services**, depending on whether you already have services that you want to connect to this app.
2. Select the kind of service you want, and follow the prompts to either add an existing service to your app or create a service instance.

After you add all the services that you want, the services are displayed in the App details page.

After you connect a service to your app, you can navigate to the service documentation and API references. Simply click the links within the **Services** card to view the related docs.

For more information, see [Adding a service to your app](/docs/apps?topic=apps-add-service).

## Deploying your app
{: #deploy-scratch}
{: step}

To deploy your app, you must select your deployment target and configure continuous delivery. This process automatically creates a toolchain and starts the app deployment.

To deploy your app, complete the following steps:

1. On the App details page for your app, click **Deploy your app**.
2. On the Deploy your app page, select a deployment target. Set up your deployment target according to the instructions for the target that you select:
   * **IBM Kubernetes Service**. With this option, you can either create a cluster or [deploy to an existing Kubernetes cluster](/docs/containers?topic=containers-app). If you create a cluster, allow 10 -  20 minutes for the cluster to be provisioned, and then select the region and cluster name.
   * **Red Hat OpenShift on IBM Cloud**. If you have an available [OpenShift cluster](/docs/openshift? topic=openshift-openshift_apps), you can select it from the **Cluster name** list. If you don't have an available cluster, you must create one before you continue. Your cluster creation might take some time to complete. After the cluster state shows **Normal**, the cluster network and load-balancing component take about 10 more minutes to deploy and update the cluster domain that you use for the OpenShift web console and other routes.
   * **Cloud Foundry**. This option deploys your cloud-native app without you needing to manage the underlying infrastructure. For more information, see [Deploying apps to Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps).
   * **Code Engine**. With this option, select your container registry region, container registry  namespace, and region. Then, select a project name that exists within your {{site.data.keyword.cloud_notm}} resource group. If you don't have a project, enter a project name, and the DevOps toolchain  creates one for you during the deployment process. Optionally, you can create a project in the [{{site. data.keyword.codeengineshort}} console](/codeengine/projects){: external}.
3. Create an {{site.data.keyword.cloud_notm}} API key, or select an existing one from a secrets store.
4. Complete the required fields for your deployment type, and click **Next**.
5. Provide a name for your DevOps toolchain.
6. Select the region to create your toolchain in, and then select the [resource group](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security) that provides access to your new toolchain.
7. Click **Create**.

The DevOps toolchain is created automatically, and the deployment process begins.

   You can deploy your app from the command line by running the [**ibmcloud dev deploy**](/docs/cli?topic=cli-idt-cli#deploy) command.
   {: note}

For more information about deploying your app, see [Deploying apps](/docs/apps?topic=apps-deploying-apps).

## Checking the deployment status
{: #status-scratch}
{: step}

The DevOps toolchain for your app includes a Delivery Pipeline tool where you can check the deployment status, start builds, manage deployment, and view logs and history.

On the App details page, you can view the deployment status in the **Delivery Pipeline** tile, or you can click the name of the Delivery Pipeline.

The **Build Stage** and **Deploy Stage** tiles indicate the status.

## Viewing your app's GitLab repo
{: #repo-scratch}
{: step}

After your app is built and deployed, you can view its GitLab repo and URL.

On the App details page, click **View repo** to view the GitLab repo for your app.

## Verifying that your app is running
{: #verify-scratch}
{: step}

After your app is built and deployed, you can view the app's URL to make sure that it's running.

### Apps that are deployed to a Kubernetes cluster
{: #view-kube-app-scratch}

For apps that are deployed to a Kubernetes cluster, you can view the app's URL in either the Delivery Pipeline or the command line.

1. On the App details page, click the name of the Delivery Pipeline.
2. On the Delivery Pipeline page, click **View logs and history** in the **Deploy Stage** tile.
3. In the log file, find the app's URL:

    At the end of the log file, search for the word `url` or `view`. For example, you might see a line in the log file that's similar to `urls: <my-app-devhost>.appdomain.cloud` or `VIEW THE APPLICATION AT: http://<ipaddress>:<port>`.

4. Go to the URL in your browser. If the app is running, a message that includes `Congratulations` or `{"status":"UP"}` is displayed.

If you are using the command line, run the [**ibmcloud dev view**](/docs/cli?topic=cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

### Viewing your app's Kubernetes cluster
{: #view-kube-cluster-scratch}

If you want to view the cluster where your app is deployed, click **View Kubernetes cluster** on the App details page.

### Apps that are deployed to {{site.data.keyword.codeengineshort}}
{: #view-codeengine-app-scratch}

For apps that are deployed to {{site.data.keyword.codeengineshort}}, you can view the app's status in either of the following ways:

* On the App details page, click the **App URL** link.

* On the Projects page in the [{{site.data.keyword.codeengineshort}} console](/codeengine/projects){: external}, click the project name, and then select **Applications**. Your app, its status, and its URL are listed.

### Apps that are deployed to Cloud Foundry
{: #view-cf-app-scratch}

For apps that are deployed to Cloud Foundry, you can view the app's URL from the App details page by clicking **Visit App URL**. If the app is running, a message that includes `Congratulations` is displayed.

If you are using the command line, run the [**ibmcloud dev view**](/docs/cli?topic=cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

## Next steps
{: #scratch-next-steps}

Download your app for local development where you can easily build, test, and deploy by using the {{site.data.keyword.cloud}} CLI. This is useful for debugging issues, and adding features or services, and when you are ready, you can redeploy your app to the cloud.

To work with the code locally, click the Actions icon ![More Actions icon](../../icons/actions-icon-vertical.svg), and then select **Run locally**.

For more information, see [Developing apps locally](/docs/apps?topic=apps-create-deploy-app-cli#build-run-app-cli).
