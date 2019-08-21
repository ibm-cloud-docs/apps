---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-20"

keywords: getting started apps, create app tutorial, add services, deploy apps, create app, app tutorial

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 시작하기 튜토리얼
{: #getting-started}

{{site.data.keyword.cloud}}에서 엔터프라이즈 레벨 모바일 및 웹 애플리케이션을 빌드하고 {{site.data.keyword.cloud_notm}}에서 호스팅하는 클라우드 확장을 활용할 수 있습니다. 시작하는 데 대해서는 몇 가지 선택사항이 있습니다. 사용자 대신 프로세스를 관리하는 스타터 킷을 사용하여 앱을 작성할 수 있으며, 필요한 것이 무엇인지 아는 경우에는 처음부터 시작하여 필요한 리소스로 앱을 빌드하거나 기존 저장소를 사용하며 자체 코드를 여기로 가져올 수 있습니다.
{: shortdesc}

현대화하여 클라우드로 가져오려는 [기존 코드](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc)가 있거나 [새로운 애플리케이션](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit)을 개발 중인지에 관계없이 사용자는 {{site.data.keyword.cloud_notm}}에서 사용 가능한 서비스 및 런타임 프레임워크의 빠르게 성장하는 에코시스템을 활용할 수 있습니다.

어디서 시작할지 결정하는 데 도움이 필요합니까? 다음 다이어그램은 스타터 킷을 사용하거나 사용자 고유 코드를 {{site.data.keyword.cloud_notm}}로 가져오는지 여부에 상관없이 앱을 작성하는 데 필요한 개요를 제공합니다.

![개발자 경험 개요](images/dev-journey.png "{{site.data.keyword.cloud_notm}}에서 앱 작성 개요")

## 시작하기 전에
{: #prereqs-getting-started}

{{site.data.keyword.cloud_notm}} 콘솔 또는 명령행 인터페이스(CLI)를 사용하여 앱을 작성할 수 있습니다. CLI를 사용하려면 [설치 단계](/docs/cli?topic=cloud-cli-getting-started)를 참조하십시오.

## 1단계. 앱 작성
{: #create-getting-started}

다음 시작점 중 하나를 선택하여 앱을 작성하십시오.

* [사전 구성된 스타터 킷](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit)은 유스 케이스에 특정하며 다양한 프로그래밍 언어와 아키텍처 패턴으로 프로덕션에 사용할 준비가 된 앱을 제공합니다.
* [기본 스타터 킷](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch)을 사용하면 앱 유형(모바일 또는 백엔드), 언어와 프레임워크, 서비스 및 배치 대상을 선택하여 앱을 빌드할 수 있습니다.
* 기존 컨텐츠 저장소에 링크하여 [자체 코드를 가져오십시오](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc). 앱 및 Docker 이미지는 동일한 저장소에 있어야 합니다.
* [{{site.data.keyword.dev_cli_long}} 명령행 인터페이스(CLI)](/docs/apps?topic=creating-apps-create-deploy-app-cli)를 사용하면 CLI를 사용하여 앱을 작성하고 배치할 수 있습니다.
* 작성 가능한 앱 및 서비스에 대한 [{{site.data.keyword.cloud_notm}} 카탈로그 ](https://{DomainName}/catalog){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")를 찾아보거나 검색한 후에 당장 사용을 시작합니다.
* [IBM Developer 코드 패턴 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://developer.ibm.com/patterns/){:new_window}을 사용하여 앱을 신속하게 작성하고 이를 {{site.data.keyword.cloud_notm}}에 배치합니다. 자세한 정보는 [코드 패턴](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern)을 참조하십시오.

## 2단계. 서비스 추가
{: #resources-getting-started}

스타터 킷을 사용하여 앱을 작성하는 경우에는 필수 서비스가 자동으로 작성됩니다. 앱을 작성하는 즉시 표시되는 **앱 세부사항** 페이지에서 콘솔의 앱에 추가 서비스를 연결할 수 있습니다.

앱이 작성된 후에 서비스를 추가하려면 [{{site.data.keyword.cloud_notm}} 대시보드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName})로 이동하고 앱을 찾은 다음 앱의 이름을 클릭하십시오. **앱 세부사항** 페이지가 표시되면 서비스 인스턴스를 작성하거나 기존 서비스에 연결할 수 있습니다.

또는 CLI를 사용하여 앱에 서비스를 추가하려면 다음 명령을 실행할 수 있습니다. 계정에서 이미 사용되고 있는 기존 서비스 중 하나를 선택하거나 서비스를 추가할 수 있습니다.
```
ibmcloud dev edit
```
{: codeblock}

자세한 정보는 [앱에 서비스 추가](/docs/apps?topic=creating-apps-add-resource)를 참조하십시오.

## 3단계. 앱 배치
{: #deploy-getting-started}

콘솔 또는 CLI를 사용하여 앱을 배치할 수 있습니다.

### 콘솔 사용
{: #console-getting-started}

콘솔을 사용하여 앱을 배치하려면 다음 단계를 완료하십시오.

1. **앱 세부사항** 페이지에서 **지속적 딜리버리 구성**을 클릭하십시오.
2. 배치 대상을 선택하고 도구 체인 설정을 선택한 후 **작성**을 클릭하십시오. {{site.data.keyword.cloud_notm}}가 Git 저장소와 지속적 Delivery Pipeline을 모두 갖춘 공개 도구 체인을 자동으로 작성합니다.
3. 새 도구 체인의 파이프라인 단계를 열어 빌드 및 배치 프로세스를 보고 나면 몇 분 내에 새 앱을 확인할 수 있습니다.

자세한 정보는 [앱 배치](/docs/apps?topic=creating-apps-deploying-apps)를 참조하십시오.

### CLI 사용
{: #cli-getting-started}

CLI를 사용하여 앱을 배치하려면 `ibmcloud dev deploy` 명령을 실행하십시오. 자세한 정보는 [CLI를 사용하여 앱 작성 및 배치](/docs/apps?topic=creating-apps-create-deploy-app-cli)를 참조하십시오.

이제 반복 배치 및 지속적 딜리버리를 수행할 준비가 되었습니다.

앱 배치에 관한 자세한 정보는 [앱 배치](/docs/apps?topic=creating-apps-deploying-apps)를 참조하십시오.

## 관련 정보
{: #related-getting-started}

시작하고 실행하는 데 도움이 되도록 언어별 [프로그래밍 안내서](https://{DomainName}/docs/home/build){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")가 제공됩니다. {{site.data.keyword.baremetal_short}}에서 서버리스 기능으로 실행하는 경우에 이르기까지 {{site.data.keyword.cloud_notm}} 인프라를 사용하여 앱을 호스팅하는 여러 옵션이 있습니다.
