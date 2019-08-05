---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-29"

keywords: apps, serverless, serverless app, functions, cli, api, sdk, create serverless app, serverless app tutorial

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 创建无服务器应用程序
{: #serverless}

对于无服务器开发，您可以使用 {{site.data.keyword.openwhisk}}，这是 IBM 函数即服务 (FaaS) 产品。您可以使用 {{site.data.keyword.openwhisk_short}} 运行应用程序逻辑来响应通过 HTTP 从 Web 或移动应用程序发出的事件或直接调用，而无需供应或管理服务器。{{site.data.keyword.openwhisk_short}} 执行系统管理，如自动缩放、可用性管理和维护，以便您作为开发者可以专注于编写应用程序逻辑。
{:shortdesc}

可以使用以下两种方法之一来开发无服务器应用程序：
* {{site.data.keyword.openwhisk_short}} 用户界面 (UI)。
* {{site.data.keyword.openwhisk_short}} 命令行界面 (CLI)，用于提供对部署和操作的更多控制权。
* {{site.data.keyword.openwhisk_short}} 入门模板工具包，可在其中使用 DevOps 工具链和 Delivery Pipeline 配置持续交付。

有关 {{site.data.keyword.openwhisk_short}} 的更详细信息，请查看[文档](/docs/openwhisk?topic=cloud-functions-getting_started)。


## 使用 {{site.data.keyword.openwhisk_short}} UI 进行开发
{: #serverless-apps-ui}

在[浏览器](https://{DomainName}/functions/actions){: new_window}中试用 {{site.data.keyword.openwhisk_short}} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")。转至[概念 ](https://{DomainName}/functions/learn){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 页面，以快速导览 {{site.data.keyword.openwhisk_short}} 用户界面。

## 使用 CLI 进行开发
{: #openwhisk_start_configure_cli}

要了解有关使用 {{site.data.keyword.openwhisk_short}} CLI 进行安装和开发的更多信息，请[设置 {{site.data.keyword.openwhisk_short}} CLI ](https://{DomainName}/functions/cli){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")。

## 将 API 和数据集公开为 Web 操作
{: #expose-actions}

缺省情况下，{{site.data.keyword.openwhisk_short}} 定义需要认证密钥的操作。在生产移动环境中，通常需要基于 OAuth 流授权移动式客户机来公开 API 和特定数据集。

通过 {{site.data.keyword.openwhisk_short}}，开发者能够将自己的功能公开为带注释的 Web 操作，以快速构建基于 Web 的应用程序。您可以使用 Web 应用程序可匿名访问的带注释操作对后端逻辑进行编程，而无需 {{site.data.keyword.openwhisk_short}} 认证密钥。

要将操作公开为 Web 操作，请转至操作的**端点**选项卡，然后选择**作为 Web 操作启用**。

现在，用户可以通过浏览器或 cURL 请求来访问操作，例如：
```
curl https://openwhisk.cloud.ibm.com/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

输出：
```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} 为 iOS 和 watchOS 设备提供[移动 SDK](/docs/openwhisk?topic=cloud-functions-pkg_mobile_sdk)，支持移动应用程序轻松发送远程触发器和调用远程操作。

## 使用入门模板工具包创建无服务器应用程序
{: #serverless-starter}

您可以使用入门模板工具包来创建无服务器应用程序，如 Python Example Serverless App。要找到入门模板工具包，请完成以下步骤：

1. 转至 {{site.data.keyword.dev_console}} 控制台中的[应用程序服务入门模板工具包](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 页面。
2. 在搜索栏中输入 `serverless` 以过滤入门模板工具包的列表。
3. 选择一个无服务器入门模板工具包，如 Python Example Serverless App。
4. 对应用程序命名并选择资源组。
5. 可选。提供标记来对应用程序分类。有关更多信息，请参阅[使用标记](/docs/resources?topic=resources-tag)。
6. 创建新的或选择现有的 Cloudant 服务实例。
7. 可选。要在添加更多服务或部署应用程序之前检查您的代码，请单击**查看源代码**。查看 `README.md` 文件，以了解是否需要执行更多操作来启动和运行应用程序。
  
8. 单击**创建**。

很好！您刚刚创建了应用程序！

## 添加服务（可选）
{: #serverless-services}

如果入门模板工具包需要特定服务，可以通过自动供应的服务，在创建应用程序时自动创建这些服务的实例。

1. 在“应用程序详细信息”页面上，单击**创建服务**或**连接现有服务**，具体取决于您是否已经有您希望连接到此应用程序的服务。
2. 选择所需的服务类型，遵循提示以将现有服务添加到应用程序或创建服务实例。

添加所需的所有服务后，这些服务将显示在“应用程序详细信息”页面中。

## 部署应用程序
{: #serverless-deploy}

要部署应用程序，请完成以下步骤：

1. 在“应用程序详细信息”页面上，单击**部署**。
2. 选择**部署到 Cloud Functions**，然后单击**下一步**。
3. 在“配置工具链”页面上，输入工具链名称，选择区域，然后单击**创建**。选择并配置部署目标后，“应用程序详细信息”页面将指示已配置持续交付。
4. 可选。在 {{site.data.keyword.openwhisk_short}} 控制台中通过单击“操作”图标 ![“更多操作”图标](../icons/action-menu-icon.svg) 并选择**打开 Cloud Functions** 来复查操作。
5. 可选。通过单击**查看存储库**来查看包含为应用程序和服务生成的代码的存储库。

## 验证应用程序是否已部署
{: #serverless-verify}

使用正确配置的工具链时，每次合并到存储库中的主分支后，都会自动启动构建/部署周期。有关更多信息，请参阅[构建和部署](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)。

要验证应用程序是否已成功部署，请完成以下步骤：

1. 在“应用程序详细信息”页面，单击**查看工具链**。
2. 单击 **Delivery Pipeline**，在其中可以启动构建、管理部署以及查看日志和历史记录。
3. 如果部署成功，每个管道阶段会指示**阶段已通过**。
4. 要查看操作和 API 信息，请单击**部署阶段**磁贴中的**查看日志和历史记录**。
