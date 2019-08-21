---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-04"

keywords: apps, applications, activity tracking events

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:deprecated: .deprecated}
{:table: .aria-labeledby="caption"}

# {{site.data.keyword.dev_console}} {{site.data.keyword.cloudaccesstrailshort}} 事件
{: #at_events}

作为安全主管、审计员或管理者，您可以使用 {{site.data.keyword.cloudaccesstrailfull}} 服务来跟踪用户和应用程序如何与 {{site.data.keyword.cloud}} 中的 {{site.data.keyword.dev_console}} 交互。
{: shortdesc}

不推荐使用 {{site.data.keyword.cloudaccesstrailfull}}。从 2019 年 5 月 9 日起，您无法供应新的 {{site.data.keyword.cloudaccesstrailshort}} 实例，并且将除去对*轻量*套餐实例的访问权。对现有高端套餐实例的支持将持续到 2019 年 9 月 30 日。要继续监视 {{site.data.keyword.cloud_notm}} 帐户的活动，请供应 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的实例。
{: deprecated}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服务会记录用户启动的活动，这些活动会更改 {{site.data.keyword.cloud_notm}} 中服务的状态。有关更多信息，请参阅[关于 {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov)。

## 在何处查看事件
{: #view-events-ui}

{{site.data.keyword.cloudaccesstrailshort}} 事件位于 {{site.data.keyword.cloudaccesstrailshort}} 帐户域中，而该帐户域位于 {{site.data.keyword.dev_console}} 事件生成所在的 {{site.data.keyword.cloud_notm}} 区域。

要开始监视用户的操作，请参阅[入门教程](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started)。

## 事件列表
{: #events}

下表列出了生成事件的操作：

|操作|描述|
|-----|-------------|
|bluemix-developer-experience.app.create|在用户创建应用程序时生成事件。|
|bluemix-developer-experience.app.read|在发生以下任一情况时生成事件：<br><br>用户下载应用程序代码。<br><br>用户使用 {{site.data.keyword.dev_console}} CLI 下载凭证文件。<br><br>{{site.data.keyword.cloud_notm}} 基础架构读取与应用程序相关联的服务的凭证。<br><br>用户查看应用程序列表。例如，用户在 {{site.data.keyword.dev_console}} 控制台中或通过 {{site.data.keyword.dev_cli_short}} CLI 查看应用程序列表。|
|bluemix-developer-experience.app.update|在发生以下任一情况时生成事件：<br><br>有关应用程序更改的信息。例如，用户修改应用程序的名称。<br><br>创建新服务并将其添加到应用程序中。<br><br>将现有服务添加到应用程序中。<br><br>从应用程序除去服务。<br><br>为应用程序生成代码。<br><br>DevOps 工具链通过 {{site.data.keyword.cloud_notm}} 控制台添加。例如，用户从“应用程序详细信息”页面选择**配置持续交付**。|
|bluemix-developer-experience.app.delete|在用户删除应用程序时生成事件。|
{: caption="表 1. 生成事件的操作" caption-side="top"}
