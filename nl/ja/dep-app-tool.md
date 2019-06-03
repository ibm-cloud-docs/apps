---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-06"

keywords: apps, deploy, deploying apps, toolchain, cli, cloud, devops, deployment, git, push

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# アプリのデプロイ
{: #deploying-apps}

DevOps ツールチェーンを使用して、アプリケーションを {{site.data.keyword.cloud}} にデプロイできます。 DevOps ツールチェーンを使用すると、多数の環境へのデプロイメントを自動化して、成長するアプリの管理に役立つモニタリング、ロギング、洞察、およびアラートの各サービスを素早く追加することができます。 継続的デリバリーの構成とアプリのデプロイは、{{site.data.keyword.cloud_notm}} Web コンソールかコマンド・ライン・インターフェース (CLI) のいずれかを使用して行うことができます。
{: shortdesc}

DevOps ツールチェーンは、アプリ用のチーム・ベースの開発環境を提供します。 ツールチェーンの作成時に、アプリ・サービスによって Git リポジトリーが作成されます。このリポジトリーでは、ソース・コードの表示、アプリの複製、および問題の作成と管理を行うことができます。 また、専用の GitLab 環境と、継続的デリバリー・パイプラインにアクセスすることもできます。 選択したデプロイメント・ターゲットが、[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about)、または[仮想サーバー (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial) のどれであっても、それに合わせてこれらはカスタマイズされています。

{{site.data.keyword.cloud_notm}} 開発者ダッシュボードから作成されたツールチェーンはすべて、自動デプロイメント用に構成されています。
{: note}

## {{site.data.keyword.cloud_notm}} コンソールの使用
{: deploy-console}

{{site.data.keyword.cloud_notm}} は、DevOps ツールチェーンを使用して継続的デリバリーの構成とアプリのデプロイを行える Web コンソールを提供します。

### 始める前に
{: deploy-console-before}

始めに、[{{site.data.keyword.cloud_notm}} ダッシュボード](https://{DomainName}){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")を使用して、[アプリを作成し](/docs/apps?topic=creating-apps-tutorial-getting-started#create-getting-started)、[サービスを追加します](/docs/apps?topic=creating-apps-tutorial-getting-started#resources-getting-started)。

### アプリの自動デプロイ
{: deploy-console-auto}

1. **「アプリの詳細」**ページで**「継続的デリバリーの構成 (Configure continuous delivery)」**をクリックします。
2. デプロイメント・ターゲットを選択します。 選択したターゲットの説明に従って、デプロイメント・ターゲットをセットアップします。
  * **IBM Kubernetes Service にデプロイします**。 このオプションは、高可用性のアプリケーション・コンテナーをデプロイして管理するためのワーカー・ノードというホスト・クラスターを作成します。 クラスターを作成したり、既存のクラスターにデプロイしたりすることができます。 詳しくは、[Kubernetes クラスターへのアプリのデプロイ](/docs/containers?topic=containers-app)を参照してください。
  * **Cloud Foundry にデプロイ**します。 このオプションはクラウド・ネイティブなアプリをデプロイします。基礎にあるインフラストラクチャーを管理する必要はありません。 アカウントに {{site.data.keyword.cfee_full_notm}} に対するアクセス権限がある場合は、エンタープライズ専用の Cloud Foundry アプリケーションをホストするための分離環境を作成および管理するために使用できる、**パブリック・クラウド**または**エンタープライズ環境**のデプロイヤー・タイプを選択できます。 詳しくは、[Cloud Foundry パブリックへのアプリのデプロイ](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)と[{{site.data.keyword.cfee_full_notm}} へのアプリのデプロイ](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)を参照してください。
  * **仮想サーバーにデプロイします**。 このオプションによって、仮想サーバー・インスタンスがプロビジョンされ、アプリを含むイメージがロードされ、DevOps ツールチェーンが作成され、最初のデプロイメント・サイクルが開始されます。 詳しくは、[仮想サーバーへのアプリのデプロイ](/docs/apps?topic=creating-apps-vsi-deploy)を参照してください。

### 手動によるアプリのデプロイ
{: deploy-console-manual}

正しく構成されたツールチェーンを使用すると、リポジトリー内のマスター・ブランチへのマージが行われるたびに、ビルドとデプロイのサイクルが自動的に開始されます。 

DevOps ツールチェーンからアプリを手動でデプロイすることもできます。

1. **「アプリの詳細」**ページで**「ツールチェーンの表示」**をクリックします。
2. **「Delivery Pipeline」**をクリックします。ここで、ビルドの開始、デプロイメントの管理、およびログと履歴の表示を行うことができます。

一部のアプリケーションでは継続的デリバリーは自動で有効になります。 継続的デリバリーを有効にして、Delivery Pipeline と GitHub を使用したビルド、テスト、およびデプロイメントを自動化することができます。

詳しくは、以下を参照してください。
* [ビルドとデプロイ](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)
* [ツールチェーンの作成](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)

## {{site.data.keyword.dev_cli_short}} CLI の使用
{: #deploy-cli}

{{site.data.keyword.cloud_notm}} は、開発者のワークフローを簡素化するのに役立つ堅固な CLI とプラグインを提供します。 アプリの構成方法に応じて、{{site.data.keyword.cloud_notm}} アプリを 2 つの方法のいずれかでデプロイできます。

### 始める前に
{: #deploy-cli-before}

開始する前に、[{{site.data.keyword.cloud_notm}} CLI をダウンロードしてインストールします](/docs/cli?topic=cloud-cli-ibmcloud-cli)。

CLI は、Cygwin によってサポートされていません。 このツールは Cygwin コマンド・ライン・ウィンドウ以外のウィンドウで使用してください。
{: important}

  1. 開発環境をセットアップするため、アプリのコードを新規ディレクトリーにダウンロードします。

  2. コードが置かれているディレクトリーに移動します。

  3.  アプリ・コードを更新します。 例えば、{{site.data.keyword.cloud_notm}} サンプル・アプリケーションを使用していて、アプリに `src/main/webapp/index.html` ファイルが含まれている場合は、それを変更して「`Thanks for creating ...`」行を編集できます。 アプリを {{site.data.keyword.cloud_notm}} にデプロイする前に、ローカルで実行できることを確認してください。

    `manifest.yml` ファイルをメモします。 アプリを {{site.data.keyword.cloud_notm}} にデプロイする際、このファイルを使用してアプリケーションの URL、メモリー割り振り、インスタンス数、およびその他の重要なパラメーターを判別します。

    また、`README.md` ファイルも確認してください。このファイルには、ビルド手順などの詳細情報が含まれています。

    アプリケーションが Liberty アプリである場合、再度デプロイする前にビルドする必要があります。
    {: note}

  4. IBMid を使用して {{site.data.keyword.cloud_notm}} CLI にログインします。 複数のアカウントを持っている場合、使用するアカウントを選択するように求めるプロンプトが出されます。 `-r` フラグを使用して地域を指定していない場合、地域も選択しなければなりません。
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    資格情報が拒否された場合、統合 ID を使用している可能性があります。 フェデレーテッド ID を使用してログインするには、`--sso` フラグを使用します。 詳しくは、[フェデレーテッド ID を使用したログイン](/docs/iam/federated_id?topic=iam-federated_id#federated_id)を参照してください。
    {: tip}

### アプリの自動デプロイ
{: #deploy-cli-auto}

アプリ用の DevOps ツールチェーンをまだ作成しておらず、アプリがまだ Git リポジトリー内にない場合、[`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit) コマンドを実行できます。 「DevOps の構成」のプロンプトに従い、新しいツールチェーンにデプロイします (また、新規 GitLab リポジトリーも作成します)。

アプリ用の DevOps ツールチェーンが作成されると、新規ビルドのデプロイは、ツールチェーン内のリポジトリーにコードをコミットしてプッシュするだけの単純なものになります。 

1. コミットする変更を準備します。
    ```
    git add .
    ```
2. 短いメッセージを付けて変更をコミットします。
    ```
    git commit -m "made changes"
    ```
3. マスター・ブランチ上のコミットをリモート・リポジトリーにプッシュします。
    ```
    git push origin master
    ```
4. {{site.data.keyword.cloud_notm}} コンソールからアプリの DevOps ツールチェーンを表示します。 アプリ・ディレクトリーから [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) コマンドを実行することで、{{site.data.keyword.cloud_notm}} コンソールの**アプリの詳細**ページからツールチェーンの詳細を表示できます。
5. ツールチェーン内のパイプラインを表示して、新規ビルドが開始されたことを確認します。

### 手動によるアプリのデプロイ
{: #deploy-cli-manual}

[`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) コマンドを使用して、アプリを {{site.data.keyword.cloud_notm}} に手動でデプロイできます。

  ```
  ibmcloud dev deploy <APP_NAME>
  ```
  {: codeblock}

### 関連情報
{: #deploy-cli-related}

CLI を使用した {{site.data.keyword.cloud_notm}} へのアプリのデプロイについて詳しくは、以下を参照してください。

* [{{site.data.keyword.dev_cli_short}} CLI を使用した IBM Cloud Environments へのデプロイ](https://www.ibm.com/cloud/blog/deploying-to-ibm-cloud-environments-with-ibm-cloud-developer-tools-cli){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")
