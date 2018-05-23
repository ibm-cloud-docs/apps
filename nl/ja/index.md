---

copyright:
  years: 2017, 2018
lastupdated: "2018-05-02"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 概説チュートリアル
{: #create}

{{site.data.keyword.Bluemix}} では、エンタープライズレベルのモバイル・アプリケーションおよび Web アプリケーションを作成し、{{site.data.keyword.Bluemix_notm}} でホストされているクラウド拡張機能を利用できます。 アプリを作成、実行、およびデプロイするには、{{site.data.keyword.Bluemix}} コンソールおよびコマンド・ライン・ツールを使用できます。 開始するには、プロセスを管理するスターター・キットを使用してアプリを作成するか、欲しいものが分かっている場合は必要なリソースを使用してアプリをビルドするかの 2 つの方法のいずれかを実行します。
{:shortdesc}

スターター・キットを使用して、アプリを素早く開始し、今後の開発に備えることができます。 スターター・キットとプログラミング言語を選択し、アプリを作成した後、自動的にアプリをデプロイするように DevOps ツールチェーンをセットアップします。即時検査用のコードをダウンロードすることもできます。

スターター・キットは、以下の多くのカテゴリーで使用可能です。

* [Watson](https://console.bluemix.net/developer/watson){:new_window}
* [Apple](https://console.bluemix.net/developer/appledevelopment){:new_window}
* [モバイル](https://console.bluemix.net/developer/mobile){:new_window}
* [Web アプリ](https://console.bluemix.net/developer/appservice){:new_window}
* [セキュリティー](https://console.bluemix.net/developer/security){:new_window}
<!--* [Watson Data Platform developer console](https://console.bluemix.net/developer/dataplatform)-->
* [金融](https://console.bluemix.net/developer/finance){:new_window}

## 始める前に

{{site.data.keyword.cloud_notm}} アカウントに[登録](https://console.bluemix.net){: new_window}します。 E メール、名前、会社、地域、電話番号を入力します。

無料アカウントの登録にクレジット・カードは必要ありませんが、クレジット・カードを入力すると、より多くのリソースへのアクセスが可能になり、{{site.data.keyword.cloud_notm}} で提供されるすべてのものを十分に理解しやすくなります。

## ステップ 1: アプリの作成
{: #project}

1. **メニュー**・アイコン![メニュー・アイコン](../icons/icon_hamburger.svg) > **「Web アプリ」**をクリックします。

2. **「Web から開始 (Start from the Web)」**セクションで**「開始」**をクリックします。

3. 任意のスターター・キットを選択し、詳細を読み、**「作成」**をクリックします。

  スターター・キットに含まれる内容を表示するには、アプリ・サービス・スターター・キットのダッシュボード上のタイルを展開します。
  {: tip}

4. アプリに名前を付け、言語を選択して、**「作成」**をクリックします。

素晴らしいスタートです。 これでアプリが作成されました。

コードを検査するには、アプリの詳細ページで**「コードのダウンロード (Download Code)」**をクリックします。 ダウンロードした圧縮ファイルの中の `README.md` を参照して、スターター・アプリを実行するためにさらに操作が必要かどうかを確認します。
{: tip}

## ステップ 2: リソースの追加
{: #addResources}

ほとんどのスターター・キットは、自動的にリソースをプロビジョンするよう {{site.data.keyword.cloud_notm}} に指示します。 アプリの詳細ページの**「リソースの追加」**をクリックして、さらにリソースをアプリに関連付けることもできます。

アプリをローカルで開発および実行するには、[{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html)を使用します。
{: tip}

## ステップ 3: {{site.data.keyword.cloud_notm}} へのデプロイ
{: #deploy}

アプリの詳細ページで**「クラウドにデプロイ (Deploy to Cloud)」**をクリックし、デプロイメント方式 (例えば、Kubernetes クラスターや Cloud Foundry アプリ) を選択して、**「作成」**をクリックします。 {{site.data.keyword.cloud_notm}} は、Git リポジトリーと継続的なデリバリー・パイプラインを備えたオープン・ツールチェーンを自動的に作成します。 新しいツールチェーンのパイプライン・コンポーネントを表示して最初のビルドとデプロイのプロセスを開始すると、数分後には新しいアプリが実行されているのを見ることができます。

これで、反復型開発と継続的デリバリーのための設定ができました。
