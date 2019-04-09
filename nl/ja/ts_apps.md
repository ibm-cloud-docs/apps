---

copyright:
  years: 2015, 2019
lastupdated: "2019-01-30"

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

## 保存されていない変更があります
{: #ts_unsaved_changes}
{: troubleshoot}

アプリの詳細ページで項目をクリックしたときに、アクションを実行できない場合があります。続行する前に、変更を保存するように求めるプロンプトが出される場合もあります。

アプリの詳細ページでアプリまたはサービスを確認しようとすると、次のエラー・メッセージが表示されます。
{: tsSymptoms}

`保存されていない変更があります。 このページを終了してよろしいですか?`

マウスをスクロールして、「ランタイム」ペインの**「インスタンス」**フィールドまたは**「メモリー割り当て量」**フィールドの上に移動すると、それらの値が変わります。 この動作は、設計によるものです。ただし、別のページに移動する前にメモリー設定またはインスタンス設定を保存するよう求めるプロンプトが表示されます。
{: tsCauses}

メッセージ・ダイアログを閉じ、ランタイム・ペインの**「リセット」**をクリックします。
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


## 削除したアプリの名前を再使用できない
{: #ts_reuse_appname}
{: troubleshoot}

アプリを削除したら、アプリ経路を削除した場合に限り、アプリ名を再使用できます。

アプリ名を再使用しようとしたときに、以下のメッセージを受け取ります。
{: tsSymptoms}

`名前は別のアプリによって既に使用されています。`

アプリが削除された時、アプリの URL である経路は自動的に削除されず、再使用できません。 アプリを再使用するため経路を削除するには、アプリが作成されたスペースに移動する必要があります。
{: tsCauses}

使用されていない経路を削除するには、以下の手順を実行します。
{: tsResolve}

  1. 以下のコマンドを入力して、該当経路が現行スペースに属しているかどうかを確認します
    ```
    ibmcloud cf routes
    ```
    {: codeblock}

  2. 該当経路が現行スペースに属していない場合は、以下のコマンドを入力して、それが属しているスペースまたは組織に切り替えます。
    ```
    ibmcloud cf target -o org_name -s space_name
    ```
    {: codeblock}

  3. 以下のコマンドを入力して、アプリ経路を削除します。
    ```
    ibmcloud cf delete-route domain_name -n host_name
    ```
    {: codeblock}

  例えば次のようにします。
  ```
  ibmcloud cf delete-route cf.cloud.ibm.com -n app001
  ```
  {: codeblock}

## 組織のスペースを取得できない
{: #ts_retrieve_space}
{: troubleshoot}

現行組織に関連付けられたスペースがない場合、アプリまたはサービスを作成できません。

{{site.data.keyword.cloud_notm}} でアプリを作成しようとすると、以下のエラー・メッセージが表示されます。
{: tsSymptoms}

`BXNUI0515E: 組織のスペースは取得されませんでした。 ネットワーク接続問題が発生したか、現在の組織に関連付けられているスペースがないかのいずれかです。`

このエラーは、多くの場合、カタログからアプリまたはサービスを初めて作成しようとしたときに、スペースがまだ作成されていない場合に発生します。
{: tsCauses}

現行組織にスペースを作成したことを確認してください。 スペースを作成するには、次のいずれかの方法を使用します。
{: tsResolve}

* メニュー・バーで、**「管理」>「アカウント」**をクリックし、**「Cloud Foundry の組織」**を選択します。 スペースを作成する組織を選択してから、**「スペースの作成」**をクリックします。
* Cloud Foundry コマンド・ライン・インターフェースに `cf create-space <space_name> -o <organization_name>` と入力します。

やり直してください。 このメッセージが再び発生する場合、[{{site.data.keyword.cloud_notm}} 状況 ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](http://ibm.biz/bluemixstatus){: new_window} ページにアクセスして、サービスまたはコンポーネントに問題がないか確認してください。

## 要求したアクションを実行できない
{: #ts_authority}
{: troubleshoot}

適切なアクセス権限がない場合、アクションを実行できません。

サービス・インスタンスまたはアプリ・インスタンスに対してアクションを実行しようとしたとき、要求したアクションを実行できず、以下のいずれかのエラー・メッセージが表示されます。
{: tsSymptoms}

`BXNUI0514E: <orgName> 組織のスペースの開発者ではありません。`

`サーバー・エラー、状況コード: 403、エラー・コード: 10003、メッセージ: 要求されたアクションの実行を許可されていません`

アクションを実行するための適切なレベルの権限を備えていません。
{: tsCauses}

適切な権限レベルを取得するには、以下のいずれかの方法を使用します。
{: tsResolve}

* 開発者役割を持つ別の組織およびスペースを選択します。
* 自分の役割を開発者に変更するように、またはスペースを作成して自分に開発者役割を割り当てるように組織マネージャーに依頼します。詳しくは、『[組織とスペースの管理](/docs/admin/orgs_spaces.html)』を参照してください。

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

他のプログラミング言語で使用できるコマンドについて詳しくは、[Java![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} および [Ruby![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window} を参照してください。

## 502 Bad Gateway エラーを受信した
{: #ts_502_error}
{: troubleshoot}

{{site.data.keyword.cloud_notm}} でアプリと対話していて `502 Bad Gateway` エラーを受信した場合は、{{site.data.keyword.cloud_notm}} 状況ページを確認して、適切なアクションを実行してください。

502 Bad Gateway で始まるエラー・メッセージを受信します。 例えば、`「502 Bad Gateway: 登録済みエンドポイントが要求の処理に失敗しました。(Registered endpoint failed to handle the request.)」`と表示されます。
{: tsSymptoms}

Bad Gateway エラーは通常、Web サイトをホストするメイン・サーバーのデータの保管と中継を行うためにプロキシー・サーバーを使用している Web サイトにアクセスしたときに発生します。 メイン・サーバーとプロキシー・サーバーが正しく接続されていない可能性があります。 このため、ブラウザー・ウィンドウに HTTP 状況コード 502 が表示されます。 この状況コードは、サイトのメイン・サーバーが、予期した HTTP 実装をプロキシー・サーバーから受信しなかったことを示します。
{: tsCauses}

Bad Gateway エラーのその他のまれな原因として、インターネット・サービス・プロバイダー (ISP) のドロップアウト、ファイアウォール構成の誤り、ブラウザー・キャッシュのエラーがあります。

{{site.data.keyword.cloud_notm}} サービスがダウンしていると疑われる場合は、まず [{{site.data.keyword.cloud_notm}} 状況![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](http://ibm.biz/bluemixstatus){: new_window}ページを確認してください。 回避策として、別の {{site.data.keyword.cloud_notm}} 地域でそのサービスを使用することができます。 『[サービスを別の地域で使用![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/services/reqnsi.html#cross_region_service){: new_window}』に詳しい説明があります。 サービスの状況が正常の場合には、以下のステップで問題を解決してください。
{: tsResolve}

  * アクションを再試行します。
    * キーボードで F5 を押すか、**「最新表示」**をクリックして、ページを再ロードします。 このステップでうまくいかない場合は、ブラウザーのキャッシュと Cookie を消去してから、もう一度再ロードしてください。
    * 異なるブラウザーを使用します。
    * ルーター、モデム、およびコンピューターを再始動します。 これらのデバイスをリブートすると、エラー 502 につながる各種エラーが解消する可能性があります。
  * 時間をおいて、後で再試行します。 インターネット・サービス・プロバイダーまたは {{site.data.keyword.cloud_notm}} サービスで一時的な問題が発生していることがあります。 一時的な問題が解決されるまで待ちます。
  * 問題が解決しない場合は、{{site.data.keyword.cloud_notm}} サポートに連絡してください。 詳しくは、[{{site.data.keyword.cloud_notm}} サポートへのお問い合わせ ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](/docs/support/index.html#contacting-bluemix-support){: new_window} を参照してください。

## ディスク割り当て量を超えた
{: #ts_disk_quota}
{: troubleshoot}

ディスク・スペースを使い尽くした場合には、手動でディスク割り当て量を変更して、ディスク・スペースを追加することができます。

ディスク・スペースを使い尽くしたときに、ディスク割り当て量を超えたというメッセージが表示される場合があります。 この問題を解決するために、アプリ・インスタンスをスケールアップしてディスク・スペースを追加しようとした可能性があります。 例えば、アプリの詳細ページでメモリー割り当て量を変更して 256 MB から 1256 MB に拡大した、などです。しかし、ディスク割り当て量は同じままであったために、ディスク・スペースは追加されませんでした。
{: tsSymptoms}

アプリに割り当てられるデフォルトのディスク割り当て量は 1 GB です。 追加のディスク・スペースが必要な場合は、ディスク割り当て量を手動で指定する必要があります。
{: tsCauses}

以下のいずれかの方法でディスク割り当て量を指定します。 指定できる最大ディスク割り当て量は 2 GB です。 2 GB でも不十分な場合は、[オブジェクト・ストア](/docs/services/ObjectStorage/index.html)などの外部サービスを試してください。
{: tsResolve}

  * manifest.yml ファイルに以下の項目を追加します。
  ```yaml
	disk_quota: <disk_quota>
	```
  * アプリを {{site.data.keyword.cloud_notm}} にプッシュするときに、以下のように `ibmcloud cf push` コマンドに **-k** オプションを使用します。

  ```
	ibmcloud cf push appname -p app_path -k <disk_quota>
	```
  {: codeblock}

## Android アプリが {{site.data.keyword.mobilepushshort}} を受信できない
{: #ts_push}
{: troubleshoot}

Google にアクセス不能な特定地域の Android アプリは、IBM {{site.data.keyword.mobilepushshort}} サービスで送信した通知を受信できません。 この場合、回避策はサード・パーティーのサービスを使用することです。

{{site.data.keyword.cloud_notm}} アプリに {{site.data.keyword.mobilepushshort}} サービスをバインドして、登録デバイスにメッセージを送信します。ただし、Android で開発されたアプリは、特定の地域で通知を受信できません。
{: tsSymptoms}

IBM {{site.data.keyword.mobilepushshort}} サービスは、Google Cloud Messaging (GCM) サービスを使用して、Android で開発されたモバイル・アプリに通知をディスパッチします。Android アプリが通知を受信できるようにするには、Google Cloud Messaging (GCM) サービスがモバイル・アプリからアクセス可能でなければなりません。 Android アプリが GCM サービスに到達できない地域では、Android アプリは {{site.data.keyword.mobilepushshort}} を受信できません。
{: tsCauses}

回避策として、GCM サービスに依存しないサード・パーティーのサービス (例えば、[Pushy ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://pushy.me){: new_window}、[getui ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.getui.com/){: new_window}、および [jpush ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.jpush.cn/){: new_window}) を使用してください。
{: tsResolve}

## 組織のサービス上限の超過
{: #ts_servicelimit}
{: troubleshoot}

ライト・アカウント・ユーザーの場合、組織のサービス上限を超過すると、{{site.data.keyword.cloud_notm}} でアプリを作成できなくなる場合があります。

{{site.data.keyword.cloud_notm}} でアプリを作成しようとすると、以下のエラー・メッセージが表示されます。
{: tsSymptoms}

`BXNUI2032E: <service_instances> リソースは作成されませんでした。 リソースを作成するために Cloud Foundry に接続している時にエラーが発生しました。 Cloud Foundry メッセージ:「組織のサービス上限を超過しました。」`

このエラーは、そのアカウントで持つことのできるサービス・インスタンス数の上限を超過した時に発生します。
{: tsCauses}

不要なサービス・インスタンスをすべて削除するか、持つことができるサービス・インスタンス数の上限を撤廃します。
{: tsResolve}

  * サービス・インスタンスを削除するには、{{site.data.keyword.cloud_notm}} コンソールか、またはコマンド・ライン・インターフェースが使用できます。

    {{site.data.keyword.cloud_notm}} コンソールを使用してサービス・インスタンスを削除するには、以下の手順を実行します。
	  1. リソース・リストで、削除するサービスの**「アクション」**メニューをクリックします。
	  2. **「サービスの削除 (Delete Service)」**をクリックします。 そのサービス・インスタンスがバインドされていたアプリを再ステージするようにプロンプトが出されます。

    コマンド・ライン・インターフェースを使用してサービス・インスタンスを削除するには、以下の手順を実行します。
	  3. アプリからサービス・インスタンスをアンバインドします。`cf unbind-service <appname> <service_instance_name>` を入力します。
	  4. サービス・インスタンスを削除します。`cf delete-service <service_instance_name>` を入力します。
	  5. サービス・インスタンスを削除した後、サービス・インスタンスがバインドされていたアプリを再ステージすることもできます。`cf restage <appname>` を入力します。

  * 使用できるサービス・インスタンス数の上限を撤廃するには、ライト・アカウントを有料アカウントにアップグレードします。詳しくは、『[アカウントのアップグレード](/docs/account/index.html#upgrade-to-paygo)』を参照してください。

## 実行可能ファイルが {{site.data.keyword.cloud_notm}} で実行できない
{: #ts_executable}
{: troubleshoot}

実行可能ファイルは、別の環境で開発とビルドが行われた場合、{{site.data.keyword.cloud_notm}} で実行できないことがあります。

実行可能ファイルは、別の環境で開発とビルドを行った時は、{{site.data.keyword.cloud_notm}} で実行することができません。
{: tsSymptoms}

{{site.data.keyword.cloud_notm}} にプッシュしたいコンテンツが既に実行可能ファイルであれば、そのコンテンツは前にビルドされており、{{site.data.keyword.cloud_notm}} でビルドする必要はありません。 その場合、{{site.data.keyword.cloud_notm}} でその実行可能ファイルを実行するためにビルドパックは必要ありません。 {{site.data.keyword.cloud_notm}} には、ビルドパックが不要であることを明示的に示さなければなりません。
{: tsCauses}

その実行可能ファイルを {{site.data.keyword.cloud_notm}} にプッシュするときに、ビルドパックが不要であることを示す `null-buildpack` を指定する必要があります。`ibmcloud cf push` コマンドで **-b** オプションを使用して `null-buildpack` を指定します。
{: tsResolve}

```
ibmcloud cf push appname -p app_path -c <start_command> -b <null-buildpack>
```
{: codeblock}

例えば次のようにします。
```
ibmcloud cf push appname -p app_path -c ./RunMeNow -b https://github.com/ryandotsmith/null-buildpack
```
{: codeblock}

## 組織のメモリー上限を超過
{: #ts_outofmemory}
{: troubleshoot}

ライト・アカウントのユーザーの場合、組織のメモリー限度を超過すると、{{site.data.keyword.cloud_notm}} にアプリをデプロイできなくなることがあります。ユーザーにできるのは、自分のアプリが使用するメモリーを削減すること、あるいは自分のアカウントのメモリー割り当て量を増やすことです。 ライト・アカウントの最大メモリー割り当て量は 256 MB で、これは有料アカウントにアップグレードすることでのみ増やすことができます。


アプリを {{site.data.keyword.cloud_notm}} にデプロイすると、次のエラー・メッセージが表示されます。
{: tsSymptoms}

`失敗 サーバー・エラー、状況コード: 400、エラー・コード: 100005、メッセージ: 組織のメモリー上限を超過しました。`

このエラーは、組織の残りメモリー量が、デプロイしたいアプリに必要なメモリー量を下回っている時に発生します。 ライト・アカウントの最大メモリー割り当て量は 256 MB です。
{: tsCauses}

自分のアカウントのメモリー割り当て量を増やすか、自分のアプリが使用するメモリーを減らすか、そのいずれかを行うことができます。
{: tsResolve}

  * アカウントのメモリー割り当て量を増やすには、ライト・アカウントを有料アカウントにアップグレードしてください。詳しくは、『[アカウントのアップグレード](/docs/account/index.html#upgrade-to-paygo)』を参照してください。
  * アプリが使用するメモリーを削減するには、{{site.data.keyword.cloud_notm}} コンソールまたは Cloud Foundry コマンド・ライン・インターフェースのいずれかを使用します。

    {{site.data.keyword.cloud_notm}} コンソールを使用する場合は、以下の手順を実行します。

    1. リソース・リストからアプリを選択します。アプリ詳細ページが開きます。
    2. 「ランタイム」ペインで、そのアプリの最大メモリー上限またはアプリ・インスタンス数のいずれか、あるいはその両方を減らすことができます。

    コマンド・ライン・インターフェースを使用する場合は、以下の手順を実行します。

    1. アプリで使用しているメモリー量を調べます。
  	  ```
	    ibmcloud cf list
	    ```
      {: codeblock}

	    `ibmcloud cf list` コマンドで、自分が現行スペースにデプロイしたアプリがすべてリストされます。 各アプリの状況も表示されます。

    2. アプリが使用するメモリー量を削減するには、アプリ・インスタンス数または最大メモリー上限のいずれか、あるいはその両方を減らします。
	    ```
	    ibmcloud cf push appname -p app_path -i instance_number -m memory_limit
      ```
      {: codeblock}

    3. アプリを再始動して、変更を有効にします。

## アプリが自動的に再始動しない
{: #ts_apps_not_auto_restarted}
{: troubleshoot}

アプリは、アプリにバインドしているサービスが機能を停止した時、自動的に再始動されません。

アプリにバインドしているサービスが異常終了すると、そのアプリで停止、例外、接続障害といった問題が発生した可能性があります。 {{site.data.keyword.cloud_notm}} では、それらの問題から復旧するためにアプリを自動的に再始動することはありません。
{: tsSymptoms}

この動作は Cloud Foundry の設計によるものです。
{: tsCauses}

コマンド・ライン・インターフェースで以下のコマンドを入力すれば、アプリを手動で再始動できます。
{: tsResolve}

```
ibmcloud cf push appname -p app_path
```
{: codeblock}

さらに、停止、例外、接続障害といった問題を見つけて、そのような問題から復旧するようにアプリをコーディングすることもできます。

<!-- begin STAGING ONLY -->

## {{site.data.keyword.cloud_notm}} Live Sync Debug がコマンド・ラインから開始しない
{: #ts_no_debug}
{: troubleshoot}

コマンド・ラインを使用して {{site.data.keyword.cloud_notm}} Live Sync Debug フィーチャーをアプリに対して使用可能にしたが、デバッグ・インターフェースにアクセスできません。

**BLUEMIX_APP_MGMT_ENABLE** 環境変数を設定し、アプリにデバッグ・フィーチャーを使用可能にしました。 しかし、`app_url/bluemix-debug/manage` でデバッグ・ユーザー・インターフェースにアクセスできません。
{: tsSymptoms}

以下の状況では、デバッグ・フィーチャーを使用可能にすることができません。
{: tsCauses}

  * `manifest.yml` に command 属性が含まれる場合
  * **-c** オプションを使用してアプリを {{site.data.keyword.cloud_notm}} にプッシュする場合

以下のいずれかのオプションを使用して問題を解決します。
{: tsResolve}

  * 推奨されるのは、IBM Node.js ビルドパックを使用してアプリを開始する方法です。 詳しくは、[{{site.data.keyword.cloud_notm}} への Node.js アプリケーションのデプロイ](/docs/runtimes/nodejs/index.html#nodejs_runtime)トピックの「開始コマンド」セクションを参照してください。
  * `manifest.yml` の command 属性を command: null に修正するか、push コマンドを編集して `-c null` を組み込むことで、既存アプリにコマンドを使用不可にします。
  * `manifest.yml` から **command** 属性を削除します。 その後、{{site.data.keyword.cloud_notm}} から現行アプリを削除し、アプリを再びプッシュします。

<!-- end STAGING ONLY -->

## 組織が {{site.data.keyword.cloud_notm}} で見つからない
{: #ts_orgs}
{: troubleshoot}

ある {{site.data.keyword.cloud_notm}} 地域で作業しているときに、{{site.data.keyword.cloud_notm}} で自分の組織が見つからない場合があります。

{{site.data.keyword.cloud_notm}} コンソールに正常にログインできますが、Cloud Foundry コマンド・ライン・インターフェースを使用してアプリをプッシュすることができません。
{: tsSymptoms}

Cloud Foundry コマンド・ライン・インターフェースを使用してアプリケーションを  {{site.data.keyword.cloud_notm}} にプッシュしようとすると、メッセージ内に組織名が指定された、次のいずれかのメッセージが表示されます。

`組織の検索中にエラーが発生しました (Error finding org)`

`組織が見つかりません (Organization not found)`

この問題は、処理したい地域の API エンドポイントが指定されていないことが原因で発生します。探している組織が、別の地域にある可能性があります。
{: tsCauses}

Cloud Foundry コマンド・ライン・インターフェースを使用して {{site.data.keyword.cloud_notm}} にアプリケーションをプッシュする場合は、`cf api` コマンドを入力し、地域の API エンドポイントを指定します。 例えば、以下のコマンドを入力して、{{site.data.keyword.cloud_notm}} の欧州英国地域に接続します。
{: tsResolve}

```
cf api https://api.eu-gb.cf.cloud.ibm.com
```
{: codeblock}


## アプリの経路を作成できない
{: #ts_hostistaken}
{: troubleshoot}

アプリを {{site.data.keyword.cloud_notm}} にデプロイする際、指定したホスト名がすでに使用されていると、アプリの経路を作成できません。

アプリを {{site.data.keyword.cloud_notm}} にデプロイする際、次のエラー・メッセージが表示されます。
{: tsSymptoms}

`経路 hostname.domainname を作成中... 失敗サーバー・エラー、状況コード: 400、エラー・コード: 210003、メッセージ: ホストは使用済みです: hostname (Creating route hostname.domainname ... FAILED Server error, status code: 400, error code: 210003, message: The host is  taken: hostname)`

この問題は、ユーザーが指定したホスト名が既に使用されている場合に発生します。
{: tsCauses}

指定するホスト名は、使用するドメイン内で固有でなければなりません。 別のホスト名を指定するには、以下のいずれかの方法を使用して下さい。
{: tsResolve}

  * `manifest.yml` ファイルを使用してアプリケーションをデプロイする場合は、host オプションでホスト名を指定します。
    ```yaml
    host: host_name
	  ```

  * コマンド・プロンプトからアプリケーションをデプロイする場合は、`ibmcloud cf push` コマンドを **-n** オプションで使用します。
    ```
    ibmcloud cf push appname -p app_path -n host_name
    ```
    {: codeblock}

## ibmcloud cf push コマンドを使用して WAR アプリをプッシュできない
{: #ts_cf_war}
{: troubleshoot}

アプリのロケーションが正しく指定されていないと、`ibmcloud cf push` コマンドを使用してアーカイブ済み Web アプリを {{site.data.keyword.cloud_notm}} にデプロイできない場合があります。

`ibmcloud cf push` コマンドを使用して WAR アプリを {{site.data.keyword.cloud_notm}} にアップロードする際に、次のエラー・メッセージが表示されます。
{: tsSymptoms}
`ステージング・エラー: ステージングに失敗したため、インスタンスを取得できません。(Staging error: cannot get instances since staging failed.)`

この問題は、WAR ファイルが指定されていない場合や、WAR ファイルへのパスが指定されていない場合に発生する可能性があります。
{: tsCauses}

**-p** オプションを使用して、WAR ファイルを指定するか、WAR ファイルへのパスを追加してください。 以下に例を示します。
{: tsResolve}

```
ibmcloud cf push MyUniqueAppName01 -p app.war
```
{: codeblock}

```
ibmcloud cf push MyUniqueAppName02 -p "./app.war"
```
{: codeblock}

`ibmcloud cf push` コマンドの詳細な情報を確認するには、`ibmcloud cf push -h` を入力してください。

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

    * [package.json ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.npmjs.com/package/jsonfile){: new_window} ファイルを使用します。 例:
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

Node.js アプリについてさらにヒントを見るには、[Node.js アプリケーションに関するヒント (Tips for Node.js Applications) ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window} を参照してください。

## Eclipse に {{site.data.keyword.cloud_notm}} Liberty アプリをインポートした後、`server.xml` ファイル内に構成エラーが現れる
{: #ts_eclipse}
{: troubleshoot}

{{site.data.keyword.cloud_notm}} Liberty アプリを Eclipse にインポートした後、`server.xml` ファイル内に構成エラーを認めた場合は、プロジェクトから `server.xml` ファイルを削除しなければならないことがあります。

{{site.data.keyword.cloud_notm}} Liberty アプリを Eclipse にインポートした後、Eclipse の「問題」ビューから `server.xml` ファイル内の構成エラーを確認できます。
{: tsSymptoms}

Liberty アプリが {{site.data.keyword.cloud_notm}} にプッシュされると、Liberty ビルドパックは `server.xml` ファイルを使用してアプリを構成し、`runtime-vars.xml` ファイルを生成します。 アプリを Eclipse にインポートする際、`runtime-vars.xml` ファイルはご使用のローカル環境に存在しません。
{: tsCauses}

server.xml ファイルをプロジェクトから削除することで、この問題を解決できます。 アプリを WAR アプリとしてプッシュすると、ビルドパックは `server.xml` ファイルを動的に作成します。 詳しくは、[『Liberty for
Java』](/docs/runtimes/liberty/index.html)を参照してください。
{: tsResolve}

## カスタム・ビルドパックを使用してアプリをステージングできない
{: #ts_bp_compilation}
{: troubleshoot}

カスタム・ビルドパック内のスクリプトが実行可能ファイルでない場合、そのビルドパックを使用して {{site.data.keyword.cloud_notm}} にアプリをデプロイできないことがあります。

カスタム・ビルドパックを使用して {{site.data.keyword.cloud_notm}} にアプリをデプロイすると、`「アプリケーションがステージングに失敗したため、表示するインスタンスはありません」`というエラー・メッセージが表示されます。
{: tsSymptoms}

この問題は、検出スクリプト、コンパイル・スクリプト、リリース・スクリプトなどのスクリプトが実行可能でない場合は発生する可能性があります。
{: tsCauses}

[Git update![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](http://git-scm.com/docs/git-update-index){: new_window} コマンドを使用して、各スクリプトのアクセス権を実行可能に変更できます。 例えば、`git update --chmod=+x script.sh` と入力できます。
{: tsResolve}

## {{site.data.keyword.cloud_notm}} Continuous Delivery の Delivery Pipeline からアプリをデプロイできない
{: #ts_devops_to_bm}
{: troubleshoot}

 アプリに `manifest.yml` ファイルが存在しない場合、{{site.data.keyword.contdelivery_short}} の {{site.data.keyword.deliverypipeline}} を使用してアプリをデプロイできないことがあります。

 {{site.data.keyword.contdelivery_short}} の {{site.data.keyword.deliverypipeline}} を使用してアプリをデプロイすると、エラー・メッセージ`「サポートされるアプリケーション・タイプを検出できません (Unable to detect a supported application type)」`が表示されることがあります。
 {: tsSymptoms}

 この問題は、{{site.data.keyword.cloud_notm}} にアプリをデプロイするために、パイプラインが `manifest.yml` ファイルを必要とすることが原因で発生する可能性があります。
 {: tsCauses}

 この問題を解決するには、`manifest.yml` ファイルを作成する必要があります。 `manifest.yml` ファイルの作成方法について詳しくは、『[アプリケーション・マニフェスト](/docs/manageapps/depapps.html#appmanifest)』を参照してください。
 {: tsResolve}

## Meteor アプリをプッシュできない
{: #ts_meteor}
{: troubleshoot}

ビルドパックが正しく指定されていない場合、Meteor アプリケーションを {{site.data.keyword.cloud_notm}} にプッシュできない可能性があります。

{{site.data.keyword.cloud_notm}} に Meteor アプリをデプロイすると、`「アプリケーションがステージングに失敗したため、表示するインスタンスはありません」`というエラー・メッセージが表示されることがあります。
{: tsSymptoms}

この問題は、Meteor アプリ用に組み込みビルドパックが提供されていないことが原因で発生します。 カスタム・ビルドパックを使用する必要があります。
{: tsCauses}

Meteor アプリにカスタム・ビルドパックを使用するには、以下のいずれかの方法を使用します。
{: tsResolve}

  * `manifest.yml` ファイルを使用してアプリをデプロイする場合は、buildpack オプションを使用して、カスタム・ビルドパックの URL または名前を指定します。 例えば次のようにします。
  ```yaml
  buildpack: https://github.com/Sing-Li/bluemix-bp-meteor
  ```

  * コマンド・プロンプトからアプリケーションをデプロイする場合は、`ibmcloud cf push` コマンドを使用し、**-b** オプションによってカスタム・ビルドパックを指定します。 例えば次のようにします。
  ```
	ibmcloud cf push appname -p app_path -b https://github.com/Sing-Li/bluemix-bp-meteor
	```
  {: codeblock}

## ストレージ割り当て量を超えた
{: #exceed_quota}

ビルド・ジョブまたはデプロイ・ジョブが失敗し、次のメッセージが表示された場合、以下の CLI コマンドを使用してイメージを削除できます。 `状況: 無許可: ストレージ割り当て量を超過しています。 1 つ以上のイメージを削除するか、ストレージ割り当て量と価格設定プランを確認してください。`

* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html) がまだない場合は、インストールします。
* `ibmcloud login` を使用して {{site.data.keyword.cloud_notm}} にログインし、現在のスペースを指すようにします。
* `ibmcloud cr images` を使用して、イメージをリストします。
* 未使用のイメージがある場合、`ibmcloud cr image-rm <respository>:<tag>` を使用して削除します。
* 失敗したビルド・ジョブまたはデプロイ・ジョブを再実行します。

## Kubernetes ログのアクセス
{: #access_kube_logs}

アプリケーションが実行されておらず、ヘルス・エンドポイントにアクセスできない場合、クラスター内のログを調べてください。
* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html) がまだない場合は、インストールします。
* `ibmcloud login` を使用して {{site.data.keyword.cloud_notm}} にログインし、現在のスペースを指すようにします。
* `ibmcloud cs clusters` を使用して、クラスターをリストします。
* `ibmcloud cs cluster-config <cluster-name>` を使用して、該当するクラスターを指します。
* リストされた環境変数をエクスポートします。
* `kubectl get pods` を使用して、ポッドを表示します。 `kubectl` をインストールする必要がある場合、[Install and set up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/) を参照してください。
* `kubectl logs <pod-name>` を使用して、アプリのログを表示できます。


## "ファイルが見つかりません" というメッセージが表示され、`docker` の起動に失敗する
{: #docker_not_found}
{: troubleshoot}

Docker を起動しようとすると、次のエラー・メッセージが表示されます。
{: tsSymptoms}

```
"docker" の実行でエラー: Docker イメージのビルド中に、$PATH に実行可能ファイルが見つかりませんでした。
```
{: screen}

Docker クライアントがインストールされていないか、インストールされているが開始されていません。
{: tsCauses}

[Docker](https://docs.docker.com/install/) がインストールされていることを確認し、起動します。
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


