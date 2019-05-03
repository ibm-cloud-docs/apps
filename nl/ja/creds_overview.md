---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, credentials

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# 資格情報の概要
{: #credentials_overview}

デプロイメント環境にサービス資格情報を手動で追加する方法について説明します。
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

一般的に、アプリケーション・ロジックでは、データベース API キーやパスワードなどの機密性の高いサービス資格情報は、アプリケーションが実行される環境から取得することが望まれます。 この方法では、資格情報をソース・コード・リポジトリー内に保持しません。 継続的統合環境、実動前環境、および実稼働環境のデータベースは、互いに隔離されます。

スターター・キット・テンプレートを使用してアプリを作成すると、環境が自動的に準備されます。 デプロイメント・ターゲットが以下のいずれであろうと、関係ありません。
  * [Kubernetes](/docs/apps?topic=creating-apps-add-credentials-kube)
  * [Cloud Foundry パブリックまたは Cloud Foundry エンタープライズ環境](/docs/apps?topic=creating-apps-add-credentials-cf)
  * [仮想サーバー・インスタンス (ローカル Docker も含む)](/docs/apps?topic=creating-apps-add-credentials-vsi)
  
環境を構成する方法についての手順が用意されています。 スターター・キットは、依存ライブラリーを使用するコードを生成して、任意のデプロイメント・ターゲットで実行できるようにコードを移植可能にします。 最後に、アプリケーションが実行されているデプロイメント・ターゲットを検出するためにブランチ・ロジックは使用されません。

その後は、管理者または DevOps エンジニアが環境を準備する責任を負い、アプリケーションが必要な値を使用できるように、適切なアクセス制御および構成を設定します。

「継続的デリバリーの構成 (Configure continuous delivery)」は、以下の主要なタスクを実行する一回限りのステップです。
 * デプロイメント・ターゲットにサービス、リソース、および資格情報を準備する。
 * 環境内の資格情報を正しく参照するコードを使用することで、アプリをビルドしてその環境にデプロイするための DevOps ツールチェーンを作成する。

ただし、以下のシナリオでは、ユーザーがデプロイメント・ターゲットを準備する必要があります。
 * 独自のコードを持ち込む (Bring Your Own Code)。
 * ブランクのスターター・キット・テンプレートから開始する。
 * デプロイされた後のスターター・キット・ベースのアプリにサービスを追加する。

環境の準備は、アプリに関連付けられたすべてのサービスのすべての資格情報を対象に常に実行され、すべての `services` が `manifest.yml` 内にリストされますが、`mappings.json` ファイル内には、必ずしもすべての資格情報参照が配置されるわけではありません。その場合、そのような参照はユーザー自身が配置する必要があります。 デプロイメント・ターゲットを決定した後、`IBMCloudEnv` ライブラリーの抽象化が不要であれば、決定したデプロイメントに適した『ユーザー作成コード + (デプロイメント・ターゲット)』のセクションを参照してください。
{: important}

一部のスターター・キットは、`IBMCloudEnv` 依存関係、`manifest.yml` ファイル、および `mappings.json` ファイルへの参照をいっさい組み込みません。
{: important}
