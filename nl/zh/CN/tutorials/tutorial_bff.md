---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-02"

keywords: create bff app, backend-for-frontend app, bff, developer tools, Node.js, Java, Swift, DevOps toolchain, bff app tutorial

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 创建服务于前端的后端应用程序
{: #tutorial-bff}

您可以使用服务于前端的后端入门模板来创建应用程序。借助这些入门模板，您可以通过使用以下各种框架来构建用 Node.js、Java&reg 或 Swift 语言编写的服务于前端的后端应用程序：Express.js、MicroProfile/Java&reg EE、Kitura 或 Spring。您将了解如何安装所需的工具，如何在本地构建和运行应用程序，以及如何将应用程序部署到云上。
{: shortdesc}

## 步骤 1. 开始之前
{: #prereqs-bff}

* 安装 [Developer Tools](/docs/cli?topic=cloud-cli-ibmcloud-cli)。
* Docker 会作为 Developer Tools 的一部分安装。Docker 必须处于运行中，构建命令才会有效。您必须创建 Docker 帐户，运行 Docker 应用程序，然后登录到该应用程序中。
* 如果计划将应用程序部署到 {{site.data.keyword.cfee_full}}，那么必须[准备 {{site.data.keyword.cloud_notm}} 帐户](/docs/cloud-foundry?topic=cloud-foundry-prepare)。

## 步骤 2. 创建应用程序
{: #create-bff}

在 {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}} 中创建应用程序。

1. 在 {{site.data.keyword.dev_console}} 中的[入门模板工具包 ](https://{DomainName}/developer/appservice/starter-kits/){: new_window} ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标") 页面中，选择适用于您语言的入门模板工具包。例如，对于 Node.js 应用程序，请转至 **Express.js 后端**，然后单击**选择入门模板工具包**。
2. 输入应用程序名称。对于本教程，请使用 `ExpressBackend`。
3. 输入唯一的主机名，例如 `abc-devhost`。此主机名是应用程序的路径 `abc-devhost.mybluemix.net`。
4. 可选。提供标记来对应用程序分类。有关更多信息，请参阅[使用标记](/docs/resources?topic=resources-tag)。
5. 选择语言和框架。某些入门模板工具包可能只有一种语言版本。
6. 选择价格套餐。对于本教程，可以使用免费选项。
7. 单击**创建**。

缺省共享域为 `mybluemix.net`，但是，`appdomain.cloud` 是另一个可供您使用的域选项。有关迁移到 `appdomain.cloud` 的更多信息，请参阅[更新域](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain)。
{: tip}

## 步骤 3. 添加服务（可选）
{: #resources-bff}

您可以通过添加服务，利用 Watson 的认知功能来增强应用程序，还可以添加移动服务或安全服务。对于本教程，请添加一个用于管理数据的位置。

1. 在**应用程序详细信息**页面上，单击**添加服务**。
2. 选择所需的服务类型。例如，选择**数据** > **下一步** > **Cloudant** > **下一步**。
3. 选择价格套餐。对于本教程，可以使用免费选项。
4. 单击**创建**。

## 步骤 4. 创建 DevOps 工具链
{: #toolchain-bff}

启用工具链会为应用程序创建基于团队的开发环境。创建工具链时，App Service 会创建一个 Git 存储库，您可以在其中查看源代码，克隆应用程序以及创建和管理问题。您还有权访问专用的 GitLab 环境和持续交付管道。您可以根据所选的部署目标（[Kubernetes](/docs/containers?topic=containers-container_index)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虚拟服务器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers)）对它们进行定制。

在 {{site.data.keyword.cloud_notm}} 开发者仪表板中创建的所有工具链都会配置为自动部署。
{: note}

1. 在**应用程序详细信息**页面上，单击**配置持续交付**。
2. 选择部署目标。根据您所选方法的指示信息来设置部署目标：
  * **部署到 [IBM Kubernetes Service](/docs/containers?topic=containers-container_index)**。此选项将创建一个主机集群（称为工作程序节点）来部署和管理高可用性应用程序容器。您可以创建一个集群，也可以部署到现有集群。
  * **部署到 Cloud Foundry**。此选项可部署云本机应用程序，而无需管理底层基础架构。如果您的帐户有权访问 {{site.data.keyword.cfee_full_notm}}，那么可以选择部署程序类型**[公共云](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)**或**[企业环境](/docs/cloud-foundry?topic=cloud-foundry-about)**，可使用这些类型来创建和管理隔离的环境，以用于专门为您的企业托管 Cloud Foundry 应用程序。
  * **部署到[虚拟服务器](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers)**。此选项会供应虚拟服务器实例，装入包含您的应用程序的映像，创建 DevOps 工具链，并为您启动第一个部署周期。

## 步骤 5. 在本地构建和运行应用程序
{: #build-run-bff}

在上一个步骤中将应用程序部署到云后，即创建了工具链。工具链会为应用程序创建一个 Git 存储库，您可以在其中查找代码。要访问该存储库，请执行以下步骤。您可以在本地构建并测试应用程序，然后再将应用程序推送到云上。

1. 在**应用程序详细信息**页面上，单击**下载代码**或**克隆存储库**以在本地使用代码。
2. 将应用程序导入到集成开发环境中。
3. 修改代码。
4. 通过添加个人访问令牌来设置 [Git 认证](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication)。
5. 登录到 {{site.data.keyword.cloud_notm}} 命令行界面。如果您的组织使用联合登录，请使用 `-sso` 选项。

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. 设置组织和空间目标。

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7.  获取凭证。

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. 确保 Docker 正在运行，然后在目录中的本地开发容器中构建应用程序。

  ```bash
ibmcloud dev build
```
  {: pre}

9. 在本地开发容器中运行应用程序。

  ```bash
ibmcloud dev run
```
  {: pre}

10.  在浏览器中打开 `http://localhost:3000`。您的端口号可能会有所不同，具体取决于所选的运行时。

## 步骤 6. 部署应用程序
{: #deploy-bff}

### 使用工具链进行部署
{: #deploy-bff-toolchain}

有多种方式可以将应用程序部署到 {{site.data.keyword.cloud_notm}}，但 DevOps 工具链是部署生产应用程序的最佳方式。通过 DevOps 工具链，您可以轻松地将应用程序自动部署到多个环境中，还可以快速地添加监视、日志记录和警报服务，从而更好地管理应用程序的日常发展。

使用正确配置的工具链时，每次合并到存储库中的主分支后，都会自动启动构建/部署周期。在 {{site.data.keyword.cloud_notm}} 开发者仪表板中创建的所有工具链都会配置为自动部署。

您也可以通过 DevOps 工具链来手动部署应用程序：

1. 在**应用程序详细信息**页面上，单击**查看工具链**。

2. 单击 **Delivery Pipeline**，在其中可以启动构建、管理部署以及查看日志和历史记录。

### 使用 {{site.data.keyword.dev_cli_short}} 进行部署
{: #deploy-bff-cli}

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

## 步骤 7. 验证应用程序是否正在运行
{: #verify-bff}

应用程序部署完成后，Delivery Pipeline 或命令行会指示您前往应用程序的 URL。

1. 在 DevOps 工具链中，单击 **Delivery Pipeline**，然后选择 **Deploy 阶段**。
2. 单击**查看日志和历史记录**。
3. 在日志文件中，查找应用程序 URL：

    在日志文件末尾，搜索 `urls` 或 `view`。例如，您可能会在日志文件中看到类似于以下内容的行：`urls: my-app-devhost.mybluemix.net` 或 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在浏览器中转至该 URL。如果应用程序正在运行，那么将显示包含 `Congratulations` 或 `{"status":"UP"}` 的消息。

如果使用的是命令行，请运行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 命令来查看应用程序的 URL。然后，在浏览器中转至该 URL。
