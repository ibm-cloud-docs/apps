---

copyright:
  years: 2019
lastupdated: "2019-05-09"

keywords: developer tools, building apps, developer entry point, DevOps, toolchain, insights

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# DevOps Insights
{: #insights-overview}

{{site.data.keyword.DRA_full}} 是一款基于云的解决方案，可通过持续集成和持续交付工具提供全面的洞察，以提高应用程序的速度和质量，增强对应用程序的控制。您可以将 {{site.data.keyword.DRA_short}} 工具集成添加到 DevOps 工具链。
{: shortdesc}

{{site.data.keyword.DRA_short}} 会从单元测试、功能测试和代码覆盖工具收集和分析结果，以确定您的代码是否符合部署过程中指定检测点的预定义条件。如果代码不满足或超出条件，那么会停止部署以防止风险扩散。您可以将 DevOps Insights 用作持续交付环境的安全网，或者作为实施和改进质量标准的方法。

此工具集成仅可用于公共 {{site.data.keyword.cloud_notm}}。它是预配置的，不需要任何配置参数。无法对此工具集成进行重新配置。
{: note}

要将 {{site.data.keyword.DRA_short}} 工具集成添加到 DevOps 工具链，请完成以下步骤：

1. [创建应用程序](/docs/apps?topic=creating-apps-tutorial-getting-started#create-getting-started)。
2. 在“应用程序详细信息”页面上，单击**配置持续交付**，并执行用于配置 DevOps 工具链的步骤。根据所选部署目标的不同，步骤也会有所不同。
3. 在“应用程序详细信息”页面上看到“已配置”消息时，单击**查看工具链**。
4. 在工具链的“概述”页面上，单击**添加工具**。
5. 在“工具集成”部分中，选择 **{{site.data.keyword.DRA_short}}**。
6. 单击**创建集成**。{{site.data.keyword.DRA_short}} 已添加到工具链。
7. 单击 **{{site.data.keyword.DRA_short}}** 磁贴以打开“概述”页面，可在其中开始使用 **{{site.data.keyword.DRA_short}}**。

有关更多信息，请参阅[{{site.data.keyword.DRA_short}}入门教程](/docs/services/DevOpsInsights?topic=DevOpsInsights-getting-started)。
