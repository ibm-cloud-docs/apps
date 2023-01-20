---

copyright:
  years: 2022, 2023
lastupdated: "2023-01-20"

keywords: apps, starter kit, create app, basic app, simple app, blank app, IBM Cloud

subcollection: apps

content-type: tutorial
services: ContinuousDelivery
account-plan: paid
completion-time: 30m

---

{{site.data.keyword.attribute-definition-list}}

# Use a starter kit to create and deploy an app with {{site.data.keyword.codeengineshort}}
{: #tutorial-code-engine}
{: toc-content-type="tutorial"}
{: toc-services="ContinuousDelivery"}
{: toc-account-plan="paid"}
{: toc-completion-time="30m"}

The {{site.data.keyword.cloud}} starter kits are deprecated. As of 18 February 2023, new applications cannot be created, and the starter kits will be removed from the catalog. For current users, existing apps will continue to operate and will be supported until the End of Support date on 31 March 2023. On this date, the Applications Details page will no longer be accessible, but you will still be able to access your application code and toolchains through your [{{site.data.keyword.cloud_notm}} Resource List](https://cloud.ibm.com/resources). For more information, see the [deprecation announcement](https://www.ibm.com/cloud/blog/announcements/deprecation-of-ibm-cloud-starter-kits){: external}.
{: deprecated}

You can use an {{site.data.keyword.cloud}} starter kit with the {{site.data.keyword.codeenginefull}} deployment target to quickly get your application started and prepare it for future development. The starter kit automatically creates a DevOps toolchain for deploying your app. You can also view the starter kit's Git repo for immediate inspection.
{: shortdesc}

{{site.data.keyword.codeenginefull_notm}} is a fully managed, serverless platform that runs your containerized workloads, including web apps, micro-services, event-driven functions, or batch jobs in a fully managed Kubernetes-based infrastructure. The {{site.data.keyword.codeengineshort}} experience is designed so that you can focus on writing code and not on the infrastructure that is needed to host it. For more information, see [{{site.data.keyword.codeengineshort}}](/codeengine/overview).

## Before you begin
{: #codeengine-prereqs-starterkit}

Ensure that you're aware of the following requirements:

* You must have either a [Pay-As-You-Go or Subscription {{site.data.keyword.cloud_notm}} account](https://{DomainName}/registration){: external} to use {{site.data.keyword.codeengineshort}} as your deployment target. If you are using a free Lite account, you must upgrade it. For more information about {{site.data.keyword.cloud_notm}} accounts, see [Setting up your {{site.data.keyword.cloud_notm}} account](/docs/account?topic=account-account-getting-started) and [Upgrading your account](/docs/account?topic=account-upgrading-account).
* [Install the {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started) if you want to interact with elements of the toolchain or infrastructure after they are created. The {{site.data.keyword.cloud_notm}} CLI includes the [**ibmcloud dev**](/docs/cli?topic=cli-idt-cli) commands.
* Create a Docker account, run the Docker app, and sign in. Docker is installed as part of the developer tools. Docker must be running for the build commands to work.
* This tutorial might incur costs. Use the [Cost Estimator](/estimator/review){: external} to generate a cost estimate based on your projected usage.

## Create the app
{: #codeengine-create}
{: step}

Starter kits are available in many programming languages and frameworks in the {{site.data.keyword.cloud_notm}} console.

To create an app that uses {{site.data.keyword.codeengineshort}} as the deployment target, complete these steps:

1. Go to the [{{site.data.keyword.cloud_notm}} App Development console](/developer/appservice/starter-kits){: external}, and select **Create App**.
2. Click the **Create** tab.
3. On the Create App page, enter a name your app, and select a resource group. If a resource group doesn't exist, you must [create one](/account/resource-groups){: external}.
4. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/account?topic=account-tag).
5. Select **Create a new app** as a starting point.
6. Select **Backend** as the app type.
   If you select **Mobile** as the app type, see [Creating a custom mobile app](/docs/apps?topic=apps-tutorial-mobile#create-mobile-basic) for instructions.
   {: tip}

7. Select the language and framework that you want to use for your app.
8. Click **Create**. The App details page is displayed, and it includes tiles for **Details**, **Services**, and **Deployment Automation**.

## Download the app code (optional)
{: #codeengine-download-code}
{: step}

You can view your app code before you deploy it by clicking **Download code** from the **Details** tile. Your code is downloaded as a `.zip` file that contains the complete app code structure. You can extract the file and run the code locally by using the [**ibmcloud dev**](/docs/cli?topic=cli-idt-cli) commands, or add it to your code management repository.

The app code includes a `README.md` file that contains technical details about the app. Check the `README.md` file to find out whether you need to take more actions to get your app up and running.
{: tip}

## Add services (optional)
{: #codeengine-services}
{: step}

You can add services that enhance your app with the cognitive power of Watson, add mobile services, security services, and more.

If you want to create a new service instance or connect any existing services to your app, complete the following steps:

1. In the **Services** tile, click either **Connect existing services** or **Create service**, depending on whether you already have services that you want to connect to this app.
2. Select the kind of service that you want, and follow the prompts to either add an existing service to your app or create a service instance.

After you add all the services that you want, the services are displayed in the **Services** tile.

After you connect a service to your app, you can navigate to the service documentation and API references. Simply click the links within the **Services** card to view the related docs.

## Configure the deployment target
{: #codeengine-target}
{: step}

To deploy your app, you must select your deployment target and configure continuous delivery. This process automatically creates a toolchain and starts the app deployment.

To configure the settings for the {{site.data.keyword.codeengineshort}} deployment target, complete the following steps:

1. In the **Deployment Automation** tile, click **Deploy your app**.
2. On the Deployment Automation page, select the **{{site.data.keyword.codeengineshort}}** deployment target.
3. Create an {{site.data.keyword.cloud_notm}} API key, or select an existing one from a secrets store.
4. Select the container registry region.
5. Enter the name of a container registry namespace if one doesn't exist. The name must be unique. This process creates one for you.
6. Select the region where your {{site.data.keyword.codeengineshort}} project is located.
7. Select the resource group.
8. Select a project name that exists within your {{site.data.keyword.cloud_notm}} resource group. If you don't have a project, enter a project name, and the DevOps toolchain creates one for you during the deployment process. Optionally, you can create a project in the [{{site.data.keyword.codeengineshort}} console](/codeengine/projects){: external}
9. Click **Next**.

## Configure the DevOps toolchain settings
{: #codeengine-toolchain}
{: step}

The DevOps toolchain includes a Delivery Pipeline tool where you can check the deployment status, start builds, manage deployment, and view logs and history.

To configure the settings for the DevOps toolchain, complete the following steps:

1. On the Configure the DevOps toolchain page, provide a name for the DevOps toolchain. 
2. Select the region to create your toolchain in, and then click **Create**.

After you click **Create**, the Continuous Delivery service is enabled, the DevOps toolchain is created automatically, and the deployment process begins. Note that the deployment status continues to update in the **Delivery Pipelines** tile.

The deployment process might take a while to complete. After the deployment is complete, the ci-pipeline status is **Success**, and the **App URL** field is populated.

   Alternatively, you can deploy your app from the command line by running the [**ibmcloud dev deploy**](/docs/cli?topic=cli-idt-cli#deploy) command.
   {: tip}

## Check the deployment status
{: #codeengine-status}
{: step}

You can view the deployment status in the **Delivery Pipelines** tile. If you want to view more information, click the name of the delivery pipeline, such as **ci-pipeline**.

A new browser tab opens the pipeline dashboard. From here, you can check the deployment status, run the pipeline again, manage deployment settings, and view logs and history.

## View your app's Git repo
{: #codeengine-repo}
{: step}

After your app is built and deployed, you can view its Git repo and URL from the App details page.

In the **Details** tile, click the URL that is displayed in the **Source** field.

## View the deployment target
{: #codeengine-target-view}
{: step}

After your app is built and deployed, you can view its deployment target from the App details page.

In the **Details** tile, click the URL that is displayed in the **Deployment target** field.

## Verify that your app is running
{: #codeengine-verify}
{: step}

After your app is built and deployed, you can view the app's URL to make sure that it's running. You can view the app's status in either of the following ways:

* In the **Details** tile on the App details page, click the URL that is displayed in the **App URL** field.

* On the Projects page in the [{{site.data.keyword.codeengineshort}} console](/codeengine/projects){: external}, click the project name, and then select **Applications**. Your app, its status, and its URL are listed.

## Next steps
{: #codeengine-more}

To view and modify your toolchain, click the toolchain's name in the **Deployment Automation** tile. The Toolchain Overview page is displayed, where you can view and manage the toolchain.

If you make any changes to your app or the toolchain, such as adding or removing a service, be sure to deploy the app again.
{: important}

To do so, open the ci-pipeline dashboard, and click **Run pipeline**. On the Run pipeline page, select `manual-run` from the **Triggers** list, and then click **Run**.

To view a related tutorial, see [Develop and deploy an app by using {{site.data.keyword.codeengineshort}}](/docs/ContinuousDelivery?topic=ContinuousDelivery-tutorial-cd-code-engine).
