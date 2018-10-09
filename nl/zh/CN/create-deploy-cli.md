---
copyright:

  years: 2018

lastupdated: "2018-10-02"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}

# 使用 CLI 创建和部署应用程序
{: #developing}

您可以使用 {{site.data.keyword.Bluemix}} 命令行界面 (CLI) 来创建和部署应用程序。
{:shortdesc}

## 开始之前
{: #prereqs}

安装 {{site.data.keyword.Bluemix_notm}} CLI、{{site.data.keyword.dev_cli_notm}} CLI 插件以及其他建议的插件和工具。有关更多信息，请参阅 [IBM Cloud CLI 入门](/docs/cli/index.html)。 

## 创建应用程序
{: #create}

您可以从头开始创建新的应用程序，也可以使用现有代码创建支持云的应用程序。 

### 从头开始创建应用程序

1. 在所选目录中运行 [`ibmcloud dev create`](/docs/cli/idt/commands.html#create) 命令。
2. 选择**后端服务/Web 应用程序**作为应用程序类型。
3. 选择 **Node** 作为语言类型。
4. 选择 **Express.js Basic（Web 应用程序）**作为要使用的入门模板工具包。
5. 输入应用程序的名称，然后选择要使用的资源组（如果需要）。暂时不要添加服务。
6. 选择 **IBM DevOps，使用 Cloud Foundry** 选项来创建 DevOps 工具链。您可能需要设置 SSH 密钥才能完成此步骤。
7. 输入唯一的主机名，例如 `abc-devhost`。此主机名是应用程序的路径 `abc-devhost.mybluemix.net`。

创建应用程序和工具链需要几秒钟时间来完成。您可以监视命令提示符中的相应状态。

### 使用现有代码创建应用程序

1. 通过在所选目录中运行以下命令来克隆 [Hello World 样本应用程序](https://github.com/IBM-Cloud/node-helloworld)。

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

2. 浏览至在其中克隆了样本应用程序的目录，并运行 [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable) 命令。
3. 选择继续，暂时不将更改落实到 GitHub。
4. 系统提示您继续使用检测到的 Node 语言时，请选择继续。
5. 选择要使用的资源组（如果需要）。暂时不要添加服务。
6. 稍候几秒钟以等待应用程序创建。 
7. 可以选择手动合并在创建应用程序时已保存到应用程序目录的部署和配置文件。或者，可以暂时跳过此步骤。

## 构建应用程序并本地运行
{: #build-run}

无论使用哪个选项创建应用程序，现在都可以构建应用程序并在本地运行。

1. 浏览至应用程序目录，并确保 Docker 正在系统上运行。
2. 运行 [`ibmcloud dev build`](/docs/cli/idt/commands.html#build) 命令构建应用程序。
3. 运行 [`ibmcloud dev run`](/docs/cli/idt/commands.html#run) 命令开始本地运行应用程序。
4. 在 `http://localhost:3000` 或类似 URL 处查看本地运行的应用程序。
5. 按 **Ctrl+C** 键以停止应用程序。

还可以使用[复合命令](/docs/cli/idt/commands.html#compound)（如 `ibmcloud dev build/run`）按顺序先发出 build 命令，再发出 run 命令。
{: tip}

## 添加服务和修改编码
{: #add-service}

既然应用程序可以本地运行，那就可以添加服务并修改某些代码了。 

1. 运行 [`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit) 命令。
2. 按照提示创建与数据相关的新服务，然后将其连接到应用程序（如 {{site.data.keyword.cloudant_short_notm}}）。您可能需要选择服务的区域和套餐。
3. 可以选择手动合并在创建服务时已保存到应用程序目录的部署和配置。或者，可以暂时跳过此步骤。
4. 在代码中进行更改。例如，修改 `/public/index.html` 文件或类似文件。如果您使用的是样本 `ExpressJS` 应用程序，那么可以将 `Congratulations!` 字符串更改为 `Hello World!` 等内容。
5. 保存修改的任何文件。

## 部署到 {{site.data.keyword.Bluemix_notm}}
{: #deploy}

您可以使用以下两种方式之一来部署应用程序 {{site.data.keyword.Bluemix_notm}}，具体取决于应用程序的配置方式。 

### 使用 DevOps 工具链部署应用程序

如果您先前已为应用程序创建了 DevOps 工具链，那么部署新构建很简单，只需落实代码并将代码推送到工具链中的存储库即可。 

1. 运行 `git add` 命令。
2. 运行 `git commit -m "made changes"` 命令落实更改。
3. 运行 `git push origin master` 命令推送到主分支。
4. 在 {{site.data.keyword.Bluemix_notm}} 控制台中查看应用程序的 DevOps 工具链。可以在 Web 浏览器中，通过从应用程序目录运行 [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) 命令并单击**查看工具链**来查看工具链。
5. 查看工具链内的管道以验证是否新构建已启动。

### 手动部署应用程序

您可以使用 [`deploy`](/docs/cli/idt/commands.html#deploy) 命令手动部署应用程序。例如，使用以下步骤将应用程序手动部署到 Kubernetes。

1. 确保已[创建 Kubernetes 集群](https://console.bluemix.net/containers-kubernetes/overview)。
2. 运行 [`ibmcloud dev deploy -t container`](/docs/cli/idt/commands.html#deploy) 命令。
3. 系统提示时，请确认要使用的集群和容器映像名称。
4. 稍候几分钟以等待部署完成。

## 查看应用程序
{: #view}

1. 要查看在 {{site.data.keyword.Bluemix_notm}} 上运行的应用程序的 URL，请运行 [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) 命令。
2. 要在 {{site.data.keyword.Bluemix_notm}} 控制台中查看有关应用程序凭证、服务和工具链的详细信息，请运行 [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) 命令。 

