---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用入门模板工具包创建基本 Web 应用程序
{: #tutorial}

{{site.data.keyword.Bluemix}} 提供了许多入门模板工具包，可帮助您快速开始编码。从 App Service 入门模板工具包中选择语言、框架和工具，以开始使用预配置的定制应用程序。在本教程中，您将全面了解安装所需工具的步骤，在本地构建和运行应用程序的步骤，以及将应用程序部署到云上的步骤。
{: shortdesc}

## 步骤 1. 安装工具
{: #install-tools}

安装 [Developer Tools](/docs/cli/index.html)。

Docker 会作为 Developer Tools 的一部分安装。Docker 必须处于运行中，构建命令才会有效。您必须创建 Docker 帐户，运行 Docker 应用程序，然后登录到该应用程序中。

## 步骤 2. 选择入门模板工具包
{: #create-devex}

在 {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}} 中，入门模板工具包有许多语言和框架可用。选择最适合开始使用项目的语言。

1. 在 {{site.data.keyword.dev_console}} 中的[入门模板工具包 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}/developer/appservice/starter-kits/) 页面中，选择适用于您语言的入门模板工具包。
2. 输入应用程序名称和唯一的主机名，例如 `abc-devhost`。此主机名就是您应用程序的路径：`abc-devhost.mybluemix.net`。
3. 选择语言和框架。某些入门模板工具包可能只有一种语言版本。
4. 选择价格套餐。对于本教程，可以使用免费选项。
5. 单击**创建**。

## 步骤 3. 添加资源（可选）
{: #add-services}

您可以通过添加资源，利用 Watson 的认知功能来增强应用程序，还可以添加移动服务或安全服务。对于本教程，请添加一个用于管理数据的位置。

1. 在 App Service 窗口中，单击**添加资源**。
2. 选择所需的服务类型。例如，选择**数据** > **下一步** > **Cloudant** > **下一步**。
3. 选择价格套餐。对于本教程，可以使用免费选项。
4. 单击**创建**。

## 步骤 4. 创建 DevOps 工具链
{: #add-toolchain}

启用工具链会为应用程序创建基于团队的开发环境。创建工具链时，App Service 会创建一个 Git 存储库，您可以在其中查看源代码，克隆应用程序以及创建和管理问题。您还有权访问专用的 GitLab 环境和持续交付管道。您可以根据所选的部署平台（Kubernetes 或 Cloud Foundry）对它们进行定制。

某些应用程序已启用了持续交付。启用持续交付后，即可通过 Delivery Pipeline 和 GitHub 进行自动构建、测试和部署。

1. 在 App Service 窗口中，单击**部署到云**。
2. 选择部署方法。根据所选方法的指示信息来设置部署方法。
  * 部署到 Kubernetes 集群。创建一个主机集群（称为工作程序节点）来部署和管理高可用性应用程序容器。您可以创建一个集群，也可以部署到现有集群。
  * 使用 Cloud Foundry 进行部署。此方法不需要管理底层基础架构。

有关更多信息，请参阅[创建工具链](https://{DomainName}/docs/services/ContinuousDelivery/toolchains_working.html)。

## 步骤 5. 在本地构建和运行应用程序
{: #build-run}

在上一个步骤中将应用程序部署到云后，即创建了工具链。工具链会为应用程序创建一个 Git 存储库，您可以在其中查找代码。要访问该存储库，请执行以下步骤。您可以在本地构建并测试应用程序，然后再将应用程序推送到云上。

1. 在 App Service 窗口中，单击**下载代码**或**克隆存储库**以在本地使用代码。
2. 将应用程序导入到集成开发环境中。
3. 修改代码。
4. 通过添加个人访问令牌来设置 [Git 认证](/docs/services/ContinuousDelivery/git_working.html#git_authentication)。
5. 登录到 {{site.data.keyword.Bluemix}} 命令行界面。如果您的组织使用联合登录，请使用 `-sso` 选项。

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. 设置组织和空间目标。

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. 获取凭证。

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

10. 在浏览器中打开 `http://localhost:3000`。您的端口号可能会有所不同，具体取决于所选的运行时。

## 步骤 6. 部署应用程序
{: #deploy}

### 使用工具链进行部署

有多种方式可以将应用程序部署到 {{site.data.keyword.cloud_notm}}，但 DevOps 工具链是部署生产应用程序的最佳方式。通过 DevOps 工具链，您可以轻松地将应用程序自动部署到多个环境中，还可以快速地添加监视、日志记录和警报服务，从而更好地管理日益增长的应用程序。

使用正确配置的工具链时，每次合并到存储库中的主分支后，都会自动启动构建/部署周期。在 {{site.data.keyword.cloud_notm}} 开发者仪表板中创建的所有工具链都会配置为自动部署。

您也可以通过 DevOps 工具链来手动部署应用程序：

1. 在“应用程序详细信息”窗口中，单击**查看工具链**。
2. 单击 **Delivery Pipeline**，在其中可以启动构建、管理部署以及查看日志和历史记录。

有关更多信息，请参阅[构建和部署](/docs/services/ContinuousDelivery/pipeline_build_deploy.html)。

### 使用 {{site.data.keyword.dev_cli_short}} 进行部署

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
{: #verify}

应用程序部署完成后，DevOps 管道或命令行会指示您前往应用程序的 URL，例如 `abc-devhost.mybluemix.net`。请在浏览器中打开该 URL。
