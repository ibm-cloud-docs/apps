---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-04"

keywords: apps, credentials, service, add service credentials, environment, deployment

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# 手動によるデプロイメント環境へのサービス資格情報の追加
{: #credentials_overview}

アプリ・ロジックでは、データベース API キーやパスワードなどの機密性の高いサービス資格情報は、アプリケーションが実行される環境から取得することが望まれます。 この方法では、資格情報をソース・コード・リポジトリー内に保持する必要はありません。
{: shortdesc}

スターター・キットを使用してアプリを作成すると、環境が自動的に準備されます。 アプリをデプロイする前にサービスをスターター・キットに接続すると、サービス資格情報が自動的に環境に追加されます。

以下のいずれかのシナリオでは、デプロイメント環境にサービス資格情報を手動で追加する必要があります。

 * 独自のコードを持ち込む (Bring Your Own Code)。
 * アプリのデプロイ後に、スターター・キット・ベースのアプリにサービスを追加する。

サービス資格情報を追加するプロセスは、デプロイメント・ターゲットとご使用のプログラミング言語によって異なります。 デプロイメント・ターゲットのサービス資格情報の構成について詳しくは、ご使用のホスト環境固有の資料を参照してください。

  * [{{site.data.keyword.containerlong}}](/docs/containers?topic=containers-service-binding#adding_app)
  * Cloud Foundry Public または {{site.data.keyword.cfee_full}}
  * 仮想サーバー・インスタンス (ローカル Docker コンテナー)

多くの言語とフレームワークには、アプリ固有の構成と環境固有の構成の両方に対して、標準ライブラリーが用意されています。 詳しくは、以下のプログラミング・ガイドを参照してください。

* [Java: サービス資格情報の処理](/docs/java?topic=cloud-native-configuration)
* [Node.js 環境の構成](/docs/node?topic=nodejs-configure-nodejs)
* [Spring 環境の構成](/docs/java?topic=java-spring-configuration)
* [Swift 環境の構成](/docs/swift?topic=swift-configuration)
* [Go 環境の構成](/docs/go?topic=go-configure-go-env)
