---

copyright:
  years: 2017, 2019
lastupdated: "2019-05-10"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 호스팅 환경 선택
{: #hosting}

기존 앱이 있는 경우 필요한 모든 인프라 또는 플랫폼 서비스를 사용하여 {{site.data.keyword.cloud}}에 기존 앱을 호스팅할 수 있습니다.
{:shortdesc}

{{site.data.keyword.Bluemix_notm}}를 사용하면 더 이상 하드웨어에 막대한 금액을 투자하여 새로운 앱을 테스트하거나 실행할 필요가 없습니다. 대신 IBM에서 모든 것을 관리하며 실제 사용량에 대한 금액만 청구합니다. 클라우드 서버 환경은 인프라 계층의 기반입니다. 단일 옵션을 선택하거나 더 복잡한 환경의 경우 옵션의 조합을 선택할 수 있습니다. 

원하거나 필요한 만큼 인프라에 대한 제어를 제공하여 앱을 호스팅하기 위한 다양한 옵션이 있습니다. 다음 방법 중 하나로 앱을 실행할 수 있습니다.

  * Kubernetes 클러스터의 Docker 컨테이너로
  * Cloud Foundry 앱으로
  * 서버리스 기능으로
  * VMware로
  * 가상 머신으로
  * 고성능 {{site.data.keyword.baremetal_short}}로 

컴퓨팅 옵션에 대한 요약은 다음 표를 확인하십시오.

|옵션 |설명 | 
|--------|---------------|
| [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started) |Docker 컨테이너, Kubernetes 기술, 직관적인 사용자 경험, 기본 제공 보안 및 격리를 결합하여 컴퓨팅 호스트의 클러스터에서 컨테이너화된 앱의 배치, 오퍼레이션, 스케일링 및 모니터링을 자동화합니다. |
| [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) |격리된 여러 엔터프라이즈급 Cloud Foundry 플랫폼을 요청 시 인스턴스화합니다. |
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-getting_started) |Apache OpenWhisk 기반의 FaaS(Function-as-a-Service) 프로그래밍 플랫폼입니다. |
| [{{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started) |확장 가능하고 안전한 고성능 인프라 및 업계 최고의 VMware 하이브리드 가상화 기술을 사용하여 온프레미스 VMware 워크로드를 빠르고 원활하게 통합하거나 마이그레이션합니다. |
| [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-public-virtual-servers) |전용 코어와 메모리 할당을 포함하여 구매하는 확장 가능한 서버입니다. |
| [{{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-about-bm)  |사용자 전용이며 서버 리소스를 포함한 모든 파트에서 다른 고객과 공유되지 않는 시간별 또는 월별 싱글 테넌트 서버입니다. |
{: caption="표 1. 컴퓨팅 옵션" caption-side="top"}

