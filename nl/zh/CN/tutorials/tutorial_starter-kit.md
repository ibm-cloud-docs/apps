---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-30"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 使用入门模板工具包创建应用程序
{: #tutorial-starterkit}

您可以使用入门模板工具包来快速开始使用应用程序，并为其未来开发做好准备。选择入门模板工具包和编程语言，创建应用程序，然后设置 DevOps 工具链以自动部署应用程序。此外，还可以下载代码来直接检查您的代码。
{: shortdesc}

可以通过所选的入门模板工具包来创建应用程序，包括空白应用程序（如果您希望自己定制构建选项）。无论采用哪种方法，都会自动创建 DevOps 工具链以用于部署应用程序。此外，还可以下载代码来直接检查您的代码。

{{site.data.keyword.cloud_notm}} 有适用于不同关注领域（如 Watson、安全性或财务）或数字渠道（如移动或 Web 应用程序）的开发者门户网站。可以通过**菜单**图标 ![“菜单”图标](../../icons/icon_hamburger.svg) 来访问这些门户网站。

每个开发者门户网站都提供有与该门户网站的关注领域相关的入门模板工具包。这些门户网站提供一致、直观的工作流程，支持在几分钟内创建有效的生产就绪型应用程序。

入门模板工具包在许多类别中都可用，包括：
* [Watson](https://{DomainName}/developer/watson/dashboard){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")
* [Apple](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")
* [移动](https://{DomainName}/developer/mobile/dashboard){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")
* [Web 应用程序](https://{DomainName}/developer/appservice/dashboard){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")
* [安全性](https://{DomainName}/developer/security/dashboard){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")
* [财务](https://{DomainName}/developer/finance/dashboard){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")

[了解更多](/docs/apps?topic=creating-apps-starter-kits)有关入门模板工具包的信息。

## 步骤 1. 创建应用程序
{: #create-starterkit}

1. 在 [{{site.data.keyword.cloud}} 仪表板](https://{DomainName}){: new_window} ![外部链接图](../../icons/launch-glyph.svg "外部链接图标") 中，单击**菜单**图标 ![“菜单”图标](../../icons/icon_hamburger.svg) > **Web 应用程序**。

2. 单击**从 Web 开始**部分中的**开始**。

3. 选择您想要的入门模板工具包，阅读详细信息，然后单击**创建**。
    
    要查看入门模板工具包中所包含的内容，请展开 [App Service 入门模板工具包 ](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标") 仪表板上的磁贴。“创建应用程序”入门模板工具包选项可用作空白入门模板应用程序，并可根据需要进一步定制。
    {: tip}

4. 对应用程序命名，选择资源组，选择性提供标记，选择语言，然后单击**创建**。
    
    很好！您刚刚创建了应用程序。

要检查您的代码，请单击**应用程序详细信息**页面上的**下载代码**。检查下载的压缩文件中的 `README.md` 文件，以了解是否需要执行更多操作来启动和运行入门模板应用程序。
{: tip}

有关更多信息，请参阅以下主题：
 * [使用入门模板工具包创建基本 Web 应用程序](/docs/apps/tutorials?topic=creating-apps-tutorial-webapp)
 * [使用标记](/docs/resources?topic=resources-tag)

## 步骤 2. 添加服务
{: #resources-starterkit}

您可以通过添加服务，利用 Watson 的认知功能来增强应用程序，还可以添加移动服务或安全服务。对于本教程，请添加一个用于管理数据的位置。

1. 在**应用程序详细信息**页面上，单击**添加服务**。
2. 选择所需的服务类型。例如，选择**数据** > **下一步** > **Cloudant** > **下一步**。
3. 选择价格套餐。对于本教程，可以使用免费选项。
4. 单击**创建**。

## 步骤 3. 部署到 {{site.data.keyword.cloud_notm}}
{: #deploy-starterkit}

单击**应用程序详细信息**页面上的**配置持续交付**，选择部署目标，然后单击**创建**。{{site.data.keyword.cloud_notm}} 会自动创建开放工具链，该工具链配套提供 Git 存储库和持续交付管道。

启用工具链会为应用程序创建基于团队的开发环境。创建工具链时，App Service 会创建一个 Git 存储库，您可以在其中查看源代码，克隆应用程序以及创建和管理问题。您还有权访问专用的 GitLab 环境和持续交付管道。您可以根据所选的部署目标（[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虚拟服务器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers)）对它们进行定制。

选择部署目标后，打开新工具链的管道组件，以开始初始构建和部署过程，这样您在几分钟后就可以看到新应用程序。

在 {{site.data.keyword.cloud_notm}} 开发者仪表板中创建的所有工具链都会配置为自动部署。
{: note}

要使用命令行来部署应用程序，请使用 `ibmcloud dev deploy`。有关更多信息，请参阅[使用 CLI 创建和部署应用程序](/docs/apps?topic=creating-apps-create-deploy-app-cli)。

有关部署应用程序的更多信息，请参阅[部署应用程序](/docs/apps?topic=creating-apps-deploying-apps)。
