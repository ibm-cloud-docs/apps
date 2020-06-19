---

copyright:
  years: 2018, 2020
lastupdated: "2020-06-05"

keywords: apps, deploy, deploying apps, toolchain, cli, cloud, devops, deployment, git, push, commit, console

subcollection: apps

---

{:new_window: target="_blank"}
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

{{site.data.keyword.cloud_notm}} provides a web console where you can configure continuous delivery and deploy your application by using a DevOps toolchain. With a DevOps toolchain, you can automate deployments to many environments and quickly add monitoring, logging, insights, and alert services to help manage your app as it grows.
{: shortdesc}

  You can configure continuous delivery and deploy your app by using either the {{site.data.keyword.cloud}} console or the {{site.data.keyword.dev_cli_short}} [(**ibmcloud dev**)](/docs/cli?topic=cli-idt-cli) commands in the {{site.data.keyword.cloud_notm}} command-line interface (CLI). For information about deploying your app by using the CLI, see [Creating and deploying apps by using the CLI](/docs/apps?topic=apps-create-deploy-app-cli).
  {: tip}

When you select a deployment target while you're creating an app, a DevOps toolchain is automatically created for your app. The toolchain includes a Delivery Pipeline that indicates your app’s deployment status. The new app is pushed to a GitLab repo that is part of the toolchain.

