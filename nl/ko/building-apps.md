---

copyright:
  years: 2017, 2018
lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 사용자 정의 앱 빌드
{: #build-your-own}

스타터 킷을 사용하지 않으며 필요한 것을 알고 있는 경우에는 선택한 리소스를 사용하여 앱을 빌드할 수 있습니다.
{: shortdesc}

## 언어 선택
{: #catalog}

{{site.data.keyword.Bluemix_notm}} 카탈로그에는 사용 가능한 인프라 및 플랫폼 리소스가 나열되어 있습니다. 가상 머신, 컨테이너 또는 Cloudant, Cloud Foundry 앱을 선택하여 앱 빌드를 시작할 수 있습니다. 플랫폼 리소스가 필요한 경우 {{site.data.keyword.Bluemix_notm}}는 런타임 및 기타 서비스를 제공하여 빌드 시작을 지원하는 [표준 유형](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=blueprints)도 제공합니다.

## 리소스 작성
{: #resource}

1. [대시보드](https://console.bluemix.net/)에서 **리소스 작성**을 클릭하십시오.

2. 카탈로그의 플랫폼 섹션에서 앱을 선택하십시오. 그런 다음 런타임을 선택하십시오. 예를 들어, IBM 빌드팩에서 지원하는 IBM 런타임 환경(예: Liberty for Java)을 선택할 수 있습니다. 오픈 소스 및 써드파티 빌드팩에 의존하는 커뮤니티 런타임(예: Tomcat)을 선택할 수도 있습니다.

  * [Containers 시작하기](../containers/container_index.html)
  * [Openwhisk 시작하기](../openwhisk/index.html)
  * [Cloud Foundry 앱 작성](../cfapps/index.html#creating_cloud_foundry_apps)

3. 앱 이름, 호스트 이름을 입력한 후 가격 책정 플랜을 선택하십시오.

4. 개발 스타일을 선택하십시오. 원하는 텍스트 편집기에서 앱을 편집하고 {{site.data.keyword.Bluemix_notm}} 명령행을 사용하여 {{site.data.keyword.Bluemix_notm}}에 배치할 수 있습니다. 또한 {{site.data.keyword.Bluemix_notm}} DevOps Services를 사용하여 브라우저에서 애플리케이션을 배치하거나 Eclipse Tools for {{site.data.keyword.Bluemix_notm}}를 사용하여 Eclipse 통합 개발 환경에서 애플리케이션에 대해 작업할 수도 있습니다.

## 코드 추가
{: #code}

각 앱은 작업 시작에 필요한 모든 소프트웨어 및 컨텐츠를 가져오는 데 도움이 되는 시작하기 섹션과 함께 제공합니다.

앱을 개발하는 데 필요한 소프트웨어를 가져오고, 소스 코드를 가리키고, 처음으로 앱 배치 시 지원할 수 있도록 대시보드에서 앱을 클릭한 후 **시작하기**를 클릭하십시오.

## 다음 단계
{: #next}

필요에 맞게 앱을 계속해서 사용자 정의하십시오. 비즈니스 결과를 달성하기 위해 앱을 확장하는 데 대한 다음 권장사항을 확인하십시오.

* [우수 사례](best-practice.html) 안내서에 간략히 설명된 [보안](https://console.bluemix.net/catalog/?taxonomyNavigation=data&category=security){:new_window}, [모니터링](https://console.bluemix.net/catalog/?category=devops){:new_window} 및 가용성 개선사항을 추가하여 앱의 안정성을 높이십시오.
* [Watson 코그너티브 서비스](https://console.bluemix.net/catalog/?taxonomyNavigation=data&category=watson){:new_window}와 [고급 분석 및 기계 학습](https://console.bluemix.net/catalog/?taxonomyNavigation=data&category=data){:new_window}을 통해 앱의 자율성을 높이십시오.
* [모바일](https://console.bluemix.net/catalog/?category=mobile){:new_window}에서 사용할 수 있도록 앱을 사용자 정의하십시오.
* [Internet of Things](https://console.bluemix.net/catalog/?category=iot){:new_window}를 사용해 보십시오.
* [API Connect](https://console.bluemix.net/catalog/?category=integration){:new_window}와 같은 서비스를 사용하여 [서버리스 조치](https://console.bluemix.net/catalog/?category=whisk){:new_window}를 통합하십시오.

