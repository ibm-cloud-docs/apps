---
copyright:

  years: 2018

lastupdated: "2018-07-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# アプリのデプロイ
{: #deploy}

アプリは、ツールチェーンやコマンド・ライン・インターフェースを使用してデプロイできます。 ツールチェーンは、ツール統合の集合です。 コマンド・ライン・インターフェースは、アプリとサービス・インスタンスをデプロイするための簡単な方法です。
{: shortdesc}

## ツールチェーンを使用したアプリのデプロイ
{: #toolchains_getting_started}

オープン・ツールチェーンは、{{site.data.keyword.Bluemix}} の Public 環境および Dedicated 環境で使用可能です。 ツールチェーンの作成方法には、テンプレートを使用した作成と、アプリからの作成の 2 とおりの方法があります。 ツールチェーンについて詳しくは、[ツールチェーンの作成](../services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started)を参照してください。

適切に構成されたツールチェーンを使用すると、アプリのデプロイは非常に簡単です。リポジトリー内のマスター・ブランチへのマージが行われるたびに、ビルドおよびデプロイのサイクルが自動的に開始されます。

{{site.data.keyword.Bluemix}} 開発者ダッシュボードから作成されたツールチェーンはすべて、自動デプロイメント用に構成されています。
{: tip}

## コマンド・ライン・インターフェースを使用したアプリのデプロイ
{: #cli}

IBM Cloud は、堅固な CLI のほかに、CLI と統合されるプラグインおよび開発者ツール拡張機能も提供します。

{{site.data.keyword.Bluemix_notm}} コマンド・ライン・インターフェースを使用して、アプリおよびサービス・インスタンスをデプロイします。
{:shortdesc}

開始する前に、[{{site.data.keyword.Bluemix_notm}} コマンド・ライン・インターフェースをダウンロードしてインストールします](/docs/cli/index.html)。

<p>
<a class="xref" href="https://console.bluemix.net/docs/cli/index.html#overview" target="_blank" title="(新しいタブまたはウィンドウで開きます)"><img class="image" src="images/btn_bx_commandline.svg" alt="IBM Cloud Developer Tools のダウンロード" /></a>
</p>

**制約事項:** コマンド・ライン・ツールは Cygwin ではサポートされていません。 このツールは Cygwin コマンド・ライン・ウィンドウ以外のコマンド・ライン・ウィンドウで使用してください。
{:prereq}

コマンド・ライン・インターフェースをインストールした後、以下の手順を開始できます。

  1. {: download} 開発環境をセットアップするため、アプリのコードを新規ディレクトリーにダウンロードします。

    <a class="xref" href="http://bluemix.net" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="(新しいタブまたはウィンドウで開く)"></a>

  2. コードが置かれているディレクトリーに移動します。

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  アプリ・コードを変更します。 例えば、{{site.data.keyword.Bluemix_notm}} サンプル・アプリケーションを使用していて、アプリに `src/main/webapp/index.html` ファイルが含まれている場合、それを編集して「Thanks for creating ...」を何か別の内容に変更します。 アプリを {{site.data.keyword.Bluemix_notm}} に戻してデプロイする前に、ローカルで稼働することを確認してください。

    `manifest.yml` ファイルをメモします。 アプリを {{site.data.keyword.Bluemix_notm}} にデプロイする際、このファイルを使用してアプリケーションの URL、メモリー割り振り、インスタンス数、およびその他の重要なパラメーターを判別します。

    該当する場合にはビルド手順などの詳細が含まれている `README.md` ファイルにも注意を払ってください。

    注: アプリケーションが Liberty アプリである場合、再デプロイする前にビルドする必要があります。

  4. {{site.data.keyword.Bluemix_notm}} に接続し、ログインします。

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  フェデレーテッド ID を使用する場合は、`-sso` オプションを追加してください。

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  **注**: `username`、`org_name`、`space_name` の値にスペースが含まれている場合は、値のまわりに単一引用符または二重引用符を追加する必要があります。例えば、`-o "my org"` のように指定します。

  5. `ibmcloud dev deploy` コマンドを使用して、<var class="keyword varname">your_new_directory</var> からアプリを {{site.data.keyword.Bluemix_notm}} に再デプロイします。詳しくは、[CLI の資料](docs/cli/idt/commands.html#deploy)を参照してください。

  <pre class="pre"><code class="hljs">ibmcloud dev deploy <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. https://<var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span> を表示してアプリにアクセスします。
