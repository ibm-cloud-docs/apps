---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-07"

keywords: apps, serverless, serverless app, functions, cli, api, sdk, create serverless app, serverless app tutorial

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# サーバーレス・アプリの作成
{: #serverless}

サーバーレス開発では、IBM の Functions as a Service (FaaS) オファリングである {{site.data.keyword.openwhisk}} を使用できます。 サーバーをプロビジョンしたり管理したりすることなく、HTTP を介した Web アプリやモバイル・アプリからのイベントまたは直接呼び出しに応答して、{{site.data.keyword.openwhisk_short}} を使用してアプリケーション・ロジックを実行できます。{{site.data.keyword.openwhisk_short}} は、開発者がアプリケーション・ロジックの作成に集中できるように、自動スケーリング、可用性管理、保守などのシステム管理を実行します。
{:shortdesc}

{{site.data.keyword.openwhisk_short}} ユーザー・インターフェース (UI) やコマンド・ライン・インターフェース (CLI) を使用して、アプリケーションを開発できます。 どちらも、類似したアプリケーション開発機能を備えています。 CLI の方が、デプロイメントおよび操作をより詳細に制御できます。 {{site.data.keyword.openwhisk_short}} について詳しくは、[資料](/docs/openwhisk?topic=cloud-functions-getting_started)で確認してください。

## {{site.data.keyword.openwhisk_short}} UI
{: #serverless-apps-ui}

ご使用の[ブラウザー ](https://{DomainName}/openwhisk/actions){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") で {{site.data.keyword.openwhisk_short}} を試してください。 {{site.data.keyword.openwhisk_short}} ユーザー・インターフェースのクイック・ツアーについては、[概念 (Concepts) ](https://{DomainName}/openwhisk/learn){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") のページに移動します。

## CLI を使用した開発
{: #openwhisk_start_configure_cli}

{{site.data.keyword.openwhisk_short}} CLI を使用したインストールと開発について詳しくは、[{{site.data.keyword.openwhisk_short}} CLI のセットアップ (Setting up the OpenWhisk CLI)](https://{DomainName}/openwhisk/cli){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") を参照してください。

## Web アクションとしての API およびデータ・セットの公開
{: #expose-actions}

デフォルトでは、{{site.data.keyword.openwhisk_short}} は、認証鍵を必要とするアクションを定義します。 モバイルの実稼働環境では多くの場合、API と特定のデータ・セットを公開するために、OAuth フローに基づいてモバイル・クライアントを許可する必要があります。

{{site.data.keyword.openwhisk_short}} では、開発者は、Web ベースのアプリケーションを迅速にビルドするために、注釈が付けられる Web アクションとして関数を公開できます。 {{site.data.keyword.openwhisk_short}} 認証鍵を使用せずにWeb アプリケーションが匿名でアクセスできる注釈付きのアクションを使用して、バックエンド・ロジックをプログラムすることができます。

アクションを Web アクションとして公開するには、アクションの**「エンドポイント」**タブに移動して、**「Web アクションとして有効化」**を選択します。

これで、ユーザーはブラウザーまたは以下の例のような cURL 要求からアクションに到達できるようになります。
```
curl https://openwhisk.cloud.ibm.com/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

出力:
```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} は、モバイル・アプリが簡単にリモート・トリガーを送信してリモート・アクションを起動できるようにする、iOS デバイスおよび watchOS デバイス用の[モバイル SDK](/docs/openwhisk?topic=cloud-functions-openwhisk_mobile_sdk) を提供します。
