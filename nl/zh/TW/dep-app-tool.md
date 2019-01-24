---

copyright:
  years: 2018
lastupdated: "2018-12-17"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 部署應用程式
{: #deploy}

您可以使用工具鏈或指令行介面 (CLI) 來部署應用程式。工具鏈是一組工具整合。CLI 是部署應用程式和服務實例的簡單方法。
{: shortdesc}

## 使用工具鏈部署應用程式
{: #toolchains_getting_started}

開放式工具鏈可用於 {{site.data.keyword.Bluemix}} 上的「公用」和「專用」環境。使用適當配置的工具鏈，部署應用程式便很輕鬆。會自動開始建置並部署的循環，並且全都合併到您儲存庫的主要分支。

您可以用兩種方式的其中一個來建立工具鏈：使用範本建立工具鏈，或是從應用程式範本工具鏈。若要進一步瞭解工具鏈，請參閱[建立工具鏈](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started)。

## 使用 CLI 來部署應用程式
{: #cli}

{{site.data.keyword.cloud_notm}} 提供強健的 CLI，以及與 CLI 整合的外掛程式和開發人員工具延伸規格。

開始之前，[請下載並安裝 {{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html)。

<p>
<a class="xref" href="https://cloud.ibm.com/docs/cli/index.html#overview" target="_blank" title="（在新分頁或視窗中開啟）"><img class="image" src="images/btn_bx_commandline.svg" alt="下載 IBM Cloud Developer Tools" /></a>
</p>

Cygwin 不支援 CLI。請在非 Cygwin 指令行視窗的視窗中使用此工具。
{: important}

  1. {: download}將您應用程式的程式碼下載至新的目錄，以設定開發環境。

    <a class="xref" href="https://cloud.ibm.com" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="（在新分頁或視窗中開啟）"></a>

  2. 切換至您程式碼所在的目錄。

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  變更應用程式碼。例如，如果您是使用 {{site.data.keyword.cloud_notm}} 範例應用程式，而且您的應用程式包含 `src/main/webapp/index.html` 檔案，則可以修改它，並編輯 `Thanks for creating ...` 這行。請先確定應用程式在本端執行，再將它部署回 {{site.data.keyword.cloud_notm}}。

    記下 `manifest.yml` 檔案。將應用程式部署回 {{site.data.keyword.cloud_notm}} 時，此檔案用來決定您應用程式的 URL、記憶體配置、實例數以及其他決定性參數。

    也請檢閱 `README.md` 檔案，它包含建置指示這類詳細資料（適用時）。

  如果您的應用程式是 Liberty 應用程式，則必須先建置它，再重新部署。
  {: note}

  4. 連接並登入 {{site.data.keyword.cloud_notm}}。

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  如果您使用聯合 ID，請新增 `-sso` 選項。

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  如果值包含空格，您必須在 `username`、`org_name` 和 `space_name` 週圍加上單引號或雙引號，例如 `-o "my org"`。
  {: note}

  5. 從您的新目錄，使用 `ibmcloud dev deploy` 指令以將應用程式部署至 {{site.data.keyword.cloud_notm}}。如需相關資訊，請參閱 [CLI 文件](/docs/cli/idt/commands.html#deploy)。

  <pre class="pre"><code class="hljs">ibmcloud dev deploy <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. 前往 https://<var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span> 以存取應用程式。
