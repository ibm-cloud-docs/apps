---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 使用代码模式创建应用程序
{: #tutorial-codepattern}

您可以使用代码模式来快速创建应用程序并将其部署到 {{site.data.keyword.cloud}}。您可以在 GitHub 中查看代码，也可以在 {{site.data.keyword.cloud_notm}} 中创建并构建应用程序，在其中您可以使用 DevOps 工具链来自动部署应用程序。
{: shortdesc}

## 步骤 1. 创建应用程序
{: #create-codepattern}

1. 转至 [IBM Developer ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/patterns/){:new_window}，然后选择所需的代码模式。例如，可以选择 [Build a MEAN Web App ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://developer.ibm.com/patterns/build-a-mean-web-app/){:new_window} 代码模式。

2. 阅读代码模式的描述，并查看 GitHub 存储库和 `README.md` 文件。要查看存储库，请单击**获取代码**，这将打开代码模式的 GitHub 存储库。

3. 使用以下任一选项开始创建应用程序。任一选项都会打开代码模式的**创建应用程序**页面。
    * 在代码模式的页面上，单击用于在 {{site.data.keyword.cloud_notm}} 上构建应用程序的链接。 
    * 在 GitHub 存储库的 `README.md` 文件中，单击用于通过入门模板工具包创建应用程序的链接。 

4. 在**创建应用程序**页面上，对应用程序命名，选择资源组，选择性提供标记，然后单击**创建**。有关标记的更多信息，请参阅[使用标记](/docs/resources/tagging_resources.html#tag)。

  要返回到代码模式，请单击**查看代码模式**。查看存储库中的 `README.md` 文件，以了解是否需要执行更多操作来启动和运行应用程序。
  {: tip}

## 步骤 2. 添加资源
{: #resources-codepattern}

您可以通过添加资源，利用 Watson 的认知功能来增强应用程序，还可以添加移动服务或安全服务。此过程会创建资源实例，创建资源密钥（凭证），并将其绑定到应用程序。对于本教程，请添加一个用于管理数据的位置。

1. 在**应用程序详细信息**页面中，单击**添加资源**。
2. 选择所需的资源类型。 
3. 选择价格套餐。轻量选项可用。
4. 单击**创建**。

## 步骤 3. 将服务凭证复制到环境

将资源添加到应用程序后，或者如果应用程序需要任何服务，请注意，该服务的凭证会显示在**凭证**框中。您必须手动将凭证复制到部署环境。

有关将凭证复制到环境的更多信息，请参阅[凭证概述](/docs/apps/creds_overview.html#credentials_overview)。

## 步骤 4. 部署到 {{site.data.keyword.cloud_notm}}
{: #deploy-codepattern}

有多种方式可以将应用程序部署到 {{site.data.keyword.cloud_notm}}，但 DevOps 工具链是部署生产应用程序的最佳方式。通过 DevOps 工具链，您可以轻松地将应用程序自动部署到多个环境中，还可以快速地添加监视、日志记录和警报服务，从而更好地管理应用程序的日常发展。

启用工具链会为应用程序创建基于团队的开发环境。创建工具链时，App Service 会创建一个 Git 存储库，您可以在其中查看源代码，克隆应用程序以及创建和管理问题。您还有权访问专用的 GitLab 环境和持续交付管道。您可以根据所选的部署环境（[Kubernetes](/docs/containers/container_index.html#container_index)、[Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) 或[虚拟服务器 (VSI)](/docs/vsi/vsi_index.html)）对它们进行定制。

1. 在**应用程序详细信息**页面上，单击**部署到云**。
2. 选择部署方法，然后单击**创建**。{{site.data.keyword.cloud_notm}} 会自动创建开放工具链，该工具链配套提供 Git 存储库和持续交付管道。
3. 打开新工具链的管道阶段，以查看构建和部署过程，这样您在几分钟后就可以查看新应用程序。

有关部署方法、构建和管道的更多信息，请参阅[构建和部署](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy)。
