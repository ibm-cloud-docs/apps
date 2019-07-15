---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-03"

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

对于无服务器开发，您可以使用 IBM 的函数即服务 (FaaS) 产品 {{site.data.keyword.openwhisk}}。您可以使用 {{site.data.keyword.openwhisk_short}} 运行应用程序逻辑，以响应通过 HTTP 从 Web 或移动应用程序发出的事件或直接调用，而无需供应或管理服务器。{{site.data.keyword.openwhisk_short}} 可执行系统管理，如自动缩放、可用性管理和维护，以便您作为开发者可以专注于编写应用程序逻辑。
{:shortdesc}

您可以使用 {{site.data.keyword.openwhisk_short}} 用户界面 (UI) 或命令行界面 (CLI) 来开发应用程序。这两个界面具有类似的应用程序开发功能。CLI 提供了对部署和操作的更多控制权。有关 {{site.data.keyword.openwhisk_short}} 的更详细信息，请查看[文档](/docs/openwhisk?topic=cloud-functions-getting_started)。

## {{site.data.keyword.openwhisk_short}} UI
{: #serverless-apps-ui}

在[浏览器](https://{DomainName}/openwhisk/actions){: new_window}中试用 {{site.data.keyword.openwhisk_short}} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")。转至[概念 ](https://{DomainName}/openwhisk/learn){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 页面，以快速导览 {{site.data.keyword.openwhisk_short}} 用户界面。

## 使用 CLI 进行开发
{: #openwhisk_start_configure_cli}

要了解有关使用 {{site.data.keyword.openwhisk_short}} CLI 进行安装和开发的更多信息，请[设置 {{site.data.keyword.openwhisk_short}} CLI ](https://{DomainName}/openwhisk/cli){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")。

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

{{site.data.keyword.openwhisk_short}} 为 iOS 和 watchOS 设备提供[移动 SDK](/docs/openwhisk?topic=cloud-functions-openwhisk_mobile_sdk)，支持移动应用程序轻松发送远程触发器和调用远程操作。