With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the master branch in your repo. For more information, see [Building and deploying](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

Enabling a DevOps toolchain creates a team-based development environment for your app. When you create a toolchain, the app service creates a Git repository, where you can view source code, clone your app, and create and manage issues. You also have access to a dedicated GitLab environment and a continuous delivery pipeline. They're customized to the deployment target that you select:
* [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started) is an open source platform for managing containerized workloads and services across multiple hosts, and offers management tools for deploying, automating, monitoring, and scaling containerized apps with minimal to no manual intervention. [Learn more](https://www.ibm.com/cloud/learn/kubernetes). When you deploy your app to a Kubernetes cluster, you can select either Helm or [Knative](/docs/containers?topic=containers-serverless-apps-knative) as the deployment type.
* [Red Hat OpenShift on {{site.data.keyword.cloud_notm}}](/docs/openshift?topic=openshift-getting-started) is a Kubernetes container platform that provides a trusted environment to run enterprise workloads. It extends the Kubernetes platform with built-in software to enhance app lifecycle development, operations, and security. With OpenShift, you can consistently deploy your workloads across hybrid cloud providers and environments. [View a comparison between Kubernetes and OpenShift clusters](/docs/openshift?topic=openshift-cs_ov#openshift_kubernetes).
* [{{site.data.keyword.cloud_notm}} Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-getting-started) is the premier industry standard Platform-as-a-Service (PaaS) that ensures fast, easy, and reliable deployment of cloud-native apps. Cloud Foundry ensures that the build and deploy aspects of coding remain carefully coordinated with any attached services — resulting in quick, consistent, and reliable iterating of applications. Cloud Foundry has a Lite plan that allows quick deployments for testing purposes.

## Before you begin
{: #prereq-deploy-apps}

### For all deployment targets
{: #prereq-deploy-all}

For all deployment targets, ensure that you're aware of the following requirements:

* Depending on your [{{site.data.keyword.cloud_notm}} account type](https://{DomainName}/registration), access to certain resources might be limited or constrained. Depending on your plan limits, certain capabilities that are required by some toolchains might not be available.
* Install the [{{site.data.keyword.cloud_notm}} command-line interface (CLI)](/docs/cli?topic=cli-getting-started), which includes the {{site.data.keyword.dev_cli_short}} [(**ibmcloud dev**)](/docs/cli?topic=cli-idt-cli) commands.
* Create a Docker account, run the Docker app, and sign in. Docker is installed as part of the developer tools. Docker must be running for the build commands to work.

### For specific deployment targets
{: #prereq-deploy-specific}

For information about requirements for specific deployment targets, see the following table.

| Deployment target | Prerequisites | 
|--------|---------------|
| {{site.data.keyword.cloud_notm}} Foundry | Ensure that you have access to a [Cloud Foundry org and space](https://{DomainName}/account/cloud-foundry). [Learn more](/docs/account?topic=account-orgsspacesusers) or [create a Cloud Foundry org](https://{DomainName}/account/cloud-foundry). |
| {{site.data.keyword.cloud_notm}} Kubernetes Service / Helm | Create a free or paid cluster. One free Kubernetes cluster is available per account. For more information, see [Deploying apps to Kubernetes clusters](/docs/containers?topic=containers-app). Helm is a package manager for Kubernetes that allows you to package, configure, and deploy apps and services to {{site.data.keyword.cloud_notm}} Kubernetes Service. With either paid or free account plans, select this option to experiment with your starter kit in a Kubernetes or OpenShift environment. |
| {{site.data.keyword.cloud_notm}} Kubernetes Service / Knative | Knative is an extension of Kubernetes that hides many of the complex management tasks and adds serverless capabilities. The Knative deployment type is available only if Knative is installed on the cluster that you select.<br>1. Install the [IBM Cloud CLI, the IBM Cloud Kubernetes Service plug-in, and the Kubernetes CLI](/docs/containers?topic=containers-cs_cli_install).<br>2. Create a [standard Kubernetes cluster](https://{DomainName}/kubernetes/catalog/cluster) with 3 worker nodes that each have 4 cores and 16 GB memory (b3c.4x16) or more. For more information, see [Creating a standard classic cluster in the console](/docs/containers?topic=containers-clusters#clusters_ui). Ensure that you note the total monthly cost before you create the cluster.<br>3. Install the [Istio add-on](/docs/containers?topic=containers-istio).<br>4. Install the [Knative add-on](/docs/containers?topic=containers-serverless-apps-knative#knative-setup). |
| Red Hat OpenShift on {{site.data.keyword.cloud_notm}} | OpenShift is available only through a standard cluster, which requires you to have a billable account. [Learn more](https://{DomainName}/docs/openshift?topic=openshift-getting-started) or [create an OpenShift cluster](https://{DomainName}/kubernetes/overview).|


## Before you deploy

Get started by [creating your app](/docs/apps?topic=apps-getting-started) from the {{site.data.keyword.cloud_notm}} console in either of the following ways:
 * Use the Apps tile on the [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external} to use a blank starter kit or to bring your own code.
 * Use a [starter kit](https://{DomainName}/developer/appservice/starter-kits){: external}.

## Deploying your app automatically
{: deploy-console-auto}

All toolchains that are created from the {{site.data.keyword.cloud_notm}} console are configured for automatic deployment.
{: note}

1. On the App details page for your app, click **Deploy your app**.
2. On the Deploy your app page, select a deployment target. Set up your deployment target according to the instructions for the target that you select:
  * **IBM Kubernetes Service**. With this option, you can either create a cluster or [deploy to an existing Kubernetes cluster](/docs/containers?topic=containers-app). If you create a cluster, allow 10 - 20 minutes for the cluster to be provisioned. Select a deployment type of **Helm** or **Knative**, and then select the region and cluster name.
  * **Red Hat OpenShift on IBM Cloud**. If you have an available [OpenShift cluster](/docs/openshift?topic=openshift-openshift_apps), you can select it from the **Cluster name** list. If you don't have an available cluster, you must create one before you continue. Your cluster creation might take some time to complete. After the cluster state shows **Normal**, the cluster network and load-balancing component take about 10 more minutes to deploy and update the cluster domain that you use for the OpenShift web console and other routes.
  * **Cloud Foundry**. This option deploys your cloud-native app without you needing to manage the underlying infrastructure. For more information, see [Deploying apps to Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps).
3. Provide a name for your toolchain.
4. Select the region to create your toolchain in, and then select the [resource group](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains-iam-security) that provides access to your new toolchain.
5. Click **Create**.

The DevOps toolchain is created automatically, and the deployment process begins. You can view the deployment status in the **Delivery Pipeline** tile, or you can click the name of the Delivery Pipeline. The **Build Stage** and **Deploy Stage** tiles indicate the status.

## Deploying your app manually
{: deploy-console-manual}

Continuous delivery is automatically enabled for some apps. You can enable continuous delivery to automate builds, tests, and deployments through the Delivery Pipeline and GitHub. With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the master branch in your repo. 

To manually deploy your app from your DevOps toolchain, complete these steps:

1. On the App details page for your app, click the Delivery Pipeline name.
2. On the Delivery Pipeline page, you can start builds, change the deployment configuration, and view logs and history.

## Related information
{: deploy-related-info}

For more information, see:
* [Building and deploying](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)
* [Creating toolchains](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)
* [Build from a pull request in the Continuous Delivery Pipeline](https://www.ibm.com/cloud/blog/build-from-a-pull-request-in-the-continuous-delivery-pipeline){: external}
* [Get Help from the IBM Cloud Continuous Delivery Development Team on Slack](https://www.ibm.com/cloud/blog/reach-out-to-the-ibm-cloud-development-teams-on-slack){: external}


## Verifying that your app is running
{: #verify-runningapp}

After your app is built and deployed, you can view the app's URL to make sure that it's running.

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

### Apps that are deployed to Cloud Foundry
{: #view-cf-runningapp}

You can view the app's URL from the App details page by clicking **Visit App URL**. If the app is running, a message that includes `Congratulations` is displayed.

If you are using the command line, run the [**ibmcloud dev view**]/docs/cli?topic=cli-idt-cli#view) command to view the URL of your app. Then, go to the URL in your browser.

## Next steps
{: #next-steps-deployapps}

* If you encounter errors with deployment to a Kubernetes cluster, check the troubleshooting topic for known issues like [exceeding storage quota](/docs/apps?topic=apps-managingapps#exceed_quota), or learn how to [access Kubernetes logs](/docs/apps?topic=apps-managingapps#access_kube_logs) to look for errors.

* Access the service configuration in your code:
	- You can use the _@Value_ annotation, or use the Spring framework environment class _getProperty()_ method. For more information, see [Accessing credentials](/docs/java?topic=java-spring-configuration).

* Add new service credentials to your Kubernetes environment:
	- When you add another service to your app after the DevOps toolchain is created, those service credentials aren't automatically updated to your deployed app and GitLab repository. You must [manually add the credentials to the deployment environment](/docs/apps?topic=apps-credentials_overview).
