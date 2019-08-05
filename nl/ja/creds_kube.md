---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-22"

keywords: apps, credentials, kubernetes, kube, add, custom, deployment.yml, cluster, deployment, environment, kubectl, secret

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# Kubernetes 環境へのサービス資格情報の追加
{: #add-credentials-kube}

Kubernetes デプロイメント環境にサービス資格情報を追加する方法について説明します。
{: shortdesc}

以下のシナリオでは、デプロイメント環境にサービス資格情報を手動で追加する必要があります。
 * 独自のコードを持ち込む (Bring Your Own Code)。
 * ブランクのスターター・キット・テンプレートから開始する。
 * デプロイされた_後_ のスターター・キット・ベースのアプリにサービスを追加する。

## ユーザー作成コード + Kubernetes
{: #credentials-byoc-kube}

<!-- (Refer to the ["Code it Right"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#code-it-right) and ["Prepare the Environment"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#prepare-the-environment) sections.  But translate a bit so we're only mentioning editing a `deployment.yml` file, not the "deployment.yml section of the script in the Deploy pipeline stage configuration".) -->

### 正しいコーディング

予防措置として、アプリケーションのメイン・エントリー・ポイントにおいて、アプリケーションの環境が完全であることを確認するようにアプリケーションをコーディングできます。 環境が完全でないために製品に中断をもたらすようなアプリケーションをクラスターにプロモートすることは避けなければなりません。 アプリケーションが開始を拒否することで、Kubernetes 構成がそのような中断を自動的に防止できます。

以下の 2 つの環境変数があるとします。
* `SECRET`
* `NOT_SECRET`

データベース用には、`APIKEY` と `DB_URL` という変数があるとします。前者は機密情報ですが、後者は違います。

Java では、メイン・アプリケーション・エントリー・ポイントに以下のようなコードを記述できます。
```java
if (System.getenv("SECRET") == null) {
    throw new RuntimeException("Environment variable 'SECRET' is not set!");
}
// and many more checks...
```
{: codeblock}

Node の場合、以下の同様の例を参照してください。
```js
if (!process.env.SECRET) {
    console.error('ENVIRONMENT variable "SECRET" is not set!');
    process.exit(1);
}
// and many more checks...
```
{: codeblock}

### 環境の準備

Kubernetes `deployment.yml` ファイル内に、環境変数または_クラスター内のシークレットへの参照_ を定義できます。

#### 環境から資格情報を取得するためのデプロイメントの設定

`kind: Deployment` があるセクション内で、`spec.template.spec.containers` の後に、以下のサンプル・コードをインデント・レベルで追加します。
```yaml
env:
  - name: SECRET
    valueFrom:
      secretKeyRef:
          name: name-secret
          key: KEY_SECRET
  - name: NOT_SECRET
    value: "I'm not a secret"
```
{: codeblock}

* **「保存」**をクリックします。

名前 `name-secret` とキー _KEY_SECRET_ を持つ `secretKeyRef` が値に解決されるようにクラスターを構成します。

#### 前提条件ツールのインストール

ワークステーションの端末を使用して、以下のツールをインストールします。

1. [{{site.data.keyword.dev_cli_long}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli) をインストールします。
2. `ibmcloud login` コマンドを使用してログインします。
3. `ibmcloud cs cluster-config {your_cluster_name}` を実行してクラスターに接続します。
4. `export` コマンドをコピー・アンド・ペーストして、端末からコマンドを実行します。

#### クラスター内のシークレットの定義

ユーザーは Kubernetes クラスターに接続されているので、{{site.data.keyword.dev_cli_notm}} が提供する `kubectl` を実行できます。

解決可能なシークレットを定義するには、以下の `kubectl` コマンドを使用します。
```console
echo -n 'This is the secret.  Shhhhh!' > ./KEY_SECRET
```
{: codeblock}

```console
kubectl create secret generic name-secret --from-file=./KEY_SECRET
```
{: codeblock}

これで、解決可能なシークレットが Kubernetes クラスターに準備されたので、`deployment.yml` ファイルに定義されている環境変数を使用するようにアプリケーションを更新できます。

## スターター・キット・アプリと Kubernetes
{: #credentials-starterkit-kube}

1. **「アプリの詳細」**ページに移動します。

2. Cloud Object Storage のインスタンスを作成するために、**「サービスの追加」**>**「ストレージ」**>**「Cloud Object Storage」**>**「ライト・プラン (無料)」**>**「作成」**を選択します。

3. **「コードのダウンロード」**をクリックして、注入されたコード・スニペットでアプリを再生成します。

4. 資格情報にローカルでアクセスするために、新しく生成された `.zip` ファイルにある以下のファイルをローカル Git クローンにコピーおよび置換して、資格情報にアクセスします。 この場合も、資格情報をホストするために、クラスター内に Kubernetes シークレットを作成する必要があります。

   - `chart/{appName}/bindings.yaml` - シークレットを指す環境変数を Kubernetes クラスター内に生成します。
   - `src/main/resources/localdev-config.json` - アプリをローカルで実行するときに資格情報にアクセスします。
   - `src/main/resources/mappings.json` - コードから環境変数にアクセスするための [`env.getProperty()`](/docs/java-spring?topic=java-spring-configuration#accessing-credentials) メソッドへのアクセスを可能にするマッピング。
   - `manifest.yml` - このファイルによってサービスが Cloud Foundry アプリケーションにバインドされます。

  後で、リソース・コントローラー・リソース (組織またはスペースでなくリソース・グループ内にあるリソース) を含んだ Cloud Foundry アプリケーションにデプロイする場合は、もう 1 つファイルをコピーする必要があります。
  {: note}

5. [対応する地域 (無料の場合は米国南部) で Kubernetes クラスター](https://{DomainName}/kubernetes/clusters){: new_window}
![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") を表示します。

6. クラスターをクリックし、右上にある**「Kubernetes ダッシュボード」**を選択してクラスター・ダッシュボードを表示します。

7. **「シークレット (Secrets)」**というラベルのセクションが表示されるまでスクロールダウンします。 {{site.data.keyword.cloudant_short_notm}} サービス・インスタンスのシークレットが表示されます。これには、`binding-{appName}-{serviceName}-{timestamp}` という規則が使用されています。 `chart/{appName}/bindings.yaml` ファイル内に、対応する {{site.data.keyword.cloudant_short_notm}} シークレットがあります。

8. これで、`chart/{appName}/bindings.yaml` に既に生成されているシークレット名を使用して、Cloud Object Storage インスタンス用の対応するシークレットを作成できます。このシークレットは、`binding-create-app-ktibr-cloudobjectstor-1538170732311` などのようになります。

9. ダッシュボードの**「アプリの詳細」**ページに移動し、Cloud Object Storage インスタンスの資格情報をコピーします。 以下の資格情報の出力例を参照してください。
  ```yaml
  {
    "apikey": "hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg",
    "endpoints": "https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints",
    "resource_instance_id": "crn:v1:staging:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"
  }    
  ```
  {: codeblock}

10. `ibmcloud cs cluster-config {your_cluster_name}` を使用し、その後の命令内のコマンドをエクスポートして、クラスターが構成されていることを確認します。

11. `echo` コマンドを使用して、資格情報を `binding` ファイルに入れます。
  ```console
  echo -n '{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints","resource_instance_id":"crn:v1:staging:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}' > ./binding

  ```
  {: codeblock}

12. `kubectl create secret generic binding-create-app-ktibr-cloudobjectstor-15381707323113 --from-file=./binding` を使用してシークレットを作成します。 Kubernetes クラスター・ダッシュボードに戻ると、作成したシークレットを確認できます。

  デプロイ先が Cloud Foundry アプリケーションの場合に、リソース・コントローラーのインスタンスを使用するには (リソースが、組織またはスペースでなくリソース・グループ内に存在する場合)、ユーザー提供のサービスを作成する必要があります。 
  {: note}
  
  ```console
  ibmcloud cf create-user-provided-service create-app-ktibr-cloudobjectstor-1538170732311 -p `{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints","resource_instance_id":"ccrn:v1:staging:public:cloud-object-storage:global::a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}`
  ```
  {: codeblock}

  ユーザー提供のサービスの名前は、`manifest.yml` ファイル内の対応するインスタンス名で見つけることができます。

13. これで、アプリケーションを Kubernetes クラスター内で実行しているときに、`env.getProperty` メソッドを使用し、環境変数を介してシークレットにアクセスできます。

### Kubernetes クラスターの準備方法

**「継続的デリバリーの構成 (Configure continuous delivery)」**フィーチャーを使用して、アプリを IBM Kubernetes クラスターにデプロイします。 このフィーチャーによって、アプリに関連付けられたリソースの資格情報用のシークレットが Kubernetes クラスターに準備されます。 以下のステップを実行して、クラスター準備の結果を確認できます。

1. 結果を表示するには、以下のコマンドを実行します。

  ```
  kubectl get secrets
  ```
  {: codeblock}

  [シークレットに関する詳細な資料](https://kubernetes.io/docs/concepts/configuration/secret/)を表示できます。
  {: tip}

2. シークレットの名前がリソース名であることを確認します。
3. `kubectl get secret binding-blarg-cloudant-1538408663553 -o=yaml` を使用して、シークレットに関する詳細情報を表示します。

  ```
  apiVersion: v1
  data:
    binding: eyJhcGlrZXkiOiI4RFprT3VMVnduVkExWW1HODFnazNQMjZOeThlNWFWbjVhaFpZLVVEOHQ1NCIsImhvc3QiOiI1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJpYW1fYXBpa2V5X2Rlc2NyaXB0aW9uIjoiQXV0byBnZW5lcmF0ZWQgYXBpa2V5IGR1cmluZyByZXNvdXJjZS1rZXkgb3BlcmF0aW9uIGZvciBJbnN0YW5jZSAtIGNybjp2MTpibHVlbWl4OnB1YmxpYzpjbG91ZGFudG5vc3FsZGI6dXMtc291dGg6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzpiZmEzNDJkZC00YjZmLTRkZmUtYTM1YS05MTA4ZmIwZWM1NzE6OiIsImlhbV9hcGlrZXlfbmFtZSI6ImF1dG8tZ2VuZXJhdGVkLWFwaWtleS01MzI3ZWMxZC0wOWE1LTQyMzctOTczNS03ZTAxZmU3NDFiYzciLCJpYW1fcm9sZV9jcm4iOiJjcm46djE6Ymx1ZW1peDpwdWJsaWM6aWFtOjo6OnNlcnZpY2VSb2xlOldyaXRlciIsImlhbV9zZXJ2aWNlaWRfY3JuIjoiY3JuOnYxOmJsdWVtaXg6cHVibGljOmlhbS1pZGVudGl0eTo6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzo6c2VydmljZWlkOlNlcnZpY2VJZC1mNWRhMjMwYy1kNDE0LTQ4NTQtYjE1Yi00MmJmZmRhYWVmNWIiLCJwYXNzd29yZCI6ImY4MjU2ZDJhODYyMjI5NzViZDI3Mjc1MjEzMTY4YTQyNzBhNDZmMmEyOGQ5NDkyMjRhYzFjOTc3NjMwMWNlZTYiLCJwb3J0Ijo0NDMsInVybCI6Imh0dHBzOi8vNTlhYTdiMWEtNWFhYi00ZjJkLTlhNzMtOGMzYjI5NDA4Zjk2LWJsdWVtaXg6ZjgyNTZkMmE4NjIyMjk3NWJkMjcyNzUyMTMxNjhhNDI3MGE0NmYyYTI4ZDk0OTIyNGFjMWM5Nzc2MzAxY2VlNkA1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJ1c2VybmFtZSI6IjU5YWE3YjFhLTVhYWItNGYyZC05YTczLThjM2IyOTQwOGY5Ni1ibHVlbWl4In0=
  kind: Secret
  metadata:
    annotations:
      service-instance-id: 'crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::'
      service-key-id: 5327ec1d-09a5-4237-9735-7e01fe741bc7
    creationTimestamp: 2018-10-01T15:45:02Z
    name: binding-blarg-cloudant-1538408663553
    namespace: default
    resourceVersion: "155591"
    selfLink: /api/v1/namespaces/default/secrets/binding-blarg-cloudant-1538408663553
    uid: f5e7885c-c590-11e8-ad83-8e37f3f3216f
  type: Opaque
  ```
  {: screen}

  `binding` は、base64 でエンコードされたシークレットの値です。 これをデコードすると、値はサービス・インスタンスの `credentials` から取得した未加工 JSON と、いくつかの `iam_...` 値であることが分かります。
  ```
  {
    "apikey": "8DZkOuLVwnVA1YmG81gk3P26Ny8e5aVn5ahZY-UD8t54",
    "host": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "iam_apikey_description": "Auto generated apikey during resource-key operation for Instance - crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::",
    "iam_apikey_name": "auto-generated-apikey-5327ec1d-09a5-4237-9735-7e01fe741bc7",
    "iam_role_crn": "crn:v1:bluemix:public:iam::::serviceRole:Writer",
    "iam_serviceid_crn": "crn:v1:bluemix:public:iam-identity::a/480fd1ec14ac540c5bc37da799a63437::serviceid:ServiceId-f5da230c-d414-4854-b15b-42bffdaaef5b",
    "password": "f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6",
    "port": 443,
    "url": "https://59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix:f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6@59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "username": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix"
  }
  ```
  {: screen}

`deployment.yml` に、シークレットを参照する `env` 値が宣言されている場合を除いて、アプリケーション・コードで Kubernetes シークレットは取得できません。 スターター・キットを使用すると、そのようなコードが自動的に生成されます。

### スターター・キットによって生成されるコード
{: #credentials-starterkit-kube-gencode}

この Case では、アプリケーションの作成元はスターター・キットです。 スターター・キットで生成されたコードは、ローカル、Cloud Foundry、または Kubernetes で実行できるように移植可能になります。 アプリケーション・コードとサービス・インスタンスの資格情報を保持する環境変数の取得との間の抽象化層を提供するために、ライブラリー `IBMCloudEnv` が使用されます。

スターター・キットから作成されるコードには、`IBMCloudEnv` ライブラリーに対する依存関係があり、コードによって以下の出力が生成されます。

* `bindings.yml` ファイル。`deployment.yml` ファイル内にインラインで組み込まれており、以下の内容が含まれています。
  ```yaml
   - name: service_cloudant
     valueFrom:
     secretKeyRef:
        name: binding-blarg-cloudant-1538408663553
        key: binding
        optional: true
  ```
  {: codeblock}

  `secretKeyRef.name` は、アプリケーションがアプリケーション・コード内で単純な環境変数としてシークレットを取得できるように、定義された Kubernetes シークレットを公開します。

* `IBMCloudEnv` ライブラリーの命令は、`mappings.json` ファイル内にカプセル化されています。このファイルはスターター・キットによって生成されるコード・ベースの一部です。 `mappings.json` には、各資格情報の個別の定義があります。
  ```json
  "cloudant_apikey": {
    "searchPatterns": [
      "user-provided:blarg-cloudant-1538408663553:apikey",
      "cloudfoundry:$['cloudant'][0].credentials.apikey",
      "env:service_cloudant:$.apikey",
      "env:cloudant_apikey",
      "file:/server/localdev-config.json:$.cloudant_apikey"
    ]
  },
  ```
  {: codeblock}

  `mappings.json` ファイルは、`jsonpath` 構文と `searchPatterns` 配列の順序を使用して、`IBMCloudEnv` ロジックをガイドします。

* 以下のコードを使用して、Cloudant API キーを取得します (疑似コード)。
  ```java
  cloudantApiKey = IBMCloudEnv.getValue('cloudant_apikey');
  ```
  {: codeblock}

`IBMCloudEnv` ライブラリーは、アプリケーションが Kubernetes、Cloud Foundry、または仮想サーバー・インスタンス (ローカル Docker と同様に扱われます) のいずれで実行されているかを自動的に検出し、正しい `searchPattern` を適用して、返す値を見つけます。

したがって、`mappings.json` ファイルは、アプリが実行される環境から取得された、事前構成済みですぐに使用可能な値の_確定的なリスト_ と見なされます。 値は、**「継続的デリバリーの構成 (Configure continuous delivery)」**フィーチャーを使用したときにターゲットにしたクラスターの環境で取り込まれます。
