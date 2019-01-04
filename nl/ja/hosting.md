---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# アプリのマイグレーションおよびホスティング
{: #hosting}

既存のアプリがある場合は、必要なすべてのインフラストラクチャーまたはプラットフォームのサービスを含めて {{site.data.keyword.Bluemix}} でホストすることができます。 アプリを一度にすべてクラウド環境にシフトするのではなく、インクリメンタルに {{site.data.keyword.Bluemix_notm}} にマイグレーションすることもできます。

## アプリのマイグレーション
{: #migrating}

アプリがオンプレミスのデータやサービスにアクセスする必要がある場合は、[{{site.data.keyword.SecureGatewayfull}}](/docs/services/SecureGateway/secure_gateway.html) を使用して、{{site.data.keyword.Bluemix_notm}} 組織とエンタープライズ・バックエンド・ネットワークの間にセキュア・トンネルを確立できます。 詳細については、[Reaching enterprise backend with {{site.data.keyword.Bluemix_notm}} Secure Gateway via console ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} を参照してください。

マイグレーションについて支援が必要な場合は、[IBM Cloud Migration Services![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud/migration-services){: new_window}を使用できます。

## アプリのホスティング
{: #ht_hostapp}

{{site.data.keyword.Bluemix_notm}} [カタログ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/?taxonomyNavigation=apps){: new_window}で、Kubernetes や Cloud Foundry などの管理対象環境を選択したり、ベア・メタル・サーバーや仮想サーバー上で直接アプリをホストしたりすることができます。

仮想デプロイメントの場合、ほとんどのアプリの操作は {{site.data.keyword.Bluemix_notm}} によって管理されます。 ワークロードが複数の地理的地域に広がっており、{{site.data.keyword.Bluemix_notm}} ハイパーバイザーを使用してデプロイメントを管理したい場合は、[仮想](/docs/vsi/vsi_about.html)デプロイメントが最適です。 より高いパフォーマンスを求めて専用物理サーバーに直接アクセスする必要がある場合は、[ベア・メタル](/docs/bare-metal/index.html)・デプロイメントが最適です。

また、以下に対する多くのオプションがあります。
* ブロック・ストレージ、ファイル・ストレージ、またはオブジェクト・ストレージから、適切な[ストレージ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window}のタイプの選択。
* 必要な[ネットワーク![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window}のタイプの選択。
* {{site.data.keyword.Bluemix_notm}} Kubernetes テクノロジーを活用するための、[コンテナリゼーション ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=containers){: new_window} サービスの選択。
