---
copyright:

  years: 2018

lastupdated: "2018-10-02"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}

# CLI를 사용하여 앱 작성 및 배치
{: #developing}

{{site.data.keyword.Bluemix}} 명령행 인터페이스(CLI)를 사용하여 앱을 작성하고 배치할 수 있습니다.
{:shortdesc}

## 시작하기 전에
{: #prereqs}

{{site.data.keyword.Bluemix_notm}} CLI, {{site.data.keyword.dev_cli_notm}} CLI 플러그인 및 기타 권장 플러그인과 도구를 설치하십시오. 자세한 정보는 [IBM Cloud CLI 시작하기](/docs/cli/index.html)를 참조하십시오. 

## 앱 작성
{: #create}

처음부터 새 앱을 작성하거나 기존 코드를 사용하여 클라우드 지원 앱을 작성할 수 있습니다. 

### 처음부터 앱 작성

1. 선택한 디렉토리에서 [`ibmcloud dev create`](/docs/cli/idt/commands.html#create) 명령을 실행하십시오.
2. **백엔드 서비스/웹 앱**을 애플리케이션 유형으로 선택하십시오.
3. **Node**를 언어 유형으로 선택하십시오.
4. **Express.js Basic(웹 앱)**을 사용할 스타터 킷으로 선택하십시오.
5. 앱의 이름을 입력하고 사용할 리소스 그룹을 선택하십시오(필요한 경우). 지금 서비스를 추가하지 마십시오.
6. DevOps 도구 체인을 작성하려면 **IBM DevOps, Cloud Foundry 사용** 옵션을 선택하십시오. 이 단계를 완료하기 위해 SSH 키를 설정해야 할 수 있습니다.
7. 고유한 호스트 이름을 입력하십시오(예: `abc-devhost`). 이 호스트 이름은 앱의 라우트인 `abc-devhost.mybluemix.net`입니다.

앱 및 도구 체인 작성을 완료하는 데 몇 초가 걸립니다. 명령 프롬프트에서 상태를 모니터할 수 있습니다.

### 기존 코드를 사용하여 앱 작성

1. 선택한 디렉토리에서 다음 명령을 실행하여 [Hello World 샘플 앱](https://github.com/IBM-Cloud/node-helloworld)을 복제하십시오.

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

2. 샘플 앱을 복제한 디렉토리로 이동하여 [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable) 명령을 실행하십시오.
3. 지금 GitHub에 변경사항을 커미트하지 않고 계속하도록 선택하십시오.
4. 발견된 Node 언어로 진행하라는 프롬프트가 표시되면 계속하도록 선택하십시오.
5. 사용할 리소스 그룹을 선택하십시오(필요한 경우). 지금 서비스를 추가하지 마십시오.
6. 앱을 작성될 때까지 몇 초 동안 기다리십시오. 
7. 앱을 작성할 때 앱 디렉토리에 저장된 배치 및 구성 파일을 수동으로 병합하도록 선택할 수 있습니다. 또는 지금 이 단계를 건너뛸 수 있습니다.

## 앱 빌드 및 로컬로 실행
{: #build-run}

앱을 작성하는 데 사용한 옵션에 관계없이 지금 앱을 빌드하고 로컬로 실행할 수 있습니다.

1. 애플리케이션 디렉토리로 이동하여 Docker가 시스템에서 실행 중인지 확인하십시오.
2. [`ibmcloud dev build`](/docs/cli/idt/commands.html#build) 명령을 실행하여 앱을 빌드하십시오.
3. [`ibmcloud dev run`](/docs/cli/idt/commands.html#run) 명령을 실행하여 앱을 로컬로 실행하십시오.
4. `http://localhost:3000` 또는 유사한 URL에서 로컬로 실행 중인 앱을 보십시오.
5. 앱을 중지하려면 **Ctrl+C** 키를 누르십시오.

`ibmcloud dev build/run`과 같은 [복합 명령](/docs/cli/idt/commands.html#compound)을 사용하여 순차적으로 빌드 다음에 실행을 발행할 수도 있습니다.
{: tip}

## 서비스 추가 및 코드 수정
{: #add-service}

로컬로 앱을 실행할 수 있으므로 서비스를 추가하고 일부 코드를 수정할 수 있습니다. 

1. [`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit) 명령을 실행하십시오.
2. 프롬프트에 따라 새 데이터 관련 서비스를 작성하고 {{site.data.keyword.cloudant_short_notm}}와 같은 앱에 연결하십시오. 서비스의 지역 및 플랜을 선택해야 합니다.
3. 서비스를 작성할 때 앱 디렉토리에 저장된 배치 및 구성을 수동으로 병합하도록 선택할 수 있습니다. 또는 지금 이 단계를 건너뛸 수 있습니다.
4. 코드를 변경하십시오. 예를 들어, `/public/index.html` 파일 또는 유사한 파일을 수정하십시오. 샘플 `ExpressJS` 애플리케이션을 사용 중인 경우 `Congratulations!` 문자열을 `Hello World!`와 같이 변경할 수 있습니다.
5. 수정한 파일을 저장하십시오.

## {{site.data.keyword.Bluemix_notm}}에 배치
{: #deploy}

앱이 구성된 방법에 따라 두 가지 방법 중 하나로 앱을 {{site.data.keyword.Bluemix_notm}}에 배치할 수 있습니다. 

### DevOps 도구 체인을 사용하여 앱 배치

이전에 앱에 대한 DevOps 도구 체인을 작성한 경우 새 빌드를 배치하는 것은 코드를 커미트하여 도구 체인의 저장소에 푸시하는 것만큼 단순합니다. 

1. `git add .` 명령을 실행하십시오.
2. `git commit -m "made changes"` 명령을 실행하여 변경사항을 커미트하십시오.
3. `git push origin master` 명령을 실행하여 마스터 분기에 푸시하십시오.
4. {{site.data.keyword.Bluemix_notm}} 콘솔에서 앱에 대한 DevOps 도구 체인을 보십시오. 앱 디렉토리에서 [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) 명령을 실행하고 **도구 체인 보기**를 클릭하여 웹 브라우저에서 도구 체인을 볼 수 있습니다.
5. 도구 체인 내의 파이프라인을 보고 새 빌드가 시작되었는지 확인하십시오.

### 수동으로 앱 배치

[`deploy`](/docs/cli/idt/commands.html#deploy) 명령을 사용하여 수동으로 앱을 배치할 수 있습니다. 예를 들어, 다음 단계를 사용하여 수동으로 앱을 Kubernetes에 배치하십시오.

1. [Kubernetes 클러스터를 작성](https://console.bluemix.net/containers-kubernetes/overview)했는지 확인하십시오.
2. [`ibmcloud dev deploy -t container`](/docs/cli/idt/commands.html#deploy) 명령을 실행하십시오.
3. 프롬프트가 표시되면 사용할 클러스터 및 컨테이너 이미지 이름을 확인하십시오.
4. 배치가 완료될 때까지 몇 분 동안 기다리십시오.

## 앱 보기
{: #view}

1. {{site.data.keyword.Bluemix_notm}}에서 실행 중인 앱의 URL을 보려면 [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) 명령을 실행하십시오.
2. {{site.data.keyword.Bluemix_notm}} 콘솔에서 앱의 인증 정보, 서비스 및 도구 체인에 대한 세부사항을 보려면 [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) 명령을 실행하십시오. 

