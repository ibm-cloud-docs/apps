---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-06"

keywords: apps, deploy, deploying apps, toolchain, cli, cloud, devops, deployment, git, push

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 앱 배치
{: #deploying-apps}

DevOps 도구 체인을 사용하여 애플리케이션을 {{site.data.keyword.cloud}}에 배치할 수 있습니다. DevOps 도구 체인을 사용하여 여러 환경으로의 배치를 자동화하고, 앱이 확장됨에 따라 이를 관리하는 데 도움을 주기 위해 신속하게 모니터링, 로깅, 인사이트 및 경보 서비스를 추가할 수 있습니다. {{site.data.keyword.cloud_notm}} 웹 콘솔 또는 명령행 인터페이스(CLI)를 사용하여 앱을 배치하고 지속적 딜리버리를 구성할 수 있습니다.
{: shortdesc}

DevOps 도구 체인에서는 앱의 팀 기반 개발 환경을 제공합니다. 도구 체인을 작성하는 경우 앱 서비스는 소스 코드를 보고, 앱을 복제하여 이슈를 작성하고 관리할 수 있는 Git 저장소를 작성합니다. 또한 전용 Git Lab Lab 환경 및 지속적 Delivery Pipeline에 대한 액세스도 제공됩니다. 이는 사용자가 선택하는 배치 대상([Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 또는 [Virtual Server(VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial))에 맞게 사용자 정의됩니다.

{{site.data.keyword.cloud_notm}} 개발자 대시보드로부터 작성된 모든 도구 체인은 자동 배치로 구성됩니다.
{: note}

## {{site.data.keyword.cloud_notm}} 콘솔 사용
{: deploy-console}

{{site.data.keyword.cloud_notm}}에서는 DevOps 도구 체인을 사용하여 앱을 배치하고 지속적 딜리버리를 구성할 수 있는 웹 콘솔을 제공합니다.

### 시작하기 전에
{: deploy-console-before}

시작하기 전에 [{{site.data.keyword.cloud_notm}} 대시보드](https://{DomainName}){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")를 사용하여 [앱 작성](/docs/apps?topic=creating-apps-tutorial-getting-started#create-getting-started) 및 [서비스 추가](/docs/apps?topic=creating-apps-tutorial-getting-started#resources-getting-started)를 수행하십시오.

### 자동으로 앱 배치
{: deploy-console-auto}

1. **앱 세부사항** 페이지에서 **지속적 딜리버리 구성**을 클릭하십시오.
2. 배치 대상을 선택하십시오. 선택하는 대상의 지시사항에 따라 배치 대상을 설정하십시오.
  * **IBM Kubernetes Service에 배치**합니다. 이 선택사항은 고가용성의 애플리케이션 컨테이너를 배치하고 관리하기 위해 작업자 노드라는 호스트 클러스터를 작성합니다. 클러스터를 작성하거나 기존 클러스터에 배치할 수 있습니다. 자세한 정보는 [Kubernetes 클러스터에 앱 배치](/docs/containers?topic=containers-app)를 참조하십시오.
  * **Cloud Foundry에 배치**합니다. 이 선택사항은 기본 인프라를 관리할 필요 없이 클라우드 기본 앱을 배치할 수 있도록 합니다. 계정에 {{site.data.keyword.cfee_full_notm}}에 대한 액세스 권한이 있는 경우에는 **퍼블릭 클라우드** 배치자 유형을 선택하거나, 사용자 엔터프라이즈 전용으로 Cloud Foundry 애플리케이션을 호스팅하는 격리된 환경을 생성하고 관리하는 데 사용할 수 있는 **엔터프라이즈 환경** 배치자 유형을 선택할 수 있습니다. 자세한 정보는 [Cloud Foundry 퍼블릭에 앱 배치](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps) 및 [{{site.data.keyword.cfee_full_notm}}에 앱 배치](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)를 참조하십시오.
  * **Virtual Server에 배치**합니다. 이 선택사항은 가상 서버를 프로비저닝하고, 앱을 포함하는 이미지를 로드하고, DevOps 도구 체인을 작성하고 첫 번째 배치 사이클을 시작합니다. 자세한 정보는 [가상 서버에 앱 배치](/docs/apps?topic=creating-apps-vsi-deploy)를 참조하십시오.

### 수동으로 앱 배치
{: deploy-console-manual}

도구 체인이 적절히 구성되면 저장소의 마스터 분기에 대한 각 병합마다 빌드-배치 주기가 자동으로 시작됩니다. 

DevOps 도구 체인에서 수동으로 앱을 배치할 수도 있습니다.

1. **앱 세부사항** 페이지에서 **도구 체인 보기**를 클릭하십시오.
2. 빌드를 시작하고 배치를 관리하며 로그 및 히스토리를 볼 수 있는 **Delivery Pipeline**을 클릭하십시오.

지속적 딜리버리는 일부 애플리케이션의 경우 자동으로 사용으로 설정됩니다. Delivery Pipeline 및 GitHub를 통해 빌드, 테스트 및 배치를 자동화하기 위해 지속적 딜리버리를 사용으로 설정할 수 있습니다.

자세한 정보는 다음을 참조하십시오.
* [빌드 및 배치](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)
* [도구 체인 작성](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)

## {{site.data.keyword.dev_cli_short}} CLI 사용
{: #deploy-cli}

{{site.data.keyword.cloud_notm}}에서는 개발자의 워크플로우를 간소화하기 위해 견고한 CLI 및 플러그인을 제공합니다. 앱이 구성된 방법에 따라 두 가지 방법 중 하나로 {{site.data.keyword.cloud_notm}} 앱을 배치할 수 있습니다.

### 시작하기 전에
{: #deploy-cli-before}

시작하기 전에 [{{site.data.keyword.cloud_notm}} CLI를 다운로드 및 설치](/docs/cli?topic=cloud-cli-ibmcloud-cli)하십시오.

CLI는 Cygwin에 의해 지원되지 않습니다. Cygwin 명령행 창 이외의 창에서 도구를 사용하십시오.
{: important}

  1. 앱에 대한 코드를 새 디렉토리에 다운로드하여 개발 환경을 설정하십시오.

  2. 코드가 있는 디렉토리로 변경하십시오.

  3.  앱 코드를 업데이트하십시오. {{site.data.keyword.cloud_notm}} 샘플 애플리케이션을 사용 중이며 사용자 앱에 `src/main/webapp/index.html` 파일이 포함되어 있는 경우에는 이를 수정하여 `Thanks for creating ...` 행을 편집할 수 있습니다. 앱을 {{site.data.keyword.cloud_notm}}에 배치하기 전에 로컬에서 실행되는지 확인하십시오.

    `manifest.yml` 파일에 주의하십시오. 앱을 {{site.data.keyword.cloud_notm}}에 배치할 때 이 파일이 애플리케이션의 URL, 메모리 할당, 인스턴스 수 및 기타 중요한 매개변수 판별에 사용됩니다.

    또한 빌드 지시사항 등의 세부사항이 포함되어 있는 `README.md` 파일을 검토하십시오.

    애플리케이션이 Liberty 앱인 경우에는 다시 배치하기 전에 우선 이를 빌드해야 합니다.
    {: note}

  4. IBM ID를 사용하여 {{site.data.keyword.cloud_notm}} CLI에 로그인하십시오. 여러 계정이 있는 경우 사용할 계정을 선택하도록 프롬프트가 표시됩니다. `-r` 플래그로 지역을 지정하지 않은 경우, 지역도 선택해야 합니다.
    ```
ibmcloud login
    ```
    {: codeblock}
  
    인증 정보가 거부되는 경우 연합 ID를 사용 중일 수 있습니다. 연합 ID로 로그인하려면 `--sso` 플래그를 사용하십시오. 자세한 정보는 [연합 ID로 로그인](/docs/iam/federated_id?topic=iam-federated_id#federated_id)을 참조하십시오.
    {: tip}

### 자동으로 앱 배치
{: #deploy-cli-auto}

앱의 DevOps 도구 체인을 아직 작성하지 않았으며 앱이 아직 Git 저장소에 없는 경우에는 [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit) 명령을 실행할 수 있습니다. "DevOps 구성"에 대한 프롬프트에 따라 새 도구 체인에 배치(하고 새 GitLab 저장소를 작성)하십시오.

앱에 대한 DevOps 도구 체인을 작성하고 나면 새 빌드 배치는 코드를 커미트하고 이를 도구 체인의 저장소에 푸시하는 것처럼 단순합니다. 

1. 커미트할 변경사항을 준비합니다.
    ```
    git add .
    ```
2. 간략한 메시지로 변경사항을 커미트하십시오.
    ```
    git commit -m "made changes"
    ```
3. 마스터 분기의 커미트를 원격 저장소에 푸시하십시오.
    ```
    git push origin master
    ```
4. {{site.data.keyword.cloud_notm}} 콘솔에서 앱에 대한 DevOps 도구 체인을 보십시오. 앱 디렉토리에서 [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) 명령을 실행하여 {{site.data.keyword.cloud_notm}} 콘솔의 **앱 세부사항** 페이지에서 도구 체인 세부사항을 볼 수 있습니다.
5. 도구 체인 내의 파이프라인을 보고 새 빌드가 시작되었는지 확인하십시오.

### 수동으로 앱 배치
{: #deploy-cli-manual}

[`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) 명령을 사용하여 {{site.data.keyword.cloud_notm}}에 앱을 수동으로 배치할 수 있습니다.

  ```
    ibmcloud dev deploy <APP_NAME>
  ```
  {: codeblock}

### 관련 정보
{: #deploy-cli-related}

CLI를 사용하여 {{site.data.keyword.cloud_notm}}에 앱을 배치하는 데 관한 자세한 정보는 다음을 참조하십시오.

* [{{site.data.keyword.dev_cli_short}} CLI](https://www.ibm.com/blogs/bluemix/2019/01/deploying-to-ibm-cloud-environments-with-ibm-cloud-developer-tools-cli/){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")로 IBM Cloud Environment에 배치