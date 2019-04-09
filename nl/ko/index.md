---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# {{site.data.keyword.Bluemix_notm}}에서 앱 작성
{: #create}

{{site.data.keyword.Bluemix}}에서 엔터프라이즈 레벨 모바일 및 웹 애플리케이션을 빌드하고 {{site.data.keyword.Bluemix_notm}}로 호스팅되는 클라우드 확장을 활용할 수 있습니다. {{site.data.keyword.Bluemix}} 콘솔 및 명령행 도구를 사용하여 앱을 빌드 및 실행하고 배치할 수 있습니다. 이 엔드 투 엔드 개발 시나리오에 따라 시작하십시오.

## 1단계: {{site.data.keyword.Bluemix_notm}} 계정 등록
{: #sign-up}

[bluemix.net](bluemix.net)으로 이동하십시오. 이메일, 이름, 회사, 지역, 전화번호만 입력하면 됩니다. 무료 계정을 등록하는 데 신용카드가 필요하지 않습니다. 편하게 둘러보십시오. 

## 2단계: 카탈로그 살펴보기
{: #catalog}

{{site.data.keyword.Bluemix_notm}} 카탈로그는 제공하는 인프라 및 플랫폼 리소스를 나열합니다. 가상 머신, 컨테이너 또는 Cloudant, Cloud Foundry 앱을 선택하여 앱 빌드를 시작할 수 있습니다. 플랫폼 리소스가 필요한 경우 {{site.data.keyword.Bluemix_notm}}는 런타임 및 기타 서비스를 제공하여 빌드 시작을 지원하는 표준 유형도 제공합니다. 

## 3단계: 리소스 작성
{: #resource}

1. [대시보드](https://console.bluemix.net/dashboard/apps/)에서 **리소스 작성**을 클릭하십시오.

2. 카탈로그의 플랫폼 섹션에서 앱을 선택하십시오. 그런 다음 런타임을 선택하십시오. 예를 들어, IBM 빌드팩에서 지원하는 IBM 런타임 환경(예: Liberty for Java)을 선택할 수 있습니다. 또한 오픈 소스 및 써드파티 빌드팩에 의존하는 커뮤니티 런타임(예: Tomcat)도 선택할 수 있습니다. 

  * [Containers 시작하기](../containers/container_index.html)
  * [Openwhisk 시작하기](../openwhisk/index.html)
  * [Cloud Foundry 앱 작성](../cfapps/index.html#creating_cloud_foundry_apps)

3. 앱 이름, 호스트 이름을 입력한 후 가격 책정 플랜을 선택하십시오. 

4. 개발 스타일을 선택하십시오. 원하는 텍스트 편집기에서 앱을 편집하고 {{site.data.keyword.Bluemix_notm}} 명령행을 사용하여 {{site.data.keyword.Bluemix_notm}}에 배치할 수 있습니다. 또한 {{site.data.keyword.Bluemix_notm}} DevOps Services를 사용하여 브라우저에서 애플리케이션을 배치하거나 Eclipse Tools for {{site.data.keyword.Bluemix_notm}}를 사용하여 Eclipse 통합 개발 환경에서 애플리케이션에 대해 작업할 수도 있습니다. 

## 4단계: 코드 추가 시작
{: #code}

각 앱은 작업 시작에 필요한 모든 소프트웨어 및 컨텐츠를 가져오는 데 도움이 되는 시작하기 섹션과 함께 제공합니다. 

앱을 개발하는 데 필요한 소프트웨어를 가져오고, 소스 코드를 가리키고, 처음으로 앱 배치 시 지원할 수 있도록 대시보드에서 앱을 클릭한 후 **시작하기**를 클릭하십시오.

## 다음 단계
{: #next}

앱이 개발되면 [우수 사례](best-practice.html) 및 [클라우드 준비성](cloud-ready.html) 안내서를 사용하여 앱이 {{site.data.keyword.Bluemix_notm}}를 실행할 준비가 되었는지 확인하십시오. 그런 다음 앱 [배치](../starters/install_cli.html)를 수행하십시오. 
