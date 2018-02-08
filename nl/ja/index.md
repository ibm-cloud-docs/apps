---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# {{site.data.keyword.Bluemix_notm}} でのアプリの作成
{: #create}

{{site.data.keyword.Bluemix}} では、エンタープライズレベルのモバイル・アプリケーションおよび Web アプリケーションを作成し、{{site.data.keyword.Bluemix_notm}} でホストされているクラウド拡張機能を利用できます。アプリを作成、実行、およびデプロイするには、{{site.data.keyword.Bluemix}} コンソールおよびコマンド・ライン・ツールを使用できます。このエンドツーエンド開発シナリオに従って作業を開始してください。

## ステップ 1: {{site.data.keyword.Bluemix_notm}} アカウントの登録
{: #sign-up}

[bluemix.net](bluemix.net) にアクセスします。E メール、名前、会社、地域、電話番号を入力すれば完了です。無料アカウントの登録では、クレジット・カードは必要ありません。ご自由にお試しください。

## ステップ 2: カタログの確認
{: #catalog}

{{site.data.keyword.Bluemix_notm}} カタログには、提供されているインフラストラクチャーおよびプラットフォームのリソースがリストされています。仮想マシン、コンテナー、または Cloudant、および Cloud Foundry アプリを選択して、自分のアプリの作成を開始できます。プラットフォーム・リソースが必要な場合、{{site.data.keyword.Bluemix_notm}} には、作成の開始を支援するためのランタイムやその他のサービスを提供するボイラープレートも用意されています。

## ステップ 3: リソースの作成
{: #resource}

1. [ダッシュボード](https://console.bluemix.net/dashboard/apps/)で**「リソースの作成」**をクリックします。

2. カタログで、「プラットフォーム」セクションからアプリを選択します。次にランタイムを選択します。例えば、IBM ビルドパックによってサポートされている、Liberty for Java などの IBM ランタイム環境を選択できます。また、オープン・ソースとサード・パーティーのビルドパックに依存する、Tomcat などのコミュニティー・ランタイムも選択できます。

  * [コンテナーの概説](../containers/container_index.html)
  * [Openwhisk の概説](../openwhisk/index.html)
  * [Cloud Foundry アプリの作成](../cfapps/index.html#creating_cloud_foundry_apps)

3. アプリ名とホスト名を入力し、価格設定プランを選択します。

4. 開発スタイルを選択します。好みのテキスト・エディターでアプリを編集し、{{site.data.keyword.Bluemix_notm}} コマンド・ラインを使用してそのアプリを {{site.data.keyword.Bluemix_notm}} にデプロイできます。また、{{site.data.keyword.Bluemix_notm}} DevOps Services を使用してブラウザーからアプリケーションをデプロイしたり、Eclipse Tools for {{site.data.keyword.Bluemix_notm}} を使用して Eclipse 統合開発環境でアプリケーションの作業を行うこともできます。

## ステップ 4: コードの追加の開始
{: #code}

各アプリには、作業を開始するために必要なすべてのソフトウェアとコンテンツの取得に役立つ「開始」セクションが備えられています。

ダッシュボードでアプリをクリックし、次に**「開始」**をクリックします。これは、アプリの開発に必要なソフトウェアの取得を助け、ソース・コードを示し、ユーザーが初めてアプリをデプロイするのを支援します。

## 次のステップ
{: #next}

アプリが開発されたら、[ベスト・プラクティス](best-practice.html)と[クラウド対応](cloud-ready.html)のガイドを使用して、アプリの {{site.data.keyword.Bluemix_notm}} へのデプロイ準備ができていることを確認してください。その後にアプリを[デプロイ](../starters/install_cli.html)します。
