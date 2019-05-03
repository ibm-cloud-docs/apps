---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-10"

keywords: getting started apps, create app tutorial, add resources, deploy apps, create app, app tutorial

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 入門チュートリアル
{: #tutorial-getting-started}

{{site.data.keyword.cloud}} で企業向けのモバイル・アプリケーションおよび Web アプリケーションを作成でき、{{site.data.keyword.cloud_notm}} でホストされているクラウド拡張機能を利用できます。 開始する方法にはいくつかあります。 プロセスを管理してくれるスターター・キットを使用してアプリを作成するか、または、何が必要かが分かっている場合は、必要なリソースと共に最初からアプリを作成するか、既存のリポジトリーを使用して独自のコードを持ち込みます。
{: shortdesc}

最新化してクラウドに取り入れる[既存のコード](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc#tutorial-byoc)があるか、[まったく新しいアプリケーション](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit)を開発しているかにかかわらず、{{site.data.keyword.cloud_notm}} で使用可能なサービスおよびランタイム・フレームワークが含まれる急速に成長しているエコシステムを活用できます。

何から始めればよいか迷っていますか? 以下の図をヒントにしてみてください。

![開発者エクスペリエンスの概要](images/dev-journey.png "開発者エクスペリエンスの概要")

## 始める前に
{: #prereqs-getting-started}

アプリの作成は、{{site.data.keyword.cloud_notm}} コンソールまたはコマンド・ライン・インターフェース (CLI) を使用して行うことができます。 CLI を使用する場合は、[インストール手順](/docs/cli?topic=cloud-cli-ibmcloud-cli)を参照してください。

## ステップ 1. アプリの作成
{: #create-getting-started}

以下のエントリー・ポイントのいずれかを選択して、アプリを作成します。

* [スターター・キット](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit)はユース・ケース固有で、実動準備完了のアプリをさまざまなプログラミング言語およびアーキテクチャー・パターンで生成します。
* [IBM Developer コード・パターン ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/patterns/){:new_window} を使用すれば、素早くアプリを作成して {{site.data.keyword.cloud_notm}} にデプロイすることができます。詳しくは、[コード・パターン](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern)を参照してください。
* 既存の独自のコンテンツ・リポジトリーにリンクすることによって、[独自のコードを持ち込みます](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc)。アプリと Docker イメージは同じリポジトリー内に配置する必要があります。
* 何が必要なのかが分かっている場合、ブランクのスターター・キットを使用して、必要なサービスが含まれる[カスタム・アプリ](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch)を最初から作成します。
* [CLI および開発者ツール](/docs/apps?topic=creating-apps-create-deploy-app-cli)を使用して、カスタム・アプリまたはスターター・キット・アプリを作成してデプロイします。
* [{{site.data.keyword.cloud_notm}} カタログ ](https://{DomainName}/catalog){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") で、今日作成して使用を開始できるアプリおよびサービスを参照または検索する。

## ステップ 2. サービスの追加
{: #resources-getting-started}

スターター・キットを使用してアプリを作成する場合、サービスは自動的に作成されます。 コンソールで**「アプリの詳細」**ページの**「サービスの作成」**をクリックすることによって、さらにサービスをアプリに関連付けることができます。

CLI を使用して次のコマンドを実行し、サービスをアプリに追加します。 ご使用のアカウントで既に使用可能になっている既存のサービスを選択することも、サービスを追加することもできます。 
```
ibmcloud dev edit
```
{: codeblock}

詳しくは、[アプリへのサービスの追加](/docs/apps?topic=creating-apps-add-resource)を参照してください。

## ステップ 3. アプリのデプロイ
{: #deploy-getting-started}

コンソールまたは CLI を使用してアプリをデプロイできます。

### コンソールの使用
{: #console-getting-started}

コンソールを使用してアプリをデプロイするには、以下の手順を実行します。

1. **「アプリの詳細」**ページで**「継続的デリバリーの構成 (Configure continuous delivery)」**をクリックします。
2. デプロイメント・ターゲットを選択し、ツールチェーン設定を選択してから**「作成」**をクリックします。 {{site.data.keyword.cloud_notm}} は、Git リポジトリーと継続的デリバリー・パイプラインを備えたオープン・ツールチェーンを自動的に作成します。
3. 新しいツールチェーンのパイプライン・ステージを開いて、ビルドとデプロイメントのプロセスを表示すると、数分後に新しいアプリが表示されます。

詳しくは、『アプリのデプロイと統合』セクションで、さまざまなデプロイメントについてのトピックの目次を参照してください。

### CLI の使用
{: #cli-getting-started}

CLI を使用してアプリをデプロイするには、`ibmcloud dev deploy` コマンドを実行します。 詳しくは、[CLI を使用したアプリの作成およびデプロイ](/docs/apps?topic=creating-apps-create-deploy-app-cli)を参照してください。

これで、反復型開発と継続的デリバリーのための設定ができました。

## 関連情報
{: #related-getting-started}

稼働に役立つ[プログラミング・ガイド](https://{DomainName}/docs/home/build){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") が言語ごとに用意されています。 {{site.data.keyword.baremetal_short}}から、サーバーレス機能としての実行まで、{{site.data.keyword.cloud_notm}} インフラストラクチャーを使用してアプリをホストするための多数のオプションがあります。
