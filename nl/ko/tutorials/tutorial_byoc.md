---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# 자체 코드 저장소에서 앱 작성
{: #tutorial-byoc}

기존 애플리케이션 저장소를 사용하여 {{site.data.keyword.cloud}}에서 애플리케이션을 작성할 수 있습니다. 단지 애플리케이션 작성 중에 저장소에 대한 웹 링크를 제공하고 리소스 계속 추가를 후에 배치를 위해 애플리케이션에 DevOps 도구 체인을 연결하십시오.
{: shortdesc}

## 시작하기 전에
{: #prereqs-byoc}

진행하려면 다음의 전제조건이 준비되어 있는지 확인하십시오.

 * [{{site.data.keyword.dev_cli_long}} 명령행 인터페이스(CLI)](/docs/cli/index.html#overview)를 설치하십시오.
 * [좋은 앱의 조건](/docs/apps/best-practice.html#best-practice)을 참조하여 앱 작성에 대한 우수 사례를 살펴보십시오.
 * GitHub, GitHub Enterprise, GitLab, BitBucket 또는 Rational 등 제공자의 Git 소스 코드 저장소가 있어야 합니다.
 * [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about)에 앱을 배치하려는 경우에는 [{{site.data.keyword.cloud_notm}} 계정을 준비](/docs/cloud-foundry/prepare-account.html#prepare)해야 합니다. 

## 1단계. 기존 저장소에서 앱 작성
{: #create-byoc}

앱을 작성하고 이를 소스 저장소와 연결하려면 다음 단계를 완료하십시오.

1. [대시보드 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}){: new_window}에서 **앱** 타일의 **앱 작성**을 클릭하십시오.
2. 앱의 이름을 지정하고, 리소스 그룹을 선택하고, 앱을 분류하기 위한 태그를 선택적으로 제공하십시오. 자세한 정보는 [태그에 대한 작업](/docs/resources/tagging_resources.html#tag)을 참조하십시오.
3. **자체 코드 가져오기**를 선택하고 Git 저장소에 대해 URL을 제공하십시오. 앱 및 Docker 이미지는 동일한 저장소에 있어야 합니다.
4. **작성**을 클릭하십시오.

**앱 세부사항** 페이지가 표시됩니다. 여기에서 다음을 수행할 수 있습니다.
* [리소스를 추가하십시오](/docs/apps/reqnsi.html#add-resource)(선택사항).
* 앱을 작성할 때 태그를 제공한 경우에는 표시된 태그 옆에 있는 **편집** 아이콘 ![편집 아이콘](../../icons/edit-tagging.svg)을 클릭하여 이를 편집할 수 있습니다. 
* **DevOps 도구 체인에 연결**을 클릭하여 DevOps 도구 체인에 앱을 연결하십시오. 아직 도구 체인이 없으면 **DevOps 도구 체인 연결** 페이지가 열립니다. **DevOps 도구 체인 작성**을 클릭하십시오. 해당 시점에서 [DevOps 대시보드](https://{DomainName}/devops/)의 [도구 체인 작성](https://{DomainName}/devops/create) 페이지가 브라우저의 새 탭에서 열립니다. 해당 탭에서 도구 체인을 작성하고 구성한 후에는 앱의 **도구 체인 연결** 페이지로 되돌아가서 페이지를 새로 고쳐야 합니다.
* **저장소 보기**를 클릭하여 저장소를 보십시오.
* **앱 세부사항** 페이지에서 관련 링크를 클릭하여 도구 체인 또는 앱 작성 환경에 대해 자세히 알아보십시오.

## 2단계. DevOps 도구 체인에 앱 연결
{: #toolchain-byoc}

앱, 도구 체인 및 저장소 간의 링크 설정은 제품 자산 구성의 전 단계입니다. 이는 모든 배치 대상 간의 종속자 서비스 및 실행 중인 앱 인스턴스, DevOps 워크플로우의 소스 보기를 집계하는 데도 도움이 됩니다. 자세한 정보는 [도구 체인 작성](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started)을 참조하십시오.

{{site.data.keyword.cloud_notm}} 콘솔 또는 CLI를 사용하여 DevOps 도구 체인에 앱을 연결할 수 있습니다.

### 콘솔 사용
{: #console-byoc-toolchain}

  1. **DevOps 도구 체인에 연결**을 클릭하여 DevOps 도구 체인에 앱을 연결하십시오. 
  
    기존 도구 체인이 없으면 **DevOps 도구 체인 작성**을 클릭하십시오. 
    
  2. 도구 체인을 작성하고 구성한 후에는 앱의 도구 체인 연결 페이지로 되돌아가서 페이지를 새로 고치십시오. 

### CLI 사용

`ibmcloud dev enable` 명령을 사용하여 DevOps 도구 체인이 작성하는 대상에 대한 지시사항 세트로서 저장소로 체크인하는 DevOps 도구 체인 템플리트를 생성할 수 있습니다.  

  1. 앱 서비스 창에서 **코드 다운로드** 또는 **저장소 복제**를 클릭하여 로컬로 코드 관련 작업을 수행하십시오.
  2. 다음 명령을 실행하십시오.
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

자세한 정보는 [CLI를 사용하여 앱 작성 및 배치](/docs/apps/create-deploy-cli.html#create-deploy-app-cli)를 참조하십시오.

## 3단계. 앱 배치
{: #deploy-byoc}

DevOps 도구 체인을 앱에 연결한 후에는 다음 단계를 완료하여 이를 {{site.data.keyword.cloud_notm}}에 배치하십시오. 

1. 앱 세부사항 페이지에서 **클라우드에 배치**를 클릭하십시오. 
2. 배치 방법을 선택하십시오. 선택하는 방법의 지시사항에 따라 배치 방법을 선택하십시오.
  * **[Kubernetes에 배치](/docs/apps/deploying/containers.html#containers)**합니다. 이 선택사항은 고가용성의 애플리케이션 컨테이너를 배치하고 관리하기 위해 작업자 노드라는 호스트 클러스터를 작성합니다. 클러스터를 작성하여 배치하거나 기존 클러스터에 배치할 수 있습니다.
  * **Cloud Foundry에 배치**합니다. 이 선택사항은 기본 인프라를 관리할 필요 없이 클라우드 기본 앱을 배치할 수 있도록 합니다. 계정에 {{site.data.keyword.cfee_full_notm}}에 대한 액세스 권한이 있는 경우에는 **[퍼블릭 클라우드](/docs/cloud-foundry-public/about-cf.html#about-cf)** 배치자 유형을 선택하거나, 사용자 엔터프라이즈 전용으로 Cloud Foundry 애플리케이션을 호스팅하는 격리된 환경을 작성하고 관리하는 데 사용할 수 있는 **[엔터프라이즈 환경](/docs/cloud-foundry-public/cfee.html#cfee)** 배치자 유형을 선택할 수 있습니다. 
  * **[Virtual Server](/docs/apps/vsi-deploy.html#vsi-deploy)에 배치**합니다. 이 선택사항은 가상 서버를 프로비저닝하고, 앱을 포함하는 이미지를 로드하고, DevOps 도구 체인을 작성하고 첫 번째 배치 사이클을 시작합니다. 


