---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Deploying your own code to a Kubernetes cluster
{: #tutorial}

Learn how to create an app in {{site.data.keyword.cloud}} by using your existing app repository. You can connect your existing DevOps toolchain or create one, and continuously deliver an app to a secure container in a Kubernetes cluster. This tutorial helps you set up a continuous integration DevOps pipeline so that the change is automatically built and propagated all the way to your deployed app in the Kubernetes cluster.
{: shortdesc}

When you already have a source code repository with a code base for a working backend application, {{site.data.keyword.cloud_notm}} helps you organize this asset into an aggregate view of all the assets that make up the breadth of your whole product. {{site.data.keyword.cloud_notm}} gets you up and running on a scalable DevOps workflow when you use the DevOps toolchain feature. This tutorial helps the experienced developer or DevOps engineer acquire and configure a target {{site.data.keyword.cloud_notm}} Kubernetes cluster and configure and run a DevOps toolchain, all under the guidance of cloud best practices.

A _cluster_ is a set of resources, worker nodes, networks, and storage devices that keep apps highly available. After you create your cluster, you can deploy your apps in containers.
{: tip}

## Before you begin
{: #prereqs}

* Follow the steps for [Creating apps from your own code repository](/docs/apps/tutorials/tutorial_byoc.html) to create an app.
* From the [{{site.data.keyword.cloud_notm}} dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://{DomainName}){: new_window}, click the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg), and select **Containers** to [configure a Kubernetes cluster](/docs/containers/container_index.html).
* To confirm that your app runs in Docker, run the following commands:
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install`
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* Then, visit your URL, such as `http://localhost/springboothelloworld/sayhello`.   
Press `Ctrl+C` to stop the Docker run.

## Optional. Adding resources to your app
{: #add_resources}

Add a service resource to your application and {{site.data.keyword.cloud_notm}} creates the service for you. The provisioning process can be different for different types of services. For example, a database service creates a database, and a push notification service for mobile applications generates configuration information. {{site.data.keyword.cloud_notm}} provides the resources of a service to your application by using a service instance. A service instance can be shared across web applications.

This process provisions a service instance, creates a resource key (credentials), and binds it to your app. For more information, see [Adding a service to your app](/docs/apps/reqnsi.html).

### Copying service credentials to your environment

After you add a service resource to your app, note that the credentials for that service are displayed in the **Credentials** box. You must copy the credentials to your deployment environment.

For more information about copying credentials to your environment, see [Adding credentials to your Kubernetes environment](/docs/apps/creds_kube.html).


## Preparing your app for deployment by using a DevOps toolchain
{: #connect_toolchain}

In this step, you attach a DevOps toolchain to the application and configure it to be deployed to a Kubernetes cluster that is hosted in the {{site.data.keyword.cloud_notm}} Kubernetes service.

The DevOps toolchain is flexible enough to allow managed execution of arbitrary stages of shell script execution. In other words, you can do nearly anything with a DevOps toolchain. The scope of this section focuses on deployment of your app on a Kubernetes cluster, while keeping in mind "future-proofing" for scaled DevOps and cloud best practices.

Establishing a link between your app, toolchain, and repo is a step toward organizing your product assets. It also helps aggregate a view of your source repository with your DevOps workflow, your running app instances, and dependent services across all of your deployment targets.

In the Connect Toolchain page, you have a few options:

* Connect your app to an existing toolchain.
* Connect your app to an existing toolchain that doesn't contain your repo. Then, connect the toolchain to your repo later.
* Connect your app to a new toolchain.

### Connect your app to an existing toolchain
{: #connect_toolchain_repo}

If you have one or more DevOps toolchains that are already connected to the Git repo that you specified during your app creation, those toolchains are displayed in the **With repo** table. The toolchain must be configured to retrieve the source from the same repository that you defined in the app. You most likely want to select one of those toolchains to connect to your app.

### Connect your app to an existing toolchain that doesn't contain your repo
{: #connect_toolchain_notrepo}

If you have one or more DevOps toolchains that are associated with your account, but are not connected to the Git repo that you specified during your app creation, those toolchains are displayed in the table that's labeled **without your repo**. You can select one of those toolchains and connect it to your app, but you must also manually add your repo to that toolchain.

For more information about adding your repo to your toolchain, see:

 * [Configuring Git repos and issue tracking](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitbluemix)
 * [Configuring GitHub](/docs/services/ContinuousDelivery/toolchains_integrations.html#github)
 * [Configuring GitLab](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitlab)


### Connect your app to a new toolchain
{: #create_toolchain}

You have these options for connecting your app to a new toolchain:
* If you don't want to create a DevOps toolchain from scratch, you can cloud-enable your existing code by using the [`ibmcloud dev enable` command](/docs/cli/idt/commands.html#enable). The command generates a DevOps toolchain template that you check into your repository. Then, you use that template as the instruction set for what the DevOps toolchain creates. For more information, see the [CLI documentation](/docs/apps/create-deploy-cli.html#byoc).
* Create a DevOps toolchain from scratch within the console. If you want to fully control the creation of the DevOps toolchain with no changes in your code repository, create the toolchain from scratch. For more information, see [Creating a DevOps toolchain from scratch](#create_toolchain_scratch).

#### Creating a DevOps toolchain from scratch
{: #create_toolchain_scratch}

If you want to create a toolchain from scratch and connect it to your app, complete these steps. You also create all of the integrations to build your app and deploy it to Kubernetes cluster. The DevOps toolchain feature offers templates, but these steps show you how to set up a DevOps toolchain from scratch.

When you choose to create a toolchain from your new app, the [Create a Toolchain](https://{DomainName}/devops/create) page in the [DevOps dashboard](https://{DomainName}/devops/) opens in a new tab in your browser. After you create and configure your toolchain in that tab, you must go back to the **Connect a toolchain** page in your app and refresh the page.
{:tip}

1. On the **Create a Toolchain** page, click the **Build your own toolchain** template.
2. On the **Build your own toolchain** page, enter a name for your toolchain, select a region and resource group (default), and click **Create**.

An empty toolchain with no preconfigured tools or integrations is created. Continue to configure and test your new toolchain by completing the remaining steps.

## Adding a GitHub integration

You can configure the DevOps toolchain with GitHub integration by using the following steps:

1. In your DevOps toolchain template, click **Add a Tool**.
2. Select **GitHub** (if your repository is indeed on public GitHub or on Enterprise GitHub).
3. On the **Configure the Integration** page for GitHub, complete these steps:
  * Select (or enter) the **GitHub Server** URL.
  * If you see an "Unauthorized on GitHub" message, click **Authorize**. Then, on the **Authorize IBM Cloud Toolchains** page, click **Authorize IBM-Cloud**. Then, enter your GitHub password.
  * On the **Configure the Integration** page, select **Existing** for the **Repository Type** so that the DevOps toolchain configures the repository with a webhook and does _not_ make any fork or copy of your repository.
  * Enter your **Repository URL**. (For example, `https://github.com/yourrepo/spring-boot-hello-world`).
  * Wait a few moments, and you might be prompted authorize GitHub to grant DevOps toolchain permission to use the GitHub ReST API to configure your repo with the webhooks that are necessary to trigger the toolchain.
  * Click **Create Integration**.

You configured this DevOps toolchain with an integration for your GitHub repo. Doing so allows the toolchain to set a webhook in your repo so that pull requests and code pushes in that repo trigger a POST to the toolchain. You can look in the settings of your repo to see the new webhook.

## Adding a Delivery Pipeline to build, test, and deploy your app

The Delivery Pipeline is where the work happens.

1. Click **Add a Tool**.
2. Select **Delivery Pipeline**.
3. On the **Configure the Integration** page for Delivery Pipeline, complete these steps:
 * Enter "Continuous Integration" for the pipeline name.
 * Click **Create Integration**.

You created an empty delivery pipeline. Next, you define pipeline stages to direct your input (the GitHub repo contents) to their destination. Because this tutorial assumes that you have a GitHub repo that produces a working Docker image and is targeting an IBM Containers Kubernetes cluster, you create pipeline stages with inputs, shell scripts, and outputs that achieve this goal.

### Configuring the "Build and Publish" pipeline stage

1. Click the delivery pipeline that you created.
2. On the delivery pipeline page, click **Add a Stage**.
3. On the **Input** tab of the **Stage Configuration** page, complete the fields as follows:
  * For the stage name, type **Build & Publish Docker Image**.
  * **Input type**: Select **Git repository**.
  * **Git repository**: Select your GitHub repo.
  * **Branch**: Select the branch that you use for continuous integration.
4. Click the **Jobs** tab, and complete the fields as follows:
  * Click the **Add Job '+'** icon, and select **Build** for the job type.
  * Enter a name, such as **Build & Publish**.
  * **Builder type**: select **Container Registry**.
  * **IBM Cloud region**: Select the region where your Kubernetes cluster is located.
  * **API key**: Select **Enter an existing API key**. If you don't have a key or don't know your API key, you can [get an API key](https://{DomainName}/iam/#/apikeys) by opening a separate browser window and navigating to **Manage** > **Security** > **Platform API Keys**. Be sure to keep this key in a safe place.
  * **Account name**: This field is automatically completed when you enter an API key.
  * **Container Registry namespace**: Enter the [container registry namespace](https://{DomainName}/containers-kubernetes/registry/namespaces) (You can find it by clicking the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg), and selecting **Containers** > **Registry** > **Namespaces**.)
  * **Docker image name**: Enter **continuous** because this pipeline build stage is for the continuous build of your repo's continuous integration branch.
  * **Build script**: Notice the shell script. It lacks the app build instructions for _your_ repository. You need to add a line or more after the first `#!/bin/bash` line. For example, for a repo that is built by using maven, you might add a few lines similar to the following example:

    ```bash
    export JAVA_HOME=/opt/IBM/java8
    # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
    export MAVEN_OPTS="-Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
    mvn -B clean verify
    ```
    {: codeblock}
5. Click **Save**. Your "Build and Publish" pipeline stage now appears in your toolchain.

### Testing your "Build and Publish" pipeline stage

Click the **Play** icon until the build succeeds. You know it works when the stage turns green, and the script output confirms your expectations. The goal in this stage is to publish a Docker image to your image registry. If the script doesn't display enough for your confidence, you can see the image registry to confirm publication by clicking the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg), and then selecting **Containers** > **Registry** > **Private Repositories**. Then, confirm that a repository that ends with the name `/continuous` is listed. (Remember, that was the image name.)

### Configuring the "Deploy to Cluster" pipeline stage

So far, you published a Docker image to your private Docker image registry. Now, it's time to create a stage that deploys that image to your Kubernetes cluster.

1. On the delivery pipeline page, click **Add a Stage**.
2. On the **Input** tab of the **Stage Configuration** page, complete the fields as follows:
  * **Name**: Type **Deploy**.
  * **Input type**: Select **Build artifacts**.
  * **Stage**: Select **Build & Publish Docker Image**.
  * **Job**: Select **Build & Publish**.
  * **Stage trigger**: Because this is your continuous integration pipeline, select the default **Run jobs then the previous stage is completed**.
3. Click the **Jobs** tab, and complete the fields as follows:
  * Click the **Add Job '+'** icon, and select **Deploy** for the job type.
  * Enter a name, such as **Deploy to Continuous Integration Cluster**.
  * **Deployer type**: Select **Kubernetes**.
  * **IBM Cloud region**: Select the region where your Kubernetes cluster is located.
  * **API key**: Select **Enter an existing API key**. If you don't have a key or don't know your API key, you can [get an API key](https://{DomainName}/iam/#/apikeys) by opening a separate browser window and navigating to **Manage** > **Security** > **Platform API Keys**. Be sure to keep this key in a safe place.
  * Accept the remaining default settings.
4. Click **Save**. Your "Deploy" pipeline stage now appears in your toolchain.

### Testing your "Deploy to Cluster" pipeline stage

Click the **Play** icon until the build succeeds. You know it works when the stage turns green, and the script output confirms your expectations. You can view the logs for the stage. Near the end of the logs, find a clickable link to the running app. However, only _you_ know your app's context root and path. Append the correct path to confirm that it runs.