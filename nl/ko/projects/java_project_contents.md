---

copyright:
  years: 2015, 2018
lastupdated: "2018-05-22"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Java 앱 파일
{: #java-project-files}

Java 앱의 경우, 다음 정보는 일반적으로 {{site.data.keyword.Bluemix}}에서 볼 수 있는 항목의 인벤토리입니다. 스타터 킷을 작성하면 이러한 파일이 사용자를 위해 작성됩니다. 앱을 {{site.data.keyword.Bluemix_notm}} 내의 호스트로 마이그레이션하는 경우에는 잠재적 충돌을 방지하기 위해 이 정보를 검토할 수 있습니다. 
{:shortdesc}

## Spring
{: #spring-project-files}

다음 표에는 생성된 Java Spring 앱에 포함되는 디렉토리 및 파일이 나열되어 있습니다.

| `./` 디렉토리                                  | 설명                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | Maven pom 파일 |
| cli-config.yml | CLI 구성 옵션 |
| manifest.yml | Cloud Foundry 배치 파일 |
| Dockerfile | `ibmcloud dev run`, `ibmcloud dev deploy` 및 `docker` 명령에 대한 Dockerfile|
| Dockerfile-tools | `ibmcloud dev build` 및 `ibmcloud dev test`에 대한 Dockerfile |
| LICENSE | 라이센스 파일 |
| README.md | 앱 설명 |
{: caption="표 1. 생성된 Java Spring 앱 루트 디렉토리의 컨텐츠" caption-side="top"}

| `./src/main/java/` 디렉토리 | 설명                       |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/test/application/SBApplication.java` | 기본 Spring 애플리케이션 |
| `./src/main/test/application/HealthEndpointTest.java` | 테스트 |
| `./src/main/java/application/rest/HealthApplication.java` | 상태 엔드포인트 |
| `./src/main/java/application/rest/v1/Example.java` | 코드 예 |
| `./src/main/java/resources/application-local.properties` | Spring 특성 |
{: caption="표 2. 생성된 Java Spring 앱 /java/ 디렉토리의 컨텐츠" caption-side="top"}

| `./.bluemix/` 디렉토리 | 설명 |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | 컨테이너 빌드 스크립트 |
| deploy.json | 배치 정보 |
| kube_deploy.sh | Kubernetes 배치 스크립트 |
| pipeline.yml | IBM Cloud 파이프라인 정의 |
| toolchain.yml | IBM Cloud 도구 체인 정의 |
{: caption="표 3. 생성된 Java Spring 앱 ./.bluemix/ 디렉토리의 컨텐츠" caption-side="top"}

| `./chart/<projectname>/` 디렉토리 | 설명 |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm 차트 |
| `./chart/<projectname>/values.yaml` | Helm 차트 값 |
| `./chart/<projectname>/templates/deployment.yaml` | 배치 템플리트 |
| `./chart/<projectname>/templates/hpa.yaml` | HPA 템플리트 |
| `./chart/<projectname>/templates/service.yaml` | 서비스 템플리트 |
{: caption="표 4. 생성된 Java Spring 앱 ./chart/<projectname/templates/ 디렉토리의 컨텐츠" caption-side="top"}

| `./manifests/` 디렉토리 | 설명 |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Kubernetes 서비스 및 배치 yaml |
{: caption="표 5. 생성된 Java Spring 앱 ./manifests/ 디렉토리의 컨텐츠" caption-side="top"}

## Liberty
{: #liberty-project-files}

다음 표에는 생성된 Java Liberty 앱에 포함되는 디렉토리 및 파일이 나열되어 있습니다.

| `./` 디렉토리                                  | 설명                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | Maven pom 파일 |
| cli-config.yml | CLI 구성 옵션 |
| manifest.yml | Cloud Foundry 배치 파일 |
| Dockerfile | `ibmcloud dev run`, `ibmcloud dev deploy` 및 `docker` 명령에 대한 Dockerfile|
| Dockerfile-tools | `ibmcloud dev build` 및 `ibmcloud dev test` 명령에 대한 Dockerfile |
| LICENSE | 라이센스 파일 |
| README.md | 앱 설명 |
{: caption="표 6. 생성된 Java Liberty 앱 루트 디렉토리의 컨텐츠" caption-side="top"}

| `./src/main` 디렉토리 | 설명 |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/java/application/rest/HealthApplication.java` | 상태 엔드포인트 |
| `./src/main/java/application/rest/v1/Example.java` | 코드 예 |
| `./src/main/liberty/config/jvm.options` | JVM 옵션 |
| `./src/main/liberty/config/jvmbx.options` | Java 메트릭 에이전트 구성 |
| `./src/main/liberty/config/server.env` | 환경 변수 |
| `./src/main/liberty/config/server.xml` | 서버 구성 |
| `./src/main/webapp/WEB-INF/beans.xml` | CDI Bean 구성 |
| `./src/main/webapp/WEB-INF/ibm-web-ext.xml` | IBM 웹 앱 구성 |
| `./src/main/test/it/HealthEndpointTest.java` | 테스트 |
{: caption="표 7. 생성된 Java Liberty 앱 ./src/main/ 디렉토리의 컨텐츠" caption-side="top"}

| `./.bluemix/` 디렉토리 | 설명 |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | 컨테이너 빌드 스크립트 |
| deploy.json | 배치 정보 |
| kube_deploy.sh | Kubernetes 배치 스크립트 |
| pipeline.yml | IBM Cloud 파이프라인 정의 |
| toolchain.yml | IBM Cloud 도구 체인 정의 |
{: caption="표 8. 생성된 Java Liberty 앱 ./bluemix/ 디렉토리의 컨텐츠" caption-side="top"}

| `./chart/<projectname>/` 디렉토리 | 설명 |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm 차트 |
| `./chart/<projectname>/values.yaml` | Helm 차트 값 |
| `./chart/<projectname>/templates/deployment.yaml` | 배치 템플리트 |
| `./chart/<projectname>/templates/hpa.yaml` | HPA 템플리트 |
| `./chart/<projectname>/templates/service.yaml` | 서비스 템플리트 |
{: caption="표 9. 생성된 Java Liberty 앱 ./chart/<projectname/ 디렉토리의 컨텐츠" caption-side="top"}

| `./manifests/` 디렉토리 | 설명 |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Kubernetes 서비스 및 배치 yaml |
{: caption="표 10. 생성된 Java Liberty 앱 ./manifests/ 디렉토리의 컨텐츠" caption-side="top"}
