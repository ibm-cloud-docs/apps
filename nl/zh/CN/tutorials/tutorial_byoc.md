---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, byoc, code repository, continuous delivery, cli, deploy

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# 通过您自己的代码存储库创建应用程序
{: #tutorial-byoc}

您可以使用现有应用程序存储库在 {{site.data.keyword.cloud}} 中创建应用程序。只需在应用程序创建期间提供存储库的 Web 链接，继续添加资源，然后将 DevOps 工具链连接到要部署的应用程序。
{: shortdesc}

## 开始之前
{: #prereqs-byoc}

确保以下先决条件已准备就绪：

 * 安装 [{{site.data.keyword.dev_cli_long}} 命令行界面 (CLI)](/docs/cli?topic=cloud-cli-ibmcloud-cli)。
 * 请参阅[优秀应用程序的要素是什么？](/docs/apps?topic=creating-apps-best-practice)以获取创建应用程序的最佳实践。
 * 您必须具有来自以下任一提供者的 Git 源代码存储库：GitHub、GitHub Enterprise、GitLab、BitBucket 或 Rational。
 * 如果计划将应用程序部署到 [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about)，那么必须[准备 {{site.data.keyword.cloud_notm}} 帐户](/docs/cloud-foundry?topic=cloud-foundry-prepare)。

## 步骤 1. 使用现有存储库创建应用程序
{: #create-byoc}

要创建应用程序并将其与源存储库连接，请完成以下步骤：

1. 在[仪表板 ](https://{DomainName}){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标") 中，单击**应用程序**磁贴中的**创建应用程序**。
2. 对应用程序命名，选择资源组，并可选择性提供标记以对应用程序分类。有关更多信息，请参阅[使用标记](/docs/resources?topic=resources-tag)。
3. 选择**自带代码**，然后提供 Git 存储库的 URL。应用程序和 Docker 映像必须位于同一存储库中。
4. 单击**创建**。这将显示**应用程序详细信息**页面。
5. 可选。[添加服务](/docs/apps?topic=creating-apps-add-resource)到应用程序。
6. 可选。如果在创建应用程序时提供了标记，那么可以通过单击所显示标记旁边的**编辑**图标 ![“编辑”图标](../../icons/edit-tagging.svg) 对其进行编辑。
7. 可选。通过单击**查看存储库**来查看存储库。

## 步骤 2. 部署应用程序
{: #toolchain-byoc}

在应用程序、工具链和存储库之间建立链接是迈向组织产品资产的一步。此步骤还可帮助集中了解源存储库与 DevOps 工作流程、运行中应用程序实例以及所有部署目标上的相依服务。有关更多信息，请参阅[创建工具链](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)。

可以使用 {{site.data.keyword.cloud_notm}} 控制台或 CLI 为应用程序配置持续交付。

### 使用控制台
{: #console-byoc-toolchain}

  1. 在**应用程序详细信息**页面， 通过单击**配置持续交付**，将应用程序连接到 DevOps 工具链。这将显示**部署应用程序**页面。
  2. 如果没有现存的工具链，请单击**创建工具链**。创建工具链后，使用面包屑返回到**应用程序详细信息**页面，该操作表示已配置持续交付。
  3. 如果已有现存的工具链，请选择它，然后单击**启用部署**。这将显示**应用程序详细信息**页面，该操作表示已配置持续交付。

### 使用 CLI

可以使用 `ibmcloud dev enable` 命令来生成 DevOps 工具链模板，您可将该模板检入到存储库中，作为 DevOps 工具链要创建的内容的指令集。 

  1. 在**应用程序详细信息**页面上，单击**查看存储库**以在本地使用代码。
  2. 运行以下命令：
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

有关更多信息，请参阅[使用 CLI 创建和部署应用程序](/docs/apps?topic=creating-apps-create-deploy-app-cli)。

