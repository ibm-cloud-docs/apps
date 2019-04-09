---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# 앱 호스팅
{: #hosting}

기존 앱이 있는 경우 필요한 모든 인프라 또는 플랫폼 서비스를 사용하여 IBM Cloud에 기존 앱을 호스팅할 수 있습니다. 또한 {{site.data.keyword.Bluemix_notm}} 인프라도 활용하여 특히 {{site.data.keyword.Bluemix_notm}}를 위해 개발한 앱을 호스팅할 수 있습니다.
{:shortdesc}

## 앱 마이그레이션
{: #ht_hostapp}

앱을 클라우드 환경으로 완전히 이동하는 대신, 점진적으로 {{site.data.keyword.Bluemix_notm}}에 앱을 마이그레이션할 수 있습니다. 우선 앱의 일부를 마이그레이션한 후에 클라우드 통합 서비스를 사용하여 기존 데이터 또는 SOR(System of Record)에 연결할 수 있습니다.

{{site.data.keyword.Bluemix_notm}} 앱의 경우 백엔드 데이터 또는 서비스에 액세스해야 할 수 있습니다(예: SOR(System of Record)). {{site.data.keyword.Bluemix_notm}}에서는 Secure Gateway 서비스를 사용하여 {{site.data.keyword.Bluemix_notm}} 조직 및 엔터프라이즈 백엔드 네트워크 간의 보안 터널을 설정할 수 있습니다. 서비스를 사용하면 {{site.data.keyword.Bluemix_notm}}의 앱이 백엔드 네트워크의 데이터 및 서비스에 액세스할 수 있습니다. 세부사항은 [Reaching enterprise backend with Bluemix Secure Gateway via console ![외부 링크 아이콘](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}을 참조하십시오.

{{site.data.keyword.Bluemix_notm}}는 기존 앱을 호스팅하고 {{site.data.keyword.Bluemix_notm}}의 모든 인프라를 제공할 수 있습니다. [카탈로그](https://console.bluemix.net/catalog/?taxonomyNavigation=apps)에서 클라우드의 앱을 베어 메탈 서버에서 호스팅할지 또는 가상 서버에서 호스팅할지를 선택할 수 있습니다. 

한 번에 모두 또는 컴포넌트별로 앱의 파트를 {{site.data.keyword.Bluemix_notm}}에 마이그레이션할 수 있습니다. 앱을 마이그레이션할 때 IBM에서 제공하는 일부 서비스를 살펴 보십시오. 

* 블록 스토리지, 파일 스토리지 또는 오브젝트 스토리지에서 적합한 [스토리지](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage) 유형을 선택하십시오. 
* 필요한 [네트워크](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork) 유형을 선택하십시오. 
* {{site.data.keyword.Bluemix_notm}} Kubernetes 기술을 활용하려면 [컨테이너](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers) 서비스를 선택하십시오. 

## 다음 단계
{: #next-steps}

하나 이상의 지역에서 서비스를 호스팅할 수 있으면 앱이 호스팅되는 지역을 선택할 수 있습니다. [앱 업데이트](updapps.html)에서 앱을 호스팅하는 지역을 선택하고 사용자 정의 URL을 편집할 수 있습니다. 
