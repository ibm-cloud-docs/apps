---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, deploy, deploying apps, toolchains, cli

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

您可以使用工具链或命令行界面 (CLI) 来部署应用程序。工具链是一组工具集成。CLI 是一种部署应用程序和服务实例的简单方法。
{: shortdesc}

## 使用工具链部署应用程序
{: #toolchain-deploy-apps}

开放工具链在 {{site.data.keyword.Bluemix}} 上的 Public 和 Dedicated 环境中可用。通过正确配置工具链，您可以轻松部署应用程序。每次合并到存储库中的主分支后，都会自动启动构建/部署周期。

您可以通过以下方式来创建工具链：
* 使用模板来创建工具链。
* 通过应用程序创建工具链。

要了解有关工具链的更多信息，请参阅[创建工具链](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)。

## 使用 CLI 部署应用程序
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}} 提供了稳健的 CLI 以及与该 CLI 集成的插件和开发者工具扩展。

开始之前，请[下载并安装 {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli)。

Cygwin 不支持 CLI。请在非 Cygwin 命令行窗口中使用该工具。
{: important}

  1. {: download}将应用程序的编码下载到新目录，以设置开发环境。

    <a class="xref" href="https://{DomainName}" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="（在新选项卡或窗口中打开）"></a>

  2. 切换到代码所在的目录。

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  对应用程序代码进行更改。例如，如果您使用的是 {{site.data.keyword.cloud_notm}} 样本应用程序，并且应用程序包含 `src/main/webapp/index.html` 文件，那么可以对其进行修改并对 `Thanks for creating ...` 行进行编辑。确保应用程序在本地运行，然后再将其部署回 {{site.data.keyword.cloud_notm}}。

    记录 `manifest.yml` 文件。将应用程序部署回 {{site.data.keyword.cloud_notm}} 时，此文件用于确定应用程序的 URL、内存分配、实例数和其他关键参数。

    此外还要复查 `README.md` 文件，其中包含构建指示信息等详细信息（如果适用）。

  如果应用程序是 Liberty 应用程序，那么必须在再次部署之前对其进行构建。
  {: note}

  4. 连接并登录到 {{site.data.keyword.cloud_notm}}。

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  如果使用的是联合标识，请添加 `-sso` 选项。

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  如果该值包含空格，那么必须用单引号或双引号将 `username`、`org_name` 和 `space_name` 括起，例如 `-o "my org"`。
  {: note}

  5. 在新的目录中，使用 `ibmcloud dev deploy` 命令将应用程序部署到 {{site.data.keyword.cloud_notm}}。有关更多信息，请参阅 [CLI 文档](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy)。

  <pre class="pre"><code class="hljs">ibmcloud dev deploy <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. 通过浏览 https://<var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span> 来访问您的应用程序。
