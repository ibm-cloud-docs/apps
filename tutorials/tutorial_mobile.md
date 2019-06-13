---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-13"

keywords: apps, mobile, mobile app, starter kit, developer tools, DevOps toolchain, toolchain, create mobile app, mobile starter kit

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Creating a mobile app with a starter kit
{: #tutorial-mobile}

{{site.data.keyword.cloud}} offers mobile starter kits to help you create a mobile application quickly. Select a language, framework, and tools from the App Service Starter Kits to start working with a preconfigured custom app. In this tutorial, you can learn how to install the tools you need, build, and run the app locally and deploy it to the cloud.
{: shortdesc}

## Step 1. Before you begin
{: #prereqs-mobile}

Install the [{{site.data.keyword.dev_cli_short}}](/docs/cli?topic=cloud-cli-getting-started).

## Step 2. Create an app by using the {{site.data.keyword.dev_console}}
{: #create-mobile}

1. Create a {{site.data.keyword.dev_console}} app in {{site.data.keyword.cloud_notm}}.
2. From the [Mobile Starter Kits](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon") page in the {{site.data.keyword.dev_console}}, select a starter kit based on the features you want. For example, for a Watson Language app, select **iOS Swift**.
3. Enter your app name. For this tutorial, use `WatsonApp`.
4. Optional. Provide tags to classify your app. For more information, see [Working with tags](/docs/resources?topic=resources-tag).
5. Select your platform. For this tutorial, select **iOS Swift**. Some starter kits might be available in only one language.
6. Select your pricing plan. Use the **Lite** option for this tutorial.
7. Click **Create**.

## Step 3. Add services (Optional)
{: #resources-mobile}

Depending on the starter kit that you selected, some services might already be connected to your app. You can add services that enhance your app with the cognitive power of Watson, add mobile services, or security services. For this tutorial, add a place to manage your data.

1. On the **App details** page, click **Create service**.
2. Select the kind of service you want. For example, select **Databases** > **Next** > **Cloudant** > **Next**.
3. Select your pricing plan. Use the **Lite** option for this tutorial.
4. Click **Create**.

## Step 4. Download the code
{: #mobile-download-code}

To download your app code and work with it locally, complete these steps:

1. On the **App details** page, click **Download code**.
2. Import the app to your integrated development environment.
3. Modify and save the code.

## Step 5. Run your mobile app
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

### Running your Cordova app in Xcode
{: #run_cordova_xcode}

If you are using Cordova as your implementation language, complete these steps:

1. Open the `README.md` file in a Markdown viewer to configure your app.
2. Open your `platforms/ios` app in Xcode.
3. Run your app.

### Running your Cordova app in Android Studio
{: #run_cordova_studio}

If you are using Cordova as your mobile app's platform, complete these steps:

1. Extract the `BasicProject-Cordova.zip` file.
2. Open the `README.md` file in a Markdown viewer to configure your app.
3. Open your `platforms/android` app in Android Studio.
4. Run your app.

### Running your Android app in Android Studio
{: #run_android}

If you are using Android as your mobile app's platform, complete these steps:

1. Open the `README.md` file in a Markdown viewer to configure your app.
2. Open your `BasicProject-Android` app in Android Studio.
3. Run your app.
