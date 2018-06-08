---

copyright:
  years: 2018
lastupdated: "2018-05-22"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 建议的云开发阶段
{: #development_process}

云应用程序开发者在开发过程中将经历四个基本阶段：入门、编码、交付和管理。目标是快速生成最小的可行应用程序，然后使用来自生产应用程序的反馈持续对代码或交付周期进行迭代，直至应用程序让用户满意。
{: shortdesc}

![开发流程](images/dev_flow_overview.png "开发流程") 图 1. 开发过程的各阶段

在某些情况下，`运行`将作为单独的阶段进行调用，但此处我们将其与“交付”和“管理”阶段组合在一起。

下面我们来进一步了解在开发流程中使用 {{site.data.keyword.cloud_notm}} 的最佳方式。

##入门
{: #get_started}

在 {{site.data.keyword.cloud_notm}} 开发者仪表板中构建应用程序，在这些仪表板中，可以选择与用例相关的入门模板工具包，然后选择编程语言。{{site.data.keyword.cloud_notm}} 使用入门模板工具包中的指示信息来自动供应所需的资源，并创建特定于语言且与运行时无关的应用程序，以作为生产应用程序的基础。要完成“入门”阶段，请在开发者仪表板中单击**部署到云**。一次单击就可创建 DevOps 工具链，并配套提供使用应用程序源代码和部署管道填充的代码存储库。

![入门](images/dev_get_started.png "入门") 图 2.“入门”流程

使用**部署到云**按钮来设置 DevOps 工具链时，请选择运行时平台，例如 Kubernetes 或 Cloud Foundry。通过 {{site.data.keyword.cloud_notm}} 生成的入门模板应用程序与运行时无关，无需进行修改。
{: tip}

##本地开发
{: #develop_locally}

创建入门模板应用程序和工具链后，可以在本地开始进行开发。将存储库中的代码克隆到本地工作站，然后导入到 IDE 中。使用 {{site.data.keyword.dev_cli_notm}} 在本地机器上构建、运行和测试云应用程序。{{site.data.keyword.dev_cli_notm}} 会为您创建和管理本地容器。当您准备好使应用程序在云上运行时，请将其推送到云存储库并合并更改。

![本地开发](images/dev_code_locally.png "本地开发") 图 3.“本地开发”流程

{{site.data.keyword.dev_cli_notm}} 的基本功能为 `ibmcloud dev build` 和 `ibmcloud dev run`，但该 CLI 还提供了更多功能。有关更多详细信息，请参阅 [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html)。
{: tip}

##在 {{site.data.keyword.cloud_notm}} 中交付和管理
{: #deliver_and_manage}

将更改合并到云存储库会启动先前创建的 DevOps 工具链中的构建和部署周期。几分钟后，应用程序就会在云中运行。

要检查 DevOps 管道的状态，请使用 Delivery Pipeline 仪表板。要检查应用程序的总体状态，请查看您帐户的 {{site.data.keyword.cloud_notm}} 仪表板。
{: tip}

由入门体验生成的工具链包含您进行基于团队的协作式持续交付所需的基本组件。不过，{{site.data.keyword.cloud_notm}} 提供了一组丰富的 DevOps 服务，您可以将这些服务添加到工具链中，以增强交付、监视、日志记录和警报功能。

![交付和管理](images/dev_deliver_and_manage.png "交付和管理") 图 4.“交付和管理”流程

了解有关[在 {{site.data.keyword.cloud_notm}} 上持续开发](../services/ContinuousDelivery/index.html#cd_getting_started)的更多信息。

## 化零为整

![过程详细信息](images/dev_process_detail.png "过程详细信息") 图 5. 端到端开发过程
