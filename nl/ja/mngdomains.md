---

copyright:
  years: 2019
lastupdated: "2019-04-02"

keywords: apps, custom, domain, kubernetes, cloud foundry, add, subdomain, custom domain, dns, domainname, domain name, endpoint, update, migrate

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# ドメインの管理
{: #update-domain}

ドメインは、{{site.data.keyword.cloud}} で各組織に割り振られた URL 経路を指定します。 カスタム・ドメインはアプリケーションの要求をユーザーが所有する URL に送ります。 カスタム・ドメインとして、共有ドメイン、共有サブドメイン、または共有ドメインおよびホストを使用できます。 カスタム・ドメインが指定されない場合、{{site.data.keyword.cloud_notm}} は、アプリケーションへの経路にデフォルトの共有ドメインを使用します。 ドメインの管理プロセスは、{{site.data.keyword.containershort}}、Cloud Foundry など、デプロイメント・ターゲットによって異なります。
{:shortdesc}

カスタム・ドメインを使用するには、パブリック DNS サーバーにカスタム・ドメインを登録し、{{site.data.keyword.cloud_notm}} 内にカスタム・ドメインを構成する必要があります。 次に、パブリック DNS サーバー上の {{site.data.keyword.cloud_notm}} システム・ドメインにカスタム・ドメインをマップする必要があります。 ご使用のカスタム・ドメインがシステム・ドメインにマップされると、そのカスタム・ドメインへの要求は {{site.data.keyword.cloud_notm}} 内のアプリケーションに経路指定されます。

## Kubernetes アプリのドメインの変更
{: #update-domain-kube}

{{site.data.keyword.containershort_notm}}のホスト名のサブドメインは `containers.appdomain.cloud` です。 IBM が提供する入口のサブドメインのワイルドカード `*.<cluster_name>.<region>.containers.appdomain.cloud` は、ご使用のクラスターにデフォルトで登録されています。 IBM 提供の TLS 証明書はワイルドカード証明書ですので、ワイルドカード・サブドメインに使用できます。 詳しくは、[名前空間内の複数ドメイン](/docs/containers?topic=containers-ingress#multi-domains)を参照してください。

## Kubernetes アプリにカスタム・ドメインを使用する
{: #custom-domain-kube}

カスタム・ドメインを使用する場合は、カスタム・ドメインを `*.custom_domain.net` などのワイルドカード・ドメインとして登録する必要があります。 TLS を使用するには、ワイルドカード証明書を取得する必要があります。 詳しくは、[名前空間内の複数ドメイン](/docs/containers?topic=containers-ingress#multi-domains)を参照してください。

[このチュートリアル](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes)をご確認ください。Web アプリケーションのスキャフォールド、それをコンテナーでローカルで実行する方法、さらにそれを IBM Kubernetes Service で作成した Kubernetes クラスターにデプロイする方法について詳しく説明されています。 また、カスタム・ドメインをバインドし、環境の正常性を監視し、アプリケーションを拡張する方法についてもチュートリアルで説明されています。

## Cloud Foundry アプリのドメインの変更
{: #update-domain-cf}

Cloud Foundry アプリの場合は、{{site.data.keyword.cloud_notm}} コンソールまたはコマンド・ライン・インターフェースを使用して、ドメインを `mybluemix.net` から `appdomain.cloud` に変更できます。 `appdomain.cloud` への変更について詳しくは、[ドメインの更新](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain)を参照してください。

デフォルトの共有ドメインは `mybluemix.net` ですが、`appdomain.cloud` という別のドメインも選択できます。
{: tip}

## Cloud Foundry アプリにカスタム・ドメインを使用する
{: #custom-domain-cf}

Cloud Foundry アプリの場合は、{{site.data.keyword.cloud_notm}} コンソールまたはコマンド・ライン・インターフェースを使用して、カスタム・ドメインを作成および使用できます。 詳しくは、[カスタム・ドメインの追加と使用](/docs/cloud-foundry-public?topic=cloud-foundry-public-custom-domains)を参照してください。
