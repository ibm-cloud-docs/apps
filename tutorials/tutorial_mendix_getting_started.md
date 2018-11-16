---

copyright:
  years: 2018
lastupdated: "2018-11-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Creating apps with Mendix
{: #getting-started}

Mendix is a low-code development environment and toolset that helps you deliver multi-device applications faster, with fewer development resources, that run on {{site.data.keyword.cloud}}. By selecting a Mendix low-code starter kit, you're guided to set up your account on Mendix Platform, start your project, and select your deployment environment in either Cloud Foundry or your Kubernetes cluster.
{: shortdesc}

## Selecting a starter kit
{: #select-a-starter-kit}

2. From the [{{site.data.keyword.cloud_notm}} dashboard ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/dashboard/apps){: new_window}, click the **Menu** icon ![Menu icon](../../icons/icon_hamburger.svg).
3. Select a Mendix low-code starter kit from one of the following categories:
  * [Mobile ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/developer/appservice/starter-kits/mendix-mobile-app)
  * [Watson Web or Mobile App ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson)
  * [Web App ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.bluemix.net/developer/appservice/starter-kits/mendix-web-app)
4. Click **Create app**.
5. Name your app. 
6. Click **Create**.

## Authorizing IBM to create your project on Mendix and link accounts
{: #link-mendix-account}

If you're not using Mendix with {{site.data.keyword.cloud_notm}} yet, you are guided to the Mendix Platform to sign up and authorize {{site.data.keyword.cloud_notm}} to create a new project on Mendix Platform in your behalf. This project is linked to {{site.data.keyword.cloud_notm}}, so deployments are automatically directed to {{site.data.keyword.cloud_notm}}.

1. If you see this message: "To complete app creation, a Mendix user account is required. Would you like to link your account now?", click **Link Account**.
2. On the Mendix confirmation page, select **I agree to the Mendix Privacy Policy and Terms**, and click **Confirm**.
3. When prompted, provide your email address, password, and country, and then click **Create**.
4. On the **Authorize access to your Mendix account** page, click **Authorize**.

After the authorization is complete, your browser returns to the Mendix app that you're creating. The **Choose a deployment environment** page is displayed.

## Selecting a deployment option for your Mendix app
{: #select-deployment}

1. On the **Choose a deployment environment** page, select Cloud Foundry, or one of your Kubernetes clusters that are running on {{site.data.keyword.cloud_notm}}.
2. Optional. If you don't have a Kubernetes cluster, you can create one now.
3. On the **Configure toolchain** page, select your region and resource group, and then click **Create**.

A DevOps toolchain is created. The toolchain integrates your Mendix project within the Mendix Platform in your {{site.data.keyword.cloud_notm}} environment. A default application is deployed to your target deployment so that you can verify that the application was successfully deployed upon completion of the DevOps toolchain.

Mendix Cloud Foundry deployments require the PostGRES database service, which doesn't have a lite tier.   If you want to evaluate the Mendix starter kits by using a lite account, you can target a trial Kubernetes cluster.
{: tip}

If you selected a Kubernetes cluster for deployment, see the [Mendix Kubernetes tutorial](/docs/apps/tutorials/tutorial_mendix_kubernetes.html) to learn how to configure your cluster for production use.


## Continuing the Mendix development and deployment lifecycle
{: #development-lifecycle}

Mendix is a low-code authoring environment. The development lifecycle requires you to open your project in the Mendix Modeler desktop application.

1. From your {{site.data.keyword.cloud_notm}} application, click **Edit on Mendix**.
2. In the Mendix web portal, click **Edit in Desktop Modeler**.
  The Mendix application is opened in the desktop modeler.
3. Edit your Mendix app, and save your changes.
4. Use the Mendix Desktop Modeler application's **Run** menu, and select the **Run** option.
  The deployment package is created and uploaded to Mendix. After the deployment package is created, you can deploy your application to {{site.data.keyword.cloud_notm}}.
5. To deploy your Mendix application, go back to your **App details** page on {{site.data.keyword.cloud_notm}}, and click **Deploy Application**.
  This action starts your application's DevOps toolchain, which pulls the latest deployment from Mendix and deploys it to your target environment. After the deployment is complete, the latest version of your application automatically starts and becomes available.

All Mendix applications are to be deployed to {{site.data.keyword.cloud_notm}} by clicking **Deploy Application** in the **App details** page on {{site.data.keyword.cloud_notm}}. Don't manually invoke Mendix toolchains through the IBM DevOps interface. Launching toolchains manually through the DevOps interface might result in a failed deployment due to a lack of required metadata that is critical for Mendix deployments. Depending on the state of your application, either a failure during the DevOps toolchain launch, or an error in the deployed application, might occur. If you manually launch a toolchain and experience a failure, you can restore your application deployment by clicking **Deploy Application** in the **App details** page on {{site.data.keyword.cloud_notm}}. This action triggers a complete DevOps flow for the Mendix application, which includes the required metadata.
{: tip}

## Next steps 
{: #next steps}

To deploy your app to the {{site.data.keyword.containerlong_notm}}, configure your app for production deployment. For more information, see [Mendix Kubernetes tutorial](/docs/apps/tutorials/tutorial_mendix_kubernetes.html). 
