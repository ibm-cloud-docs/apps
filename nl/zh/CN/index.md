---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-04"

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

## 开始之前
{: #prereqs-getting-started}

您可以使用 {{site.data.keyword.cloud_notm}} 控制台或命令行界面 (CLI) 来创建应用程序。如果要使用 CLI，请参阅 [{{site.data.keyword.cloud_notm}} CLI 入门](/docs/cli/index.html#overview)以获取安装详细信息。

## 步骤 1. 创建应用程序
{: #create-getting-started}

通过选择以下其中一个入口点来创建应用程序：
* [入门模板工具包](/docs/apps/tutorials/tutorial_starter-kit.html#tutorial-starterkit)：通过选择的用于管理过程的 App Service 入门模板工具包来创建应用程序。
* [定制](/docs/apps/tutorials/tutorial_scratch.html#tutorial-scratch)：如果您知道自己需要什么，请通过空白入门模板工具包使用所需资源从头开始构建定制应用程序。
* [自带代码](/docs/apps/tutorials/tutorial_byoc.html#tutorial-byoc)：通过链接到您自己的现有内容存储库来使用自己的代码。应用程序和 Docker 映像必须位于同一存储库中。
* [CLI](/docs/apps/create-deploy-cli.html#create-deploy-app-cli)：使用 CLI 和 Developer Tools 来创建和部署定制或入门模板工具包应用程序。
* [代码模式](/docs/apps/tutorials/tutorial_code-pattern.html#tutorial-codepattern)：使用 IBM Developer 代码模式作为创建应用程序的基础。
* [{{site.data.keyword.cloud_notm}} 目录 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://cloud.ibm.com/catalog){: new_window}：可以在目录中浏览或搜索可以创建并立即开始使用的应用程序和服务。

## 步骤 2. 添加资源
{: #resources-getting-started}

使用入门模板工具包创建应用程序时，会自动为您创建资源。您可以通过在控制台的“应用程序详细信息”页面上单击**添加资源**，将更多资源与应用程序相关联。

要使用 CLI 添加资源，请运行以下命令向应用程序添加服务。您可以从已在帐户上启用的服务中选择现有服务，或添加新服务。 
```
ibmcloud dev edit
```
{: codeblock}

有关更多信息，请参阅[向应用程序添加服务](/docs/apps/reqnsi.html#add-resource)。

## 步骤 3. 部署应用程序
{: #deploy-getting-started}

您可以使用控制台或命令行来部署应用程序。

### 使用控制台
{: #console-getting-started}

要使用控制台来部署应用程序，请完成以下步骤：

1. 在**应用程序详细信息**页面上，单击**部署到云**。
2. 选择部署方法，然后单击**创建**。{{site.data.keyword.cloud_notm}} 会自动创建开放工具链，该工具链配套提供 Git 存储库和持续交付管道。
3. 打开新工具链的管道阶段，以查看构建和部署过程，这样您在几分钟后就可以查看新应用程序。

有关更多信息，请参阅目录以查看“部署和集成应用程序”部分中的各种部署主题。

### 使用命令行
{: #cli-getting-started}

要使用命令行来部署应用程序，请运行 `ibmcloud dev deploy` 命令。有关更多信息，请参阅[使用 CLI 创建和部署应用程序](/docs/apps/create-deploy-cli.html#create-deploy-app-cli)。

现在，您已准备就绪，可进行迭代开发和持续交付。
