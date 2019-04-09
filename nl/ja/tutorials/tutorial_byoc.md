---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

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

 * [{{site.data.keyword.dev_cli_long}} コマンド・ライン・インターフェース (CLI)](/docs/cli/index.html) をインストールします。
 * アプリを作成するためのベスト・プラクティスについて、[良いアプリを作成するには](/docs/apps/best-practice.html#best-practice)を参照してください。
 * GitHub、GitHub Enterprise、GitLab、BitBucket、または Rational のいずれかのプロバイダーからの Git ソース・コード・リポジトリーが必要です。
 * アプリを [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about) にデプロイする予定の場合、[{{site.data.keyword.cloud_notm}} アカウントを準備](/docs/cloud-foundry/prepare-account.html#prepare)する必要があります。

## ステップ 1. 既存のリポジトリーを使用したアプリの作成
{: #create-byoc}

アプリを作成し、それをソース・リポジトリーに接続するには、以下のステップを実行します。

1. [ダッシュボード ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}){: new_window} で、**「アプリ」**タイルの**「アプリの作成」**をクリックします。
2. アプリに名前を付け、リソース・グループを選択します。さらに、オプションで、アプリを分類するためのタグを指定します。 詳しくは、『[タグの処理](/docs/resources/tagging_resources.html#tag)』を参照してください。
3. **「独自のコードを持ち込む (Bring your own code)」**を選択し、使用する Git リポジトリーへの URL を提供します。 アプリと Docker イメージは同じリポジトリー内に配置する必要があります。
4. **「作成」**をクリックします。

**アプリの詳細**ページが表示されます。 ここから、以下のことを実行できます。
* [リソースを追加](/docs/apps/reqnsi.html#add-resource)する (オプション)。
* アプリの作成時にタグを指定した場合、表示されたタグの横の**「編集」**アイコン ![編集アイコン](../../icons/edit-tagging.svg) をクリックしてタグを編集できます。
* **「DevOps ツールチェーンへの接続 (Connect to DevOps toolchain)」**をクリックして、アプリを DevOps ツールチェーンに接続する。 ツールチェーンがまだない場合は、**「DevOps ツールチェーンの接続 (Connect DevOps Toolchain)」**ページが開きます。 **「DevOps ツールチェーンの作成 (Create DevOps toolchain)」**をクリックします。 その時点で、[DevOps ダッシュボード](https://{DomainName}/devops/)の[「ツールチェーンの作成」](https://{DomainName}/devops/create)ページが、ブラウザーの新しいタブで開きます。 そのタブでツールチェーンを作成し、構成した後は、アプリの**「ツールチェーンの接続 (Connect a toolchain)」**ページに戻り、ページをリフレッシュする必要があります。
* **「リポジトリーの表示 (View repo)」**をクリックして、リポジトリーを表示します。
* **「アプリの詳細」**ページにある関連リンクをクリックして、ツールチェーンまたはアプリ作成エクスペリエンスに関する詳細を理解します。

## ステップ 2. DevOps ツールチェーンへのアプリの接続
{: #toolchain-byoc}

アプリ、ツールチェーン、およびリポジトリーの間のリンクを設定することは、製品アセットを編成するためのステップです。 また、ソースのビューと、DevOps ワークフロー、実行中のアプリ・インスタンス、および従属するサービスとを、すべてのデプロイメント・ターゲットにわたって集約するのにも役立ちます。 詳しくは、[ツールチェーンの作成](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started)を参照してください。

アプリを DevOps ツールチェーンに接続する際は、{{site.data.keyword.cloud_notm}} コンソールまたは CLI のいずれかを使用できます。

### コンソールの使用
{: #console-byoc-toolchain}

  1. **「DevOps ツールチェーンへの接続 (Connect to DevOps toolchain)」**をクリックして、アプリを DevOps ツールチェーンに接続します。 
  
    既存のツールチェーンがない場合は、**「DevOps ツールチェーンの作成 (Create DevOps toolchain)」**をクリックします。 
    
  2. ツールチェーンを作成し、構成したら、アプリの「ツールチェーンの接続 (Connect a toolchain)」ページに戻り、ページをリフレッシュします。 

### CLI の使用

`ibmcloud dev enable` コマンドを使用して、DevOps ツールチェーンが作成する命令セットとしてリポジトリーにチェックインする DevOps ツールチェーン・テンプレートを生成できます。 

  1. 「アプリ・サービス」ウィンドウで、**「コードのダウンロード (Download Code)」**または**「リポジトリーの複製 (Clone your repo)」**をクリックして、コードをローカルで処理します。
  2. 次のコマンドを実行します。
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

詳しくは、[CLI を使用したアプリの作成およびデプロイ](/docs/apps/create-deploy-cli.html#create-deploy-app-cli)を参照してください。

## ステップ 3. アプリのデプロイ
{: #deploy-byoc}

DevOps ツールチェーンをアプリに接続したら、以下のステップを実行して、それを {{site.data.keyword.cloud_notm}} にデプロイします。 

1. アプリの詳細ページで、**「クラウドにデプロイ」**をクリックします。
2. デプロイメント方式を選択します。 選択した方式の説明に従って、デプロイメント方式をセットアップします。
  * **[Kubernetes](/docs/apps/deploying/containers.html#containers) にデプロイ**します。 このオプションは、高可用性のアプリケーション・コンテナーをデプロイして管理するためのワーカー・ノードというホスト・クラスターを作成します。 クラスターを作成したり、既存のクラスターにデプロイしたりすることができます。
  * **Cloud Foundry にデプロイ**します。 このオプションはクラウド・ネイティブなアプリをデプロイします。基礎にあるインフラストラクチャーを管理する必要はありません。 ご使用のアカウントに {{site.data.keyword.cfee_full_notm}} へのアクセス権限がある場合、デプロイヤー・タイプとして、**[パブリック・クラウド](/docs/cloud-foundry-public/about-cf.html#about-cf)**または**[エンタープライズ環境](/docs/cloud-foundry-public/cfee.html#cfee)**のいずれかを選択できます。エンタープライズ環境を使用すると、自社専用に Cloud Foundry アプリケーションをホスティングする隔離された環境を作成して管理できます。
  * **[仮想サーバー](/docs/apps/vsi-deploy.html#vsi-deploy)にデプロイします**。 このオプションによって、仮想サーバー・インスタンスがプロビジョンされ、アプリを含むイメージがロードされ、DevOps ツールチェーンが作成され、最初のデプロイメント・サイクルが開始されます。


