---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-03-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 创建服务于前端的后端 API
{: #tutorial}

您可以通过服务于前端的后端入门模板来创建项目。使用这些入门模板，可以使用以下各种框架来构建用 Node.js、Java 或 Swift 编写的服务于前端的后端 API：Express.js、MicroProfile/Java EE、Kitura 或 Spring。您可以查看如何安装所需的工具，在本地构建和运行项目，以及将其部署到云。
{: shortdesc}

## 步骤 1：安装工具
{: #before-you-begin}

安装 [Developer Tools ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}。

## 步骤 2：创建项目
{: #create-devex}

在 {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}} 中创建项目。

1. 在 {{site.data.keyword.dev_console}} 中的[初学者工具包 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) 页面中，选择适用于您语言的初学者工具包。例如，对于 Node.js 应用程序，请转至 **Express.js 后端**，然后单击**选择初学者工具包**。

2. 输入项目名称。对于本教程，请使用 `ExpressBackend`。

3. 输入唯一的主机名，例如您的姓名首字母加 `-devhost`。例如：

	```
	abc-devhost
	```

	此主机名是项目的路径。例如，`abc-devhost.mybluemix.net`。

4. 选择语言平台。对于本教程，请使用 `Node.js`。

5. 单击**创建项目**。

## 可选：添加资源
{: #add-services}

1. 在**项目详细信息**视图中，选择**添加资源**。

2. 选择所需的服务类型。对于本教程，请选择**数据** > **下一步** > **Cloudant NoSQL DB** > **下一步**。

3. 单击**创建**。

## 可选：创建 DevOps 工具链
{: #add-toolchain}

启用工具链会为项目创建基于团队的开发环境。创建工具链时，App Service 将供应 Git 存储库，在其中可以查看源代码，克隆项目以及创建和管理问题。您还有权访问专用的 GitLab 环境以及根据您选择的部署平台（例如，Kubernetes 或 Cloud Foundry）定制的持续交付管道。

某些应用程序已启用了持续交付。您可能希望启用持续交付以通过 Delivery Pipeline 和 GitHub 来自动执行构建、测试和部署。

1. 在**项目**页面中选择项目。

2. 单击**部署到云**。

3. 选择部署方法。您可以选择以下任一项：

	* 部署到 Kubernetes 集群。供应主机集群（称为工作程序节点）来部署和管理高可用性应用程序容器。
可以创建集群或部署到现有集群。

	* 使用 Cloud Foundry 进行部署，在其中不需要管理底层基础架构。

## 步骤 3：生成项目代码
{: #generate-code}

如果在先前步骤中创建了工具链，那么已为项目创建 Git 存储库，因此您可以在其中找到相应代码。请执行以下步骤来访问该存储库：


1. 在**项目**页面中选择项目。

2. 单击**查看工具链**。

3. 单击 **CODE** 标题下的 **Git** 卡以打开存储库，在其中可以查看源代码并克隆项目。

如果未启用工具链，那么可以通过直接在“项目详细信息”视图中下载源代码来访问代码。

1. 在**项目**页面中选择项目。

2. 单击**下载代码**以下载项目归档。

## 步骤 4：开始使用应用程序
{: #code}

开始使用下载的项目：

1. 解压缩归档文件。

2. 将项目导入到 IDE。

3. 修改代码。

4. 使用 {{site.data.keyword.dev_cli_notm}} 在本地构建和运行代码。

## 步骤 5：在本地构建和运行应用程序
{: #build-run}

添加自己的代码，构建并运行项目。如果安装了必需的构建工具，或者使用 {{site.data.keyword.dev_cli_notm}} 中的可用容器支持，那么可以在主机系统上本地运行应用程序。

### 使用 {{site.data.keyword.dev_cli_short}}

1. 要在当前项目目录中构建项目，请输入以下命令：

  ```
  bx dev build
  ```
  {: codeblock}

2. 要在当前项目目录中运行项目，请输入以下命令：

  ```
  bx dev run
  ```
  {: codeblock}

3. 可以使用以下命令在服务器上运行 curl：

   ```
   curl http://localhost:3000
   ```
   {: codeblock}

4. 可以在以下位置查看服务器上的 API 文档：

   ```
   http://localhost:3000/swagger/api
   ```
   {: codeblock}

5. 可以在以下位置浏览服务器上的 API：

   ```
   http://localhost:3000/explorer
   ```
   {: codeblock}

## 步骤 6：部署到云
{: #deploy}

### 使用工具链进行部署
有多种方式可以将应用程序部署到 {{site.data.keyword.cloud_notm}}，但使用 DevOps 工具链是部署生产应用程序的最佳方式。通过 DevOps 工具链，您可以轻松地自动部署到多个环境，并快速添加监视、日志记录和警报服务，以帮助在应用程序增长时对其进行管理。

使用正确配置的工具链，每次合并到存储库中的主分支时，会自动启动构建/部署周期。在 {{site.data.keyword.cloud_notm}} 开发者仪表板中创建的所有工具链都将配置为自动部署。


您还可以通过 DevOps 工具链来手动部署应用程序：

1. 在**项目**页面中选择项目。

2. 单击**查看工具链**。

3. 查看可以在其中启动构建、管理部署以及查看日志和历史记录的 Delivery Pipeline。

### 使用 {{site.data.keyword.dev_cli_short}} 进行部署
如果选择不使用工具链，那么还可以使用 {{site.data.keyword.dev_cli_short}} 进行部署。

要将项目部署到 Cloud Foundry，请输入以下命令：

  ```
  bx dev deploy
  ```
  {: codeblock}

要将项目部署到 Kubernetes 集群，请输入以下命令：

```
bx dev deploy --target <container>
```
{: codeblock}

### 查看应用程序是否在运行
部署应用程序后，将在 DevOps 管道或终端（如果使用的是命令行）中看到类似于 `abc-devhost.mybluemix.net` 的 URL。在浏览器中访问该 URL。
