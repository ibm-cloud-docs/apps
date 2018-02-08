---

copyright:

  years: 2015，2017, 2018

lastupdated: "2018-01-18"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:prereq: .prereq}
{:download: .download}
{:pre: .pre}
{:app_name: data-hd-keyref="app_name"}
{:app_key: data-hd-keyref="app_key"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:host: data-hd-keyref="host"}
{:org_name: data-hd-keyref="org_name"}
{:route: data-hd-keyref="route"}
{:space_name: data-hd-keyref="space_name"}
{:service_name: data-hd-keyref="service_name"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:user_ID: data-hd-keyref="user_ID"}

# コマンド・ライン・インターフェースを使用したアプリのデプロイ

{{site.data.keyword.Bluemix_notm}} コマンド・ライン・インターフェースを使用して、アプリおよびサービス・インスタンスをデプロイします。
{:shortdesc}

開始する前に、{{site.data.keyword.Bluemix_notm}} コマンド・ライン・インターフェースをダウンロードしてインストールします。

<p>
<a class="xref" href="https://clis.ng.bluemix.net" target="_blank" title="(新規タブまたはウィンドウで開きます)"><img class="image" src="images/btn_bx_commandline.svg" alt="Bluemix コマンド・ライン・インターフェースのダウンロード" /> </a>
</p>

**制約事項:** コマンド・ライン・ツールは Cygwin ではサポートされていません。 このツールは Cygwin コマンド・ライン・ウィンドウ以外のコマンド・ライン・ウィンドウで使用してください。
{:prereq}

コマンド・ライン・インターフェースをインストールした後、以下の手順を開始できます。

  1. {: download} 開発環境をセットアップするため、アプリのコードを新規ディレクトリーにダウンロードします。

    <a class="xref" href="http://bluemix.net" target="_blank" title="(新規タブまたはウィンドウで開きます)"><img class="image" src="images/btn_starter-code.svg" alt="アプリケーション・コードのダウンロード" /> </a>

  2. コードが置かれているディレクトリーに移動します。

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  適切なアプリ・コードを変更します。 例えば、{{site.data.keyword.Bluemix}} サンプル・アプリケーションを使用していて、アプリに `src/main/webapp/index.html` ファイルが含まれている場合、それを編集して「Thanks for creating ...」を何か別の内容に変更します。 アプリを {{site.data.keyword.Bluemix_notm}} に戻してデプロイする前に、ローカルで稼働することを確認してください。

    `manifest.yml` ファイルをメモします。 アプリを {{site.data.keyword.Bluemix_notm}} にデプロイする際、このファイルを使用してアプリケーションの URL、メモリー割り振り、インスタンス数、およびその他の重要なパラメーターを判別します。

    該当する場合にはビルド手順などの詳細が含まれている `README.md` ファイルにも注意を払ってください。

    注: アプリケーションが Liberty アプリである場合、再デプロイする前にビルドする必要があります。

  4. {{site.data.keyword.Bluemix_notm}} に接続し、ログインします。

  <pre class="pre"><code class="hljs">bluemix api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">bluemix login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  フェデレーテッド ID を使用する場合は、`-sso` オプションを使用してください。

  <pre class="pre"><code class="hljs">bluemix login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  **注**: `username`、`org_name`、および `space_name` の値にスペースが含まれている場合は、値のまわりに単一引用符または二重引用符を追加する必要があります。例えば、`-o "my org"` のように指定します。

  5. `bluemix app push` コマンドを使用して、<var class="keyword varname">your_new_directory</var> からアプリを {{site.data.keyword.Bluemix_notm}} に再デプロイします。 `bx app push` コマンドについて詳しくは、『[アプリケーションのアップロード](/docs/starters/upload_app.html)』を参照してください。

  <pre class="pre"><code class="hljs">bluemix app push <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. https://<var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span> を表示してアプリにアクセスします。
