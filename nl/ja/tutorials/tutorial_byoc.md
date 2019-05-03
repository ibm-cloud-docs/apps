---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-05"

keywords: byoc, code repository, continuous delivery, cli, deploy, create app custom repo, custom repo, existing repo, custom code

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# 独自のコード・リポジトリーからのアプリの作成
{: #tutorial-byoc}

既存のリポジトリーにアプリケーションがある場合、ブランクのスターター・キットを使用して {{site.data.keyword.cloud_notm}} にアプリ・レコードを作成し、そのアプリをソース・リポジトリーおよび DevOps ツールチェーンに接続できます。
{: shortdesc}

{{site.data.keyword.cloud_notm}} ダッシュボードまたはブランクのスターター・キットから開始できます。 アプリに名前を付けてリソース・グループを選択したら、**独自のコードの持ち込み**開始点を選択し、コードを含む Git リポジトリー URL を指定し、**「作成」**をクリックします。

既存の DevOps ツールチェーンを接続または作成し、Kubernetes や Cloud Foundry などの任意のデプロイメント・ターゲットにアプリを継続的にデリバリーできます。

## 始める前に
{: #prereqs-byoc}

以下の前提条件が整っていることを確認します。

 * [{{site.data.keyword.dev_cli_long}} コマンド・ライン・インターフェース (CLI)](/docs/cli?topic=cloud-cli-ibmcloud-cli) をインストールします。
 * アプリを作成するためのベスト・プラクティスについて、[良いアプリを作成するには](/docs/apps?topic=creating-apps-best-practice)を参照してください。
 * GitHub、GitHub Enterprise、GitLab、BitBucket、または Rational のいずれかのプロバイダーからの Git ソース・コード・リポジトリーが必要です。
 * アプリを [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about) にデプロイする計画の場合は、[{{site.data.keyword.cloud_notm}} アカウントを準備する](/docs/cloud-foundry?topic=cloud-foundry-prepare)必要があります。

## 既存のリポジトリーを使用したアプリの作成
{: #create-byoc}

アプリを作成し、それをソース・リポジトリーに接続するには、以下のステップを実行します。

1. [{{site.data.keyword.cloud_notm}} コンソール ](https://{DomainName}){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") で、**「アプリ」**タイルの**「アプリの作成」**をクリックします。
2. アプリに名前を付け、リソース・グループを選択します。さらに、オプションで、アプリを分類するためのタグを指定します。 詳しくは、『[タグの処理](/docs/resources?topic=resources-tag)』を参照してください。
3. **「独自のコードを持ち込む (Bring your own code)」**を選択し、使用する Git リポジトリーへの URL を提供します。 アプリと Docker イメージは同じリポジトリー内に配置する必要があります。
4. **「作成」**をクリックします。 **アプリの詳細**ページが表示されます。
5. オプション。 アプリに[サービスを追加](/docs/apps?topic=creating-apps-add-resource)します。
6. オプション。 **「タグの追加」**をクリックしてこのアプリにタグを追加したり、表示されたタグの横の**「編集」**アイコン ![「編集」アイコン](../../icons/edit-tagging.svg)をクリックしてタグを編集したりできます。
7. オプション。 **「リポジトリーの表示 (View repo)」**をクリックして、リポジトリーを表示します。

## アプリのデプロイ
{: #toolchain-byoc}

アプリ、ツールチェーン、およびリポジトリーの間のリンクを設定することは、製品アセットを編成するためのステップです。 また、ソースのビューと、DevOps ワークフロー、実行中のアプリ・インスタンス、および従属するサービスとを、すべてのデプロイメント・ターゲットにわたって集約するのにも役立ちます。 詳しくは、[ツールチェーンの作成](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)を参照してください。

アプリの継続的デリバリーを構成する際には、{{site.data.keyword.cloud_notm}} コンソールまたは CLI のいずれかを使用できます。

### コンソールの使用
{: #console-byoc-toolchain}

#### アプリに接続する DevOps ツールチェーンがすでにある場合は、以下の手順を実行します。

1. **「アプリの詳細」**ページで**「継続的デリバリーの構成 (Configure continuous delivery)」**をクリックします。 **「マイ・アプリのデプロイ (Deploy my app)」**ページが表示されます。
2. アプリに接続するツールチェーンを選択し、**「デプロイメントの有効化 (Enable deployment)」**をクリックします。**「アプリの詳細」**ページが表示され、継続的デリバリーが構成されたことが示されます。

#### このアプリ用の DevOps ツールチェーンがない場合は、以下の手順を実行してください。

1. **「アプリの詳細」**ページで、**「DevOps ツールチェーンの作成 (Create DevOps toolchain)」**をクリックします。**「ツールチェーンの作成」**ページが表示されます。
2. [ツールチェーンを作成します](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)。
3. ブラウザー・ウィンドウの階層リンクを使用して**「アプリの詳細」**ページに戻ると、継続的デリバリーが構成されたことが表示されています。

### CLI の使用
{: #cli-byoc-toolchain}

`ibmcloud dev enable` コマンドを使用して、DevOps ツールチェーンが作成する命令セットとしてリポジトリーにチェックインする DevOps ツールチェーン・テンプレートを生成できます。 

  1. **「アプリの詳細」**ページで**「リポジトリーの表示 (View repo)」**をクリックして、コードをローカルに処理します。
  2. 次のコマンドを実行します。
    
    ```
    ibmcloud dev enable
    ```
   {: codeblock}

詳しくは、[CLI を使用したアプリの作成およびデプロイ](/docs/apps?topic=creating-apps-create-deploy-app-cli)を参照してください。

## アプリが実行中であることの確認
{: #verify-byoc-app}

Delivery Pipeline またはコマンド・ラインにアプリの URLが示されます。

1. DevOps ツールチェーンから、**「Delivery Pipeline」**をクリックし、**「デプロイ・ステージ」**を選択します。
2. **「ログおよび履歴の表示」**をクリックします。
3. ログ・ファイルで、アプリケーション URL を見つけます。 ログ・ファイルの末尾で `urls` または `view` という語を探します。 例えば、`urls: my-app-devhost.mybluemix.net` または `View the application health at: http://<ipaddress>:<port>/health` のような行がログ・ファイル内で見つかります。
4. ご使用のブラウザーでその URL にアクセスします。 アプリが実行されている場合は、`Congratulations` または `{"status":"UP"}` を含むメッセージが表示されます。

コマンド・ラインを使用している場合は、[`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) コマンドを実行して、手動でデプロイしたアプリのページをデフォルト・ブラウザーで開きます。
