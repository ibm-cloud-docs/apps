---

copyright:
  years: 2015, 2016, 2017, 2018
lastupdated: "2018-01-18"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}

# 앱에 서비스 추가
{: #add_service}

애플리케이션에 서비스를 추가하려면 서비스의 인스턴스를 요청하고 서비스와 상호작용하도록 애플리케이션을 구성해야 합니다.
{: shortdesc}

다음 방법으로 {{site.data.keyword.Bluemix_notm}}에서 사용 가능한 모든 서비스를 확인할 수 있습니다.

* {{site.data.keyword.Bluemix_notm}} 콘솔에서 {{site.data.keyword.Bluemix_notm}} 카탈로그를 확인합니다.
* bluemix 명령행 인터페이스에서 **bluemix service offerings** 명령을 사용합니다.
* 사용자 고유 애플리케이션: [GET /v2/services 서비스 API](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window}를 사용합니다.

애플리케이션을 개발할 때 필요한 서비스를 선택할 수 있습니다. 선택하면 {{site.data.keyword.Bluemix_notm}}에서 서비스와 상호작용하여 서비스 리소스를 프로비저닝하는 데 필요한 단계를 수행합니다. 프로비저닝 프로세스는 서로 다른 유형의 서비스마다 서로 다를 수 있습니다. 예를 들어, 데이터베이스 서비스는 데이터베이스를 작성하고, 모바일 애플리케이션의 푸시 알림 서비스는 구성 정보를 생성합니다.

{{site.data.keyword.Bluemix_notm}}에서는 서비스 인스턴스를 사용하여 애플리케이션에 서비스 리소스를 제공합니다. 서비스 인스턴스는 웹 애플리케이션 간에 공유할 수 있습니다.

다른 지역에서 호스팅되는 서비스가 해당 지역에서 사용 가능할 경우 이 서비스도 사용할 수 있습니다. 이러한 서비스는 인터넷을 통해 액세스할 수 있으며 API 엔드포인트를 사용합니다. {{site.data.keyword.Bluemix_notm}} 서비스를 사용하도록 외부 애플리케이션 또는 써드파티 도구를 코딩할 때와 동일한 방식으로 이러한 서비스를 사용하도록 애플리케이션을 수동으로 코딩해야 합니다. 자세한 정보는 [외부 애플리케이션 및 써드파티 도구가 {{site.data.keyword.Bluemix_notm}} 서비스를 사용하도록 설정](#accser_external)을 참조하십시오.

## 새 서비스 인스턴스 요청
{: #req_instance}

새 서비스 인스턴스를 요청하려면 {{site.data.keyword.Bluemix_notm}} 사용자 인터페이스 또는 bluemix 명령행 인터페이스를 사용해야 합니다.

**참고:** 서비스 이름을 지정하는 경우 영문자 또는 숫자만 사용하십시오. 그렇지 않을 경우 예측할 수 없는 결과가 초래될 수 있습니다.

{{site.data.keyword.Bluemix_notm}} 사용자 인터페이스를 사용하여 서비스 인스턴스를 요청하는 경우에는 다음 단계를 완료하십시오.

1. {{site.data.keyword.Bluemix_notm}} **카탈로그**에서 추가할 서비스의 타일을 클릭하십시오. 서비스 세부사항 페이지가 열립니다.

2. **서비스 이름** 필드에 이름을 입력하십시오. 기본 서비스 이름이 제공됩니다. 필드에서 이름을 변경하거나, 기본 이름을 그대로 사용할 수 있습니다.

3. 추가 필드나 선택사항을 채운 다음 **작성**을 클릭하십시오.

bluemix 명령행 인터페이스를 사용하여 서비스 인스턴스를 요청하는 경우에는 다음 단계를 완료하십시오.

1. **bluemix service offerings** 명령을 사용하여 필요한 서비스의 이름과 플랜을 찾으십시오.

2. 다음 명령을 사용하여 서비스 인스턴스를 작성하십시오. 여기서 service_name은 서비스 이름이고, service_plan은 서비스 플랜이며, service_instance는 이 서비스 인스턴스에 사용할 이름입니다.

```
bluemix service create service_name service_plan service_instance
```

3. 다음 명령을 사용하여 서비스 인스턴스를 애플리케이션에 바인딩하십시오. 여기서 appname은 애플리케이션의 이름이고, service_instance는 서비스 인스턴스의 이름입니다.

```
bluemix service bind appname service_instance
```

동일한 영역 또는 조직 내의 해당 앱 인스턴스에만 서비스 인스턴스를 바인딩할 수 있습니다. 단, 외부 앱이 사용하는 것과 동일한 방식으로 기타 영역 또는 조직에서 서비스 인스턴스를 사용할 수 있습니다. 바인딩을 작성하는 대신 신임 정보를 사용하여 앱 인스턴스를 직접 구성할 수 있습니다. 외부 앱이 {{site.data.keyword.Bluemix_notm}} 서비스를 사용하는 방법에 대한 자세한 정보는 [외부 앱이 {{site.data.keyword.Bluemix_notm}} 서비스를 사용하도록 설정](#accser_external){: new_window}을 참조하십시오.

## 애플리케이션 구성
{: #config}

서비스 인스턴스를 애플리케이션에 바인딩한 후에는 애플리케이션이 서비스와 상호작용하도록 구성해야 합니다.

애플리케이션과 상호작용하는 데 서비스마다 서로 다른 메커니즘이 필요할 수 있습니다. 이러한 메커니즘은 애플리케이션을 개발할 때 사용자의 정보에 대한 서비스 정의의 일부로 기술됩니다. 일관성을 위해 애플리케이션이 서비스와 상호작용하기 위한 메커니즘이 필요합니다.

* 데이터베이스 서비스와 상호작용하려면 사용자 ID, 비밀번호, 애플리케이션에 대한 액세스 URI 등 {{site.data.keyword.Bluemix_notm}}에서 제공하는 정보를 사용하십시오.
* 모바일 백엔드 서비스와 상호작용하려면 애플리케이션 ID(앱 ID), 클라이언트에 고유한 보안 정보, 애플리케이션에 대한 액세스 URI 등 {{site.data.keyword.Bluemix_notm}}에서 제공하는 정보를 사용하십시오. 모바일 서비스는 일반적으로 애플리케이션 개발자의 이름, 애플리케이션 사용자 등의 컨텍스트정보를 서비스 세트에서 공유할 수 있도록 서로 함께 작동합니다.
* 웹 애플리케이션 또는 모바일 애플리케이션의 서버 측 클라우드 코드와 상호작용하려면 애플리케이션의 *VCAP_SERVICES* 환경 변수에 있는 런타임 신임 정보 등 {{site.data.keyword.Bluemix_notm}}에서 제공하는 정보를 사용하십시오. *VCAP_SERVICES* 환경 변수의 값은 직렬화된 JSON 오브젝트입니다. 이 변수에는 애플리케이션이 바인딩된 서비스와 상호작용하는 데 필요한 런타임 데이터가 포함되어 있습니다. 데이터 형식은 서비스마다 다릅니다. 예상 내용 및 각 정보를 해석하는 방법에 대한 서비스 문서를 읽어야 할 수 있습니다.

애플리케이션에 바인딩한 서비스가 충돌할 경우 애플리케이션 실행이 중단되거나 애플리케이션에서 오류가 발생할 수 있습니다. {{site.data.keyword.Bluemix_notm}}에서는 이러한 문제점에서 복구하기 위해 애플리케이션을 자동으로 다시 시작하지 않습니다. 가동 중단, 예외, 연결 오류를 식별하고 이러한 오류에서 복구할 수 있도록 애플리케이션 코딩을 고려하십시오. 자세한 정보는 [앱이 자동으로 다시 시작되지 않음](/docs/troubleshoot/ts_apps.html#ts_topmenubar) 문제점 해결 주제를 참조하십시오.

## 외부 앱 사용
{: #accser_external}

{{site.data.keyword.Bluemix_notm}} 외부에서 작성되어 실행되는 애플리케이션을 사용하거나, 써드파티 도구를 사용할 수 있습니다. {{site.data.keyword.Bluemix_notm}} 서비스가 인터넷을 통해 액세스할 수 있는 서비스 키를 제공하는 경우 로컬 앱 또는 써드파티 도구에서 이러한 서비스를 사용할 수 있습니다.

다음 서비스는 외부적으로 사용할 서비스 키를 제공합니다.

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

외부 앱이나 써드파티 도구에서 {{site.data.keyword.Bluemix_notm}} 서비스를 사용하도록 하려면 다음 단계를 완료하십시오.

1. 서비스의 인스턴스를 요청하십시오.
    1. {{site.data.keyword.Bluemix_notm}} 사용자 인터페이스의 대시보드에서 **리소스 작성**을 클릭하십시오. 카탈로그가 표시됩니다.
    2. 카탈로그에서 서비스 타일을 클릭하여 원하는 서비스를 선택하십시오. 서비스 세부사항 페이지가 열립니다.
    3. 서비스 창에서 기본 **연결 대상:**: 목록 선택사항을 **언바인드 상태로 두기**로 유지하십시오. 이 선택사항은 서비스가 {{site.data.keyword.Bluemix_notm}} 앱에 연결되지 않음을 의미합니다.
    4. 필요에 따라 기타 선택사항을 작성하십시오. 그런 다음 **작성**을 클릭하십시오. 서비스 인스턴스가 작성되고 서비스 대시보드가 표시됩니다.
2. 서비스 대시보드에서 **서비스 신임 정보**를 선택하여 JSON 형식의 신임 정보를 보거나 추가할 수 있습니다. 신임 정보 세트를 선택하고 조치 열에서 **신임 정보 보기**를 클릭하십시오. 표시되는 API 키를 신임 정보로 사용하여 서비스 인스턴스에 연결하십시오.

{{site.data.keyword.Bluemix_notm}} 외부에서 실행되는 애플리케이션이 이제 {{site.data.keyword.Bluemix_notm}} 서비스에 액세스할 수 있습니다.

**참고:** 서비스 인스턴스를 삭제하거나 청구 정보를 확인하려면 서비스 인스턴스를 관리하기 위해 사용자 인터페이스의 대시보드로 되돌아가야 합니다.

## 사용자 제공 서비스 인스턴스 작성
{: #user_provide_services}

{{site.data.keyword.Bluemix_notm}} 외부에서 관리되는 리소스들이 있을 수 있습니다. 인터넷에서 이들 외부 리소스에 액세스하기 위한 신임 정보를 가지고 있는 경우, {{site.data.keyword.Bluemix_notm}} 사용자 제공 서비스 인스턴스를 작성하여 외부 리소스를 표시하고 통신할 수 있습니다.

사용자 제공 서비스 인스턴스를 작성하고 애플리케이션에 바인딩하려면 다음 단계를 완료하십시오.

1. **bluemix service user-provided-create** 명령을 사용하여 사용자 제공 서비스 인스턴스를 작성하십시오.
    * 일반적인 사용자 제공 서비스 인스턴스를 작성하려면 **-p** 옵션을 사용하고 매개변수 이름을 쉼표로 구분하십시오. 그러면 bx 명령행 인터페이스에서 각 매개변수에 대한 프롬프트를 차례로 제시합니다. 예를 들어, 다음과 같습니다.
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

    * 써드파티 로그 관리 소프트웨어로 정보를 제공하는 서비스 인스턴스를 작성하려면 **-l** 옵션을 사용하고 써드파티 로그 관리 소프트웨어가 제공하는 대상을 지정하십시오. 예를 들어, 다음과 같습니다.

        ```
        bluemix service user-provided-create testups2 -l syslog://example.com
        Creating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

    사용자 제공 서비스 인스턴스의 하나 이상의 매개변수를 업데이트하려면 **bluemix service user-provided-update**를 사용하십시오.

    * 일반적인 사용자 제공 서비스 인스턴스를 업데이트하려면 **-p** 옵션을 사용하고 JSON 오브젝트에 매개변수 키 및 값을 지정하십시오. 예를 들어, 다음과 같습니다.

        ```
        bluemix service user-provided-update testups1 -p "{\"username\":\"pubsubuser2\",\"password\":\"p@$$w0rd2\"}"
        Updating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * 써드파티 로그 관리 소프트웨어로 정보를 제공하는 서비스 인스턴스를 작성하려면 -l 옵션을 사용하십시오. 예를 들어, 다음과 같습니다.

        ```
        bluemix service user-provided-create testups2 -l syslog://example2.com
        Updating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

2. `bluemix service bind` 명령을 사용하여 서비스 인스턴스를 애플리케이션에 바인딩하십시오. 예를 들어, 다음과 같습니다.

	```
	bluemix service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

이제 외부 리소스를 사용하도록 애플리케이션을 구성할 수 있습니다. 서비스와 상호작용하도록 애플리케이션을 구성하는 방법은 [서비스와 상호작용하도록 애플리케이션 구성](#config){: new_window}을 참조하십시오.
