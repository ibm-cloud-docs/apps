---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, credentials, virtual server instance, vsi, virtual machine, vm, environment, credential, virtual, docker, local, ibmcloudenv

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 가상 인스턴스 또는 로컬 Docker 환경에 인증 정보 추가
{: #add-credentials-vsi}

가상 서버 인스턴스 또는 로컬 Docker 배치 환경에 서비스 인증 정보를 추가하는 방법에 대해 알아봅니다.
{: shortdesc}

## 사용자 코드 + 가상 서버 인스턴스 또는 로컬 Docker
{: #credentials-byoc-vsi}

VSI 또는 로컬 Docker에서 환경은 전적으로 사용자 소유입니다. 예를 들어, 다음 예제와 같이 코드를 작성하고 실행 시에 애플리케이션에 인증 정보의 환경 값을 제공할 수 있습니다.
```
password = getEnvironment('password');
```
{: codeblock}

Bash에서는 다음 예제와 같은 코드를 작성할 수 있습니다.
```bash
export password="someThingSensitive"
# run app locally.  If node, something like:
npm run start
```
{: codeblock}

Docker에서는 다음 예제와 같은 코드를 작성할 수 있습니다.
```
docker run -p 80:8080 -e password="someThingSensitive"
```
{: codeblock}

## 스타터 킷 + VSI(또는 로컬 Docker)
{: #credentials-starterkit-vsi}

### 가상 서버 인스턴스의 준비 방법

환경은 마치 사용자가 노트북에서 애플리케이션을 실행하듯이 전적으로 사용자에 의해 제어됩니다. 즉, 로컬 Docker. 실행 중인 애플리케이션의 관점에서 보면 VSI가 사실상 베어메탈이므로, 어떤 _시크릿_(Kubernetes에서와 같은) 또는 _서비스_(Cloud Foundry에서와 같은)도 존재하지 않습니다.

### 스타터 킷에서 생성된 코드
{: #starterkit-generated-code-vsi}

스타터 킷에서 생성된 코드에는 고유 `IBMCloudEnv` 라이브러리가 있으며, 이는 애플리케이션 코드가 여러 배치 대상에서 실행될 수 있는 이식 가능한 코드가 되도록 환경 값의 검색을 추상화합니다. 가상 또는 로컬 Docker에서는 _반드시_ 실제 환경 변수에서 가져올 필요는 없는 `IBMCloudEnv` 라이브러리를 충족하는 값으로 해당 환경을 준비해야 합니다.

편의상, 스타터 킷에서 생성된 출력에 포함된 `mappings.json` 지시사항에는 애플리케이션이 사용할 수 있는 값을 `IBMCloudEnv` 라이브러리가 소싱할 수 있는 로컬 파일에 대한 참조가 있습니다.

예를 들어, `mappings.json` 파일에서 다음 섹션의 마지막 행을 주목하십시오.
```json
"cloudant_apikey": {
  "searchPatterns": [
    "user-provided:blarg-cloudant-1538408663553:apikey",
    "cloudfoundry:$['cloudant'][0].credentials.apikey",
    "env:service_cloudant:$.apikey",
    "env:cloudant_apikey",
    "file:/server/localdev-config.json:$.cloudant_apikey"
  ]
},
```
{: codeblock}

앱을 작성할 때 "지속적 딜리버리 구성" 기능을 사용하면 `/server/localdev-config.json` 파일이 GitLab 저장소에서 제거됩니다. 보안상의 이유로, 인증 정보를 소스 코드 저장소에 두고 싶지는 않습니다.

작성된 GitLab 저장소에서 `git clone`을 사용하여 본격적으로 개발을 시작하는 경우, 민감한 인증 정보가 있는 파일의 원하지 않는 유입을 방지하는 데 도움이 될 수 있도록 `.gitignore` 파일이 특정하게 `server/localdev-config.json`을 무시한다는 점을 유념하십시오. 그러나 VSI에서는 노트북에서 작업하는 개발자의 경우와 마찬가지로 해당 파일이 _필요_합니다.

다음 단계를 완료하여 `server/localdev-config.json` 파일을 검색할 수 있습니다.

1. "지속적 딜리버리 구성" 기능을 사용할 때 자동으로 작성된 GitLab 저장소에서 `git clone`을 사용하십시오.
2. `dev` 플러그인이 포함된 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli)를 설치하십시오.
3. `ibmcloud` 명령행을 사용하여 {{site.data.keyword.cloud_notm}}에 로그인하십시오.
4. `cli-config.yml` 파일을 참조하는 `ibmcloud dev get-credentials`를 실행하십시오. `cli-config.yml` 파일에는 인증 정보를 보유한 애플리케이션 및 생성 작업에 대한 정보가 포함되어 있습니다.

임의의 서비스가 `ibmcloud dev get-credentials` 및 "지속적 딜리버리 구성" 기능의 사용 간에 애플리케이션에서 제거된 경우, 다운로드된 `/server/localdev-config.json` 파일에는 원래 `git clone` 코드 베이스에서 필요로 하는 모든 인증 정보가 없을 수 있습니다.
{: tip}

Docker 컨테이너에서 애플리케이션을 실행하는 경우에는 `/server/localdev-config.json` 파일을 완전히 제거하고 Docker 명령행에서 환경 변수를 전달하도록 선택할 수 있습니다.

`mappings.json` 파일의 "cloudant_apikey" 섹션에서 계속하여, `file...` 행 앞의 `env:cloudant_apikey`를 주목하십시오. 이는 `cloudant_apikey`로 이름 지정된 환경 변수가 파일의 컨텐츠에 우선함을 의미합니다. 따라서 파일이 사용자가 빌드한 Docker 이미지에 있어도(이는 반드시 필요하지는 않음) Docker 명령행에서 이를 전달하여 값을 대체할 수 있습니다.

예를 들어, 다음과 같습니다.
```
docker run -p 80:8080 -e cloudant_apikey="someKeyValue"
```
{: codeblock}
