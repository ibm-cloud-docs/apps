---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# スターター・キットを使用したアプリの作成
{: #create_starterkit}

スターター・キットを使用して、アプリを素早く開始し、今後の開発に備えることができます。 スターター・キットとプログラミング言語を選択し、アプリを作成した後、自動的にアプリをデプロイするように DevOps ツールチェーンをセットアップします。 即時検査用のコードをダウンロードすることもできます。
{: shortdesc}

選択したスターター・キットからアプリを作成できます。ビルド・オプションを自分でカスタマイズする場合に使用できるブランクのスターター・キットもあります。いずれの方法でも、アプリをデプロイするための DevOps ツールチェーンが自動的に作成されます。即時検査用のコードをダウンロードすることもできます。

スターター・キットは、以下の多くのカテゴリーで使用可能です。
* [Watson ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/developer/watson/dashboard){:new_window}
* [Apple ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/developer/appledevelopment/dashboard){:new_window}
* [モバイル ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/developer/mobile/dashboard){:new_window}
* [Web App ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/developer/appservice/dashboard){:new_window}
* [Security ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/developer/security/dashboard){:new_window}
* [Finance ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/developer/finance/dashboard){:new_window}

## ステップ 1. アプリの作成
{: #create-app}

1. [{{site.data.keyword.cloud}} ダッシュボード](https://{DomainName})で、**「メニュー」**アイコン ![「メニュー」アイコン](../../icons/icon_hamburger.svg) > **「Web アプリ」**をクリックします。

2. **「Web から開始 (Start from the Web)」**セクションで**「開始」**をクリックします。

3. 任意のスターター・キットを選択し、詳細を読み、**「作成」**をクリックします。
    
    スターター・キットに含まれているものを表示するには、[アプリ・サービス・スターター・キット ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/developer/appservice/starter-kits){:new_window} ダッシュボード上のタイルを展開します。「アプリの作成」スターター・キット・オプションは、ブランクのスターター・アプリとして使用でき、ニーズに合わせてさらにカスタマイズできます。
    {: tip}

4. アプリに名前を付け、言語を選択して、**「作成」**をクリックします。
    
    素晴らしいスタートです。 これでアプリが作成されました。

コードを検査するには、アプリの詳細ページで**「コードのダウンロード (Download Code)」**をクリックします。 ダウンロードした圧縮ファイルの中の `README.md` ファイルを参照して、スターター・アプリを稼働状態にするためにさらに操作が必要かどうかを確認します。
{: tip}

詳しくは、[スターター・キットを使用した基本 Web アプリの作成](/docs/apps/tutorials/tutorial_web.html)を参照してください。

## ステップ 2. リソースの追加
{: #add-services}

Watson のコグニティブ機能でアプリを拡張するリソースを追加したり、モバイル・サービスやセキュリティー・サービスを追加したりできます。 このチュートリアルでは、データを管理する場所を追加します。

1. 「アプリ・サービス」ウィンドウで、**「リソースの追加」**をクリックします。
2. 必要なサービスの種類を選択します。 例えば、**「データ (Data)」**>**「次へ」**>**「Cloudant」**>**「次へ」**をクリックします。
3. 価格プランを選択します。 このチュートリアルでは無料オプションを使用できます。
4. **「作成」**をクリックします。

## ステップ 3. {{site.data.keyword.cloud_notm}} へのデプロイ
{: #deploy}

アプリの詳細ページで**「クラウドにデプロイ (Deploy to Cloud)」**をクリックし、デプロイメント方式 (例えば、Kubernetes クラスターや Cloud Foundry アプリ) を選択して、**「作成」**をクリックします。 {{site.data.keyword.cloud_notm}} は、Git リポジトリーと継続的デリバリー・パイプラインを備えたオープン・ツールチェーンを自動的に作成します。 新しいツールチェーンのパイプライン・コンポーネントを開いて、最初のビルドとデプロイのプロセスを開始すると、数分後には新しいアプリを確認できます。

コマンド・ラインを使用してアプリをデプロイするには、`ibmcloud dev deploy` を使用します。 詳しくは、[CLI を使用したアプリの作成およびデプロイ](/docs/apps/create-deploy-cli.html)を参照してください。
