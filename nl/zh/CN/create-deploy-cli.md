---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-08"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# 使用 CLI 创建和部署应用程序
{: #create-deploy-app-cli}

您可以使用 {{site.data.keyword.cloud}} 命令行界面 (CLI) 来创建和部署应用程序。 

您可以从头开始创建入门模板应用程序，也可以对现有应用程序代码进行云启用。
{: note}

## 开始之前
{: #prereqs-app-cli}

必须安装 {{site.data.keyword.cloud_notm}} CLI、{{site.data.keyword.dev_cli_notm}} CLI 插件以及其他建议的插件和工具。有关更多信息，请参阅 [IBM Cloud CLI 入门](/docs/cli/index.html)。 

## 从头开始创建入门模板应用程序
{: #create-app-cli}

如果您还没有现存的代码，希望从语言或框架入门模板开始，那么从头开始创建应用程序非常有用。

1. 在所选目录中运行 [`ibmcloud dev create`](/docs/cli/idt/commands.html#create) 命令。
2. 选择**后端服务/Web 应用程序**作为应用程序类型。
3. 选择 **Node** 作为语言类型。
4. 选择 **Node.js Web App with Express.js（Web 应用程序）**作为要使用的入门模板工具包。
5. 输入应用程序的名称，然后选择要使用的资源组（如果需要）。暂时不要添加服务。
6. 选择 **IBM DevOps，使用 Cloud Foundry** 选项来创建 DevOps 工具链。您可能需要设置 SSH 密钥才能完成此步骤。如果为 SSH 密钥设置了口令，那么需要输入此代码。
  {: note}
7. 输入唯一的主机名，例如 `abc-devhost`。此主机名就是您应用程序的路径：`abc-devhost.cloud.ibm.com`。

创建应用程序和工具链需要几秒钟时间来完成。

## 生成部署和云支持资产
{: #byoc-cli}

如果您已有现存的代码库，并且希望使用 [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable) 为单个微服务或 Web 应用程序生成部署和云支持资产，那么可以使用此选项。请注意，此命令处于 Beta 版，无法支持所有语言和/或应用程序结构。以下指示信息说明如何将此功能与样本存储库配合使用，但对于您自己的代码库，步骤大致相同。

1. 通过运行 ibmcloud login 登录到 {{site.data.keyword.cloud_notm}}，然后将某个组织和空间设定为目标。
2. 通过在所选目录中运行以下命令来克隆 [Hello World 样本应用程序](https://github.com/IBM-Cloud/node-helloworld)。

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

3. 浏览至在其中克隆了样本应用程序的目录，并运行 [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable) 命令。
4. 选择继续，暂时不要落实更改（如果需要）。
5. 系统提示您继续使用检测到的 Node 语言时，请选择继续。
6. 选择要使用的资源组（如果需要）。 
7. 选择此选项以创建链接到此 Git 存储库的新 {{site.data.keyword.cloud_notm}} 应用程序。有关详细信息，请参阅**重要说明**。
8. 暂时不要添加服务。
9. 稍候几秒钟以等待操作完成。 
10. 完成后，您可以手动合并部署和云支持文件，并将其保存到应用程序目录。使用 `git diff` 或类似工具来合并标记为 `.merge` 的新文件。

### 重要说明
 - 如果已使用 {{site.data.keyword.cloud_notm}} 控制台创建了 {{site.data.keyword.cloud_notm}} 应用程序，请在应用程序目录中执行先前部分中的步骤 2 - 5。对于步骤 6，可以选择用于将本地代码连接到现有应用程序的选项。
 - 您还可以选择通过运行 [`ibmcloud dev enable --no-create`](/docs/cli/idt/commands.html#enable)，生成部署和云支持文件，而不连接到 {{site.data.keyword.cloud_notm}} 应用程序。
 - 要手动配置工具链和部署文件，请遵循[本教程](/docs/apps/tutorials/tutorial_byoc_kube.html#tutorial-byoc-kube)。如果要尝试为多个相互关联的 Web 应用程序或微服务配置 Continuous Delivery 工具链，那么这会非常有用。
 - 如果现有代码库尚未位于 Git 存储库中，请在应用程序目录中执行先前部分中的步骤 2 - 5。对于步骤 6，可以选择用于创建新的 {{site.data.keyword.cloud_notm}} 应用程序并将其部署到 DevOps 工具链（具有新创建的 GitLab 存储库）的选项。

## 在本地构建和运行应用程序
{: #build-run-app-cli}

无论之前使用了哪个选项创建应用程序，现在都可以在本地构建和运行应用程序。

1. 浏览至应用程序目录，并确保 Docker 正在系统上运行。
2. 运行 [`ibmcloud dev build`](/docs/cli/idt/commands.html#build) 命令构建应用程序。
3. 运行 [`ibmcloud dev run`](/docs/cli/idt/commands.html#run) 命令，开始在本地运行应用程序。
4. 在 `http://localhost:3000` 或类似 URL 处查看本地运行的应用程序。
5. 按 **Ctrl+C** 键以停止应用程序。

还可以使用[复合命令](/docs/cli/idt/commands.html#compound)（如 `ibmcloud dev build/run`），按顺序先发出 build 命令，再发出 run 命令。
{: tip}

## 添加服务和修改代码
{: #resources-app-cli}

既然应用程序可本地运行，就可以添加服务和修改某些代码。 

1. 运行 [`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit) 命令。
2. 按照提示创建与数据相关的新服务，然后将其连接到应用程序（如 {{site.data.keyword.cloudant_short_notm}}）。您可能需要选择服务的区域和套餐。
3. 可以选择手动合并在创建服务时已保存到应用程序目录的配置文件。或者，可以暂时跳过此步骤。
4. 更新您的代码。例如，修改 `/public/index.html` 文件或类似文件。如果您使用的是样本 `ExpressJS` 应用程序，那么可以将 `Congratulations!` 字符串更改为 `Hello World!` 之类的字符串。
5. 保存修改的任何文件。

## 部署到 {{site.data.keyword.cloud_notm}}
{: #deploy-app-cli}

您可以使用以下两种方式之一来部署 {{site.data.keyword.cloud_notm}} 应用程序，具体取决于应用程序的配置方式。 

### 使用 DevOps 工具链部署应用程序
如果尚未为应用程序创建 DevOps 工具链，并且应用程序尚未位于 Git 存储库中，那么可以运行 [`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit) 命令。请遵循“配置 DevOps”的提示并部署到新的工具链（然后创建新的 GitLab 存储库）。

为应用程序创建了 DevOps 工具链后，部署新构建就很简单，只需落实代码并将代码推送到工具链中的存储库即可。 

1. 运行 `git add` 命令。
2. 运行 `git commit -m "made changes"` 命令以落实更改。
3. 运行 `git push origin master` 命令以推送到主分支。
4. 在 {{site.data.keyword.cloud_notm}} 控制台中查看应用程序的 DevOps 工具链。通过从应用程序目录运行 [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) 命令，可在 {{site.data.keyword.cloud_notm}} 控制台的“应用程序详细信息”屏幕中查看工具链详细信息。
5. 查看工具链内的管道以验证是否已启动新构建。

### 手动部署应用程序

您可以使用 [`deploy`](/docs/cli/idt/commands.html#deploy) 命令手动部署应用程序。例如，使用以下步骤将应用程序手动部署到 Kubernetes。

1. 确保已[创建 Kubernetes 集群](https://{DomainName}/containers-kubernetes/overview)。
2. 运行 [`ibmcloud dev deploy -t container`](/docs/cli/idt/commands.html#deploy) 命令。
3. 系统提示时，请确认要使用的集群和容器映像名称。
4. 稍候几分钟以等待部署完成。

## 查看应用程序
{: #view-app-cli}

1. 要查看在 {{site.data.keyword.cloud_notm}} 上运行的应用程序的 URL，请运行 [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) 命令。
2. 要在 {{site.data.keyword.cloud_notm}} 控制台中查看有关应用程序凭证、服务和工具链的详细信息，请运行 [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) 命令。 

**要报告问题或提供反馈，可以使用 [{{site.data.keyword.cloud_notm}} Tech 的 Slack - #developer-tools 通道](https://ibm-cloud-tech.slack.com) - 请求团队访问[此处](https://slack-invite-ibm-cloud-tech.mybluemix.net/)。**
