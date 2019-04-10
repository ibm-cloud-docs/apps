---

copyright:
  years: 2019
lastupdated: "2019-03-15"

keywords: apps, domain, Kubernetes, Cloud Foundry, cli

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 도메인 업데이트
{: #update-domain}

도메인은 {{site.data.keyword.cloud}}에서 조직에 할당되는 URL 라우트를 제공합니다. Cloud Foundry 앱의 경우 {{site.data.keyword.cloud_notm}} 콘솔 또는 명령행 인터페이스를 사용하여 도메인을 `mybluemix.net`에서 `appdomain.cloud`로 마이그레이션할 수 있습니다.
{:shortdesc}

## {{site.data.keyword.cloud_notm}} 콘솔에서 도메인 업데이트
{: #update-domain-console}

기본 공유 도메인은 `mybluemix.net`이지만 `appdomain.cloud `는 사용할 수 있는 다른 도메인 옵션입니다.
{: tip}

콘솔을 사용하여 Cloud Foundry 조직의 도메인을 업데이트하려면 다음 단계를 완료하십시오.

1. [{{site.data.keyword.cloud_notm}} 콘솔![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}){: new_window}에서 **메뉴** 아이콘 ![메뉴 아이콘](../icons/icon_hamburger.svg)을 클릭하고 **리소스 목록**을 선택하십시오.
2. **리소스 목록** 페이지에서 **Cloud Foundry 앱**을 클릭하십시오.
3. 도메인을 변경할 애플리케이션을 클릭하십시오. 해당 앱의 **개요** 페이지가 표시됩니다.
4. **라우트** 메뉴를 선택하고 현재 도메인(예: `<myapp.mybluemix.net>`)을 확인한 다음 **라우트 편집**을 클릭하십시오.
5. 도메인 목록을 선택한 다음 사용할 도메인(예: `us-south.cf.appdomain.cloud`)을 클릭하십시오.
6. **저장**을 클릭하여 업데이트를 확인하십시오.
7. 이전 도메인을 대체할지 확인하고 **제거**를 클릭하십시오.
8. 새 라우트가 작동하는지 확인하려면 **앱 URL 방문**을 클릭하십시오.

## {{site.data.keyword.cloud_notm}} 명령행 인터페이스에서 도메인 업데이트
{: #update-domain-cli}

1. Cloud Foundry 앱의 경우 다음 명령을 입력하여 대상으로 지정된 Cloud Foundry API 엔드포인트에 연결하십시오.
   ```
   ibmcloud target --cf-api <CF_ENDPOINT>
   ```
   
   **Cloud Foundry API 엔드포인트:**
   * US-SOUTH - `api.us-south.cf.cloud.ibm.com`
   * US-EAST - `api.us-east.cf.cloud.ibm.com`
   * EU-DE - `api.eu-de.cf.cloud.ibm.com`
   * EU-GB - `api.eu-gb.cf.cloud.ibm.com`
   * AU-SYD - `api.au-syd.cf.cloud.ibm.com`

2. 다음 명령을 입력하여 새 도메인을 포함하는 라우트를 애플리케이션에 추가하십시오.
   ```
   ibmcloud app route-map APP_NAME DOMAIN -n HOSTNAME
   ```

## Kubernetes 앱의 도메인 업데이트
{: #update-domain-kube}

{{site.data.keyword.containerlong}} 호스트 이름의 하위 도메인은 `containers.appdomain.cloud`입니다. IBM에서 제공하는 Ingress 하위 도메인 와일드카드, `*.<cluster_name>.<region>.containers.appdomain.cloud`는 클러스터에 기본적으로 등록되어 있습니다. IBM에서 제공하는 TLS 인증서는 와일드카드 인증서이며 와일드카드 하위 도메인에 사용할 수 있습니다. 자세한 정보는 [네임스페이스 내의 다중 도메인](/docs/containers?topic=containers-ingress#multi-domains)을 참조하십시오.
