---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, byoc, code repository, continuous delivery, cli, deploy

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

既存のアプリケーション・リポジトリーを使用して、{{site.data.keyword.cloud}} でアプリケーションを作成できます。 単に、アプリケーションの作成時にリポジトリーへの Web リンクを提供し、続けてリソースを追加し、その後、デプロイメントのために DevOps ツールチェーンをアプリケーションに接続します。
{: shortdesc}

## 始める前に
{: #prereqs-byoc}

以下の前提条件が整っていることを確認します。

 * [{{site.data.keyword.dev_cli_long}} コマンド・ライン・インターフェース (CLI)](/docs/cli?topic=cloud-cli-ibmcloud-cli) をインストールします。
 * アプリを作成するためのベスト・プラクティスについて、[良いアプリを作成するには](/docs/apps?topic=creating-apps-best-practice)を参照してください。
 * GitHub、GitHub Enterprise、GitLab、BitBucket、または Rational のいずれかのプロバイダーからの Git ソース・コード・リポジトリーが必要です。
 * アプリを [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about) にデプロイする計画の場合は、[{{site.data.keyword.cloud_notm}} アカウントを準備する](/docs/cloud-foundry?topic=cloud-foundry-prepare)必要があります。

## ステップ 1. 既存のリポジトリーを使用したアプリの作成
{: #create-byoc}

アプリを作成し、それをソース・リポジトリーに接続するには、以下のステップを実行します。

1. [ダッシュボード ](https://{DomainName}){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") で、**「アプリ」**タイルの**「アプリの作成」**をクリックします。
2. アプリに名前を付け、リソース・グループを選択します。さらに、オプションで、アプリを分類するためのタグを指定します。 詳しくは、『[タグの処理](/docs/resources?topic=resources-tag)』を参照してください。
3. **「独自のコードを持ち込む (Bring your own code)」**を選択し、使用する Git リポジトリーへの URL を提供します。 アプリと Docker イメージは同じリポジトリー内に配置する必要があります。
4. **「作成」**をクリックします。 **アプリの詳細**ページが表示されます。
5. オプション。 アプリに[サービスを追加](/docs/apps?topic=creating-apps-add-resource)します。
6. オプション。 アプリの作成時にタグを指定した場合、表示されたタグの横の**「編集」**アイコン ![編集アイコン](../../icons/edit-tagging.svg) をクリックしてタグを編集できます。
7. オプション。 **「リポジトリーの表示 (View repo)」**をクリックして、リポジトリーを表示します。

## ステップ 2. アプリのデプロイ
{: #toolchain-byoc}

アプリ、ツールチェーン、およびリポジトリーの間のリンクを設定することは、製品アセットを編成するためのステップです。 また、ソースのビューと、DevOps ワークフロー、実行中のアプリ・インスタンス、および従属するサービスとを、すべてのデプロイメント・ターゲットにわたって集約するのにも役立ちます。 詳しくは、[ツールチェーンの作成](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)を参照してください。

アプリの継続的デリバリーを構成する際には、{{site.data.keyword.cloud_notm}} コンソールまたは CLI のいずれかを使用できます。

### コンソールの使用
{: #console-byoc-toolchain}

  1. **「アプリの詳細」**ページで**「継続的デリバリーの構成 (Configure continuous delivery)」**をクリックして、アプリを DevOps ツールチェーンに接続します。**「マイ・アプリのデプロイ (Deploy my app)」**ページが表示されます。
  2. 既存のツールチェーンがない場合は、**「ツールチェーンの作成 (Create a toolchain)」**をクリックします。ツールチェーンを作成した後、階層リンクを使用して**「アプリの詳細」**ページに戻ると、継続的デリバリーが構成されたことが表示されています。
  3. 既存のツールチェーンがある場合はそれを選択してから**「デプロイメントの有効化 (Enable deployment)」**をクリックします。**「アプリの詳細」**ページが表示され、継続的デリバリーが構成されたことが示されます。

### CLI の使用

`ibmcloud dev enable` コマンドを使用して、DevOps ツールチェーンが作成する命令セットとしてリポジトリーにチェックインする DevOps ツールチェーン・テンプレートを生成できます。 

  1. **「アプリの詳細」**ページで**「リポジトリーの表示 (View repo)」**をクリックして、コードをローカルに処理します。
  2. 次のコマンドを実行します。
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

詳しくは、[CLI を使用したアプリの作成およびデプロイ](/docs/apps?topic=creating-apps-create-deploy-app-cli)を参照してください。

