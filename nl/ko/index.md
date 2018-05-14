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

# 시작하기 튜토리얼
{: #create}

{{site.data.keyword.Bluemix}}에서 엔터프라이즈 레벨 모바일 및 웹 애플리케이션을 빌드하고 {{site.data.keyword.Bluemix_notm}}로 호스팅되는 클라우드 확장을 활용할 수 있습니다. {{site.data.keyword.Bluemix}} 콘솔 및 명령행 도구를 사용하여 앱을 빌드 및 실행하고 배치할 수 있습니다. 시작하는 방법에는 사용자 대신 프로세스를 관리하는 스타터 킷을 사용하여 프로젝트를 작성하는 것, 또는 원하는 것이 무엇인지 아는 경우 필요한 리소스로 앱을 빌드하는 것의 두 가지 방법이 있습니다.
{:shortdesc}

스타터 킷을 사용하여 앱을 사용 가능하도록 신속히 작성하고 이후의 개발을 위해 준비할 수 있습니다. 스타터 킷 및 프로그래밍 언어를 선택하고, 프로젝트를 작성한 후 즉각적 검토를 위해 코드를 다운로드하십시오. 앱을 신속히 배치하기 위해 DevOps 도구 체인을 작성할 수도 있습니다.

스타터 킷은 다음 항목을 포함한 다양한 카테고리에서 사용 가능합니다.

* [Watson](https://console.bluemix.net/developer/watson){:new_window}
* [Apple](https://console.bluemix.net/developer/appledevelopment){:new_window}
* [모바일](https://console.bluemix.net/developer/mobile){:new_window}
* [웹 앱](https://console.bluemix.net/developer/appservice){:new_window}
* [보안](https://console.bluemix.net/developer/security){:new_window}
<!--* [Watson Data Platform developer console](https://console.bluemix.net/developer/dataplatform)-->
* [금융](https://console.bluemix.net/developer/finance){:new_window}

## 시작하기 전에

{{site.data.keyword.cloud_notm}} 계정에 [등록](https://console.bluemix.net){: new_window}하십시오. 이메일, 이름, 회사, 지역 및 전화번호를 입력하십시오.

무료 계정을 등록하는 데는 신용카드가 필요하지 않지만, 신용카드 정보를 입력하면 더 많은 리소스에 액세스할 수 있으며 {{site.data.keyword.cloud_notm}}에서 제공하는 모든 항목을 더 쉽게 알아볼 수 있습니다.

## 1단계: 프로젝트 작성
{: #project}

1. **메뉴** 아이콘 ![메뉴 아이콘](../icons/icon_hamburger.svg) > **웹 앱**을 클릭하십시오.

2. **웹에서 시작** 섹션에서 **시작하기**를 클릭하십시오.

3. 원하는 스타터 킷을 선택하고, 세부사항을 읽은 후 **프로젝트 작성**을 클릭하십시오.

  스타터 킷에 무엇이 포함되어 있는지 보려면 앱 서비스 스타터 킷 대시보드에서 타일을 펼치십시오.
  {: tip}

4. 프로젝트 이름을 지정하고, 언어를 선택한 후 **프로젝트 작성**을 클릭하십시오.

시작이 좋습니다! 앱이 작성되었습니다.

코드를 검토하려면 프로젝트 세부사항 페이지에서 **코드 다운로드**를 클릭하십시오. 다운로드된 압축 파일에 있는 `README.md` 파일을 확인하여 스타터 앱을 실행하기 위해 추가 조치를 수행해야 하는지 알아보십시오.
{: tip}

## 2단계: 리소스 추가
{: #addResources}

대부분의 스타터 킷은 사용자를 위해 리소스를 자동으로 프로비저닝하도록 {{site.data.keyword.cloud_notm}}에 지시합니다. 프로젝트 세부사항 페이지에서 **리소스 추가**를 클릭하여 더 많은 리소스를 앱과 연관시킬 수도 있습니다.

앱을 로컬로 개발하고 실행하려는 경우에는 [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html)을 사용하십시오.
{: tip}

## 3단계: {{site.data.keyword.cloud_notm}}에 배치
{: #deploy}

프로젝트 세부사항 페이지의 **클라우드에 배치**를 클릭하고, 배치 방법(예: Kubernetes 클러스터 또는 Cloud Foundry 앱)을 선택한 후 **작성**을 클릭하십시오. {{site.data.keyword.cloud_notm}}가 Git 저장소와 지속적 Delivery Pipeline을 모두 갖춘 공개 도구 체인을 자동으로 작성합니다. 새 도구 체인의 파이프라인 컴포넌트를 확인하고 첫 빌드 및 배치 프로세스를 시작하고 나면 몇 분 내에 새 앱이 실행되는 것을 볼 수 있습니다.

이제 반복 배치 및 지속적 딜리버리를 수행할 준비가 되었습니다.
