---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-06"

keywords: apps, deploy, deploying apps, toolchain, cli, cloud, devops, deployment, git, push

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 部署应用程序
{: #deploying-apps}

您可以使用 DevOps 工具链将应用程序部署到 {{site.data.keyword.cloud}}。通过 DevOps 工具链，您可以将应用程序自动部署到多个环境中，还可以快速地添加监视、日志记录、洞察和警报服务，从而更好地管理应用程序的日常发展。您可以使用 {{site.data.keyword.cloud_notm}} 控制台或命令行界面 (CLI) 来配置持续交付和部署应用程序。
{: shortdesc}

DevOp 工具链会为应用程序提供基于团队的开发环境。创建工具链时，App Service 会创建一个 Git 存储库，您可以在其中查看源代码，克隆应用程序以及创建和管理问题。您还有权访问专用的 GitLab 环境和持续交付管道。您可以根据所选的部署目标（[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虚拟服务器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers)）对它们进行定制。

在 {{site.data.keyword.cloud_notm}} 开发者仪表板中创建的所有工具链都会配置为自动部署。
{: note}

## 使用 {{site.data.keyword.cloud_notm}} 控制台
{: deploy-console}

{{site.data.keyword.cloud_notm}} 提供 Web 控制台，您可以在其中使用 DevOps 工具链来配置持续交付和部署应用程序。

### 开始之前
{: deploy-console-before}

开始之前，使用 [{{site.data.keyword.cloud_notm}} 仪表板](https://{DomainName}){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 来[创建应用程序](/docs/apps?topic=creating-apps-tutorial-getting-started#create-getting-started)和[添加服务](/docs/apps?topic=creating-apps-tutorial-getting-started#resources-getting-started)。

### 自动部署应用程序
{: deploy-console-auto}

1. 在**应用程序详细信息**页面上，单击**配置持续交付**。
2. 选择部署目标。根据您所选目标的指示信息来设置部署目标：
  * **部署到 IBM Kubernetes Service**。此选项将创建一个主机集群（称为工作程序节点）来部署和管理高可用性应用程序容器。您可以创建一个集群，也可以部署到现有集群。有关更多信息，请参阅[将应用程序部署到 Kubernetes 集群](/docs/containers?topic=containers-app)。
  * **部署到 Cloud Foundry**。此选项可部署云本机应用程序，而无需管理底层基础架构。如果您的帐户有权访问 {{site.data.keyword.cfee_full_notm}}，那么可以选择部署程序类型**公共云**或**企业环境**，可使用这些类型来创建和管理隔离的环境，以用于专门为您的企业托管 Cloud Foundry 应用程序。有关更多信息，请参阅[将应用程序部署到 Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps) 和[将应用程序部署到 {{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)。
  * **部署到虚拟服务器**。此选项会供应虚拟服务器实例，装入包含您的应用程序的映像，创建 DevOps 工具链，并为您启动第一个部署周期。有关更多信息，请参阅[将应用程序部署到虚拟服务器](/docs/apps?topic=creating-apps-vsi-deploy)。

### 手动部署应用程序
{: deploy-console-manual}

使用正确配置的工具链时，每次合并到存储库中的主分支后，都会自动启动构建/部署周期。 

您也可以通过 DevOps 工具链来手动部署应用程序：

1. 在**应用程序详细信息**页面上，单击**查看工具链**。
2. 单击 **Delivery Pipeline**，在其中可以启动构建、管理部署以及查看日志和历史记录。

某些应用程序已自动启用了持续交付。启用持续交付后，即可通过 Delivery Pipeline 和 GitHub 进行自动构建、测试和部署。

有关更多信息，请参阅：
* [构建和部署](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)
* [创建工具链](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)

## 使用 {{site.data.keyword.dev_cli_short}} CLI
{: #deploy-cli}

{{site.data.keyword.cloud_notm}} 提供强大的 CLI 和插件，帮助简化开发者的工作流程。您可以使用以下两种方式之一来部署 {{site.data.keyword.cloud_notm}} 应用程序，具体取决于应用程序的配置方式。

### 开始之前
{: #deploy-cli-before}

开始之前，请[下载并安装 {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli)。

Cygwin 不支持 CLI。请在非 Cygwin 命令行窗口中使用该工具。
{: important}

  1. 将应用程序的编码下载到新目录，以设置开发环境。

  2. 切换到代码所在的目录。

  3.  更新您的应用程序代码。例如，如果您使用的是 {{site.data.keyword.cloud_notm}} 样本应用程序，并且应用程序包含 `src/main/webapp/index.html` 文件，那么可以对其进行修改并对 `Thanks for creating ...` 行进行编辑。确保应用程序在本地运行，然后再将其部署到 {{site.data.keyword.cloud_notm}}。

    记录 `manifest.yml` 文件。将应用程序部署到 {{site.data.keyword.cloud_notm}} 时，此文件用于确定应用程序的 URL、内存分配、实例数和其他关键参数。

    此外还要复查 `README.md` 文件，其中包含构建指示信息等详细信息。

    如果应用程序是 Liberty 应用程序，那么必须在再次部署之前对其进行构建。
  {: note}

  4. 使用您的 IBM 标识登录到 {{site.data.keyword.cloud_notm}} CLI。 如果您有多个帐户，系统会提示您选择要使用的帐户。如果未使用 `-r` 标志指定区域，那么还必须选择区域。
```
    ibmcloud login
    ```
    {: codeblock}
  
    如果凭证被拒绝，说明您可能使用的是联合标识。要使用联合标识登录，请使用 `--sso` 标志。有关更多信息，请参阅[使用联合标识登录](/docs/iam/federated_id?topic=iam-federated_id#federated_id)。
    {: tip}

### 自动部署应用程序
{: #deploy-cli-auto}

如果尚未为应用程序创建 DevOps 工具链，并且应用程序尚未位于 Git 存储库中，那么可以运行 [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit) 命令。请遵循“配置 DevOps”的提示并部署到新的工具链（然后创建新的 GitLab 存储库）。

为应用程序创建了 DevOps 工具链后，部署新构建就很简单，只需落实代码并将代码推送到工具链中的存储库即可。 

1. 准备要提交的更改。
    ```
    git add .
    ```
2. 使用简单消息提交更改。
    ```
    git commit -m "made changes"
    ```
3. 将主分支上的提交推送到远程存储库。
    ```
    git push origin master
    ```
4. 在 {{site.data.keyword.cloud_notm}} 控制台中查看应用程序的 DevOps 工具链。通过从应用程序目录运行 [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) 命令，可在 {{site.data.keyword.cloud_notm}} 控制台的**应用程序详细信息**页面查看工具链详细信息。
5. 查看工具链内的管道以验证是否已启动新构建。

### 手动部署应用程序
{: #deploy-cli-manual}

您可以使用 [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) 命令将应用程序手动部署到 {{site.data.keyword.cloud_notm}}。

  ```
    ibmcloud dev deploy <APP_NAME>
    ```
  {: codeblock}

### 相关信息
{: #deploy-cli-related}

有关使用 CLI 将应用程序部署到 {{site.data.keyword.cloud_notm}} 的更多信息，请参阅：

* [使用 {{site.data.keyword.dev_cli_short}} CLI 部署到 IBM Cloud Environments](https://www.ibm.com/blogs/bluemix/2019/01/deploying-to-ibm-cloud-environments-with-ibm-cloud-developer-tools-cli/){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")
