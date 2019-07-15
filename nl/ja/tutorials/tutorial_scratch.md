---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-20"

keywords: scratch, developer tools, custom app, app tutorial, basic starter kit, language, backend, mobile

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# 基本スターター・キットからのカスタム・アプリの作成
{: #tutorial-scratch}

基本スターター・キットを使用すれば、アプリ・タイプ (モバイルまたはバックエンド)、言語、フレームワークを選択し、サービスを追加し、デプロイメント・ターゲットを選択することで、カスタム・アプリケーションを作成できます。
{: shortdesc}

基本スターター・キットは汎用性のあるツールです。これを使用すると、言語、アプリ・タイプ、フレームワーク、およびサービスに応じて定義したカスタム・アプリを作成することができます。その後、継続的デリバリーをセットアップし、任意のデプロイメント・ターゲットを選択します。

## 始める前に
{: #prereqs-scratch}

* [{{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-getting-started) をインストールします。これには Docker が含まれています。 
* Docker アカウントを作成して、Docker アプリを実行し、サインインします。 ビルド・コマンドが機能するためには、Docker が実行中でなければなりません。
* アプリを {{site.data.keyword.cfee_full}} にデプロイする計画の場合は、[{{site.data.keyword.cloud_notm}} アカウントを準備する](/docs/cloud-foundry?topic=cloud-foundry-prepare)必要があります。

## アプリの作成
{: #create-scratch}

1. [{{site.data.keyword.cloud_notm}} ダッシュボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}) で、「アプリ」ウィジェットの**「アプリの作成」**をクリックします。

  {{site.data.keyword.dev_console}}の[「スターター・キット」 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/developer/appservice/starter-kits) ページから、カスタム・アプリケーションを作成することもできます。
  {: tip}

2. アプリの名前を入力します。 このチュートリアルでは、`CustomProject` と入力します。
3. オプションで、アプリを分類するためのタグを指定できます。 詳しくは、『[タグの処理](/docs/resources?topic=resources-tag)』を参照してください。
4. ご使用の言語とフレームワークを選択します。 一部のスターター・キットは、1 つの言語でしか使用できない場合があります。
5. 価格プランを選択します。 このチュートリアルでは、無料オプションを使用できます。
6. **「作成」**をクリックします。

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

デプロイメント・ターゲットを選択すると、アプリ用の DevOps ツールチェーンが自動的に作成されます。 このツールチェーンには、アプリのデプロイメント状況を示すデリバリー・パイプラインが含まれています。 生成された新規アプリは、ツールチェーンの一部である GitLab リポジトリーにプッシュされます。

DevOps ツールチェーンを有効にすると、アプリ用のチーム・ベースの環境が作成されます。 ツールチェーンの作成時に、アプリ・サービスによって Git リポジトリーが作成されます。このリポジトリーでは、ソース・コードの表示、アプリの複製、および問題の作成と管理を行うことができます。 また、専用の GitLab 環境と、継続的デリバリー・パイプラインにアクセスすることもできます。 選択したデプロイメント・ターゲットが、[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about)、または[仮想サーバー (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial) のどれであっても、それに合わせてこれらはカスタマイズされています。

{{site.data.keyword.cloud_notm}} 開発者ダッシュボードから作成されたツールチェーンはすべて、自動デプロイメント用に構成されています。
{: note}

デプロイメント・ターゲットを選択して、継続的デリバリーを構成するには、以下の手順を実行します。

1. 「アプリの詳細」ページで、**「継続的デリバリーの構成 (Configure continuous delivery)」**をクリックします。
2. デプロイメント・ターゲットを選択します。 選択したターゲットの説明に従って、デプロイメント・ターゲットをセットアップします。
  * **[IBM Kubernetes Service](/docs/containers?topic=containers-app) にデプロイ**します。 このオプションは、高可用性のアプリ・コンテナーをデプロイして管理するためのワーカー・ノードというホスト・クラスターを作成します。 クラスターを作成したり、既存のクラスターにデプロイしたりすることができます。
  * **Cloud Foundry にデプロイ**します。 このオプションはクラウド・ネイティブなアプリをデプロイします。基礎にあるインフラストラクチャーを管理する必要はありません。 アカウントに {{site.data.keyword.cfee_full_notm}} に対するアクセス権限がある場合は、エンタープライズ専用の Cloud Foundry アプリをホストするための分離環境を作成および管理するために使用できる、**[パブリック・クラウド](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)**または**[エンタープライズ環境](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**のデプロイヤー・タイプを選択できます。
  * **[仮想サーバー](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server)にデプロイ**します。 このオプションによって、仮想サーバー・インスタンスがプロビジョンされ、アプリを含むイメージがロードされ、DevOps ツールチェーンが作成され、最初のデプロイメント・サイクルが開始されます。

デプロイメント・ターゲットを選択して構成すると、「アプリの詳細」ページに、継続的デリバリーが構成されたことが表示されます。 **「リポジトリーの表示」**をクリックすると、アプリのソース・コードを含むリポジトリーを表示できます。

コマンド・ラインを使用してアプリをデプロイするには、`ibmcloud dev deploy` を使用します。 詳しくは、[CLI を使用したアプリの作成およびデプロイ](/docs/apps?topic=creating-apps-create-deploy-app-cli)を参照してください。

アプリのデプロイについて詳しくは、[アプリのデプロイ](/docs/apps?topic=creating-apps-deploying-apps)を参照してください。

## アプリが実行中であることの確認
{: #verify-scratch}

アプリのデプロイ後に、Delivery Pipeline またはコマンド・ラインにアプリの URLが示されます。

1. DevOps ツールチェーンから、**「Delivery Pipeline」**をクリックし、**「デプロイ・ステージ」**を選択します。
2. **「ログおよび履歴の表示」**をクリックします。
3. ログ・ファイルで、アプリ URL を見つけます。

   ログ・ファイルの末尾で `urls` または `view` という語を探します。 例えば、`urls: my-app-devhost.mybluemix.net` または `View the application health at: http://<ipaddress>:<port>/health` のような行がログ・ファイル内で見つかります。

4. ご使用のブラウザーでその URL にアクセスします。 アプリが実行されている場合は、`Congratulations` または `{"status":"UP"}` を含むメッセージが表示されます。

コマンド・ラインを使用している場合は、[`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) コマンドを実行して、アプリの URL を表示します。 次に、ブラウザーでその URL にアクセスします。

