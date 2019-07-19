---

copyright:
  years: 2019
lastupdated: "2019-03-15"

keywords: apps, domain, Kubernetes, Cloud Foundry, cli

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# ドメインの更新
{: #update-domain}

ドメインは、{{site.data.keyword.cloud}} で各組織に割り振られた URL 経路を指定します。 Cloud Foundry アプリの場合は、{{site.data.keyword.cloud_notm}} コンソールまたはコマンド・ライン・インターフェースを使用して、ドメインを `mybluemix.net` から `appdomain.cloud` に移行できます。
{:shortdesc}

## {{site.data.keyword.cloud_notm}} コンソールからドメインを更新する
{: #update-domain-console}

デフォルトの共有ドメインは `mybluemix.net` ですが、`appdomain.cloud` という別のドメインも選択できます。
{: tip}

コンソールを使用して Cloud Foundry 組織のドメインを更新するには、以下の手順を実行します。

1. [{{site.data.keyword.cloud_notm}} コンソール![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}){: new_window}から**「メニュー」**アイコン![「メニュー」アイコン](../icons/icon_hamburger.svg)をクリックして**「リソース・リスト」**を選択します。
2. **「リソース・リスト」**ページで**「Cloud Foundry アプリ」**をクリックします。
3. ドメインを変更するアプリケーションをクリックします。アプリの**「概要」**ページが表示されます。
4. **「経路」**メニューを選択し (`<myapp.mybluemix.net>` のように、現在のドメインが表示されます) **「経路の編集」**をクリックします。
5. ドメインのリストを選択し、使用するドメインをクリックします (`us-south.cf.appdomain.cloud` など)。
6. **「保存」**をクリックして更新を確認します。
7. 古いドメインを置き換えることを確認し、**「削除」**をクリックします。
8. 新しい経路が機能していることを確認するには、**「アプリ URL にアクセス」**をクリックします。

## {{site.data.keyword.cloud_notm}} コマンド・ライン・インターフェースからドメインを更新する
{: #update-domain-cli}

1. Cloud Foundry アプリの場合は、次のコマンドを入力して対象の Cloud Foundry API エンドポイントに接続します。
   ```
   ibmcloud target --cf-api <CF_ENDPOINT>
   ```
   
   **Cloud Foundry API エンドポイント:**
   * US-SOUTH - `api.us-south.cf.cloud.ibm.com`
   * US-EAST - `api.us-east.cf.cloud.ibm.com`
   * EU-DE - `api.eu-de.cf.cloud.ibm.com`
   * EU-GB - `api.eu-gb.cf.cloud.ibm.com`
   * AU-SYD - `api.au-syd.cf.cloud.ibm.com`

2. 次のコマンドを入力して、新しいドメインの経路をアプリケーションに追加します。
   ```
   ibmcloud app route-map APP_NAME DOMAIN -n HOSTNAME
   ```

## Kubernetes アプリのドメインの更新
{: #update-domain-kube}

{{site.data.keyword.containerlong}}のホスト名のサブドメインは `containers.appdomain.cloud` です。IBM が提供する入口のサブドメインのワイルドカード `*.<cluster_name>.<region>.containers.appdomain.cloud` は、ご使用のクラスターにデフォルトで登録されています。IBM 提供の TLS 証明書はワイルドカード証明書ですので、ワイルドカード・サブドメインに使用できます。詳しくは、[名前空間内の複数ドメイン](/docs/containers?topic=containers-ingress#multi-domains)を参照してください。
