---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-15"

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
{:table: .aria-labeledby="caption"}

# {{site.data.keyword.dev_console}} {{site.data.keyword.cloudaccesstrailshort}} 事件
{: #at_events}

作为安全主管、审计员或管理者，您可以使用 {{site.data.keyword.cloudaccesstrailfull}} 服务来跟踪用户和应用程序如何与 {{site.data.keyword.cloud}} 中的 {{site.data.keyword.dev_console}} 交互。
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服务会记录用户启动的活动，这些活动会更改 {{site.data.keyword.cloud_notm}} 中服务的状态。有关更多信息，请参阅[关于 {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov)。

## 在何处查看事件
{: #view-events-ui}

{{site.data.keyword.cloudaccesstrailshort}} 事件位于 {{site.data.keyword.cloudaccesstrailshort}} 帐户域中，而该帐户域位于 {{site.data.keyword.dev_console}} 事件生成所在的 {{site.data.keyword.cloud_notm}} 区域。

要开始监视用户的操作，请参阅[入门教程](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started)。

## 事件列表
{: #events}

下表列出了生成事件的操作：

<table>
  <caption>生成事件的操作</caption>
  <tr>
    <th>操作</th>
	  <th>描述
</th>
  <tr>
  <tr>
    <td>bluemix-developer-experience.app.create</td>
	  <td>在用户创建应用程序时生成事件。</td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.read</td>
	  <td>在发生以下任一情况时生成事件：</br><ul><li>用户下载应用程序代码。</li> <li>用户使用 {{site.data.keyword.dev_console}} CLI 下载凭证文件。</li> <li>开发者体验基础架构读取与应用程序相关联的资源的凭证。</li> <li>用户查看应用程序列表。例如，用户在 {{site.data.keyword.dev_console}} 控制台中或通过 {{site.data.keyword.dev_cli_short}} CLI 查看应用程序列表时。</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.update</td>
	  <td>在发生以下任一情况时生成事件：</br><ul><li>应用程序的某个属性发生更改。例如，用户修改应用程序的名称时。</li><li>创建新资源并将其添加到应用程序中。</li><li>将现有资源添加到应用程序中。</li><li>从应用程序除去服务。</li><li>为应用程序生成代码。</li><li>通过开发者体验添加 DevOps 工具链，例如通过选择*部署到云*。</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.delete</td>
	  <td>在用户删除应用程序时生成事件。</td>
  </tr>
</table>
