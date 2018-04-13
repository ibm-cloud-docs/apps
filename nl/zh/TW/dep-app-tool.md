---
copyright:

  years: 2018

lastupdated: "2018-03-17"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}

# 部署應用程式
{: #deploy}

您可以使用工具鏈或指令行介面來部署應用程式。工具鏈是一組工具整合。指令行介面是部署應用程式和服務實例的簡單方法。
{: shortdesc}

## 使用工具鏈部署應用程式
{: #toolchains_getting_started}

開放式工具鏈可用於 {{site.data.keyword.Bluemix}} 上的「公用」和「專用」環境。您可以用兩種方式建立工具鏈：使用範本建立工具鏈，或是從應用程式範本工具鏈。若要進一步瞭解工具鏈，請參閱[建立工具鏈](../services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started)。

使用適當配置的工具鏈，部署應用程式便微不足道：建置-部署的循環會自動開始，並且全都合併到您儲存庫的主要分支。

從 {{site.data.keyword.Bluemix}} 開發人員儀表板建立的所有工具鏈都會針對自動部署進行配置。
{: tip}

## 使用指令行介面部署應用程式
{: #cli}

IBM Cloud 提供一個健全的 CLI，以及與 CLI 整合的外掛程式和開發人員工具延伸規格。

使用 {{site.data.keyword.Bluemix_notm}} 指令行介面，以部署應用程式及服務實例。
{:shortdesc}

開始之前，請下載並安裝 {{site.data.keyword.Bluemix_notm}} 指令行介面。

<p>
<a class="xref" href="https://clis.ng.bluemix.net" target="_blank" title="（在新分頁或視窗中開啟）"><img class="image" src="images/btn_bx_commandline.svg" alt="下載 Bluemix 指令行介面" /> </a>
</p>

**限制：**Cygwin 不支援指令行工具。在指令行視窗（而非 Cygwin 指令行視窗）中，使用此工具。
{:prereq}

安裝指令行介面之後，即可開始：

  1. {: download} 將您應用程式的程式碼下載至新的目錄，以設定開發環境。

    <a class="xref" href="http://bluemix.net" target="_blank" title="（在新分頁或視窗中開啟）"></a>

  2. 切換至您程式碼所在的目錄。

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  變更應用程式碼。例如，如果您是使用 {{site.data.keyword.Bluemix_notm}} 範例應用程式，而且您的應用程式包含 `src/main/webapp/index.html` 檔案，則可以修改它，並編輯 "Thanks for creating ..." 傳達新的訊息。請先確定應用程式在本端執行，再將它部署回 {{site.data.keyword.Bluemix_notm}}。

    記下 `manifest.yml` 檔案。將應用程式部署回 {{site.data.keyword.Bluemix_notm}} 時，此檔案用來決定您應用程式的 URL、記憶體配置、實例數以及其他決定性參數。

    也請注意 `README.md` 檔案，它包含建置指示這類詳細資料（適用時）。

    附註：如果您的應用程式是 Liberty 應用程式，則必須先建置它，再重新部署。

  4. 連接並登入 {{site.data.keyword.Bluemix_notm}}。

  <pre class="pre"><code class="hljs">bluemix api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">bluemix login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  如果您要使用聯合 ID，請使用 `-sso` 選項。

  <pre class="pre"><code class="hljs">bluemix login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  **附註**：如果值包含空格，您必須在 `username`、`org_name` 和 `space_name` 週圍加上單引號或雙引號，例如 `-o "my org"`。

  5. 從 <var class="keyword varname">your_new_directory</var> 中，使用 `bluemix app push` 指令以將應用程式重新部署至 {{site.data.keyword.Bluemix_notm}}。如需 `bx app push` 指令的相關資訊，請參閱[上傳應用程式](/docs/starters/upload_app.html)。

  <pre class="pre"><code class="hljs">bluemix app push <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. 瀏覽至 https://<var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span>，以存取應用程式。
