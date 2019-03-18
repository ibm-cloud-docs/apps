---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, starter kit, Kubernetes, cluster

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Deploying a starter kit app to a Kubernetes cluster
{: #tutorial-starterkit-kube}

Learn how to create an application in {{site.data.keyword.cloud}} by using a blank starter kit and a Kubernetes toolchain, and continuously deliver the app to a secure container in a Kubernetes cluster. Your continuous integration DevOps pipeline can be configured so that your code changes are automatically built and propagated to the app that’s in the Kube cluster. If you already have a pipeline, you can connect it to your app.
{: shortdesc}

{{site.data.keyword.cloud_notm}} offers starter kits that help you build the foundation of an app that runs on Kubernetes. When you use a starter kit, it's easy to follow a cloud native programming model that uses {{site.data.keyword.cloud_notm}} best practices for app development. Starter kits generate apps that follow the cloud native programming model, and they include test cases, health check, and metrics in each programming language. You can also provision cloud services that are then initialized in your generated application.

This tutorial uses the Kubernetes deployment target. In this tutorial, we're creating an application from a basic starter kit by using Java + Spring, adding a Cloudant service instance to it, and deploying it to {{site.data.keyword.cloud_notm}} by using IBM Kubernetes Service.

First, see the following starter kit flow diagram and its corresponding overview steps.

![Starter kit flow diagram](../images/starterkit-flow.png) 

## Before you begin
{: #prereqs-starterkit-kube}

* Create a **Java + Spring** app by using a [starter kit](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit).
* Install the [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli).
* Set up [Docker](https://www.docker.com/get-started){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon").

## Adding services to your app
{: #resources-starterkit-kube}

Add an {{site.data.keyword.cloud_notm}} service to your application. The following steps provision a Cloudant instance, create a resource key (credentials), and bind it to your app.

1. On the **App details** page, click **Add service**.
2. Select **Data** and click **Next**..
3. Select **Cloudant** and click **Next**.
4. On the **Add Cloudant** page, select the region (US-South), resource group (default), and pricing plan (Lite - one free instance).
5. Click **Create**. The **App details** page is displayed, and the Cloudant instance is provisioned and bound to your app. Notice that the Cloudant resource key (credentials) is added to the **Credentials** field.
6. Optional. If you want to take a quick look at your app code after you add services, click **Download code**. Your code is downloaded as a `.zip` file that contains the complete app code structure. You can easily extract the file and run the code locally by using the {{site.data.keyword.dev_cli_notm}}, or add it to your code management repository.

## Deploying your app by using a DevOps toolchain
{: #deploy-starterkit-kube}

Attach a DevOps toolchain to the application, and configure it to be deployed to a Kubernetes cluster that is hosted in the {{site.data.keyword.cloud_notm}} Kubernetes service.

1. On the **App details** page, click **Configure continuous delivery**.
2. On the **Select a deployment target** page, select **Deploy to IBM Kubernetes Service**.
3. Select a region and a cluster. If you don't have a Kubernetes cluster, click **Create cluster**.
  * On the **Create new cluster** page, select the location, the cluster type (free), enter a cluster name, and then click **Create cluster**.
  * If necessary, follow the on-screen instructions to gain access to your cluster.
  * Wait until the cluster indicates **READY** to create the toolchain. With the **US-South** region, you can provision one free cluster.
  * Return to the **Select a deployment target** page.
4. Click **Next**. The **Configure toolchain** page is displayed.
5. On the **Configure toolchain** page, enter a toolchain name, select a region, select a resource group, and then click **Create**. The **App details** page is displayed, along with deployment information about your toolchain.

## Viewing your repository
{: #view-repo-starterkit-kube}

1. On the **App details** page, click **View repo**. The Git repo that the starter kit generated is displayed.
2. Optional. Configure SSH on your desktop by following the on-screen instructions.
3. Optional. Create a personal access token on your account by following the on-screen instructions.

## Viewing the toolchain tools, logs, and history
{: #view-logs-starterkit-kube}

1. When the deployment stage is finished, the **App details** page is displayed, along with deployment information about your toolchain.
2. Access the toolchain by clicking **View toolchain**. The **Overview** tab of the toolchain page is displayed, which shows the tools that are included with the toolchain. This example includes the following tools that were preselected in the starter kit when the toolchain was created:
  * An issues tracker to track project updates and changes.
  * A Git repo that contains the source code of your application.
  * An Eclipse Orion instance, which is a web-based IDE to edit your application.
  * A Delivery Pipeline that consists of a customizable build and deploy stage.
	 * The BUILD stage containerizes the app. More specifically, the build stage:
	   * Clones your GitLab repository.
	   * Builds the app.
	   * Builds the Docker image.
	   * Publishes the image to your private container registry.
	 * The DEPLOY stage retrieves the container image from your container registry and then deploys it to your Kubernetes cluster.
3. Click **Delivery Pipeline**. The pipeline stages are displayed.
4. In the **Deploy Stage** tile, click **View logs and history**.

## Verifying that your app is running
{: #verify-starterkit-kube}

After you deploy your app, the Delivery Pipeline or command line points you to the URL for your app.

1. From your DevOps toolchain, click **Delivery Pipeline**, and then select **Deploy Stage**.
2. Click **View logs and history**.
3. In the log file, find the application URL:

    At the end of the log file, search for `View the application health at: http://<ipaddress>:<port>/health`.

4. Go to the URL in your browser. If the app is running, a message that includes `Congratulations` or `{"status":"UP"}` is displayed.

FIf you are using the command line, run the [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

## Next steps
{: #next-steps-startkit-kube notoc}

* If you encounter errors with deployment, check the troubleshooting topic for known issues like [exceeding storage quota](/docs/apps?topic=creating-apps-managingapps#exceed_quota), or learn how to [access Kubernetes logs](/docs/apps?topic=creating-apps-managingapps#access_kube_logs) to look for errors.

* Access the service configuration in your code:
	- You can use the _@Value_ annotation, or use the Spring framework environment class _getProperty()_ method. For more information, see [Accessing credentials](/docs/java-spring?topic=java-spring-configuration#accessing-credentials).

* Add new credentials to your Kubernetes environment:
	- When you add another service to your application after the DevOps toolchain is created, those service credentials aren't automatically updated to your deployed application and GitLab repository. You must [manually add the credentials](/docs/apps?topic=creating-apps-add-credentials-kube) to the deployment environment.
