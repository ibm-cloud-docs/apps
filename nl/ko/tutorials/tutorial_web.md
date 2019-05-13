---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-30"

keywords: basic web app tutorial, apps, web app, starter kit, App Service, developer tools, DevOps toolchain, basic app, create basic web app

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 스타터 킷을 사용한 기본 웹 앱 작성
{: #tutorial-webapp}

{{site.data.keyword.cloud}}는 코딩을 빠르게 시작할 수 있도록 다양한 스타터 킷을 제공합니다. 앱 서비스 스타터 킷에서 언어, 프레임워크 및 도구를 선택하여 사전 구성된 사용자 정의 애플리케이션에 대한 작업을 시작하십시오. 이 튜토리얼에서는 필요한 도구를 설치한 후 앱을 빌드하여 로컬로 실행하고, 이를 클라우드에 배치하는 단계를 수행합니다.
{: shortdesc}

## 1단계. 도구 설치
{: #prereqs-webapp}

[개발자 도구](/docs/cli?topic=cloud-cli-ibmcloud-cli)를 설치하십시오.

Docker는 개발자 도구의 일부로 설치됩니다. Docker는 작업할 빌드 명령에 대해 실행되어야 합니다. Docker 계정을 작성하고, Docker 앱을 실행하고, 로그인해야 합니다.

## 2단계. 스타터 킷 선택
{: #create-webapp}

스타터 킷은 {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}에서 다양한 언어 및 프레임워크로 사용 가능합니다. 프로젝트에 가장 적합한 언어를 선택하여 시작하십시오.

1. {{site.data.keyword.dev_console}}의 [스타터 킷 ](https://{DomainName}/developer/appservice/starter-kits/){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘") 페이지에서 언어에 맞는 스타터 킷을 선택하십시오.
2. 선택사항. 앱을 분류하기 위한 태그를 제공하십시오. 자세한 정보는 [태그에 대한 작업](/docs/resources?topic=resources-tag)을 참조하십시오.
3. 언어 및 프레임워크를 선택하십시오. 일부 스타터 킷은 하나의 언어로만 사용 가능할 수 있습니다.
4. 가격 플랜을 선택하십시오. 이 튜토리얼에 사용할 수 있는 무료 옵션이 있습니다.
5. **작성**을 클릭하십시오.

## 3단계. 서비스 추가(선택사항)
{: #resources-webapp}

Watson의 코그너티브 기능으로 앱을 향상시키는 서비스를 추가하거나 모바일 서비스 또는 보안 서비스를 추가할 수 있습니다. 이 튜토리얼의 경우 데이터를 관리할 위치를 추가하십시오.

1. **앱 세부사항** 페이지에서 **서비스 추가**를 클릭하십시오.
2. 원하는 서비스의 종류를 선택하십시오. 예를 들어, **데이터** > **다음** > **Cloudant** > **다음**을 선택하십시오.
3. 가격 플랜을 선택하십시오. 이 튜토리얼에 사용할 수 있는 무료 옵션이 있습니다.
4. **작성**을 클릭하십시오.

## 4단계. DevOps 도구 체인 작성
{: #toolchain-webapp}

도구 체인을 사용으로 설정하면 앱에 대한 팀 기반 개발 환경을 작성할 수 있습니다. 도구 체인을 작성하는 경우 앱 서비스는 소스 코드를 보고, 앱을 복제하여 이슈를 작성하고 관리할 수 있는 Git 저장소를 작성합니다. 또한 전용 Git Lab 환경 및 지속적 Delivery Pipeline에 대한 액세스도 제공됩니다. 이는 사용자가 선택하는 배치 대상([Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 또는 [Virtual Server(VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers))에 맞게 사용자 정의됩니다.

지속적 딜리버리는 일부 애플리케이션에 대해 사용으로 설정됩니다. Delivery Pipeline 및 GitHub를 통해 빌드, 테스트 및 배치를 자동화하기 위해 지속적 딜리버리를 사용으로 설정할 수 있습니다.

**앱 세부사항** 페이지에서 **지속적 딜리버리 구성**을 클릭하고 배치 대상을 선택한 후 **작성**을 클릭하십시오. {{site.data.keyword.cloud_notm}}가 Git 저장소와 지속적 Delivery Pipeline을 모두 갖춘 공개 도구 체인을 자동으로 작성합니다.

배치 대상을 선택한 후, 새 도구 체인의 파이프라인 컴포넌트를 열어 초기 빌드 및 배치 프로세스를 시작하고 나면 몇 분 내에 새 앱을 확인할 수 있습니다.

자세한 정보는 [도구 체인 작성](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)을 참조하십시오.

## 5단계. 앱을 로컬로 빌드하고 실행
{: #build-run-webapp}

도구 체인을 작성한 마지막 단계에서 앱을 클라우드에 배치합니다. 도구 체인은 코드를 찾을 수 있는 앱을 위한 Git 저장소를 작성합니다. 저장소에 액세스하려면 다음 단계를 따르십시오. 앱을 클라우드에 푸시하기 전에 테스트를 위해 앱을 로컬로 빌드할 수 있습니다.

1. **앱 세부사항** 페이지에서 **코드 다운로드** 또는 **저장소 복제**를 클릭하여 로컬로 코드 관련 작업을 수행하십시오.
2. 앱을 통합된 개발 환경으로 가져오십시오.
3. 코드를 수정하십시오.
4. 개인 액세스 토큰을 추가하여 [Git 인증](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication)을 설정하십시오.
5. {{site.data.keyword.cloud_notm}} 명령행 인터페이스에 로그인하십시오. 조직에서 연합 로그인을 사용하는 경우 `-sso` 옵션을 사용하십시오.

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. 조직 및 영역 대상을 설정하십시오.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. 인증 정보를 가져오십시오.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Docker가 실행 중인지 확인하고 디렉토리에서 로컬 개발 컨테이너에 있는 앱을 빌드하십시오.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. 로컬 개발 컨테이너에 있는 앱을 실행하십시오.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. 브라우저에서 `http://localhost:3000`을 여십시오. 포트 번호는 선택한 런타임에 따라 다를 수 있습니다.

## 6단계. 앱 배치
{: #deploy-webapp}

### 도구 체인을 사용하여 배치
{: #deploy-webapp-toolchain}

여러 가지 방법으로 앱을 {{site.data.keyword.cloud_notm}}에 배치할 수 있지만 프로덕션 앱을 배치하는 데 DevOps 도구 체인을 사용하는 것이 가장 좋은 방법입니다. DevOps 도구 체인을 사용하여 여러 환경으로의 배치를 손쉽게 자동화하고, 앱이 확장됨에 따라 이를 관리하는 데 도움을 주기 위해 신속하게 모니터링, 로깅 및 경보 서비스를 추가할 수 있습니다.

도구 체인이 적절히 구성되면 저장소의 마스터 분기에 대한 각 병합마다 빌드-배치 주기가 자동으로 시작됩니다. {{site.data.keyword.cloud_notm}} 개발자 대시보드로부터 작성된 모든 도구 체인은 자동 배치로 구성됩니다.

DevOps 도구 체인에서 수동으로 앱을 배치할 수도 있습니다.

1. **앱 세부사항** 페이지에서 **도구 체인 보기**를 클릭하십시오.
2. 빌드를 시작하고 배치를 관리하며 로그 및 히스토리를 볼 수 있는 **Delivery Pipeline**을 클릭하십시오.

자세한 정보는 [빌드 및 배치](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)를 참조하십시오.

### {{site.data.keyword.dev_cli_short}}을 사용하여 배치
{: #deploy-webapp-cli}

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

앱 배치에 관한 자세한 정보는 [앱 배치](/docs/apps?topic=creating-apps-deploying-apps)를 참조하십시오.

## 7단계. 앱 실행 확인
{: #verify-webapp}

앱을 배치하고 나면 Delivery Pipeline 또는 명령행이 사용자를 앱의 URL로 이동시킵니다.

1. DevOps 도구 체인에서 **Delivery Pipeline**을 클릭한 후 **배치 단계**를 선택하십시오.
2. **로그 및 히스토리 보기**를 클릭하십시오.
3. 로그 파일에서 애플리케이션 URL을 찾으십시오.

    로그 파일의 끝에서 단어 `urls` 또는 `view`를 찾으십시오. 예를 들면, 로그 파일에서 `urls: my-app-devhost.mybluemix.net` 또는 `View the application health at: http://<ipaddress>:<port>/health`와 같은 행을 볼 수 있습니다.

4. 브라우저에서 해당 URL로 이동하십시오. 앱이 실행 중인 경우에는 `Congratulations` 또는 `{"status":"UP"}`와 같은 항목을 포함하는 메시지가 표시됩니다.

명령행을 사용하는 경우에는 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 명령을 사용하여 앱의 URL을 보십시오. 그 후 브라우저에서 해당 URL로 이동하십시오.
