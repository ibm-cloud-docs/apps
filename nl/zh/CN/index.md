---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# 在 {{site.data.keyword.Bluemix_notm}} 中创建应用程序
{: #create}

在 {{site.data.keyword.Bluemix}} 中，可以构建企业级移动和 Web 应用程序，并可利用由 {{site.data.keyword.Bluemix_notm}} 托管的云扩展。构建、运行和部署应用程序时，可以使用 {{site.data.keyword.Bluemix}} 控制台和命令行工具。请按照以下步骤开始此端到端开发场景。


## 步骤 1：注册 {{site.data.keyword.Bluemix_notm}} 帐户
{: #sign-up}

转至 [bluemix.net](bluemix.net)。输入您的电子邮件、姓名、公司、区域和电话号码即可。您无需信用卡就可以注册免费帐户。然后可随意浏览。

## 步骤 2：浏览目录
{: #catalog}

{{site.data.keyword.Bluemix_notm}}“目录”列出了它提供的基础架构和平台资源。您可以通过选择虚拟机、容器或 Cloudant（即 Cloud Foundry 应用程序）来开始构建应用程序。如果您需要平台资源，{{site.data.keyword.Bluemix_notm}} 还提供有样板，其中有多种运行时和其他服务可帮助您开始进行构建。

## 步骤 3：创建资源
{: #resource}

1. 在[仪表板](https://console.bluemix.net/dashboard/apps/)中，单击**创建资源**。

2. 从“目录”的“平台”部分中选择应用程序。然后，选择运行时。例如，可以选择 IBM buildpack 支持的 IBM 运行时环境，例如 Liberty for Java。您还可以选择依赖于开放式源代码和第三方 buildpack 的社区运行时，例如 Tomcat。

  * [Containers 入门](../containers/container_index.html)
  * [Openwhisk 入门](../openwhisk/index.html)
  * [创建 Cloud Foundry 应用程序](../cfapps/index.html#creating_cloud_foundry_apps)

3. 输入应用程序名称和主机名，并选择价格套餐。

4. 选择开发样式。可以在首选文本编辑器中编辑应用程序，并使用 {{site.data.keyword.Bluemix_notm}} 命令行将其部署到 {{site.data.keyword.Bluemix_notm}}。此外，还可以使用 {{site.data.keyword.Bluemix_notm}} DevOps Services 从浏览器部署应用程序，或者使用 Eclipse Tools for {{site.data.keyword.Bluemix_notm}} 在 Eclipse 集成开发环境中处理应用程序。

## 步骤 4：开始添加代码
{: #code}

每个应用程序都有一个入门部分，可帮助您获得开始工作所需的所有软件和内容。

在仪表板中，单击应用程序，然后单击**入门**，这可以帮助您获得开发应用程序所需的软件，指向源代码以及帮助您首次部署应用程序。

## 后续步骤
{: #next}

开发应用程序后，请使用我们的[最佳实践](best-practice.html)和[云就绪](cloud-ready.html)指南，以确保应用程序已准备好用于 {{site.data.keyword.Bluemix_notm}}。然后，[部署](../starters/install_cli.html)应用程序。
