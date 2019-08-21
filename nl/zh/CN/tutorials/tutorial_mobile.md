---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-17"

keywords: apps, mobile, mobile app, starter kit, developer tools, devops toolchain, toolchain, create mobile app, mobile starter kit, android, ios, swift, xcode

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 创建移动应用程序
{: #tutorial-mobile}

{{site.data.keyword.cloud}} 提供了移动入门模板工具包，可帮助您快速创建移动应用程序。从移动入门模板工具包中选择语言、框架和工具，以开始使用预配置的应用程序。或者，您可以使用基本入门模板工具包来创建定制移动应用程序。
{: shortdesc}

## 开始之前
{: #prereqs-mobile}

安装 [{{site.data.keyword.dev_cli_long}} 命令行界面 (CLI)](/docs/cli?topic=cloud-cli-getting-started)。

## 使用入门模板工具包创建移动应用程序
{: #create-mobile}

要使用入门模板工具包创建移动应用程序，请完成以下步骤：

1. 在 {{site.data.keyword.dev_console}} 中的[移动入门模板工具包](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标") 页面中，根据您需要的功能来选择入门模板工具包。例如，选择 **Watson Visual Recognition**。
2. 输入应用程序名称。对于本教程，请使用 `WatsonApp`。
3. 可选。提供标记来对应用程序分类。有关更多信息，请参阅[使用标记](/docs/resources?topic=resources-tag)。
4. 选择平台。对于本教程，请选择 **iOS Swift**。某些入门模板工具包可能只有一种语言版本。
5. 选择价格套餐。对于本教程，请使用**轻量**选项。如果需要任何服务，那么会在入门模板工具包中自动定义这些服务。
6. 单击**创建**。

## 创建定制移动应用程序
{: #create-mobile-basic}

要创建定制移动应用程序，请完成以下步骤：

1. 在 {{site.data.keyword.dev_console}} 中的[移动入门模板工具包](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标") 页面中，选择**创建应用程序**磁贴。
2. 输入应用程序的名称。对于本教程，请输入 `CustomMobile`。
3. 可以选择性提供标记来对应用程序分类。有关更多信息，请参阅[使用标记](/docs/resources?topic=resources-tag)。
4. 选择**创建新应用程序**作为起始点。
5. 选择**移动**作为应用程序类型。
6. 选择语言和框架。某些入门模板工具包可能只有一种语言版本。
7. 选择价格套餐。对于本教程，您可以使用免费选项。
8. 单击**创建**。

## 使用 CLI 创建移动应用程序
{: #create-mobile-cli}

要使用 [{{site.data.keyword.dev_cli_long}} CLI](/docs/cli?topic=cloud-cli-getting-started) 创建移动应用程序，请完成以下步骤：

1. 打开终端并导航至要在其中创建应用程序的目录。
2. 运行 `ibmcloud dev create` 命令。
3. 从应用程序类型列表中选择**移动应用程序**选项。
4. 从列表中选择移动平台：Android 或 Swift。
5. 选择入门模板工具包。
6. 输入应用程序的名称。
7. 如果已添加服务，那么系统将提示您为每个服务选择区域和价格套餐。

这将在当前工作目录中创建应用程序。

## 添加服务（可选）
{: #resources-mobile}

根据您选择的入门模板工具包，某些服务可能已连接到应用程序。您可以通过添加服务，利用 Watson 的认知功能来增强应用程序，还可以添加移动服务或安全服务。对于本教程，请添加一个用于管理数据的位置。

要将服务添加到应用程序中，请完成以下步骤：

1. 在**应用程序详细信息**页面上，单击**创建服务**。
2. 选择所需的服务类型。例如，选择**数据库** > **下一步** > **Cloudant** > **下一步**。
3. 选择价格套餐。对于本教程，请使用**轻量**选项。
4. 单击**创建**。

## 下载代码
{: #mobile-download-code}

要下载应用程序代码并在本地使用，请完成以下步骤：

1. 在**应用程序详细信息**页面上，单击**下载代码**。
2. 将应用程序导入到集成开发环境中。
3. 修改并保存代码。

## 运行移动应用程序
{: #run-mobile-app}

### 在 Xcode 中运行 Swift 应用程序
{: #run_swift}

如果您使用 iOS Swift 作为实现语言，请完成以下步骤：

1. 在 Markdown 查看器中打开 `README.md` 文件，以查看用于配置应用程序的步骤。
2. 打开终端并浏览到应用程序文件夹，然后运行以下命令：
    1. 如果需要设置 CocoaPods 存储库，请运行 `pod setup`。
    2. 如果需要更新现有 pod，请运行 `pod update`。
    3. 运行 `pod install`，为应用程序安装 pod。
3. 打开 `<appname>.xcworkspace` Xcode 工作空间。
4. 运行应用程序。

### 在 Android Studio 中运行 Android 应用程序
{: #run_android}

如果您使用 Android 作为移动应用程序的平台，请完成以下步骤：

1. 在 Markdown 查看器中打开 `README.md` 文件以配置应用程序。
2. 在 Android Studio 中打开 `BasicProject-Android` 应用程序。
3. 运行应用程序。

## 相关信息
{: #related-mobile}

您可以通过探索以下教程来了解有关移动应用程序的更多信息：

 * [使用 Push Notifications 的 iOS 移动应用程序](/docs/tutorials?topic=solution-tutorials-ios-mobile-push-analytics)
 * [使用 Push Notifications 的 Android 本机移动应用程序](/docs/tutorials?topic=solution-tutorials-android-mobile-push-analytics)
 * [使用无服务器后端的移动应用程序](/docs/tutorials?topic=solution-tutorials-serverless-mobile-backend)
