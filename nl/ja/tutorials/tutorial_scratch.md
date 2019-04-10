---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-15"

keywords: apps, scratch, developer tools

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# アプリの最初からの作成
{: #tutorial-scratch}

サービスとランタイムを使用してカスタム・アプリケーションを最初から作成できます。 
{: shortdesc}

## 始める前に
{: #prereqs-scratch}

* [{{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli) をインストールします。これには Docker が含まれています。 
* Docker アカウントを作成して、Docker アプリを実行し、サインインします。 ビルド・コマンドが機能するためには、Docker が実行中でなければなりません。
* アプリを {{site.data.keyword.cfee_full}} にデプロイする計画の場合は、[{{site.data.keyword.cloud_notm}} アカウントを準備する](/docs/cloud-foundry?topic=cloud-foundry-prepare)必要があります。

## アプリの作成
{: #create-scratch}

1. [{{site.data.keyword.cloud_notm}} ダッシュボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}) で、「アプリ」ウィジェットの**「アプリの作成」**をクリックします。

  {{site.data.keyword.dev_console}}の[「スターター・キット」 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/developer/appservice/starter-kits/) ページから、カスタム・アプリケーションを作成することもできます。
  {: tip}

2. アプリの名前を入力します。 このチュートリアルでは、`CustomProject` と入力します。
3. 固有のホスト名 (例えば、`abc-devhost`) を入力します。ホスト名は、アプリの経路に使用されます。 例えば、`abc-devhost.mybluemix.net` です。
4. オプションで、アプリを分類するためのタグを指定できます。 詳しくは、『[タグの処理](/docs/resources?topic=resources-tag)』を参照してください。
5. ご使用の言語とフレームワークを選択します。 一部のスターター・キットは、1 つの言語でしか使用できない場合があります。
6. 価格プランを選択します。 このチュートリアルでは、無料オプションを使用できます。
7. **「作成」**をクリックします。

デフォルトの共有ドメインは `mybluemix.net` ですが、`appdomain.cloud` という別のドメインも選択できます。`appdomain.cloud` への移行について詳しくは、[ドメインの更新](/docs/apps/tutorials?topic=creating-apps-update-domain)を参照してください。
{: tip}

## サービスの追加 (オプション)
{: #resources-scratch}

Watson のコグニティブ機能でアプリを拡張するサービスを追加したり、モバイル・サービスやセキュリティー・サービスを追加したりできます。 このチュートリアルでは、データを管理する場所を追加することができます。

1. **アプリの詳細**ページで、**「サービスの追加」**をクリックします。
2. 必要なサービスの種類を選択します。 例えば、**「データ (Data)」**>**「次へ」**>**「Cloudant」**>**「次へ」**をクリックします。
3. 価格プランを選択します。 このチュートリアルでは、無料オプションを使用できます。
4. **「作成」**をクリックします。

## アプリのビルドおよびローカルでの実行
{: #build-run-scratch}

アプリをクラウドにデプロイする前に、テスト用にアプリをローカルでビルドすることもできます。

1. **「アプリの詳細」**ページで**「コードのダウンロード (Download code)」**または**「リポジトリーの複製 (Clone your repo)」**をクリックして、コードをローカルに処理します。
2. 統合開発環境にアプリをインポートします。
3. コードを変更します。
4. パーソナル・アクセス・トークンを追加して、[Git 認証](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication)をセットアップします。
5. {{site.data.keyword.cloud_notm}} コマンド・ライン・インターフェース (CLI) にログインします。 組織でフェデレーテッド・ログインを使用している場合は、`-sso` オプションを使用します。以下に例を示します。

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. 以下のコマンドを実行して、組織およびスペースのターゲットを設定します。

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. 以下のコマンドを実行して、資格情報を取得します。

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Docker が実行中であることを確認し、以下のコマンドを実行して、ディレクトリーからローカル開発コンテナー内にアプリをビルドします。

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. 以下のコマンドを実行して、ローカル開発コンテナーでアプリを実行します。

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. ご使用のブラウザーで `http://localhost:3000` にアクセスします。 ご使用のポート番号は、選択したランタイムによって異なる可能性があります。

## アプリのデプロイ
{: #deploy-scratch}

アプリはいくつかの方法で {{site.data.keyword.cloud_notm}} にデプロイできますが、DevOps ツールチェーンが、実動アプリをデプロイする場合に最適な方法です。 DevOps ツールチェーンを使用すると、多数の環境へのデプロイメントを簡単に自動化して、成長するアプリの管理に役立つモニタリング、ロギング、およびアラートの各サービスを素早く追加することができます。

ツールチェーンを有効にすると、アプリ用のチーム・ベースの開発環境が作成されます。 ツールチェーンの作成時に、アプリ・サービスによって Git リポジトリーが作成されます。このリポジトリーでは、ソース・コードの表示、アプリの複製、および問題の作成と管理を行うことができます。 また、専用の GitLab 環境と、継続的 Delivery Pipeline にアクセスすることもできます。 選択したデプロイメント環境が、[Kubernetes](/docs/containers?topic=containers-container_index)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about)、または[仮想サーバー (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers) のどれであっても、それに合わせてこれらはカスタマイズされています。

{{site.data.keyword.cloud_notm}} 開発者ダッシュボードから作成されたツールチェーンはすべて、自動デプロイメント用に構成されています。
{: note}

### DevOps ツールチェーンを使用した手動デプロイメント

正しく構成されたツールチェーンを使用すると、リポジトリー内のマスター・ブランチへのマージが行われるたびに、ビルドとデプロイのサイクルが自動的に開始されます。 

DevOps ツールチェーンからアプリを手動でデプロイすることもできます。

1. アプリの詳細ページで、**「ツールチェーンの表示」**をクリックします。
2. **「Delivery Pipeline」**をクリックします。ここで、ビルドの開始、デプロイメントの管理、およびログと履歴の表示を行うことができます。

一部のアプリケーションでは継続的デリバリーは有効になっています。 継続的デリバリーを有効にして、Delivery Pipeline と GitHub を使用したビルド、テスト、およびデプロイメントを自動化することができます。

詳しくは、以下を参照してください。
* [継続的デリバリーを使用したビルドおよびデプロイ](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)。
* [テンプレートからのツールチェーンの作成](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)。

### DevOps ツールチェーンを使用した自動デプロイメント

1. **「アプリの詳細」**ページで**「継続的デリバリーの構成 (Configure continuous delivery)」**をクリックします。
2. デプロイメント・ターゲットを選択します。 選択したターゲットの説明に従って、デプロイメント・ターゲットをセットアップします。
  * **IBM Kubernetes Service にデプロイします**。 このオプションは、高可用性のアプリケーション・コンテナーをデプロイして管理するためのワーカー・ノードというホスト・クラスターを作成します。 クラスターを作成したり、既存のクラスターにデプロイしたりすることができます。
  * **Cloud Foundry にデプロイ**します。 このオプションはクラウド・ネイティブなアプリをデプロイします。基礎にあるインフラストラクチャーを管理する必要はありません。 ご使用のアカウントに {{site.data.keyword.cfee_full_notm}} へのアクセス権限がある場合、デプロイヤー・タイプとして、**パブリック・クラウド**または**エンタープライズ環境**のいずれかを選択できます。エンタープライズ環境を使用すると、自社専用に Cloud Foundry アプリケーションをホスティングする隔離された環境を作成して管理できます。
  * **仮想サーバーにデプロイします**。 このオプションによって、仮想サーバー・インスタンスがプロビジョンされ、アプリを含むイメージがロードされ、DevOps ツールチェーンが作成され、最初のデプロイメント・サイクルが開始されます。

最後のステップでアプリをクラウドにデプロイすることで、ツールチェーンが自動的に作成されます。 ツールチェーンによってアプリ用の Git リポジトリーが作成され、ユーザーはそこでコードを見つけることができます。 

### {{site.data.keyword.dev_cli_short}} を使用したデプロイ
{: #deploy-scratch-cli}

アプリを Cloud Foundry にデプロイするには、以下のコマンドを入力します。
```
ibmcloud dev deploy
```
{: pre}

アプリを Kubernetes クラスターにデプロイするには、以下のコマンドを入力します。
```
ibmcloud dev deploy --target <container>
```
{: pre}

## アプリが実行中であることの確認
{: #verify-scratch}

アプリのデプロイ後に、Delivery Pipeline またはコマンド・ラインにアプリの URLが示されます。

1. DevOps ツールチェーンから、**「Delivery Pipeline」**をクリックし、**「デプロイ・ステージ」**を選択します。
2. **「ログおよび履歴の表示」**をクリックします。
3. ログ・ファイルで、アプリケーション URL を見つけます。

    ログ・ファイルの末尾で `urls` または `view` という語を探します。 例えば、`urls: my-app-devhost.mybluemix.net` または `View the application health at: http://<ipaddress>:<port>/health` のような行がログ・ファイル内で見つかります。

4. ご使用のブラウザーでその URL にアクセスします。 アプリが実行されている場合は、`Congratulations` または `{"status":"UP"}` を含むメッセージが表示されます。

コマンド・ラインを使用している場合は、[`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) コマンドを実行して、アプリの URL を表示します。 次に、ブラウザーでその URL にアクセスします。
