---

copyright:
  years: 2015, 2018
lastupdated: "2018-05-22"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 사용자 정의 도메인 작성 및 사용
{: #updatingapps}

명령행 또는 {{site.data.keyword.Bluemix}} Continuous Delivery를 사용하여 {{site.data.keyword.Bluemix_notm}}의 애플리케이션을 업데이트할 수 있습니다. 대부분의 경우(Node.js와 같은 빌드팩의 경우에도)에는 -c 매개변수를 제공하여 애플리케이션을 시작하는 데 사용되는 명령을 지정해야 합니다.
{:shortdesc}

도메인은 {{site.data.keyword.Bluemix_notm}}에서 조직에 할당되는 URL 라우트를 제공합니다. 사용자 정의 도메인을 사용하려면 공용 DNS 서버에 사용자 정의 도메인을 등록하고, {{site.data.keyword.Bluemix_notm}}에서 사용자 정의 도메인을 구성한 다음 해당 사용자 도메인을 공용 DNS 서버의 {{site.data.keyword.Bluemix_notm}} 시스템 도메인에 맵핑해야 합니다. 사용자 정의 도메인이 시스템 도메인에 맵핑되면 사용자 정의 도메인에 대한 요청이 {{site.data.keyword.Bluemix_notm}}의 애플리케이션으로 라우팅됩니다.

{{site.data.keyword.Bluemix_notm}} 콘솔 또는 명령행 인터페이스를 사용하여 사용자 정의 도메인을 작성하고 사용할 수 있습니다.

## {{site.data.keyword.Bluemix_notm}} 콘솔 사용

콘솔을 사용하여 조직의 사용자 정의 도메인을 작성하려면 다음 단계를 완료하십시오.

1. **관리** > **계정** > **Cloud Foundry 조직**으로 이동하십시오.
2. 사용자 정의 도메인을 작성하는 조직의 이름을 클릭하십시오.
3. **도메인** 탭을 클릭하십시오.
4. **도메인 추가**를 클릭하고 도메인 이름을 입력한 후 지역을 선택하십시오.
5. 업데이트를 확인하십시오. **추가**를 클릭하십시오. 

예를 들면, `*.mycompany.com`을 사용하여 라우트 `www.mybluemix.com`을 앱과 연관시킬 수 있습니다. `example.mycompany.com`을 사용하여 라우트 `www.example.mybluemix.com`을 앱과 연관시킬 수도 있습니다.
{: tip}

사용자 정의 도메인을 포함한 라우트를 애플리케이션에 추가하십시오.

1. **메뉴** 아이콘 ![메뉴 아이콘](../icons/icon_hamburger.svg) > **대시보드**를 클릭한 다음 라우트를 추가할 애플리케이션의 행을 클릭하십시오. **개요** 페이지가 표시됩니다.
2. **라우트** 메뉴에서 **라우트 편집**을 선택하십시오.
3. **라우트 추가**를 클릭하고 애플리케이션에 사용할 라우트를 지정하십시오.
4. **저장**을 클릭하여 업데이트를 확인하십시오.

## {{site.data.keyword.Bluemix_notm}} 명령행 인터페이스 사용

1. 다음 명령을 입력하여 조직의 사용자 정의 도메인을 작성하십시오.

   ```
   ibmcloud app domain-create <your org name> mydomain
   ```

2. 사용자 정의 도메인을 포함한 라우트를 애플리케이션에 추가하십시오. CF 앱의 경우 다음 명령을 입력하십시오.

   ```
   ibmcloud app route-map myapp mydomain -n host_name

   ```

       컨테이너 그룹의 경우 다음 명령을 입력하십시오.

   ```
     cf ic route map -n host_name -d mydomain mycontainergroup

   ```

{{site.data.keyword.Bluemix_notm}}에 사용자 정의 도메인을 구성한 후에는 사용자 정의 도메인을 등록된 DNS 서버의 {{site.data.keyword.Bluemix_notm}} 시스템 도메인에 맵핑하십시오.

1. DNS 서버에 사용자 정의 도메인 이름에 대한 'CNAME' 레코드를 설정하십시오. CNAME 레코드를 설정하기 위한 단계는 DNS 제공자에 따라 다릅니다. 예를 들어, GoDaddy를 사용하는 경우에는 GoDaddy의 [도메인 도움말 ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} 안내를 따르십시오. 
2. 애플리케이션이 실행 중인 {{site.data.keyword.Bluemix_notm}} 지역의 보안 엔드포인트에 사용자 정의 도메인 이름을 맵핑하십시오. 다음과 같은 지역 엔드포인트를 사용하여 {{site.data.keyword.Bluemix_notm}}에서 사용자 조직에 할당되는 URL 라우트를 제공하십시오.

  * US-SOUTH: `secure.us-south.bluemix.net`
  * US-EAST: `secure.us-east.bluemix.net`
  * EU-DE: `secure.eu-de.bluemix.net`
  * EU-GB: `secure.eu-gb.bluemix.net`
  * AU-SYD: `secure.au-syd.bluemix.net`

브라우저 또는 명령행 인터페이스에서 myapp 애플리케이션에 액세스하는 데 필요한 다음 URL을 입력하십시오.

```
http://host_name.mydomain

```

고아 라우트를 제거하려면 다음 명령을 실행하십시오.

```
ibmcloud app route-delete domain -n hostname -f

```
{: tip}

`domain`은 도메인 이름이고, `hostname`은 애플리케이션에 대한 라우트의 호스트 이름입니다. **ibmcloud app route-delete** 명령에 대한 자세한 정보를 보려면 `ibmcloud app route-delete -h`를 입력하십시오. 

