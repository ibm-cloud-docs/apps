---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 独自のコードを Kubernetes クラスターにデプロイする
{: #tutorial-byoc-kube}

既存のアプリ・リポジトリーを使用して、{{site.data.keyword.cloud}} でアプリを作成する方法について説明します。 既存の DevOps ツールチェーンを接続するか、ツールチェーンを作成して、アプリを Kubernetes クラスター内のセキュアなコンテナーに継続的にデリバリーできます。 このチュートリアルでは、変更を自動的にビルドし、Kubernetes クラスター内のデプロイ済みアプリまで伝搬できるように、継続的統合 DevOps パイプラインのセットアップを支援します。
{: shortdesc}

作動中バックエンド・アプリケーションのコード・ベースを含んだソース・コード・リポジトリーが既に存在する場合、{{site.data.keyword.cloud_notm}} は、そのアセットを、製品全体を構成するすべてのアセットを集約したビューの一部として編成するのを支援します。 DevOps ツールチェーン・フィーチャーを使用すると、{{site.data.keyword.cloud_notm}} によって、スケーラブルな DevOps ワークフローを立ち上げ、稼働することが可能になります。 このチュートリアルは、経験を積んだ開発者または DevOps エンジニアがターゲットの {{site.data.keyword.cloud_notm}} Kubernetes クラスターを獲得および構成し、DevOps ツールチェーンを構成および実行するまでのすべてを、クラウドのベスト・プラクティスを指針として行えるように支援します。

_クラスター_ とは、アプリの高可用性を維持する一連のリソース、ワーカー・ノード、ネットワーク、ストレージ・デバイスのことです。 クラスターを作成した後、アプリをコンテナーにデプロイできます。
{: tip}

## 始める前に
{: #prereqs-byoc-kube}

* アプリを作成します。 詳しくは、[独自のコード・リポジトリーからのアプリの作成](/docs/apps/tutorials/tutorial_byoc.html#tutorial-byoc)を参照してください。
* [{{site.data.keyword.cloud_notm}} コンソール ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://{DomainName}){: new_window} で、**「メニュー」**アイコン ![「メニュー」アイコン](../../icons/icon_hamburger.svg) をクリックし、**「コンテナー」**を選択して、[Kubernetes クラスターを構成](/docs/containers/container_index.html#container_index)します。
* アプリが Docker で実行されることを確認するために、以下のコマンドを実行します。
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install`
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* 次に、`http://localhost/springboothelloworld/sayhello` などの URL にアクセスします。 Ctrl + C キーを押して Docker の実行を停止します。

## アプリへのリソースの追加 (オプション)
{: #resources-byoc-kube}

アプリケーションにサービス・リソースを追加すると、{{site.data.keyword.cloud_notm}} によってサービスが自動的に作成されます。 サービスのタイプによってプロビジョンのプロセスが異なる場合があります。 例えば、データベース・サービスはデータベースを作成し、
モバイル・アプリケーションのプッシュ通知サービスは構成情報を生成します。 {{site.data.keyword.cloud_notm}} は、サービス・インスタンスを使用してサービスのリソースをアプリケーションに提供します。 サービス・インスタンスは Web アプリケーション間で共有できます。

このプロセスでは、サービス・インスタンスをプロビジョンし、リソース・キー (資格情報) を作成し、それをアプリにバインドします。 詳しくは、[アプリへのサービスの追加](/docs/apps/reqnsi.html#add-resource)を参照してください。

サービス・リソースをアプリに追加した後、そのサービスの資格情報をデプロイメント環境にコピーする必要があります。 詳しくは、[Kubernetes 環境への資格情報の追加](/docs/apps/creds_kube.html#add_credentials)を参照してください。

## デプロイメントに向けたアプリの準備
{: #deploy-byoc-kube}

このステップでは、DevOps ツールチェーンをアプリケーションに接続し、{{site.data.keyword.cloud_notm}} Kubernetes サービスでホストされている Kubernetes クラスターにデプロイされるように構成します。

DevOps ツールチェーンは柔軟であり、シェル・スクリプト実行の任意のステージを管理下で実行できます。 つまり、DevOps ツールチェーンでは、ほとんどのことを行うことができます。 このセクションのスコープでは、拡大される DevOps に対応する「将来の保証」およびクラウドのベスト・プラクティスに留意しながら、Kubernetes クラスターへのアプリのデプロイメントに焦点を当てます。

アプリ、ツールチェーン、およびリポジトリーの間のリンクを設定することは、製品アセットを編成するためのステップです。 また、ソース・リポジトリーのビューと、DevOps ワークフロー、実行中アプリ・インスタンス、および従属するサービスとを、すべてのデプロイメント・ターゲットにわたって集約するのにも役立ちます。

「ツールチェーンの接続 (Connect Toolchain)」ページでは、以下のいくつかのオプションがあります。

* 既存のツールチェーンにアプリを接続する。
* リポジトリーを含んでいない既存のツールチェーンにアプリを接続する。 その後、ツールチェーンをリポジトリーに後で接続します。
* 新規ツールチェーンにアプリを接続する。

### 既存のツールチェーンにアプリを接続する
{: #connect_toolchain_repo}

アプリの作成時に指定した Git リポジトリーに既に接続されている DevOps ツールチェーンが 1 つ以上ある場合、それらのツールチェーンが**「リポジトリーあり (With repo)」**表に表示されます。 ツールチェーンは、アプリで定義したのと同じリポジトリーからソースを取得するように構成される必要があります。 それらのツールチェーンのいずれかを選択して、アプリに接続することをお勧めします。

### リポジトリーを含んでいない既存のツールチェーンにアプリを接続する
{: #connect_toolchain_notrepo}

アカウントに関連付けられている DevOps ツールチェーンが 1 つ以上ありながら、それらが、アプリの作成時に指定した Git リポジトリーに接続されていない場合、それらのツールチェーンが**「リポジトリーなし (without your repo)」**表に表示されます。 これらのツールチェーンのいずれかを選択してアプリに接続できますが、リポジトリーをそのツールチェーンに手動で追加する必要もあります。

リポジトリーをツールチェーンに追加する方法について詳しくは、以下を参照してください。

 * [Git Repos and Issue Tracking の構成](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitbluemix)
 * [GitHub の構成](/docs/services/ContinuousDelivery/toolchains_integrations.html#github)
 * [GitLab の構成](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitlab)


### 新規ツールチェーンにアプリを接続する
{: #toolchain-byoc-kube-create}

コード・リポジトリーはいっさい変更せずに、DevOps ツールチェーンの作成を完全に制御することを希望する場合は、ツールチェーンを最初から作成します。 また、アプリをビルドして Kubernetes クラスターにデプロイするためのすべての統合も作成します。 

1. 「ツールチェーンの作成」ページで、**「Build your own ツールチェーン」**テンプレートをクリックします。
2. ツールチェーンの名前を入力し、地域とリソース・グループ (デフォルト) を選択し、**「作成」**をクリックします。

新規アプリからツールチェーンを作成することを選択すると、DevOps ダッシュボードの[「ツールチェーンの作成」](https://{DomainName}/devops/create)ページが、ブラウザーの新しいタブで開きます。 そのタブでツールチェーンを作成し、構成した後は、アプリの「ツールチェーンの接続 (Connect a toolchain)」ページに戻り、ページをリフレッシュする必要があります。
{:tip}

DevOps ツールチェーンを最初から作成することを希望しない場合は、[`ibmcloud dev enable` コマンド](/docs/cli/idt/commands.html#enable)を使用して既存のコードをクラウド対応にすることができます。 このコマンドにより、リポジトリーにチェックインする DevOps ツールチェーン・テンプレートが生成されます。 次に、DevOps ツールチェーンが作成する命令セットとしてそのテンプレートを使用します。 詳しくは、[CLI の資料](/docs/apps/create-deploy-cli.html#byoc-cli)を参照してください。

## GitHub 統合の追加
{: #github-byoc-kube}

ツールチェーンがリポジトリーに Web フックを設定して、そのリポジトリー内のプル要求およびコード・プッシュがツールチェーンに POST を送信するように、GitHub リポジトリーの統合を使用して DevOps ツールチェーンを構成します。 

1. DevOps ツールチェーン・テンプレートで、**「ツールの追加」**をクリックします。
2. **「GitHub」**を選択します (ご使用のリポジトリーがパブリック GitHub または Enterprise GitHub 上にある場合)。
3. GitHub サーバーの URL を選択または入力します。
4. `「GitHub で認証が必要 (Unauthorized on GitHub)」`メッセージが表示される可能性があります。 表示された場合は、**「許可」**をクリックします。 次に、「IBM Cloud ツールチェーンの許可 (Authorize IBM Cloud Toolchains)」ページで、**「IBM-Cloud を許可 (Authorize IBM-Cloud)」**をクリックし、GitHub パスワードを入力します。
5. 「統合の構成」ページで、リポジトリー・タイプに**「既存」**を選択し、DevOps ツールチェーンがリポジトリーに Webhook を構成し、リポジトリーのフォークまたはコピーを作成しないようにします。
6. リポジトリー URL を入力します (例えば、`https://github.com/yourrepo/spring-boot-hello-world`）。
7. しばらくすると、GitHub ReST API を使用するための許可を GitHub が DevOps ツールチェーンに付与するのを許可するよう求めるプロンプトが出される場合があります。この許可は、ツールチェーンをトリガーするのに必要な Web フックでリポジトリーを構成するために必要です。
8.  **「統合の作成 (Create Integration)」**をクリックします。

リポジトリー設定から、新しい Web フックを表示できます。

## Delivery Pipeline の追加
{: #pipeline-byoc-kube}

1. **「ツールの追加」**をクリックします。
2. **「Delivery Pipeline」**を選択します。
3. パイプラインの名前として`「Continuous Integration」`と入力し、**「統合の作成」**をクリックします。

## パイプライン・ステージの構成
{: #pipelineconfig-byoc-kube}

入力 (GitHub リポジトリーのコンテンツ) を正しい宛先に送信するためのパイプライン・ステージを構成します。 このチュートリアルでは、作業用 Docker イメージを生成する GitHub リポジトリーが存在し、ターゲットが IBM Containers Kubernetes クラスターであることを前提としているため、この目標を達成する入力、シェル・スクリプト、および出力を持つパイプライン・ステージを作成します。

1. `「ビルドおよび公開 (build and publish)」`パイプライン・ステージを構成します。
  1. 作成した Delivery Pipeline を選択して、**「ステージを追加」**をクリックします。
  2. **「入力」**タブをクリックし、以下のようにフィールドに入力します。
    * ステージ名として`「build and publish Docker image」`と入力します。
    * 入力タイプとして**「Git リポジトリー」**を選択します。
    * ご使用の GitHub リポジトリーを選択します。
    * 継続的統合に使用するブランチを選択します。
  3.  **「ジョブ」**タブをクリックし、**「ジョブの追加 '+'」**をクリックして、以下のようにフィールドに入力します。
    * ジョブ・タイプとして**「ビルド」**を選択します。
    * 名前として`「build and publish」`を選択します。
    * ビルダー・タイプとして**「コンテナー・レジストリー」**を選択します。
    * Kubernetes クラスターが配置されている地域を選択します。
    * **「既存の API キーを入力」**を選択します。 API キーがない場合は、『[API キーの作成](/docs/iam/userid_keys.html#creating-an-api-key)』を参照してください。 
    * コンテナー・レジストリー名前空間を入力します。これは、**「メニュー」**アイコン ![「メニュー」アイコン](../../icons/icon_hamburger.svg) をクリックし、**「コンテナー」** > **「レジストリー」** > **「名前空間」**をクリックして見つけることができます。
    * Docker イメージ名には、`「continuous」`と入力します (このパイプライン・ビルド・ステージは、リポジトリーの継続的統合ブランチの継続ビルド用だからです)。
    * 最初の `#!/bin/bash` 行の後に 1 行以上を追加してビルド・スクリプトを編集します。 例えば、Maven を使用してビルドされたリポジトリーの場合、以下の例のような数行を追加できます。

      ```bash
      export JAVA_HOME=/opt/IBM/java8
      # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
      export MAVEN_OPTS="-  
      Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
      mvn -B clean verify
      ```
      {: codeblock}
  4. **「保存」**をクリックします。 
2. ビルドが成功するまで**「再生」**アイコンをクリックして、`「build and publish」`パイプライン・ステージをテストします。 緑色のステージは、ビルドが正常に実行されたことを示しています。 
3. Docker イメージを Kubernetes クラスターにデプロイするように`「クラスターにデプロイ (deploy to cluster)」`パイプライン・ステージを構成します。 
  1. Delivery Pipeline のページで、**「ステージを追加」**をクリックします。
  2. **「入力」**タブをクリックし、以下のようにフィールドに入力します。
    * 名前として`「deploy to cluster」`と入力します。
    * 入力タイプとして**「ビルド成果物」**を選択します。
    * ステージに対して**「Docker イメージのビルドおよび公開 (Build & Publish Docker Image)」**を選択します。
    * ジョブに対して**「ビルドおよび公開 (Build & Publish)」**を選択します。
    * これは継続的統合パイプラインであるため、ステージ・トリガーのデフォルト・オプションを受け入れます。
  3. **「ジョブ」**タブをクリックし、**「ジョブの追加 '+'」**をクリックして、以下のようにフィールドに入力します。
    * 名前として`「deploy to continuous integration cluster」`と入力します。
    * デプロイヤー・タイプとして**「Kubernetes」**を選択します。
    * Kubernetes クラスターが配置されている地域を選択します。
    * 既存の API キーを入力します。 
  4. **「保存」**をクリックします。
4. ビルドが成功するまで**「再生」**アイコンをクリックして、`「クラスターにデプロイ (deploy to cluster)」`パイプライン・ステージをテストします。 緑色のステージは、ビルドが正常に実行されたことを示しています。

## アプリが実行中であることの確認
{: #verify-byoc-kube}

アプリのデプロイ後に、Delivery Pipeline またはコマンド・ラインにアプリの URLが示されます。

1. DevOps ツールチェーンから、**「Delivery Pipeline」**をクリックし、**「デプロイ・ステージ」**を選択します。
2. **「ログおよび履歴の表示」**をクリックします。
3. ログ・ファイルで、アプリケーション URL を見つけます。

    ログ・ファイルの末尾で `View the application health at: http://<ipaddress>:<port>/health` を探します。

4. ご使用のブラウザーでその URL にアクセスします。 アプリが実行されている場合は、`Congratulations` または `{"status":"UP"}` を含むメッセージが表示されます。

コマンド・ラインを使用している場合は、[`ibmcloud dev view`](/docs/cli/idt/commands.html#view) コマンドを実行して、アプリの URL を表示します。次に、ブラウザーでその URL にアクセスします。
