---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-17"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# スターター・キットを使用したアプリの作成
{: #tutorial-starterkit}

スターター・キットを使用して、アプリケーションを素早く開始し、今後の開発に備えることができます。 スターター・キットとプログラミング言語を選択し、アプリを作成した後、自動的にアプリをデプロイするように DevOps ツールチェーンをセットアップします。
{: shortdesc}

一連のスターター・キットから選択してアプリを作成することができます。ビルド・オプションを自分でカスタマイズする場合に使用できる、基本スターター・キットも用意されています。 いずれの方法でも、アプリをデプロイするための DevOps ツールチェーンが自動的に作成されます。 即時検査用のコードをダウンロードすることもできます。

{{site.data.keyword.cloud_notm}} には、(Watson などの) 各種関心分野の開発者ポータル、または (モバイルまたは Web アプリなどの) デジタル・チャネル用の開発者ポータルがあります。 これらのポータルには、**メニュー**・アイコン![メニュー・アイコン](../../icons/icon_hamburger.svg)からアクセスできます。

各開発者ポータルには、ポータルのフォーカス・エリアに関連したスターター・キットが用意されています。 これらのポータルは、すぐに実動可能な、機能するアプリを数分で作成するための、一貫性のある直感的なワークフローを提供します。

スターター・キットは、以下の多くのカテゴリーで使用可能です。
* [Watson](https://{DomainName}/developer/watson/dashboard){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")
* [Apple](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")
* [モバイル](https://{DomainName}/developer/mobile/dashboard){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")
* [Web App ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")

詳しくは、[スターター・キットとは何ですか?](/docs/apps?topic=creating-apps-starter-kits) を参照してください。

## ステップ 1. ツールのインストール
{: #prereqs-starterkit}

* [開発者ツール](/docs/cli?topic=cloud-cli-getting-started)をインストールします。
* Docker は開発者ツールの一部としてインストールされます。 ビルド・コマンドが機能するためには、Docker が実行中でなければなりません。 Docker アカウントを作成して、Docker アプリを実行し、サインインする必要があります。
* アプリを {{site.data.keyword.cfee_full}} にデプロイする計画の場合は、[{{site.data.keyword.cloud_notm}} アカウントを準備する](/docs/cloud-foundry?topic=cloud-foundry-prepare)必要があります。

## ステップ 2. アプリの作成
{: #create-starterkit}

スターター・キットは、{{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}で多数の言語とフレームワークで使用可能です。 言語やタイプなどのカテゴリー・フィルターを使用して、選択を絞り込むことができます。

1. {{site.data.keyword.dev_console}} コンソールの[「スターター・キット」](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン") ページから、スターター・キットを選択して、**「アプリの作成」**をクリックします。 

    スターター・キットの内容を表示するには、タイルを選択して詳細を読みます。 基本スターター・キットを使用してアプリをカスタマイズする場合は、**「アプリの作成」**タイルを選択します。
    {: tip}

2. アプリに名前を付け、リソース・グループを選択します。

3. オプション。 アプリを分類するためのタグを指定します。 詳しくは、『[タグの処理](/docs/resources?topic=resources-tag)』を参照してください。

4. ご使用の言語とフレームワークを選択します。 一部のスターター・キットは、1 つの言語でしか使用できない場合があります。

5. **「作成」**をクリックします。

素晴らしいスタートです。 これでアプリが作成されました。

サービスの追加や継続的デリバリーのセットアップを行う前にコードを検査するには、「アプリの詳細」ページで**「コードのダウンロード (Download code)」**をクリックします。 ダウンロードした圧縮ファイル内の `README.md` ファイルを参照して、スターター・アプリを稼働状態にするためにさらに操作が必要かどうかを確認します。
{: tip}

## ステップ 3. サービスの追加 (オプション)
{: #resources-starterkit}

特定のサービスを必要とするスターター・キットの場合は、自動的にプロビジョンされるサービス・インスタンスが自動的に作成され、アプリに接続されます。

Watson のコグニティブ機能でアプリを拡張するサービスを追加したり、モバイル・サービスやセキュリティー・サービスを追加したりすることもできます。 このチュートリアルでは、データを管理する場所を追加します。

1. 「アプリの詳細」ページで、このアプリに接続するサービスの有無に応じて、**「サービスの作成」**または**「既存のサービスの接続 (Connect existing services)」**をクリックします。
2. 必要なサービスの種類を選択し、プロンプトに従って、アプリに既存のサービスを追加するか、サービス・インスタンスを作成します。

必要なサービスをすべて追加すると、それらが「アプリの詳細」ページに表示されます。

## ステップ 4. デプロイメント・ターゲットの選択と継続的デリバリーの構成
{: #target-starterkit}

デプロイメント・ターゲットを選択すると、アプリ用の DevOps ツールチェーンが自動的に作成されます。 このツールチェーンには、アプリのデプロイメント状況を示すデリバリー・パイプラインが含まれています。 生成された新規アプリは、ツールチェーンの一部である GitLab リポジトリーにプッシュされます。

DevOps ツールチェーンを有効にすると、アプリ用のチーム・ベースの環境が作成されます。 ツールチェーンの作成時に、アプリ・サービスによって Git リポジトリーが作成されます。このリポジトリーでは、ソース・コードの表示、アプリの複製、および問題の作成と管理を行うことができます。 また、専用の GitLab 環境と、継続的デリバリー・パイプラインにアクセスすることもできます。 選択したデプロイメント・ターゲットが、[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about)、または[仮想サーバー (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial) のどれであっても、それに合わせてこれらはカスタマイズされています。

{{site.data.keyword.cloud_notm}} 開発者ダッシュボードから作成されたツールチェーンはすべて、自動デプロイメント用に構成されています。
{: note}

デプロイメント・ターゲットを選択して、継続的デリバリーを構成するには、以下の手順を実行します。

1. 「アプリの詳細」ページで、**「継続的デリバリーの構成 (Configure continuous delivery)」**をクリックします。
2. デプロイメント・ターゲットを選択します。 選択したターゲットの説明に従って、デプロイメント・ターゲットをセットアップします。
  * **[IBM Kubernetes Service](/docs/containers?topic=containers-app) にデプロイ**します。 このオプションは、高可用性のアプリ・コンテナーをデプロイして管理するためのワーカー・ノードというホスト・クラスターを作成します。 クラスターを作成したり、既存のクラスターにデプロイしたりすることができます。
  * **Cloud Foundry にデプロイ**します。 このオプションはクラウド・ネイティブなアプリをデプロイします。基礎にあるインフラストラクチャーを管理する必要はありません。 アカウントに {{site.data.keyword.cfee_full_notm}} に対するアクセス権限がある場合は、エンタープライズ専用の Cloud Foundry アプリをホストするための分離環境を作成および管理するために使用できる、**[パブリック・クラウド](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)**または**[エンタープライズ環境](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**のデプロイヤー・タイプを選択できます。
  * **仮想サーバーにデプロイします**。 このオプションによって、仮想サーバー・インスタンスがプロビジョンされ、アプリを含むイメージがロードされ、DevOps ツールチェーンが作成され、最初のデプロイメント・サイクルが開始されます。 詳しくは、[仮想サーバーへのアプリのデプロイ](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server)を参照してください。

    VSI デプロイメントは、一部のスターター・キットで使用できます。 この機能を使用するには、[{{site.data.keyword.cloud_notm}} ダッシュボード](https://{DomainName})に移動し、**「アプリ」**タイルで**「アプリの作成」**をクリックします。
    {: note}

デプロイメント・ターゲットを選択して構成すると、「アプリの詳細」ページに、継続的デリバリーが構成されたことが表示されます。 **「リポジトリーの表示」**をクリックすると、アプリのソース・コードを含むリポジトリーを表示できます。

## ステップ 5. アプリのデプロイ
{: #deploy-starterkit}

{{site.data.keyword.cloud_notm}} 開発者ダッシュボードから作成された DevOps ツールチェーンは、自動デプロイメント用に構成されています。
{: note}

デプロイメント・ターゲットを選択した後、新しいツールチェーンのパイプライン・コンポーネントを開いて、最初のビルドとデプロイメントのプロセスを開始すると、数分後には新しいアプリを確認できます。

1. 「アプリの詳細」ページで、**「ツールチェーンの表示」**をクリックします。
2. **「Delivery Pipeline」**をクリックします。ここで、ビルドの開始、デプロイメントの管理、およびログと履歴の表示を行うことができます。

正しく構成されたツールチェーンを使用すると、リポジトリー内のマスター・ブランチへのマージが行われるたびに、ビルドとデプロイのサイクルが自動的に開始されます。 詳しくは、[ビルドとデプロイ](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)を参照してください。

[`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) コマンドを実行して、アプリをコマンド・ラインからデプロイできます。 詳しくは、[CLI を使用したアプリのデプロイ](/docs/apps?topic=creating-apps-deploying-apps#deploy-cli)を参照してください。

## ステップ 6. アプリが実行中であることの確認
{: #verify-starterkit}

アプリのデプロイ後に、Delivery Pipeline またはコマンド・ラインにアプリの URLが示されます。

1. DevOps ツールチェーンから、**「Delivery Pipeline」**をクリックし、**「デプロイ・ステージ」**を選択します。
2. **「ログおよび履歴の表示」**をクリックします。
3. ログ・ファイルで、アプリ URL を見つけます。

    ログ・ファイルの末尾で `urls` または `view` という語を探します。 例えば、`urls: my-app-devhost.mybluemix.net` または `View the application health at: http://<ipaddress>:<port>/health` のような行がログ・ファイル内で見つかります。

4. ご使用のブラウザーでその URL にアクセスします。 アプリが実行されている場合は、`Congratulations` または `{"status":"UP"}` を含むメッセージが表示されます。

コマンド・ラインを使用している場合は、[`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) コマンドを実行して、アプリの URL を表示します。 次に、ブラウザーでその URL にアクセスします。
