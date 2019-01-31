---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-03"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Kubernetes 클러스터에 자체 코드 배치
{: #tutorial}

기존 앱 저장소를 사용하여 {{site.data.keyword.cloud}}에서 앱을 작성하는 방법에 대해 알아봅니다. 기존 DevOps 도구 체인을 연결하거나 새로 하나를 작성하고 Kubernetes 클러스터의 보안 컨테이너에 앱을 지속적으로 전달할 수 있습니다. 이 튜토리얼은 변경사항이 자동으로 빌드되어 Kubernetes 클러스터의 배치된 앱에 항상 전파될 수 있도록 지속적 통합 DevOps 파이프라인을 설정하는 데 도움을 줍니다.
{: shortdesc}

작업 중인 백엔드 애플리케이션에 대한 코드 베이스의 소스 코드 저장소가 이미 있는 경우, {{site.data.keyword.cloud_notm}}에서는 전체 제품 범위를 구성하는 모든 자산의 집계 보기로 이 자산을 구성하는 데 도움을 줍니다. {{site.data.keyword.cloud_notm}}에서는 사용자가 DevOps 도구 체인 기능을 사용할 때 확장 가능한 DevOps 워크플로우에서 시작하고 실행할 수 있도록 합니다. 이 튜토리얼은 모두 클라우드 우수 사례의 안내에 따라 경험이 풍부한 개발자나 DevOps 엔지니어가 대상 {{site.data.keyword.cloud_notm}} Kubernetes 클러스터를 확보 및 구성하고 DevOps 도구 체인을 구성 및 실행하도록 도움을 줍니다.

_클러스터_는 앱의 고가용성을 유지하는 리소스, 작업자 노드, 네트워크 및 스토리지 디바이스 세트입니다. 클러스터가 작성되면 컨테이너에 앱을 배치할 수 있습니다.
{: tip}

## 시작하기 전에
{: #prereqs}

* 앱을 작성하십시오. 자세한 정보는 [자체 코드 저장소에서 앱 작성](/docs/apps/tutorials/tutorial_byoc.html)을 참조하십시오. 
* [{{site.data.keyword.cloud_notm}} 콘솔 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://{DomainName}){: new_window}에서 **메뉴** 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg)을 클릭하고 [Kubernetes 클러스터 구성](/docs/containers/container_index.html)을 위한 **컨테이너**를 선택하십시오. 
* 앱이 Docker에서 실행 중인지 확인하려면 다음 명령을 실행하십시오.
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install`
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* 그리고 `http://localhost/springboothelloworld/sayhello` 등의 URL로 이동하십시오. Ctrl+C 키를 눌러서 Docker 실행을 중지하십시오.  

## 앱에 리소스 추가(선택사항)
{: #add_resources}

애플리케이션에 서비스 리소스를 추가하면 {{site.data.keyword.cloud_notm}}에서 서비스를 작성합니다. 프로비저닝 프로세스는 서로 다른 유형의 서비스마다 서로 다를 수 있습니다. 예를 들어, 데이터베이스 서비스는 데이터베이스를 작성하고, 모바일 애플리케이션의 푸시 알림 서비스는 구성 정보를 생성합니다. {{site.data.keyword.cloud_notm}}에서는 서비스 인스턴스를 사용하여 애플리케이션에 서비스 리소스를 제공합니다. 서비스 인스턴스는 웹 애플리케이션 간에 공유할 수 있습니다.

이 프로세스는 서비스 인스턴스를 프로비저닝하고 리소스 키(인증 정보)를 작성하며 이를 앱에 바인드합니다. 자세한 정보는 [앱에 서비스 추가](/docs/apps/reqnsi.html)를 참조하십시오.

앱에 서비스 리소스를 추가한 후에는 서비스에 대한 인증 정보를 배치 환경에 복사해야 합니다. 자세한 정보는 [Kubernetes 환경에 인증 정보 추가](/docs/apps/creds_kube.html)를 참조하십시오. 

## 배치를 위한 앱 준비
{: #connect_toolchain}

이 단계에서는 애플리케이션에 DevOps 도구 체인을 연결하고 {{site.data.keyword.cloud_notm}} Kubernetes 서비스에서 호스팅된 Kubernetes 클러스터에 배치되도록 이를 구성합니다.

DevOps 도구 체인은 쉘 스크립트 실행의 임의 단계의 관리적 실행을 허용할 만큼 충분히 탄력적입니다. 즉, 사용자는 DevOps 도구 체인으로 거의 모든 작업을 수행할 수 있습니다. 이 절의 범위는 스케일링된 DevOps 및 클라우드 우수 사례의 "미래 사용 보장(future-proofing)"을 염두에 두고 Kubernetes 클러스터의 앱 배치에 초점을 맞춥니다.

앱, 도구 체인 및 저장소 간의 링크 설정은 제품 자산 구성의 전 단계입니다. 이는 모든 배치 대상 간의 종속자 서비스 및 실행 중인 앱 인스턴스, DevOps 워크플로우의 소스 저장소 보기를 집계하는 데도 도움이 됩니다.

도구 체인 연결 페이지에는 일부 옵션이 있습니다. 

* 기존 도구 체인에 앱을 연결합니다.
* 저장소가 없는 기존 도구 체인에 앱을 연결합니다. 그리고 나중에 저장소에 도구 체인을 연결합니다.
* 새 도구 체인에 앱을 연결합니다.

### 기존 도구 체인에 앱 연결
{: #connect_toolchain_repo}

앱 작성 중에 지정된 Git 저장소에 이미 하나 이상의 DevOps 도구 체인이 연결되어 있는 경우, 해당 도구 체인은 **저장소 있음** 테이블에 표시됩니다. 도구 체인은 앱에서 정의된 동일 저장소에서 소스를 검색하도록 구성되어야 합니다. 앱에 연결하기 위해 해당 도구 체인 중 하나를 선택하고자 할 가능성이 가장 큽니다.

### 저장소가 없는 기존 도구 체인에 앱 연결
{: #connect_toolchain_notrepo}

계정과 연관된 하나 이상의 DevOps 도구 체인이 있지만 앱 작성 중에 지정된 Git 저장소에 연결되어 있지 않은 경우, 해당 도구 체인은 **저장소 없음** 테이블에 표시됩니다. 해당 도구 체인 중 하나를 선택하고 이를 앱에 연결할 수 있지만, 해당 도구 체인에 저장소 수동 추가도 수행해야 합니다.

저장소를 도구 체인에 추가하는 데 대한 자세한 정보는 다음을 참조하십시오.

 * [Git 저장소 및 문제 추적 구성](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitbluemix)
 * [GitHub 구성](/docs/services/ContinuousDelivery/toolchains_integrations.html#github)
 * [GitLab 구성](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitlab)


### 새 도구 체인에 앱 연결
{: #create_toolchain}

코드 저장소의 변경 없이 DevOps 도구 체인의 작성을 완전히 제어하려면 처음부터 도구 체인을 작성하십시오. 또한 앱을 빌드하고 이를 Kubernetes 클러스터에 배치할 수 있도록 모든 통합을 작성하십시오. 

1. 도구 체인 작성 페이지에서 **자체 도구 체인 빌드** 템플리트를 클릭하십시오. 
2. 도구 체인의 이름을 입력하고 지역 및 리소스 그룹(기본값)을 선택한 후에 **작성**을 클릭하십시오. 

새 앱에서 도구 체인 작성을 선택하는 경우에는 DevOps 대시보드의 [도구 체인 작성](https://{DomainName}/devops/create) 페이지가 브라우저의 새 탭에서 열립니다. 해당 탭에서 도구 체인을 작성하고 구성한 후에는 앱의 도구 체인 연결 페이지로 되돌아가서 페이지를 새로 고쳐야 합니다.
{:tip}

처음부터 DevOps 도구 체인 작성을 원하지 않으면 [`ibmcloud dev enable` 명령](/docs/cli/idt/commands.html#enable)을 사용하여 기존 코드를 클라우드-사용으로 설정할 수 있습니다. 이 명령은 저장소로 가져오는 DevOps 도구 체인 템플리트를 생성합니다. 그러면 해당 템플리트를 DevOps 도구 체인이 무엇을 작성하는지에 대한 지시사항 세트로서 사용하십시오. 자세한 정보는 [CLI 문서](/docs/apps/create-deploy-cli.html#byoc)를 참조하십시오.

## GitHub 통합 추가

해당 저장소의 가져오기 요청과 코드 푸시가 도구 체인에 POST를 전송할 수 있게, 도구 체인이 저장소의 웹훅을 설정하도록 GitHub 저장소에 대한 통합으로 DevOps 도구 체인을 구성하십시오.  

1. DevOps 도구 체인 템플리트에서 **도구 추가**를 클릭하십시오.
2. 저장소가 공용 GitHub 또는 Enterprise GitHub에 있는 경우에는 **GitHub**를 선택하십시오. 
3. GitHub 서버 URL을 선택하거나 입력하십시오. 
4. `Unauthorized on GitHub` 메시지가 표시될 수 있습니다. 이 경우에는 **권한 부여**를 클릭하십시오. 그리고 IBM Cloud 도구 체인 권한 부여 페이지에서 **IBM Cloud 권한 부여**를 클릭하고 GitHub 비밀번호를 입력하십시오. 
5. DevOps 도구 체인이 웹훅으로 저장소를 구성하고 저장소의 사본 또는 분기를 작성하지 않도록, 통합 구성 페이지에서 저장소 유형에 대해 **기존**을 선택하십시오. 
6. 저장소 URL(예: `https://github.com/yourrepo/spring-boot-hello-world`)을 입력하십시오. 
7. 잠시 후에 도구 체인의 트리거에 필요한 웹훅으로 저장소를 구성하는 GitHub ReST API를 사용할 수 있도록 DevOps 도구 체인 권한을 부여하기 위한 GitHub 권한 부여에 대한 프롬프트가 표시될 수 있습니다. 
8.  **통합 작성**을 클릭하십시오.

저장소 설정에서 새 웹훅을 볼 수 있습니다. 

## Delivery Pipeline 추가

1. **도구에 추가**를 클릭하십시오.
2. **Delivery Pipeline**을 선택하십시오.
3. 파이프라인 이름에 대해 `Continuous Integration`을 입력하고 **통합 작성**을 클릭하십시오. 

## 파이프라인 단계 구성

입력(GitHub 저장소 컨텐츠)이 올바른 대상을 지시하도록 파이프라인 단계를 구성하십시오. 작업 중인 Docker 이미지를 생성하고 IBM Containers Kubernetes 클러스터를 대상으로 지정하는 GitHub 저장소가 있다고 이 튜토리얼에서 가정하므로, 사용자는 이 목표를 달성하는 입력, 쉘 스크립트 및 출력의 파이프라인 단계를 작성합니다.

1. `build and publish` 파이프라인 단계를 구성하십시오. 
  1. 클릭한 Delivery Pipeline을 선택하고 **단계 추가**를 클릭하십시오. 
  2. **입력** 탭을 클릭하고 다음과 같이 필드를 채우십시오. 
    * 단계 이름에 대해 `build and publish Docker image`를 입력하십시오. 
    * 입력 유형에 대해 **Git 저장소**를 선택하십시오. 
    * GitHub 저장소를 선택하십시오. 
    * 지속적 통합에 사용하는 분기를 선택하십시오. 
  3.  **작업** 탭을 클릭한 후에 **작업 추가 '+'**를 클릭하고 다음과 같이 필드를 채우십시오. 
    * 작업 유형에 대해 **빌드**를 선택하십시오. 
    * 이름에 대해 `build and publish`를 입력하십시오. 
    * 빌더 유형에 대해 **컨테이너 레지스트리**를 선택하십시오. 
    * Kubernetes 클러스터가 있는 지역을 선택하십시오. 
    * **기존 API 키 입력**을 선택하십시오. API 키가 없으면 [API 키 작성](/docs/iam/userid_keys.html#creating-an-api-key)을 참조하십시오.  
    * 컨테이너 레지스트리 네임스페이스를 입력하십시오. 이는 **메뉴** 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg)을 클릭하고 **컨테이너** > **레지스트리** > **네임스페이스**를 선택하여 찾을 수 있습니다. 
    * 이 파이프라인 빌드 단계가 저장소의 지속적 통합 분기의 지속적 빌드에 대한 단계이므로, Docker 이미지 이름에 대해 `continuous`를 입력하십시오. 
    * 첫 번째 `#!/bin/bash` 행 이후에 1개 이상의 행을 추가하여 빌드 스크립트를 편집하십시오. 예를 들어, maven을 사용하여 빌드된 저장소의 경우에는 다음 예와 유사한 몇 개의 행을 추가할 수 있습니다.

      ```bash
      export JAVA_HOME=/opt/IBM/java8
      # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
      export MAVEN_OPTS="-  
      Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
      mvn -B clean verify
      ```
      {: codeblock}
  4. **저장**을 클릭하십시오. 
2. 빌드가 성공할 때까지 **재생** 아이콘을 클릭하여 `build and publish` 파이프라인 단계를 테스트하십시오. 초록색의 단계는 빌드가 성공했음을 표시합니다.  
3. Docker 이미지를 Kubernetes 클러스터에 배치하도록 `deploy to cluster` 파이프라인 단계를 구성하십시오.  
  1. Delivery Pipeline 페이지에서 **단계 추가**를 클릭하십시오.
  2. **입력** 탭을 클릭하고 다음과 같이 필드를 채우십시오. 
    * 이름에 대해 `deploy to cluster`를 입력하십시오. 
    * 입력 유형에 대해 **아티팩트 빌드**를 선택하십시오. 
    * 단계에 대해 **Docker 이미지 빌드 및 공개**를 선택하십시오. 
    * 작업에 대해 **빌드 및 공개**를 선택하십시오. 
    * 이는 지속적 통합 파이프라인입니다. 따라서 단계 트리거에 대해 기본 옵션을 수락하십시오. 
  3. **작업** 탭을 클릭한 후에 **작업 추가 '+'**를 클릭하고 다음과 같이 필드를 채우십시오. 
    * 이름에 대해 `deploy to continuous integration cluster`를 입력하십시오. 
    * 배치자 유형에 대해 **Kubernetes**를 선택하십시오. 
    * Kubernetes 클러스터가 있는 지역을 선택하십시오. 
    * 기존 API 키를 입력하십시오.  
  4. **저장**을 클릭하십시오.
4. 빌드가 성공할 때까지 **재생** 아이콘을 클릭하여 `deploy to cluster` 파이프라인 단계를 테스트하십시오. 초록색의 단계는 빌드가 성공했음을 표시합니다. 로그에서 단계를 볼 수 있습니다. 로그의 끝 부분에서 실행 중인 앱에 대한 클릭 가능한 링크를 찾으십시오. 앱에 대한 올바른 경로를 추가하여 이의 실행을 확인하십시오. 
