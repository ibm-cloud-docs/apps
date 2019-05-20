---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-30"

keywords: apps, code pattern, DevOps, toolchain, service credentials, create app code pattern, app pattern

subcollection: creating-apps

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

1. 转至 [IBM Developer ](https://developer.ibm.com/patterns/){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")，然后选择所需的代码模式。例如，可以选择 [Build a MEAN Web App ](https://developer.ibm.com/patterns/build-a-mean-web-app/){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标") 代码模式。

2. 阅读代码模式的描述，并查看 GitHub 存储库和 `README.md` 文件。要查看存储库，请单击**获取代码**，这将打开代码模式的 GitHub 存储库。

3. 使用以下任一选项开始创建应用程序。任一选项都会打开代码模式的**创建应用程序**页面。
    * 在代码模式的页面上，单击用于在 {{site.data.keyword.cloud_notm}} 上构建应用程序的链接。 
    * 在 GitHub 存储库的 `README.md` 文件中，单击用于通过入门模板工具包创建应用程序的链接。 

4. 在**创建应用程序**页面上，对应用程序命名，选择资源组，选择性提供标记，然后单击**创建**。有关标记的更多信息，请参阅[使用标记](/docs/resources?topic=resources-tag)。

  要返回到代码模式，请单击**查看代码模式**。查看存储库中的 `README.md` 文件，以了解是否需要执行更多操作来启动和运行应用程序。
  {: tip}

## 步骤 2. 添加服务
{: #resources-codepattern}

您可以通过添加服务，利用 Watson 的认知功能来增强应用程序，还可以添加移动服务或安全服务。此过程会创建服务实例，创建资源密钥（凭证），并将其绑定到应用程序。对于本教程，请添加一个用于管理数据的位置。

1. 在**应用程序详细信息**页面上，单击**添加服务**。
2. 选择所需的服务类型。 
3. 选择价格套餐。轻量选项可用。
4. 单击**创建**。

## 步骤 3. 将服务凭证复制到环境

将服务添加到应用程序后，或者如果应用程序需要任何服务，请注意，该服务的凭证会显示在**凭证**框中。您必须手动将凭证复制到部署环境。

有关将凭证复制到环境的更多信息，请参阅[凭证概述](/docs/apps?topic=creating-apps-credentials_overview#credentials_overview)。

## 步骤 4. 部署到 {{site.data.keyword.cloud_notm}}
{: #deploy-codepattern}

选择部署目标时，会自动为您的应用程序创建 DevOps 工具链。工具链包含指示应用程序部署状态的 Delivery Pipeline。生成的新应用程序将推送到作为工具链一部分的 GitLab 存储库。

启用 DevOp 工具链会为应用程序创建基于团队的开发环境。创建工具链时，App Service 会创建一个 Git 存储库，您可以在其中查看源代码，克隆应用程序以及创建和管理问题。您还有权访问专用的 GitLab 环境和持续交付管道。您可以根据所选的部署目标（[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虚拟服务器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial)）对它们进行定制。

在 {{site.data.keyword.cloud_notm}} 开发者仪表板中创建的所有工具链都会配置为自动部署。
{: note}

要选择部署目标并配置持续交付，请完成以下步骤：

1. 在“应用程序详细信息”页面上，单击**配置持续交付**。
2. 选择部署目标。根据您所选目标的指示信息来设置部署目标：
  * **部署到 [IBM Kubernetes Service](/docs/containers?topic=containers-app)**。此选项将创建一个主机集群（称为工作程序节点）来部署和管理高可用性应用程序容器。您可以创建一个集群，也可以部署到现有集群。
  * **部署到 Cloud Foundry**。此选项可部署云本机应用程序，而无需管理底层基础架构。如果您的帐户有权访问 {{site.data.keyword.cfee_full_notm}}，那么可以选择部署程序类型**[公共云](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)**或**[企业环境](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**，可使用这些类型来创建和管理隔离的环境，以用于专门为您的企业托管 Cloud Foundry 应用程序。
  * **部署到虚拟服务器**。此选项会供应虚拟服务器实例，装入包含您的应用程序的映像，创建 DevOps 工具链，并为您启动第一个部署周期。

选择并配置部署目标后，“应用程序详细信息”页面将指示已配置持续交付。您可以通过单击**查看存储库**来查看包含应用程序的源代码的存储库。

有关部署应用程序的更多信息，请参阅[部署应用程序](/docs/apps?topic=creating-apps-deploying-apps)。

有关部署目标、构建和管道的更多信息，请参阅[构建和部署](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)。
