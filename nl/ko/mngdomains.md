---

copyright:
  years: 2019
lastupdated: "2019-04-02"

keywords: apps, custom, domain, kubernetes, cloud foundry, add, subdomain, custom domain, dns, domainname, domain name, endpoint, update, migrate

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 도메인 관리
{: #update-domain}

도메인은 {{site.data.keyword.cloud}}에서 조직에 할당되는 URL 라우트를 제공합니다. 사용자 정의 도메인은 애플리케이션에 대한 요청을 사용자가 소유한 URL로 직접 전달합니다. 사용자 정의 도메인은 공유 도메인, 공유 하위 도메인 또는 공유 도메인 및 호스트가 될 수 있습니다. 사용자 정의 도메인이 지정되지 않은 경우 {{site.data.keyword.cloud_notm}}는 애플리케이션의 라우트에 기본 공유 도메인을 사용합니다. 도메인 관리 프로세스는 배치 대상({{site.data.keyword.containershort}}, Cloud Foundry 및 기타)에 따라 다릅니다.
{:shortdesc}

사용자 정의 도메인을 사용하려면 공용 DNS 서버에 사용자 정의 도메인을 등록한 다음 {{site.data.keyword.cloud_notm}}에서 사용자 정의 도메인을 구성해야 합니다. 그런 다음 해당 사용자 정의 도메인을 공용 DNS 서버의 {{site.data.keyword.cloud_notm}} 시스템 도메인에 맵핑해야 합니다. 사용자 정의 도메인이 시스템 도메인에 맵핑되면 사용자 정의 도메인에 대한 요청이 {{site.data.keyword.cloud_notm}}의 애플리케이션으로 라우팅됩니다.

## Kubernetes 앱의 도메인 변경
{: #update-domain-kube}

{{site.data.keyword.containershort_notm}} 호스트 이름의 하위 도메인은 `containers.appdomain.cloud`입니다. IBM에서 제공하는 Ingress 하위 도메인 와일드카드, `*.<cluster_name>.<region>.containers.appdomain.cloud`는 클러스터에 기본적으로 등록되어 있습니다. IBM에서 제공하는 TLS 인증서는 와일드카드 인증서이며 와일드카드 하위 도메인에 사용할 수 있습니다. 자세한 정보는 [네임스페이스 내의 다중 도메인](/docs/containers?topic=containers-ingress#multi-domains)을 참조하십시오.

## Kubernetes 앱의 사용자 정의 도메인 사용
{: #custom-domain-kube}

사용자 정의 도메인을 사용하려면 사용자 정의 도메인을 `*.custom_domain.net `과 같은 와일드카드 도메인으로 등록해야 합니다. TLS를 사용하려면 와일드카드 인증서를 가져와야 합니다. 자세한 정보는 [네임스페이스 내의 다중 도메인](/docs/containers?topic=containers-ingress#multi-domains)을 참조하십시오.

웹 애플리케이션을 스캐폴딩(scaffolding)하고 컨테이너에서 로컬로 실행한 다음 IBM Kubernetes Service로 작성된 Kubernetes 클러스터에 배치하는 과정을 안내하는 [이 튜토리얼](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes)을 체크아웃하십시오. 또한 튜토리얼에서는 사용자 정의 도메인을 바인드하고 환경의 상태를 모니터하며 애플리케이션을 스케일링하는 방법에 대해 보여줍니다. 

## Cloud Foundry 앱의 도메인 변경
{: #update-domain-cf}

Cloud Foundry 앱의 경우 {{site.data.keyword.cloud_notm}} 콘솔 또는 명령행 인터페이스를 사용하여 도메인을 `mybluemix.net`에서 `appdomain.cloud`로 변경할 수 있습니다.
도메인을 `appdomain.cloud`로 변경하는 방법에 대한 자세한 정보는 [도메인 업데이트](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain)를 참조하십시오.


기본 공유 도메인은 `mybluemix.net`이지만 `appdomain.cloud `는 사용할 수 있는 다른 도메인 옵션입니다.
{: tip}

## Cloud Foundry 앱의 사용자 정의 도메인 사용
{: #custom-domain-cf}

Cloud Foundry 앱의 경우, {{site.data.keyword.cloud_notm}} 콘솔 또는 명령행 인터페이스를 사용하여 사용자 정의 도메인을 작성하고 사용할 수 있습니다.
자세한 정보는 [사용자 정의 도메인 추가 및 사용](/docs/cloud-foundry-public?topic=cloud-foundry-public-custom-domains)을 참조하십시오. 
