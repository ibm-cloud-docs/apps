---

copyright:
  years: 2018, 2020
lastupdated: "2020-12-07"

keywords: apps, starter kit, create app starter kit, basic app, simple app, blank app
content-type: tutorial
services: apps
account-plan: lite
completion-time: 30m
subcollection: apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}
{:external: target="_blank" .external}
{:step: data-tutorial-type='step'}

# Creating an app with a starter kit
{: #tutorial-starterkit}
{: toc-content-type="tutorial"} 
{: toc-services="apps"} 
{: toc-completion-time="30m"}

Use this tutorial to create an app by using an {{site.data.keyword.cloud}} starter kit. You can create an app from a selection of starter kits, including a blank one if you want to customize the build options yourself. Either way, a DevOps toolchain is automatically created for deploying your app.
{: shortdesc}

{{site.data.keyword.cloud_notm}} has developer consoles that you can access from the **Menu** icon ![Menu icon](../icons/icon_hamburger.svg). Each developer console provides starter kits that are relevant to the console's focus area. The consoles offer consistent, intuitive workflows for creating a working production-ready app in minutes.

You can find starter kits in the following developer consoles:
* [App Development console](https://{DomainName}/developer/appservice/starter-kits){: external}
* [Watson](https://{DomainName}/developer/watson/starter-kits){: external}
* [Apple](https://{DomainName}/developer/appledevelopment/starter-kits){: external}

For more information, see [What are starter kits?](/docs/apps?topic=apps-starter-kits).

## Objectives
{: #objectives-starterkit}

* Use a starter kit to create an app. 
* Add services to an app (optional).
* Deploy your app.
* Verify the app.

## Before you begin
{: #prereqs-starterkit}

### For all deployment targets
{: #prereq-starterkit-deploy-all}

For all deployment targets, ensure that you're aware of the following requirements:

* Depending on your [{{site.data.keyword.cloud_notm}} account type](https://{DomainName}/registration), access to certain resources might be limited or constrained. Depending on your plan limits, certain capabilities that are required by some toolchains might not be available. For more information, see [Setting up your IBM Cloud account](/docs/account?topic=account-account-getting-started).
* Install the [{{site.data.keyword.cloud_notm}} Command Line Interface (CLI)](/docs/cli?topic=cli-getting-started), which includes the {{site.data.keyword.dev_cli_short}} (`ibmcloud dev`) commands.
* Create a Docker account, run the Docker app, and sign in. Docker is installed as part of the developer tools. Docker must be running for the build commands to work.

### For specific deployment targets
{: #prereq-starterkit-deploy-specific}

For more information about requirements for specific deployment targets, see the following table.

| Deployment target | Prerequisites | 
|--------|---------------|
| {{site.data.keyword.cloud_notm}} Foundry | Ensure that you have access to a [Cloud Foundry org and space](https://{DomainName}/account/cloud-foundry). [Learn more](/docs/account?topic=account-orgsspacesusers) or [create a Cloud Foundry org](https://{DomainName}/account/cloud-foundry). |
| {{site.data.keyword.cloud_notm}} Kubernetes Service / Helm | Create a free or paid cluster. One free Kubernetes cluster is available per account. For more information, see [Deploying apps to Kubernetes clusters](/docs/containers?topic=containers-app). Helm is a package manager for Kubernetes that allows you to package, configure, and deploy apps and services to {{site.data.keyword.cloud_notm}} Kubernetes Service. With either paid or free account plans, select this option to experiment with your starter kit in a Kubernetes or OpenShift environment. |
| {{site.data.keyword.cloud_notm}} Kubernetes Service / Knative | Knative is an extension of Kubernetes that hides many of the complex management tasks and adds serverless capabilities. The Knative deployment type is available only if Knative is installed on the cluster that you select.<br>1. Install the [IBM Cloud CLI, the IBM Cloud Kubernetes Service plug-in, and the Kubernetes CLI](/docs/containers?topic=containers-cs_cli_install).<br>2. Create a [standard Kubernetes cluster](https://{DomainName}/kubernetes/catalog/cluster) with 3 worker nodes that each have 4 cores and 16 GB memory (b3c.4x16) or more. For more information, see [Creating a standard classic cluster in the console](/docs/containers?topic=containers-clusters#clusters_ui). Ensure that you note the total monthly cost before you create the cluster.<br>3. Install the [Istio add-on](/docs/containers?topic=containers-istio).<br>4. Install the [Knative add-on](/docs/containers?topic=containers-serverless-apps-knative#knative-setup). |
| Red Hat OpenShift on {{site.data.keyword.cloud_notm}} | OpenShift is available only through a standard cluster, which requires you to have a billable account. [Learn more](/docs/openshift?topic=openshift-getting-started) or [create an OpenShift cluster](https://{DomainName}/kubernetes/overview).|

## Creating an app
{: #create-starterkit}
{: step}

Starter kits are available in many languages and frameworks in the {{site.data.keyword.cloud_notm}} console. You can use the category filters, such as language and deployment target, to narrow the selection.

1. Go to the [{{site.data.keyword.cloud_notm}} App Development console](https://{DomainName}/developer/appservice/starter-kits){: external}, and select a starter kit to view details about it. For example, select the **Node.js Express App** starter kit.
2. Select the **Create** tab.
3. On the App details page for the starter kit, enter a name for your app, and select a resource group. If a resource group doesn't exist, you must [create one](https://{DomainName}/account/resource-groups){: external}.
4. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/account?topic=account-tag).
5. Optional. To inspect the source code before you add services or deploy your app, click **View source code**. The app code includes a `README.md` file that contains technical details about the app. Check the `README.md` file to find out whether you need to take more actions to get your app up and running.
5. Click **Create**.

If you want to view the Git repo for the starter kit, click **View sample repo**.

## Adding services (optional)
{: #resources-starterkit}
{: step}

If a starter kit requires specific services, the required services are automatically created and provisioned for you. You can connect more services to your app in the {{site.data.keyword.cloud_notm}} console from the App details page, which is displayed as soon as you create the app.

If you want to create a new service instance or connect any existing services to your app, complete the following steps:

1. On the App details page, click **Create service** or **Connect existing services**, depending on whether you already have services that you want to connect to this app.
2. Select the kind of service you want, and follow the prompts to either add an existing service to your app or create a service instance.

After you add all the services that you want, the services are displayed in the App details page.

After you connect a service to your app, you can navigate to the service documentation and API references. Simply click the links within the **Services** card to view the related docs.

For more information, see [Adding a service to your app](/docs/apps?topic=apps-add-service).

## Deploying your app
{: #deploy-starterkit}
{: step}

To deploy your app, you must select your deployment target and configure continuous delivery. This process automatically creates a toolchain and starts the app deployment.

To deploy your app, complete the following steps:

1. On the App details page for your app, click **Deploy your app**.
2. On the Deploy your app page, select a deployment target. Set up your deployment target according to the instructions for the target that you select:
  * **IBM Kubernetes Service**. With this option, you can either create a cluster or [deploy to an existing Kubernetes cluster](/docs/containers?topic=containers-app). If you create a cluster, allow 10 - 20 minutes for the cluster to be provisioned. Select a deployment type of **Helm** or **Knative**, and then select the region and cluster name.
  * **Red Hat OpenShift on IBM Cloud**. If you have an available [OpenShift cluster](/docs/openshift?topic=openshift-openshift_apps), you can select it from the **Cluster name** list. If you don't have an available cluster, you must create one before you continue. Your cluster creation might take some time to complete. After the cluster state shows **Normal**, the cluster network and load-balancing component take about 10 more minutes to deploy and update the cluster domain that you use for the OpenShift web console and other routes.
  * **Cloud Foundry**. This option deploys your cloud-native app without you needing to manage the underlying infrastructure. For more information, see [Deploying apps to Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps).
3. Provide a name for your toolchain.
4. Select the region to create your toolchain in, and then select the [resource group](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security) that provides access to your new toolchain.
5. Click **Create**.

The DevOps toolchain is created automatically, and the deployment process begins.

  You can deploy your app from the command line by running the [**ibmcloud dev deploy**](/docs/cli?topic=cli-idt-cli#deploy) command.
  {: note}

For more information about deploying your app, see [Deploying apps](/docs/apps?topic=apps-deploying-apps).

## Checking the deployment status
{: #status-starterkit}
{: step}

The DevOps toolchain for your app includes a Delivery Pipeline tool where you can check the deployment status, start builds, manage deployment, and view logs and history.

On the App details page, you can view the deployment status in the **Delivery Pipeline** tile, or you can click the name of the Delivery Pipeline.

The **Build Stage** and **Deploy Stage** tiles indicate the status.

## Viewing your app's GitLab repo
{: #repo-starterkit}
{: step}

After your app is built and deployed, you can view its GitLab repo and URL.

On the App details page, click **View repo** to view the GitLab repo for your app.

## Verifying that your app is running
{: #verify-starterkit}
{: step}

After your app is built and deployed, you can view the app's URL to make sure that it's running.

### Apps that are deployed to a Kubernetes cluster
{: #view-kube-app-starterkit}

For apps that are deployed to a Kubernetes cluster, you can view the app's URL in either the Delivery Pipeline or the command line.

1. On the App details page, click the name of the Delivery Pipeline.
2. On the Delivery Pipeline page, click **View logs and history** in the **Deploy Stage** tile.
3. In the log file, find the app's URL:

    At the end of the log file, search for the word `url` or `view`. For example, you might see a line in the log file that's similar to `urls: <my-app-devhost>.appdomain.cloud` or `VIEW THE APPLICATION AT: http://<ipaddress>:<port>`.

4. Go to the URL in your browser. If the app is running, a message that includes `Congratulations` or `{"status":"UP"}` is displayed.

If you are using the command line, run the [**ibmcloud dev view**](/docs/cli?topic=cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

### Viewing your app's Kubernetes cluster
{: #view-kube-cluster-starterkit}

If you want to view the cluster where your app is deployed, click **View Kubernetes cluster** on the App details page.

### Apps that are deployed to Cloud Foundry
{: #view-cf-app-starterkit}

For apps that are deployed to Cloud Foundry, you can view the app's URL from the App details page by clicking **Visit App URL**. If the app is running, a message that includes `Congratulations` is displayed.

If you are using the command line, run the [**ibmcloud dev view**](/docs/cli?topic=cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

## Next steps
{: #starter-next-steps}

Download your app for local development where you can easily build, test, and deploy by using the {{site.data.keyword.cloud}} CLI. This is useful for debugging issues, and adding features or services, and when you are ready, you can redeploy your app to the cloud.

To work with the code locally, click the Actions icon ![More Actions icon](../icons/actions-icon-vertical.svg), and then select **Run locally**.

For more information, see [Developing apps locally](/docs/apps?topic=apps-create-deploy-app-cli#build-run-app-cli).
