---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-14"

keywords: cloud development, develop apps, build apps, continuous delivery, toolchain

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# 권장하는 클라우드 개발 단계
{: #development_process}

클라우드 앱 개발자는 개발 프로세스에서 시작하기, 코딩, 전달 및 관리의 네 가지 기본 단계를 거칩니다. 목표는 작동하는 앱을 빠르게 작성한 후 사용자가 앱에 대해 만족할 때까지 프로덕션 앱의 피드백을 사용하여 지속적으로 코딩 또는 전달 주기를 반복하는 것입니다.
{: shortdesc}

![개발 플로우](images/dev_flow_overview.png "개발 플로우") 그림 1. 개발 프로세스의 단계

일부 경우에는 `실행`이 별도의 단계로 구분되기도 하지만 여기서는 전달 및 관리 단계에 포함되었습니다.

개발 플로우에서 {{site.data.keyword.cloud}}를 사용하는 최선의 방법에 대해 자세히 알아보겠습니다.

## 시작하기
{: #get_started}

유스 케이스와 관련된 스타터 킷을 선택하고 프로그래밍 언어를 선택할 수 있는 {{site.data.keyword.cloud_notm}} 개발자 대시보드에서 앱을 빌드하십시오. {{site.data.keyword.cloud_notm}}에서는 스타터 킷의 지시사항을 사용하여 사용자에게 필요한 리소스를 자동으로 작성하고 프로덕션 앱의 기반이 되는, 런타임을 가리지 않으며 특정 언어에 고유한 앱을 작성합니다. 시작하기 단계를 완료하려면 개발자 대시보드에서 **클라우드에 배치**를 클릭하십시오. 한 번의 클릭으로 앱 소스 코드 및 개발 파이프라인으로 채워진 코드 저장소를 갖춘 DevOps 도구 체인이 작성됩니다.

![시작하기](images/dev_get_started.png "시작하기") 그림 2. 시작하기 플로우

**클라우드에 배치** 단추를 사용하여 DevOps 도구 체인을 설정할 때는 Kubernetes 또는 Cloud Foundry와 같은 런타임 플랫폼을 선택하십시오. {{site.data.keyword.cloud_notm}}로부터 작성된 스타터 킷 앱은 런타임을 가리지 않으며 수정할 필요가 없습니다.
{: tip}

## 로컬로 개발
{: #develop_locally}

스타터 킷 앱 및 도구 체인을 작성한 후에는 로컬로 개발을 시작합니다. 저장소에서 코드를 로컬 워크스테이션에 복제한 후 IDE로 가져오십시오. {{site.data.keyword.dev_cli_long}}을 사용하여 로컬 시스템에서 클라우드 앱을 빌드하고, 실행하고 테스트하십시오. {{site.data.keyword.dev_cli_notm}}은 사용자를 위해 로컬 컨테이너를 작성하고 관리합니다. 클라우드에서 앱이 실행되고 있는 것을 확인할 준비가 되면 클라우드 저장소에 푸시하고 변경사항을 병합하십시오.

![로컬로 개발](images/dev_code_locally.png "로컬로 개발") 그림 3. 로컬로 개발 플로우

{{site.data.keyword.dev_cli_notm}}의 기본 기능은 `ibmcloud dev build` 및 `ibmcloud dev run`이지만 이 CLI는 그 외에도 더 많은 기능을 제공합니다. 세부사항은 [{{site.data.keyword.dev_cli_notm}}](/docs/cli/index.html)의 내용을 참조하십시오.
{: tip}

## {{site.data.keyword.cloud_notm}}에서의 전달 및 관리
{: #deliver_and_manage}

변경사항을 클라우드 저장소에 병합하면 이전에 작성한 DevOps 도구 체인에서의 빌드 및 개발 주기가 시작됩니다. 몇 분이 지나면 앱이 클라우드에서 실행됩니다.

DevOps 파이프라인의 상태를 확인하려면 Delivery Pipeline 대시보드를 사용하십시오. 앱의 전체 상태를 확인하려면 사용자 계정의 {{site.data.keyword.cloud_notm}} 대시보드를 보십시오.
{: tip}

시작하기 플로우에서 작성된 도구 체인에는 협업을 통한 팀 기반의 지속적 딜리버리를 위해 필요한 기본 컴포넌트가 있습니다. 또한 {{site.data.keyword.cloud_notm}}에서는 전달, 모니터링, 로깅 및 경보 기능을 강화하기 위해 도구 체인에 추가할 수 있는 다양한 DevOps 서비스 세트를 제공합니다.

![전달 및 관리](images/dev_deliver_and_manage.png "전달 및 관리") 그림 4. 전달 및 관리 플로우

[{{site.data.keyword.cloud_notm}}에서의 지속적 개발](/docs/services/ContinuousDelivery/index.html#cd_getting_started)에 대해 자세히 알아보십시오.

## 통합

![프로세스 세부사항](images/dev_process_detail.png "프로세스 세부사항") 그림 5. 엔드-투-엔드 개발 프로세스
