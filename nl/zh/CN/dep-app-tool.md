---
copyright:

  years: 2018

lastupdated: "2018-05-14"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}

# 部署应用程序
{: #deploy}

您可以使用工具链或命令行界面来部署应用程序。工具链是一组工具集成。命令行界面是部署应用程序和服务实例的简单方法。
{: shortdesc}

## 使用工具链部署应用程序
{: #toolchains_getting_started}

开放工具链在 {{site.data.keyword.Bluemix}} 上的 Public 和 Dedicated 环境中可用。您可以通过两种方式创建工具链：使用模板创建工具链或通过应用程序创建工具链。要了解有关工具链的更多信息，请参阅[创建工具链](../services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started)。

使用正确配置的工具链，部署应用程序不过是小事一桩：每次合并到存储库中的主分支时，构建/部署周期都会自动启动。

在 {{site.data.keyword.Bluemix}} 开发者仪表板中创建的所有工具链都将配置用于自动部署。
{: tip}

## 通过命令行界面部署应用程序
{: #cli}

IBM Cloud 提供了稳健的 CLI 以及与该 CLI 集成的插件和开发者工具扩展。

使用 {{site.data.keyword.Bluemix_notm}} 命令行界面部署应用程序和服务实例。
{:shortdesc}

开始之前，请下载并安装 {{site.data.keyword.Bluemix_notm}} 命令行界面。

<p>
<a class="xref" href="https://clis.ng.bluemix.net" target="_blank" title="（在新选项卡或窗口中打开）"><img class="image" src="images/btn_bx_commandline.svg" alt="下载 Bluemix 命令行界面" /> </a>
</p>

**限制：**Cygwin 不支持命令行工具。请在非 Cygwin 的命令行窗口中使用命令行工具。
{:prereq}

安装命令行界面后，可以开始执行以下操作：

  1. {: download} 将应用程序的编码下载到新目录，以设置开发环境。

    <a class="xref" href="http://bluemix.net" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="（在新选项卡或窗口中打开）"></a>

  2. 切换到代码所在的目录。

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  对应用程序代码进行更改。例如，如果要使用 {{site.data.keyword.Bluemix_notm}} 样本应用程序，并且应用程序包含 `src/main/webapp/index.html` 文件，那么可以对其进行修改并编辑“Thanks for creating ...”以输入新内容。确保应用程序在本地运行，然后再将其部署回 {{site.data.keyword.Bluemix_notm}}。

    记录 `manifest.yml` 文件。将应用程序部署回 {{site.data.keyword.Bluemix_notm}} 时，此文件用于确定应用程序的 URL、内存分配、实例数和其他关键参数。

    此外，请注意 `README.md` 文件，此文件包含详细信息，如构建指示信息（如果适用）。

    注：如果应用程序是 Liberty 应用程序，那么必须先对其进行构建，然后再重新部署。

  4. 连接并登录到 {{site.data.keyword.Bluemix_notm}}。

  <pre class="pre"><code class="hljs">bluemix api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">bluemix login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  如果使用的是联合标识，请使用 `-sso` 选项。

  <pre class="pre"><code class="hljs">bluemix login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  **注**：如果 `username`、`org_name` 和 `space_name` 的值包含空格，那么必须用单引号或双引号将其括起，例如 `-o "my org"`。

  5. 在 <var class="keyword varname">your_new_directory</var> 中，使用 `bluemix app push` 命令将应用程序重新部署到 {{site.data.keyword.Bluemix_notm}}。有关 `bluemix app push` 命令的更多信息，请参阅[上传应用程序](/docs/starters/upload_app.html)。

  <pre class="pre"><code class="hljs">bluemix app push <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. 通过浏览到 https://<var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span> 来访问应用程序。
