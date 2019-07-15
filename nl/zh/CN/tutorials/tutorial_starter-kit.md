---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-20"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# 使用入门模板工具包创建应用程序
{: #tutorial-starterkit}

您可以使用入门模板工具包来快速开始使用应用程序，并为其未来开发做好准备。选择入门模板工具包和编程语言，创建应用程序，然后设置 DevOps 工具链以自动部署应用程序。
{: shortdesc}

可以通过所选的入门模板工具包来创建应用程序，包括基本入门模板工具包（如果您希望自己定制构建选项）。无论采用哪种方法，都会自动创建 DevOps 工具链以用于部署应用程序。此外，还可以下载代码来直接检查您的代码。

{{site.data.keyword.cloud_notm}} 有适用于不同关注领域（如 Watson、安全性或财务）或数字渠道（如移动或 Web 应用程序）的开发者门户网站。可以通过**菜单**图标 ![“菜单”图标](../../icons/icon_hamburger.svg) 来访问这些门户网站。

每个开发者门户网站都提供有与该门户网站的关注领域相关的入门模板工具包。这些门户网站提供一致、直观的工作流程，支持在几分钟内创建有效的生产就绪型应用程序。

入门模板工具包在许多类别中都可用，包括：
* [Watson](https://{DomainName}/developer/watson/dashboard){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")
* [Apple](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")
* [移动](https://{DomainName}/developer/mobile/dashboard){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")
* [Web 应用程序](https://{DomainName}/developer/appservice/dashboard){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")
* [安全性](https://{DomainName}/developer/security/dashboard){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")
* [财务](https://{DomainName}/developer/finance/dashboard){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")

请参阅[什么是入门模板工具包？](/docs/apps?topic=creating-apps-starter-kits) 。


## 步骤 1. 安装工具
{: #prereqs-starterkit}

* 安装 [Developer Tools](/docs/cli?topic=cloud-cli-getting-started)。
* Docker 会作为 Developer Tools 的一部分安装。Docker 必须处于运行中，构建命令才会有效。您必须创建 Docker 帐户，运行 Docker 应用程序，然后登录到该应用程序中。
* 如果计划将应用程序部署到 {{site.data.keyword.cfee_full}}，那么必须[准备 {{site.data.keyword.cloud_notm}} 帐户](/docs/cloud-foundry?topic=cloud-foundry-prepare)。

## 步骤 2. 创建应用程序
{: #create-starterkit}

在 {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}} 中，入门模板工具包有许多语言和框架可用。您可以使用类别过滤器（例如，语言和类型）缩小选择范围。

1. 从 {{site.data.keyword.dev_console}} 控制台上的[入门模板工具包](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标") 页面，选择入门模板工具包，并单击**创建应用程序**。 

    要查看入门模板工具包中所包含的内容，请选择磁贴并阅读详细信息。如果希望使用基本入门模板工具包并定制应用程序，请选择**创建应用程序**磁贴。
    {: tip}

2. 对应用程序命名并选择资源组。

3. 可选。提供标记来对应用程序分类。有关更多信息，请参阅[使用标记](/docs/resources?topic=resources-tag)。

4. 选择语言和框架。某些入门模板工具包可能只有一种语言版本。

5. 单击**创建**。

很好！您刚刚创建了应用程序！

要在添加服务或设置持续交付之前检查您的代码，请单击“应用程序详细信息”页面上的**下载代码**。检查下载的压缩文件中的 `README.md` 文件，以了解是否需要执行更多操作来启动和运行应用程序。
{: tip}

## 步骤 3. 添加服务（可选）
{: #resources-starterkit}

如果入门模板工具包需要特定服务，可以通过自动供应的服务，在创建应用程序时自动创建这些服务的实例。

您可以通过添加服务，利用 Watson 的认知功能来增强应用程序，还可以添加移动服务或安全服务。对于本教程，请添加一个用于管理数据的位置。

1. 在“应用程序详细信息”页面上，单击**创建服务**或**连接现有服务**，具体取决于您是否已经有您希望连接到此应用程序的服务。
2. 选择所需的服务类型，遵循提示以将现有服务添加到应用程序或创建服务实例。

添加所需的所有服务后，它们将显示在“应用程序详细信息”页面中。

## 步骤 4. 选择部署目标并配置持续交付
{: #target-starterkit}

选择部署目标时，会自动为您的应用程序创建 DevOps 工具链。工具链包含指示应用程序部署状态的 Delivery Pipeline。生成的新应用程序将推送到作为工具链一部分的 GitLab 存储库。

启用 DevOp 工具链会为应用程序创建基于团队的开发环境。创建工具链时，App Service 会创建一个 Git 存储库，您可以在其中查看源代码，克隆应用程序以及创建和管理问题。您还有权访问专用的 GitLab 环境和持续交付管道。您可以根据所选的部署目标（[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虚拟服务器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial)）对它们进行定制。

在 {{site.data.keyword.cloud_notm}} 开发者仪表板中创建的所有工具链都会配置为自动部署。
{: note}

要选择部署目标并配置持续交付，请完成以下步骤：

1. 在“应用程序详细信息”页面上，单击**配置持续交付**。
2. 选择部署目标。根据您所选目标的指示信息来设置部署目标：
  * **部署到 [IBM Kubernetes Service](/docs/containers?topic=containers-app)**。此选项将创建一个主机集群（称为工作程序节点）来部署和管理高可用性应用程序容器。您可以创建一个集群，也可以部署到现有集群。
  * **部署到 Cloud Foundry**。此选项可部署云本机应用程序，而无需管理底层基础架构。如果您的帐户有权访问 {{site.data.keyword.cfee_full_notm}}，那么可以选择部署程序类型**[公共云](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)**或**[企业环境](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**，可使用这些类型来创建和管理隔离的环境，以用于专门为您的企业托管 Cloud Foundry 应用程序。
  * **部署到虚拟服务器**。此选项会供应虚拟服务器实例，装入包含您的应用程序的映像，创建 DevOps 工具链，并为您启动第一个部署周期。有关更多信息，请参阅[将应用程序部署到虚拟服务器](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server)。

    VSI 部署可用于某些入门模板工具包。要使用此功能，请转至 [{{site.data.keyword.cloud_notm}} 仪表板](https://{DomainName})，然后单击**应用程序**磁贴中的**创建应用程序**。
    {: note}

选择并配置部署目标后，“应用程序详细信息”页面将指示已配置持续交付。您可以通过单击**查看存储库**来查看包含应用程序的源代码的存储库。

## 步骤 5. 部署应用程序
{: #deploy-starterkit}

在 {{site.data.keyword.cloud_notm}} 开发者仪表板中创建的 DevOps 工具链都会配置为自动部署。
{: note}

选择部署目标后，打开新工具链的管道组件，以开始初始构建和部署过程，这样您在几分钟后就可以看到新应用程序。

1. 在“应用程序详细信息”页面，单击**查看工具链**。
2. 单击 **Delivery Pipeline**，在其中可以启动构建、管理部署以及查看日志和历史记录。

使用正确配置的工具链时，每次合并到存储库中的主分支后，都会自动启动构建/部署周期。有关更多信息，请参阅[构建和部署](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)。

您可以通过从命令行运行 [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) 命令来部署应用程序。有关更多信息，请参阅[使用 CLI 部署应用程序](/docs/apps?topic=creating-apps-deploying-apps#deploy-cli)。

## 步骤 6. 验证应用程序是否正在运行
{: #verify-starterkit}

应用程序部署完成后，Delivery Pipeline 或命令行会指示您前往应用程序的 URL。

1. 在 DevOps 工具链中，单击 **Delivery Pipeline**，然后选择 **Deploy 阶段**。
2. 单击**查看日志和历史记录**。
3. 在日志文件中，查找应用程序的 URL：

    在日志文件末尾，搜索 `urls` 或 `view`。例如，您可能会在日志文件中看到类似于以下内容的行：`urls: my-app-devhost.mybluemix.net` 或 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在浏览器中转至该 URL。如果应用程序正在运行，那么将显示包含 `Congratulations` 或 `{"status":"UP"}` 的消息。

如果使用的是命令行，请运行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 命令来查看应用程序的 URL。然后，在浏览器中转至该 URL。
