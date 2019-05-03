---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, starter kit, kubernetes, cluster, kube, deploy, deployment

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 将入门模板工具包应用程序部署到 Kubernetes 集群
{: #tutorial-starterkit-kube}

了解如何使用空白入门模板工具包和 Kubernetes 工具链在 {{site.data.keyword.cloud}} 中创建应用程序，并持续将应用程序交付到 Kubernetes 集群中的安全容器。可配置持续集成 DevOps 管道，以便自动构建代码更改并将其传播到 Kube 集群中的应用程序。如果您已有管道，那么可以将其连接到应用程序。
{: shortdesc}

{{site.data.keyword.cloud_notm}} 提供了入门模板工具包，可帮助您构建在 Kubernetes 上运行的应用程序的基础。使用入门模板工具包时，可以轻松遵循使用 {{site.data.keyword.cloud_notm}} 应用程序开发最佳实践的云本机编程模型。入门模板工具包会生成遵循云本机编程模型的应用程序，这些应用程序包含每种编程语言的测试用例、运行状况检查和度量值。您还可以供应云服务，然后在生成的应用程序中对这些服务进行初始化。

本教程使用 Kubernetes 部署目标。在本教程中，我们将使用 Java + Spring 通过基本入门模板工具包来创建应用程序，向该应用程序添加 Cloudant 服务实例，然后使用 IBM Kubernetes Service 将该应用程序部署到 {{site.data.keyword.cloud_notm}}。

首先，请参阅以下入门模板工具包流程图及其相应的概述步骤。

![入门模板工具包流程图](../images/starterkit-flow.png) 

## 开始之前
{: #prereqs-starterkit-kube}

* 使用[入门模板工具包](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit)创建 **Java + Spring** 应用程序。
* 安装 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli)。
* 设置 [Docker ](https://www.docker.com/get-started){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")。

## 向应用程序添加服务
{: #resources-starterkit-kube}

向应用程序添加 {{site.data.keyword.cloud_notm}} 服务。以下步骤将供应 Cloudant 实例，创建资源密钥（凭证），并将其绑定到应用程序。

1. 在**应用程序详细信息**页面上，单击**添加服务**。
2. 选择**数据**，然后单击**下一步**。
3. 选择 **Cloudant**，然后单击**下一步**。
4. 在**添加 Cloudant** 页面上，选择区域 (US-South)、资源组（缺省值）和价格套餐（轻量 - 一个免费实例）。
5. 单击**创建**。这将显示**应用程序详细信息**页面，供应 Cloudant 实例并将其绑定到应用程序。请注意，Cloudant 资源密钥（凭证）将添加到**凭证**字段。
6. 可选。如果要在添加服务后快速查看应用程序代码，请单击**下载代码**。代码会下载为 `.zip` 文件，其中包含完整的应用程序代码结构。您可以使用 {{site.data.keyword.dev_cli_notm}} 轻松解压缩该文件并在本地运行代码，或者将其添加到代码管理存储库中。

## 使用 DevOps 工具链部署应用程序
{: #deploy-starterkit-kube}

将 DevOps 工具链连接到应用程序，并将其配置为部署到 {{site.data.keyword.cloud_notm}} Kubernetes 服务中托管的 Kubernetes 集群。

1. 在**应用程序详细信息**页面上，单击**配置持续交付**。
2. 在**选择部署目标**页面上，选择**部署到 IBM Kubernetes Service**。
3. 选择区域和集群。如果您没有 Kubernetes 集群，请单击**创建集群**。
  * 在**新建集群**页面上，选择位置和集群类型（免费），输入集群名称，然后单击**创建集群**。
  * 如果需要，请遵循屏幕上的指示信息来获取对集群的访问权。
  * 等待集群指示**就绪**以创建工具链。使用 **US-South** 区域时，可以供应一个免费集群。
  * 返回到**选择部署目标**页面。
4. 单击**下一步**。这将显示**配置工具链**页面。
5. 在**配置工具链**页面上，输入工具链名称，选择区域，选择资源组，然后单击**创建**。这将显示**应用程序详细信息**页面，以及有关工具链的部署信息。

## 查看存储库
{: #view-repo-starterkit-kube}

1. 在**应用程序详细信息**页面上，单击**查看存储库**。这将显示入门模板工具包生成的 Git 存储库。
2. 可选。遵循屏幕上的指示信息，在桌面上配置 SSH。
3. 可选。遵循屏幕上的指示信息，在帐户上创建个人访问令牌。

## 查看工具链工具、日志和历史记录
{: #view-logs-starterkit-kube}

1. 部署阶段完成后，将显示**应用程序详细信息**页面，以及有关工具链的部署信息。
2. 通过单击**查看工具链**来访问工具链。这将显示工具链页面的**概述**选项卡，其中显示工具链随附的工具。此示例包含的以下工具是创建工具链时在入门模板工具包中预先选择的工具：
  * 作业跟踪程序，用于跟踪项目更新和更改。
  * Git 存储库，包含应用程序源代码。
  * Eclipse Orion 实例，这是基于 Web 的 IDE，用于编辑应用程序。
  * Delivery Pipeline，由可定制的 Build 和 Deploy 阶段组成。
	 * BUILD 阶段用于对应用程序容器化。更具体地说，Build 阶段执行以下操作：
	   * 克隆 GitLab 存储库。
	   * 构建应用程序。
	   * 构建 Docker 映像。
	   * 将映像发布到专用容器注册表。
	 * DEPLOY 阶段用于从容器注册表检索容器映像，然后将其部署到 Kubernetes 集群。
3. 单击 **Delivery Pipeline**。这将显示管道各阶段。
4. 在 **Deploy 阶段**磁贴中，单击**查看日志和历史记录**。

## 验证应用程序是否正在运行
{: #verify-starterkit-kube}

应用程序部署完成后，Delivery Pipeline 或命令行会指示您前往应用程序的 URL。

1. 在 DevOps 工具链中，单击 **Delivery Pipeline**，然后选择 **Deploy 阶段**。
2. 单击**查看日志和历史记录**。
3. 在日志文件中，查找应用程序 URL：

    在日志文件末尾，搜索 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在浏览器中转至该 URL。如果应用程序正在运行，那么将显示包含 `Congratulations` 或 `{"status":"UP"}` 的消息。

如果使用的是命令行，请运行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 命令来查看应用程序的 URL。然后，在浏览器中转至该 URL。

## 后续步骤
{: #next-steps-startkit-kube notoc}

* 如果在部署时遇到错误，请查看故障诊断主题以了解[超过存储配额](/docs/apps?topic=creating-apps-managingapps#exceed_quota)等已知问题，或者了解如何[访问 Kubernetes 日志](/docs/apps?topic=creating-apps-managingapps#access_kube_logs)来查找错误。

* 访问代码中的服务配置：
	- 可以使用 _@Value_ 注释，也可以使用 Spring 框架环境类 _getProperty()_ 方法。有关更多信息，请参阅[访问凭证](/docs/java-spring?topic=java-spring-configuration#accessing-credentials)。

* 向 Kubernetes 环境添加新凭证：
	- 创建 DevOps 工具链后，向应用程序添加其他服务时，这些服务凭证不会自动更新到已部署的应用程序和 GitLab 存储库。您必须向部署环境[手动添加凭证](/docs/apps?topic=creating-apps-add-credentials-kube)。
