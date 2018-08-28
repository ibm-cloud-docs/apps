---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-21"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 入門チュートリアル
{: #create}

{{site.data.keyword.Bluemix}} では、エンタープライズレベルのモバイル・アプリケーションおよび Web アプリケーションを作成し、{{site.data.keyword.Bluemix_notm}} でホストされているクラウド拡張機能を利用できます。 アプリを作成、実行、およびデプロイするには、{{site.data.keyword.Bluemix}} コンソールおよびコマンド・ライン・ツールを使用できます。 開始するには、プロセスを管理するスターター・キットを使用してアプリを作成するか、何が必要かがわかっている場合は必要なリソースを使用してアプリをビルドするかの 2 つの方法を使用します。
{:shortdesc}

スターター・キットを使用して、アプリを素早く開始し、今後の開発に備えることができます。 スターター・キットとプログラミング言語を選択し、アプリを作成した後、自動的にアプリをデプロイするように DevOps ツールチェーンをセットアップします。 即時検査用のコードをダウンロードすることもできます。

スターター・キットは、以下の多くのカテゴリーで使用可能です。

* [Watson ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/developer/watson/dashboard){:new_window}
* [Apple ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/developer/appledevelopment/dashboard){:new_window}
* [Mobile ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/developer/mobile/dashboard){:new_window}
* [Web App ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/developer/appservice/dashboard){:new_window}
* [Security ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/developer/security/dashboard){:new_window}
<!--* [Watson Data Platform developer console](https://console.bluemix.net/developer/dataplatform)-->
* [Finance ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net/developer/finance/dashboard){:new_window}

## 始める前に

{{site.data.keyword.cloud_notm}} アカウントの [登録![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://console.bluemix.net){: new_window} をしてください。 E メール、名前、会社、地域、電話番号を入力します。

無料アカウントの登録にクレジット・カードは必要ありません。 ただし、クレジット・カードを入力すると、より多くのリソースへのアクセスが可能になり、{{site.data.keyword.cloud_notm}} で提供されるすべてのものをより簡単に利用できます。

## ステップ 1. アプリの作成
{: #project}

1. **メニュー**・アイコン![メニュー・アイコン](../icons/icon_hamburger.svg) > **「Web アプリ」**をクリックします。

2. **「Web から開始 (Start from the Web)」**セクションで**「開始」**をクリックします。

3. 任意のスターター・キットを選択し、詳細を読み、**「作成」**をクリックします。

   スターター・キットに含まれる内容を表示するには、アプリ・サービス・スターター・キットのダッシュボード上のタイルを展開します。
   {: tip}

4. アプリに名前を付け、言語を選択して、**「作成」**をクリックします。

   素晴らしいスタートです。 これでアプリが作成されました。

   コードを検査するには、アプリの詳細ページで**「コードのダウンロード (Download Code)」**をクリックします。 ダウンロードした圧縮ファイルの中の `README.md` ファイルを参照して、スターター・アプリを稼働状態にするためにさらに操作が必要かどうかを確認します。
   {: tip}

## ステップ 2. リソースの追加
{: #addResources}

ほとんどのスターター・キットは、自動的にリソースをプロビジョンするよう {{site.data.keyword.cloud_notm}} に指示します。 アプリの詳細ページの**「リソースの追加」**をクリックして、さらにリソースをアプリに関連付けることもできます。

アプリをローカルで開発および実行するには、[{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html)を使用します。
{: tip}

## ステップ 3. アプリのデプロイ
{: #deploy}

アプリの詳細ページで**「クラウドにデプロイ (Deploy to Cloud)」**をクリックし、デプロイメント方式 (例えば、Kubernetes クラスターや Cloud Foundry アプリ) を選択して、**「作成」**をクリックします。 {{site.data.keyword.cloud_notm}} は、Git リポジトリーと継続的デリバリー・パイプラインを備えたオープン・ツールチェーンを自動的に作成します。 新しいツールチェーンのパイプライン・コンポーネントを開いて、最初のビルドとデプロイのプロセスを開始すると、数分後には新しいアプリを確認できます。

これで、反復型開発と継続的デリバリーのための設定ができました。
