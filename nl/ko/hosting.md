---

copyright:
  years: 2017, 2018
lastupdated: "2017-01-26"

---

{:shortdesc: .shortdesc}

# 앱 호스팅
{: #hosting}

기존 앱이 있는 경우 필요한 모든 인프라 또는 플랫폼 서비스를 사용하여 IBM Cloud에 기존 앱을 호스팅할 수 있습니다. 기존 앱의 경우에는 {{site.data.keyword.Bluemix_notm}} 인프라를 활용하여 {{site.data.keyword.Bluemix_notm}}용으로 별도 개발된 앱을 호스팅할 수 있습니다.
{:shortdesc}

## 앱 마이그레이션
{: #ht_hostapp}

기존 앱의 경우에는 앱을 클라우드 환경으로 완전히 이동하는 대신에 점진적으로 앱을 {{site.data.keyword.Bluemix_notm}}에 마이그레이션할 수 있습니다. 우선 앱의 일부를 마이그레이션한 후에 클라우드 통합 서비스를 사용하여 기존 데이터 또는 SOR(System of Record)에 연결할 수 있습니다.

{{site.data.keyword.Bluemix_notm}} 앱의 경우 백엔드 데이터 또는 서비스에 액세스해야 할 수 있습니다(예: SOR(System of Record)). {{site.data.keyword.Bluemix_notm}}에서 Secure Gateway 서비스를 사용하여 {{site.data.keyword.Bluemix_notm}} 조직 및 엔터프라이즈 백엔드 네트워크 간의 보안 터널을 설정할 수 있습니다. 서비스를 사용하면 {{site.data.keyword.Bluemix_notm}}의 앱이 백엔드 네트워크의 데이터 및 서비스에 액세스할 수 있습니다. 세부사항은 [Reaching enterprise backend with Bluemix Secure Gateway via console ![외부 링크 아이콘](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}을 참조하십시오.

{{site.data.keyword.Bluemix_notm}}는 기존 앱을 호스팅하고 필요한 모든 인프라를 제공할 수 있습니다. [카탈로그](https://console.bluemix.net/catalog/?taxonomyNavigation=apps)에서, 베어메탈 서버 또는 가상 서버에서 앱을 호스팅하는지 여부를 선택할 수 있습니다. 고성능을 위해 전용 실제 서버가 필요한 경우에는 [베어메탈](../bare-metal/index.html#about-bare-metal-servers) 배치가 최상입니다. 지리적 지역 간에 워크로드가 분산되어 있으며 {{site.data.keyword.Bluemix_notm}} 하이퍼바이저를 사용하여 배치를 관리하려는 경우에는 [가상](/vsi/vsi_index.html#provisioning-a-virtual-server) 배치가 최상입니다. 

한 번에 모두 또는 컴포넌트별로 앱의 파트를 {{site.data.keyword.Bluemix_notm}}에 마이그레이션할 수 있습니다. 앱을 마이그레이션할 때 IBM에서 제공하는 일부 서비스를 살펴 보십시오.

* 블록 스토리지, 파일 스토리지 또는 오브젝트 스토리지에서 적합한 [스토리지](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage) 유형을 선택하십시오.
* 필요한 [네트워크](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork) 유형을 선택하십시오.
* {{site.data.keyword.Bluemix_notm}} Kubernetes 기술을 활용하려면 [컨테이너](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers) 서비스를 선택하십시오.

## 다음 단계
{: #next-steps}

둘 이상의 지역에서 서비스를 호스팅할 수 있으면 앱이 호스팅되는 지역을 선택할 수 있습니다. 이를 수행하려면 {{site.data.keyword.Bluemix_notm}}에서 앱의 사용자 정의 URL 정보를 등록하고 추가하십시오. 그리고 앱이 호스팅된 지역을 선택하십시오. 앱을 배치하는 방법에 대한 자세한 정보는 [앱 업데이트](updapps.html)를 참조하십시오. 
