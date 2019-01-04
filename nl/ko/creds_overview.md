---

copyright:
  years: 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 인증 정보 개요
{: #credentials_overview}

배치 환경에 서비스 인증 정보를 수동으로 추가하는 방법에 대해 알아봅니다.
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

일반적으로, 사용자는 애플리케이션이 실행되는 환경에서 애플리케이션 로직이 민감한 서비스 인증 정보(예: 데이터베이스 API 키 또는 비밀번호)를 가져오기를 원합니다. 이러한 방식으로, 사용자는 소스 코드 저장소에 인증 정보를 보관하지 않습니다. 지속적 통합, 사전 프로덕션 및 프로덕션 환경의 데이터베이스는 서로 간에 격리되어 있습니다. 

스타터 킷 템플리트를 사용하여 앱을 작성하는 경우에는 환경이 자동으로 준비됩니다. 배치 대상이 아래와 같은지 여부는 문제가 되지 않습니다. 
  * [Kubernetes](/docs/apps/creds_kube.html)
  * [Cloud Foundry](/docs/apps/creds_cf.html)
  * [가상 서버 인스턴스(또한 로컬 Docker)](/docs/apps/creds_vsi.html)
  
환경 구성 방법에 대한 단계가 제공됩니다. 스타터 킷은 배치 대상에서 실행될 수 있는 포터블 코드의 작성을 위해 종속자 라이브러리를 사용하는 코드를 생성합니다. 마지막으로, 분기 로직은 애플리케이션이 실행되는 배치 대상을 찾는 데 사용되지 않습니다. 

그리고 관리자나 DevOps 엔지니어는 애플리케이션이 자신에게 필요한 값을 사용할 수 있도록 적절한 액세스 제어와 구성으로 환경을 준비하는 역할을 담당합니다. 

"클라우드에 배치"는 다음의 주요 태스크를 수행하는 일회성 단계입니다. 
 * 서비스, 리소스 및 인증 정보로 대상 배치 환경을 준비합니다. 
 * 환경의 인증 정보를 올바르게 참조하는 코드를 사용하여 앱을 빌드하고 이를 해당 환경에 배치할 수 있도록 DevOps 도구 체인을 작성합니다. 

그러나 다음 시나리오에서는 대상 배치 환경을 준비해야 합니다. 
 * 자체 코드를 가져옵니다. 
 * 공백 스타터 킷 템플리트에서 시작합니다. 
 * 배치된 _이후_ 스타터 킷 기반 앱에 서비스를 추가합니다. 




