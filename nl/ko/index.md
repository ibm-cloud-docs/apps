---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, create apps, add resources, deploy apps

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 시작하기 튜토리얼
{: #tutorial-getting-started}

{{site.data.keyword.cloud}}에서 엔터프라이즈 레벨 모바일 및 웹 애플리케이션을 빌드하고 {{site.data.keyword.cloud_notm}}에서 호스팅하는 클라우드 확장을 활용할 수 있습니다. 시작하는 데 대해서는 몇 가지 선택사항이 있습니다. 사용자 대신 프로세스를 관리하는 스타터 킷을 사용하여 앱을 작성할 수 있으며, 필요한 것이 무엇인지 아는 경우에는 처음부터 시작하여 필요한 리소스로 앱을 빌드하거나 기존 저장소를 사용하며 자신의 코드를 여기로 가져올 수 있습니다.
{: shortdesc}

## 시작하기 전에
{: #prereqs-getting-started}

{{site.data.keyword.cloud_notm}} 콘솔 또는 명령행 인터페이스(CLI)를 사용하여 앱을 작성할 수 있습니다. CLI를 사용하려면 [설치 단계](/docs/cli?topic=cloud-cli-ibmcloud-cli)를 참조하십시오.

## 1단계. 앱 작성
{: #create-getting-started}

다음 시작점 중 하나를 선택하여 앱을 작성하십시오.
* [스타터 킷](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit): 사용자 대신 프로세스를 관리하는 앱 서비스 스타터 킷을 선택하여 앱을 작성하십시오.
* [사용자 정의](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch): 필요한 것이 무엇인지 아는 경우에는 비어 있는 스타터 킷을 사용하여 필요한 리소스로 사용자 정의 앱을 처음부터 빌드하십시오.
* [자신의 코드 가져오기](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc): 기존 컨텐츠 저장소를 링크하여 자신의 코드를 가져오십시오. 앱 및 Docker 이미지는 동일한 저장소에 있어야 합니다.
* [CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli): CLI 및 개발자 도구를 사용하여 사용자 정의 앱 또는 스타터 킷 앱을 작성하고 배치하십시오.
* [코드 패턴](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern): IBM Developer 코드 패턴을 앱 작성의 기초로 사용하십시오.
* [{{site.data.keyword.cloud_notm}} 카탈로그 ](https://cloud.ibm.com/catalog){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘"): 카탈로그에서 바로 작성하여 사용하기 시작할 수 있는 앱 및 서비스를 찾아보거나 검색할 수 있습니다.

## 2단계. 리소스 추가
{: #resources-getting-started}

앱을 작성하는 데 스타터 킷을 사용하는 경우에는 서비스가 자동으로 작성됩니다. 콘솔의 **앱 세부사항** 페이지에서 **서비스 추가**를 클릭하여 추가 서비스를 앱과 연관시킬 수 있습니다.

CLI를 사용하여 서비스를 추가하려면 다음 명령을 실행하여 서비스를 앱에 추가하십시오. 계정에서 이미 사용되고 있는 기존 서비스 중 하나를 선택하거나 새 서비스를 추가할 수 있습니다. 
```
ibmcloud dev edit
```
{: codeblock}

자세한 정보는 [앱에 서비스 추가](/docs/apps?topic=creating-apps-add-resource)를 참조하십시오.

## 3단계. 앱 배치
{: #deploy-getting-started}

콘솔 또는 명령행 인터페이스를 사용하여 앱을 배치할 수 있습니다.

### 콘솔 사용
{: #console-getting-started}

콘솔을 사용하여 앱을 배치하려면 다음 단계를 완료하십시오.

1. **앱 세부사항** 페이지에서 **지속적 딜리버리 구성**을 클릭하십시오.
2. 배치 대상을 선택하고 도구 체인 설정을 선택한 후 **작성**을 클릭하십시오. {{site.data.keyword.cloud_notm}}가 Git 저장소와 지속적 Delivery Pipeline을 모두 갖춘 공개 도구 체인을 자동으로 작성합니다.
3. 새 도구 체인의 파이프라인 단계를 열어 빌드 및 배치 프로세스를 보고 나면 몇 분 내에 새 앱을 확인할 수 있습니다.

자세한 정보는 "앱 배치 및 통합" 절에 있는 다양한 배치 주제에 대한 목차를 참조하십시오.

### 명령행 사용
{: #cli-getting-started}

명령행을 사용하여 앱을 배치하려면 `ibmcloud dev deploy` 명령을 사용하십시오. 자세한 정보는 [CLI를 사용하여 앱 작성 및 배치](/docs/apps?topic=creating-apps-create-deploy-app-cli)를 참조하십시오.

이제 반복 배치 및 지속적 딜리버리를 수행할 준비가 되었습니다.
