---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# スターター・キットを使用した基本 Web アプリの作成
{: #tutorial-webapp}

{{site.data.keyword.cloud}} は、素早くコーディングするために役立つ多数のスターター・キットを提供します。 事前構成されたカスタム・アプリの操作を開始するには、アプリ・サービスの「スターター・キット」から言語、フレームワーク、およびツールを選択します。 このチュートリアルでは、必要なツールをインストールしてから、アプリをローカルでビルドして実行し、クラウドにデプロイするためのステップを実行します。
{: shortdesc}

## ステップ 1. ツールのインストール
{: #prereqs-webapp}

[開発者ツール](/docs/cli/index.html#overview)をインストールします。

Docker は開発者ツールの一部としてインストールされます。 ビルド・コマンドが機能するためには、Docker が実行中でなければなりません。 Docker アカウントを作成して、Docker アプリを実行し、サインインする必要があります。

## ステップ 2. スターター・キットの選択
{: #create-webapp}

スターター・キットは、{{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}で多数の言語とフレームワークで使用可能です。 ご使用のプロジェクトを開始するのに最適な言語を選択してください。

1. {{site.data.keyword.dev_console}}の[「スターター・キット」![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/developer/appservice/starter-kits/) ページから、ご使用の言語に対応するスターター・キットを選択します。
2. アプリ名と固有のホスト名 (例えば、`abc-devhost`) を入力します。このホスト名は、アプリの経路 `abc-devhost.cloud.ibm.com` です。
3. オプション。 アプリを分類するためのタグを指定します。詳しくは、『[タグの処理](/docs/resources/tagging_resources.html#tag)』を参照してください。
4. ご使用の言語とフレームワークを選択します。 一部のスターター・キットは、1 つの言語でしか使用できない場合があります。
5. 価格プランを選択します。 このチュートリアルでは無料オプションを使用できます。
6. **「作成」**をクリックします。

## ステップ 3. リソースの追加 (オプション)
{: #resources-webapp}

Watson のコグニティブ機能でアプリを拡張するリソースを追加したり、モバイル・サービスやセキュリティー・サービスを追加したりできます。 このチュートリアルでは、データを管理する場所を追加します。

1. 「アプリ・サービス」ウィンドウで、**「リソースの追加」**をクリックします。
2. 必要なサービスの種類を選択します。 例えば、**「データ (Data)」**>**「次へ」**>**「Cloudant」**>**「次へ」**をクリックします。
3. 価格プランを選択します。 このチュートリアルでは無料オプションを使用できます。
4. **「作成」**をクリックします。

## ステップ 4. DevOps ツールチェーンの作成
{: #toolchain-webapp}

ツールチェーンを有効にすると、アプリ用のチーム・ベースの開発環境が作成されます。 ツールチェーンの作成時に、アプリ・サービスによって Git リポジトリーが作成されます。このリポジトリーでは、ソース・コードの表示、アプリの複製、および問題の作成と管理を行うことができます。 また、専用の GitLab 環境と、継続的 Delivery Pipeline にアクセスすることもできます。 選択したデプロイメント環境が、[Kubernetes](/docs/containers/container_index.html#container_index)、[Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about)、または[仮想サーバー (VSI)](/docs/vsi/vsi_index.html) のどれであっても、それに合わせてこれらはカスタマイズされています。

一部のアプリケーションでは継続的デリバリーは有効になっています。 継続的デリバリーを有効にして、Delivery Pipeline と GitHub を使用したビルド、テスト、およびデプロイメントを自動化することができます。

アプリの詳細ページで**「クラウドにデプロイ」**をクリックし、デプロイメント環境を選択して、**「作成」**をクリックします。 {{site.data.keyword.cloud_notm}} は、Git リポジトリーと継続的デリバリー・パイプラインを備えたオープン・ツールチェーンを自動的に作成します。

開発環境を選択した後、新しいツールチェーンのパイプライン・コンポーネントを開いて、最初のビルドとデプロイメントのプロセスを開始すると、数分後には新しいアプリを確認できます。

詳しくは、[ツールチェーンの作成](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started)を参照してください。

## ステップ 5. アプリのビルドおよびローカルでの実行
{: #build-run-webapp}

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

7. 資格情報を取得します。

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

10. ご使用のブラウザーで `http://localhost:3000` を開きます。 ご使用のポート番号は、選択したランタイムによって異なる可能性があります。

## ステップ 6. アプリのデプロイ
{: #deploy-webapp}

### ツールチェーンを使用したデプロイ
{: #deploy-webapp-toolchain}

アプリはいくつかの方法で {{site.data.keyword.cloud_notm}} にデプロイできますが、DevOps ツールチェーンが、実動アプリをデプロイする場合に最適な方法です。 DevOps ツールチェーンを使用すると、多数の環境へのデプロイメントを簡単に自動化して、成長するアプリの管理に役立つモニタリング、ロギング、およびアラートの各サービスを素早く追加することができます。

正しく構成されたツールチェーンを使用すると、リポジトリー内のマスター・ブランチへのマージが行われるたびに、ビルドとデプロイのサイクルが自動的に開始されます。 {{site.data.keyword.cloud_notm}} 開発者ダッシュボードから作成されたツールチェーンはすべて、自動デプロイメント用に構成されています。

DevOps ツールチェーンからアプリを手動でデプロイすることもできます。

1. 「アプリ詳細」ウィンドウから、**「ツールチェーンの表示」**をクリックします。
2. **「Delivery Pipeline」**をクリックします。ここで、ビルドの開始、デプロイメントの管理、およびログと履歴の表示を行うことができます。

詳しくは、[ビルドとデプロイ](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy)を参照してください。

### {{site.data.keyword.dev_cli_short}} を使用したデプロイ
{: #deploy-webapp-cli}

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
{: #verify-webapp}

アプリのデプロイ後に、Delivery Pipeline またはコマンド・ラインにアプリの URLが示されます。

1. DevOps ツールチェーンから、**「Delivery Pipeline」**をクリックし、**「デプロイ・ステージ」**を選択します。
2. **「ログおよび履歴の表示」**をクリックします。
3. ログ・ファイルで、アプリケーション URL を見つけます。

    ログ・ファイルの末尾で `urls` または `view` という語を探します。例えば、`urls: my-app-devhost.cloud.ibm.com` または `View the application health at: http://<ipaddress>:<port>/health` のような行がログ・ファイル内で見つかります。

4. ご使用のブラウザーでその URL にアクセスします。 アプリが実行されている場合は、`Congratulations` または `{"status":"UP"}` を含むメッセージが表示されます。

コマンド・ラインを使用している場合は、[`ibmcloud dev view`](/docs/cli/idt/commands.html#view) コマンドを実行して、アプリの URL を表示します。次に、ブラウザーでその URL にアクセスします。
