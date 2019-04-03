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

# アプリのデプロイ
{: #deploying-apps}

アプリは、ツールチェーンやコマンド・ライン・インターフェース (CLI) を使用してデプロイできます。 ツールチェーンは、ツール統合の集合です。 CLI は、アプリとサービス・インスタンスをデプロイするための簡単な方法です。
{: shortdesc}

## ツールチェーンを使用したアプリのデプロイ
{: #toolchain-deploy-apps}

オープン・ツールチェーンは、{{site.data.keyword.Bluemix}} の Public 環境および Dedicated 環境で使用可能です。 適切に構成されたツールチェーンを使用すると、アプリのデプロイは簡単です。 リポジトリー内のマスター・ブランチへのマージが行われるたびに、ビルドとデプロイのサイクルが自動的に開始されます。

ツールチェーンは以下の方法で作成できます。
* テンプレートを使用してツールチェーンを作成する。
* アプリからツールチェーンを作成する。

ツールチェーンについて詳しくは、[ツールチェーンの作成](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)を参照してください。

## CLI を使用したアプリのデプロイ
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}} には、堅固な CLI と、CLI に統合されるプラグインおよび開発者ツール拡張機能が用意されています。

開始する前に、[{{site.data.keyword.cloud_notm}} CLI をダウンロードしてインストールします](/docs/cli?topic=cloud-cli-ibmcloud-cli)。

CLI は、Cygwin によってサポートされていません。 このツールは Cygwin コマンド・ライン・ウィンドウ以外のウィンドウで使用してください。
{: important}

  1. {: download} 開発環境をセットアップするため、アプリのコードを新規ディレクトリーにダウンロードします。

    <a class="xref" href="https://{DomainName}" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="(新しいタブまたはウィンドウで開く)"></a>

  2. コードが置かれているディレクトリーに移動します。

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">your_new_directory</var></code></pre>

  3.  アプリ・コードを変更します。 例えば、{{site.data.keyword.cloud_notm}} サンプル・アプリケーションを使用していて、アプリに `src/main/webapp/index.html` ファイルが含まれている場合は、それを変更して「`Thanks for creating ...`」行を編集できます。 アプリを {{site.data.keyword.cloud_notm}} に戻してデプロイする前に、ローカルで稼働することを確認してください。

    `manifest.yml` ファイルをメモします。 アプリを {{site.data.keyword.cloud_notm}} にデプロイする際、このファイルを使用してアプリケーションの URL、メモリー割り振り、インスタンス数、およびその他の重要なパラメーターを判別します。

    また、`README.md` ファイルも確認してください。このファイルには、該当する場合、ビルド手順などの詳細情報が含まれています。

  アプリケーションが Liberty アプリである場合、再度デプロイする前にビルドする必要があります。
  {: note}

  4. {{site.data.keyword.cloud_notm}} に接続し、ログインします。

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">DomainName</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">username</var> -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var></code></pre>

  フェデレーテッド ID を使用する場合は、`-sso` オプションを追加してください。

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">org_name</var> -s <var class="keyword varname" data-hd-keyref="space_name">space_name</var> -sso</code></pre>

  `username`、`org_name`、`space_name` の値にスペースが含まれている場合は、値のまわりに単一引用符または二重引用符を追加する必要があります。例えば、`-o "my org"` のように指定します。
  {: note}

  5. 新規ディレクトリーから、`ibmcloud dev deploy` コマンドを使用して、アプリを {{site.data.keyword.cloud_notm}} にデプロイします。 詳しくは、[CLI の資料](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy)を参照してください。

  <pre class="pre"><code class="hljs">ibmcloud dev deploy <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. <var class="keyword varname" data-hd-keyref="app_url">app_url</var>.<span class="keyword" data-hd-keyref="APPDomain">AppDomainName</span> を表示してアプリにアクセスします。
