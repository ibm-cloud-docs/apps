---

copyright:
  years: 2018, 2019
lastupdated: "2019-08-19"

keywords: byoc, code repository, continuous delivery, cli, deploy, create app custom repo, custom repo, existing repo, custom code

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Creating apps from your own code repository
{: #tutorial-byoc}

If you have an application in an existing repository, you can use a basic starter kit to create an app record in {{site.data.keyword.cloud_notm}} and connect the app to your source repository and your DevOps toolchain.
{: shortdesc}

You can start from the {{site.data.keyword.cloud_notm}} dashboard or from any basic starter kit. After you name your app and select a resource group, select the **Bring your own code** starting point, provide the Git repo URL that contains your code, and click **Create**.

You can connect your existing DevOps toolchain or create one, and continuously deliver your app to the deployment target of your choice, such as Kubernetes or Cloud Foundry.

## Before you begin
{: #prereqs-byoc}

Be sure that you have the following prerequisites ready to go:

 * Install the [{{site.data.keyword.dev_cli_long}} command-line interface (CLI)](/docs/cli?topic=cloud-cli-getting-started).
 * See [What makes a good app?](/docs/apps?topic=creating-apps-best-practice) for best practices for creating apps.
 * You must have a Git source code repository from any of the following providers: GitHub, GitHub Enterprise, Git lab, BitBucket, or Rational.
 * If you plan to deploy your app to [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), you must [prepare your {{site.data.keyword.cloud_notm}} account](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Creating an app with an existing repository
{: #create-byoc}

To create an app and connect it with your source repo, complete these steps:

1. From the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon"), click **Create an app** in the **Apps** tile.
2. Name your app, select a resource group, and optionally provide tags to classify your app. For more information, see [Working with tags](/docs/resources?topic=resources-tag).
3. Select **Bring your own code**, and provide the URL to your Git repository. Your app and Docker image must be located in the same repo.
4. Click **Create**. The **App details** page is displayed.
5. Optional. [Add services](/docs/apps?topic=creating-apps-add-resource) to your app.
6. Optional. You can add tags to this app by clicking **Add tags**, or you can edit tags by clicking the **Edit** icon ![Edit icon](../../icons/edit-tagging.svg) that's next to the displayed tags.
7. Optional. View your repo by clicking **View repo.**

## Deploying your app
{: #toolchain-byoc}

Establishing a link between your app, toolchain, and repo is a step toward organizing your product assets. It also helps aggregate a view of your source with your DevOps workflow, your running app instances, and dependent services across all of your deployment targets. For more information, see [Creating toolchains](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

You can configure continuous delivery for your app by using either the {{site.data.keyword.cloud_notm}} console or the CLI.

### Using the console
{: #console-byoc-toolchain}

#### If you already have a DevOps toolchain that you want to connect to your app, complete these steps:

1. On the **App details** page, click **Configure continuous delivery**. The **Deploy my app** page is displayed.
2. Select the toolchain that you want to connect to your app, and click **Enable deployment**. The **App details** page is displayed, indicating that continuous delivery is configured.

#### If you don't have a DevOps toolchain for this app, complete these steps:

1. On the **App details** page, click **Create DevOps toolchain.** The **Create a toolchain** page is displayed.
2. [Create the toolchain](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).
3. Use the breadcrumbs in the browser window to return to the **App details** page, which indicates that continuous delivery is configured.

### Using the CLI
{: #cli-byoc-toolchain}

You can use the `ibmcloud dev enable` command to generate a DevOps toolchain template that you check into your repository as the instruction set for what the DevOps toolchain is to create. 

  1. On the **App details** page, click **View repo** to work with your code locally.
  2. Run the following command:
    
    ```
    ibmcloud dev enable
    ```
   {: codeblock}

For more information about deploying your app, see [Deploying apps](/docs/apps?topic=creating-apps-deploying-apps).

## Verifying that your app is running
{: #verify-byoc-app}

The Delivery Pipeline or command line points you to the URL for your app.

1. From your DevOps toolchain, click **Delivery Pipeline**, and then select **Deploy Stage**.
2. Click **View logs and history**.
3. In the log file, find the app's URL. At the end of the log file, search for the word `urls` or `view`. For example, you might see a line in the log file that's similar to `urls: my-app-devhost.mybluemix.net` or `View the application health at: http://<ipaddress>:<port>/health`.
4. Go to the URL in your browser. If the app is running, a message that includes `Congratulations` or `{"status":"UP"}` is displayed.

If you are using the command line, run the [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) command to open the page of a manually deployed app in your default browser.

### Viewing your app's Kubernetes cluster
{: #view-kube-cluster-starterkit}

If you want to view the cluster where your app is deployed, click **View Kubernetes cluster** on the App details page.
