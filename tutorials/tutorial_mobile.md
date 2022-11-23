---

copyright:
  years: 2018, 2022
lastupdated: "2022-06-03"

keywords: apps, mobile, mobile app, starter kit, developer tools, devops toolchain, toolchain, create mobile app, mobile starter kit, android, ios, swift, xcode
content-type: tutorial
services: apps
account-plan: lite
completion-time: 30m
subcollection: apps

---

{{site.data.keyword.attribute-definition-list}}

# Creating mobile apps
{: #tutorial-mobile}
{: toc-content-type="tutorial"} 
{: toc-services="apps"} 
{: toc-completion-time="30m"}

Use this tutorial to create a mobile app using an {{site.data.keyword.cloud}} mobile starter kit. You can create a preconfigured app or use the blank starter kit to create a custom mobile app.
{: shortdesc}

## Objectives
{: #objectives-mobile}

* Create an app with a mobile starter kit.
* Add services to the app (optional).
* Download and run the app.

## Before you begin
{: #prereqs-mobile}

* Depending on your [{{site.data.keyword.cloud}} account type](/registration){: external}, access to certain resources might be limited or constrained. Depending on your plan limits, certain capabilities that are required by some toolchains might not be available. For more information, see [Setting up your IBM Cloud account](/docs/account?topic=account-account-getting-started).
* Install the [{{site.data.keyword.cloud_notm}} Command Line Interface (CLI)](/docs/cli?topic=cli-getting-started), which includes the {{site.data.keyword.dev_cli_short}} (`ibmcloud dev`) commands.
* Create a Docker account, run the Docker app, and sign in. Docker is installed as part of the developer tools. Docker must be running for the build commands to work.

## Creating a mobile app 
{: #create-mobile}
{: step}

### Creating a mobile app with a starter kit
{: #create-mobile-starter}

To create a mobile app by using a starter kit, complete these steps:

1. Go to the [{{site.data.keyword.cloud_notm}} App Development console](/developer/appservice/starter-kits){: external}.
1. Type `mobile` in the search bar to filter the list of starter kits.
1. Select a mobile starter kit to view details about it.
1. Select the **Create** tab.
1. On the App details page for the starter kit, enter a name for your app, and select a resource group. If a resource group doesn't exist, you must [create one](/account/resource-groups){: external}.
1. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/account?topic=account-tag).
1. Select your language. For this tutorial, select **iOS Swift**. Some starter kits might be available in only one language.
1. Select your pricing plan. Use the **Lite** option for this tutorial. If any services are required, they are automatically defined in the starter kit.
1. Click **Create**.

### Creating a custom mobile app
{: #create-mobile-basic}

To create a custom mobile app, complete these steps:

1. From your [{{site.data.keyword.cloud_notm}} console](https://{DomainName}){: external}, click **Create an app** in the Apps tile.

   You can also create a custom mobile app from the [App Development console](/developer/appservice/starter-kits){: external}.
   {: tip}

2. On the App details page, enter a name your app, and select a resource group. If a resource group doesn't exist, you must [create one](/account/resource-groups){: external}.
3. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/account?topic=account-tag).
4. Select **Create a new app** as a starting point.
5. Select **Mobile** as the app type.
6. Select your language. For this tutorial, select **iOS Swift**. Some starter kits might be available in only one language.
7. Select your pricing plan. You can use the free option for this tutorial.
8. Click **Create**.

### Creating a mobile app with the CLI
{: #create-mobile-cli}

To create a mobile app with the [{{site.data.keyword.dev_cli_short}} (`ibmcloud dev`) commands](/docs/cli?topic=cli-getting-started), complete these steps:

1. Open a terminal and navigate to a directory where you would like to create your app.
2. Run the `ibmcloud dev create` command.
3. Select the **Mobile App** option from the list of app types.
4. Select a mobile platform from the list: Android or Swift.
5. Select a starter kit.
6. Enter a name for your app.
7. If services are added, you are prompted to select a region and pricing plan for each service.

The app is created in your current working directory.

## Adding services (optional)
{: #resources-mobile}
{: step}

If a starter kit requires specific services, the required services are automatically created and provisioned for you. You can connect more services to your app in the {{site.data.keyword.cloud_notm}} console from the App details page, which is displayed as soon as you create the app.

If you want to create a new service instance or connect any existing services to your app, complete the following steps:

1. On the App details page, click **Create service** or **Connect existing services**, depending on whether you already have services that you want to connect to this app.
2. Select the kind of service you want, and follow the prompts to either add an existing service to your app or create a service instance.

After you add all the services that you want, the services are displayed in the App details page.

After you connect a service to your app, you can navigate to the service documentation and API references. Simply click the links within the **Services** card to view the related docs.

For more information, see [Adding a service to your app](/docs/apps?topic=apps-add-service).

## Downloading the code
{: #mobile-download-code}
{: step}

To download your app code and work with it locally, complete these steps:

1. On the App details page, click **Download code**.
2. Import the app to your integrated development environment.
3. Modify and save the code.

## Running your mobile app
{: #run-mobile-app}
{: step}

### Running your Swift app in Xcode
{: #run_swift}

If you are using iOS Swift as your implementation languages, complete these steps:

1. Open the `README.md` file in a Markdown viewer to review the steps to configure your app.
2. Open your terminal and navigate to your app folder, and run the following commands:
    1. Run `pod setup` if you need to set up your CocoaPods repository.
    2. Run `pod update` if you need to update you update your existing pods.
    3. Run `pod install` to install the pods for your app.
3. Open your `<appname>.xcworkspace` Xcode workspace.
4. Run your app.

### Running your Android app in Android Studio
{: #run_android}

If you are using Android as your mobile app's platform, complete these steps:

1. Open the `README.md` file in a Markdown viewer to configure your app.
2. Open your `BasicProject-Android` app in Android Studio.
3. Run your app.

## Related information
{: #related-mobile}

You can learn more about mobile apps by exploring these tutorials:

 * [Mobile application with a serverless backend](/docs/solution-tutorials?topic=solution-tutorials-serverless-mobile-backend)
