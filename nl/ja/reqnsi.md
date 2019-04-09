---

copyright:
  years: 2015, 2016, 2017, 2018
lastupdated: "2018-01-18"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}

# アプリへのサービスの追加
{: #add_service}

アプリケーションにサービスを追加するには、そのサービスのインスタンスを要求し、そのサービスと対話するようにアプリケーションを構成します。
{: shortdesc}

以下の方法で、{{site.data.keyword.Bluemix_notm}} で使用可能なサービスをすべて表示できます。

* {{site.data.keyword.Bluemix_notm}} コンソールから。 {{site.data.keyword.Bluemix_notm}} カタログを表示します。
* bluemix コマンド・ライン・インターフェースから。 **bluemix service offerings** コマンドを使用します。
* ご使用のアプリケーションから。[GET /v2/services Services API](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window} を使用します。

アプリケーションを開発するときに、必要なサービスを選択できます。選択すると、{{site.data.keyword.Bluemix_notm}} はサービスと対話し、サービスのリソースをプロビジョンするのに必要な手順を実行します。サービスのタイプによってプロビジョンのプロセスが異なる場合があります。 例えば、データベース・サービスはデータベースを作成し、モバイル・アプリケーションのプッシュ通知サービスは構成情報を生成します。

{{site.data.keyword.Bluemix_notm}} は、サービス・インスタンスを使用してサービスのリソースをアプリケーションに提供します。サービス・インスタンスは Web アプリケーション間で共有できます。

他の地域でホストされているサービスがその地域内で使用可能である場合、それらのサービスを使用することもできます。これらのサービスはインターネットからアクセスできる必要があり、さらに API エンドポイントを持つ必要があります。{{site.data.keyword.Bluemix_notm}} サービスを利用するために外部アプリケーションやサード・パーティー・ツールをコード化するのと同様に、これらのサービスを利用するにはお使いのアプリケーションを手動でコード化する必要があります。詳しくは、『[{{site.data.keyword.Bluemix_notm}} サービスを利用するための外部アプリケーションとサード・パーティー・ツールの使用可能化](#accser_external)』を参照してください。

## 新規サービス・インスタンスの要求
{: #req_instance}

新規サービス・インスタンスを要求するには、{{site.data.keyword.Bluemix_notm}} ユーザー・インターフェースまたは bluemix コマンド・ライン・インターフェースを使用する必要があります。

**注:** サービス名を指定するときは、英字と数字のみを使用してください。英字と数字以外を使用すると、予測できない結果が生じる可能性があります。

{{site.data.keyword.Bluemix_notm}} ユーザー・インターフェースを使用してサービス・インスタンスを要求する場合、以下のステップを実行します。

1. {{site.data.keyword.Bluemix_notm}} **カタログ**で、追加するサービスのタイルをクリックします。サービス詳細ページが開きます。

2. **「サービス名」**フィールドに名前を入力します。 デフォルトのサービス名が表示されます。このフィールドで名前を変更できますし、変更せずにそのままにすることもできます。

3. 追加のフィールドまたは選択に入力してから、**「作成」**をクリックします。

bluemix コマンド・ライン・インターフェースを使用してサービス・インスタンスを要求する場合、以下のステップを実行します。

1. **bluemix service offerings** コマンドを使用して、要求するサービスの名前とプランを見つけます。

2. 以下のコマンドを使用してサービス・インスタンスを作成します。ここで、service_name はサービスの名前、service_plan はサービスのプラン、service_instance はこのサービス・インスタンス用に使用する名前です。

```
bluemix service create service_name service_plan service_instance
```

3. 以下のコマンドを使用してサービス・インスタンスをアプリケーションにバインドします。ここで、appname はアプリケーションの名前、service_instance はサービス・インスタンスの名前です。

```
bluemix service bind appname service_instance
```

サービス・インスタンスは、同じスペースまたは組織内のアプリ・インスタンスにのみバインド可能です。ただし、外部アプリと同じように他のスペースまたは組織からサービス・インスタンスを使用できます。バインディングを作成する代わりに、資格情報を使用してアプリ・インスタンスを直接構成します。 外部アプリが {{site.data.keyword.Bluemix_notm}} サービスを使用する方法について詳しくは、[『外部アプリが {{site.data.keyword.Bluemix_notm}} サービスを使用できるようにする』](#accser_external){: new_window}を参照してください。

## アプリケーションの構成
{: #config}

ご使用のアプリケーションにサービス・インスタンスをバインドした後、そのサービスと対話するようアプリケーションを構成する必要があります。

各サービスは、アプリケーションと通信するために別のメカニズムを必要とする場合もあります。これらのメカニズムについては、アプリケーションを開発するときに、サービス定義の一部として情報が文書化されます。一貫性のために、メカニズムは、アプリケーションがサービスと対話するために必要です。

* データベース・サービスと対話するには、ユーザー ID、パスワード、およびアプリケーションのアクセス URI など、{{site.data.keyword.Bluemix_notm}} が提供する情報を使用します。
* モバイル・バックエンド・サービスと対話するには、アプリケーション ID (アプリ ID)、クライアント固有のセキュリティー情報、およびアプリケーションのアクセス URI など、{{site.data.keyword.Bluemix_notm}} が提供する情報を使用します。アプリケーション開発者の名前やアプリケーションを使用するユーザーなどのコンテキスト情報を一連のサービスで共有できるように、モバイル・サービスは、通常、互いのコンテキストで作業します。
* Web アプリケーションと、またはモバイル・アプリケーションのサーバー・サイドのクラウド・コードと対話するには、アプリケーションの *VCAP_SERVICES* 環境変数内のランタイム資格情報など、{{site.data.keyword.Bluemix_notm}} が提供する情報を使用します。*VCAP_SERVICES* 環境変数の値は、JSON オブジェクトの直列化です。変数には、アプリケーションにバインドされているサービスと対話するために必要なランタイム・データが含まれます。データのフォーマットは、サービスごとに異なります。期待される情報と、情報の各部分を解釈する方法について、サービスの文書を読み取る必要が生じる場合もあります。

アプリケーションにバインドしたサービスが異常終了すると、そのアプリケーションが稼動を停止したり、エラーを起こしたりする場合があります。これらの問題からリカバリーするために {{site.data.keyword.Bluemix_notm}} がアプリケーションを自動的に再始動することはありません。障害、例外、および接続失敗を識別してリカバリーするようにアプリケーションをコーディングすることを検討してください。詳しくは、[アプリの非自動再始動](/docs/troubleshoot/ts_apps.html#ts_topmenubar)のトラブルシューティングのトピックを参照してください。

## 外部アプリの使用可能化
{: #accser_external}

{{site.data.keyword.Bluemix_notm}} の外部で作成および実行されたアプリケーションがある場合や、サード・パーティーのツールを使用する場合があります。 インターネットからアクセスできるサービス・キーを {{site.data.keyword.Bluemix_notm}} サービスが提供している場合、それらのサービスをローカル・アプリやサード・パーティー・ツールで使用できます。

外部で使用するためのサービス・キーを提供するサービスは次のとおりです。

* {{site.data.keyword.amashort_old}} <!--Advanced Mobile Access-->
* {{site.data.keyword.alchemyapishort}} <!--AlchemyAPI-->
* {{site.data.keyword.alertnotificationshort}} <!--Alert Notification-->
* {{site.data.keyword.sparks}} <!--Analytics for Apache Spark-->
* {{site.data.keyword.appseccloudshort}} <!--Application Security on Cloud-->
* {{site.data.keyword.blockchain}} <!--Blockchain-->
* {{site.data.keyword.cloudant}} <!--Cloudant&reg; NoSQL DB-->
* {{site.data.keyword.iotmapinsights_short}} <!--Context Mapping-->
* {{site.data.keyword.conversationshort}} <!--Conversation-->
* {{site.data.keyword.dashdbshort}} <!--dashDB-->
* {{site.data.keyword.discoveryshort}} <!--Discovery-->
* {{site.data.keyword.documentconversionshort}} <!--Document Conversion-->
* {{site.data.keyword.iotdriverinsights_short}} <!--Driver Behavior-->
* {{site.data.keyword.geospatialshort_Geospatial}} <!--Geospatial Analytics-->
* {{site.data.keyword.GlobalizationPipeline_short}} <!--Globalization Pipeline-->
* {{site.data.keyword.appconserviceshort}} <!--IBM&reg; App Connect-->
* {{site.data.keyword.dataworks_short}} <!--IBM&reg; Data Connect-->
* {{site.data.keyword.graphshort}} <!--IBM&reg; Graph-->
* {{site.data.keyword.iotelectronics_full}} <!--IBM&reg; IoT for Electronics-->
* {{site.data.keyword.twittershort}} <!--Insights for Twitter-->
* {{site.data.keyword.iot4auto_short}} <!--IoT for Automotive-->
* {{site.data.keyword.iotinsurance_short}} <!--IoT for Insurance-->
* {{site.data.keyword.languagetranslatorshort}} <!--Language Translator-->
* {{site.data.keyword.dwl_short}} <!--Lift-->
* {{site.data.keyword.messagehub}} <!--Message Hub-->
* {{site.data.keyword.mobileanalytics_short}} <!--Mobile Analytics-->
* {{site.data.keyword.nlclassifiershort}} <!--Natural Language Classifier-->
* {{site.data.keyword.objectstorageshort}} <!--Object Storage-->
* {{site.data.keyword.personalityinsightsshort}} <!--Personality Insights-->
* {{site.data.keyword.HybridConnect_short}} <!--Product Insights-->
* {{site.data.keyword.mobilepush}} <!--Push-->
* {{site.data.keyword.retrieveandrankshort}} <!--Retrieve and Rank-->
* {{site.data.keyword.speechtotextshort}} <!-- Speech to Text-->
* {{site.data.keyword.streaminganalyticsshort}} <!--Streaming Analytics-->
* {{site.data.keyword.texttospeechshort}} <!--Text to Speech-->
* {{site.data.keyword.toneanalyzershort}} <!--Tone Analyzer-->
* {{site.data.keyword.tradeoffanalyticsshort}} <!--Tradeoff Analytics-->
* {{site.data.keyword.weather_short}} <!--Weather Company Data-->
* {{site.data.keyword.workloadscheduler}} <!--Workload Scheduler-->

外部アプリまたはサード・パーティー・ツールで {{site.data.keyword.Bluemix_notm}} サービスを使用できるようにするには、以下のステップを実行します。

1. サービスのインスタンスを要求します。
    1. {{site.data.keyword.Bluemix_notm}} ユーザー・インターフェースのダッシュボードで、**「リソースの作成」**をクリックします。 「カタログ」が表示されます。
    2. 「カタログ」で、サービス・タイルをクリックして必要なサービスを選択します。サービス詳細ページが開きます。
    3. サービスのウィンドウで、デフォルトの**「接続先:」**リスト選択を**「アンバインドのまま」**にしておきます。 この選択は、サービスが {{site.data.keyword.Bluemix_notm}} アプリに接続されないことを意味します。
    4. 必要に応じてその他の選択を行います。次に、**「作成」**をクリックします。 サービス・インスタンスが作成され、サービスの「ダッシュボード」が表示されます。
2. サービスの「ダッシュボード」で、**「サービス資格情報 (Service Credentials)」**を選択すると JSON 形式で資格情報を表示および追加することができます。 資格情報のセットを選択し、「アクション」列で**「資格情報の表示」**をクリックします。 資格情報として表示されている API キーを使用して、サービス・インスタンスに接続します。

これで、{{site.data.keyword.Bluemix_notm}} の外部で実行されるアプリケーションが、{{site.data.keyword.Bluemix_notm}} サービスにアクセスできるようになりました。

**注:** サービス・インスタンスの削除または請求情報の確認を行う場合は、ユーザー・インターフェースの「ダッシュボード」に戻ってサービス・インスタンスを管理する必要があります。

## ユーザー提供のサービス・インスタンスの作成
{: #user_provide_services}

{{site.data.keyword.Bluemix_notm}} の外部で管理されているリソースが存在する場合もあります。そうした外部リソースにインターネットからアクセスするための資格情報を持っていれば、{{site.data.keyword.Bluemix_notm}} のユーザー提供サービス・インスタンスを作成することによって、外部リソースを表現し、そのリソースと通信することができます。

ユーザー提供のサービス・インスタンスを作成し、それをアプリケーションにバインドするには、以下のステップを実行します。

1. **bluemix service user-provided-create** コマンドを使用して、ユーザー提供のサービス・インスタンスを作成します。
    * 一般的なユーザー提供のサービス・インスタンスを作成するには、**-p** オプションを使用し、パラメーター名をコンマで区切ります。bx コマンド・ライン・インターフェースはその後、各パラメーターについて順にプロンプトを出します。 例えば次のようにします。
        ```
        bluemix service user-provided-create testups1 -p "host, port, dbname, username, password"
        host> pubsub01.example.com
        port> 1234
        dbname> sampledb01
        username> pubsubuser
        password> p@$$w0rd
        Creating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * サード・パーティーのログ管理ソフトウェアに情報をドレーンするサービス・インスタンスを作成するには、**-l** オプションを使用し、そのサード・パーティーのログ管理ソフトウェアが提供する宛先を指定します。例えば次のようにします。

        ```
        bluemix service user-provided-create testups2 -l syslog://example.com
        Creating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

    ユーザー提供のサービス・インスタンスの 1 つ以上のパラメーターを更新する場合は、**bluemix service user-provided-update** コマンドを使用します。

    * 一般的なユーザー提供のサービス・インスタンスを更新するには、**-p** オプションを使用して、パラメーターのキーと値を JSON オブジェクトで指定します。例えば次のようにします。

        ```
        bluemix service user-provided-update testups1 -p "{\"username\":\"pubsubuser2\",\"password\":\"p@$$w0rd2\"}"
        Updating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * サード・パーティーのログ管理ソフトウェアに情報をドレーンするサービス・インスタンスを作成するには、-l オプションを使用します。例えば次のようにします。

        ```
        bluemix service user-provided-create testups2 -l syslog://example2.com
        Updating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

2. `bluemix service bind` コマンドを使用して、サービス・インスタンスをアプリケーションにバインドします。 例えば次のようにします。

	```
	bluemix service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

外部リソースを使用するようアプリケーションを構成できるようになりました。サービスと対話するようアプリケーションを構成する方法については、[「サービスと対話するようアプリケーションを構成する」](#config){: new_window}を参照してください。
