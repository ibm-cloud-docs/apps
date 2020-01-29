---

copyright:
  years: 2018, 2020
lastupdated: "2020-01-28"

keywords: apps, mobile, mobile app, starter kit, developer tools, devops toolchain, toolchain, create mobile app, mobile starter kit, android, ios, swift, xcode

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:external: target="_blank" .external}

# Creating mobile apps
{: #tutorial-mobile}

{{site.data.keyword.cloud}} offers mobile starter kits to help you create a mobile application quickly. Select a language, framework, and tools from the mobile starter kits to start working with a preconfigured app. Or, you can use a basic starter kit to create a custom mobile app.
{: shortdesc}

## Before you begin
{: #prereqs-mobile}

Install the [{{site.data.keyword.dev_cli_long}} command-line interface (CLI)](/docs/cli?topic=cloud-cli-getting-started).

## Creating a mobile app with a starter kit
{: #create-mobile}

To create a mobile app by using a starter kit, complete these steps:

1. Go to the [App Development console](https://{DomainName}/developer/appservice/starter-kits){: external}.
1. Type `mobile` in the search bar to filter the list of starter kits.
1. Select a mobile starter kit, such as `Mobile App with Push Notifications`.
1. On the starter kit overview page, click **Create app**.
1. On the App details page for the starter kit, enter a name for your app, and select a resource group. If a resource group doesn't exist, you must [create one](https://{DomainName}/account/resource-groups){: external}.
1. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/resources?topic=resources-tag).
1. Select your language. For this tutorial, select **iOS Swift**. Some starter kits might be available in only one language.
1. Select your pricing plan. Use the **Lite** option for this tutorial. If any services are required, they are automatically defined in the starter kit.
1. Click **Create**.

## Creating a custom mobile app
{: #create-mobile-basic}

To create a custom mobile app, complete these steps:

1. From your [{{site.data.keyword.cloud_notm}} dashboard](https://{DomainName}){: external}, click **Create an app** in the Apps tile.

  You can also create a custom mobile app from the [App Development console](https://{DomainName}/developer/appservice/starter-kits){: external}.
  {: tip}

2. On the App details page, enter a name your app, and select a resource group. If a resource group doesn't exist, you must [create one](https://{DomainName}/account/resource-groups){: external}.
3. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/resources?topic=resources-tag).
4. Select **Create a new app** as a starting point.
5. Select **Mobile** as the app type.
6. Select your language. For this tutorial, select **iOS Swift**. Some starter kits might be available in only one language.
7. Select your pricing plan. You can use the free option for this tutorial.
8. Click **Create**.

## Creating a mobile app with the CLI
{: #create-mobile-cli}

To create a mobile app with the [{{site.data.keyword.dev_cli_long}} CLI](/docs/cli?topic=cloud-cli-getting-started), complete these steps:

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

If a starter kit requires specific services, the auto-provisioned service instances are automatically created and connected to your app. You can add services that enhance your app with the cognitive power of Watson, add mobile services, or security services. For this tutorial, add a place to manage your data.

If you want to create a new service instance or connect any existing services to your app, complete these steps:

1. On the App details page, click **Create service** or **Connect existing services**, depending on whether you already have services that you want to connect to this app.
2. Select the kind of service you want, and follow the prompts to either add an existing service to your app or create a service instance. For example, select **Databases** > **Next** > **Cloudant** > **Next**.
3. Select your pricing plan. Use the **Lite** option for this tutorial.
4. Click **Create**.

After you add all the services that you want, the services are displayed in the App details page.

## Downloading the code
{: #mobile-download-code}

To download your app code and work with it locally, complete these steps:

1. On the App details page, click **Download code**.
2. Import the app to your integrated development environment.
3. Modify and save the code.

## Running your mobile app
{: #run-mobile-app}

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

 * [iOS mobile application with Push Notifications](/docs/tutorials?topic=solution-tutorials-ios-mobile-push-analytics)
 * [Android native mobile application with Push Notifications](/docs/tutorials?topic=solution-tutorials-android-mobile-push-analytics)
 * [Mobile application with a serverless backend](/docs/tutorials?topic=solution-tutorials-serverless-mobile-backend)
