---

copyright:
  years: 2018
lastupdated: "2018-11-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# 通过您自己的代码存储库创建应用程序
{: #code-repo}

您可以使用现有应用程序存储库在 {{site.data.keyword.cloud}} 中创建应用程序。只需在应用程序创建期间提供存储库的 Web 链接，继续添加资源，然后将 DevOps 工具链连接到要部署的应用程序。
{: shortdesc}

## 开始之前
{: #prereqs}

确保以下先决条件已准备就绪：

 * 安装 [{{site.data.keyword.dev_cli_long}} 命令行界面 (CLI)](/docs/cli/index.html)。
 * 请参阅[优秀应用程序的要素是什么？](/docs/apps/best-practice.html)以获取创建应用程序的最佳实践。
 * 您必须具有来自以下任一提供者的 Git 源代码存储库：GitHub、GitHub Enterprise、GitLab、BitBucket 或 Rational。

## 步骤 1. 使用现有存储库创建应用程序
{: #create}

要创建应用程序并将其与源存储库连接，请完成以下步骤：

1. 在[仪表板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}){: new_window} 中，单击**应用程序**磁贴中的**创建应用程序**。
2. 命名应用程序，然后选择资源组。
3. 选择**自带代码**，然后提供 Git 存储库的 URL。应用程序和 Docker 映像必须位于同一存储库中。
4. 单击**创建**。

这将显示**应用程序详细信息**页面。从其中，您可以：
* [添加资源](/docs/apps/reqnsi.html)（可选）。
* 通过单击**连接到 DevOps 工具链**，将应用程序连接到 DevOps 工具链。如果您还没有工具链，那么将打开**连接 DevOps 工具链**页面。单击**创建 DevOps 工具链**。此时，会在浏览器的新选项卡中打开 [DevOps 仪表板](https://{DomainName}/devops/)中的[创建工具链](https://{DomainName}/devops/create)页面。在该选项卡中创建并配置工具链后，必须返回到应用程序中的**连接工具链**页面，然后刷新该页面。有关更多信息，请参阅[将应用程序连接到新的工具链](#create_toolchain)。
* 通过单击**查看存储库**来查看存储库。
* 通过单击**应用程序详细信息**页面上的任一相关链接，了解有关工具链或应用程序创建体验的更多信息。

## 步骤 2. 将应用程序连接到 DevOps 工具链
{: #connect_toolchain}

在应用程序、工具链和存储库之间建立链接是迈向组织产品资产的一步。此步骤还可帮助集中了解源存储库与 DevOps 工作流程、运行中应用程序实例以及所有部署目标上的相依服务。有关更多信息，请参阅[将应用程序连接到新的工具链](/docs/services/ContinuousDelivery/toolchains_working.html)。

可以使用 {{site.data.keyword.cloud_notm}} 控制台或 CLI 将应用程序连接到 DevOps 工具链。 

### 使用控制台

  1. 通过单击**连接到 DevOps 工具链**，将应用程序连接到 DevOps 工具链。 
  
    如果没有现有工具链，请单击**创建 DevOps 工具链**。 
    
  2. 在创建并配置工具链后，请返回到应用程序中的“连接工具链”页面，然后刷新该页面。 

### 使用 CLI

可以使用 `ibmcloud dev enable` 命令来生成 Devops 工具链模板，您可将该模板检入到存储库中，作为 Devops 工具链要创建的内容的指令集。 

  1. 在 App Service 窗口中，单击**下载代码**或**克隆存储库**以在本地使用代码。
  2. 运行以下命令：
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

有关更多信息，请参阅[使用 CLI 创建和部署应用程序](/docs/apps/create-deploy-cli.html#developing)。

## 步骤 3. 部署应用程序
{: #deploy_app}

将 DevOps 工具链连接到应用程序后，请完成以下步骤以将其部署到 {{site.data.keyword.cloud_notm}}： 

1. 在“应用程序详细信息”页面中，单击**部署到云**。
2. 选择部署方法。 

    * [部署到 Kubernetes 集群](/docs/apps/tutorials/tutorial_byoc_kube.html)。创建一个主机集群（称为工作程序节点）来部署和管理高可用性应用程序容器。您可以创建一个集群，也可以部署到现有集群。
    * 使用 Cloud Foundry 进行部署。此方法不需要管理底层基础架构。
    * 部署到[虚拟服务器实例](/docs/apps/vsi-deploy.html)。


