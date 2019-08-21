---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-17"

keywords: apps, application, troubleshooting, debug apps, known issues, debug, help, configuration, app, troubleshoot, error, errors, failure, failed, fail, issues, applications

subcollection: creating-apps

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# 앱 작성 문제점 해결
{: #managingapps}

앱 작성과 관련된 일반적인 문제에는 앱을 업데이트할 수 없거나 2바이트 문자가 표시되지 않는 등의 문제가 포함될 수 있습니다. 대부분 몇 가지 간단한 단계를 수행하여 이러한 문제점에서 복구할 수 있습니다.
{:shortdesc}

## 내 앱이 다른 도메인에서 호스팅됨
{: #domains-ts}
{: troubleshoot}

내 앱 중 일부는 `mybluemix.net` 도메인에서 호스팅되지만 다른 앱은 `appdomain.cloud` 도메인에서 호스팅됨

기존 앱은 `mybluemix.net` 도메인에서 호스팅되지만 새 앱은 `appdomain.cloud` 도메인에서 호스팅됨
{: tsSymptoms}

새 호스트 이름 옵션 `*.appdomain.cloud`는 cloud.ibm.com에서 사용할 수 있습니다.

이전에는 {{site.data.keyword.containerlong_notm}} 또는 Cloud Foundry와 같은 다양한 배치 대상에서 앱을 호스팅하는 데 `mybluemix.net` 도메인이 사용되었습니다. `mybluemix.net`에서 호스팅한 앱에는 영향을 미치지 않습니다.

Cloud Foundry 앱의 하위 도메인은 `cf.appdomain.cloud`입니다. {{site.data.keyword.containerlong_notm}}에 배치하는 앱의 하위 도메인은 `containers.appdomain.cloud`입니다.

자세한 정보는 [도메인 관리](/docs/apps?topic=creating-apps-update-domain)를 참조하십시오.

## 저장되지 않은 변경사항이 있음
{: #ts_unsaved_changes}
{: troubleshoot}

앱 세부사항 페이지에서 항목을 클릭하는 경우 조치를 수행하지 못할 수 있습니다. 또한 계속하려면 변경사항을 저장하라는 프롬프트가 표시될 수 있습니다.

앱 세부사항 페이지에서 앱 또는 서비스를 확인하려고 시도하는 경우 다음 오류 메시지가 표시됩니다.
{: tsSymptoms}

`저장되지 않은 변경사항이 있습니다. 이 페이지에서 나가시겠습니까?`

런타임 분할창의 **인스턴스** 또는 **메모리 할당량** 필드 위로 마우스를 스크롤하면 값이 변경됩니다. 이 동작은 의도된 동작입니다. 그러나 다른 페이지로 이동하기 전에 메모리 또는 인스턴스 설정을 저장하도록 프롬프트가 표시됩니다.
{: tsCauses}

메시지 창을 닫고 런타임 분할창에서 **재설정**을 클릭하십시오.
{: tsResolve}

## 권한 오류로 인해 {{site.data.keyword.cloud_notm}} 서비스에 액세스할 수 없음
{: #ts_vcap}
{: troubleshoot}

사용자 앱에서 서비스 인증 정보가 하드 코딩된 경우 사용자 앱이 {{site.data.keyword.cloud_notm}} 서비스에 액세스하려 하면 권한 오류가 발생합니다.

{{site.data.keyword.cloud_notm}} 서비스와 통신하도록 사용자 앱을 구성한 후에는 앱을 {{site.data.keyword.cloud_notm}}에 배치하십시오. 그러나 앱을 사용하여 {{site.data.keyword.cloud_notm}} 서비스에 액세스할 수는 없으며 권한 오류가 수신됩니다.
{: tsSymptoms}

앱에 하드 코딩된 인증 정보가 올바르지 않습니다. 서비스가 다시 작성될 때마다 이에 액세스하기 위한 인증 정보가 변경됩니다.
{: tsCauses}

앱에서 인증 정보를 하드 코딩하는 대신 VCAP_SERVICES 환경 변수의 연결 매개변수를 사용하십시오. VCAP_SERVICES 환경 변수를 통해 연결 매개변수를 사용하는 메소드는 프로그램 언어마다 다릅니다. 예를 들어, Node.js 앱의 경우에는 다음 명령을 사용할 수 있습니다.
{: tsResolve}

```
process.env.VCAP_SERVICES
```

다른 프로그램 언어로 사용할 수 있는 명령에 대한 자세한 정보는 [Java ](https://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘") 및 [Ruby ](https://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")를 참조하십시오.

## 502 잘못된 게이트웨이 오류가 수신됨
{: #ts_502_error}
{: troubleshoot}

{{site.data.keyword.cloud_notm}}에서 앱과 상호작용할 때 `502 잘못된 게이트웨이` 오류가 수신되면 {{site.data.keyword.cloud_notm}} 상태 페이지를 확인한 후 적절한 조치를 취하십시오.

502 Bad Gateway로 시작하는 오류 메시지를 수신합니다. 예를 들어, `502 Bad Gateway: Registered endpoint failed to handle the request`가 표시될 수 있습니다.
{: tsSymptoms}

잘못된 게이트웨이 오류는 사이트를 호스팅하는 기본 서버의 데이터를 저장하고 릴레이하기 위해 프록시 서버를 사용하는 웹 사이트로 이동할 때 일반적으로 발생합니다. 기본 서버와 프록시 서버가 제대로 연결되지 않았을 수 있습니다. 그러면 브라우저 창에 HTTP 상태 코드 502가 표시됩니다. 이 상태 코드는 사이트의 기본 서버가 프록시 서버로부터 예상한 HTTP 구현을 수신하지 않았음을 나타냅니다.
{: tsCauses}

잘못된 게이트웨이 오류의 덜 일반적인 기타 원인은 ISP(Internet Service Provider) 드롭아웃, 잘못된 방화벽 구성 및 브라우저 캐시 오류입니다.

{{site.data.keyword.cloud_notm}} 서비스의 작동이 중지된 것으로 의심되는 경우 먼저 [{{site.data.keyword.cloud_notm}} 상태 ](https://cloud.ibm.com/status){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘") 페이지를 확인하십시오. 임시 해결책으로 [다른 {{site.data.keyword.cloud_notm}} 지역의 서비스를 사용](/docs/resources/connect_external_app?topic=resources-externalapp){: new_window}할 수 있습니다. 서비스 상태가 정상이면 다음 단계를 수행하여 문제를 해결하십시오.
{: tsResolve}

  * 조치 재시도:
    * 키보드에서 F5를 누르거나 **새로 고치기**를 클릭하여 페이지를 다시 로드하십시오. 이 단계가 작동하지 않는 경우에는 브라우저의 캐시 및 쿠키를 지운 후 다시 로드하십시오.
    * 다른 브라우저를 사용하십시오.
    * 라우터, 모뎀 및 컴퓨터를 다시 시작하십시오. 이 디바이스를 다시 부팅하면 오류 502의 원인이 되는 다양한 오류를 정리할 수 있습니다.
  * 대기한 후 나중에 다시 시도하십시오. 인터넷 서비스 제공업체 또는 {{site.data.keyword.cloud_notm}} 서비스에 일시적인 문제점이 발생할 수 있습니다. 일시적인 문제점이 해결될 때까지 대기할 수 있습니다.
  * 문제점이 계속 존재하면 {{site.data.keyword.cloud_notm}} 지원 센터에 문의하십시오. 자세한 정보는 [{{site.data.keyword.cloud_notm}} 지원 문의](/docs/get-support?topic=get-support-getting-customer-support){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")를 참조하십시오.

## Android 앱이 {{site.data.keyword.mobilepushshort}}를 받을 수 없음
{: #ts_push}
{: troubleshoot}

Google이 액세스할 수 없는 특정 지역의 Android 앱은 IBM {{site.data.keyword.mobilepushshort}} 서비스를 통해 전송하는 알림을 받을 수 없습니다. 이 경우 임시 해결책으로 서드파티 서비스를 사용합니다.

 {{site.data.keyword.cloud_notm}} 앱에 대해 {{site.data.keyword.mobilepushshort}} 서비스를 바인딩하고 등록된 디바이스에 메시지를 전송합니다. 하지만 Android에서 개발된 앱이 특정 지역에서 알림을 수신할 수 없습니다.
{: tsSymptoms}

IBM {{site.data.keyword.mobilepushshort}} 서비스에서는 GCM(Google Cloud Messaging) 서비스를 사용하여 Android에서 개발되는 모바일 앱에 알림을 디스패치합니다. Android 앱이 알림을 수신하도록 설정하려면 모바일 앱이 GCM(Google Cloud Messaging) 서비스에 액세스할 수 있어야 합니댜. Android 앱이 GCM 서비스에 도달할 수 없는 지역에서는 Android 앱이 {{site.data.keyword.mobilepushshort}}를 받을 수 없습니다.
{: tsCauses}

임시 해결책으로 GCM 서비스에 의존하지 않는 서드파티 서비스를 사용하십시오(예: [Pushy](https://pushy.me/){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘") 및 [jpush](https://www.jiguang.cn/en/){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")).
{: tsResolve}

## 앱이 {{site.data.keyword.cloud_notm}}로 푸시될 때 2바이트 문자가 올바르게 표시되지 않음
{: #ts_doublebytes}
{: troubleshoot}

서블릿 또는 JSP 파일에 대해 유니코드 지원이 제대로 구성되지 않은 경우 2바이트 문자가 올바르게 표시되지 않을 수 있습니다.

앱이 {{site.data.keyword.cloud_notm}}로 푸시될 때 앱 내에 지정된 2바이트 문자가 올바르게 표시되지 않습니다.
{: tsSymptoms}

이 문제점은 서블릿 또는 JSP 파일에 대해 유니코드 지원이 제대로 구성되지 않은 경우에 발생할 수 있습니다.
{: tsCauses}

서블릿 또는 JSP 파일에서 다음 코드를 사용할 수 있습니다.
{: tsResolve}

  * 서블릿 소스 파일
  ```java
	response.setContentType("text/html; charset=UTF-8");
	```
  {: codeblock}

  * JSP
  ```jsp
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```
  {: codeblock}

## Node.js 앱을 배치할 수 없음
{: #ts_nodejs_deploy}
{: troubleshoot}

Node.js 앱을 업데이트하거나 Node.js 앱을 {{site.data.keyword.cloud_notm}}에 배치할 때 문제점이 발생할 수 있습니다.

Node.js 앱을 업데이트하거나 {{site.data.keyword.cloud_notm}}에 배치할 때 다음 오류 메시지 중 하나가 표시될 수 있습니다.
{: tsSymptoms}

`An app was not successfully detected by any available buildpack.`

`Instance (index 0) failed to start accepting connections.`

`Cannot get instances since staging failed.`

가능한 원인은 다음과 같습니다.
{: tsCauses}

  * 시작 명령이 지정되지 않았습니다.
  * Node.js 앱을 배치하는 데 필요한 파일이 앱에서 누락되었거나 루트 디렉토리 이외의 다른 폴더에 있습니다.

문제점의 원인에 따라서 다음 방법 중 하나를 사용하십시오.
{: tsResolve}

  * 다음 방법 중 하나로 시작 명령을 지정하십시오.
     * Cloud Foundry 명령행 인터페이스를 사용하십시오. 예를 들어, 다음과 같습니다.
      ```
		  ibmcloud cf push MyUniqueNodejs01 -p app_path -c "node app.js"
		  ```
      {: codeblock}

    * [package.json ](https://www.npmjs.com/package/jsonfile){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘") 파일을 사용하십시오. 예를 들어, 다음과 같습니다.
	    ```json
		  {
        ...
  	    "scripts": {
	 		  "start": "node app.js"
 	   }
	    }
	    ```

    * `manifest.yml` 파일을 사용하십시오. 예를 들어, 다음과 같습니다.
	    ```
		  applications:
  name: MyUniqueNodejs01
  ...
      command: node app.js
  ...
      ```

  * Node.js 빌드팩에서 앱을 인식할 수 있게 하려면 Node.js 앱에 `package.json` 파일이 있어야 합니다. 또한 이 파일이 앱의 루트 디렉토리에 있어야 합니다.
    다음 예에서는 단순한 `package.json` 파일을 보여줍니다.
	```json
	{
        "name": "MyUniqueNodejs01",
        "version": "0.0.1",
        "description": "A sample package.json file",
        "dependencies": {
                "express": "3.4.x",
                "jade": "1.1.x"
        },
        "engines": {
                "node": "0.10.x"
        },
        "scripts": {
                  "start": "node app.js"
        }
 }
    ```

Node.js 앱에 대한 추가 팁은 [Node.js 애플리케이션에 대한 팁 ](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")을 참조하십시오.

## {{site.data.keyword.cloud_notm}} Liberty 앱을 Eclipse로 가져온 후에 `server.xml` 파일에서 구성 오류가 나타남
{: #ts_eclipse}
{: troubleshoot}

{{site.data.keyword.cloud_notm}} Liberty 앱을 Eclipse로 가져온 후에 `server.xml` 파일에서 구성 오류가 나타나면 프로젝트에서 `server.xml` 파일을 제거해야 합니다.

{{site.data.keyword.cloud_notm}} Liberty 앱을 Eclipse로 가져온 후에 Eclipse 문제점 보기에서 `server.xml` 파일 내의 구성 오류가 나타납니다.
{: tsSymptoms}

Liberty 앱이 {{site.data.keyword.cloud_notm}}로 푸시되면 Liberty 빌드팩은 `server.xml` 파일을 사용하여 앱을 구성하고 `runtime-vars.xml` 파일을 생성합니다. 앱을 Eclipse로 가져오면 `runtime-vars.xml` 파일이 로컬 환경에 없습니다.
{: tsCauses}

이 문제점은 프로젝트에서 server.xml 파일을 제거하여 해결할 수 있습니다. 앱을 WAR 앱으로 푸시하면 빌드팩이 동적으로 `server.xml` 파일을 작성합니다. 자세한 정보는 [Liberty for Java](/docs/runtimes/liberty?topic=liberty-liberty_runtime#liberty_runtime)를 참조하십시오.
{: tsResolve}

## 사용자 정의 빌드팩을 사용하여 앱을 스테이징할 수 없음
{: #ts_bp_compilation}
{: troubleshoot}

빌드팩의 스크립트가 실행 파일이 아닌 경우 사용자 정의 빌드팩을 사용하여 앱을 {{site.data.keyword.cloud_notm}}에 배치할 수 없습니다.

사용자 정의 빌드팩을 사용하여 앱을 {{site.data.keyword.cloud_notm}}에 배치할 때 `The application failed to stage, so there are no instances to display.`라는 오류 메시지가 표시됩니다.
{: tsSymptoms}

이 문제점은 발견 스크립트, 컴파일 스크립트, 릴리스 스크립트 등의 스크립트가 실행 가능하지 않을 경우에 발생합니다.
{: tsCauses}

[Git update ](https://git-scm.com/docs/git-update-index){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘") 명령을 사용하여 각 스크립트의 권한을 실행 가능으로 변경할 수 있습니다. 예를 들어, `git update --chmod=+x script.sh`를 입력합니다.
{: tsResolve}

## {{site.data.keyword.cloud_notm}} Continuous Delivery에서 Delivery Pipeline의 앱을 배치할 수 없음
{: #ts_devops_to_bm}
{: troubleshoot}

 `manifest.yml` 파일이 앱에 없는 경우에는 {{site.data.keyword.contdelivery_short}}에서 {{site.data.keyword.deliverypipeline}}을 사용하여 앱을 배치할 수 없을 수 있습니다.

 {{site.data.keyword.contdelivery_short}}에서 {{site.data.keyword.deliverypipeline}}을 사용하여 앱을 배치할 때 `Unable to detect a supported application type`이라는 오류 메시지가 표시될 수 있습니다.
 {: tsSymptoms}

 이 문제점은 앱을 {{site.data.keyword.cloud_notm}}에 배치하려면 파이프라인에 `manifest.yml` 파일이 필요하기 때문에 발생할 수 있습니다.
 {: tsCauses}

 이 문제점을 해결하려면 `manifest.yml` 파일을 작성해야 합니다. `manifest.yml` 파일을 작성하는 방법에 대한 자세한 정보는 [애플리케이션 Manifest](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest)를 참조하십시오.
 {: tsResolve}

## 스토리지 할당량 초과
{: #exceed_quota}

빌드 또는 배치 작업에 실패하고 다음 메시지가 표시되는 경우에는 다음 CLI 명령을 사용하여 이미지를 삭제할 수 있습니다. `Status: unauthorized: You have exceeded your storage quota. Delete one or more images, or review your storage quota and pricing plan.`

* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started)를 아직 설치하지 않은 경우 설치하십시오.
* `ibmcloud login`을 사용하여 {{site.data.keyword.cloud_notm}}에 로그인하고 현재 있는 영역을 가리키십시오.
* `ibmcloud cr images`를 사용하여 이미지를 나열하십시오.
* `ibmcloud cr image-rm <respository>:<tag>`를 사용하여 사용하지 않는 이미지를 삭제하십시오.
* 실패한 빌드 또는 배치 작업을 다시 실행하십시오.

## Kubernetes 로그 액세스
{: #access_kube_logs}

앱이 실행 중이 아니며 상태 엔드포인트에 액세스할 수 없는 경우에는 클러스터의 로그 보기를 시도하십시오.
* [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started)를 아직 설치하지 않은 경우 설치하십시오.
* `ibmcloud login`을 사용하여 {{site.data.keyword.cloud_notm}}에 로그인하고 현재 있는 영역을 가리키십시오.
* `ibmcloud cs clusters`를 사용하여 클러스터를 나열하십시오.
* `ibmcloud cs cluster-config <cluster-name>`를 사용하여 해당 클러스터를 가리키십시오.
* 나열된 환경 변수를 내보내십시오.
* `kubectl get pods`을 사용하여 팟(Pod)을 보십시오. `kubectl`을 설치해야 하는 경우 [kubectl 설치 및 설정](https://kubernetes.io/docs/tasks/tools/install-kubectl/){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")을 참조하십시오.
* `kubectl logs <pod-name>`을 사용하여 앱에서 로그를 볼 수 있습니다.

## `docker` 시작에 실패하며 파일을 찾을 수 없음 메시지가 표시됨
{: #docker_not_found}
{: troubleshoot}

Docker를 시작하려고 시도하면 다음 오류 메시지가 표시됩니다.
{: tsSymptoms}

```
An error exec: "docker": executable file not found in $PATH was encountered while the Docker image is building.
```
{: screen}

Docker 클라이언트가 설치되지 않았거나 설치되었지만 시작되지 않았습니다.
{: tsCauses}

[Docker](https://docs.docker.com/install/){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")가 설치되어 있는지 확인하고 이를 시작하십시오.
{: tsResolve}

## Docker 오류가 표시되며 앱 빌드에 실패함
{: #build_error}
{: troubleshoot}

`ibmcloud dev build` 명령을 사용하여 앱을 빌드하려고 시도하면 Docker 사용자 이름/비밀번호 오류가 표시되며 빌드에 실패합니다. 
{: tsSymptoms}

올바르지 않은 Docker 허브 인증 정보가 인증에 사용되고 있습니다. 
{: tsCauses}

Docker 클라이언트의 Docker 허브에서 로그아웃하십시오.
{: tsResolve}
