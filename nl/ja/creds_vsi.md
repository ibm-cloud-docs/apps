---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-14"

keywords: apps, credentials, virtual server instance, vsi, virtual machine, vm

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 仮想インスタンスまたはローカル Docker 環境への資格情報の追加
{: #add-credentials-vsi}

仮想サーバー・インスタンスまたはローカル Docker デプロイメント環境にサービス資格情報を追加する方法について説明します。
{: shortdesc}

## ユーザー作成コード + 仮想サーバー・インスタンスまたはローカル Docker
{: #credentials-byoc-vsi}

VSI またはローカル Docker の下では、環境は完全にユーザーのものです。 例えば、以下の例のようなコードを記述し、アプリケーションの実行時に資格情報の環境値をアプリケーションに提供できます。
```
password = getEnvironment('password');
```
{: codeblock}

Bash では、以下の例のようなコードを記述できます。
```bash
export password="someThingSensitive"
# run app locally.  If node, something like:
npm run start
```
{: codeblock}

Docker では、以下の例のようなコードを記述できます。
```
docker run -p 80:8080 -e password="someThingSensitive"
```
{: codeblock}

## スターター・キット + VSI (またはローカル Docker)
{: #credentials-starterkit-vsi}

### 仮想サーバー・インスタンスの準備方法

この環境は、完全にユーザーの制御下にあり、ノートブックからアプリケーションを実行しているかのように扱うことができます。 つまり、ローカル Docker です。 VSI は、実行中のアプリケーションの観点から見ると、実質的にベアメタルであるため、(Kubernetes などの場合の) _シークレット_ も (Cloud Foundry などの場合の) _サービス_ も存在しません。

### スターター・キットによって生成されるコード
{: #starterkit-generated-code-vsi}

スターター・キットから生成されるコードには、ネイティブの `IBMCloudEnv` ライブラリーがあります。このライブラリーは、アプリケーション・コードを移植可能にして複数のデプロイメント・ターゲットで実行できるように、環境値の取得を抽象化します。 仮想またはローカル Docker では、その環境に、`IBMCloudEnv` ライブラリーを満たす値が準備されなければなりませんが、それらの値は、_必ずしも_ 実際の環境変数から取得する必要はありません。

ユーザーにとって便利なように、スターター・キットによって生成される出力に含まれる `mappings.json` の命令には、アプリケーションが使用できる値を `IBMCloudEnv` ライブラリーが入手する元となるローカル・ファイルへの参照が含まれます。

例えば、`mappings.json` ファイルの以下のセクションにある最後の行に注目してください。
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

アプリの作成時に「継続的デリバリーの構成 (Configure continous delivery)」フィーチャーを使用すると、`/server/localdev-config.json` ファイルは GitLab リポジトリーから削除されます。セキュリティー上の理由から、資格情報はソース・コード・リポジトリー内に入れないでください。

作成された GitLab リポジトリーに対し `git clone` を使用してアクティブな開発を開始した場合、機密性の高い資格情報を含んだファイルが誤ってチェックインされないように、`.gitignore` ファイルが `server/localdev-config.json` を具体的に無視する点に注意してください。 ただし、ノートブックで作業する開発者と同じように、VSI はこのファイルを_必要とします_。

以下のステップを実行して、`server/localdev-config.json` ファイルを取得できます。

1. 「継続的デリバリーの構成 (Configure continous delivery)」フィーチャーを使用したときに自動的に作成された Git lab リポジトリーに対して `git clone` を使用します。
2. `dev` プラグインを含んでいる [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli) をインストールします。
3. `ibmcloud` コマンド・ラインを使用して、{{site.data.keyword.cloud_notm}} にログインします。
4. `ibmcloud dev get-credentials` を実行します。これで、`cli-config.yml` ファイルを参照します。 `cli-config.yml` ファイルには、資格情報を持つアプリケーションおよび生成ジョブに関する情報が含まれています。

「継続的デリバリーの構成 (Configure continous delivery)」フィーチャーを使用してから `ibmcloud dev get-credentials` を使用するまでの間に、いずれかのサービスが削除された場合、ダウンロードされたファイル `/server/localdev-config.json` には、オリジナルの `git clone` コードベースが必要とする資格情報がすべては含まれないことになります。
{: tip}

アプリケーションを Docker コンテナーで実行している場合は、`/server/localdev-config.json` ファイルを完全に削除し、Docker コマンド・ラインで環境変数を渡すことを選択できます。

`mappings.json` ファイルの「cloudant_apikey」セクションの続きで、`file...` 行の前の `env:cloudant_apikey` に注目してください。 これは、`cloudant_apikey` という名前の環境変数がファイルの内容よりも優先されることを意味します。 したがって、作成した Docker イメージ内にファイルが存在する場合でも (これは必須ではありません)、Docker コマンド・ラインで値を渡すことにより、値をオーバーライドできます。

例えば次のようにします。
```
docker run -p 80:8080 -e cloudant_apikey="someKeyValue"
```
{: codeblock}
