---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# {{site.data.keyword.containerlong_notm}} への Mendix アプリのデプロイ
{: #deploy-mendix-kube}

デフォルトでは、{{site.data.keyword.containerlong}} へのデプロイメントをターゲットとする Mendix アプリケーションは評価モードでセットアップされます。 このモードでは、アプリケーション作成を迅速に開始してクラウドにデプロイできますが、データ・パーシスタンスや拡張 Kubernetes 構成は構成されません。 このチュートリアルでは、{{site.data.keyword.cos_full_notm}} サービスを使用して Kubernetes で永続ストレージ・ボリュームをセットアップすることによって実稼働環境を構成する手順について説明します。
{: shortdesc}

## 始める前に
{: #prereqs-mendix-kube}

- Mendix アプリを作成します。 詳しくは、『[Mendix アプリの作成](/docs/apps/tutorials/tutorial_mendix_getting_started.html#create-mendix)』を参照してください。
- [{{site.data.keyword.dev_cli_notm}} コマンド・ライン・インターフェース (CLI)](/docs/cli/index.html) をインストールします。これには {{site.data.keyword.containershort_notm}} CLI が含まれています。
- `ibmcloud` CLI にログインし、[Kubernetes クラスターへのアクセス](/docs/containers/cs_tutorials.html#cs_cluster_tutorial_lesson3)のために `kubectl` を構成します。

## Cloud Object Storage サービス・インスタンスの作成
{: #cos-mendix-kube}

アプリケーションの詳細ページから開始し、以下の手順を使用します。
1. **「リソースの追加」**をクリックします。
2. **「ストレージ」**を選択し、**「次へ」**をクリックします。
3. 次に、**「クラウド・オブジェクト・ストレージ」**オプションを選択し、**「次へ」**をクリックします。
4. {{site.data.keyword.cos_full_notm}} インスタンスの価格プランが提示されます。 自分のニーズに最も適した価格プランを選択し、Mendix アプリケーションで使用するための {{site.data.keyword.cos_full_notm}} サービスのインスタンスを作成するために**「作成」**をクリックします。

  {{site.data.keyword.cos_full_notm}} サービスの既存インスタンスを使用する場合は、**「リソースの追加」**をクリックし、アプリケーションで使用するための既存インスタンスを選択します。
  {: tip}

## ストレージ・バケットの作成
{: #storage-bucket-mendix-kube}

{{site.data.keyword.cos_full_notm}} サービスのインスタンスが Mendix アプリケーションと関連付けられたら、データを保存できるストレージ・バケットを作成する必要があります。 バケットを作成するには、{{site.data.keyword.cos_full_notm}} インスタンスの**「...」**をクリックし、**「ダッシュボードを開く」**を選択します。  

新しいウィンドウの**「バケット (Buckets)」**タブで {{site.data.keyword.cos_full_notm}} サービス・ダッシュボードが開きます。 **「バケットの作成 (Create Bucket)」**をクリックし、バケット作成手順に従います。その際、固有の名前を使用してください。 このチュートリアルの目的のため、`my-mendix-bucket` という名前のバケットを作成してください。

## 永続ストレージの構成
{: #kube-storage-mendix}

次に、『[Storing data on {{site.data.keyword.cos_full_notm}}](/docs/containers/cs_storage_cos.html#object_storage)』の文書に従ってください。 `PersistentVolumeClaim` および `PersistentVolume` が Kubernetes クラスター内に作成され、Mendix アプリケーションの一部としてクラスター内で稼働している PostGres データベース・インスタンスによって使用できるようになります。 前のステップで説明されているように `my-mendix-bucket` バケットを使用して `PersistentVolumeClaim` を作成し、次のステップでの使用のために `PersistentVolumeClaim` 名を確認してください。

## `postgres-deployment.yaml` ファイルの編集
{: #postgres-deploy-mendix}

Kubernetes クラスター用の永続ボリュームの構成が終わったら、次のステップは、クラスター内で実行中の PostGres データベース・デプロイメントを変更することです。 まず、IBM DevOps ツールチェーン統合ステップの一環として作成された、Git リポジトリー内のファイルを編集します。 Git リポジトリーを見つけるには、アプリケーションの詳細ページに戻り、**「デプロイメントの詳細」**タイルから Git url リンクをクリックします。  

Git リポジトリーをローカル・マシンに複製するか、または、オンライン・エディターで以下の変更を行うことができます。 `chart/{app name}/templates/postgres-deployment.yaml` ファイルを開きます (`{app name}` を Mendix アプリの名前に置き換えてください)。 このファイルには `volumeMount` および `volumes` 項目はデフォルトでは存在しないため、すべてのデータが、実行中のデプロイメント・ポッド内でメモリー内に保管されます。 データが {{site.data.keyword.cos_full_notm}} バケットに保存され、ポッドが再始動してもデータが失われないようにするため、`volumeMount` と `volumes` の両方の項目を Kubernetes `deployment.yaml` ファイルに追加する必要があります。 

以下の `postgres-deployment.yaml` 例を参照してください。これには、`volumeMount` および `volumes` 項目が含まれています。  
```yaml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: "{appname}-postgres"
spec:
  replicas: 1
  template:
    metadata:
      labels:
        service: "{appname}-postgres"
    spec:
      containers:
        - name: "{appname}-postgres"
          image: postgres:10.1
          ports:
            - containerPort: 5432
          env:
            - name: POSTGRES_DB
              value: db0
            - name: POSTGRES_USER
              value: mendix
            - name: POSTGRES_PASSWORD
              value: mendix
          volumeMounts:
            - mountPath: "/var/lib/postgresql/data"
              name: "mendix-data"
      volumes:
        - name: mendix-data
          persistentVolumeClaim:
            claimName: {pvc-name}
```

`{pvc-name}` を、前のステップからの `PersistentVolumeClaim` の名前に置き換えてください。また、Git リポジトリー内のファイルに既に設定されているアプリの名前を上書きしないように注意してください。 次に、変更を Git リポジトリーにコミットして戻します。

## 再デプロイ
{: #redeploy-mendix-kube}

`postgres-deployment.yaml` ファイルの変更がリポジトリーにコミットして戻されたら、DevOps パイプラインの新しい実行が自動的にトリガーされます。 ただし、それによってデフォルト・アプリケーションが再デプロイされます。 最新の永続ボリューム変更と共に最新バージョンのアプリケーションがデプロイされるようにするには、最新バージョンの Mendix アプリケーションを再デプロイする必要があります。

再デプロイするには、アプリケーションの詳細ページに移動し、**「デプロイメントの詳細」**タイルで**「アプリケーションのデプロイ」**をクリックします。 DevOps ツールチェーン内部でデプロイメントが失敗し、アプリケーションの `.mda` ファイルが見つからないというエラーが示される場合は、それを Mendix から再度エクスポートする必要があります。 エクスポートするには、Mendix Modeler デスクトップ・アプリケーションからエクスポートするか、または、**「Mendix での編集 (Edit on Mendix)」**をクリックします。 その後、Mendix Web インターフェース内で、**「環境」**セクションに移動し、**「teamserver からパッケージを作成 (Create package from teamserver)」**をクリックした後、示される手順に従います。 アプリケーションが Mendix からエクスポートされたら、アプリケーションの詳細ページに戻り、再び**「アプリケーションのデプロイ」**をクリックします。 最後にエクスポートされたアプリケーションが、{{site.data.keyword.cloud}} DevOps ツールチェーンを使用して Kubernetes クラスターにデプロイされます。 デプロイメントが正常に完了すると、アプリケーションは稼働中になり、実動で使用できるようになります。

## アプリが実行中であることの確認
{: #verify-mendix-kube}

アプリのデプロイ後に、Delivery Pipeline またはコマンド・ラインにアプリの URLが示されます。

1. DevOps ツールチェーンから、**「Delivery Pipeline」**をクリックし、**「デプロイ・ステージ」**を選択します。
2. **「ログおよび履歴の表示」**をクリックします。
3. ログ・ファイルで、アプリケーション URL を見つけます。

    ログ・ファイルの末尾で `urls` または `view` という語を探します。 例えば、`urls: my-app-devhost.cloud.ibm.com` または `View the application health at: http://<ipaddress>:<port>/health` のような行がログ・ファイル内で見つかります。

4. ご使用のブラウザーでその URL にアクセスします。 アプリが実行されている場合は、`Congratulations` または `{"status":"UP"}` を含むメッセージが表示されます。

コマンド・ラインを使用している場合は、[`ibmcloud dev view`](/docs/cli/idt/commands.html#view) コマンドを実行して、アプリの URL を表示します。 次に、ブラウザーでその URL にアクセスします。

## 追加情報
{: #more-info-mendix-kube}

Kubernetes 環境での Mendix アプリケーションの実行に関するアーキテクチャーの詳細については、Mendix ユーザー資料の [Run Mendix on Kubernetes](https://docs.mendix.com/developerportal/deploy/run-mendix-on-kubernetes) セクションを参照してください。
