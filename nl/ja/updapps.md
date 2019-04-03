---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-15"

keywords: apps, custom domain, Kubernetes

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# カスタム・ドメインの追加と使用
{: #updatingapps}

ドメインは、{{site.data.keyword.cloud}} で各組織に割り振られた URL 経路を指定します。 カスタム・ドメインはアプリケーションの要求をユーザーが所有する URL に送ります。カスタム・ドメインとして、共有ドメイン、共有サブドメイン、または共有ドメインおよびホストを使用できます。 カスタム・ドメインが指定されない場合、{{site.data.keyword.cloud_notm}} は、アプリケーションへの経路にデフォルトの共有ドメインを使用します。 カスタム・ドメインの作成と使用には、{{site.data.keyword.cloud_notm}} コンソールまたはコマンド・ライン・インターフェースのいずれかを使用できます。
{:shortdesc}

デフォルトの共有ドメインは `mybluemix.net` ですが、`appdomain.cloud` という別のドメインも選択できます。`appdomain.cloud` への移行について詳しくは、[ドメインの更新](/docs/apps/tutorials?topic=creating-apps-update-domain)を参照してください。
{: tip}

カスタム・ドメインを使用するには、パブリック DNS サーバーにカスタム・ドメインを登録し、{{site.data.keyword.cloud_notm}} 内にカスタム・ドメインを構成する必要があります。 次に、パブリック DNS サーバー上の {{site.data.keyword.cloud_notm}} システム・ドメインにカスタム・ドメインをマップする必要があります。ご使用のカスタム・ドメインがシステム・ドメインにマップされると、そのカスタム・ドメインへの要求は {{site.data.keyword.cloud_notm}} 内のアプリケーションに経路指定されます。

## {{site.data.keyword.cloud_notm}} コンソールからカスタム・ドメインを追加する
{: #custom-domain-console}

コンソールを使用して組織のカスタム・ドメインを追加するには、以下の手順を実行します。

1. **「管理」 > 「アカウント」**と進み、**「Cloud Foundry の組織」**を選択します。
2. カスタム・ドメインを作成する組織の名前をクリックします。
3. **「ドメイン」**タブをクリックして、使用可能なドメインのリストを表示します。
4. **「ドメインの追加」**をクリックして、ドメイン名を入力して地域を選択します。
5. 更新を確認して **「追加」**をクリックします。

## カスタム・ドメインを使用した経路をアプリケーションに追加する

1. [{{site.data.keyword.cloud_notm}} コンソール](https://{DomainName}){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")から**「メニュー」**アイコン![「メニュー」アイコン](../../icons/icon_hamburger.svg)をクリックして**「リソース・リスト」**を選択します。
2. **「リソース・リスト」**ページで**「Cloud Foundry アプリ」**をクリックします。
3. 経路を追加するアプリケーションをクリックします。アプリの**「概要」**ページが表示されます。
4. **「経路」**メニューを選択し、**「経路の編集」**を選択します。
5. **「経路の追加」**をクリックし、アプリケーションに使用する経路を指定します。
6. **「保存」**をクリックして更新を確認します。

例えば、`*.mycompany.com` を使用して経路 `www.mybluemix.net` をアプリに関連付けることができます。 `example.mycompany.com` を使用して、経路 `www.example.bluemix.net` をアプリに関連付けることもできます。
{: tip}

## {{site.data.keyword.cloud_notm}} コマンド・ライン・インターフェースからカスタム・ドメインを追加する
{: #custom-domain-cli}

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
   
2. 次のコマンドを入力して、自分の組織のカスタム・ドメインを作成します。
   ```
   ibmcloud app domain-create <MY_ORGNAME> <MY_DOMAIN>
   ```

3. カスタム・ドメインを使用した経路をアプリケーションに追加します。

   Cloud Foundry アプリの場合、次のコマンドを入力します。
   ```
   ibmcloud app route-map <MY_APPNAME> <MY_DOMAIN> -n <MY_HOSTNAME>
   ```
   
## カスタム・ドメインをシステム・ドメインにマップする
{: #mapcustomdomain}

{{site.data.keyword.cloud_notm}} でカスタム・ドメインを構成した後、登録された DNS サーバー上の {{site.data.keyword.cloud_notm}} システム・ドメインにカスタム・ドメインをマップします。

1. DNS サーバー上のカスタム・ドメイン・ネームに 'CNAME' レコードをセットアップします。 CNAME レコードのセットアップ手順は、使用している DNS プロバイダーによって異なります。 例えば、GoDaddy を使用する場合、GoDaddy の[ドメインのヘルプ ](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") にあるガイダンスに従ってください。
2. アプリケーションが実行されている {{site.data.keyword.cloud_notm}} 地域のセキュア・エンドポイントにカスタム・ドメイン・ネームをマップします。 以下の地域エンドポイントを使用して、{{site.data.keyword.cloud_notm}} で組織に割り振られた URL 経路を指定します。 例えば、CNAME を `<custom-domain>.us-east.cf.cloud.ibm.com にポイントします。`

  **Cloud Foundry エンドポイント:**
  * US-SOUTH - `custom-domain.us-south.cf.cloud.ibm.com`
  * US-EAST - `custom-domain.us-east.cf.cloud.ibm.com`
  * EU-DE - `custom-domain.eu-de.cf.cloud.ibm.com`
  * EU-GB - `custom-domain.eu-gb.cf.cloud.ibm.com`
  * AU-SYD - `custom-domain.au-syd.cf.cloud.ibm.com`

## アプリケーションへのアクセス
{: #access-app}

ブラウザーで以下の URL を入力し、アプリケーションにアクセスします。ここで、`hostname` はお使いのホスト名、`mydomain` はドメイン名です。
```
http://hostname.mydomain
```

## 孤立した経路の削除
{: #remove-orphaned-route}

孤立した経路を削除するには、以下のコマンドを実行します。
```
ibmcloud app route-delete <MY_DOMAIN> -n <MY_HOSTNAME> -f
```
{: tip}

このサンプルにおいて、`domain` はご使用のドメインの名前で、`hostname` はご使用のアプリケーションの経路のホスト名です。 `ibmcloud app route-delete` コマンドについて詳しくは、コマンド `ibmcloud app route-delete -h` を入力してください。

## Kubernetes アプリにカスタム・ドメインを使用する
{: #kube-custom-domain}

IBM Cloud Kubernetes Service のホスト名のサブドメインは `containers.appdomain.cloud` です。IBM が提供する入口のサブドメインのワイルドカード `*.<cluster_name>.<region>.containers.mybluemix.net` は、ご使用のクラスターにデフォルトで登録されています。IBM 提供の TLS 証明書はワイルドカード証明書ですので、ワイルドカード・サブドメインに使用できます。カスタム・ドメインを使用する場合は、カスタム・ドメインを `*.custom_domain.net` などのワイルドカード・ドメインとして登録する必要があります。TLS を使用するには、ワイルドカード証明書を取得する必要があります。詳しくは、[名前空間内の複数ドメイン](/docs/containers?topic=containers-ingress#multi-domains)を参照してください。

[このチュートリアル](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes)をご確認ください。Web アプリケーションのスキャフォールド、それをコンテナーでローカルで実行する方法、さらにそれを IBM Kubernetes Service で作成した Kubernetes クラスターにデプロイする方法について詳しく説明されています。また、カスタム・ドメインをバインドし、環境の正常性を監視し、アプリケーションを拡張する方法についても説明されています。
