---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-04"

keywords: apps, credentials, service, add service credentials, environment, deployment

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# 向部署环境手动添加服务凭证
{: #credentials_overview}

您希望应用程序逻辑可从运行应用程序的环境中获取敏感服务凭证，例如数据库 API 密钥或密码。这样，您就不用将凭证保存在源代码存储库中。
{: shortdesc}

如果使用入门模板工具包创建应用程序，那么将自动为您准备环境，在部署应用程序之前将服务连接到入门模板工具包时，服务凭证会自动添加到您的环境。


在以下任一场景中，必须以手动方式将服务凭证添加到部署环境：

 * 自带代码。
 * 在部署了应用程序之后，将服务添加到基于入门模板工具包的应用程序。

添加服务凭证的过程取决于部署目标和编程语言。有关为部署目标配置服务凭证的更多信息，请参阅特定于您的托管环境的文档：

  * [{{site.data.keyword.containerlong}}](/docs/containers?topic=containers-service-binding#adding_app)
  * Cloud Foundry Public 或 {{site.data.keyword.cfee_full}}
  * 虚拟服务器实例（本地 Docker 容器）

许多语言和框架都为特定于应用程序和特定于环境的配置提供标准库。有关更多信息，请参阅以下编程指南：

* [Java：使用服务凭证](/docs/java?topic=cloud-native-configuration)
* [配置 Node.js 环境](/docs/node?topic=nodejs-configure-nodejs)
* [配置 Spring 环境](/docs/java?topic=java-spring-configuration)
* [配置 Swift 环境](/docs/swift?topic=swift-configuration)
* [配置 Go 环境](/docs/go?topic=go-configure-go-env)
