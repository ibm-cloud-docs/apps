---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-02"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# カスタム・ドメインの作成と使用
{: #updatingapps}

ドメインは、{{site.data.keyword.Bluemix_notm}} で各組織に割り振られた URL 経路を指定します。 カスタム・ドメインを使用するには、パブリック DNS サーバーにカスタム・ドメインを登録し、{{site.data.keyword.Bluemix_notm}} 内にカスタム・ドメインを構成する必要があります。 次に、パブリック DNS サーバー上の {{site.data.keyword.Bluemix_notm}} システム・ドメインにカスタム・ドメインをマップする必要があります。 ご使用のカスタム・ドメインがシステム・ドメインにマップされると、そのカスタム・ドメインへの要求は {{site.data.keyword.Bluemix_notm}} 内のアプリケーションに経路指定されます。
{:shortdesc}

カスタム・ドメインの作成と使用には、{{site.data.keyword.Bluemix_notm}} コンソールまたはコマンド・ライン・インターフェースのいずれかを使用できます。

## {{site.data.keyword.Bluemix_notm}} コンソールの使用

コンソールを使用して組織のカスタム・ドメインを作成するには、以下のステップを実行します。

1. **「管理」** > **「アカウント」** > **「Cloud Foundry の組織」**に移動します。
2. カスタム・ドメインを作成する組織の名前をクリックします。
3. **「ドメイン」**タブをクリックします。
4. **「ドメインの追加 (Add a domain)」**をクリックして、ドメイン名を入力して地域を選択します。
5. 更新を確認します。 **「追加」**をクリックします。

例えば、`*.mycompany.com` を使用して経路 `www.mybluemix.com` をアプリに関連付けることができます。 `example.mycompany.com` を使用して、経路 `www.example.mybluemix.com` をアプリに関連付けることもできます。
{: tip}

カスタム・ドメインを使用した経路をアプリケーションに追加します。

1. **「メニュー」**アイコン ![メニュー・アイコン](../icons/icon_hamburger.svg) > **「ダッシュボード」**をクリックし、次に、経路を追加するアプリケーションの行をクリックします。 **「概要」** ページが表示されます。
2. **「経路」**メニューで、**「経路の編集」**を選択します。
3. **「経路の追加」**をクリックし、アプリケーションに使用する経路を指定します。
4. **「保存」**をクリックして更新を確認します。

## {{site.data.keyword.Bluemix_notm}} コマンド・ライン・インターフェースの使用

1. 次のコマンドを入力して、自分の組織のカスタム・ドメインを作成します。

   ```
   ibmcloud app domain-create <your org name> mydomain
   ```

2. カスタム・ドメインを使用した経路をアプリケーションに追加します。 CF アプリの場合、次のコマンドを入力します。

   ```
   ibmcloud app route-map myapp mydomain -n host_name

   ```

   コンテナー・グループの場合、次のコマンドを入力します。

   ```
   cf ic route map -n host_name -d mydomain mycontainergroup

   ```

{{site.data.keyword.Bluemix_notm}} でカスタム・ドメインを構成した後、登録された DNS サーバー上の {{site.data.keyword.Bluemix_notm}} システム・ドメインにカスタム・ドメインをマップします。

1. DNS サーバー上のカスタム・ドメイン・ネームに 'CNAME' レコードをセットアップします。 CNAME レコードのセットアップ手順は、使用している DNS プロバイダーによって異なります。 例えば、GoDaddy を使用する場合、GoDaddy の[ドメインのヘルプ ![「外部リンク」アイコン](../icons/launch-glyph.svg "「外部リンク」アイコン")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window}にあるガイダンスに従ってください。
2. アプリケーションが実行されている {{site.data.keyword.Bluemix_notm}} 地域のセキュア・エンドポイントにカスタム・ドメイン・ネームをマップします。 以下の地域エンドポイントを使用して、{{site.data.keyword.Bluemix_notm}} で組織に割り振られた URL 経路を指定します。

  * US-SOUTH - `secure.us-south.bluemix.net`
  * US-EAST - `secure.us-east.bluemix.net`
  * EU-DE - `secure.eu-de.bluemix.net`
  * EU-GB - `secure.eu-gb.bluemix.net`
  * AU-SYD - `secure.au-syd.bluemix.net`

ブラウザーまたはコマンド・ライン・インターフェースで、`myapp` アプリケーションにアクセスするための URL を次のように入力します。

```
http://host_name.mydomain

```

孤立した経路を削除するには、以下のコマンドを実行します。

```
ibmcloud app route-delete domain -n hostname -f
```
{: tip}

このサンプルにおいて、`domain` はご使用のドメインの名前で、`hostname` はご使用のアプリケーションの経路のホスト名です。 `ibmcloud app route-delete` コマンドについて詳しくは、コマンド `ibmcloud app route-delete -h` を入力してください。
