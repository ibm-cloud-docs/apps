---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-08"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# CLI を使用したアプリの作成およびデプロイ
{: #create-deploy-app-cli}

{{site.data.keyword.cloud}} コマンド・ライン・インターフェース (CLI) を使用して、アプリを作成し、デプロイすることができます。 

スターター・アプリを最初から作成することも、既存のアプリ・コードをクラウド対応にすることもできます。 
{: note}

## 始める前に
{: #prereqs-app-cli}

{{site.data.keyword.cloud_notm}} CLI、{{site.data.keyword.dev_cli_notm}} CLI プラグイン、およびその他の推奨プラグインとツールをインストールする必要があります。 詳しくは、[IBM Cloud CLI の概要](/docs/cli/index.html)を参照してください。 

## スターター・アプリを最初から作成する
{: #create-app-cli}

そもそも既存のコードが存在せず、言語またはフレームワーク・スターター・テンプレートから開始することを望む場合には、アプリを最初から作成する方法が適しています。

1. 任意のディレクトリーで [`ibmcloud dev create`](/docs/cli/idt/commands.html#create) コマンドを実行します。
2. アプリケーション・タイプとして **「バックエンド・サービス/Web アプリ」** を選択します。
3. 言語タイプとして**「Node」**を選択します。
4. 使用するスターター・キットとして**「Node.js Web App with Express.js (Web アプリ)」**を選択します。
5. アプリの名前を入力し、使用するリソース・グループを選択します (必要な場合)。 今はサービスを追加しないでください。
6. **「IBM DevOps、Cloud Foundry を使用 (IBM DevOps, using Cloud Foundry)」** オプションを選択して、DevOps ツールチェーンを作成します。 このステップを実行するには、SSH 鍵をセットアップする必要が生じる場合もあります。
  SSH 鍵のパスフレーズを設定した場合、このコードを入力する必要があります。
  {: note}
7. 固有のホスト名 (例えば、`abc-devhost`) を入力します。このホスト名は、アプリの経路 `abc-devhost.cloud.ibm.com` です。

アプリとツールチェーンを作成するのに数秒かかります。

## デプロイメントおよびクラウド対応アセットの生成
{: #byoc-cli}

既存のコードベースが既にあり、[`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable) を使用して単一のマイクロサービス用または Web アプリ用のデプロイメントおよびクラウド対応アセットを生成する場合、このオプションを使用できます。 このコマンドはベータ版であり、すべての言語またはアプリケーション構造、あるいはその両方がサポートされているわけではないことに注意してください。 以下の説明は、この機能をサンプル・リポジトリーで使用する方法を示していますが、ユーザー独自のコードベースの場合もステップはほぼ同じです。

1. ibmcloud login を実行して {{site.data.keyword.cloud_notm}} にログインし、組織とスペースをターゲットにします。
2. 任意のディレクトリーで以下のコマンドを実行して、[Hello World サンプル・アプリ](https://github.com/IBM-Cloud/node-helloworld)を複製します。

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

3. サンプル・アプリを複製したディレクトリーに移動し、[`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable) コマンドを実行します。
4. 現時点では変更をコミットせずに続行することを選択します (必要な場合)。
5. 検出されたノード言語を続行するようプロンプトが出されたときに続行する場合に選択します。
6. 使用するリソース・グループを選択します (必要な場合)。 
7. この Git リポジトリーにリンクされる新規 {{site.data.keyword.cloud_notm}} アプリを作成するオプションを選択します。 詳しくは、**重要事項**を参照してください。
8. 今はサービスを追加しないでください。
9. 操作が完了するまで数秒待ちます。 
10. 完了したら、アプリ・ディレクトリーに保存されたデプロイメント・ファイルおよびクラウド対応ファイルを手動でマージできます。 `.merge` とマークされた新規ファイルを `git diff` または類似ツールを使用してマージしてください。

### 重要事項
 - {{site.data.keyword.cloud_notm}} コンソールを使用して既に {{site.data.keyword.cloud_notm}} アプリを作成済みであった場合は、アプリ・ディレクトリー内で、前のセクションのステップ 2 から 5 を続行します。 ステップ 6 については、ローカル・コードを既存のアプリに接続するオプションを選択できます。
 - [`ibmcloud dev enable --no-create`](/docs/cli/idt/commands.html#enable) を実行することにより、{{site.data.keyword.cloud_notm}} アプリに接続せずに、デプロイメント・ファイルおよびクラウド対応ファイルの生成を選択することもできます。
 - ツールチェーンおよびデプロイメント・ファイルを手動で構成するには、[チュートリアル](/docs/apps/tutorials/tutorial_byoc_kube.html#tutorial-byoc-kube)に従ってください。 これは、相互に関連する複数の Web アプリまたはマイクロサービスに対する Continuous Delivery ツールチェーンを構成しようとする場合に役立ちます。
 - 既存のコードベースがまだ Git リポジトリー内にない場合は、アプリ・ディレクトリー内で、前のセクションのステップ 2 から 5 を続行します。 ステップ 6 については、新規 {{site.data.keyword.cloud_notm}} アプリを作成し、それを (新しく作成された GitLab リポジトリーを持つ) DevOps ツールチェーンにデプロイするオプションを選択できます。

## アプリのビルドとローカルでの実行
{: #build-run-app-cli}

アプリの作成に使用したオプションに関係なく、この時点で、アプリをビルドしてローカルで実行できます。

1. アプリケーション・ディレクトリーに移動し、Docker がシステムで実行されていることを確認します。
2. [`ibmcloud dev build`](/docs/cli/idt/commands.html#build) コマンドを実行してアプリをビルドします。
3. [`ibmcloud dev run`](/docs/cli/idt/commands.html#run) コマンドを実行して、アプリのローカルでの実行を開始します。
4. `http://localhost:3000` または類似の URL で、ローカルに実行されているアプリを表示します。
5. **Ctrl + C** キーを押してアプリを停止します。

`ibmcloud dev build/run` のような[複合コマンド](/docs/cli/idt/commands.html#compound)を使用して、ビルドの後に実行という順序で実行することもできます。
{: tip}

## サービスの追加およびコードの変更
{: #resources-app-cli}

アプリをローカルで実行できるようになったので、サービスを追加して一部のコードを変更できます。 

1. [`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit) コマンドを実行します。
2. プロンプトに従って、新しいデータ関連サービスを作成し、{{site.data.keyword.cloudant_short_notm}} などのアプリに接続します。 サービスの地域とプランを選択する必要がある場合があります。
3. サービスの作成時に、アプリ・ディレクトリーに保存された構成ファイルを手動でマージすることを選択できます。 または、今は、このステップをスキップすることができます。
4. コードを更新します。 例えば、`/public/index.html` ファイルまたは同様のファイルを変更します。 サンプルの `ExpressJS` アプリケーションを使用している場合、`Congratulations!` ストリングを、`Hello World!` のようなものに変更できます。
5. 変更したファイルを保存します。

## {{site.data.keyword.cloud_notm}} へのデプロイ
{: #deploy-app-cli}

アプリの構成方法に応じて、{{site.data.keyword.cloud_notm}} アプリを 2 つの方法のいずれかでデプロイできます。 

### DevOps ツールチェーンを使用したアプリのデプロイ
アプリ用の DevOps ツールチェーンをまだ作成しておらず、アプリがまだ Git リポジトリー内にない場合、[`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit) コマンドを実行できます。 「DevOps の構成」のプロンプトに従い、新しいツールチェーンにデプロイします (また、新規 GitLab リポジトリーも作成します)。

アプリ用の DevOps ツールチェーンが作成されると、新規ビルドのデプロイは、ツールチェーン内のリポジトリーにコードをコミットしてプッシュするだけの単純なものになります。 

1. `git add .` コマンドを実行します。
2. `git commit-m"made changes"` コマンドを実行して変更をコミットします。
3. `git push origin master` コマンドを実行して、マスター・ブランチにプッシュします。
4. {{site.data.keyword.cloud_notm}} コンソールからアプリの DevOps ツールチェーンを表示します。 アプリ・ディレクトリーから [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) コマンドを実行することで、{{site.data.keyword.cloud_notm}} コンソールの「アプリの詳細」画面からツールチェーンの詳細を表示できます。
5. ツールチェーン内のパイプラインを表示して、新規ビルドが開始されたことを確認します。

### 手動によるアプリのデプロイ

[`deploy`](/docs/cli/idt/commands.html#deploy) コマンドを使用して、アプリを手動でデプロイできます。 例えば、アプリを Kubernetes に手動でデプロイするには、以下の手順を実行します。

1. [Kubernetes クラスターを作成](https://{DomainName}/containers-kubernetes/overview)したことを確認します。
2. [`ibmcloud dev deploy-t container`](/docs/cli/idt/commands.html#deploy) コマンドを実行します。
3. プロンプトが出されたら、使用するクラスターおよびコンテナーのイメージ名を確認します。
4. デプロイメントが終了するまで数分待ちます。

## アプリの表示
{: #view-app-cli}

1. {{site.data.keyword.cloud_notm}}で実行されているアプリの URL を表示するには、[`ibmcloud dev view`](/docs/cli/idt/commands.html#view) コマンドを実行します。
2. {{site.data.keyword.cloud_notm}} コンソールからアプリの資格情報、サービス、およびツールチェーンに関する詳細を表示するには、[`ibmcloud dev console`](/docs/cli/idt/commands.html#console) コマンドを実行します。 

**問題を報告したり、フィードバックを提供したりするには、[{{site.data.keyword.cloud_notm}} Tech の Slack - #developer-tools チャネル](https://ibm-cloud-tech.slack.com)を使用できます ([ここ](https://slack-invite-ibm-cloud-tech.mybluemix.net/)でチーム・アクセスを依頼できます)。**
