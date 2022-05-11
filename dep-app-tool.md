---

copyright:
  years: 2018, 2022
lastupdated: "2022-05-11"

keywords: apps, deploy, deploying apps, toolchain, cli, cloud, devops, deployment, git, push, commit, console

subcollection: apps

---

{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:external: target="_blank" .external}

# Deploying apps
{: #deploying-apps}

{{site.data.keyword.cloud}} provides a web console where you can configure continuous delivery and deploy your application by using a DevOps toolchain. With a DevOps toolchain, you can automate deployments to many environments and quickly add monitoring, logging, insights, and alert services to help manage your app as it grows.
{: shortdesc}

You can configure continuous delivery and deploy your app by using either the {{site.data.keyword.cloud}} console or the {{site.data.keyword.dev_cli_short}} [(**ibmcloud dev**)](/docs/cli?topic=cli-idt-cli) commands in the {{site.data.keyword.cloud_notm}} Command Line Interface (CLI). For information about deploying your app by using the CLI, see [Creating and deploying apps by using the CLI](/docs/apps?topic=apps-create-deploy-app-cli).
{: tip}

When you select a deployment target while you're creating an app, a DevOps toolchain is automatically created for your app. The toolchain includes a Delivery Pipeline that indicates your app’s deployment status. The new app is pushed to a GitLab repo that is part of the toolchain.

With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the `master` branch in your repo. For more information, see [Building and deploying](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

Enabling a DevOps toolchain creates a team-based development environment for your app. When you create a toolchain, the app service creates a Git repository, where you can view source code, clone your app, and create and manage issues. You also have access to a dedicated GitLab environment and a continuous delivery pipeline. They're customized to the deployment target that you select:
* [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started) is an open source platform for managing containerized workloads and services across multiple hosts, and offers management tools for deploying, automating, monitoring, and scaling containerized apps with minimal to no manual intervention. [Learn more](https://www.ibm.com/cloud/learn/kubernetes).
* [Red Hat OpenShift on {{site.data.keyword.cloud_notm}}](/docs/openshift?topic=openshift-getting-started) is a Kubernetes container platform that provides a trusted environment to run enterprise workloads. It extends the Kubernetes platform with built-in software to enhance app lifecycle development, operations, and security. With OpenShift, you can consistently deploy your workloads across hybrid cloud providers and environments. [View a comparison between Kubernetes and OpenShift clusters](/docs/openshift?topic=openshift-cs_ov#openshift_kubernetes).
* [{{site.data.keyword.cloud_notm}} Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-getting-started) is the premier industry standard Platform-as-a-Service (PaaS) that ensures fast, easy, and reliable deployment of cloud-native apps. Cloud Foundry ensures that the build and deploy aspects of coding remain carefully coordinated with any attached services — resulting in quick, consistent, and reliable iterating of applications. Cloud Foundry has a Lite plan that allows quick deployments for testing purposes.
* [{{site.data.keyword.codeenginefull}}](/docs/codeengine?topic=codeengine-getting-started) is a fully managed, serverless platform that runs your containerized workloads, including web apps, micro-services, event-driven functions, or batch jobs. {{site.data.keyword.codeengineshort}} even builds container images for you from your source code. Because these workloads are all hosted within the same Kubernetes infrastructure, all of them can seamlessly work together. The {{site.data.keyword.codeengineshort}} experience is designed so that you can focus on writing code and not on the infrastructure that is needed to host it.

## Before you begin
{: #prereq-deploy-apps}

### For all deployment targets
{: #prereq-deploy-all}

For all deployment targets, ensure that you're aware of the following requirements:

* Depending on your [{{site.data.keyword.cloud_notm}} account type](/registration){: external}, access to certain resources might be limited or constrained. Depending on your plan limits, certain capabilities that are required by some toolchains might not be available.
* Install the [{{site.data.keyword.cloud_notm}} Command Line Interface (CLI)](/docs/cli?topic=cli-getting-started), which includes the {{site.data.keyword.dev_cli_short}} [(**ibmcloud dev**)](/docs/cli?topic=cli-idt-cli) commands.
* Create a Docker account, run the Docker app, and sign in. Docker is installed as part of the developer tools. Docker must be running for the build commands to work.

### For specific deployment targets
{: #prereq-deploy-specific}

For information about requirements for specific deployment targets, see the following table.

| Deployment target | Prerequisites | 
|--------|---------------|
| {{site.data.keyword.cloud_notm}} Foundry | Ensure that you have access to a [Cloud Foundry org and space](/account/cloud-foundry){: external}. [Learn more](/docs/account?topic=account-orgsspacesusers) or [create a Cloud Foundry org](/account/cloud-foundry){: external}. |
| {{site.data.keyword.cloud_notm}} Kubernetes Service / Helm | Create a free or paid cluster. One free Kubernetes cluster is available per account. For more information, see [Deploying apps to Kubernetes clusters](/docs/containers?topic=containers-app). Helm is a package manager for Kubernetes that allows you to package, configure, and deploy apps and services to {{site.data.keyword.cloud_notm}} Kubernetes Service. With either paid or free account plans, select this option to experiment with your starter kit in a Kubernetes environment. |
| Red Hat OpenShift on {{site.data.keyword.cloud_notm}} | OpenShift is available only through a standard cluster, which requires you to have a billable account. [Learn more](/docs/openshift?topic=openshift-getting-started) or [create an OpenShift cluster](/kubernetes/overview){: external}.|
| {{site.data.keyword.codeenginefull}} | Ensure that you have either a Pay-As-You-Go account or a Subscription account to use {{site.data.keyword.codeengineshort}} as your deployment target. If you are using a free Lite account, upgrade it before you use {{site.data.keyword.codeengineshort}}. [Learn more about accounts.](/docs/account) |

## Before you deploy

Get started by [creating your app](/docs/apps?topic=apps-getting-started) by using a [starter kit](/developer/appservice/starter-kits){: external} from the {{site.data.keyword.cloud_notm}} console.

## Deploying your app automatically
{: deploy-console-auto}

To deploy your app, you must select your deployment target and configure continuous delivery. This process automatically creates a toolchain and starts the app deployment.

To configure the settings for your deployment target, complete the following steps:

1. In the **Deployment Automation** tile, click **Deploy your app**.
1. On the Deployment Automation page, select a deployment target. Set up your deployment target according to the instructions for the target that you select:
   * **IBM Kubernetes Service**. With this option, you can either create a cluster or [deploy to an existing Kubernetes cluster](/docs/containers?topic=containers-app). If you create a cluster, allow 10 -  20 minutes for the cluster to be provisioned, and then select the region and cluster name.
   * **Red Hat OpenShift on {{site.data.keyword.cloud_notm}}**. If you have an available [OpenShift cluster](/docs/openshift? topic=openshift-openshift_apps), you can select it from the **Cluster name** list. If you don't have an available cluster, you must create one before you continue. Your cluster creation might take some time to complete. After the cluster state shows **Normal**, the cluster network and load-balancing component take about 10 more minutes to deploy and update the cluster domain that you use for the OpenShift web console and other routes.
   * **Cloud Foundry**. This option deploys your cloud-native app without you needing to manage the underlying infrastructure. For more information, see [Deploying apps to Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps).
   * **Code Engine**. With this option, select your container registry region, container registry  namespace, and region. Then, select a project name that exists within your {{site.data.keyword.cloud_notm}} resource group. If you don't have a project, enter a project name, and the DevOps toolchain creates one for you during the deployment process. Optionally, you can create a project in the [{{site. data.keyword.codeengineshort}} console](/codeengine/projects){: external}.
1. Create an {{site.data.keyword.cloud_notm}} API key, or select an existing one from a secrets store.
1. Complete the required fields for your deployment type, and click **Next**.
1. On the Configure the DevOps toolchain page, provide a name for the DevOps toolchain.
1. Select the region to create your toolchain in, and then click **Create**.

After you click **Create**, the Continuous Delivery service is enabled, the DevOps toolchain is created automatically, and the deployment process begins. Note that the deployment status continues to update in the **Delivery Pipelines** tile.

The deployment process might take a while to complete. After the deployment is complete, the ci-pipeline status is **Success**, and the **App URL** field is populated.

   Alternatively, you can deploy your app from the command line by running the [**ibmcloud dev deploy**](/docs/cli?topic=cli-idt-cli#deploy) command.
   {: tip}

## Deploying your app manually
{: deploy-console-manual}

Continuous delivery is automatically enabled for some apps. You can enable continuous delivery to automate builds, tests, and deployments through the Delivery Pipeline and GitHub. With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the master branch in your repo.

To manually deploy your app from your DevOps toolchain, complete these steps:

1. In the **Delivery Pipelines** tile, click the name of the delivery pipeline, such as **ci-pipeline**. A new browser tab opens the pipeline dashboard.
1. Click **Run pipeline**.
1. On the Run pipeline page, click **Run**.

If you make any changes to your app or the toolchain, such as adding or removing a service, be sure to deploy the app again.
{: important}

## Related information
{: deploy-related-info}

For more information, see:
* [Building and deploying](/docs/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)
* [Creating toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)
* [Build from a pull request in the Continuous Delivery Pipeline](https://www.ibm.com/cloud/blog/build-from-a-pull-request-in-the-continuous-delivery-pipeline){: external}
* [Get Help from the IBM Cloud Continuous Delivery Development Team on Slack](https://www.ibm.com/cloud/blog/reach-out-to-the-ibm-cloud-development-teams-on-slack){: external}

## Verifying that your app is running
{: #verify-runningapp}

After your app is built and deployed, you can view the app's URL to make sure that it's running. You can view the app's status in the following ways:

* In the **Details** tile on the App details page, click the URL that is displayed in the **App URL** field.

### Apps that are deployed to a Kubernetes cluster
{: #view-kube-runningapp}

For apps that are deployed to a Kubernetes cluster, you can view the app's URL in either the Delivery Pipeline or the command line.

1. On the App details page, click the name of the Delivery Pipeline.
2. On the Delivery Pipeline page, click **View logs and history** in the **Deploy Stage** tile.
3. In the log file, find the app's URL:

    At the end of the log file, search for the word `url` or `view`. For example, you might see a line in the log file that's similar to `urls: <my-app-devhost>.appdomain.cloud` or `VIEW THE APPLICATION AT: http://<ipaddress>:<port>`.

4. Go to the URL in your browser. If the app is running, a message that includes `Congratulations` or `{"status":"UP"}` is displayed.

If you are using the command line, run the [**ibmcloud dev view**](/docs/cli?topic=cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

### Viewing your app's Kubernetes cluster
{: #view-kube-cluster-runningapp}

If you want to view the cluster where your app is deployed, click **View Kubernetes cluster** on the App details page.

### Apps that are deployed to {{site.data.keyword.codeengineshort}}
{: #view-codeengine-runningapp}

For apps that are deployed to {{site.data.keyword.codeengineshort}}, you can view the app's status in either of the following ways:

* On the App details page, click the **App URL** link.

* On the Projects page in the [{{site.data.keyword.codeengineshort}} console](/codeengine/projects){: external}, click the project name, and then select **Applications**. Your app, its status, and its URL are listed.

### Apps that are deployed to Cloud Foundry
{: #view-cf-runningapp}

You can view the app's URL from the App details page by clicking **Visit App URL**. If the app is running, a message that includes `Congratulations` is displayed.

If you are using the command line, run the [**ibmcloud dev view**](/docs/cli?topic=cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

## Next steps
{: #next-steps-deployapps}

* If you encounter errors with deployment to a Kubernetes cluster, check the troubleshooting topic for known issues like [exceeding storage quota](/docs/apps?topic=apps-managingapps#exceed_quota), or learn how to [access Kubernetes logs](/docs/apps?topic=apps-managingapps#access_kube_logs) to look for errors.

* Access the service configuration in your code:
	- You can use the _@Value_ annotation, or use the Spring framework environment class _getProperty()_ method. For more information, see [Accessing credentials](/docs/java?topic=java-spring-configuration).

* Add new service credentials to your Kubernetes environment:
	- When you add another service to your app after the DevOps toolchain is created, those service credentials aren't automatically updated to your deployed app and GitLab repository. You must [manually add the credentials to the deployment environment](/docs/apps?topic=apps-credentials_overview).
