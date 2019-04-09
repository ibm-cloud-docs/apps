---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# アプリのホスティング
{: #hosting}

既存のアプリがある場合は、必要なすべてのインフラストラクチャーまたはプラットフォームのサービスを含めて IBM Cloud でホストすることができます。また、{{site.data.keyword.Bluemix_notm}} インフラストラクチャーを利用して、{{site.data.keyword.Bluemix_notm}} 用に特定して開発したアプリをホストすることもできます。
{:shortdesc}

## アプリのマイグレーション
{: #ht_hostapp}

アプリを完全にクラウド環境に移す代わりに、アプリを {{site.data.keyword.Bluemix_notm}} にインクリメンタルにマイグレーションできます。アプリの一部を先にマイグレーションし、Cloud Integration サービスを使用して、既存のデータまたは SoR (Systems of Record、定型業務処理システム) に接続することができます。

{{site.data.keyword.Bluemix_notm}} アプリで、SoR などのバックエンドのデータやサービスへのアクセスが必要になる場合があります。{{site.data.keyword.Bluemix_notm}} では、Secure Gateway サービスを使用して、{{site.data.keyword.Bluemix_notm}} 組織とエンタープライズ・バックエンド・ネットワークの間にセキュア・トンネルを確立できます。 このサービスによって、{{site.data.keyword.Bluemix_notm}} 上のアプリがバックエンド・ネットワークのデータおよびサービスにアクセスできるようになります。 詳細については、[Reaching enterprise backend with Bluemix Secure Gateway via console ![「外部リンク」アイコン](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} を参照してください。

{{site.data.keyword.Bluemix_notm}} は既存のアプリをホストし、{{site.data.keyword.Bluemix_notm}} でのすべてのインフラストラクチャーを提供できます。[カタログ](https://console.bluemix.net/catalog/?taxonomyNavigation=apps)で、アプリをベア・メタル・サーバーのクラウドでホストするか、または仮想サーバーでホストするかを選択できます。

アプリのパーツは、1 度に全部、またはコンポーネントごとに {{site.data.keyword.Bluemix_notm}} にマイグレーションできます。アプリをマイグレーションする際に提供されるいくつかのサービスをご覧ください。

* ブロック・ストレージ、ファイル・ストレージ、またはオブジェクト・ストレージから、自分に適した[ストレージ](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage)のタイプを選択します。
* 自分に必要な[ネットワーク](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork)のタイプを選択します。
* {{site.data.keyword.Bluemix_notm}} Kubernetes テクノロジーを利用するには、[コンテナリゼーション](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers)・サービスを選択します。

## 次のステップ
{: #next-steps}

複数の地域でサービスのホスティングが可能な場合は、どこでアプリをホストするかを選択できます。[アプリの更新](updapps.html)で、アプリをホストする地域を選択し、カスタム URL を編集できます。
