---

copyright:
  years: 2017, 2018
lastupdated: "2018-05-21"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 入门教程
{: #create}

在 {{site.data.keyword.Bluemix}} 中，可以构建企业级移动和 Web 应用程序，并可利用由 {{site.data.keyword.Bluemix_notm}} 托管的云扩展。使用 {{site.data.keyword.Bluemix}} 控制台和命令行工具，可构建、运行和部署应用程序。您可以通过两种方式开始构建应用程序：一种是使用可帮您管理创建过程的入门模板工具包来创建应用程序；另一种是自行使用所需的资源来构建应用程序，前提是您知道自己想要什么。
{:shortdesc}

您可以使用初学者工具包来快速开始使用应用程序，并为其未来开发做好准备。选择入门模板工具包和编程语言，创建应用程序，然后设置 DevOps 工具链以自动部署应用程序。此外，还可以下载代码来直接检查您的代码。

初学者工具包在许多类别中都可用，包括：

* [Watson](https://console.bluemix.net/developer/watson){:new_window}
* [Apple](https://console.bluemix.net/developer/appledevelopment){:new_window}
* [移动](https://console.bluemix.net/developer/mobile){:new_window}
* [Web 应用程序](https://console.bluemix.net/developer/appservice){:new_window}
* [安全性](https://console.bluemix.net/developer/security){:new_window}
<!--* [Watson Data Platform developer console](https://console.bluemix.net/developer/dataplatform)-->
* [财务](https://console.bluemix.net/developer/finance){:new_window}

## 开始之前

[注册](https://console.bluemix.net){: new_window} {{site.data.keyword.cloud_notm}} 帐户。输入您的电子邮件、姓名、公司、区域和电话号码。

您无需信用卡就可以注册免费帐户，但通过输入信用卡，您可以访问更多资源，并且能更轻松地全面了解所有 {{site.data.keyword.cloud_notm}} 优惠。

## 步骤 1：创建应用程序
{: #project}

1. 单击**菜单**图标 ![“菜单”图标](../icons/icon_hamburger.svg) > **Web 应用程序**。

2. 单击**从 Web 开始**部分中的**开始**。

3. 选择您想要的初学者工具包，阅读详细信息，然后单击**创建**。

  要查看初学者工具包中所包含的内容，请展开“应用程序服务初学者工具包”仪表板上的磁贴。
  {: tip}

4. 为应用程序命名，选择语言，然后单击**创建**。

很好！您刚刚创建了应用程序。

要检查您的代码，请单击应用程序详细信息页面上的**下载代码**。检查下载的压缩文件中的 `README.md` 文件，以了解是否需要执行更多操作来使入门模板应用程序运行。
{: tip}

## 步骤 2：添加资源
{: #addResources}

大多数初学者工具包指示 {{site.data.keyword.cloud_notm}} 自动为您供应资源。您还可以单击应用程序详细信息页面上的**添加资源**，将更多资源与应用程序进行关联。

要在本地开发并运行应用程序，请使用 [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html)。
{: tip}

## 步骤 3：部署到 {{site.data.keyword.cloud_notm}}
{: #deploy}

单击应用程序详细信息页面上的**部署到云**，选择部署方法（例如，Kubernetes 集群或 Cloud Foundry 应用程序），然后单击**创建**。{{site.data.keyword.cloud_notm}} 会自动创建开放工具链，该工具链配套提供 Git 存储库和持续交付管道。查看新工具链的管道组件，以开始初始构建和部署过程，这样您在几分钟内就可以看到新应用程序开始运行。

现在，您已准备就绪，可进行迭代开发和持续交付。
