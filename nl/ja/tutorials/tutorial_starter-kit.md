---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, starter kit

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# スターター・キットを使用したアプリの作成
{: #tutorial-starterkit}

スターター・キットを使用して、アプリを素早く開始し、今後の開発に備えることができます。 スターター・キットとプログラミング言語を選択し、アプリを作成した後、自動的にアプリをデプロイするように DevOps ツールチェーンをセットアップします。 即時検査用のコードをダウンロードすることもできます。
{: shortdesc}

選択したスターター・キットからアプリを作成できます。ビルド・オプションを自分でカスタマイズする場合に使用できるブランクのスターター・キットもあります。 いずれの方法でも、アプリをデプロイするための DevOps ツールチェーンが自動的に作成されます。 即時検査用のコードをダウンロードすることもできます。

スターター・キットは、以下の多くのカテゴリーで使用可能です。
* [Watson](https://{DomainName}/developer/watson/dashboard){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")
* [Apple](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")
* [モバイル](https://{DomainName}/developer/mobile/dashboard){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")
* [Web App ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")
* [セキュリティー](https://{DomainName}/developer/security/dashboard){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")
* [金融](https://{DomainName}/developer/finance/dashboard){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")

## ステップ 1. アプリの作成
{: #create-starterkit}

1. [{{site.data.keyword.cloud}} ダッシュボード](https://{DomainName}){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") から **「メニュー」**アイコン![「メニュー」アイコン](../../icons/icon_hamburger.svg) > **「Web アプリ」**を選択します。

2. **「Web から開始 (Start from the Web)」**セクションで**「開始」**をクリックします。

3. 任意のスターター・キットを選択し、詳細を読み、**「作成」**をクリックします。
    
    スターター・キットに含まれているものを表示するには、[アプリ・サービス・スターター・キット ](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") ダッシュボード上のタイルを展開します。 「アプリの作成」スターター・キット・オプションは、ブランクのスターター・アプリとして使用でき、ニーズに合わせてさらにカスタマイズできます。
    {: tip}

4. アプリに名前を付け、リソース・グループを選択し、オプションでタグを指定し、言語を選択し、**「作成」**をクリックします。
    
    素晴らしいスタートです。 これでアプリが作成されました。

コードを検査するには、**アプリの詳細**ページで**「コードのダウンロード (Download Code)」**をクリックします。 ダウンロードした圧縮ファイルの中の `README.md` ファイルを参照して、スターター・アプリを稼働状態にするためにさらに操作が必要かどうかを確認します。
{: tip}

詳しくは、以下のトピックを参照してください。
 * [スターター・キットを使用した基本 Web アプリの作成](/docs/apps/tutorials?topic=creating-apps-tutorial-webapp)
 * [タグの操作](/docs/resources?topic=resources-tag)

## ステップ 2. サービスの追加
{: #resources-starterkit}

Watson のコグニティブ機能でアプリを拡張するサービスを追加したり、モバイル・サービスやセキュリティー・サービスを追加したりできます。 このチュートリアルでは、データを管理する場所を追加します。

1. **アプリの詳細**ページで、**「サービスの追加」**をクリックします。
2. 必要なサービスの種類を選択します。 例えば、**「データ (Data)」**>**「次へ」**>**「Cloudant」**>**「次へ」**をクリックします。
3. 価格プランを選択します。 このチュートリアルでは無料オプションを使用できます。
4. **「作成」**をクリックします。

## ステップ 3. {{site.data.keyword.cloud_notm}} へのデプロイ
{: #deploy-starterkit}

**「アプリの詳細」**ページで**「継続的デリバリーの構成 (Configure continuous delivery)」**を選択し、デプロイメント・ターゲットを選択してから**「作成」**をクリックします。{{site.data.keyword.cloud_notm}} は、Git リポジトリーと継続的デリバリー・パイプラインを備えたオープン・ツールチェーンを自動的に作成します。

ツールチェーンを有効にすると、アプリ用のチーム・ベースの開発環境が作成されます。 ツールチェーンの作成時に、アプリ・サービスによって Git リポジトリーが作成されます。このリポジトリーでは、ソース・コードの表示、アプリの複製、および問題の作成と管理を行うことができます。 また、専用の GitLab 環境と、継続的 Delivery Pipeline にアクセスすることもできます。 選択したデプロイメント環境が、[Kubernetes](/docs/containers?topic=containers-container_index)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about)、または[仮想サーバー (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers) のどれであっても、それに合わせてこれらはカスタマイズされています。

開発環境を選択した後、新しいツールチェーンのパイプライン・コンポーネントを開いて、最初のビルドとデプロイメントのプロセスを開始すると、数分後には新しいアプリを確認できます。

{{site.data.keyword.cloud_notm}} 開発者ダッシュボードから作成されたツールチェーンはすべて、自動デプロイメント用に構成されています。
{: note}

コマンド・ラインを使用してアプリをデプロイするには、`ibmcloud dev deploy` を使用します。 詳しくは、[CLI を使用したアプリの作成およびデプロイ](/docs/apps?topic=creating-apps-create-deploy-app-cli)を参照してください。
