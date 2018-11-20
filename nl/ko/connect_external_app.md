---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-05"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{: tip: .tip}

# 외부 앱에 서비스 연결
{: #externalapp}

{{site.data.keyword.Bluemix_notm}} 외부에서 작성되어 실행되는 애플리케이션을 사용하거나, 서드파티 도구를 사용할 수 있습니다. {{site.data.keyword.Bluemix_notm}} 서비스가 인터넷을 통해 액세스할 수 있는 서비스 키를 제공하는 경우 로컬 앱 또는 서드파티 도구에서 이러한 서비스를 사용할 수 있습니다.

다음 서비스는 외부적으로 사용할 서비스 키를 제공합니다.

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

외부 앱이나 서드파티 도구에서 {{site.data.keyword.Bluemix_notm}} 서비스를 사용하도록 하려면 다음 단계를 완료하십시오.

1. 서비스 인스턴스를 작성하십시오.
    1. **카탈로그**를 클릭하십시오.
    2. 카탈로그에서 서비스 타일을 클릭하여 원하는 서비스를 선택하십시오. 
    3. 위치와 조직 및 공간 또는 리소스 그룹을 선택한 다음 **작성**을 클릭하십시오.
2. 서비스 세부사항 페이지에서 **서비스 인증 정보**를 선택하여 JSON 형식으로 신임 정보를 보거나 추가하십시오. 
    * 새 인증 정보를 작성하려면 **새 인증 정보**를 선택하고 선택적으로 구성 매개변수를 수동으로 추가하거나 JSON 형식으로 파일을 가져온 다음 **추가**를 클릭하십시오. **인증 정보 보기**를 선택하여 외부 앱에 연결하기 위한 인증 정보를 저장하십시오.
    * 인증 정보 세트를 선택하고 조치 열에서 **인증 정보 보기**를 클릭하십시오(이미 있는 경우). 
3. 표시되는 API 키를 인증 정보로 사용하여 서비스 인스턴스에 연결하십시오.

{{site.data.keyword.Bluemix_notm}} 외부에서 실행되는 애플리케이션이 이제 {{site.data.keyword.Bluemix_notm}} 서비스에 액세스할 수 있습니다.

서비스 인스턴스를 삭제하거나 청구 정보를 확인하려면 서비스 인스턴스를 관리하기 위해 사용자 인터페이스의 대시보드로 되돌아가야 합니다.
{: tip}
