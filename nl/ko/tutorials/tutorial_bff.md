---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-03-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 프론트 엔드를 위한 백엔드 API 작성
{: #tutorial}

프론트 엔드를 위한 백엔드 스타터로부터 프로젝트를 작성할 수 있습니다. Express.js, MicroProfile/Java EE, Kitura 또는 Spring과 같은 다양한 프레임워크를 사용하여 Node.js, Java 또는 Swift로 프론트 엔드를 위한 백엔드 API를 빌드하려면 이러한 스타터를 사용하십시오. 사용자는 필요한 도구를 설치하고, 프로젝트를 로컬로 빌드 및 실행하고, 이를 클라우드에 배치하는 방법을 알아볼 수 있습니다.
{: shortdesc}

## 1단계: 도구 설치
{: #before-you-begin}

[개발자 도구 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}를 설치하십시오. 

## 2단계: 프로젝트 작성
{: #create-devex}

{{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}에서 프로젝트를 작성하십시오. 

1. {{site.data.keyword.dev_console}}의 [스타터 킷 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) 페이지에서 언어에 맞는 스타터 킷을 선택하십시오. 예를 들어, Node.js 애플리케이션의 경우에는 **Express.js 백엔드**로 이동하여 **스타터 킷 선택**을 클릭하십시오. 

2. 프로젝트 이름을 입력하십시오. 이 튜토리얼의 경우에는 `ExpressBackend`를 사용하십시오. 

3. 이니셜에 `-devhost`를 추가한 것과 같은, 고유 호스트 이름을 입력하십시오. 예를 들어, 다음과 같습니다.

	```
	abc-devhost
	```

	이 호스트 이름이 프로젝트의 라우트입니다. 예를 들면, `abc-devhost.mybluemix.net`과 같습니다. 

4. 언어 플랫폼을 선택하십시오. 이 튜토리얼의 경우에는 `Node.js`를 사용하십시오. 

5. **프로젝트 작성**을 클릭하십시오. 

## 선택사항: 리소스 추가
{: #add-services}

1. **프로젝트 세부사항** 보기에서 **리소스 추가**를 클릭하십시오. 

2. 원하는 서비스의 종류를 선택하십시오. 이 튜토리얼의 경우에는 **데이터** > **다음** > **Cloudant NoSQL DB** > **다음**을 선택하십시오. 

3. **작성**을 클릭하십시오.

## 선택사항: DevOps 도구 체인 작성
{: #add-toolchain}

도구 체인을 사용으로 설정하면 프로젝트에 대한 팀 기반 개발 환경이 작성됩니다. 도구 체인을 작성하면 앱 서비스에서 소스 코드를 보고, 프로젝트를 복제하고, 발행을 작성 및 관리할 수 있는 Git 저장소를 프로비저닝합니다. 또한 Kubernetes 또는 Cloud Foundry와 같은 선택한 배치 플랫폼에 대해 사용자 정의된 전용 Gitlab 환경 및 지속적 Delivery Pipeline에 대한 액세스도 제공됩니다. 

지속적 딜리버리는 일부 애플리케이션에 대해 사용으로 설정됩니다. Delivery Pipeline 및 GitHub를 통해 빌드, 테스트 및 배치를 자동화하기 위해 지속적 딜리버리를 사용으로 설정할 수 있습니다. 

1. **프로젝트** 페이지에서 프로젝트를 선택하십시오. 

2. **클라우드에 배치**를 클릭하십시오. 

3. 배치 방법을 선택하십시오. 다음 항목 중 하나를 선택할 수 있습니다. 

	* Kubernetes 클러스터에 배치합니다. 고가용성의 애플리케이션 컨테이너를 배치하고 관리하기 위해 작업자 노드라는 호스트 클러스터를 프로비저닝합니다. 클러스터를 작성하여 배치하거나 기존 클러스터에 배치할 수 있습니다. 

	* 기본 인프라를 관리할 필요가 없는 Cloud Foundry를 사용하여 배치합니다. 

## 3단계: 프로젝트 코드 생성
{: #generate-code}

이전 단계에서 도구 체인을 작성한 경우에는 프로젝트에 대한 Git 저장소가 작성되어 있으며, 여기서 코드를 찾을 수 있습니다. 저장소에 액세스하려면 다음 단계를 따르십시오. 

1. **프로젝트** 페이지에서 프로젝트를 선택하십시오. 

2. **도구 체인 보기**를 클릭하십시오. 

3. 표제 **CODE**에 있는 **Git**를 클릭하여 소스 코드를 보고 프로젝트를 복제할 수 있는 저장소를 여십시오. 

도구 체인이 사용으로 설정되지 않은 경우에는 프로젝트 세부사항 보기에서 직접 소스를 다운로드하여 코드에 액세스할 수 있습니다. 

1. **프로젝트** 페이지에서 프로젝트를 선택하십시오. 

2. **코드 다운로드**를 클릭하여 프로젝트 아카이브를 다운로드하십시오. 

## 4단계: 앱에 대한 작업 시작
{: #code}

다운로드한 프로젝트에 대한 작업을 시작하십시오. 

1. 아카이브된 파일을 펼치십시오. 

2. 프로젝트를 IDE로 가져오십시오. 

3. 코드를 수정하십시오. 

4. {{site.data.keyword.dev_cli_notm}}을 사용하여 코드를 로컬로 빌드하고 실행하십시오. 

## 5단계: 앱을 로컬로 빌드하고 실행
{: #build-run}

자신의 고유 코드를 추가하고, 프로젝트를 빌드한 후 실행하십시오. 필요한 빌드 도구를 설치하거나 {{site.data.keyword.dev_cli_notm}}의 사용 가능한 컨테이너 지원을 사용하여 애플리케이션을 호스트 시스템에서 로컬로 실행할 수 있습니다. 

### {{site.data.keyword.dev_cli_short}} 사용

1. 현재 프로젝트 디렉토리에 있는 프로젝트를 빌드하려면 다음 명령을 실행하십시오. 

  ```
  bx dev build
  ```
  {: codeblock}

2. 현재 프로젝트 디렉토리에 있는 프로젝트를 실행하려면 다음 명령을 실행하십시오. 

  ```
  bx dev run
  ```
  {: codeblock}

3. 다음 명령을 사용하여 서버에서 curl을 실행할 수 있습니다. 

   ```
   curl http://localhost:3000
   ```
   {: codeblock}

4. 다음 주소에서 서버에 있는 API 문서를 볼 수 있습니다. 

   ```
   http://localhost:3000/swagger/api
   ```
   {: codeblock}

5. 다음 주소에서 서버에 있는 API를 탐색할 수 있습니다. 

   ```
   http://localhost:3000/explorer
   ```
   {: codeblock}

## 6단계: 클라우드에 배치
{: #deploy}

### 도구 체인을 사용하여 배치
프로덕션 앱을 {{site.data.keyword.cloud_notm}}에 배치하는 데는 몇 가지 방법이 있지만 DevOps 도구 체인을 사용하는 것이 가장 좋은 방법입니다. DevOps 도구 체인은 여러 환경으로의 배치를 손쉽게 자동화하고, 앱이 확장됨에 따라 이를 관리하는 데 도움을 주기 위해 신속하게 모니터링, 로깅 및 경보 서비스를 추가할 수 있게 해 줍니다. 

도구 체인이 적절히 구성되면 저장소의 마스터 분기에 대한 각 병합마다 빌드-배치 주기가 자동으로 시작됩니다. {{site.data.keyword.cloud_notm}} 개발자 대시보드로부터 작성된 모든 도구 체인은 자동 배치로 구성됩니다. 

DevOps 도구 체인에서 수동으로 앱을 배치할 수도 있습니다. 

1. **프로젝트** 페이지에서 프로젝트를 선택하십시오. 

2. **도구 체인 보기**를 클릭하십시오. 

3. 빌드를 시작하고, 배치를 관리하고 로그 및 히스토리를 볼 수 있는 Delivery Pipeline을 보십시오. 

### {{site.data.keyword.dev_cli_short}}을 사용하여 배치
도구 체인을 사용하지 않도록 선택하는 경우에는 {{site.data.keyword.dev_cli_short}}을 사용하여 배치할 수도 있습니다. 

프로젝트를 Cloud Foundry에 배치하려면 다음 명령을 입력하십시오. 

  ```
  bx dev deploy
  ```
  {: codeblock}

프로젝트를 Kubernetes 클러스터에 배치하려면 다음 명령을 입력하십시오. 

```
bx dev deploy --target <container>
```
{: codeblock}

### 앱 실행 확인
애플리케이션이 배치되면 DevOps 파이프라인 또는 터미널(명령행을 사용하고 있는 경우)에 `abc-devhost.mybluemix.net`과 유사한 URL이 표시됩니다. 브라우저에서 해당 URL을 방문하십시오. 
