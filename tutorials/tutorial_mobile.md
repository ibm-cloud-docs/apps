---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-22"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creating a mobile application with a starter kit
{: #tutorial}

You can create a mobile app from a mobile basic starter. You'll see how to install the tools you need, and the steps to run the app in Xcode and Android Studio.
{: shortdesc}

## Install the tools
{: #before-you-begin}

Install the [developer tools](/docs/cli/idt/index.html#create){: new_window}.

## Choose how to create your app
{: #choose_how}

You can create a app by using one of the following methods:
- Web-based [{{site.data.keyword.dev_console}}](#create-devex)
- Local command-driven [{{site.data.keyword.dev_cli_notm}}](#create-cli)

## Creating a app with the {{site.data.keyword.dev_console}}
{: #create-devex}

1. Create a {{site.data.keyword.dev_console}} app in {{site.data.keyword.Bluemix}}.

    1. From the [Starter Kits ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) page in the {{site.data.keyword.dev_console}}, select a Starter Kit based on the capabilities you want. For example, for a Watson Language application, go to **Watson Language** and click **Select Starter Kit**.

    2. Enter your app name. For this tutorial, use `WatsonApp`.   

    3. Select your language platform. For this tutorial, use `Swift`.

    4. Click **Create**.

### Optional: Add services
{: #add-services}

1. Select your app in the **Apps** page.

2. Click **Add Service**.

3. Select the kind of service you want. For this tutorial, select **Security** > **Next** > **App ID** > **Next**.

4. Enter your service name and click **Create**.

5. For more information about configuring authentication, see [Configuring identity providers ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/appid/identity-providers.html){: new_window}.

6. For more information about configuring analytics, see [Getting started with {{site.data.keyword.mobileanalytics_short}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/mobileanalytics/index.html){: new_window}.

7. For more information about configuring {{site.data.keyword.cloudant_short_notm}}, see [Getting started with {{site.data.keyword.cloudant_short_notm}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/Cloudant/index.html){: new_window}.

8. For more information about configuring {{site.data.keyword.objectstorageshort}}, see [Getting started with {{site.data.keyword.objectstorageshort}} ![External link icon](../../icons/launch-glyph.svg "External link icon")](/docs/services/ObjectStorage/index.html){: new_window}.

9. For more information about adding push notifications, see the Push [notifications documentation](/docs/services/mobilepush/c_overview_push.html#overview-push).

### Generate your app code
{: #generate-code}

1. Select your app in the **Apps** page.

2. Click **Download Code** to download your app archive.

### Begin working on your app
{: #code}

Begin working with your downloaded app:

1. Expand the archived file.

2. Navigate to the new app directory.

3. Use the {{site.data.keyword.dev_cli_notm}} to proceed.


## Creating a app with the {{site.data.keyword.dev_cli_notm}}
{: #create-cli}

1. Ensure that you install the [{{site.data.keyword.dev_cli_short}}](/docs/cli/idt/index.html).

2. In your Terminal prompt, navigate to a local directory of your choice and run the following command.

	```
	ibmcloud dev create
	```
	{: codeblock}

3. Provide the following values when prompted:

	* Select a app type of "Mobile Client", option 2
	* Select implementation language to be "iOS Swift", option 3
	* Select starter kit of "Mobile App: Basic", option 1
	* Enter a name for your app: `MobileBasicProject`

    Note: Actual selection numbers may change with tools enhancements.

4. If you want to add services to your app, type `y` at the question prompt and answer the remaining questions.

5. When your `MobileBasicProject` is successfully created and saved, navigate to the `MobileBasicProject/MobileBasicProject-Swift` folder.

### Running your Swift app in Xcode
{: #run_swift}

1. Open the `README.md` file in a markdown viewer to review the steps to configure your app.

2. Open your terminal and navigate to your app folder, and run the following commands:
    1. Run `pod setup` if you need to set up your CocoaPods repository.
    2. Run `pod update` if you need to update you update your existing pods.
    3. Run `pod install` to install the pods for your app.

3. Open your `<appname>.xcworkspace` Xcode workspace.

4. Run your app.

### Running your Cordova app in Xcode
{: #run_cordova_xcode}

If you opted to use Cordova as your implementation language, then follow these instructions.

1. Open the `README.md` file in a Markdown viewer to configure your app.

2. Open your `platforms/ios` app in Xcode.

3. Run your app.

### Running your Cordova app in Android Studio
{: #run_cordova_studio}

Use this section if you chose to use Cordova as your mobile app's platform.

1. Extract the `BasicProject-Cordova.zip` file.

2. Open the `README.md` file in a Markdown viewer to configure your app.

3. Open your `platforms/android` app in Android Studio.

4. Run your app.

### Running your Android app in Android Studio
{: #run_android}

Use this section if you chose to use Android as your mobile app's platform.

1. Open the `README.md` file in a Markdown viewer to configure your app.

2. Open your `BasicProject-Android` app in Android Studio.

3. Run your app.
