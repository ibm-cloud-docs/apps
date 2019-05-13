---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-30"

keywords: scratch, developer tools, custom app, app tutorial, verify app running, run app local

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
3. 可以选择性提供标记来对应用程序分类。有关更多信息，请参阅[使用标记](/docs/resources?topic=resources-tag)。
4. 选择语言和框架。某些入门模板工具包可能只有一种语言版本。
5. 选择价格套餐。对于本教程，您可以使用免费选项。
6. 单击**创建**。

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

单击**应用程序详细信息**页面上的**配置持续交付**，选择部署目标，然后单击**创建**。{{site.data.keyword.cloud_notm}} 会自动创建开放工具链，该工具链配套提供 Git 存储库和持续交付管道。

启用工具链会为应用程序创建基于团队的开发环境。创建工具链时，App Service 会创建一个 Git 存储库，您可以在其中查看源代码，克隆应用程序以及创建和管理问题。您还有权访问专用的 GitLab 环境和持续交付管道。您可以根据所选的部署目标（[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虚拟服务器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers)）对它们进行定制。

选择部署目标后，打开新工具链的管道组件，以开始初始构建和部署过程，这样您在几分钟后就可以看到新应用程序。

在 {{site.data.keyword.cloud_notm}} 开发者仪表板中创建的所有工具链都会配置为自动部署。
{: note}

要使用命令行来部署应用程序，请使用 `ibmcloud dev deploy`。有关更多信息，请参阅[使用 CLI 创建和部署应用程序](/docs/apps?topic=creating-apps-create-deploy-app-cli)。

有关部署应用程序的更多信息，请参阅[部署应用程序](/docs/apps?topic=creating-apps-deploying-apps)。

## 验证应用程序是否正在运行
{: #verify-scratch}

应用程序部署完成后，Delivery Pipeline 或命令行会指示您前往应用程序的 URL。

1. 在 DevOps 工具链中，单击 **Delivery Pipeline**，然后选择 **Deploy 阶段**。
2. 单击**查看日志和历史记录**。
3. 在日志文件中，查找应用程序 URL：

   在日志文件末尾，搜索 `urls` 或 `view`。例如，您可能会在日志文件中看到类似于以下内容的行：`urls: my-app-devhost.mybluemix.net` 或 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在浏览器中转至该 URL。如果应用程序正在运行，那么将显示包含 `Congratulations` 或 `{"status":"UP"}` 的消息。

如果使用的是命令行，请运行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 命令来查看应用程序的 URL。然后，在浏览器中转至该 URL。

