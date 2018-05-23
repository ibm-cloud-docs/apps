---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-02"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用初学者工具包创建移动应用程序
{: #tutorial}

您可以通过移动基本入门模板来创建移动应用程序。您将了解如何安装所需的工具，以及在 Xcode 和 Android Studio 中运行应用程序的步骤。
{: shortdesc}

## 安装工具
{: #before-you-begin}

安装 [Developer Tools](/docs/cli/idt/index.html#create){: new_window}。

## 选择应用程序创建方式
{: #choose_how}

可以使用以下其中一种方法来创建应用程序：
- 基于 Web 的 [{{site.data.keyword.dev_console}}](#create-devex)
- 本地命令驱动的 [{{site.data.keyword.dev_cli_notm}}](#create-cli)

## 使用 {{site.data.keyword.dev_console}} 创建应用程序
{: #create-devex}

1. 在 {{site.data.keyword.Bluemix}} 中创建 {{site.data.keyword.dev_console}} 应用程序。

    1. 在 {{site.data.keyword.dev_console}} 中的[初学者工具包 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) 页面中，根据您需要的功能来选择初学者工具包。例如，对于 Watson Language 应用程序，请转至 **Watson Language**，然后单击**选择初学者工具包**。

    2. 输入应用程序名称。对于本教程，请使用 `WatsonApp`。   

    3. 选择语言平台。对于本教程，请使用 `Swift`。

    4. 单击**创建**。

### 可选：添加服务
{: #add-services}

1. 在**应用程序**页面中选择您的应用程序。

2. 单击**添加服务**。

3. 选择所需的服务类型。对于本教程，请选择**安全性** > **下一步** > **App ID** > **下一步**。

4. 输入服务名称，然后单击**创建**。

5. 有关配置认证的更多信息，请参阅[配置身份提供者 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/appid/identity-providers.html){: new_window}。

6. 有关配置分析的更多信息，请参阅 [{{site.data.keyword.mobileanalytics_short}} 入门 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/mobileanalytics/index.html){: new_window}。

7. 有关配置 {{site.data.keyword.cloudant_short_notm}} 的更多信息，请参阅 [{{site.data.keyword.cloudant_short_notm}} 入门 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/Cloudant/index.html){: new_window}。

8. 有关配置 {{site.data.keyword.objectstorageshort}} 的更多信息，请参阅 [{{site.data.keyword.objectstorageshort}} 入门 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](/docs/services/ObjectStorage/index.html){: new_window}。

9. 有关添加推送通知的更多信息，请参阅 [Push Notifications 文档](/docs/services/mobilepush/c_overview_push.html#overview-push)。

### 生成应用程序代码
{: #generate-code}

1. 在**应用程序**页面中选择您的应用程序。

2. 单击**下载代码**以下载应用程序归档文件。

### 开始使用应用程序
{: #code}

开始使用下载的应用程序：

1. 解压缩归档文件。

2. 浏览到新应用程序目录。

3. 使用 {{site.data.keyword.dev_cli_notm}} 以继续。


## 使用 {{site.data.keyword.dev_cli_notm}} 创建应用程序
{: #create-cli}

1. 确保安装 [{{site.data.keyword.dev_cli_short}}](/docs/cli/idt/index.html)。

2. 在终端提示符中，导航至所选的本地目录，并运行以下命令。

	```
	bx dev create
	```
	{: codeblock}

3. 系统提示时，提供以下值：

	* 对于应用程序类型，选择“移动式客户机”（选项 2）
	* 对于实现语言，选择“iOS Swift”（选项 3）
	* 对于初学者工具包，选择“移动应用程序：基本”（选项 1）
	* 输入应用程序的名称：`MobileBasicProject`

    注：实际的选择编号可能会随着工具增强而更改。

4. 如果要向应用程序添加服务，请在问题提示处输入 `y` 并回答其余问题。

5. 成功创建并保存 `MobileBasicProject` 后，导航至 `MobileBasicProject/MobileBasicProject-Swift` 文件夹。

### 在 Xcode 中运行 Swift 应用程序
{: #run_swift}

1. 在 Markdown 查看器中打开 `README.md` 文件，以查看用于配置应用程序的步骤。

2. 打开终端并浏览到应用程序文件夹，然后运行以下命令：
    1. 如果需要设置 CocoaPods 存储库，请运行 `pod setup`。
    2. 如果需要更新现有 pod，请运行 `pod update`。
    3. 运行 `pod install`，为应用程序安装 pod。

3. 打开 `<appname>.xcworkspace` Xcode 工作空间。

4. 运行应用程序。

### 在 Xcode 中运行 Cordova 应用程序
{: #run_cordova_xcode}

如果选择使用 Cordova 作为实现语言，请遵循以下指示信息进行操作。

1. 在 Markdown 查看器中打开 `README.md` 文件以配置应用程序。

2. 在 Xcode 中打开 `platforms/ios` 应用程序。

3. 运行应用程序。

### 在 Android Studio 中运行 Cordova 应用程序
{: #run_cordova_studio}

如果选择使用 Cordova 作为移动应用程序的平台，请使用此部分。

1. 解压缩 `BasicProfile-Cordova.zip` 文件。

2. 在 Markdown 查看器中打开 `README.md` 文件以配置应用程序。

3. 在 Android Studio 中打开 `platforms/android` 应用程序。

4. 运行应用程序。

### 在 Android Studio 中运行 Android 应用程序
{: #run_android}

如果选择使用 Android 作为移动应用程序的平台，请使用此部分。

1. 在 Markdown 查看器中打开 `README.md` 文件以配置应用程序。

2. 在 Android Studio 中打开 `BasicProject-Android` 应用程序。

3. 运行应用程序。
