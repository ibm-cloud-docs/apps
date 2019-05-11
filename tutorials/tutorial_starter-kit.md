---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-10"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{: note .note}

# Creating an app with a starter kit
{: #tutorial-starterkit}

You can use a starter kit to quickly get your application started and prepare it for future development. Select a starter kit and programming language, create an app, and then set up a DevOps toolchain to automatically deploy your app. You can also download the code for immediate inspection.
{: shortdesc}

You can create an app from a selection of starter kits, including a blank one if you would like to customize build options yourself. Either way, a DevOps toolchain is automatically created for deploying your app. You can also download the code for immediate inspection.

{{site.data.keyword.cloud_notm}} has developer portals in different areas of interest (like Watson, Security, or Finance) or a digital channel (like Mobile or Web Apps). You can access these portals from the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg).

Each developer portal provides starter kits that are relevant to the portal's focus area. The portals offers consistent, intuitive workflows for creating a working production-ready app in minutes.

Starter kits are available in many categories, including:
* [Watson](https://{DomainName}/developer/watson/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")
* [Apple](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")
* [Mobile](https://{DomainName}/developer/mobile/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")
* [Web App](https://{DomainName}/developer/appservice/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")
* [Security](https://{DomainName}/developer/security/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")
* [Finance](https://{DomainName}/developer/finance/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")

See [What are starter kits?](/docs/apps?topic=creating-apps-starter-kits) for more information.

## Step 1. Install the tools
{: #prereqs-starterkit}

* Install the [developer tools](/docs/cli?topic=cloud-cli-ibmcloud-cli).
* Docker is installed as part of the developer tools. Docker must be running for the build commands to work. You must create a Docker account, run the Docker app, and sign in.
* If you plan to deploy your app to {{site.data.keyword.cfee_full}}, you must [prepare your {{site.data.keyword.cloud_notm}} account](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Step 2. Create an app
{: #create-starterkit}

Starter kits are available in many languages and frameworks in the {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}. You can use the category filters, such as language and type, to narrow the selection.

1. From the [starter kits](https://{DomainName}/developer/appservice/starter-kits/){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon") page in the {{site.data.keyword.dev_console}} console, select a starter kit, and click **Create app**. 

    To see what is included in the starter kit, select the tile and read the details. If you want to use a blank starter kit and customize it, select the **Create App** tile.
    {: tip}

2. Name your app, and select a resource group.

3. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/resources?topic=resources-tag).

4. Select your language and framework. Some starter kits might be available only in one language.

5. Click **Create**.

Great start! You just created an app!

To inspect your code before you add services or set up continuous delivery, click **Download code** on the App details page. Check the `README.md` file in the downloaded compressed file to find out whether you need to take more actions to get your app up and running.
{: tip}

## Step 3. Add services (optional)
{: #resources-starterkit}

If a starter kit requires specific services, auto-provisioned services are available so that instances for those services are automatically created when you create your app.

You can also add services that enhance your app with the cognitive power of Watson, add mobile services, or security services. For this tutorial, add a place to manage your data.

1. On the App details page, click **Create service** or **Connect existing services**, depending on whether you already have services that you want to connect to this app.
2. Select the kind of service you want, and follow the prompts to either add an existing service to your app or create a service instance.

After you add all the services that you want, they are displayed in the App details page.

## Step 4. Select a deployment target and configure continuous delivery
{: #target-starterkit}

When you select a deployment target, a DevOps toolchain is automatically created for your app. The toolchain includes a Delivery Pipeline that indicates your app’s deployment status. The new app that is generated is pushed to a GitLab repo that is part of the toolchain.

Enabling a DevOps toolchain creates a team-based development environment for your app. When you create a toolchain, the app service creates a Git repository, where you can view source code, clone your app, and create and manage issues. You also have access to a dedicated GitLab environment and a continuous delivery pipeline. They're customized to the deployment target that you select, whether it's [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about), or [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

All toolchains that are created from an {{site.data.keyword.cloud_notm}} Developer dashboard are configured for automatic deployment.
{: note}

To select your deployment target and configure continuous delivery, complete these steps:

1. On the App details page, click **Configure continuous delivery**.
2. Select a deployment target. Set up your deployment target according to the instructions for the target that you select:
  * **Deploy to [IBM Kubernetes Service](/docs/containers?topic=containers-app)**. This option creates a cluster of hosts, called worker nodes, to deploy and manage highly available application containers. You can create a cluster or deploy to an existing cluster.
  * **Deploy to Cloud Foundry**. This option deploys your cloud-native app without you needing to manage the underlying infrastructure. If your account has access to {{site.data.keyword.cfee_full_notm}}, you can select a deployer type of either **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** or **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**, which you can use to create and manage isolated environments for hosting Cloud Foundry applications exclusively for your enterprise.
  * **Deploy to a Virtual Server**. This option provisions a virtual server instance, loads an image that includes your app, creates a DevOps toolchain, and initiates the first deployment cycle for you.

After you select and configure the deployment target, the App details page indicates that continuous delivery is configured. You can view the repo that contains the source code for your app by clicking **View repo**.

## Step 5. Deploy your app
{: #deploy-starterkit}

DevOps toolchains that are created from the {{site.data.keyword.cloud_notm}} developer dashboard are configured for automatic deployment.
{: note}

After you select your deployment target, open the pipeline component of your new toolchain to start the initial build and deployment process so that you can see your new app in minutes.

1. On the App details page, click **View toolchain**.
2. Click **Delivery Pipeline** where you can start builds, manage deployment, and view logs and history.

With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the master branch in your repo. For more information, see [Building and deploying](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

You can deploy your app from the command line by running the [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) command. For more information, see [Deploying apps with the CLI](/docs/apps?topic=creating-apps-deploying-apps#deploy-cli).

## Step 6. Verify that your app is running
{: #verify-starterkit}

After you deploy your app, the Delivery Pipeline or command line points you to the URL for your app.

1. From your DevOps toolchain, click **Delivery Pipeline**, and then select **Deploy Stage**.
2. Click **View logs and history**.
3. In the log file, find the application URL:

    At the end of the log file, search for the word `urls` or `view`. For example, you might see a line in the log file that's similar to `urls: my-app-devhost.mybluemix.net` or `View the application health at: http://<ipaddress>:<port>/health`.

4. Go to the URL in your browser. If the app is running, a message that includes `Congratulations` or `{"status":"UP"}` is displayed.

If you are using the command line, run the [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.
