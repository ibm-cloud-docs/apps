---

copyright:
  years: 2017, 2019
lastupdated: "2019-03-29"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# アプリのマイグレーションおよびホスティング
{: #hosting}

既存のアプリがある場合は、必要なすべてのインフラストラクチャーまたはプラットフォームのサービスを含めて {{site.data.keyword.cloud}} でホストすることができます。 アプリを一度にすべてクラウド環境にシフトするのではなく、インクリメンタルに {{site.data.keyword.cloud_notm}} にマイグレーションすることもできます。

## アプリのマイグレーション
{: #migrating}

アプリがオンプレミスのデータやサービスにアクセスする必要がある場合は、[{{site.data.keyword.SecureGatewayfull}}](/docs/services/SecureGateway?topic=securegateway-getting-started-with-sg#getting-started-with-sg) を使用して、{{site.data.keyword.cloud_notm}} 組織とエンタープライズ・バックエンド・ネットワークの間にセキュア・トンネルを確立できます。 詳細については、[Reaching enterprise backend with {{site.data.keyword.cloud_notm}} Secure Gateway via console ](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") を参照してください。

マイグレーションについて支援が必要な場合は、[{{site.data.keyword.cloud_notm}} Migration Services](https://www.ibm.com/cloud/migration-services){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")を使用できます。

## アプリのホスティング
{: #ht_hostapp}

{{site.data.keyword.cloud_notm}} [カタログ](https://{DomainName}/catalog/?taxonomyNavigation=apps){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")で、Kubernetes や Cloud Foundry などの管理対象環境を選択したり、ベア・メタル・サーバーや仮想サーバー上で直接アプリをホストしたりすることができます。

仮想デプロイメントの場合、ほとんどのアプリの操作は {{site.data.keyword.cloud_notm}} によって管理されます。 ワークロードが複数の地理的地域に広がっており、{{site.data.keyword.cloud_notm}} ハイパーバイザーを使用してデプロイメントを管理したい場合は、[仮想](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)デプロイメントが最適です。 より高いパフォーマンスを求めて専用物理サーバーに直接アクセスする必要がある場合は、[ベア・メタル](/docs/bare-metal?topic=bare-metal-bm-getting-started#getting-started)・デプロイメントが最適です。

また、以下に対する多くのオプションがあります。
* ブロック・ストレージ、ファイル・ストレージ、またはオブジェクト・ストレージから、適切な[ストレージ](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")のタイプの選択。
* 必要な[ネットワーク](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")のタイプの選択。
* {{site.data.keyword.cloud_notm}} Kubernetes テクノロジーを活用するための、[コンテナリゼーション ](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=containers){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") サービスの選択。
