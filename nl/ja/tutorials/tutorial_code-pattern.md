---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, code pattern, DevOps, toolchain, service credentials, create app code pattern, app pattern

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

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

アプリはいくつかの方法で {{site.data.keyword.cloud_notm}} にデプロイできますが、DevOps ツールチェーンが、実動アプリをデプロイする場合に最適な方法です。 DevOps ツールチェーンを使用すると、多数の環境へのデプロイメントを簡単に自動化して、成長するアプリの管理に役立つモニタリング、ロギング、およびアラートの各サービスを素早く追加することができます。

ツールチェーンを有効にすると、アプリ用のチーム・ベースの開発環境が作成されます。 ツールチェーンの作成時に、アプリ・サービスによって Git リポジトリーが作成されます。このリポジトリーでは、ソース・コードの表示、アプリの複製、および問題の作成と管理を行うことができます。 また、専用の GitLab 環境と、継続的 Delivery Pipeline にアクセスすることもできます。 選択したデプロイメント・ターゲットが、[Kubernetes](/docs/containers?topic=containers-container_index)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about)、または[仮想サーバー (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers) のどれであっても、それに合わせてこれらはカスタマイズされています。

1. **「アプリの詳細」**ページで**「継続的デリバリーの構成 (Configure continuous delivery)」**をクリックします。
2. デプロイメント・ターゲットを選択し、**「作成」**をクリックします。 {{site.data.keyword.cloud_notm}} は、Git リポジトリーと継続的デリバリー・パイプラインを備えたオープン・ツールチェーンを自動的に作成します。
3. 新しいツールチェーンのパイプライン・ステージを開いて、ビルドとデプロイメントのプロセスを表示すると、数分後に新しいアプリが表示されます。

デプロイメント・ターゲット、ビルド、およびパイプラインについて詳しくは、[ビルドおよびデプロイ](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)を参照してください。
