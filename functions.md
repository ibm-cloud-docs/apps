---

copyright:
  years: 2018, 2019
lastupdated: "2019-08-26"

keywords: apps, serverless, serverless app, functions, cli, api, sdk, create serverless app, serverless app tutorial

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creating serverless apps
{: #serverless}

For serverless development, you can use {{site.data.keyword.openwhisk}}, which is the IBM functions-as-a-service (FaaS) offering. You can run application logic with {{site.data.keyword.openwhisk_short}} in response to events or direct invocations from web or mobile apps over HTTP without provisioning or managing servers. {{site.data.keyword.openwhisk_short}} performs system administration, such as auto-scaling, availability management, and maintenance so that you, as a developer, can focus on writing app logic.
{: shortdesc}

You can develop your serverless apps by using one of the following methods:
* {{site.data.keyword.openwhisk_short}} user interface (UI).
* {{site.data.keyword.openwhisk_short}} command-line interface (CLI), which provides more control over your deployment and operations.
* {{site.data.keyword.openwhisk_short}} starter kit, in which you can configure continuous delivery by using a DevOps toolchain and a Delivery Pipeline.

For more detailed information about {{site.data.keyword.openwhisk_short}}, check out the [documentation](/docs/openwhisk?topic=cloud-functions-getting-started).


## Developing with the {{site.data.keyword.openwhisk_short}} UI
{: #serverless-apps-ui}

Try out {{site.data.keyword.openwhisk_short}} in your [browser](https://{DomainName}/functions/actions){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon")}. Go to the [Concepts](https://{DomainName}/functions/learn){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") page for a quick tour of the {{site.data.keyword.openwhisk_short}} user interface.

## Developing with the CLI
{: #openwhisk_start_configure_cli}

To learn more about installing and developing with the {{site.data.keyword.openwhisk_short}} CLI, see [Setting up the {{site.data.keyword.openwhisk_short}} CLI](https://{DomainName}/functions/cli){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").

## Exposing APIs and data sets as web actions
{: #expose-actions}

By default, {{site.data.keyword.openwhisk_short}} defines actions that require an authentication key. In production mobile environments, it is often necessary to authorize mobile clients based on OAuth flows to expose APIs and specific data sets.

{{site.data.keyword.openwhisk_short}} enables developers to expose their functions as web actions, which are annotated, to quickly build web-based apps. You can program backend logic with annotated actions that your web app can access anonymously, without requiring a {{site.data.keyword.openwhisk_short}} authentication key.

To expose an action as a web action, go to the **Endpoints** tab of your action, and select **Enable as Web Action**.

Now, users can reach the action from a browser or cURL request, for example:
```
curl https://openwhisk.cloud.ibm.com/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

Output:
```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} provides a [mobile SDK](/docs/openwhisk?topic=cloud-functions-pkg_mobile_sdk) for iOS and watchOS devices that enables mobile apps to easily send remote triggers and invoke remote actions.

## Creating serverless apps by using a starter kit
{: #serverless-starter}

You can use a starter kit to create a serverless app, such as Python Example Serverless App. To locate the starter kits and create an app, complete these steps:

1. Go to the [App Service Starter Kits](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon") page in the {{site.data.keyword.dev_console}} console.
2. Type `serverless` in the search bar to filter the list of starter kits.
3. Select a serverless starter kit, such as Python Example Serverless App.
4. In the App details page for the starter kit, name your app, and select a resource group.
5. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/resources?topic=resources-tag).
6. Create or select an existing Cloudant service instance.
7. Optional. To inspect your code before you add more services or deploy your app, click **View source code**. The app code includes a `README.md` file that contains technical details about the app. Check the `README.md` file to find out whether you need to take more actions to get your app up and running.
8. Click **Create**.

Great start! You just created an app!

## Adding services (optional)
{: #serverless-services}

If a starter kit requires specific services, the auto-provisioned service instances are automatically created and connected to your app.

If you want to create or connect more services, complete these steps:

1. On the App details page, click **Create service** or **Connect existing services**, depending on whether you already have services that you want to connect to this app.
2. Select the kind of service you want, and follow the prompts to either add an existing service to your app or create a service instance.

After you add all the services that you want, the services are displayed in the App details page.

## Deploying your app
{: #serverless-deploy}

To deploy your app, complete these steps:

1. On the App details page, click **Deploy**.
2. Select **Deploy to Cloud Functions**, and click **Next**.
3. On the Configure toolchain page, enter a toolchain name, select a region, and click **Create**. After you select and configure the deployment target, the App details page indicates that continuous delivery is configured.
4. Optional. Review the actions in the {{site.data.keyword.openwhisk_short}} console by clicking the Actions icon ![More Actions icon](../icons/action-menu-icon.svg) and selecting **Open Cloud Functions**.
5. Optional. View the repo that contains the generated code for your app and services by clicking **View repo**.

## Verifying that your app is deployed
{: #serverless-verify}

With a properly configured toolchain, a build-deploy cycle automatically starts with each merge to the master branch in your repo. For more information, see [Building and deploying](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

To verify that your app is successfully deployed, complete these steps:

1. On the App details page, click **View toolchain**.
2. Click **Delivery Pipeline** where you can start builds, manage deployment, and view logs and history.
3. If the deployment is successful, each pipeline stage indicates **Stage Passed**.
4. To view the action and API information, click **View logs and history** in the **Deploy Stage** tile.
