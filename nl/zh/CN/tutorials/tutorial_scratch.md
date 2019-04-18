---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-15"

keywords: apps, scratch, developer tools

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# 从头开始创建应用程序
{: #tutorial-scratch}

您可以使用服务和运行时来从头开始创建定制应用程序。
{: shortdesc}

## 开始之前
{: #prereqs-scratch}

* 安装 [{{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli)，其中包含 Docker。 
* 创建 Docker 帐户，运行 Docker 应用程序，然后登录到该应用程序中。Docker 必须处于运行中，构建命令才会有效。
* 如果计划将应用程序部署到 {{site.data.keyword.cfee_full}}，那么必须[准备 {{site.data.keyword.cloud_notm}} 帐户](/docs/cloud-foundry?topic=cloud-foundry-prepare)。

## 创建应用程序
{: #create-scratch}

1. 在 [{{site.data.keyword.cloud_notm}} 仪表板 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}) 中，单击“应用程序”窗口小部件中的**创建应用程序**。

  还可以在 {{site.data.keyword.dev_console}} 中的[入门模板工具包 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/developer/appservice/starter-kits/) 页面中创建定制应用程序。
  {: tip}

2. 输入应用程序的名称。对于本教程，请输入 `CustomProject`。
3. 输入唯一的主机名，例如 `abc-devhost`。主机名用于应用程序的路径，例如 `abc-devhost.mybluemix.net`。
4. 可以选择性提供标记来对应用程序分类。有关更多信息，请参阅[使用标记](/docs/resources?topic=resources-tag)。
5. 选择语言和框架。某些入门模板工具包可能只有一种语言版本。
6. 选择价格套餐。对于本教程，您可以使用免费选项。
7. 单击**创建**。

缺省共享域为 `mybluemix.net`，但是，`appdomain.cloud` 是另一个可供您使用的域选项。有关迁移到 `appdomain.cloud` 的更多信息，请参阅[更新域](/docs/apps/tutorials?topic=creating-apps-update-domain)。
{: tip}

## 添加服务（可选）
{: #resources-scratch}

您可以通过添加服务，利用 Watson 的认知功能来增强应用程序，还可以添加移动服务或安全服务。对于本教程，可以添加一个用于管理数据的位置。

1. 在**应用程序详细信息**页面上，单击**添加服务**。
2. 选择所需的服务类型。例如，选择**数据** > **下一步** > **Cloudant** > **下一步**。
3. 选择价格套餐。对于本教程，您可以使用免费选项。
4. 单击**创建**。

## 在本地构建和运行应用程序
{: #build-run-scratch}

您可以在本地构建应用程序以进行测试，然后再将应用程序部署到云。

1. 在**应用程序详细信息**页面上，单击**下载代码**或**克隆存储库**以在本地使用代码。
2. 将应用程序导入到集成开发环境中。
3. 修改代码。
4. 通过添加个人访问令牌来设置 [Git 认证](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication)。
5. 登录到 {{site.data.keyword.cloud_notm}} 命令行界面 (CLI)。如果您的组织使用联合登录，请使用 `-sso` 选项；例如：

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. 运行以下命令来设置组织和空间目标。

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. 运行以下命令来检索凭证。

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. 确保 Docker 正在运行，然后运行以下命令在目录中的本地开发容器中构建应用程序。

  ```bash
ibmcloud dev build
```
  {: pre}

9. 运行以下命令在本地开发容器中运行应用程序。

  ```bash
ibmcloud dev run
```
  {: pre}

10. 在浏览器中转至 `http://localhost:3000`。您的端口号可能会有所不同，具体取决于所选的运行时。

## 部署应用程序
{: #deploy-scratch}

有多种方式可以将应用程序部署到 {{site.data.keyword.cloud_notm}}，但 DevOps 工具链是部署生产应用程序的最佳方式。通过 DevOps 工具链，您可以轻松地将应用程序自动部署到多个环境中，还可以快速地添加监视、日志记录和警报服务，从而更好地管理应用程序的日常发展。

启用工具链会为应用程序创建基于团队的开发环境。创建工具链时，App Service 会创建一个 Git 存储库，您可以在其中查看源代码，克隆应用程序以及创建和管理问题。您还有权访问专用的 GitLab 环境和持续交付管道。您可以根据所选的部署环境（[Kubernetes](/docs/containers?topic=containers-container_index)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虚拟服务器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers)）对它们进行定制。

在 {{site.data.keyword.cloud_notm}} 开发者仪表板中创建的所有工具链都会配置为自动部署。
{: note}

### 使用 DevOps 工具链手动进行部署

使用正确配置的工具链时，每次合并到存储库中的主分支后，都会自动启动构建/部署周期。 

您也可以通过 DevOps 工具链来手动部署应用程序：

1. 在“应用程序详细信息”页面，单击**查看工具链**。
2. 单击 **Delivery Pipeline**，在其中可以启动构建、管理部署以及查看日志和历史记录。

某些应用程序已启用了持续交付。启用持续交付后，即可通过 Delivery Pipeline 和 GitHub 进行自动构建、测试和部署。

有关更多信息，请参阅：
* [使用 Continuous Delivery 进行构建和部署](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)。
* [基于模板创建工具链](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)。

### 使用 DevOps 工具链自动进行部署

1. 在**应用程序详细信息**页面上，单击**配置持续交付**。
2. 选择部署目标。根据您所选目标的指示信息来设置部署目标：
  * **部署到 IBM Kubernetes Service**。此选项将创建一个主机集群（称为工作程序节点）来部署和管理高可用性应用程序容器。您可以创建一个集群，也可以部署到现有集群。
  * **部署到 Cloud Foundry**。此选项可部署云本机应用程序，而无需管理底层基础架构。如果您的帐户有权访问 {{site.data.keyword.cfee_full_notm}}，那么可以选择部署程序类型**公共云**或**企业环境**，可使用这些类型来创建和管理隔离的环境，以用于专门为您的企业托管 Cloud Foundry 应用程序。
  * **部署到虚拟服务器**。此选项会供应虚拟服务器实例，装入包含您的应用程序的映像，创建 DevOps 工具链，并为您启动第一个部署周期。

在最后一步中将应用程序部署到云后，即会自动创建工具链。工具链会为应用程序创建 Git 存储库，在其中可以查找代码。 

### 使用 {{site.data.keyword.dev_cli_short}} 进行部署
{: #deploy-scratch-cli}

要将应用程序部署到 Cloud Foundry，请输入以下命令：
```
ibmcloud dev deploy
```
{: pre}

要将应用程序部署到 Kubernetes 集群，请输入以下命令：
```
ibmcloud dev deploy --target <container>
```
{: pre}

## 验证应用程序是否正在运行
{: #verify-scratch}

应用程序部署完成后，Delivery Pipeline 或命令行会指示您前往应用程序的 URL。

1. 在 DevOps 工具链中，单击 **Delivery Pipeline**，然后选择 **Deploy 阶段**。
2. 单击**查看日志和历史记录**。
3. 在日志文件中，查找应用程序 URL：

    在日志文件末尾，搜索 `urls` 或 `view`。例如，您可能会在日志文件中看到类似于以下内容的行：`urls: my-app-devhost.mybluemix.net` 或 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在浏览器中转至该 URL。如果应用程序正在运行，那么将显示包含 `Congratulations` 或 `{"status":"UP"}` 的消息。

如果使用的是命令行，请运行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 命令来查看应用程序的 URL。然后，在浏览器中转至该 URL。
