---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, mobile, mobile application, starter kit, developer tools, DevOps toolchain, toolchain, create mobile app, mobile starter kit

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# スターター・キットを使用したモバイル・アプリケーションの作成
{: #tutorial-mobile}

{{site.data.keyword.cloud}} は、モバイル・アプリケーションを素早く作成するために役立つモバイル・スターター・キットを提供します。 事前構成されたカスタム・アプリの操作を開始するには、アプリ・サービスの「スターター・キット」から言語、フレームワーク、およびツールを選択します。 このチュートリアルでは、必要なツールをインストールしてから、アプリをローカルでビルドして実行し、クラウドにデプロイする方法を確認できます。
{: shortdesc}

## ステップ 1. 始める前に
{: #prereqs-mobile}

* [{{site.data.keyword.dev_cli_short}}](/docs/cli?topic=cloud-cli-ibmcloud-cli) をインストールします。
* Docker は開発者ツールの一部としてインストールされます。 ビルド・コマンドが機能するためには、Docker が実行中でなければなりません。 Docker アカウントを作成して、Docker アプリを実行し、サインインする必要があります。
* アプリを [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about) にデプロイする計画の場合は、[{{site.data.keyword.cloud_notm}} アカウントを準備する](/docs/cloud-foundry?topic=cloud-foundry-prepare)必要があります。

## ステップ 2. {{site.data.keyword.dev_console}}を使用したアプリの作成
{: #create-mobile}

1. {{site.data.keyword.cloud_notm}} で {{site.data.keyword.dev_console}}・アプリを作成します。
2. {{site.data.keyword.dev_console}}の[「スターター・キット」](https://{DomainName}/developer/appservice/starter-kits/){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") ページから、必要な機能に基づいてスターター・キットを選択します。 例えば、Watson Language アプリケーションの場合、**「Swift Kitura」**を選択します。
3. アプリ名を入力します。 このチュートリアルでは、`WatsonApp` を使用します。
4. オプション。 アプリを分類するためのタグを指定します。 詳しくは、『[タグの処理](/docs/resources?topic=resources-tag)』を参照してください。
5. ご使用の言語プラットフォームを選択します。 このチュートリアルでは、`Swift` を使用します。
6. ご使用の言語とフレームワークを選択します。 一部のスターター・キットは、1 つの言語でしか使用できない場合があります。
7. 価格プランを選択します。 このチュートリアルでは無料オプションを使用できます。
8. **「作成」**をクリックします。

## ステップ 3. サービスの追加 (オプション)
{: #resources-mobile}

Watson のコグニティブ機能でアプリを拡張するサービスを追加したり、モバイル・サービスやセキュリティー・サービスを追加したりできます。 このチュートリアルでは、データを管理する場所を追加します。

1. **アプリの詳細**ページで、**「サービスの追加」**をクリックします。
2. 必要なサービスの種類を選択します。 例えば、**「データ (Data)」**>**「次へ」**>**「Cloudant」**>**「次へ」**をクリックします。
3. 価格プランを選択します。 このチュートリアルでは無料オプションを使用できます。
4. **「作成」**をクリックします。

## ステップ 4. DevOps ツールチェーンの作成
{: #toolchain-mobile}

ツールチェーンを有効にすると、アプリ用のチーム・ベースの開発環境が作成されます。 ツールチェーンの作成時に、アプリ・サービスによって Git リポジトリーが作成されます。このリポジトリーでは、ソース・コードの表示、アプリの複製、および問題の作成と管理を行うことができます。 また、専用の GitLab 環境と、継続的 Delivery Pipeline にアクセスすることもできます。 選択したデプロイメント・ターゲットが、[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html)、または[仮想サーバー (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers) のどれであっても、それに合わせてこれらはカスタマイズされています。

{{site.data.keyword.cloud_notm}} 開発者ダッシュボードから作成されたツールチェーンはすべて、自動デプロイメント用に構成されています。
{: note}

1. **「アプリの詳細」**ページで**「継続的デリバリーの構成 (Configure continuous delivery)」**をクリックします。
2. デプロイメント・ターゲットを選択します。 選択したターゲットの説明に従って、デプロイメント・ターゲットをセットアップします。
  * **[IBM Kubernetes Service](/docs/apps/deploying?topic=creating-apps-containers-kube) にデプロイします**。 このオプションは、高可用性のアプリケーション・コンテナーをデプロイして管理するためのワーカー・ノードというホスト・クラスターを作成します。 クラスターを作成したり、既存のクラスターにデプロイしたりすることができます。
  * **Cloud Foundry にデプロイ**します。 このオプションはクラウド・ネイティブなアプリをデプロイします。基礎にあるインフラストラクチャーを管理する必要はありません。 ご使用のアカウントに {{site.data.keyword.cfee_full_notm}} へのアクセス権限がある場合、デプロイヤー・タイプとして、**[パブリック・クラウド](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)**または**[エンタープライズ環境](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**のいずれかを選択できます。エンタープライズ環境を使用すると、自社専用に Cloud Foundry アプリケーションをホスティングする隔離された環境を作成して管理できます。
  * **[仮想サーバー](/docs/apps?topic=creating-apps-vsi-deploy)にデプロイします**。 このオプションによって、仮想サーバー・インスタンスがプロビジョンされ、アプリを含むイメージがロードされ、DevOps ツールチェーンが作成され、最初のデプロイメント・サイクルが開始されます。

アプリのデプロイについて詳しくは、[アプリのデプロイ](/docs/apps?topic=creating-apps-deploying-apps)を参照してください。

## ステップ 5. アプリのビルドおよびローカルでの実行
{: #build-run-mobile}

最後のステップでアプリをクラウドにデプロイしたときに、ツールチェーンが作成されています。 ツールチェーンは、アプリ用の Git リポジトリーを作成します。このリポジトリーで、コードを見つけることができます。 リポジトリーにアクセスするには、次のステップに従います。 アプリをクラウドにプッシュする前に、アプリをテスト用にローカルでビルドすることができます。

1. **「アプリの詳細」**ページで**「コードのダウンロード (Download code)」**または**「リポジトリーの複製 (Clone your repo)」**をクリックして、コードをローカルに処理します。
2. 統合開発環境にアプリをインポートします。
3. コードを変更します。
4. パーソナル・アクセス・トークンを追加して、[Git 認証](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication)をセットアップします。
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

### Xcode での Swift アプリの実行
{: #run_swift}

1. Markdown ビューアーで `README.md` ファイルを開き、アプリを構成するためのステップを確認します。
2. 端末を開き、アプリ・フォルダーにナビゲートし、以下のコマンドを実行します。
    1. CocoaPods リポジトリーのセットアップが必要な場合は、`pod setup` を実行します。
    2. 既存の pod を更新する必要がある場合は、`pod update` を実行します。
    3. アプリの pod をインストールするには、`pod install` を実行します。
3. `<appname>.xcworkspace` Xcode ワークスペースを開きます。
4. アプリを実行します。

### Xcode での Cordova アプリの実行
{: #run_cordova_xcode}

実装言語として Cordova を使用するように選択した場合は、以下の指示に従います。

1. Markdown ビューアーで `README.md` ファイルを開いてアプリを構成します。
2. Xcode で `platforms/ios` アプリを開きます。
3. アプリを実行します。

### Android Studio での Cordova アプリの実行
{: #run_cordova_studio}

モバイル・アプリのプラットフォームとして Cordova を使用するように選択した場合は、このセクションを使用します。

1. `BasicProject-Cordova.zip` ファイルを解凍します。
2. Markdown ビューアーで `README.md` ファイルを開いてアプリを構成します。
3. Android Studio で `platforms/android` アプリを開きます。
4. アプリを実行します。

### Android Studio での Android アプリの実行
{: #run_android}

モバイル・アプリのプラットフォームとして Android を使用するように選択した場合は、このセクションを使用します。

1. Markdown ビューアーで `README.md` ファイルを開いてアプリを構成します。
2. Android Studio で `BasicProject-Android` アプリを開きます。
3. アプリを実行します。

## ステップ 6. アプリのデプロイ
{: #deploy-mobile}

### ツールチェーンを使用したデプロイ
{: #deploy-mobile-toolchain}

アプリはいくつかの方法で {{site.data.keyword.cloud_notm}} にデプロイできますが、DevOps ツールチェーンが、実動アプリをデプロイする場合に最適な方法です。 DevOps ツールチェーンを使用すると、多数の環境へのデプロイメントを簡単に自動化して、成長するアプリの管理に役立つモニタリング、ロギング、およびアラートの各サービスを素早く追加することができます。

正しく構成されたツールチェーンを使用すると、リポジトリー内のマスター・ブランチへのマージが行われるたびに、ビルドとデプロイのサイクルが自動的に開始されます。 {{site.data.keyword.cloud_notm}} 開発者ダッシュボードから作成されたツールチェーンはすべて、自動デプロイメント用に構成されています。

DevOps ツールチェーンからアプリを手動でデプロイすることもできます。

1. **「アプリの詳細」**ページで**「ツールチェーンの表示」**をクリックします。

2. **「Delivery Pipeline」**をクリックします。ここで、ビルドの開始、デプロイメントの管理、およびログと履歴の表示を行うことができます。

### {{site.data.keyword.dev_cli_short}} を使用したデプロイ
{: #deploy-mobile-cli}

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
{: #verify-mobile}

アプリのデプロイ後に、Delivery Pipeline またはコマンド・ラインにアプリの URLが示されます。

1. DevOps ツールチェーンから、**「Delivery Pipeline」**をクリックし、**「デプロイ・ステージ」**を選択します。
2. **「ログおよび履歴の表示」**をクリックします。
3. ログ・ファイルで、アプリケーション URL を見つけます。

    ログ・ファイルの末尾で `urls` または `view` という語を探します。 例えば、`urls: my-app-devhost.mybluemix.net` または `View the application health at: http://<ipaddress>:<port>/health` のような行がログ・ファイル内で見つかります。

4. ご使用のブラウザーでその URL にアクセスします。 アプリが実行されている場合は、`Congratulations` または `{"status":"UP"}` を含むメッセージが表示されます。

コマンド・ラインを使用している場合は、[`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) コマンドを実行して、アプリの URL を表示します。 次に、ブラウザーでその URL にアクセスします。
