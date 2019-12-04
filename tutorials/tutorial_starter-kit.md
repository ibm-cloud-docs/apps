---

copyright:
  years: 2018, 2019
lastupdated: "2019-12-04"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# Creating an app with a starter kit
{: #tutorial-starterkit}

You can use a starter kit to quickly get your application started and prepare it for future development. Select a starter kit and programming language, create an app, and then set up a DevOps toolchain to automatically deploy your app.
{: shortdesc}

You can create an app from a selection of starter kits, including a basic one if you would like to customize the build options yourself. Either way, a DevOps toolchain is automatically created for deploying your app. You can also download the code for immediate inspection.

{{site.data.keyword.cloud_notm}} has developer portals in different areas of interest (like Watson) or a digital channel (like Mobile or Web Apps). You can access these portals from the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg).

Each developer portal provides starter kits that are relevant to the portal's focus area. The portals offers consistent, intuitive workflows for creating a working production-ready app in minutes.

Starter kits are available in many categories, including:
* [Watson](https://{DomainName}/developer/watson/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")
* [Apple](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")
* [Mobile](https://{DomainName}/developer/mobile/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")
* [Web App](https://{DomainName}/developer/appservice/dashboard){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon")

For more information, see [What are starter kits?](/docs/apps?topic=creating-apps-starter-kits).

## Before you begin
{: #prereqs-starterkit}

* Install the [{{site.data.keyword.cloud_notm}} developer tools CLI](/docs/cli?topic=cloud-cli-getting-started).
* Docker is installed as part of the developer tools. Docker must be running for the build commands to work. You must create a Docker account, run the Docker app, and sign in.
* If you plan to deploy your app to {{site.data.keyword.cfee_full}}, you must [prepare your {{site.data.keyword.cloud_notm}} account](/docs/cloud-foundry?topic=cloud-foundry-permissions).
* If you plan to deploy your app to a Kubernetes or OpenShift cluster, you must create a cluster. For more information, see [Deploying apps to Kubernetes clusters](/docs/containers?topic=containers-app) or [Deploying apps in OpenShift clusters](/docs/openshift?topic=openshift-openshift_apps).
* If you plan to deploy your app by using Knative:
  * Create a paid Kubernetes cluster with at least three worker nodes with 16GM RAM each.
  * Ensure that the Knative and Istio addons are installed into your Kubernetes cluster. For more information, see [Setting up Knative in your cluster](/docs/containers?topic=containers-serverless-apps-knative#knative-setup).

## Creating an app
{: #create-starterkit}

Starter kits are available in many languages and frameworks in the {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}. You can use the category filters, such as language and type, to narrow the selection.

1. Go to the [App Service Starter Kits](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon") page in the {{site.data.keyword.dev_console}} console, and select a starter kit.
2. In the App details page for the starter kit, name your app, and select a resource group.
3. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/resources?topic=resources-tag).
4. Optional. To inspect the source code before you add services or deploy your app, click **View source code**. The app code includes a `README.md` file that contains technical details about the app. Check the `README.md` file to find out whether you need to take more actions to get your app up and running.
5. Click **Create**.

Great start! You just created an app!

## Adding services (optional)
{: #resources-starterkit}

If a starter kit requires specific services, the auto-provisioned service instances are automatically created and connected to your app. You can add services that enhance your app with the cognitive power of Watson, add mobile services, or security services.

If you want to create a new service instance or connect any existing services to your app, complete the following steps:

1. On the App details page, click **Create service** or **Connect existing services**, depending on whether you already have services that you want to connect to this app.
2. Select the kind of service you want, and follow the prompts to either add an existing service to your app or create a service instance.

After you add all the services that you want, the services are displayed in the App details page.

## Deploying your app
{: #deploy-starterkit}

To deploy your app, you must select your deployment target and configure continuous delivery. This process automatically creates a toolchain and starts the app deployment.

To deploy your app, complete the following steps:

1. On the App details page, click **Configure continuous delivery**.
2. Select a deployment target and complete the information according to the instructions for the target that you select:
  * **Deploy to IBM Kubernetes Service**. With this option, you can create a cluster or deploy to an existing cluster. For more information, see [Deploying apps to Kubernetes clusters](/docs/containers?topic=containers-app) or [Deploying apps in OpenShift clusters](/docs/openshift?topic=openshift-openshift_apps). Select a deployment type of **Helm**, **Knative**, or **OpenShift**. The **Knative** type is available only if Knative is installed. For more information, see [Deploying serverless apps with Knative](/docs/containers?topic=containers-serverless-apps-knative).
  * **Deploy to Cloud Foundry**. This option deploys your cloud-native app without you needing to manage the underlying infrastructure. If your account has access to {{site.data.keyword.cfee_full_notm}}, you can select a deployer type of either **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** or **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**, which you can use to create and manage isolated environments for hosting Cloud Foundry apps exclusively for your enterprise.
3. Click **Next**.
4. On the Configure toolchain page, provide the required information, and click **Create**.

The DevOps toolchain is created, and the app deployment starts automatically. The App details page indicates that continuous delivery is configured.

  You can deploy your app from the command line by running the [**ibmcloud dev deploy**](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) command. For more information, see [Deploying apps with the CLI](/docs/apps?topic=creating-apps-deploying-apps#deploy-cli).
  {: note}

For more information about deploying your app, see [Deploying apps](/docs/apps?topic=creating-apps-deploying-apps).

## Checking the deployment status
{: #status-starterkit}

The DevOps toolchain for your app includes a Delivery Pipeline tool where you can check the deployment status, start builds, manage deployment, and view logs and history.

To check the deployment status of your app, complete the following steps:

1. On the App details page, click **View toolchain**.
2. From your DevOps toolchain, click **Delivery Pipeline**.

The Build Stage and Deploy Stage tiles indicate the status.

## Viewing your app's GitLab repo
{: #repo-starterkit}

After your app is built and deployed, you can view its GitLab repo and URL.

On the App details page, click **View Repo** to view the GitLab repo for your app.

## Verifying that your app is running
{: #verify-starterkit}

After your app is built and deployed, you can view the app's URL to make sure that it's running.

### Apps that are deployed to a Kubernetes cluster
{: #view-kube-app-starterkit}

For apps that are deployed to a Kubernetes cluster, you can view the app's URL in either the Delivery Pipeline or the command line.

1. On the App details page, click **View toolchain**.
1. From your DevOps toolchain, click **Delivery Pipeline**, and then select **Deploy Stage**.
2. Click **View logs and history**.
3. In the log file, find the app's URL:

    At the end of the log file, search for the word `urls` or `view`. For example, you might see a line in the log file that's similar to `urls: my-app-devhost.mybluemix.net` or `View the application health at: http://<ipaddress>:<port>/health`.

4. Go to the URL in your browser. If the app is running, a message that includes `Congratulations` or `{"status":"UP"}` is displayed.

If you are using the command line, run the [**ibmcloud dev view**](/docs/cli/idt?topic=cloud-cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

### Viewing your app's Kubernetes cluster
{: #view-kube-cluster-starterkit}

If you want to view the cluster where your app is deployed, click **View Kubernetes cluster** on the App details page.

### Apps that are deployed to Cloud Foundry
{: #view-cf-app-starterkit}

For apps that are deployed to Cloud Foundry, you can view the app's URL from the App details page by clicking **Visit App URL**. If the app is running, a message that includes `Congratulations` is displayed.

If you are using the command line, run the [**ibmcloud dev view**](/docs/cli/idt?topic=cloud-cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

## Next steps
{: #starter-next-steps}

* Download your app for local development where you can easily build, test, and deploy by using the {{site.data.keyword.cloud}} CLI. This is useful for debugging issues, and adding features or services, and when you are ready, you can re-deploy your app to the cloud. For more information, see [Developing apps locally](/docs/apps?topic=creating-apps-local-app-development).

