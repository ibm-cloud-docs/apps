---

copyright:
  years: 2018, 2022
lastupdated: "2022-06-03"

keywords: byoc, code repository, continuous delivery, cli, deploy, create app custom repo, custom repo, existing repo, custom code, migrate code
content-type: tutorial
services: apps
account-plan: lite
completion-time: 30m
subcollection: apps

---

{{site.data.keyword.attribute-definition-list}}

# Creating apps from your own code repository
{: #tutorial-byoc}
{: toc-content-type="tutorial"} 
{: toc-services="apps"} 
{: toc-completion-time="30m"}

If you have an application in an existing repository, use this tutorial to create an app record in {{site.data.keyword.cloud}}. You can start from the {{site.data.keyword.cloud_notm}} console or from any blank starter kit. After you provide the Git repo URL that contains your code, you connect the app record to your source repository and your DevOps toolchain.
{: shortdesc}

## Objectives
{: #objectives-byoc}

* Create an app from your existing repository.
* Enable your app.
* Add services to your app (optional).
* Deploy your app.
* Verify your app.

## Before you begin
{: #prereqs-byoc}

### For all deployment targets
{: #prereq-byoc-deploy-all}

For all deployment targets, ensure that you're aware of the following requirements:

* Depending on your [{{site.data.keyword.cloud_notm}} account type](/registration){: external}, access to certain resources might be limited or constrained. Depending on your plan limits, certain capabilities that are required by some toolchains might not be available. For more information, see [Setting up your IBM Cloud account](/docs/account?topic=account-account-getting-started).
* Install the [{{site.data.keyword.cloud_notm}} Command Line Interface (CLI)](/docs/cli?topic=cli-getting-started), which includes the {{site.data.keyword.dev_cli_short}} (`ibmcloud dev`) commands.
* Create a Docker account, run the Docker app, and sign in. Docker is installed as part of the developer tools. Docker must be running for the build commands to work.
   * See [What makes a good app?](/docs/apps?topic=apps-best-practice) for best practices for creating apps.
   * You must have a Git source code repository from any of the following providers: GitHub, GitHub Enterprise, Git lab, BitBucket, or Rational.

### For specific deployment targets
{: #prereq-byoc-deploy-specific}

For more information about requirements for specific deployment targets, see the following table.

| Deployment target | Prerequisites | 
|--------|---------------|
| {{site.data.keyword.cloud_notm}} Kubernetes Service / Helm | Create a free or paid cluster. One free Kubernetes cluster is available per account. For more information, see [Deploying apps to Kubernetes clusters](/docs/containers?topic=containers-app). Helm is a package manager for Kubernetes that allows you to package, configure, and deploy apps and services to {{site.data.keyword.cloud_notm}} Kubernetes Service. With either paid or free account plans, select this option to experiment with your starter kit in a Kubernetes environment. |
| Red Hat OpenShift on {{site.data.keyword.cloud_notm}} | OpenShift is available only through a standard cluster, which requires you to have a billable account. [Learn more](/docs/openshift?topic=openshift-getting-started) or [create an OpenShift cluster](/kubernetes/overview){: external}.|
| {{site.data.keyword.codeenginefull}} | Ensure that you have either a Pay-As-You-Go account or a Subscription account to use {{site.data.keyword.codeengineshort}} as your deployment target. If you are using a free Lite account, upgrade it before you use {{site.data.keyword.codeengineshort}}. [Learn more about accounts.](/docs/account) |

## Creating an app by using an existing repository
{: #create-byoc}
{: step}

To create an app record and connect it with your source repo, complete these steps:

From the [{{site.data.keyword.cloud_notm}} App Development console](/developer/appservice/dashboard){: external}, click **Get a Starter Kit**.
2. Click the **Create App** tile, and then select the **Create** tab.
3. Name your app, select a resource group, and optionally provide tags to classify your app. For more information, see [Working with tags](/docs/account?topic=account-tag). If a resource group doesn't exist, you must [create one](/account/resource-groups){: external}.
4. Select **Bring your own code**, and provide the URL to your Git repository. Your app and Docker image must be located in the same repo.
5. Click **Create**. The App details page is displayed.

## Viewing your Git repo
{: #repo-byoc}
{: step}

You can view your Git repo by clicking **View repo** on the App details page.

## Editing your Git URL
{: #repo-byoc-edit}
{: step}

You might want to edit the Git URL in your app if you manually renamed your Git repo and need to update the URL reference in your app so that it points to your renamed repo.

To change your Git URL, click the Actions icon ![Actions icon](../../icons/actions-icon-vertical.svg), and then select **Edit Git URL**.

## Enabling your app for {{site.data.keyword.cloud_notm}}
{: #enable-byoc-cli}
{: step}

Enable your existing app for {{site.data.keyword.cloud_notm}} deployment by using the CLI. Use the [`ibmcloud dev enable`](/docs/cli?topic=cli-idt-cli#enable) command to generate a DevOps toolchain template that you check into your repository as the instruction set for what the DevOps toolchain is to create.

To enable your app for deployment, complete these steps:

1. On the App details page, click **View repo** to work with your code locally.
2. Follow the instructions for [using the CLI to enable your app for deployment](/docs/apps?topic=apps-create-deploy-app-cli#byoc-cli).
3. After your app is enabled, continue using the {{site.data.keyword.cloud_notm}} console for the remaining steps.

## Adding services (optional)
{: #services-byoc}
{: step}

You can add services that enhance your app with the cognitive power of Watson, add mobile services, or security services.

If you want to create a new service instance or connect any existing services to your app, complete the following steps:

1. On the App details page, click **Create service** or **Connect existing services**, depending on whether you already have services that you want to connect to this app.
2. Select the kind of service you want, and follow the prompts to either add an existing service to your app or create a service instance.

After you add all the services that you want, the services are displayed in the App details page.

After you connect a service to your app, you can navigate to the service documentation and API references. Simply click the links within the **Services** card to view the related docs.

For more information, see [Adding a service to your app](/docs/apps?topic=apps-add-service).

## Deploying your app
{: #toolchain-byoc}
{: step}

Establishing a link between your app, toolchain, and repo is a step toward organizing your product assets. It also helps aggregate a view of your source with your DevOps workflow, your running app instances, and dependent services across all of your deployment targets. For more information, see [Creating toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

You can configure continuous delivery for your app by using either the {{site.data.keyword.cloud_notm}} console or the CLI.

### Creating a toolchain for your app
{: #toolchain-byoc-create}

If you don't have a DevOps toolchain for this app, complete these steps:

1. On the App details page, click **Create DevOps toolchain.**
2. On the Create a Toolchain page, select a toolchain template, or select the **Build your own toolchain** tile.
3. Provide a name for your toolchain.
4. Select the region to create your toolchain in, and then select the [resource group](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security) that provides access to your new toolchain.
5. Click **Create**.
6. On the toolchain configuration page, add the tools that you want. For more information, see [Configuring tool integrations](/docs/ContinuousDelivery?topic=ContinuousDelivery-integrations).
7. Continue to the next set of instructions to connect your new toolchain with your app.

### Connecting a toolchain to your app
{: #toolchain-byoc-connect}

If you have a DevOps toolchain that you want to connect to your app, complete these steps:

1. On the App details page, click **Deploy your app**.
2. On the Deploy my app page, select the toolchain that you want to connect to your app, and click **Enable deployment**.
3. On the Configure the Integration page, complete the required fields, and click **Create Integration**.
4. On the toolchain page, configure your toolchain as you prefer, and select the **Delivery Pipeline** tile.
5. Run the build stage to begin a new build and deploy your app.
6. Use the breadcrumbs in your browser to return to the App details page.

For more information about deploying your app, see [Deploying apps](/docs/apps?topic=apps-deploying-apps).

## Checking the deployment status
{: #status-byoc}
{: step}

The DevOps toolchain for your app includes a Delivery Pipeline tool where you can check the deployment status, start builds, manage deployment, and view logs and history.

On the App details page, you can view the deployment status in the **Delivery Pipeline** tile, or you can click the name of the Delivery Pipeline.

The **Build Stage** and **Deploy Stage** tiles indicate the status.

## Verifying that your app is running
{: #verify-byoc}
{: step}

After your app is built and deployed, you can view the app's URL to make sure that it's running.

### Apps that are deployed to a Kubernetes cluster
{: #view-kube-app-byoc}

For apps that are deployed to a Kubernetes cluster, you can view the app's URL in either the Delivery Pipeline or the command line.

1. On the App details page, click the name of the Delivery Pipeline.
2. On the Delivery Pipeline page, click **View logs and history** in the **Deploy Stage** tile.
3. In the log file, find the app's URL:

    At the end of the log file, search for the word `url` or `view`. For example, you might see a line in the log file that's similar to `urls: <my-app-devhost>.appdomain.cloud` or `VIEW THE APPLICATION AT: http://<ipaddress>:<port>`.

4. Go to the URL in your browser. If the app is running, a message that includes `Congratulations` or `{"status":"UP"}` is displayed.

If you are using the command line, run the [**ibmcloud dev view**](/docs/cli?topic=cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

### Viewing your app's Kubernetes cluster
{: #view-kube-cluster-byoc}

If you want to view the cluster where your app is deployed, click **View Kubernetes cluster** on the App details page.

### Apps that are deployed to {{site.data.keyword.codeengineshort}}
{: #view-codeengine-app-byoc}

For apps that are deployed to {{site.data.keyword.codeengineshort}}, you can view the app's status in either of the following ways:

* On the App details page, click the **App URL** link.

* On the Projects page in the [{{site.data.keyword.codeengineshort}} console](/codeengine/projects){: external}, click the project name, and then select **Applications**. Your app, its status, and its URL are listed.
