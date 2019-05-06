---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-23"

keywords: getting started apps, create app tutorial, add services, deploy apps, create app, app tutorial

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 入门教程
{: #tutorial-getting-started}

在 {{site.data.keyword.cloud}} 中，可以构建企业就绪型移动和 Web 应用程序，并可利用由 {{site.data.keyword.cloud_notm}} 托管的云扩展。您有多个选项可开始此操作。使用用于管理过程的入门模板工具包来创建应用程序；使用所需的资源从头开始构建应用程序（如果您知道自己需要什么）；或者使用现有存储库并自带代码。
{: shortdesc}

无论您是有要进行现代化并移至云的[现有代码](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc)，还是要开发[全新应用程序](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit)，都可以利用 {{site.data.keyword.cloud_notm}} 中快速发展的可用服务和运行时框架生态系统。

是否需要帮助决定从何处开始？请参阅此图以获取构想！

![Developer Experience 概述](images/dev-journey.png "Developer Experience 概述")

## 开始之前
{: #prereqs-getting-started}

您可以使用 {{site.data.keyword.cloud_notm}} 控制台或命令行界面 (CLI) 来创建应用程序。如果要使用 CLI，请参阅[安装步骤](/docs/cli?topic=cloud-cli-ibmcloud-cli)。

## 步骤 1. 创建应用程序
{: #create-getting-started}

通过选择以下其中一个入口点来创建应用程序：

* [入门模板工具包](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit)特定于用例，使用各种编程语言和体系结构模式生成生产就绪型应用程序。
* [IBM Developer 代码模式 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/patterns/){:new_window} 有助于快速创建应用程序，并将其部署到 {{site.data.keyword.cloud_notm}}。有关更多信息，请参阅[代码模式](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern)。
* [自带代码](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc)，方法是链接到您自己的现有内容存储库。应用程序和 Docker 映像必须位于同一存储库中。
* 如果您知道自己需要什么，请通过空白入门模板工具包使用所需服务从头开始构建[定制应用程序](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch)。
* 使用 [CLI 和开发者工具](/docs/apps?topic=creating-apps-create-deploy-app-cli)创建和部署定制或入门模板工具包应用程序。
* 浏览或搜索 [{{site.data.keyword.cloud_notm}} 目录 ](https://{DomainName}/catalog){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")，以查看现在您可以创建并开始使用的应用程序和服务。

## 步骤 2. 添加服务
{: #resources-getting-started}

使用入门模板工具包创建应用程序时，会自动为您创建必需服务。可以在控制台的**应用程序详细信息**页面中将更多服务连接到应用程序，该页面在您创建应用程序时会立即显示。

如果要在创建应用程序后添加服务，请转至 [{{site.data.keyword.cloud_notm}} 仪表板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName})，找到您的应用程序，然后单击应用程序的名称。这将显示**应用程序详细信息**页面，并且您可以创建服务实例或连接现有服务。

或者，使用 CLI 运行以下命令将服务添加到应用程序。您可以从已在帐户上启用的服务中选择现有服务，或添加服务。
```
ibmcloud dev edit
```
{: codeblock}

有关更多信息，请参阅[向应用程序添加服务](/docs/apps?topic=creating-apps-add-resource)。

## 步骤 3. 部署应用程序
{: #deploy-getting-started}

您可以使用控制台或 CLI 来部署应用程序。

### 使用控制台
{: #console-getting-started}

要使用控制台来部署应用程序，请完成以下步骤：

1. 在**应用程序详细信息**页面上，单击**配置持续交付**。
2. 选择部署目标，选择工具链设置，然后单击**创建**。{{site.data.keyword.cloud_notm}} 会自动创建开放工具链，该工具链配套提供 Git 存储库和持续交付管道。
3. 打开新工具链的管道阶段，以查看构建和部署过程，这样您在几分钟后就可以查看新应用程序。

有关更多信息，请参阅目录以查看“部署和集成应用程序”部分中的各种部署主题。

### 使用 CLI
{: #cli-getting-started}

要使用 CLI 来部署应用程序，请运行 `ibmcloud dev deploy` 命令。有关更多信息，请参阅[使用 CLI 创建和部署应用程序](/docs/apps?topic=creating-apps-create-deploy-app-cli)。

现在，您已准备就绪，可进行迭代开发和持续交付。

## 相关信息
{: #related-getting-started}

按语言提供的[编程指南](https://{DomainName}/docs/home/build){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 可帮助您快速入门并熟练运用。通过 {{site.data.keyword.baremetal_short}}，您有多种选项用于通过 {{site.data.keyword.cloud_notm}} 基础架构来托管应用程序，以作为无服务器功能运行。
