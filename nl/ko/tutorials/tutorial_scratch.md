---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# 처음부터 앱 작성
{: #tutorial-scratch}

서비스 및 런타임을 사용하여 처음부터 사용자 정의 애플리케이션을 작성할 수 있습니다. 
{: shortdesc}

## 시작하기 전에
{: #prereqs-scratch}

* Docker를 포함하는 [{{site.data.keyword.dev_cli_long}}](/docs/cli/index.html#overview)를 설치하십시오.  
* Docker 계정을 작성하고, Docker 앱을 실행하고 로그인하십시오. Docker는 작업할 빌드 명령에 대해 실행되어야 합니다.
* [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about)에 앱을 배치하려는 경우에는 [{{site.data.keyword.cloud_notm}} 계정을 준비](/docs/cloud-foundry/prepare-account.html#prepare)해야 합니다. 

## 앱 작성
{: #create-scratch}

1. [{{site.data.keyword.cloud_notm}} 대시보드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://cloud.ibm.com)의 앱 위젯에서 **앱 작성**을 클릭하십시오. 

  {{site.data.keyword.dev_console}}의 [스타터 킷 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}/developer/appservice/starter-kits/) 페이지로부터 사용자 정의 앱을 작성할 수도 있습니다.
  {: tip}

2. 앱의 이름을 입력하십시오. 이 튜토리얼의 경우에는 `CustomProject`를 사용하십시오. 
3. 고유한 호스트 이름을 입력하십시오(예: `abc-devhost`). 호스트 이름은 앱의 라우트(예: `abc-devhost.cloud.ibm.com`)로 사용됩니다. 
4. 앱을 분류하기 위한 태그를 선택적으로 제공할 수 있습니다. 자세한 정보는 [태그에 대한 작업](/docs/resources/tagging_resources.html#tag)을 참조하십시오.
5. 언어 및 프레임워크를 선택하십시오. 일부 스타터 킷은 하나의 언어로만 사용 가능할 수 있습니다. 
6. 가격 플랜을 선택하십시오. 이 튜토리얼의 경우 무료 옵션을 사용할 수 있습니다.
7. **작성**을 클릭하십시오.

## 리소스 추가(선택사항)
{: #resources-scratch}

Watson의 코그너티브 기능으로 앱을 향상시키는 리소스를 추가하고 모바일 서비스 또는 보안 서비스를 추가할 수 있습니다. 이 튜토리얼의 경우에는 데이터를 관리할 위치를 추가할 수 있습니다. 

1. 앱 서비스 창에서 **리소스 추가**를 클릭하십시오.
2. 원하는 서비스의 종류를 선택하십시오. 예를 들어, **데이터** > **다음** > **Cloudant** > **다음**을 선택하십시오.
3. 가격 플랜을 선택하십시오. 이 튜토리얼의 경우 무료 옵션을 사용할 수 있습니다.
4. **작성**을 클릭하십시오.

## 앱을 로컬로 빌드하고 실행
{: #build-run-scratch}

앱을 클라우드에 배치하기 전에 테스트를 위해 로컬로 빌드할 수도 있습니다. 

1. 앱 서비스 창에서 **코드 다운로드** 또는 **저장소 복제**를 클릭하여 로컬로 코드 관련 작업을 수행하십시오.
2. 앱을 통합된 개발 환경으로 가져오십시오.
3. 코드를 수정하십시오.
4. 개인 액세스 토큰을 추가하여 [Git 인증](/docs/services/ContinuousDelivery/git_working.html#git_authentication)을 설정하십시오.
5. {{site.data.keyword.cloud_notm}} 명령행 인터페이스(CLI)에 로그인하십시오. 조직에서 연합 로그인을 사용하는 경우 `-sso` 옵션을 사용하십시오. 예를 들면 다음과 같습니다. 

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. 다음 명령을 실행하여 조직 및 영역 대상을 설정하십시오. 

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. 다음 명령을 실행하여 인증 정보를 검색하십시오. 

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Docker가 실행 중인지 확인하고, 다음 명령을 실행하여 디렉토리로부터 로컬 개발 컨테이너에 앱을 빌드하십시오. 

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. 다음 명령을 실행하여 로컬 개발 컨테이너에서 앱을 실행하십시오. 

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. 브라우저에서 `http://localhost:3000`으로 이동하십시오. 포트 번호는 선택한 런타임에 따라 다를 수 있습니다.

## 앱 배치
{: #deploy-scratch}

여러 가지 방법으로 앱을 {{site.data.keyword.cloud_notm}}에 배치할 수 있지만 프로덕션 앱을 배치하는 데 DevOps 도구 체인을 사용하는 것이 가장 좋은 방법입니다. DevOps 도구 체인을 사용하여 여러 환경으로의 배치를 손쉽게 자동화하고, 앱이 확장됨에 따라 이를 관리하는 데 도움을 주기 위해 신속하게 모니터링, 로깅 및 경보 서비스를 추가할 수 있습니다.

도구 체인을 사용으로 설정하면 앱에 대한 팀 기반 개발 환경을 작성할 수 있습니다. 도구 체인을 작성하는 경우 앱 서비스는 소스 코드를 보고, 앱을 복제하여 이슈를 작성하고 관리할 수 있는 Git 저장소를 작성합니다. 또한 전용 Git Lab 환경 및 지속적 Delivery Pipeline에 대한 액세스도 제공됩니다. 이들은 사용자가 선택하는 배치 환경([Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) 또는 [Virtual Server(VSI)](/docs/vsi/vsi_index.html))에 대해 사용자 정의되어 있습니다. 

{{site.data.keyword.cloud_notm}} 개발자 대시보드로부터 작성된 모든 도구 체인은 자동 배치로 구성됩니다.
{: note}

### DevOps 도구 체인을 사용한 수동 배치

도구 체인이 적절히 구성되면 저장소의 마스터 분기에 대한 각 병합마다 빌드-배치 주기가 자동으로 시작됩니다. 

DevOps 도구 체인에서 수동으로 앱을 배치할 수도 있습니다.

1. 앱 세부사항 창에서 **도구 체인 보기**를 클릭하십시오.
2. 빌드를 시작하고, 배치를 관리하고 로그 및 히스토리를 볼 수 있는 **Delivery Pipeline**을 클릭하십시오.

지속적 딜리버리는 일부 애플리케이션에 대해 사용으로 설정됩니다. Delivery Pipeline 및 GitHub를 통해 빌드, 테스트 및 배치를 자동화하기 위해 지속적 딜리버리를 사용으로 설정할 수 있습니다.

자세한 정보는 다음을 참조하십시오.
* Continuous Delivery를 사용하여 [빌드 및 배치](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy)하십시오. 
* 템플리트로부터 [도구 체인을 작성](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started)하십시오. 

### DevOps 도구 체인을 사용한 자동 배치

1. 앱 세부사항 페이지에서 **클라우드에 배치**를 클릭하십시오.
2. 배치 방법을 선택하십시오. 선택하는 방법의 지시사항에 따라 배치 방법을 선택하십시오.
  * **[Kubernetes에 배치](/docs/apps/deploying/containers.html#containers)**합니다. 이 선택사항은 고가용성의 애플리케이션 컨테이너를 배치하고 관리하기 위해 작업자 노드라는 호스트 클러스터를 작성합니다. 클러스터를 작성하여 배치하거나 기존 클러스터에 배치할 수 있습니다.
  * **Cloud Foundry에 배치**합니다. 이 선택사항은 기본 인프라를 관리할 필요 없이 클라우드 기본 앱을 배치할 수 있도록 합니다. 계정에 {{site.data.keyword.cfee_full_notm}}에 대한 액세스 권한이 있는 경우에는 **[퍼블릭 클라우드](/docs/cloud-foundry-public/about-cf.html#about-cf)** 배치자 유형을 선택하거나, 사용자 엔터프라이즈 전용으로 Cloud Foundry 애플리케이션을 호스팅하는 격리된 환경을 작성하고 관리하는 데 사용할 수 있는 **[엔터프라이즈 환경](/docs/cloud-foundry-public/cfee.html#cfee)** 배치자 유형을 선택할 수 있습니다. 
  * **[Virtual Server](/docs/apps/vsi-deploy.html#vsi-deploy)에 배치**합니다. 이 선택사항은 가상 서버를 프로비저닝하고, 앱을 포함하는 이미지를 로드하고, DevOps 도구 체인을 작성하고 첫 번째 배치 사이클을 시작합니다. 

마지막 단계에서 앱을 클라우드에 배치하면 도구 체인이 자동으로 작성됩니다. 도구 체인은 코드를 찾을 수 있는 앱의 Git 저장소를 작성합니다. 

### {{site.data.keyword.dev_cli_short}}을 사용하여 배치
{: #deploy-scratch-cli}

앱을 Cloud Foundry에 배치하려면 다음 명령을 입력하십시오.
```
ibmcloud dev deploy
```
{: pre}

앱을 Kubernetes 클러스터에 배치하려면 다음 명령을 입력하십시오.
```
ibmcloud dev deploy --target <container>
```
{: pre}

## 앱이 실행 중인지 확인
{: #verify-scratch}

앱을 배치하고 나면 Delivery Pipeline 또는 명령행이 사용자를 앱의 URL로 이동시킵니다. 

1. DevOps 도구 체인에서 **Delivery Pipeline**을 클릭한 후 **배치 단계**를 선택하십시오. 
2. **로그 및 히스토리 보기**를 클릭하십시오. 
3. 로그 파일에서 애플리케이션 URL을 찾으십시오. 

    로그 파일의 끝에서 단어 `urls` 또는 `view`를 찾으십시오. 예를 들면, 로그 파일에서 `urls: my-app-devhost.cloud.ibm.com` 또는 `View the application health at: http://<ipaddress>:<port>/health`와 같은 행을 볼 수 있습니다. 

4. 브라우저에서 해당 URL로 이동하십시오. 앱이 실행 중인 경우에는 `Congratulations` 또는 `{"status":"UP"}`와 같은 항목을 포함하는 메시지가 표시됩니다. 

명령행을 사용하는 경우에는 [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) 명령을 사용하여 앱의 URL을 보십시오. 그 후 브라우저에서 해당 URL로 이동하십시오. 
