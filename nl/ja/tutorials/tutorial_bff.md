---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# backend-for-frontend アプリ の作成
{: #tutorial-bff}

backend-for-frontend スターターからアプリを作成できます。 これらのスターターを使用して、Express.js、MicroProfile/ Java&reg EE、Kitura、Spring などのさまざまなフレームワークによって、Node.js、Java&reg、または Swift で backend-for-frontend アプリをビルドできます。必要なツールをインストールして、アプリをビルドしてローカルで実行し、クラウドにデプロイする方法を確認できます。
{: shortdesc}

## ステップ 1. 始める前に
{: #prereqs-bff}

* [開発者ツール](/docs/cli/index.html#overview)をインストールします。
* Docker は開発者ツールの一部としてインストールされます。 ビルド・コマンドが機能するためには、Docker が実行中でなければなりません。 Docker アカウントを作成して、Docker アプリを実行し、サインインする必要があります。
* アプリを [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about) にデプロイする予定の場合、[{{site.data.keyword.cloud_notm}} アカウントを準備](/docs/cloud-foundry/prepare-account.html#prepare)する必要があります。

## ステップ 2. アプリの作成
{: #create-bff}

{{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}でアプリを作成します。

1. {{site.data.keyword.dev_console}}の[「スターター・キット」![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/developer/appservice/starter-kits/) ページから、ご使用の言語に対応するスターター・キットを選択します。 例えば、Node.js アプリケーションの場合は、**「Express.js バックエンド (Express.js Backend)」**に移動し、**「スターター・キットの選択」**をクリックします。
2. アプリ名を入力します。 このチュートリアルでは、`ExpressBackend` を使用します。
3. 固有のホスト名 (例えば、`abc-devhost`) を入力します。このホスト名は、アプリの経路 `abc-devhost.cloud.ibm.com` です。
4. オプション。 アプリを分類するためのタグを指定します。詳しくは、『[タグの処理](/docs/resources/tagging_resources.html#tag)』を参照してください。
5. ご使用の言語とフレームワークを選択します。 一部のスターター・キットは、1 つの言語でしか使用できない場合があります。
6. 価格プランを選択します。 このチュートリアルでは無料オプションを使用できます。
7. **「作成」**をクリックします。

## ステップ 3. リソースの追加 (オプション)
{: #resources-bff}

Watson のコグニティブ機能でアプリを拡張するリソースを追加したり、モバイル・サービスやセキュリティー・サービスを追加したりできます。 このチュートリアルでは、データを管理する場所を追加します。

1. 「アプリ・サービス」ウィンドウで、**「リソースの追加」**をクリックします。
2. 必要なサービスの種類を選択します。 例えば、**「データ (Data)」**>**「次へ」**>**「Cloudant」**>**「次へ」**をクリックします。
3. 価格プランを選択します。 このチュートリアルでは無料オプションを使用できます。
4. **「作成」**をクリックします。

## ステップ 4. DevOps ツールチェーンの作成
{: #toolchain-bff}

ツールチェーンを有効にすると、アプリ用のチーム・ベースの開発環境が作成されます。 ツールチェーンの作成時に、アプリ・サービスによって Git リポジトリーが作成されます。このリポジトリーでは、ソース・コードの表示、アプリの複製、および問題の作成と管理を行うことができます。 また、専用の GitLab 環境と、継続的 Delivery Pipeline にアクセスすることもできます。 選択したデプロイメント環境が、[Kubernetes](/docs/containers/container_index.html#container_index)、[Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about)、または[仮想サーバー (VSI)](/docs/vsi/vsi_index.html) のどれであっても、それに合わせてこれらはカスタマイズされています。

{{site.data.keyword.cloud_notm}} 開発者ダッシュボードから作成されたツールチェーンはすべて、自動デプロイメント用に構成されています。
{: note}

1. アプリの詳細ページで、**「クラウドにデプロイ (Deploy to Cloud)」**をクリックします。
2. デプロイメント方式を選択します。 選択した方式の説明に従って、デプロイメント方式をセットアップします。
  * **[Kubernetes](/docs/apps/deploying/containers.html#containers) にデプロイ**します。このオプションは、高可用性のアプリケーション・コンテナーをデプロイして管理するためのワーカー・ノードというホスト・クラスターを作成します。 クラスターを作成したり、既存のクラスターにデプロイしたりすることができます。
  * **Cloud Foundry にデプロイ**します。 このオプションはクラウド・ネイティブなアプリをデプロイします。基礎にあるインフラストラクチャーを管理する必要はありません。ご使用のアカウントに {{site.data.keyword.cfee_full_notm}} へのアクセス権限がある場合、デプロイヤー・タイプとして、**[パブリック・クラウド](/docs/cloud-foundry-public/about-cf.html#about-cf)**または**[エンタープライズ環境](/docs/cloud-foundry-public/cfee.html#cfee)**のいずれかを選択できます。エンタープライズ環境を使用すると、自社専用に Cloud Foundry アプリケーションをホスティングする隔離された環境を作成して管理できます。
  * **[仮想サーバー](/docs/apps/vsi-deploy.html#vsi-deploy)にデプロイします**。 このオプションによって、仮想サーバー・インスタンスがプロビジョンされ、アプリを含むイメージがロードされ、DevOps ツールチェーンが作成され、最初のデプロイメント・サイクルが開始されます。

## ステップ 5. アプリのビルドおよびローカルでの実行
{: #build-run-bff}

最後のステップでアプリをクラウドにデプロイしたときに、ツールチェーンが作成されています。 ツールチェーンは、アプリ用の Git リポジトリーを作成します。このリポジトリーで、コードを見つけることができます。 リポジトリーにアクセスするには、次のステップに従います。 アプリをクラウドにプッシュする前に、アプリをテスト用にローカルでビルドすることができます。

1. 「アプリ・サービス」ウィンドウで、**「コードのダウンロード (Download Code)」**または**「リポジトリーの複製 (Clone your repo)」**をクリックして、コードをローカルで処理します。
2. 統合開発環境にアプリをインポートします。
3. コードを変更します。
4. パーソナル・アクセス・トークンを追加して、[Git 認証](/docs/services/ContinuousDelivery/git_working.html#git_authentication)をセットアップします。
5. {{site.data.keyword.cloud_notm}} コマンド・ライン・インターフェースにログインします。 組織でフェデレーテッド・ログインを使用している場合は、`-sso` オプションを使用します。

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. 組織とスペースのターゲットを設定します。

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7.  資格情報を取得します。

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Docker が実行中であることを確認して、ディレクトリーからローカル開発コンテナーでアプリをビルドします。

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. ローカル開発コンテナーでアプリを実行します。

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10.  ご使用のブラウザーで `http://localhost:3000` を開きます。 ご使用のポート番号は、選択したランタイムによって異なる可能性があります。

## ステップ 6. アプリのデプロイ
{: #deploy-bff}

### ツールチェーンを使用したデプロイ
{: #deploy-bff-toolchain}

アプリはいくつかの方法で {{site.data.keyword.cloud_notm}} にデプロイできますが、DevOps ツールチェーンが、実動アプリをデプロイする場合に最適な方法です。 DevOps ツールチェーンを使用すると、多数の環境へのデプロイメントを簡単に自動化して、成長するアプリの管理に役立つモニタリング、ロギング、およびアラートの各サービスを素早く追加することができます。

正しく構成されたツールチェーンを使用すると、リポジトリー内のマスター・ブランチへのマージが行われるたびに、ビルドとデプロイのサイクルが自動的に開始されます。 {{site.data.keyword.cloud_notm}} 開発者ダッシュボードから作成されたツールチェーンはすべて、自動デプロイメント用に構成されています。

DevOps ツールチェーンからアプリを手動でデプロイすることもできます。

1. 「アプリ詳細」ウィンドウから、**「ツールチェーンの表示」**をクリックします。

2. **「Delivery Pipeline」**をクリックします。ここで、ビルドの開始、デプロイメントの管理、およびログと履歴の表示を行うことができます。

### {{site.data.keyword.dev_cli_short}} を使用したデプロイ
{: #deploy-bff-cli}

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

## ステップ 7. アプリが実行中であることの確認
{: #verify-bff}

アプリのデプロイ後に、Delivery Pipeline またはコマンド・ラインにアプリの URLが示されます。

1. DevOps ツールチェーンから、**「Delivery Pipeline」**をクリックし、**「デプロイ・ステージ」**を選択します。
2. **「ログおよび履歴の表示」**をクリックします。
3. ログ・ファイルで、アプリケーション URL を見つけます。

    ログ・ファイルの末尾で `urls` または `view` という語を探します。例えば、`urls: my-app-devhost.cloud.ibm.com` または `View the application health at: http://<ipaddress>:<port>/health` のような行がログ・ファイル内で見つかります。

4. ご使用のブラウザーでその URL にアクセスします。 アプリが実行されている場合は、`Congratulations` または `{"status":"UP"}` を含むメッセージが表示されます。

コマンド・ラインを使用している場合は、[`ibmcloud dev view`](/docs/cli/idt/commands.html#view) コマンドを実行して、アプリの URL を表示します。次に、ブラウザーでその URL にアクセスします。
