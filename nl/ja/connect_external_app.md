---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-05"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{: tip: .tip}

# 外部アプリへのサービスの接続
{: #externalapp}

{{site.data.keyword.Bluemix_notm}} の外部で作成および実行されたアプリケーションがある場合や、サード・パーティーのツールを使用する場合があります。 インターネットからアクセスできるサービス・キーを {{site.data.keyword.Bluemix_notm}} サービスが提供している場合、それらのサービスをローカル・アプリやサード・パーティー・ツールで使用できます。

外部で使用するためのサービス・キーを提供するサービスは次のとおりです。

* {{site.data.keyword.alertnotificationshort}} <!--Alert Notification-->
* {{site.data.keyword.sparks}} <!--Analytics for Apache Spark-->
* {{site.data.keyword.blockchain}} <!--Blockchain-->
* {{site.data.keyword.cloudant}} <!--Cloudant&reg; NoSQL DB-->
* {{site.data.keyword.conversationshort}} <!--Conversation-->
* {{site.data.keyword.discoveryshort}} <!--Discovery-->
* {{site.data.keyword.geospatialshort_Geospatial}} <!--Geospatial Analytics-->
* {{site.data.keyword.GlobalizationPipeline_short}} <!--Globalization Pipeline-->
* {{site.data.keyword.appconserviceshort}} <!--IBM&reg; App Connect-->
* {{site.data.keyword.languagetranslatorshort}} <!--Language Translator-->
* {{site.data.keyword.dwl_short}} <!--Lift-->
* {{site.data.keyword.messagehub}} <!--Message Hub-->
* {{site.data.keyword.nlclassifiershort}} <!--Natural Language Classifier-->
* {{site.data.keyword.objectstorageshort}} <!--Object Storage-->
* {{site.data.keyword.personalityinsightsshort}} <!--Personality Insights-->
* {{site.data.keyword.mobilepush}} <!--Push-->
* {{site.data.keyword.speechtotextshort}} <!-- Speech to Text-->
* {{site.data.keyword.streaminganalyticsshort}} <!--Streaming Analytics-->
* {{site.data.keyword.texttospeechshort}} <!--Text to Speech-->
* {{site.data.keyword.toneanalyzershort}} <!--Tone Analyzer-->
* {{site.data.keyword.weather_short}} <!--Weather Company Data-->
* {{site.data.keyword.workloadscheduler}} <!--Workload Scheduler-->

外部アプリまたはサード・パーティー・ツールで {{site.data.keyword.Bluemix_notm}} サービスを使用できるようにするには、以下のステップを実行します。

1. サービスのインスタンスを作成します。
    1. **「カタログ」**をクリックします。
    2. カタログで、サービス・タイルをクリックして必要なサービスを選択します。 
    3. ロケーションと、組織およびスペースまたはリソース・グループを選択し、**「作成」**をクリックします。
2. サービス詳細ページで、**「サービス資格情報」**を選択して、JSON 形式で資格情報を表示または追加します。 
    * 新規資格情報を作成するには、**「新規資格情報」**を選択します。オプションで、構成パラメーターを手動で追加するか、または JSON 形式のファイルをインポートした後、**「追加」**をクリックします。外部アプリに接続するための資格情報を保存するため、**「資格情報の表示」**を選択します。
    * 資格情報のセットを選択し、「アクション」列の**「資格情報の表示」** をクリックします (既に存在する場合)。 
3. 資格情報として表示されている API キーを使用して、サービス・インスタンスに接続します。

これで、{{site.data.keyword.Bluemix_notm}} の外部で実行されるアプリケーションが、{{site.data.keyword.Bluemix_notm}} サービスにアクセスできるようになりました。

サービス・インスタンスの削除または請求情報の確認を行う場合は、ユーザー・インターフェースの「ダッシュボード」に戻ってサービス・インスタンスを管理する必要があります。
{: tip}
