---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-25"

keywords: apps, services, add service, application, service, instance, ibmcloud dev edit, vcap_services, credentials

subcollection: creating-apps

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{:note: .note}

# 앱에 서비스 추가
{: #add-resource}

{{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}에서 앱을 작성할 때 앱 세부사항 페이지에서 서비스를 추가할 수 있습니다. 앱의 컨텍스트에 속하지 않는 {{site.data.keyword.cloud_notm}} 카탈로그로부터 직접 리소스를 프로비저닝할 수도 있습니다.
{: shortdesc}

사용자는 서비스의 인스턴스를 요청하고 앱과 무관하게 이를 사용하거나, 앱 세부사항 페이지에서 앱에 서비스 인스턴스를 추가할 수 있습니다. 특정 유형의 서비스를 {{site.data.keyword.cloud_notm}} 카탈로그로부터 직접 프로비저닝할 수 있습니다.

## 자동 프로비저닝된 서비스
{: #auto-provision}

스타터 킷이 필수 서비스를 지정하는 경우 사용자가 앱을 작성할 때 {{site.data.keyword.cloud_notm}}에서 이러한 서비스의 인스턴스를 자동으로 작성합니다. 서비스를 수동으로 작성하거나 앱이 작성된 후에 앱에 추가할 기존 서비스 인스턴스를 선택할 수도 있습니다. 나중에 필요한 경우 **앱 세부사항** 페이지에서 앱과 연결된 서비스 인스턴스 목록을 서비스 인증 정보와 함께 볼 수 있습니다.

## 서비스 검색
{: #discover-resources}

다음 방법으로 {{site.data.keyword.cloud_notm}}에서 사용 가능한 모든 서비스를 확인할 수 있습니다.

* {{site.data.keyword.cloud_notm}} 콘솔에서 {{site.data.keyword.cloud_notm}} 카탈로그를 봅니다.
* 명령행에서 `ibmcloud service offerings` 명령을 사용합니다.
* 사용자 고유 애플리케이션: [GET /v2/services 서비스 API ](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")를 사용하십시오.

애플리케이션을 개발할 때 필요한 서비스를 선택할 수 있습니다. 이를 선택하면 {{site.data.keyword.cloud_notm}}가 서비스를 프로비저닝합니다. 프로비저닝 프로세스는 서로 다른 유형의 서비스마다 서로 다를 수 있습니다. 예를 들어, 데이터베이스 서비스는 데이터베이스를 작성하고, 모바일 애플리케이션의 푸시 알림 서비스는 구성 정보를 생성합니다.

{{site.data.keyword.cloud_notm}}에서는 서비스 인스턴스를 사용하여 애플리케이션에 서비스 리소스를 제공합니다. 서비스 인스턴스는 웹 애플리케이션 간에 공유할 수 있습니다.

다른 지역에서 호스팅되는 서비스가 해당 지역에서 사용 가능할 경우 이 서비스도 사용할 수 있습니다. 이러한 서비스는 인터넷을 통해 액세스할 수 있으며 API 엔드포인트를 사용합니다. {{site.data.keyword.cloud_notm}} 서비스를 사용하도록 외부 애플리케이션 또는 서드파티 도구를 코딩할 때와 동일한 방식으로 이러한 서비스를 사용하도록 애플리케이션을 수동으로 코딩해야 합니다. 자세한 정보는 [외부 앱에 서비스 연결](/docs/resources?topic=resources-externalapp)을 참조하십시오.

## 새 서비스 인스턴스 요청
{: #request-instance}

새 서비스 인스턴스를 요청하려면 {{site.data.keyword.cloud_notm}} 사용자 인터페이스 또는 {{site.data.keyword.cloud_notm}} 명령행 인터페이스를 사용해야 합니다.

서비스 이름을 지정할 때는 영문자 또는 숫자 이외의 문자는 사용하지 마십시오. 예측할 수 없는 결과가 발생할 수 있습니다.
{: note}

{{site.data.keyword.cloud_notm}} 사용자 인터페이스를 사용하여 서비스 인스턴스를 요청하는 경우에는 다음 단계를 완료하십시오.

1. {{site.data.keyword.cloud_notm}} 카탈로그에서 추가할 서비스의 타일을 클릭하십시오. 서비스 세부사항 페이지가 열립니다.

2. **서비스 이름** 필드에 이름을 입력하십시오. 기본 이름이 제공됩니다. 필드에서 이름을 변경하거나, 기본 이름을 그대로 사용할 수 있습니다.

3. 추가 필드 또는 선택사항을 완료한 후 **작성**을 클릭하십시오.

{{site.data.keyword.cloud_notm}} 명령행 인터페이스를 사용하여 서비스 인스턴스를 요청하는 경우, 앱을 로컬로 다운로드하고 명령행을 열고 앱 디렉토리로 변경하십시오.

1. 다음 명령을 실행하여 앱에 서비스를 추가하십시오. 계정에서 이미 사용되고 있는 기존 서비스 중 하나를 선택하거나 새 서비스를 추가할 수 있습니다.

  ```bash
ibmcloud dev edit
  ```
  {: pre}

2. 프롬프트에 따라 리소스 그룹을 선택하고 새 데이터 관련 서비스를 작성하고 Cloudant와 같은 애플리케이션에 연결하십시오. 서비스의 지역 및 플랜을 선택해야 합니다.
3. 서비스가 작성되면 인증 정보를 포함한 여러 파일이 애플리케이션 디렉토리에 추가되어 사용자가 서비스를 애플리케이션으로 통합할 수 있습니다. 임의 파일을 수동으로 병합하거나 이 단계를 건너뛸 수 있습니다.

동일한 영역 또는 조직 내의 해당 앱 인스턴스에만 서비스 인스턴스를 바인딩할 수 있습니다. 단, 외부 앱이 사용하는 것과 동일한 방식으로 기타 영역 또는 조직에서 서비스 인스턴스를 사용할 수 있습니다. 바인딩을 작성하는 대신 인증 정보를 사용하여 앱 인스턴스를 직접 구성하십시오. 외부 앱이 {{site.data.keyword.cloud_notm}} 서비스를 사용하는 방법에 대한 자세한 정보는 [외부 앱이 {{site.data.keyword.cloud_notm}} 서비스를 사용하도록 설정](/docs/resources?topic=resources-externalapp#externalapp)을 참조하십시오.

## 애플리케이션 구성
{: #configure-app}

서비스 인스턴스를 애플리케이션에 바인딩한 후에는 애플리케이션이 서비스와 상호작용하도록 구성해야 합니다.

애플리케이션과 상호작용하는 데 서비스마다 서로 다른 메커니즘이 필요할 수 있습니다. 이러한 메커니즘은 애플리케이션을 개발할 때 사용자의 정보에 대한 서비스 정의의 일부로 기술됩니다. 일관성을 위해 애플리케이션이 서비스와 상호작용하기 위한 메커니즘이 필요합니다.

* 데이터베이스 서비스와 상호작용하려면 사용자 ID, 비밀번호, 애플리케이션에 대한 액세스 URI 등 {{site.data.keyword.cloud_notm}}에서 제공하는 정보를 사용하십시오.
* 모바일 백엔드 서비스와 상호작용하려면 애플리케이션 ID(앱 ID), 클라이언트에 고유한 보안 정보, 애플리케이션에 대한 액세스 URI 등 {{site.data.keyword.cloud_notm}}에서 제공하는 정보를 사용하십시오. 모바일 서비스는 종종 애플리케이션 개발자의 이름, 애플리케이션 사용자 등의 컨텍스트 정보를 서비스 세트에서 공유할 수 있도록 서로 함께 작동합니다.
* 웹 애플리케이션 또는 모바일 애플리케이션의 서버 측 클라우드 코드와 상호작용하려면 애플리케이션의 *VCAP_SERVICES* 환경 변수에 있는 런타임 인증 정보 등 {{site.data.keyword.cloud_notm}}에서 제공하는 정보를 사용하십시오. *VCAP_SERVICES* 환경 변수의 값은 직렬화된 JSON 오브젝트입니다. 이 변수에는 애플리케이션이 바인딩된 서비스와 상호작용하는 데 필요한 런타임 데이터가 포함되어 있습니다. 데이터 형식은 서비스마다 다릅니다. 예상 내용 및 각 정보를 해석하는 방법에 대한 서비스 문서를 읽어야 할 수 있습니다.

애플리케이션에 바인딩한 서비스가 충돌할 경우 애플리케이션 실행이 중단되거나 애플리케이션에서 오류가 발생할 수 있습니다. {{site.data.keyword.cloud_notm}}에서는 이러한 문제점에서 복구하기 위해 애플리케이션을 자동으로 다시 시작하지 않습니다. 가동 중단, 예외, 연결 오류를 식별하고 이러한 오류에서 복구할 수 있도록 애플리케이션 코딩을 고려하십시오.

## {{site.data.keyword.cloud_notm}} 개발 환경의 서비스에 액세스
{: #migrate_instance}

{{site.data.keyword.cloud_notm}}에서 다양한 개발 옵션을 제공함에 따라 사용자는 하나의 환경에서 실행되는 서비스에 다른 환경에서 액세스할 수 있습니다. 예를 들어, Cloud Foundry에서 실행되는 서비스가 있는 경우 Kubernetes 클러스터에서 실행되는 애플리케이션에서 해당 서비스에 액세스할 수 있습니다.

### 예: Kubernetes 팟(Pod)에서 Cloud Foundry 서비스에 액세스

Kubernetes 클러스터의 팟에서 Cloud Foundry 서비스에 액세스하려면 Kubernetes 시크릿에 서비스 인증 정보를 저장하기 위해 클러스터에 서비스를 바인드해야 합니다. 그런 다음 이 정보를 앱에서 사용 가능하게 할 수 있습니다. 
{: shortdesc}

Kubernetes 시크릿에 저장된 서비스 인증 정보는 기본적으로 base64 인코딩되고 etcd로 암호화됩니다. 

**중요**: 배치 YAML 파일에 직접 서비스 인증 정보를 노출하거나 참조하지 마십시오. 배치 YAML 파일은 민감한 데이터를 보관하도록 디자인되지 않았으며 기본적으로 서비스 인증 정보를 암호화하지 않습니다. 이 정보를 제대로 저장하고 액세스하려면 Kubernetes 시크릿을 사용해야 합니다. 

1. [서비스를 클러스터에 바인딩](/docs/containers?topic=containers-service-binding#bind-services)하십시오. 
2. 앱 팟(Pod)에서 서비스 인증 정보에 액세스하려면 다음 옵션 중에서 선택하십시오. 
   - 시크릿을 볼륨으로 팟(Pod)에 마운트
   - 환경 변수의 시크릿 참조

## 사용자 제공 서비스 인스턴스 작성
{: #user_provide_services}

{{site.data.keyword.cloud_notm}} 외부에서 관리되는 서비스가 있을 수 있습니다. 인터넷에서 이들 외부 서비스에 액세스하기 위한 인증 정보를 가지고 있는 경우에는 {{site.data.keyword.cloud_notm}} 사용자 제공 서비스 인스턴스를 작성하여 외부 서비스를 표시하고 통신할 수 있습니다.

사용자 제공 서비스 인스턴스를 작성하고 애플리케이션에 바인딩하려면 다음 단계를 완료하십시오.

1. `ibmcloud service user-provided-create` 명령을 사용하여 사용자 제공 서비스 인스턴스를 작성하십시오.
    * 일반적인 사용자 제공 서비스 인스턴스를 작성하려면 **-p** 옵션을 사용하고 매개변수 이름을 쉼표로 구분하십시오. 그러면 `ibmcloud` 명령행 인터페이스에서 각 매개변수에 대한 프롬프트를 차례로 표시합니다. 예를 들어, 다음과 같습니다.
        ```
        ibmcloud service user-provided-create testups1 -p "host, port, dbname, username, password"
        host> pubsub01.example.com
        port> 1234
        dbname> sampledb01
        username> pubsubuser
        password> p@$$w0rd
        Creating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * 서드파티 로그 관리 소프트웨어에 정보를 제공하는 서비스 인스턴스를 작성하려면 `-l` 옵션을 사용하십시오. 서드파티 로그 관리 소프트웨어에서 제공하는 대상을 지정하십시오. 예를 들어, 다음과 같습니다.

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example.com
        Creating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

    사용자 제공 서비스 인스턴스의 매개변수를 하나 이상 업데이트하려면 `ibmcloud service user-provided-update`를 사용하십시오.

    * 일반적인 사용자 제공 서비스 인스턴스를 업데이트하려면 **-p** 옵션을 사용하고 JSON 오브젝트에 매개변수 키 및 값을 지정하십시오. 예를 들어, 다음과 같습니다.

        ```
        ibmcloud service user-provided-update testups1 -p "{\"username\":\"pubsubuser2\",\"password\":\"p@$$w0rd2\"}"
        Updating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * 서드파티 로그 관리 소프트웨어에 정보를 제공하는 서비스 인스턴스를 작성하려면 `-l` 옵션을 사용하십시오. 예를 들어, 다음과 같습니다.

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example2.com
        Updating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

2. `ibmcloud service bind` 명령을 사용하여 서비스 인스턴스를 애플리케이션에 바인드하십시오. 예를 들어, 다음과 같습니다.

	```
	ibmcloud service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

이제 외부 서비스를 사용하도록 애플리케이션을 구성할 수 있습니다. 서비스와 상호작용하도록 애플리케이션을 구성하는 방법에 대한 정보는 [서비스와 상호작용하도록 애플리케이션 구성](/docs/apps?topic=creating-apps-add-resource#configure-app)을 참조하십시오.
