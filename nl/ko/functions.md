---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-29"

keywords: apps, serverless, serverless app, functions, cli, api, sdk, create serverless app, serverless app tutorial

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 서버리스 앱 작성
{: #serverless}

서버리스 개발을 위해 IBM FaaS(Functions-as-a-Service) 오퍼링인 {{site.data.keyword.openwhisk}}를 사용할 수 있습니다. 서버의 프로비저닝 또는 관리 없이 HTTP를 통해 웹이나 모바일 앱에서의 직접 호출 또는 이벤트에 대한 응답으로 {{site.data.keyword.openwhisk_short}}에서 애플리케이션 로직을 실행할 수 있습니다. {{site.data.keyword.openwhisk_short}}는 개발자인 사용자가 앱 로직 작성에 집중할 수 있도록 Auto-Scaling, 가용성 관리 및 유지보수 등의 시스템 관리를 수행합니다.
{:shortdesc}

다음 방법 중 하나를 사용하여 서버리스 앱을 개발할 수 있습니다.
* {{site.data.keyword.openwhisk_short}} 사용자 인터페이스(UI).
* 배치와 조작에 대한 추가 제어를 제공하는 {{site.data.keyword.openwhisk_short}} 명령행 인터페이스(CLI).
* DevOps 도구 체인 및 Delivery Pipeline을 사용하여 지속적 딜리버리를 구성할 수 있는 {{site.data.keyword.openwhisk_short}} 스타터 킷.

{{site.data.keyword.openwhisk_short}}에 대한 자세한 정보는 [문서](/docs/openwhisk?topic=cloud-functions-getting_started)를 참조하십시오.


## {{site.data.keyword.openwhisk_short}} UI로 개발
{: #serverless-apps-ui}

[브라우저 ](https://{DomainName}/functions/actions){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")에서 {{site.data.keyword.openwhisk_short}}를 시도해 보십시오. {{site.data.keyword.openwhisk_short}} 사용자 인터페이스의 빠른 둘러보기를 위해 [개념 ](https://{DomainName}/functions/learn){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘") 페이지로 이동하십시오.

## CLI로 개발
{: #openwhisk_start_configure_cli}

{{site.data.keyword.openwhisk_short}}  CLI를 사용한 설치와 개발에 대해 자세히 알아보려면 [{{site.data.keyword.openwhisk_short}} CLI 설정](https://{DomainName}/functions/cli){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")을 참조하십시오.

## 웹 액션으로 API 및 데이터 세트 노출
{: #expose-actions}

기본적으로 {{site.data.keyword.openwhisk_short}}는 인증 키가 필요한 액션을 정의합니다. 프로덕션 모바일 환경에서는 종종 OAuth 플로우 기반의 모바일 클라이언트에 권한을 부여하여 API 및 특정 데이터 세트를 노출해야 합니다.

{{site.data.keyword.openwhisk_short}}를 통해 개발자는 신속하게 웹 기반 앱을 빌드하도록 어노테이션된 웹 액션으로 기능을 노출할 수 있습니다. {{site.data.keyword.openwhisk_short}} 인증 키 없이도 웹 앱이 익명으로 액세스할 수 있는 어노테이션된 액션으로 백엔드 로직을 프로그래밍할 수 있습니다.

웹 액션으로 액션을 노출하려면 액션의 **엔드포인트** 탭으로 이동하여 **웹 액션으로 사용**을 선택하십시오.

이제 사용자는 브라우저 또는 cURL 요청의 액션에 도달할 수 있습니다. 예를 들면, 다음과 같습니다.
```
curl https://openwhisk.cloud.ibm.com/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

출력:
```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}}는 iOS 및 watchOS 디바이스를 위한 [모바일 SDK](/docs/openwhisk?topic=cloud-functions-pkg_mobile_sdk)를 제공하여 모바일 앱이 쉽게 원격 트리거를 전송하고 원격 액션을 호출할 수 있도록 합니다.

## 스타터 킷을 사용한 서버리스 앱 작성
{: #serverless-starter}

스타터 킷을 사용하여 서버리스 앱(예: Python Example Serverless App)을 작성할 수 있습니다. 스타터 킷을 찾으려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.dev_console}} 콘솔에서 [앱 서비스 스타터 킷 ](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘") 페이지로 이동하십시오.
2. 검색 표시줄에서 `serverless`를 입력하여 스타터 킷의 목록을 필터링하십시오.
3. 서버리스 스타터 킷(예: Python Example Serverless App)을 선택하십시오.
4. 앱을 이름을 지정하고 리소스 그룹을 선택하십시오.
5. 선택사항. 앱을 분류하기 위한 태그를 제공하십시오. 자세한 정보는 [태그에 대한 작업](/docs/resources?topic=resources-tag)을 참조하십시오.
6. Cloudant 서비스 인스턴스를 작성하거나 기존 Cloudant 서비스 인스턴스를 선택하십시오.
7. 선택사항. 서비스를 더 추가하거나 앱을 배치하기 전에 코드를 검사하려면 **소스 코드 보기**를 클릭하십시오. `README.md` 파일을 검사하여 앱을 시작하고 실행하기 위한 추가 조치가 필요한지 여부를 알아보십시오.
8. **작성**을 클릭하십시오.

시작이 좋습니다! 앱이 작성되었습니다!

## 서비스 추가(선택사항)
{: #serverless-services}

스타터 킷에 특정 리소스가 필요한 경우 자동 프로비저닝된 서비스를 사용할 수 있습니다. 그러면 인스턴스가 앱을 작성할 때 해당 서비스에 대한 인스턴스가 자동으로 작성됩니다.

1. 앱 세부사항 페이지에서 이 앱에 연결하려는 서비스가 이미 있는지 여부에 따라 **서비스 작성** 또는 **기존 서비스 연결**을 클릭하십시오.
2. 원하는 서비스의 종류를 선택한 후 프롬프트에 따라 기존 서비스를 앱에 추가하거나 서비스 인스턴스를 작성하십시오.

원하는 서비스가 모두 추가되면 해당 서비스가 앱 세부사항 페이지에 표시됩니다.

## 앱 배치
{: #serverless-deploy}

앱을 배치하려면 다음 단계를 완료하십시오.

1. 앱 세부사항 페이지에서 **배치**를 클릭하십시오.
2. **Cloud Functions에 배치**를 선택하고 **다음**을 클릭하십시오.
3. 도구 체인 구성 페이지에서 도구 체인 이름을 입력하고 지역을 선택한 후 **작성**을 클릭하십시오. 배치 대상을 선택하고 구성하면 앱 세부사항 페이지에 지속적 딜리버리가 구성되었음이 표시됩니다.
4. 선택사항. 조치 아이콘 ![추가 조치 아이콘](../icons/action-menu-icon.svg)을 클릭하고 **Cloud Functions 열기**를 선택하여 {{site.data.keyword.openwhisk_short}} 콘솔에서 조치를 검토하십시오.
5. 선택사항. **저장소 보기**를 클릭하여 앱과 서비스에 대해 생성된 코드가 포함된 저장소를 보십시오.

## 앱 배치 확인
{: #serverless-verify}

도구 체인이 적절히 구성되면 저장소의 마스터 분기에 대한 각 병합마다 빌드-배치 주기가 자동으로 시작됩니다. 자세한 정보는 [빌드 및 배치](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)를 참조하십시오.

앱 배치에 성공했는지 확인하려면 다음 단계를 완료하십시오.

1. 앱 세부사항 페이지에서 **도구 체인 보기**를 클릭하십시오.
2. 빌드를 시작하고 배치를 관리하며 로그 및 히스토리를 볼 수 있는 **Delivery Pipeline**을 클릭하십시오.
3. 배치에 성공하면 각 파이프라인 단계에서 **단계 패스**를 표시합니다.
4. 조치 및 API 정보를 보려면 **배치 단계** 타일에서 **로그 및 히스토리 보기**를 클릭하십시오.
