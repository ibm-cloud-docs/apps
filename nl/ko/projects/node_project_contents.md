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

# Node.js 앱 파일
{: #node-project-files}

Node.js 앱의 경우, 다음 정보는 일반적으로 {{site.data.keyword.Bluemix}}에서 볼 수 있는 항목의 인벤토리입니다. 스타터 킷을 작성하면 이러한 파일이 사용자를 위해 작성됩니다. 앱을 {{site.data.keyword.Bluemix_notm}} 내의 호스트로 마이그레이션하는 경우에는 잠재적 충돌을 방지하기 위해 이 정보를 검토할 수 있습니다. 
{:shortdesc}

다음 표에는 생성된 Node.js 앱에 포함되는 공통 디렉토리 및 파일이 나열되어 있습니다.

| 루트 디렉토리                                     | 설명                       |
|:------------------------------------------------|:------------------------------------------|
|package.json | 메타데이터 파일 |
|cli-config.yml | CLI 구성 옵션 |
|manifest.yml | Cloud Foundry 배치 파일 |
|Dockerfile | `ibmcloud dev run`, `ibmcloud dev deploy` 및 `docker` 명령에 대한 Dockerfile|
|Dockerfile-tools | `ibmcloud dev build` 및 `ibmcloud dev test`에 대한 Dockerfile |
|docker-compose.yml | Docker Compose에 대한 앱 서비스 구성 |
|webpack.config.js | 빌드 관련 정보에 대한 webpack 구성 |
| LICENSE | 라이센스 파일 |
|README.md | 앱 설명 |
{: caption="표 1. 생성된 Node.js 앱 루트 디렉토리의 컨텐츠" caption-side="top"}

| `./public/` 디렉토리 | 설명 |
|:------------------------------------------------|:------------------------------------------|
| `./public/swagger.yml` | REST API 설명을 위한 Swagger 스펙 |
| `./public/index.html` | 웹 애플리케이션에 대한 스켈레톤 마크업 |
|`./public/server/server.js` | 서버 구현 파일 |
{: caption="표 2. 생성된 Node.js 앱 public 디렉토리의 컨텐츠" caption-side="top"}

| `./test/` 디렉토리 | 설명 |
|:------------------------------------------------|:------------------------------------------|
| test-server.js | Express Server에 대한 통합 테스트 |
{: caption="표 3. 생성된 Node.js 앱 test 디렉토리의 컨텐츠" caption-side="top"}

| `./.bluemix/` 디렉토리 | 설명 |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | 컨테이너 빌드 스크립트 |
| deploy.json | 배치 정보 |
| kube_deploy.sh | Kubernetes 배치 스크립트 |
| pipeline.yml | IBM Cloud 파이프라인 정의 |
| toolchain.yml | IBM Cloud 도구 체인 정의 |
{: caption="표 4. 생성된 Node.js 앱 .bluemix 디렉토리의 컨텐츠" caption-side="top"}

| `./chart/<projectname>/` 디렉토리 | 설명 |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm 차트 |
| `./chart/<projectname>/values.yaml` | Helm 차트 값 |
| `./chart/<projectname>/templates/deployment.yaml` | 배치 템플리트 |
| `./chart/<projectname>/templates/service.yaml` | 서비스 템플리트 |
{: caption="표 5. 생성된 Node.js 앱 chart 디렉토리의 컨텐츠" caption-side="top"}
