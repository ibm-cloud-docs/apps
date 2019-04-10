---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-15"

keywords: apps, custom domain, Kubernetes

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 사용자 정의 도메인 추가 및 사용
{: #updatingapps}

도메인은 {{site.data.keyword.cloud}}에서 조직에 할당되는 URL 라우트를 제공합니다. 사용자 정의 도메인은 애플리케이션에 대한 요청을 사용자가 소유한 URL로 직접 전달합니다. 사용자 정의 도메인은 공유 도메인, 공유 하위 도메인 또는 공유 도메인 및 호스트가 될 수 있습니다. 사용자 정의 도메인이 지정되지 않은 경우 {{site.data.keyword.cloud_notm}}는 애플리케이션의 라우트에 기본 공유 도메인을 사용합니다. {{site.data.keyword.cloud_notm}} 콘솔 또는 명령행 인터페이스를 사용하여 사용자 정의 도메인을 작성하고 사용할 수 있습니다.
{:shortdesc}

기본 공유 도메인은 `mybluemix.net`이지만 `appdomain.cloud `는 사용할 수 있는 다른 도메인 옵션입니다. `appdomain.cloud`로 마이그레이션하는 방법에 대한 자세한 정보는 [도메인 업데이트](/docs/apps/tutorials?topic=creating-apps-update-domain)를 참조하십시오.
{: tip}

사용자 정의 도메인을 사용하려면 공용 DNS 서버에 사용자 정의 도메인을 등록한 다음 {{site.data.keyword.cloud_notm}}에서 사용자 정의 도메인을 구성해야 합니다. 그런 다음 해당 사용자 정의 도메인을 공용 DNS 서버의 {{site.data.keyword.cloud_notm}} 시스템 도메인에 맵핑해야 합니다. 사용자 정의 도메인이 시스템 도메인에 맵핑되면 사용자 정의 도메인에 대한 요청이 {{site.data.keyword.cloud_notm}}의 애플리케이션으로 라우팅됩니다.

## {{site.data.keyword.cloud_notm}} 콘솔에서 사용자 정의 도메인 추가
{: #custom-domain-console}

콘솔을 사용하여 조직의 사용자 정의 도메인을 추가하려면 다음 단계를 완료하십시오.

1. **관리 > 계정**으로 이동하여 **Cloud Foundry 조직**을 선택하십시오.
2. 사용자 정의 도메인을 작성하는 조직의 이름을 클릭하십시오.
3. 사용 가능한 도메인 목록을 보려면 **도메인** 탭을 클릭하십시오.
4. **도메인 추가**를 클릭하고 도메인 이름을 입력한 후 지역을 선택하십시오.
5. 업데이트를 확인하고 **추가**를 클릭하십시오.

## 사용자 정의 도메인을 포함하는 라우트를 애플리케이션에 추가

1. [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")에서 **메뉴** 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg)을 클릭하고 **리소스 목록**을 선택하십시오.
2. **리소스 목록** 페이지에서 **Cloud Foundry 앱**을 클릭하십시오.
3. 라우트를 추가할 애플리케이션을 클릭하십시오. 해당 앱의 **개요** 페이지가 표시됩니다.
4. **라우트** 메뉴를 선택하고 **라우트 편집**을 선택하십시오.
5. **라우트 추가**를 클릭하고 애플리케이션에 사용할 라우트를 지정하십시오.
6. **저장**을 클릭하여 업데이트를 확인하십시오.

예를 들면, `*.mycompany.com`을 사용하여 라우트 `www.mybluemix.net`을 앱과 연관시킬 수 있습니다. `example.mycompany.com`을 사용하여 라우트 `www.example.bluemix.net`을 앱과 연관시킬 수도 있습니다.
{: tip}

## {{site.data.keyword.cloud_notm}} 명령행 인터페이스에서 사용자 정의 도메인 추가
{: #custom-domain-cli}

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
   
2. 다음 명령을 입력하여 조직의 사용자 정의 도메인을 작성하십시오.
   ```
   ibmcloud app domain-create <MY_ORGNAME> <MY_DOMAIN>
   ```

3. 사용자 정의 도메인을 포함하는 라우트를 애플리케이션에 추가하십시오.

   Cloud Foundry 앱의 경우 다음 명령을 입력하십시오.
   ```
   ibmcloud app route-map <MY_APPNAME> <MY_DOMAIN> -n <MY_HOSTNAME>
   ```
   
## 사용자 정의 도메인을 시스템 도메인에 맵핑
{: #mapcustomdomain}

{{site.data.keyword.cloud_notm}}에 사용자 정의 도메인을 구성한 후에는 사용자 정의 도메인을 등록된 DNS 서버의 {{site.data.keyword.cloud_notm}} 시스템 도메인에 맵핑하십시오.

1. DNS 서버에 사용자 정의 도메인 이름에 대한 'CNAME' 레코드를 설정하십시오. CNAME 레코드를 설정하기 위한 단계는 DNS 제공자에 따라 다릅니다. 예를 들어, GoDaddy를 사용하는 경우에는 GoDaddy의 [도메인 도움말 ](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘") 안내를 따르십시오.
2. 애플리케이션이 실행 중인 {{site.data.keyword.cloud_notm}} 지역의 보안 엔드포인트에 사용자 정의 도메인 이름을 맵핑하십시오. 다음과 같은 지역 엔드포인트를 사용하여 {{site.data.keyword.cloud_notm}}에서 사용자 조직에 할당되는 URL 라우트를 제공하십시오. 예를 들어, CNAME을 다음으로 지정하십시오. `<custom-domain>.us-east.cf.cloud.ibm.com.`

  **Cloud Foundry 엔드포인트:**
  * US-SOUTH - `custom-domain.us-south.cf.cloud.ibm.com`
  * US-EAST - `custom-domain.us-east.cf.cloud.ibm.com`
  * EU-DE - `custom-domain.eu-de.cf.cloud.ibm.com`
  * EU-GB - `custom-domain.eu-gb.cf.cloud.ibm.com`
  * AU-SYD - `custom-domain.au-syd.cf.cloud.ibm.com`

## 애플리케이션에 액세스
{: #access-app}

브라우저에서 다음 URL을 입력하여 애플리케이션에 액세스하십시오. 여기서, `hostname`은 호스트 이름이고 `mydomain`은 도메인 이름입니다.
```
http://hostname.mydomain
```

## 고아 라우트 제거
{: #remove-orphaned-route}

고아 라우트를 제거하려면 다음 명령을 실행하십시오.
```
ibmcloud app route-delete <MY_DOMAIN> -n <MY_HOSTNAME> -f
```
{: tip}

이 예에서 `domain`은 도메인 이름이고, `hostname`은 애플리케이션에 대한 라우트의 호스트 이름입니다. `ibmcloud app route-delete` 명령에 대한 자세한 정보를 보려면 `ibmcloud app route-delete -h` 명령을 입력하십시오.

## Kubernetes 앱의 사용자 정의 도메인 사용
{: #kube-custom-domain}

IBM Cloud Kubernetes Service 호스트 이름의 하위 도메인은 `containers.appdomain.cloud`입니다. IBM에서 제공하는 Ingress 하위 도메인 와일드카드, `*.<cluster_name>.<region>.containers.mybluemix.net`은 클러스터에 기본적으로 등록되어 있습니다. IBM에서 제공하는 TLS 인증서는 와일드카드 인증서이며 와일드카드 하위 도메인에 사용할 수 있습니다. 사용자 정의 도메인을 사용하려면 사용자 정의 도메인을 `*.custom_domain.net `과 같은 와일드카드 도메인으로 등록해야 합니다. TLS를 사용하려면 와일드카드 인증서를 가져와야 합니다. 자세한 정보는 [네임스페이스 내의 다중 도메인](/docs/containers?topic=containers-ingress#multi-domains)을 참조하십시오.

웹 애플리케이션을 스캐폴딩(scaffolding)하고 컨테이너에서 로컬로 실행한 다음 IBM Kubernetes Service로 작성된 Kubernetes 클러스터에 배치하는 과정을 안내하는 [이 튜토리얼](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes)을 체크아웃하십시오. 또한 사용자 정의 도메인을 바인드하고 환경의 상태를 모니터하며 애플리케이션을 스케일링하는 방법에 대해 알아봅니다.
