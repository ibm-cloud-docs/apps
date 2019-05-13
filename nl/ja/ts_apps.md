---

copyright:
  years: 2015, 2019
lastupdated: "2019-05-08"

keywords: apps, application, troubleshooting, debug apps, known issues, debug, help, configuration, app, troubleshoot, error, errors, failure, failed, fail, issues, applications

subcollection: creating-apps

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# アプリの作成に関するトラブルシューティング
{: #managingapps}

アプリの作成に関する一般的な問題には、アプリを更新できない、2 バイト文字が表示されないなどがあります。 多くの場合、いくつかの簡単なステップを実行することで、これらの問題から復旧することが可能です。
{:shortdesc}

## マイ・アプリがさまざまなドメインでホストされている
{: #domains-ts}
{: troubleshoot}

`mybluemix.net` ドメインでホストされているマイ・アプリと、`appdomain.cloud` ドメインでホストされているマイ・アプリがあります。

既存のマイ・アプリは `mybluemix.net` ドメインでホストされていますが、新しいマイ・アプリは `appdomain.cloud` ドメインでホストされています。
{: tsSymptoms}

新しいホスト名オプション `*.appdomain.cloud` を cloud.ibm.com で使用することができます。

以前は、{{site.data.keyword.containerlong_notm}} や Cloud Foundry など、さまざまなデプロイメント・ターゲットでアプリをホストするために `mybluemix.net` ドメインが使用されていました。`mybluemix.net` でホストされているアプリは影響を受けません。

Cloud Foundry アプリのサブドメインは `cf.appdomain.cloud` です。{{site.data.keyword.containerlong_notm}} にデプロイするアプリのサブドメインは `containers.appdomain.cloud` です。

詳しくは、[ドメインの管理](/docs/apps?topic=creating-apps-update-domain)を参照してください。

## 保存されていない変更があります
{: #ts_unsaved_changes}
{: troubleshoot}

アプリの詳細ページで項目をクリックしたときに、アクションを実行できない場合があります。続行する前に、変更を保存するように求めるプロンプトが出される場合もあります。

アプリの詳細ページでアプリまたはサービスを確認しようとすると、次のエラー・メッセージが表示されます。
{: tsSymptoms}

`保存されていない変更があります。 このページを終了してよろしいですか?`

マウスをスクロールして、「ランタイム」ペインの**「インスタンス」**フィールドまたは**「メモリー割り当て量」**フィールドの上に移動すると、それらの値が変わります。 この動作は、設計によるものです。 ただし、別のページに移動する前にメモリー設定またはインスタンス設定を保存するよう求めるプロンプトが表示されます。
{: tsCauses}

メッセージ・ウィンドウを閉じ、ランタイム・ペインの**「リセット」**をクリックします。
{: tsResolve}

## {{site.data.keyword.cloud_notm}} 領域間の自動フェイルオーバーを使用できない
{: #ts_failover}
{: troubleshoot}

{{site.data.keyword.cloud}} 領域間の自動フェイルオーバーは使用できません。 ただし、回避策として、多くの IP アドレス間のフェイルオーバーをサポートする DNS プロバイダーを使用できます。

ある {{site.data.keyword.cloud_notm}} 領域が使用不可になると、その領域で実行されているアプリは、たとえそれと同じアプリが別の {{site.data.keyword.cloud_notm}} 領域で実行されていても、使用不可になります。
{: tsSymptoms}

{{site.data.keyword.cloud_notm}} では、ある領域から別の領域への自動フェイルオーバーはまだ提供されていません。
{: tsCauses}

多数の ID アドレス間のインテリジェント・フェイルオーバーをサポートする DNS プロバイダーを使用し、{{site.data.keyword.cloud_notm}} 領域間の自動フェイルオーバーを使用可能にするように、DNS 設定を手動で構成することができます。 この機能を備えた DNS プロバイダーとしては、NSONE、Akamai、および Dyn があります。
{: tsResolve}

DNS 設定を構成する場合、アプリが実行されている {{site.data.keyword.cloud_notm}} 領域のパブリック IP アドレスを指定する必要があります。 {{site.data.keyword.cloud_notm}} 領域のパブリック IP アドレスを取得するには、`nslookup` コマンドを使用します。 例えば、次のコマンドをコマンド・ライン・ウィンドウに入力できます。
```
nslookup cloud.ibm.com
```
{: codeblock}

## 許可エラーのため、{{site.data.keyword.cloud_notm}} サービスにアクセスできない
{: #ts_vcap}
{: troubleshoot}

許可エラーは、アプリでサービス資格情報がハードコーディングされている場合にアプリが {{site.data.keyword.cloud_notm}} サービスにアクセスすると生じることがあります。

{{site.data.keyword.cloud_notm}} サービスと通信するようにアプリを構成した後に、そのアプリを {{site.data.keyword.cloud_notm}} にデプロイします。 しかし、アプリを使用して {{site.data.keyword.cloud_notm}} サービスにアクセスできず、許可エラーを受け取ります。
{: tsSymptoms}

アプリ内にハードコーディングされた資格情報が正しくない可能性があります。 サービスが再作成されるごとに、そのサービスにアクセスするための資格情報が変更されます。
{: tsCauses}

アプリ内に資格情報をハードコーディングするのではなく、VCAP_SERVICES 環境変数からの接続パラメーターを使用してください。 VCAP_SERVICES 環境変数からの接続パラメーターを使用する方法は、プログラミング言語によって異なります。 例えば、Node.js アプリの場合、以下のコマンドを使用できます。
{: tsResolve}

```
process.env.VCAP_SERVICES
```

他のプログラミング言語で使用できるコマンドについて詳しくは、[Java](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") および [Ruby](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") を参照してください。

## 502 Bad Gateway エラーを受信した
{: #ts_502_error}
{: troubleshoot}

{{site.data.keyword.cloud_notm}} でアプリと対話していて `502 Bad Gateway` エラーを受信した場合は、{{site.data.keyword.cloud_notm}} 状況ページを確認して、適切なアクションを実行してください。

502 Bad Gateway で始まるエラー・メッセージを受信します。 例えば、`「502 Bad Gateway: 登録済みエンドポイントが要求の処理に失敗しました。(Registered endpoint failed to handle the request.)」`と表示されます。
{: tsSymptoms}

Bad Gateway エラーは通常、Web サイトをホストするメイン・サーバーのデータの保管と中継を行うためにプロキシー・サーバーを使用している Web サイトにアクセスしたときに発生します。 メイン・サーバーとプロキシー・サーバーが正しく接続されていない可能性があります。 このため、ブラウザー・ウィンドウに HTTP 状況コード 502 が表示されます。 この状況コードは、サイトのメイン・サーバーが、予期した HTTP 実装をプロキシー・サーバーから受信しなかったことを示します。
{: tsCauses}

Bad Gateway エラーのその他のまれな原因として、インターネット・サービス・プロバイダー (ISP) のドロップアウト、ファイアウォール構成の誤り、ブラウザー・キャッシュのエラーがあります。

{{site.data.keyword.cloud_notm}} サービスがダウンしていると疑われる場合は、まず [{{site.data.keyword.cloud_notm}} 状況](https://cloud.ibm.com/status){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")ページを確認してください。 回避策として、[別の {{site.data.keyword.cloud_notm}} 地域でそのサービスを使用する](/docs/resources/connect_external_app?topic=resources-externalapp){: new_window}ことができます。 サービスの状況が正常の場合には、以下のステップで問題を解決してください。
{: tsResolve}

  * アクションを再試行します。
    * キーボードで F5 を押すか、**「最新表示」**をクリックして、ページを再ロードします。 このステップでうまくいかない場合は、ブラウザーのキャッシュと Cookie を消去してから、もう一度再ロードしてください。
    * 異なるブラウザーを使用します。
    * ルーター、モデム、およびコンピューターを再始動します。 これらのデバイスをリブートすると、エラー 502 につながる各種エラーが解消する可能性があります。
  * 時間をおいて、後で再試行します。 インターネット・サービス・プロバイダーまたは {{site.data.keyword.cloud_notm}} サービスで一時的な問題が発生していることがあります。 一時的な問題が解決されるまで待ちます。
  * 問題が解決しない場合は、{{site.data.keyword.cloud_notm}} サポートに連絡してください。 詳しくは、[{{site.data.keyword.cloud_notm}} サポートへのお問い合わせ](/docs/get-support?topic=get-support-getting-customer-support){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") を参照してください。

## Android アプリが {{site.data.keyword.mobilepushshort}} を受信できない
{: #ts_push}
{: troubleshoot}

Google にアクセス不能な特定地域の Android アプリは、IBM {{site.data.keyword.mobilepushshort}} サービスで送信した通知を受信できません。 この場合、回避策はサード・パーティーのサービスを使用することです。

{{site.data.keyword.cloud_notm}} アプリに {{site.data.keyword.mobilepushshort}} サービスをバインドして、登録デバイスにメッセージを送信します。 ただし、Android で開発されたアプリは、特定の地域で通知を受信できません。
{: tsSymptoms}

IBM {{site.data.keyword.mobilepushshort}} サービスは、Google Cloud Messaging (GCM) サービスを使用して、Android で開発されたモバイル・アプリに通知をディスパッチします。 Android アプリが通知を受信できるようにするには、Google Cloud Messaging (GCM) サービスがモバイル・アプリからアクセス可能でなければなりません。 Android アプリが GCM サービスに到達できない地域では、Android アプリは {{site.data.keyword.mobilepushshort}} を受信できません。
{: tsCauses}

回避策として、GCM サービスに依存しないサード・パーティーのサービス (例えば、[Pushy ](https://pushy.me){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")、[getui ](http://www.getui.com/){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")、および [jpush ](https://www.jpush.cn/){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")) を使用してください。
{: tsResolve}

## アプリが {{site.data.keyword.cloud_notm}} にプッシュされる際、2 バイト文字が適切に表示されない
{: #ts_doublebytes}
{: troubleshoot}

サーブレットまたは JSP ファイルに対して Unicode サポートが適切に構成されていない場合、2 バイト文字が適切に表示されない可能性があります。

アプリケーションが {{site.data.keyword.cloud_notm}} にプッシュされたときは、アプリ内に指定されている 2 バイト文字は正しく表示されません。
{: tsSymptoms}

この問題は、サーブレットまたは JSP ファイルに対して Unicode サポートが適切に構成されていない場合に発生する可能性があります。
{: tsCauses}

サーブレットまたは JSP ファイル内で、以下のコードを使用できます。
{: tsResolve}

  * サーブレット・ソース・ファイル内
  ```java
	response.setContentType("text/html; charset=UTF-8");
	```
  {: codeblock}

  * JSP 内
  ```jsp
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```
  {: codeblock}

## Node.js アプリをデプロイできない
{: #ts_nodejs_deploy}
{: troubleshoot}

Node.js アプリを更新する時、または Node.js アプリを {{site.data.keyword.cloud_notm}} にデプロイする時に問題が発生することがあります。

Node.js アプリを更新する際、または Node.js アプリを {{site.data.keyword.cloud_notm}} にデプロイする際に、以下のいずれかのエラー・メッセージが表示される場合があります。
{: tsSymptoms}

`使用可能なビルドパックによってアプリが正常に検出されませんでした。`

`インスタンス (インデックス 0) は接続の受け入れを開始できませんでした。`

`ステージングに失敗したため、インスタンスを取得できません。`

考えられる原因は次のとおりです。
{: tsCauses}

  * 開始コマンドが指定されていません。
  * Node.js アプリのデプロイに必要なファイルが、アプリから欠落しているか、ルート・ディレクトリー以外のフォルダーにあります。

問題の原因に応じて、以下のいずれかの方法を使用します。
{: tsResolve}

  * 以下のいずれかの方法で開始コマンドを指定します。
     * Cloud Foundry コマンド・ライン・インターフェースを使用します。 以下に例を示します。
      ```
		  ibmcloud cf push MyUniqueNodejs01 -p app_path -c "node app.js"
		  ```
      {: codeblock}

    * [package.json ](https://www.npmjs.com/package/jsonfile){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") ファイルを使用します。 例:
	    ```json
		  {
        ...
  	    "scripts": {
	 		  "start": "node app.js"
 	   }
	    }
	    ```

    * `manifest.yml` ファイルを使用します。 例:
	    ```
		  applications:
  name: MyUniqueNodejs01
  ...
      command: node app.js
  ...
      ```

  * Node.js ビルドパックがアプリを認識できるように、ご使用の Node.js アプリ内に必ず `package.json` ファイルが存在するようにしてください。 このファイルは必ずアプリのルート・ディレクトリーに置いてください。
    以下は単純な `package.json` ファイルの例です。
	```json
	{
        "name": "MyUniqueNodejs01",
        "version": "0.0.1",
        "description": "A sample package.json file",
        "dependencies": {
                "express": "3.4.x",
                "jade": "1.1.x"
        },
        "engines": {
                "node": "0.10.x"
        　　　　},
        "scripts": {
                  "start": "node app.js"
        }
 }
    ```

Node.js アプリについてさらにヒントを見るには、[Node.js アプリケーションに関するヒント (Tips for Node.js Applications) ](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") を参照してください。

## Eclipse に {{site.data.keyword.cloud_notm}} Liberty アプリをインポートした後、`server.xml` ファイル内に構成エラーが現れる
{: #ts_eclipse}
{: troubleshoot}

{{site.data.keyword.cloud_notm}} Liberty アプリを Eclipse にインポートした後、`server.xml` ファイル内に構成エラーを認めた場合は、プロジェクトから `server.xml` ファイルを削除しなければならないことがあります。

{{site.data.keyword.cloud_notm}} Liberty アプリを Eclipse にインポートした後、Eclipse の「問題」ビューから `server.xml` ファイル内の構成エラーを確認できます。
{: tsSymptoms}

Liberty アプリが {{site.data.keyword.cloud_notm}} にプッシュされると、Liberty ビルドパックは `server.xml` ファイルを使用してアプリを構成し、`runtime-vars.xml` ファイルを生成します。 アプリを Eclipse にインポートする際、`runtime-vars.xml` ファイルはご使用のローカル環境に存在しません。
{: tsCauses}

server.xml ファイルをプロジェクトから削除することで、この問題を解決できます。 アプリを WAR アプリとしてプッシュすると、ビルドパックは `server.xml` ファイルを動的に作成します。 詳しくは、[『Liberty forJava』](/docs/runtimes/liberty?topic=liberty-liberty_runtime#liberty_runtime)を参照してください。
{: tsResolve}

## カスタム・ビルドパックを使用してアプリをステージングできない
{: #ts_bp_compilation}
{: troubleshoot}

カスタム・ビルドパック内のスクリプトが実行可能ファイルでない場合、そのビルドパックを使用して {{site.data.keyword.cloud_notm}} にアプリをデプロイできないことがあります。

カスタム・ビルドパックを使用して {{site.data.keyword.cloud_notm}} にアプリをデプロイすると、`「アプリケーションがステージングに失敗したため、表示するインスタンスはありません」`というエラー・メッセージが表示されます。
{: tsSymptoms}

この問題は、検出スクリプト、コンパイル・スクリプト、リリース・スクリプトなどのスクリプトが実行可能でない場合は発生する可能性があります。
{: tsCauses}

[Git update](http://git-scm.com/docs/git-update-index){: new_window} ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン") コマンドを使用して、各スクリプトのアクセス権を実行可能に変更できます。 例えば、`git update --chmod=+x script.sh` と入力できます。
{: tsResolve}

## {{site.data.keyword.cloud_notm}} Continuous Delivery の Delivery Pipeline からアプリをデプロイできない
{: #ts_devops_to_bm}
{: troubleshoot}

 アプリに `manifest.yml` ファイルが存在しない場合、{{site.data.keyword.contdelivery_short}} の {{site.data.keyword.deliverypipeline}} を使用してアプリをデプロイできないことがあります。

 {{site.data.keyword.contdelivery_short}} の {{site.data.keyword.deliverypipeline}} を使用してアプリをデプロイすると、エラー・メッセージ`「サポートされるアプリケーション・タイプを検出できません (Unable to detect a supported application type)」`が表示されることがあります。
 {: tsSymptoms}

 この問題は、{{site.data.keyword.cloud_notm}} にアプリをデプロイするために、パイプラインが `manifest.yml` ファイルを必要とすることが原因で発生する可能性があります。
 {: tsCauses}

 この問題を解決するには、`manifest.yml` ファイルを作成する必要があります。 `manifest.yml` ファイルの作成方法について詳しくは、『[アプリケーション・マニフェスト](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest)』を参照してください。
 {: tsResolve}

## ストレージ割り当て量を超えた
{: #exceed_quota}

ビルド・ジョブまたはデプロイ・ジョブが失敗し、次のメッセージが表示された場合、以下の CLI コマンドを使用してイメージを削除できます。 `状況: 無許可: ストレージ割り当て量を超過しています。 1 つ以上のイメージを削除するか、ストレージ割り当て量と価格設定プランを確認してください。`

* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli) がまだない場合には、インストールします。
* `ibmcloud login` を使用して {{site.data.keyword.cloud_notm}} にログインし、現在のスペースを指すようにします。
* `ibmcloud cr images` を使用して、イメージをリストします。
* 未使用のイメージがある場合、`ibmcloud cr image-rm <respository>:<tag>` を使用して削除します。
* 失敗したビルド・ジョブまたはデプロイ・ジョブを再実行します。

## Kubernetes ログのアクセス
{: #access_kube_logs}

アプリケーションが実行されておらず、ヘルス・エンドポイントにアクセスできない場合、クラスター内のログを調べてください。
* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli) がまだない場合には、インストールします。
* `ibmcloud login` を使用して {{site.data.keyword.cloud_notm}} にログインし、現在のスペースを指すようにします。
* `ibmcloud cs clusters` を使用して、クラスターをリストします。
* `ibmcloud cs cluster-config <cluster-name>` を使用して、該当するクラスターを指します。
* リストされた環境変数をエクスポートします。
* `kubectl get pods` を使用して、ポッドを表示します。 `kubectl` をインストールする必要がある場合には、[Install and set up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/){: new_window} ![外部リンクのアイコン](../icons/launch-glyph.svg "外部リンクのアイコン") を参照してください。
* `kubectl logs <pod-name>.` を使用して、アプリのログを表示できます。

## 「ファイルが見つかりません」というメッセージが表示され、`docker` の起動に失敗する
{: #docker_not_found}
{: troubleshoot}

Docker を起動しようとすると、次のエラー・メッセージが表示されます。
{: tsSymptoms}

```
"docker" の実行でエラー: Docker イメージのビルド中に、$PATH に実行可能ファイルが見つかりませんでした。
```
{: screen}

Docker クライアントがインストールされていないか、インストールされているものの開始されていません。
{: tsCauses}

[Docker](https://docs.docker.com/install/){: new_window} ![外部リンクのアイコン](../icons/launch-glyph.svg "外部リンクのアイコン") がインストールされていることを確認し、開始します。
{: tsResolve}

## Docker エラーでアプリのビルドが失敗する
{: #build_error}
{: troubleshoot}

`ibmcloud dev build` コマンドを使用してアプリをビルドしようとすると、Docker のユーザー名/パスワードのエラーで失敗します。 
{: tsSymptoms}

認証に不適切な Docker Hub の資格情報が使用されています。 
{: tsCauses}

Docker クライアントで Docker ハブからログアウトします。
{: tsResolve}
