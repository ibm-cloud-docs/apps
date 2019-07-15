---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-13"

keywords: apps, code pattern, DevOps, toolchain, service credentials, create app code pattern, app pattern

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# コード・パターンを使用したアプリの作成
{: #tutorial-codepattern}

コード・パターンを使用して、素早くアプリケーションを作成して {{site.data.keyword.cloud}} にデプロイできます。 GitHub でコードを表示するか、{{site.data.keyword.cloud_notm}} でアプリを作成およびビルドできます。そこでは、DevOps ツールチェーンを使用してアプリを自動的にデプロイできます。
{: shortdesc}

## ステップ 1. アプリの作成
{: #create-codepattern}

1. [IBM Developer ](https://developer.ibm.com/patterns/){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") にアクセスし、使用したいコード・パターンを選択します。 例えば、[Build a MEAN Web App ](https://developer.ibm.com/patterns/build-a-mean-web-app/){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") コード・パターンを選択できます。

2. コード・パターンの説明を読み、GitHub リポジトリーおよび `README.md` ファイルを表示します。 リポジトリーを表示するには、**「Get the code」**をクリックします。そうすると、コード・パターンの GitHub リポジトリーが開きます。

3. 以下のいずれかのオプションを使用して、アプリの作成を開始します。 どちらのオプションでも、コード・パターンの**「アプリの作成」**ページが開きます。
    * コード・パターンのページで、{{site.data.keyword.cloud_notm}} でアプリを作成するためのリンクをクリックします。 
    * GitHub リポジトリー内の `README.md` ファイルで、スターター・キットを使用してアプリを作成するためのリンクをクリックします。 

4. **「アプリの作成」**ページで、アプリに名前を付け、リソース・グループを選択し、オプションでタグを指定します。その後、**「作成」**をクリックします。 タグについて詳しくは、『[タグの処理](/docs/resources?topic=resources-tag)』を参照してください。

  コード・パターンに戻るには、**「コード・パターンの表示」**をクリックします。 リポジトリーの中の `README.md` ファイルを参照して、アプリを稼働状態にするためにさらに操作が必要かどうかを確認します。
  {: tip}

## ステップ 2. サービスの追加
{: #resources-codepattern}

Watson のコグニティブ機能でアプリを拡張するサービスを追加したり、モバイル・サービスやセキュリティー・サービスを追加したりできます。 このプロセスでは、サービス・インスタンスを作成し、リソース・キー (資格情報) を作成し、それをアプリにバインドします。 このチュートリアルでは、データを管理する場所を追加します。

1. **アプリの詳細**ページで、**「サービスの追加」**をクリックします。
2. 必要なサービスの種類を選択します。 
3. 価格プランを選択します。 ライト・オプションが使用可能です。
4. **「作成」**をクリックします。

## ステップ 3. 環境へのサービス資格情報のコピー

アプリにサービスを追加した後、または、何らかのサービスがアプリに必要な場合は、そのサービスの資格情報が**「資格情報」**ボックスに表示されることに注意してください。 この資格情報をデプロイメント環境に手動でコピーする必要があります。

ご使用の環境への資格情報のコピーについて詳しくは、[資格情報の概要](/docs/apps?topic=creating-apps-credentials_overview#credentials_overview)を参照してください。

## ステップ 4. {{site.data.keyword.cloud_notm}} へのデプロイ
{: #deploy-codepattern}

デプロイメント・ターゲットを選択すると、アプリ用の DevOps ツールチェーンが自動的に作成されます。 このツールチェーンには、アプリのデプロイメント状況を示すデリバリー・パイプラインが含まれています。 生成された新規アプリは、ツールチェーンの一部である GitLab リポジトリーにプッシュされます。

DevOps ツールチェーンを有効にすると、アプリ用のチーム・ベースの環境が作成されます。 ツールチェーンの作成時に、アプリ・サービスによって Git リポジトリーが作成されます。このリポジトリーでは、ソース・コードの表示、アプリの複製、および問題の作成と管理を行うことができます。 また、専用の GitLab 環境と、継続的デリバリー・パイプラインにアクセスすることもできます。 選択したデプロイメント・ターゲットが、[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about)、または[仮想サーバー (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial) のどれであっても、それに合わせてこれらはカスタマイズされています。

{{site.data.keyword.cloud_notm}} 開発者ダッシュボードから作成されたツールチェーンはすべて、自動デプロイメント用に構成されています。
{: note}

デプロイメント・ターゲットを選択して、継続的デリバリーを構成するには、以下の手順を実行します。

1. 「アプリの詳細」ページで、**「継続的デリバリーの構成 (Configure continuous delivery)」**をクリックします。
2. デプロイメント・ターゲットを選択します。 選択したターゲットの説明に従って、デプロイメント・ターゲットをセットアップします。
  * **[IBM Kubernetes Service](/docs/containers?topic=containers-app) にデプロイ**します。 このオプションは、高可用性のアプリ・コンテナーをデプロイして管理するためのワーカー・ノードというホスト・クラスターを作成します。 クラスターを作成したり、既存のクラスターにデプロイしたりすることができます。
  * **Cloud Foundry にデプロイ**します。 このオプションはクラウド・ネイティブなアプリをデプロイします。基礎にあるインフラストラクチャーを管理する必要はありません。 アカウントに {{site.data.keyword.cfee_full_notm}} に対するアクセス権限がある場合は、エンタープライズ専用の Cloud Foundry アプリをホストするための分離環境を作成および管理するために使用できる、**[パブリック・クラウド](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)**または**[エンタープライズ環境](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**のデプロイヤー・タイプを選択できます。
  * **仮想サーバーにデプロイします**。 このオプションによって、仮想サーバー・インスタンスがプロビジョンされ、アプリを含むイメージがロードされ、DevOps ツールチェーンが作成され、最初のデプロイメント・サイクルが開始されます。 詳しくは、[仮想サーバーへのアプリのデプロイ](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server)を参照してください。

    VSI デプロイメントは、一部のスターター・キットで使用できます。この機能を使用するには、[{{site.data.keyword.cloud_notm}} ダッシュボード](https://{DomainName})に移動し、**「アプリ」**タイルで**「アプリの作成」**をクリックします。
    {: note}

デプロイメント・ターゲットを選択して構成すると、「アプリの詳細」ページに、継続的デリバリーが構成されたことが表示されます。 **「リポジトリーの表示」**をクリックすると、アプリのソース・コードを含むリポジトリーを表示できます。

アプリのデプロイについて詳しくは、[アプリのデプロイ](/docs/apps?topic=creating-apps-deploying-apps)を参照してください。

デプロイメント・ターゲット、ビルド、およびパイプラインについて詳しくは、[ビルドおよびデプロイ](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)を参照してください。
