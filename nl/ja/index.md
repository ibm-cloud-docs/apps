---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-20"

keywords: getting started apps, create app tutorial, add services, deploy apps, create app, app tutorial

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 入門チュートリアル
{: #getting-started}

{{site.data.keyword.cloud}} で企業向けのモバイル・アプリケーションおよび Web アプリケーションを作成でき、{{site.data.keyword.cloud_notm}} でホストされているクラウド拡張機能を利用できます。 開始する方法にはいくつかあります。 プロセスを管理してくれるスターター・キットを使用してアプリを作成するか、または、何が必要かが分かっている場合は、必要なリソースと共に最初からアプリを作成するか、既存のリポジトリーを使用して独自のコードを持ち込みます。
{: shortdesc}

最新化してクラウドに取り入れる[既存のコード](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc)があるか、[まったく新しいアプリケーション](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit)を開発しているかにかかわらず、{{site.data.keyword.cloud_notm}} で使用可能なサービスおよびランタイム・フレームワークが含まれる急速に成長しているエコシステムを活用できます。

何から始めればよいか迷っていますか? 以下の図に、スターター・キットを使用する方法、または独自のコードを {{site.data.keyword.cloud_notm}} に取り込む方法でアプリを作成する手順の概要を示します。

![開発者エクスペリエンスの概要](images/dev-journey.png "{{site.data.keyword.cloud_notm}} におけるアプリの作成の概要")

## 始める前に
{: #prereqs-getting-started}

アプリの作成は、{{site.data.keyword.cloud_notm}} コンソールまたはコマンド・ライン・インターフェース (CLI) を使用して行うことができます。 CLI を使用する場合は、[インストール手順](/docs/cli?topic=cloud-cli-getting-started)を参照してください。

## ステップ 1. アプリの作成
{: #create-getting-started}

以下のエントリー・ポイントのいずれかを選択して、アプリを作成します。

* [事前構成済みのスターター・キット](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit)はユース・ケース固有のものです。これを使用すると、実動用のアプリをさまざまなプログラミング言語およびアーキテクチャー・パターンで作成できます。
* [基本スターター・キット](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch)を使用すると、アプリのタイプ (モバイルまたはバックエンド)、言語とフレームワーク、サービス、デプロイメント・ターゲットを選択してアプリを作成できます。
* 既存の独自のコンテンツ・リポジトリーにリンクすることによって、[独自のコードを持ち込みます](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc)。 アプリと Docker イメージは同じリポジトリー内に配置する必要があります。
* [{{site.data.keyword.dev_cli_long}} コマンド・ライン・インターフェース (CLI)](/docs/apps?topic=creating-apps-create-deploy-app-cli) では、CLI を使用したアプリの作成とデプロイが可能になります。
* [{{site.data.keyword.cloud_notm}} カタログ ](https://{DomainName}/catalog){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") で、今日作成して使用を開始できるアプリおよびサービスを参照または検索する。
* [IBM Developer コード・パターン ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://developer.ibm.com/patterns/){:new_window} を使用すれば、素早くアプリを作成して {{site.data.keyword.cloud_notm}} にデプロイすることができます。 詳しくは、[コード・パターン](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern)を参照してください。

## ステップ 2. サービスの追加
{: #resources-getting-started}

スターター・キットを使用してアプリを作成する場合、必須サービスは自動的に作成されます。 アプリを作成するとすぐに表示される、コンソールの**「アプリの詳細」**ページから、アプリにさらにサービスを接続できます。

アプリの作成後にサービスを追加する場合、[{{site.data.keyword.cloud_notm}} ダッシュボード ![外部リンクのアイコン](../../icons/launch-glyph.svg "外部リンクのアイコン")](https://{DomainName}) に移動し、対象アプリを見つけてその名前をクリックします。 **「アプリの詳細」**ページが表示され、サービス・インスタンスを作成したり、既存のサービスを接続したりできます。

または、CLI を使用して次のコマンドを実行し、サービスをアプリに追加することもできます。 ご使用のアカウントで既に使用可能になっている既存のサービスを選択することも、サービスを追加することもできます。
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

詳しくは、[アプリのデプロイ](/docs/apps?topic=creating-apps-deploying-apps)を参照してください。

### CLI の使用
{: #cli-getting-started}

CLI を使用してアプリをデプロイするには、`ibmcloud dev deploy` コマンドを実行します。 詳しくは、[CLI を使用したアプリの作成およびデプロイ](/docs/apps?topic=creating-apps-create-deploy-app-cli)を参照してください。

これで、反復型開発と継続的デリバリーのための設定ができました。

アプリのデプロイについて詳しくは、[アプリのデプロイ](/docs/apps?topic=creating-apps-deploying-apps)を参照してください。

## 関連情報
{: #related-getting-started}

稼働に役立つ[プログラミング・ガイド](https://{DomainName}/docs/home/build){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") が言語ごとに用意されています。 {{site.data.keyword.baremetal_short}}から、サーバーレス機能としての実行まで、{{site.data.keyword.cloud_notm}} インフラストラクチャーを使用してアプリをホストするための多数のオプションがあります。
