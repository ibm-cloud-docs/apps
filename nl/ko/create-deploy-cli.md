---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-25"

keywords: apps, create, build, deploy, cli, web app, microservice, deploy cli, deploy command line, build app local, developer tools, ibmcloud dev create

subcollection: creating-apps

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# CLI를 사용하여 앱 작성 및 배치
{: #create-deploy-app-cli}

{{site.data.keyword.cloud}} 명령행 인터페이스(CLI)를 사용하여 애플리케이션을 작성하고 배치할 수 있습니다. 

처음부터 스타터 앱을 작성하거나 기존 앱 코드를 클라우드-사용으로 설정 할 수 있습니다. 
{: note}

## 시작하기 전에
{: #prereqs-app-cli}

{{site.data.keyword.cloud_notm}} CLI, {{site.data.keyword.dev_cli_notm}} CLI 플러그인 및 기타 권장 플러그인과 도구를 설치해야 합니다. 자세한 정보는 [IBM Cloud CLI 시작하기](/docs/cli?topic=cloud-cli-ibmcloud-cli)를 참조하십시오. 

## 처음부터 스타터 앱 작성
{: #create-app-cli}

처음부터 앱 작성은 아직 시작할 기존 코드가 없으며 언어 또는 프레임워크 스타터 템플리트에서 시작하고자 하는 경우에 유용합니다.

1. 선택한 디렉토리에서 [`ibmcloud dev create`](/docs/cli/idt?topic=cloud-cli-idt-cli#create) 명령을 실행하십시오.
2. **백엔드 서비스/웹 앱**을 애플리케이션 유형으로 선택하십시오.
3. **Node**를 언어 유형으로 선택하십시오.
4. **Express.js의 Node.js 웹 앱(웹 앱)**을 사용할 스타터 킷으로 선택하십시오.
5. 앱의 이름을 입력하고 사용할 리소스 그룹을 선택하십시오(필요한 경우). 지금은 서비스를 추가하지 마십시오.
6. DevOps 도구 체인을 작성하려면 **IBM DevOps, Cloud Foundry 빌드팩에 배치** 옵션을 선택하십시오. 이 단계를 완료하기 위해 SSH 키를 설정해야 할 수 있습니다.
  SSH 키에 대해 비밀번호 문구를 설정하는 경우에는 이 코드를 입력해야 합니다.
  {: note}
7. 나머지 프롬프트에 따라 다음을 수행하십시오.
  * 도구 체인의 지역을 선택하십시오.
  * DevOps 도구 체인 이름에 이름을 입력하십시오.
  * 호스트 이름에 이름을 입력하십시오.

앱 및 도구 체인 작성을 완료하는 데 몇 초가 걸립니다.

## 배치 및 클라우드 인에이블먼트 자산 생성
{: #byoc-cli}

이 옵션은 이미 기존 코드 베이스를 보유 중이며 [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable)을 사용하여 단일 마이크로서비스 또는 웹 앱의 배치 및 클라우드 인에이블먼트 자산을 생성하고자 하는 경우에 사용될 수 있습니다. 이 명령은 베타 상태이며 일부 언어 및/또는 앱 구조는 지원되지 않음을 유념하십시오. 다음 지시사항에서는 샘플 저장소에서 이 기능을 사용하는 방법을 보여주지만, 해당 단계는 자체 코드 베이스에 대해 거의 동일합니다.

1. `ibmcloud login`을 실행하여 {{site.data.keyword.cloud_notm}}에 로그인한 후에 조직 및 영역을 대상으로 지정하십시오.
2. 선택한 디렉토리에서 다음 명령을 실행하여 [Hello World 샘플 앱](https://github.com/IBM-Cloud/node-helloworld){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")을 복제하십시오.

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

3. 샘플 앱을 복제한 디렉토리로 이동하여 [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable) 명령을 실행하십시오.
4. 지금 변경사항을 커미트하지 않고 계속하도록 선택하십시오(필요한 경우).
5. 발견된 Node 언어로 진행하라는 프롬프트가 표시되면 계속하도록 선택하십시오.
6. 사용할 리소스 그룹을 선택하십시오(필요한 경우). 
7. 이 Git 저장소에 링크된 새 {{site.data.keyword.cloud_notm}} 앱을 작성하는 옵션을 선택하십시오. 세부사항은 **중요 참고사항**를 참조하십시오.
8. 지금은 서비스를 추가하지 마십시오.
9. 오퍼레이션이 완료될 때까지 잠시 기다리십시오. 
10. 오퍼레이션이 완료되고 나면 앱 디렉토리에 저장된 배치 및 클라우드 인에이블먼트 파일을 수동으로 병합하십시오. `git diff` 또는 이와 유사한 도구를 사용하여 `.merge` 표시가 있는 새 파일을 병합하십시오.

### 중요 참고사항
 - {{site.data.keyword.cloud_notm}} 콘솔을 사용하여 {{site.data.keyword.cloud_notm}} 앱을 이미 작성한 경우에는 앱 디렉토리에서 이전 절의 2 - 5단계를 수행하십시오. 6단계의 경우, 로컬 코드를 기존 앱에 연결하는 옵션을 선택할 수 있습니다.
 - [`ibmcloud dev enable --no-create`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable)를 실행하여 {{site.data.keyword.cloud_notm}} 앱에 연결하지 않고 배치 및 클라우드 인에이블먼트 파일 생성을 수행하도록 선택할 수도 있습니다.
 - 도구 체인 및 배치 파일을 수동으로 구성하려는 경우에는 [이 튜토리얼](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc-kube)을 따르십시오. 이는 둘 이상의 상호 연관된 웹 앱이나 마이크로서비스에 대해 Continuous Delivery 도구 체인을 구성하고자 할 때 유용할 수 있습니다.
 - 기존 코드 베이스가 아직 Git 저장소에 없는 경우에는 앱 디렉토리에서 이전 절의 2 - 5단계를 수행하십시오. 6단계의 경우, 새 {{site.data.keyword.cloud_notm}} 앱을 작성하고 이를 DevOps 도구 체인(이에는 새로 작성된 GitLab 저장소가 있음)에 배치하는 옵션을 선택할 수 있습니다.

## 앱 빌드 및 로컬로 실행
{: #build-run-app-cli}

앱을 작성하는 데 사용한 옵션에 관계없이 지금 앱을 빌드하고 로컬로 실행할 수 있습니다.

1. 애플리케이션 디렉토리로 이동하여 Docker가 시스템에서 실행 중인지 확인하십시오.
2. [`ibmcloud dev build`](/docs/cli/idt?topic=cloud-cli-idt-cli#build) 명령을 실행하여 앱을 빌드하십시오.
3. [`ibmcloud dev run`](/docs/cli/idt?topic=cloud-cli-idt-cli#run) 명령을 실행하여 앱을 로컬로 실행하십시오.
4. `http://localhost:3000` 또는 이와 유사한 URL에서 로컬로 실행 중인 앱을 보십시오.
5. 앱을 중지하려면 **Ctrl+C** 키를 누르십시오.

`ibmcloud dev build/run`과 같은 [복합 명령](/docs/cli/idt?topic=cloud-cli-idt-cli#compound)을 사용하여 순차적으로 빌드 다음에 실행을 발행할 수도 있습니다.
{: tip}

## 서비스 추가 및 코드 수정
{: #resources-app-cli}

로컬로 앱을 실행할 수 있으므로 서비스를 추가하고 일부 코드를 수정할 수 있습니다. 

1. [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit) 명령을 실행하십시오.
2. 프롬프트에 따라 새 데이터 관련 서비스를 작성하고 {{site.data.keyword.cloudant_short_notm}}와 같은 앱에 연결하십시오. 서비스의 지역 및 플랜을 선택해야 합니다.
3. 서비스를 작성할 때 앱 디렉토리에 저장된 구성 파일의 수동 병합을 선택할 수 있습니다. 또는 지금 이 단계를 건너뛸 수 있습니다.
4. 코드를 업데이트하십시오. 예를 들어, `/public/index.html` 파일 또는 유사한 파일을 수정하십시오. 샘플 `ExpressJS` 애플리케이션을 사용 중인 경우 `Congratulations!` 문자열을 `Hello World!`와 같이 변경할 수 있습니다.
5. 수정한 파일을 저장하십시오.

## {{site.data.keyword.cloud_notm}}에 배치
{: #deploy-app-cli}

앱이 구성된 방법에 따라 두 가지 방법 중 하나로 {{site.data.keyword.cloud_notm}} 앱을 배치할 수 있습니다. 

### DevOps 도구 체인을 사용하여 앱 배치
앱의 DevOps 도구 체인을 아직 작성하지 않았으며 앱이 아직 Git 저장소에 없는 경우에는 [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit) 명령을 실행할 수 있습니다. "DevOps 구성"에 대한 프롬프트에 따라 새 도구 체인에 배치(하고 새 GitLab 저장소를 작성)하십시오.

앱에 대한 DevOps 도구 체인을 작성하고 나면 새 빌드 배치는 코드를 커미트하고 이를 도구 체인의 저장소에 푸시하는 것처럼 단순합니다. 

1. `git add .` 명령을 실행하십시오.
2. `git commit -m "made changes"` 명령을 실행하여 변경사항을 커미트하십시오.
3. `git push origin master` 명령을 실행하여 마스터 분기에 푸시하십시오.
4. {{site.data.keyword.cloud_notm}} 콘솔에서 앱에 대한 DevOps 도구 체인을 보십시오. 앱 디렉토리에서 [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) 명령을 실행하여 {{site.data.keyword.cloud_notm}} 콘솔의 **앱 세부사항** 페이지에서 도구 체인 세부사항을 볼 수 있습니다.
5. 도구 체인 내의 파이프라인을 보고 새 빌드가 시작되었는지 확인하십시오.

### 수동으로 앱 배치

[`deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) 명령을 사용하여 수동으로 앱을 배치할 수 있습니다. 예를 들어, 다음 단계를 사용하여 수동으로 앱을 Kubernetes에 배치하십시오.

1. [Kubernetes 클러스터를 작성](https://{DomainName}/kubernetes/overview){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")했는지 확인하십시오.
2. [`ibmcloud dev deploy -t container`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) 명령을 실행하십시오.
3. 프롬프트가 표시되면 사용할 클러스터 및 컨테이너 이미지 이름을 확인하십시오.
4. 배치가 완료될 때까지 몇 분 동안 기다리십시오.

## 앱 보기
{: #view-app-cli}

1. {{site.data.keyword.cloud_notm}}에서 실행 중인 앱의 URL을 보려면 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 명령을 실행하십시오.
2. {{site.data.keyword.cloud_notm}} 콘솔에서 앱의 인증 정보, 서비스 및 도구 체인에 대한 세부사항을 보려면 [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) 명령을 실행하십시오. 

**문제를 보고하거나 피드백을 제공하려면 [{{site.data.keyword.cloud_notm}} Tech의 Slack(#developer-tools 채널)](https://ibm-cloud-tech.slack.com/){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")을 사용할 수 있습니다. [여기](https://slack-invite-ibm-cloud-tech.mybluemix.net/){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")에서 팀 액세스를 요청하십시오.**
