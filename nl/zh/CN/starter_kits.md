---

copyright:
  years: 2018
lastupdated: "2018-07-05"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 应用程序开发
{: #intro}

{{site.data.keyword.cloud_notm}} 开发者控制台可帮助开发者通过入门模板工具包创建应用程序，供应并连接 {{site.data.keyword.cloud_notm}} 优化的关键服务，然后快速下载工作代码，或设置进行持续交付。您可以创建、查看、配置和管理应用程序，并下载应用程序的代码。使用入门模板工具包可帮助您使用样本应用程序来快速评估和测试 {{site.data.keyword.cloud_notm}} 服务。
{:shortdesc}

## 什么是入门模板工具包？
{: #starter_kits}

入门模板工具包非常适合按您选择的语言来动态组合框架生产应用程序，以准备好进行云部署。每个入门模板工具包中都具有针对特定现实世界用例的语言、框架和模式。您可以复用代码，而不用重新创建代码。

### 比较样本和入门模板工具包

开发者通常依赖于预先编写的代码，例如片段、演示和样本。那么片段、演示、样本和 {{site.data.keyword.cloud_notm}} 入门模板工具包有何区别呢？

* **片段** - 通常在 IDE 中显示的一些代码行。片段可帮助开发者与编程语言语法集成，或支持与定义的 API 集成。

* **演示** - 通常质量和精确度较高，并且会使用一系列服务和集成点的代码。演示通常需要进行设置，并用于证明业务问题或演示平台功能。演示可以评估采用云的阶段。有时，演示代码会包含在生产代码中。

* **样本** - 由特定特征、功能、服务或用户旅程组成的小型示例代码。样本可以复用于或包含在生产应用程序中。可以使用样本来展示技术能力以及解决技术问题的可行方法。

* **{{site.data.keyword.cloud_notm}} 入门模板工具包** - 入门模板工具包是生产就绪型模式，可与一组服务集成以生成生产就绪型资产。然后，可以将这些资产直接部署到 DevOps 管道和 Kubernetes 集群。入门模板工具包具有描述性元数据，为您提供了足够的信息来了解该工具包的功能和用途。另外还有指示 {{site.data.keyword.cloud_notm}} 生成哪些内容的指示信息。输出可以进一步增强。入门模板工具包的内容不像演示那么复杂，也不像片段或样本那么简单。入门模板工具包是根据您的需求动态创建的。

  入门模板工具包显示了通过运行时（例如，Swift 和 Kitura）进行的主要模式实现。初学者工具包可以包含简单的用户体验，以着重强调服务的集成。入门模板工具包是复杂用例的可定制实现。

  入门模板工具包包含允许 {{site.data.keyword.cloud_notm}} 使用可移植代码来自动生成搭建有脚手架的应用程序项目的指示信息。此外，还指定在创建项目时要自动供应的资源。

## 自动供应的资源
{: #auto_privisioned_resources}

如果入门模板工具包指定了所需资源，那么在创建项目时，{{site.data.keyword.cloud_notm}} 会自动创建这些资源的实例。创建项目后，可以向项目手动供应资源或选择现有资源实例以扩充项目。您可以在*项目详细信息*视图中查看与项目关联的服务实例列表，还可在需要时在其中查看凭证。

## 生成可移植代码
{: #portable_code}

通过入门模板工具包创建应用程序会自动生成与运行时无关的统一格式代码。您可以将代码原封不动地部署到所选环境中，例如 Kubernetes 或 Cloud Foundry。

项目包含一个 `README` 文件，其中包含项目的技术详细信息，并说明了需要什么来使应用程序准备好运行。

有关更多信息，请参阅 [{{site.data.keyword.cloud_notm}} 开发者控制台中的 Apple 学习资源](https://console.bluemix.net/developer/appledevelopment/learning-resources)。
{: tip}

### 生成的应用程序内容是什么？
{: #content}

{{site.data.keyword.cloud_notm}} 入门模板工具包生成的代码有四个基本组成部分：用例逻辑、语言组成部分、服务支持和云支持。生成这些组成部分可节省您宝贵的时间，并确保使用的是同类中最佳的体系结构。

* **用例逻辑**是特定用例的代码。例如，Watson Conversation 聊天机器人的代码或移动直观识别应用程序的代码。
* **语言组成部分**是特定于为入门模板工具包所选择语言的代码组成部分和文件。例如，Node.js 程序员需要 `package.json` 文件进行依赖关系管理，此文件由 {{site.data.keyword.cloud_notm}} Developer Experience 自动创建。
* **服务支持**是允许应用程序连接项目并使用向项目添加的服务的代码。服务支持项的示例为凭证管理、初始化代码和特定于服务的 SDK。
* **云支持**是支持应用程序在 {{site.data.keyword.cloud_notm}} 上运行的代码。例如，允许应用程序在 {{site.data.keyword.cloud_notm}} Kubernetes 集群上运行的 Helm 图表就属于云支持类别。

{{site.data.keyword.cloud_notm}} 生成的应用程序不仅在体系结构上成熟可靠，还针对为项目所选语言建立了最佳实践模型。要查看有关应用程序项目的文件和结构的详细信息，请参阅以下主题。

* [Java 应用程序文件](/docs/apps/projects/java_project_contents.html)
* [Node.js 应用程序文件](/docs/apps/projects/node_project_contents.html)
* [Python 应用程序文件](/docs/apps/projects/python_project_contents.html)
* [Swift 应用程序文件](/docs/apps/projects/swift_project_contents.html)。
