---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-30"

keywords: apps, code pattern, DevOps, toolchain, service credentials, create app code pattern, app pattern

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 코드 패턴으로 앱 작성
{: #tutorial-codepattern}

코드 패턴을 사용하여 애플리케이션을 신속히 작성하고 이를 {{site.data.keyword.cloud}}에 배치할 수 있습니다. GitHub에서 코드를 보거나 {{site.data.keyword.cloud_notm}}에서 앱 작성 및 빌드를 수행할 수 있으며, 여기서 DevOps 도구 체인을 사용하여 앱을 자동으로 배치할 수 있습니다.
{: shortdesc}

## 1단계. 앱 작성
{: #create-codepattern}

1. [IBM Developer ](https://developer.ibm.com/patterns/){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")로 이동하여 원하는 코드 패턴을 선택하십시오. 예를 들면, [Build a MEAN Web App ](https://developer.ibm.com/patterns/build-a-mean-web-app/){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘") 코드 패턴을 선택할 수 있습니다.

2. 코드 패턴에 대한 설명을 읽고, GitHub 저장소 및 `README.md` 파일을 보십시오. 저장소를 보려면 **코드 가져오기**를 클릭하십시오. 이렇게 하면 해당 코드 패턴의 GitHub 저장소가 열립니다.

3. 다음 선택사항 중 하나를 사용하여 앱 작성을 시작하십시오. 두 옵션은 모두 해당 코드 패턴에 대한 **앱 작성** 페이지를 엽니다.
    * 코드 패턴의 페이지에서, {{site.data.keyword.cloud_notm}}에서 앱을 빌드하는 링크를 클릭하십시오. 
    * GitHub 저장소의 `README.md` 파일에서, 스타터 킷을 사용하여 앱을 작성하는 링크를 클릭하십시오. 

4. **앱 작성** 페이지에서 앱의 이름을 지정하고, 리소스 그룹을 선택하고, 태그를 선택적으로 제공한 후 **작성**을 클릭하십시오. 태그에 대한 자세한 정보는 [태그에 대한 작업](/docs/resources?topic=resources-tag)을 참조하십시오.

  코드 패턴으로 돌아가려면 **코드 패턴 보기**를 클릭하십시오. 저장소에 있는 `README.md` 파일을 확인하여 앱을 시작하고 실행하기 위해 추가 조치를 수행해야 하는지 알아보십시오.
  {: tip}

## 2단계. 서비스 추가
{: #resources-codepattern}

Watson의 코그너티브 기능으로 앱을 향상시키는 서비스를 추가하거나 모바일 서비스 또는 보안 서비스를 추가할 수 있습니다. 이 프로세스는 서비스 인스턴스를 작성하고 리소스 키(인증 정보)를 작성하며 이를 앱에 바인드합니다. 이 튜토리얼의 경우 데이터를 관리할 위치를 추가하십시오.

1. **앱 세부사항** 페이지에서 **서비스 추가**를 클릭하십시오.
2. 원하는 서비스의 종류를 선택하십시오. 
3. 가격 플랜을 선택하십시오. Lite 옵션이 사용 가능합니다.
4. **작성**을 클릭하십시오.

## 3단계. 환경에 서비스 인증 정보 복사

앱에 서비스를 추가한 후 또는 서비스가 앱에 필요한 경우, 해당 서비스의 인증 정보가 **인증 정보** 상자에 표시되는 것을 볼 수 있습니다. 사용자는 해당 인증 정보를 배치 환경에 수동으로 복사해야 합니다.

환경에 인증 정보를 복사하는 데 대한 자세한 정보는 [인증 정보 개요](/docs/apps?topic=creating-apps-credentials_overview#credentials_overview)를 참조하십시오.

## 4단계. {{site.data.keyword.cloud_notm}}에 배치
{: #deploy-codepattern}

여러 가지 방법으로 앱을 {{site.data.keyword.cloud_notm}}에 배치할 수 있지만 프로덕션 앱을 배치하는 데 DevOps 도구 체인을 사용하는 것이 가장 좋은 방법입니다. DevOps 도구 체인을 사용하여 여러 환경으로의 배치를 손쉽게 자동화하고, 앱이 확장됨에 따라 이를 관리하는 데 도움을 주기 위해 신속하게 모니터링, 로깅 및 경보 서비스를 추가할 수 있습니다.

도구 체인을 사용으로 설정하면 앱에 대한 팀 기반 개발 환경을 작성할 수 있습니다. 도구 체인을 작성하는 경우 앱 서비스는 소스 코드를 보고, 앱을 복제하여 이슈를 작성하고 관리할 수 있는 Git 저장소를 작성합니다. 또한 전용 Git Lab 환경 및 지속적 Delivery Pipeline에 대한 액세스도 제공됩니다. 이는 사용자가 선택하는 배치 대상([Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 또는 [Virtual Server(VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers))에 맞게 사용자 정의됩니다.

1. **앱 세부사항** 페이지에서 **지속적 딜리버리 구성**을 클릭하십시오.
2. 배치 대상을 선택하고 **작성**을 클릭하십시오. {{site.data.keyword.cloud_notm}}가 Git 저장소와 지속적 Delivery Pipeline을 모두 갖춘 공개 도구 체인을 자동으로 작성합니다.
3. 새 도구 체인의 파이프라인 단계를 열어 빌드 및 배치 프로세스를 보고 나면 몇 분 내에 새 앱을 확인할 수 있습니다.

앱 배치에 관한 자세한 정보는 [앱 배치](/docs/apps?topic=creating-apps-deploying-apps)를 참조하십시오.

배치 대상, 빌드 및 파이프라인에 대한 자세한 정보는 [빌드 및 배치](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)를 참조하십시오.
