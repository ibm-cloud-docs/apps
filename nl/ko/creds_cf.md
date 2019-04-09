---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Cloud Foundry 환경에 인증 정보 추가
{: #add-credentials-cf}

Cloud Foundry 배치 환경에 서비스 인증 정보를 추가하는 방법에 대해 알아봅니다. 이러한 지시사항은 [Cloud Foundry 퍼블릭](/docs/cloud-foundry-public/about-cf.html) 및 [Cloud Foundry 엔터프라이즈 환경](/docs/cloud-foundry-public/cfee.html) 모두에 적용됩니다.
{: shortdesc}

## 사용자 코드 + Cloud Foundry
{: #credentials-byoc-cf}

애플리케이션이 존재하는 Cloud Foundry 영역에서 사용자 제공 서비스를 호출하는 Cloud Foundry를 정의할 수 있습니다. 사용자 제공 서비스는 Cloud Foundry 영역에서 바인드 가능 서비스인 것처럼 저장된 문자열로 변환된 JSON입니다. 로그인하여 Cloud Foundry 조직 및 영역에 연결되면 다음 단계를 완료하여 서비스를 작성하고 바인드하십시오.

1. 다음 명령을 실행하여 사용자 제공 서비스를 작성하십시오.
  ```console
  cf cups customcreds -p '{"username":"Leeroy","password":"Jenkins"}'
  ```
  {: codeblock}

2. 서비스 섹션에 추가하여 사용자 제공 서비스에 바인딩하도록 Cloud Foundry 애플리케이션를 구성하십시오.
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - customcreds
  ```

3. `VCAP_SERVICES` 환경 변수의 환경을 읽고 이를 JSON으로 구문 분석한 후에 필요한 인증 정보를 찾도록 애플리케이션을 코딩하십시오(node.js 같은 유사 코드).
  ```
  // get the 'password' from "customcreds" user-provided service
  vcapServices = getEnvironment('VCAP_SERVICES');
  vcapServicesAsJSON = JSON.parse(vcapServices);
  upsArray = vcapServicesAsJSON['user-provided'];
  if (upsArray) {
      for (var i = 0, len = upsArray.length; i < len; i++) {
          if (upsArray[i].name === 'customcreds') {
              return upsArray[i].credentials.password
          }
      }
  }
  ```
{: codeblock}


## 스타터 킷 앱 + Cloud Foundry
{: #credentials-starterkit-cf}

### Cloud Foundry 영역의 준비 방법

**클라우드에 배치** 기능을 사용하여 Cloud Foundry 영역에 앱을 배치하십시오.

Cloud Foundry 기반 리소스 인스턴스가 배치된 Cloud Foundry 애플리케이션과 동일한 Cloud Foundry 영역에 있으면 [다음 절](/docs/apps/creds_cf.html#cf_resource_same)을 참조하십시오.

Cloud Foundry 기반 리소스 인스턴스가 Cloud Foundry 애플리케이션의 대상 영역이 아닌 다른 영역에 있으면 [다음 절](/docs/apps/creds_cf.html#cf_resource_different)을 참조하십시오.

애플리케이션과 연관된 리소스가 리소스 제어기 기반이면 [리소스 제어기](/docs/apps/creds_cf.html#cf_resource_controller)를 참조하십시오.

#### Cloud Foundry 기반 리소스가 배치된 앱과 동일한 영역에 있음
{: #cf_resource_same}

애플리케이션과 연관된 리소스가 Cloud Foundry 기반인 경우, 리소스는 Cloud Foundry에서 "바인드 가능"합니다. `cf` 명령행을 올바른 지역 + 조직 + 영역과 연결하여 Cloud Foundry 영역의 서비스를 볼 수 있습니다. 어떤 Cloud Foundry 조직 및 영역에 리소스를 작성하는지에 대한 질문을 받은 경우에는 리소스 작성 시점에 해당 리소스가 Cloud Foundry 기반인지 알 수 있습니다.

다음 명령을 실행하여 바인딩된 애플리케이션을 볼 수 있습니다.
```console
cf services
```
{: codeblock}

출력 예:
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg3-alertnotificati-1538417831070   alertnotification   authorizedusers                create succeeded
```
{: screen}

#### Cloud Foundry 기반 리소스가 배치된 앱과 다른 영역에 있음
{: #cf_resource_different}

애플리케이션과 서비스가 동일한 Cloud Foundry 영역에 없는 경우, Cloud Foundry는 Cloud Foundry 서비스에 대한 Cloud Foundry 애플리케이션의 "바인딩"을 지원하지 않습니다. Cloud Foundry 영역은 "사용자 제공" 서비스로 준비되어야 하며 다음 절이 적용될 수 있습니다.

#### 리소스 제어기 기반 리소스가 앱과 연관되어 있음
{: #cf_resource_controller}

애플리케이션과 연관된 리소스가 ResourceController 기반인 경우(어떤 리소스 그룹에 리소스를 작성하는지에 대한 질문을 받은 경우에는 리소스 작성 시점에 해당 리소스가 `ResourceController` 기반임을 알 수 있음), 리소스는 Cloud Foundry에서 "바인딩 가능"하지 _않습니다_. 애플리케이션이 코드에서 참조할 수 있도록 Cloud Foundry 영역이 리소스 인증 정보와 함께 준비되어야 합니다. 준비는 자동으로 이루어지며, 다음을 실행하여 `cf` 명령행을 사용자의 영역에 연결함으로써 영역 준비의 결과를 관찰할 수 있습니다.
```console
cf services
```
{: codeblock}

출력 예:
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg-cloudant-1538408663553           user-provided
```
{: screen}

Cloud Foundry는 서비스 인증 정보 값(인코딩됨 또는 기타)에 대한 가시성을 `cf service` 또는 `cf services` 명령행에 허용하지 않습니다. 기능적으로, 사용자 제공 서비스는 Cloud Foundry 영역에서 이름 지정된 "서비스 인스턴스"로서 정의되어 있는 문자열로 변환된 JSON입니다. 해당 값을 보려면 우선 앱의 `manifest.yml` 파일에서 `services` 표제 아래에 서비스 인스턴스 이름을 표시하여 애플리케이션을 Cloud Foundry 서비스에 바인딩해야 합니다. 그리고 Cloud Foundry 영역에서 앱을 실행한 후에 `cf env $APP_NAME`을 실행하여 해당 애플리케이션의 환경을 가져오십시오.

다행스럽게도, 스타터 킷에서 생성된 코드는 애플리케이션이 실행되는 Cloud Foundry 영역에서 이에 대해 정의된 환경으로부터 값을 검색하여 사용할 수 있도록 올바른 바인딩으로 자동으로 채워집니다.

### 스타터 킷에서 생성된 코드
{: #starterkit-generated-code-cf}

계속하기 전에 [스타터 킷 앱 + kube](/docs/apps/creds_kube.html#credentials-starterkit-kube-gencode)를 참조하십시오. 그리고 다음 변경사항을 적용하십시오.

* 생성된 코드에서 `deployment.yml`을 제공하기는 하지만, 이는 Cloud Foundry에 배치된 애플리케이션에는 적용되지 않습니다. 오히려 `manifest.yml`이 _적용될 수 있으며_, Cloud Foundry 영역에서 작성된 두 개의 서비스에 _바인드_할 수 있도록 해당 컨텐츠가 표시됩니다.
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - blarg3-alertnotificati-1538417831070
      - blarg-cloudant-1538408663553
  ```
  {: codeblock}

이전 하위 절에서 문서의 나머지가 다시 한 번 적용됩니다. `IBMCloudEnv` 라이브러리는 애플리케이션이 실행되는 환경에서 값의 검색을 추상화합니다.

라이브러리는 Cloud Foundry의 환경 값 검색에서 일부 복잡도를 추상화합니다. Cloud Foundry에서, 실행 중인 애플리케이션은 서비스가 사용자 정의 서비스 값 또는 Cloud Foundry 영역 _내의_ 서비스 인스턴스인지와 무관하게 바인딩된 서비스 인증 정보의 값을 보유하며 해당 값이 문자열 처리된 JSON인 `VCAP_SERVICES`로 이름 지정된 환경 변수를 제공받습니다. `VCAP_SERVICES` 환경 변수에서 구문 분석된 JSON의 최상위 레벨 키는 해당 값이 모든 "사용자 제공" 서비스에 대한 인증 정보의 배열을 보유한 키 `user-provided` 및 Cloud Foundry 기반인 서비스와 연관된 Cloud Foundry `label`입니다.

**주의**: 참조 섹션에서 표시된 주의와 유사하게, 환경 준비는 _항상_ 앱과 연관된 모든 리소스의 모든 인증 정보에 대해 수행되며 모든 `services`는 `manifest.yml`에 나열되지만 _일부 인증 정보 참조_는 `mappings.json` 파일에 지정되지 않습니다. 이러한 경우에는 사용자가 해당 참조를 직접 지정해야 합니다. 일단 대상 배치를 결정했으며 `IBMCloudEnv` 라이브러리의 추상화가 필요하지 않은 경우에는 자체 의사결정에 맞는 "사용자 코드 + (대상 배치)" 절을 참조하십시오.

**재차 주의**: 일부 스타터 킷에는 `IBMCloudEnv` 종속 항목, `manifest.yml` 또는 `mappings.json` 파일에 대한 참조가 전혀 포함되지 않습니다.
