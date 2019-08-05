---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-29"

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

サーバーレス開発では、IBM の Functions which is Service (FaaS) オファリングである {{site.data.keyword.openwhisk}} を使用できます。サーバーをプロビジョニングしたり管理したりすることなく、HTTP を介した Web アプリやモバイル・アプリからのイベントまたは直接呼び出しに応答して、{{site.data.keyword.openwhisk_short}} を使用してアプリ・ロジックを実行できます。
{{site.data.keyword.openwhisk_short}} は、開発者がアプリケーション・ロジックの作成に集中できるように、自動スケーリング、可用性管理、保守などのシステム管理を実行します。{:shortdesc}

以下のいずれかの方法を使用して、サーバーレス・アプリを開発することができます。
* {{site.data.keyword.openwhisk_short}} ユーザー・インターフェース (UI)。
* {{site.data.keyword.openwhisk_short}} コマンド・ライン・インターフェース (CLI)。CLI では、デプロイメントおよび操作をより詳細に制御できます。
* {{site.data.keyword.openwhisk_short}} スターター・キット。スターター・キットでは、DevOps ツールチェーンと Delivery Pipeline を使用して継続的デリバリーを設定できます。

{{site.data.keyword.openwhisk_short}} について詳しくは、[資料](/docs/openwhisk?topic=cloud-functions-getting_started)で確認してください。


## {{site.data.keyword.openwhisk_short}} UI による開発
{: #serverless-apps-ui}

ご使用の[ブラウザー ](https://{DomainName}/functions/actions){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") で {{site.data.keyword.openwhisk_short}} を試してください。 {{site.data.keyword.openwhisk_short}} ユーザー・インターフェースのクイック・ツアーについては、[概念 (Concepts) ](https://{DomainName}/functions/learn){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") のページに移動します。

## CLI を使用した開発
{: #openwhisk_start_configure_cli}

{{site.data.keyword.openwhisk_short}} CLI を使用したインストールと開発について詳しくは、[{{site.data.keyword.openwhisk_short}} CLI のセットアップ (Setting up the OpenWhisk CLI)](https://{DomainName}/functions/cli){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") を参照してください。

## Web アクションとしての API およびデータ・セットの公開
{: #expose-actions}

デフォルトでは、{{site.data.keyword.openwhisk_short}} は、認証鍵を必要とするアクションを定義します。 モバイルの実稼働環境では多くの場合、API と特定のデータ・セットを公開するために、OAuth フローに基づいてモバイル・クライアントを許可する必要があります。

{{site.data.keyword.openwhisk_short}} では、開発者は、Web ベースのアプリを迅速にビルドするために、注釈が付けられる Web アクションとして関数を公開できます。 {{site.data.keyword.openwhisk_short}} 認証鍵を使用せずにWeb アプリが匿名でアクセスできる注釈付きのアクションを使用して、バックエンド・ロジックをプログラムすることができます。

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

{{site.data.keyword.openwhisk_short}} は、モバイル・アプリが簡単にリモート・トリガーを送信してリモート・アクションを起動できるようにする、iOS デバイスおよび watchOS デバイス用の[モバイル SDK](/docs/openwhisk?topic=cloud-functions-pkg_mobile_sdk) を提供します。

## スターター・キットを使用したサーバーレス・アプリの作成
{: #serverless-starter}

スターター・キットを使用して、Python Example Serverless App などのサーバーレス・アプリを作成することができます。スターター・キットを見つけるには、以下の手順を実行します。

1. {{site.data.keyword.dev_console}} コンソールの[「アプリ・サービス・スターター・キット」](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") ページに移動します。 
2. 検索バーに `serverless` と入力して、スターター・キットのリストにフィルターを掛けます。
3. Python Example Serverless App などのサーバーレス・スターター・キットを選択します。
4. アプリに名前を付け、リソース・グループを選択します。
5. オプション。 アプリを分類するためのタグを指定します。 詳しくは、『[タグの処理](/docs/resources?topic=resources-tag)』を参照してください。
6. Cloudant サービス・インスタンスを作成するか、既存のものを選択します。
7. オプション。 サービスの追加やアプリのデプロイを行う前にコードを検査するには、**「ソース・コードの表示 (View source code)」**をクリックします。`README.md` ファイルを参照して、アプリを稼働状態にするためにさらに操作が必要かどうかを確認します。
  
8. **「作成」**をクリックします。

素晴らしいスタートです。 これでアプリが作成されました。

## サービスの追加 (オプション)
{: #serverless-services}

スターター・キットで特定のサービスが必要な場合は、自動的にプロビジョンされたサービスを使用することにより、アプリの作成時にこれらのサービスのインスタンスが自動的に作成されます。

1. 「アプリの詳細」ページで、このアプリに接続するサービスの有無に応じて、**「サービスの作成」**または**「既存のサービスの接続 (Connect existing services)」**をクリックします。
2. 必要なサービスの種類を選択し、プロンプトに従って、アプリに既存のサービスを追加するか、サービス・インスタンスを作成します。

必要なサービスをすべて追加すると、それらが「アプリの詳細」ページに表示されます。

## アプリのデプロイ
{: #serverless-deploy}

アプリをデプロイするには、以下の手順を実行します。

1. 「アプリの詳細」ページで、**「デプロイ」**をクリックします。
2. **「Cloud Functions にデプロイ」**を選択し、**「次へ」**をクリックします。
3. 「ツールチェーンの構成」ページで、ツールチェーン名を入力し、地域を選択し、**「作成」**をクリックします。デプロイメント・ターゲットを選択して構成すると、「アプリの詳細」ページに、継続的デリバリーが構成されたことが表示されます。 
4. オプション。 {{site.data.keyword.openwhisk_short}} コンソールでアクションを確認するには、「アクション」アイコン![「その他のアクション」アイコン](../icons/action-menu-icon.svg)をクリックして、**「Cloud Functions を開く (Open Cloud Functions)」**を選択します。
5. オプション。 **「リポジトリーの表示」**をクリックすると、アプリ用に生成されたコードを含むリポジトリーを表示できます。

## アプリがデプロイ済みであることの確認
{: #serverless-verify}

正しく構成されたツールチェーンを使用すると、リポジトリー内のマスター・ブランチへのマージが行われるたびに、ビルドとデプロイのサイクルが自動的に開始されます。 詳しくは、[ビルドとデプロイ](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)を参照してください。

アプリが正常にデプロイされたことを検証するには、以下の手順を実行します。

1. 「アプリの詳細」ページで、**「ツールチェーンの表示」**をクリックします。
2. **「Delivery Pipeline」**をクリックします。ここで、ビルドの開始、デプロイメントの管理、およびログと履歴の表示を行うことができます。
3. デプロイメントに成功した場合、各パイプライン・ステージに**「ステージは成功」**と表示されます。
4. アクションおよび API 情報を表示するには、**「デプロイ・ステージ」**タイルで**「ログおよび履歴の表示」**をクリックします。
