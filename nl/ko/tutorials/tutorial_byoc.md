---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-20"

keywords: byoc, code repository, continuous delivery, cli, deploy, create app custom repo, custom repo, existing repo, custom code

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# 자체 코드 저장소에서 앱 작성
{: #tutorial-byoc}

기존 저장소에 애플리케이션이 있는 경우 기본 스타터 킷을 사용하여 {{site.data.keyword.cloud_notm}}에서 앱 레코드를 작성하고 앱을 소스 저장소와 DevOps 도구 체인에 연결할 수 있습니다.
{: shortdesc}

{{site.data.keyword.cloud_notm}} 대시보드 또는 기본 스타터 킷에서 시작할 수 있습니다. 앱에 이름을 지정하고 리소스 그룹을 선택한 후 **고유 코드 가져오기** 시작점을 선택하고 코드가 포함된 Git 저장소 URL을 제공한 다음 **작성**을 클릭하십시오.

기존 DevOps 도구 체인을 연결하거나 새로 작성하고 선택한 배치 대상(예: Kubernetes 또는 Cloud Foundry)에 앱을 지속적으로 제공할 수 있습니다.

## 시작하기 전에
{: #prereqs-byoc}

진행하려면 다음의 전제조건이 준비되어 있는지 확인하십시오.

 * [{{site.data.keyword.dev_cli_long}} 명령행 인터페이스(CLI)](/docs/cli?topic=cloud-cli-getting-started)를 설치하십시오.
 * [좋은 앱의 조건](/docs/apps?topic=creating-apps-best-practice)을 참조하여 앱 작성에 대한 우수 사례를 살펴보십시오.
 * GitHub, GitHub Enterprise, GitLab, BitBucket 또는 Rational 등 제공자의 Git 소스 코드 저장소가 있어야 합니다.
 * [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about)에 앱을 배치하려는 경우에는 [{{site.data.keyword.cloud_notm}} 계정을 준비](/docs/cloud-foundry?topic=cloud-foundry-prepare)해야 합니다.

## 기존 저장소를 사용하여 앱 작성
{: #create-byoc}

앱을 작성하고 이를 소스 저장소와 연결하려면 다음 단계를 완료하십시오.

1. [{{site.data.keyword.cloud_notm}} 콘솔](https://{DomainName}){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")에서 **앱** 타일의 **앱 작성**을 클릭하십시오.
2. 앱의 이름을 지정하고, 리소스 그룹을 선택하고, 앱을 분류하기 위한 태그를 선택적으로 제공하십시오. 자세한 정보는 [태그에 대한 작업](/docs/resources?topic=resources-tag)을 참조하십시오.
3. **자체 코드 가져오기**를 선택하고 Git 저장소에 대해 URL을 제공하십시오. 앱 및 Docker 이미지는 동일한 저장소에 있어야 합니다.
4. **작성**을 클릭하십시오. **앱 세부사항** 페이지가 표시됩니다.
5. 선택사항. 앱에 [서비스를 추가](/docs/apps?topic=creating-apps-add-resource)하십시오.
6. 선택사항. **태그 추가**를 클릭하여 이 앱에 태그를 추가하거나 표시된 태그 옆에 있는 **편집** 아이콘 ![편집 아이콘](../../icons/edit-tagging.svg)을 클릭하여 태그를 편집할 수 있습니다.
7. 선택사항. **저장소 보기**를 클릭하여 저장소를 보십시오.

## 앱 배치
{: #toolchain-byoc}

앱, 도구 체인 및 저장소 간의 링크 설정은 제품 자산 구성의 전 단계입니다. 이는 모든 배치 대상 간의 종속자 서비스 및 실행 중인 앱 인스턴스, DevOps 워크플로우의 소스 보기를 집계하는 데도 도움이 됩니다. 자세한 정보는 [도구 체인 작성](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)을 참조하십시오.

{{site.data.keyword.cloud_notm}} 콘솔 또는 CLI를 사용하여 앱에 지속적 딜리버리를 구성할 수 있습니다.

### 콘솔 사용
{: #console-byoc-toolchain}

#### 앱에 연결하려는 DevOps 도구 체인이 이미 있는 경우 다음 단계를 완료하십시오.

1. **앱 세부사항** 페이지에서 **지속적 딜리버리 구성**을 클릭하십시오. **내 앱 배치** 페이지가 표시됩니다.
2. 앱에 연결할 도구 체인을 선택하고 **배치 사용**을 클릭하십시오. 지속적 딜리버리가 구성되었음을 표시하는 **앱 세부사항** 페이지가 표시됩니다.

#### 이 애플리케이션에 대한 DevOps 도구 체인이 없는 경우 다음 단계를 완료하십시오.

1. **앱 세부사항** 페이지에서 **DevOps 도구 체인 작성**을 클릭하십시오. **도구 체인 작성** 페이지가 표시됩니다.
2. [도구 체인 작성](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).
3. 브라우저 창의 이동 경로를 사용하여 **앱 세부사항** 페이지로 돌아가십시오. 이 페이지에 지속적 딜리버리가 구성되었음이 표시됩니다.

### CLI 사용
{: #cli-byoc-toolchain}

`ibmcloud dev enable` 명령을 사용하여 DevOps 도구 체인이 작성하는 대상에 대한 지시사항 세트로서 저장소로 체크인하는 DevOps 도구 체인 템플리트를 생성할 수 있습니다. 

  1. **앱 세부사항** 페이지에서 **저장소 보기**를 클릭하여 로컬로 코드에 대한 작업을 수행하십시오.
  2. 다음 명령을 실행하십시오.
    
    ```
    ibmcloud dev enable
    ```
   {: codeblock}

앱 배치에 관한 자세한 정보는 [앱 배치](/docs/apps?topic=creating-apps-deploying-apps)를 참조하십시오.

## 앱이 실행 중인지 확인
{: #verify-byoc-app}

Delivery Pipeline 또는 명령행이 사용자를 앱의 URL로 이동시킵니다.

1. DevOps 도구 체인에서 **Delivery Pipeline**을 클릭한 후 **배치 단계**를 선택하십시오.
2. **로그 및 히스토리 보기**를 클릭하십시오.
3. 로그 파일에서 앱의 URL을 찾으십시오. 로그 파일의 끝에서 단어 `urls` 또는 `view`를 찾으십시오. 예를 들면, 로그 파일에서 `urls: my-app-devhost.mybluemix.net` 또는 `View the application health at: http://<ipaddress>:<port>/health`와 같은 행을 볼 수 있습니다.
4. 브라우저에서 해당 URL로 이동하십시오. 앱이 실행 중인 경우에는 `Congratulations` 또는 `{"status":"UP"}`와 같은 항목을 포함하는 메시지가 표시됩니다.

명령행을 사용하는 경우에는 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 명령을 실행하여 기본 브라우저에서 수동으로 배치된 앱의 페이지를 여십시오.
