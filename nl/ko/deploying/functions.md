---

copyright:
  years: 2018
lastupdated: "2018-07-23"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 서버리스 앱 개발
{: #serverless}

서버리스 개발을 위해 IBM의 FaaS(Functions as a Service) 오퍼링인 {{site.data.keyword.openwhisk}}를 사용할 수 있습니다. 서버를 프로비저닝하거나 관리하지 않고 HTTP를 통해 웹 또는 모바일 앱의 직접 호출이나 이벤트에 응답하여 {{site.data.keyword.openwhisk_short}}가 포함된 애플리케이션 로직을 실행할 수 있습니다. {{site.data.keyword.openwhisk_short}}가 Auto-Scaling, 가용성 관리 및 유지보수와 같은 시스템 관리를 수행함에 따라 사용자는 개발자로서 애플리케이션 로직 작성에 집중할 수 있습니다.
{:shortdesc}

{{site.data.keyword.openwhisk_short}} 사용자 인터페이스(UI) 또는 명령행 인터페이스(CLI)를 사용하여 애플리케이션을 개발할 수 있습니다. 둘 모두 애플리케이션 개발을 위한 유사한 기능이 있습니다. CLI는 배치 및 오퍼레이션에 대한 추가 제어를 제공합니다. {{site.data.keyword.openwhisk_short}}에 대한 자세한 정보는 전체 [문서](/docs/openwhisk/index.html)를 참조하십시오.

## {{site.data.keyword.openwhisk_short}} UI
{: #ui}

[브라우저 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.{DomainName}/openwhisk/actions){:new_window}에서 {{site.data.keyword.openwhisk_short}}를 시도해 보십시오. {{site.data.keyword.openwhisk_short}} 사용자 인터페이스의 빠른 둘러보기를 위해 [개념 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.{DomainName}/openwhisk/learn){:new_window} 페이지로 이동하십시오.

## CLI로 개발
{: #openwhisk_start_configure_cli}

{{site.data.keyword.openwhisk_short}} CLI를 사용한 설치 및 개발에 대해 자세히 알아보려면 [{{site.data.keyword.openwhisk_short}} CLI 설정 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.{DomainName}/openwhisk/cli){:new_window}을 참조하십시오.

## 웹 액션으로 API 및 데이터 세트 노출
{: #containers}

기본적으로 {{site.data.keyword.openwhisk_short}}는 인증 키가 필요한 액션을 정의합니다. 프로덕션 모바일 환경에서는 종종 OAuth 플로우 기반의 모바일 클라이언트에 권한을 부여하여 API 및 특정 데이터 세트를 노출해야 합니다.

{{site.data.keyword.openwhisk_short}}를 통해 개발자는 신속하게 웹 기반 애플리케이션을 빌드하도록 어노테이션된 웹 액션으로 기능을 노출할 수 있습니다. {{site.data.keyword.openwhisk_short}} 인증 키 없이도 웹 애플리케이션이 익명으로 액세스할 수 있는 어노테이션된 액션으로 백엔드 로직을 프로그래밍할 수 있습니다.

웹 액션으로 액션을 노출하려면 액션의 **엔드포인트** 탭으로 이동하여 **웹 액션으로 사용**을 선택하십시오.

이제 사용자는 브라우저 또는 cURL 요청의 액션에 도달할 수 있습니다. 예를 들면, 다음과 같습니다.

```
curl https://openwhisk.ng.bluemix.net/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

**출력:**

```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}}는 iOS 및 watchOS 디바이스를 위한 [모바일 SDK](/docs/openwhisk/openwhisk_mobile_sdk.html#mobile-sdk)를 제공하여 모바일 앱이 쉽게 원격 트리거를 전송하고 원격 액션을 호출할 수 있도록 합니다. 또한 서버리스 애플리케이션을 사용으로 설정하는 [서버리스 프레임워크 SDK ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](docs/openwhisk/openwhisk_goserverless.html){:new_window}도 제공합니다.
