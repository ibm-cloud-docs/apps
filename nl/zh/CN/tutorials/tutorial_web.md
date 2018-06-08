---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-22"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用初学者工具包创建基本 Web 应用程序
{: #tutorial}

您可以通过基本 Web 入门模板来创建应用程序。使用这些入门模板可通过多个可供选择的 Web 框架针对 Swift、Node、Java 或 Python 构建简单的 Web 服务器。您可以了解如何安装所需的工具，如何在本地构建和运行应用程序，以及如何将应用程序部署到云上。
{: shortdesc}

## 步骤 1：安装工具
{: #before-you-begin}

安装 [Developer Tools ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}。


## 步骤 2：创建应用程序
{: #create-devex}

在 {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}} 中创建应用程序：

1. 在 {{site.data.keyword.dev_console}} 中的[初学者工具包 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) 页面中，选择适用于您语言的初学者工具包。例如，对于 Node.js 应用程序，请选择 **Express.js 基本**，然后选择**创建**。

2. 输入应用程序名称。对于本教程，请使用 `WebBasicProject`。   

3. 输入唯一的主机名，例如您的姓名首字母加 `-devhost`。例如：

	```
	abc-devhost
	```

	此主机名是应用程序的路径。例如，`abc-devhost.mybluemix.net`。

4. 选择语言平台。对于本教程，请使用 `Node.js`。

5. 单击**创建**。

## 可选：添加资源
{: #add-services}

1. 在**应用程序详细信息**视图中，选择**添加资源**。

2. 选择所需的服务类型。对于本教程，请选择**数据** > **下一步** > **Cloudant NoSQL DB** > **下一步**。

3. 单击**创建**。

## 可选：创建 DevOps 工具链
{: #add-toolchain}

启用工具链会为应用程序创建基于团队的开发环境。创建工具链时，App Service 将供应 Git 存储库，在其中可以查看源代码，克隆应用程序以及创建和管理问题。您还有权访问专用的 GitLab 环境以及根据您选择的部署平台（例如，Kubernetes 或 Cloud Foundry）定制的持续交付管道。

某些应用程序已启用了持续交付。您可能希望启用持续交付以通过 Delivery Pipeline 和 GitHub 来自动执行构建、测试和部署。

1. 在**应用程序**页面中选择您的应用程序。

2. 单击**部署到云**。

3. 选择部署方法。您可以选择以下任一项：

	* 部署到 Kubernetes 集群。供应主机集群（称为工作程序节点）来部署和管理高可用性应用程序容器。
可以创建集群或部署到现有集群。

	* 使用 Cloud Foundry 进行部署，在其中不需要管理底层基础架构。

## 步骤 3：生成应用程序代码
{: #generate-code}

如果在前面的步骤中创建了工具链，那么您的应用程序就有一个创建好的 Git 存储库，您可以在其中查找代码。请执行以下步骤来访问该存储库：


1. 在**应用程序**页面中选择您的应用程序。

2. 单击**查看工具链**。

3. 单击**代码**标题下的 **Git** 卡以打开存储库，在其中可以查看源代码和克隆应用程序。

如果未启用工具链，那么可以直接从“应用程序详细信息”视图中下载源代码来访问您的代码。

1. 在**应用程序**页面中选择您的应用程序。

2. 单击**下载代码**以下载应用程序归档文件。

## 步骤 4：开始使用应用程序
{: #code}

开始使用下载的应用程序：

1. 解压缩归档文件。

2. 将应用程序导入到 IDE 中。

3. 修改代码。

4. 使用 {{site.data.keyword.dev_cli_notm}} 在本地构建和运行代码。

## 步骤 5：在本地构建和运行应用程序
{: #build-run}

添加自己的代码，然后构建并运行应用程序。如果安装了必需的构建工具，或者使用 {{site.data.keyword.dev_cli_notm}} 中的可用容器支持，那么可以在主机系统上本地运行应用程序。

### 使用 {{site.data.keyword.dev_cli_short}}

1. 安装节点依赖项：

  ```
  npm install
  ```
  {: codeblock}

2. 将前端代码捆绑到模块中：

  ```
  gulp
  ```
  {: codeblock}

3. 要在当前应用程序目录中构建应用程序，请输入以下命令：

  ```
  ibmcloud dev build
  ```
  {: codeblock}

4. 要在当前应用程序目录中运行应用程序，请输入以下命令：

  ```
  ibmcloud dev run
  ```
  {: codeblock}

5. 打开浏览器并转至 `http://localhost:3000`。您的端口号可能有所不同，具体取决于所选的运行时。


## 步骤 6：部署到云
{: #deploy}

### 使用工具链进行部署
有多种方式可以将应用程序部署到 {{site.data.keyword.cloud_notm}}，但使用 DevOps 工具链是部署生产应用程序的最佳方式。通过 DevOps 工具链，您可以轻松地自动部署到多个环境，并快速添加监视、日志记录和警报服务，以帮助在应用程序增长时对其进行管理。

使用正确配置的工具链，每次合并到存储库中的主分支时，会自动启动构建/部署周期。在 {{site.data.keyword.cloud_notm}} 开发者仪表板中创建的所有工具链都将配置为自动部署。


您还可以通过 DevOps 工具链来手动部署应用程序：

1. 在**应用程序**页面中选择您的应用程序。

2. 单击**查看工具链**。

3. 查看可以在其中启动构建、管理部署以及查看日志和历史记录的 Delivery Pipeline。

### 使用 {{site.data.keyword.dev_cli_short}} 进行部署
如果选择不使用工具链，那么还可以使用 {{site.data.keyword.dev_cli_short}} 进行部署。

要将应用程序部署到 Cloud Foundry，请输入以下命令：

  ```
  ibmcloud dev deploy
  ```
  {: codeblock}

要将应用程序部署到 Kubernetes 集群，请输入以下命令：

```
ibmcloud dev deploy --target <container>
```
{: codeblock}

### 查看应用程序是否在运行
部署应用程序后，将在 DevOps 管道或终端（如果使用的是命令行）中看到类似于 `abc-devhost.mybluemix.net` 的 URL。在浏览器中访问该 URL。
