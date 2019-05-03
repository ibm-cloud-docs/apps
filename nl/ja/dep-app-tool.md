---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-02"

keywords: apps, deploy, deploying apps, toolchains, cli, cloud

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

アプリケーションは、DevOps ツールチェーンやコマンド・ライン・インターフェース (CLI) を使用してデプロイできます。 DevOps ツールチェーンは、ツール統合の集合です。 CLI は、アプリとサービス・インスタンスをデプロイするための簡単な方法です。
{: shortdesc}

## DevOps ツールチェーンを使用したアプリのデプロイ
{: #toolchain-deploy-apps}

オープン・ツールチェーンは、{{site.data.keyword.Bluemix}} の Public 環境および Dedicated 環境で使用可能です。 適切に構成されたツールチェーンを使用すると、アプリのデプロイは簡単です。 リポジトリー内のマスター・ブランチへのマージが行われるたびに、ビルドとデプロイのサイクルが自動的に開始されます。

ツールチェーンは以下の方法で作成できます。
* アプリからツールチェーンを作成する。 詳しくは、[アプリのデプロイ](/docs/apps?topic=creating-apps-tutorial-scratch#deploy-scratch)を参照してください。
* テンプレートを使用してツールチェーンを作成する。 詳しくは、[ツールチェーンの作成](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)を参照してください。

## CLI を使用したアプリのデプロイ
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}} には、堅固な CLI と、CLI に統合されるプラグインおよび開発者ツール拡張機能が用意されています。

開始する前に、[{{site.data.keyword.cloud_notm}} CLI をダウンロードしてインストールします](/docs/cli?topic=cloud-cli-ibmcloud-cli)。

CLI は、Cygwin によってサポートされていません。 このツールは Cygwin コマンド・ライン・ウィンドウ以外のウィンドウで使用してください。
{: important}

  1. 開発環境をセットアップするため、アプリのコードを新規ディレクトリーにダウンロードします。

  2. コードが置かれているディレクトリーに移動します。

  3.  アプリ・コードを更新します。 例えば、{{site.data.keyword.cloud_notm}} サンプル・アプリケーションを使用していて、アプリに `src/main/webapp/index.html` ファイルが含まれている場合は、それを変更して「`Thanks for creating ...`」行を編集できます。 アプリを {{site.data.keyword.cloud_notm}} にデプロイする前に、ローカルで実行できることを確認してください。

    `manifest.yml` ファイルをメモします。 アプリを {{site.data.keyword.cloud_notm}} にデプロイする際、このファイルを使用してアプリケーションの URL、メモリー割り振り、インスタンス数、およびその他の重要なパラメーターを判別します。

    また、`README.md` ファイルも確認してください。このファイルには、ビルド手順などの詳細情報が含まれています。

    アプリケーションが Liberty アプリである場合、再度デプロイする前にビルドする必要があります。
    {: note}

  4. IBMid を使用して {{site.data.keyword.cloud_notm}} CLI にログインします。 複数のアカウントを持っている場合、使用するアカウントを選択するように求めるプロンプトが出されます。 `-r` フラグを使用して地域を指定していない場合、地域も選択しなければなりません。
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    資格情報が拒否された場合、統合 ID を使用している可能性があります。 フェデレーテッド ID を使用してログインするには、`--sso` フラグを使用します。 詳しくは、[フェデレーテッド ID を使用したログイン](/docs/iam/federated_id?topic=iam-federated_id#federated_id)を参照してください。
    {: tip}

  5. 新規ディレクトリーから、[`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) コマンドを使用して、アプリを {{site.data.keyword.cloud_notm}} にデプロイします。
    ```
    ibmcloud dev deploy <APP_NAME>
    ```
    {: codeblock}

  6. [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) コマンドを実行してアプリの URL を表示し、アプリにアクセスします。 次に、ブラウザーでその URL にアクセスします。
