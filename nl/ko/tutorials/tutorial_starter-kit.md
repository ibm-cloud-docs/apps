---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-10"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{: note .note}

# 스타터 킷을 사용한 앱 작성
{: #tutorial-starterkit}

스타터 킷을 사용하여 앱을 빠르게 시작하고 향후 개발에 대비할 수 있습니다. 스타터 킷 및 프로그래밍 언어를 선택하고, 앱을 작성한 후 DevOps 도구 체인을 설정하여 앱을 자동으로 배치하십시오. 바로 검사하기 위해 코드를 다운로드할 수도 있습니다.
{: shortdesc}

빌드 옵션을 직접 사용자 정의하려는 경우 공백인 경우를 포함하여 스타터 킷 선택에서 앱을 작성할 수 있습니다. 어느 쪽이든 DevOps 도구 체인이 앱 배치를 위해 자동으로 작성됩니다. 바로 검사하기 위해 코드를 다운로드할 수도 있습니다.

{{site.data.keyword.cloud_notm}}에는 관심 있는 여러 분야(예: Watson, 보안 또는 금융) 또는 디지털 채널(예: 모바일 또는 웹 앱)의 개발자 포털이 있습니다. **메뉴** 아이콘 ![메뉴 아이콘](../../icons/icon_hamburger.svg)에서 이러한 포털에 액세스할 수 있습니다.

각 개발자 포털은 포털의 핵심 영역과 관련된 스타터 킷을 제공합니다.
이 포털은 몇 분 이내에 제품화 가능한 구동되는 앱을 작성할 수 있는 일관적이고 직관적인 워크플로우를 제공합니다.

스타터 킷은 다음 항목을 포함한 다양한 카테고리에서 사용 가능합니다.
* [Watson](https://{DomainName}/developer/watson/dashboard){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")
* [Apple](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")
* [모바일](https://{DomainName}/developer/mobile/dashboard){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")
* [웹 앱](https://{DomainName}/developer/appservice/dashboard){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")
* [보안](https://{DomainName}/developer/security/dashboard){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")
* [금융](https://{DomainName}/developer/finance/dashboard){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")

자세한 정보는 [스타터 킷 개념](/docs/apps?topic=creating-apps-starter-kits)을 참조하십시오.

## 1단계. 도구 설치
{: #prereqs-starterkit}

* [개발자 도구](/docs/cli?topic=cloud-cli-ibmcloud-cli)를 설치하십시오.
* Docker는 개발자 도구의 일부로 설치됩니다. Docker는 작업할 빌드 명령에 대해 실행되어야 합니다. Docker 계정을 작성하고, Docker 앱을 실행하고, 로그인해야 합니다.
* {{site.data.keyword.cfee_full}}에 앱을 배치하려는 경우에는 [{{site.data.keyword.cloud_notm}} 계정을 준비](/docs/cloud-foundry?topic=cloud-foundry-prepare)해야 합니다.

## 2단계. 앱 작성
{: #create-starterkit}

스타터 킷은 {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}에서 다양한 언어 및 프레임워크로 사용 가능합니다. 언어 및 유형 등의 카테고리 필터를 사용하여 선택사항을 좁힐 수 있습니다. 

1. {{site.data.keyword.dev_console}}의 [스타터 킷 ](https://{DomainName}/developer/appservice/starter-kits/){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘") 페이지에서 스타터 킷을 선택한 후 **앱 작성**을 클릭하십시오.  

    스타터 킷에 포함된 항목을 보려면 타일을 선택한 후 세부사항을 읽어보십시오. 빈 스타터 킷을 사용하여 사용자 정의하려는 경우 **앱 작성** 타일을 선택하십시오. {: tip}

2. 앱을 이름을 지정하고 리소스 그룹을 선택하십시오.

3. 선택사항. 앱을 분류하기 위한 태그를 제공하십시오. 자세한 정보는 [태그에 대한 작업](/docs/resources?topic=resources-tag)을 참조하십시오.

4. 언어 및 프레임워크를 선택하십시오. 일부 스타터 킷은 하나의 언어로만 사용 가능할 수 있습니다.

5. **작성**을 클릭하십시오.

시작이 좋습니다! 앱이 작성되었습니다! 

서비스를 추가하거나 지속적 딜리버리를 설정하기 전에 코드를 검사하려면 앱 세부사항 페이지에서 **코드 다운로드**를 클릭하십시오. 다운로드한 압축 파일에 있는 `README.md` 파일을 확인하여 앱을 시작하고 실행하기 위해 추가 조치를 수행해야 하는지 알아보십시오.
{: tip}

## 3단계. 서비스 추가(선택사항)
{: #resources-starterkit}

스타터 킷에 특정 리소스가 필요한 경우 자동 프로비저닝된 서비스를 사용할 수 있습니다. 그러면 인스턴스가 앱을 작성할 때 해당 서비스에 대한 인스턴스가 자동으로 작성됩니다. 

Watson의 코그너티브 기능으로 앱을 향상시키는 서비스를 추가하거나 모바일 서비스 또는 보안 서비스를 추가할 수도 있습니다. 이 튜토리얼의 경우 데이터를 관리할 위치를 추가하십시오.

1. 앱 세부사항 페이지에서 이 앱에 연결하려는 서비스가 이미 있는지 여부에 따라 **서비스 작성** 또는 **기존 서비스 연결**을 클릭하십시오. 
2. 원하는 서비스의 종류를 선택한 후 프롬프트에 따라 기존 서비스를 앱에 추가하거나 서비스 인스턴스를 작성하십시오. 

원하는 서비스를 모두 추가하면 앱 세부사항 페이지에 해당 서비스가 표시됩니다. 

## 4단계. 배치 대상 선택 및 지속적 딜리버리 구성
{: #target-starterkit}

배치 대상을 선택하면 앱에 사용할 DevOps 도구 체인이 자동으로 작성됩니다. 이 도구 체인에는 앱의 배치 상태를 나타내는 Delivery Pipeline이 포함됩니다. 생성된 새 앱은 도구 체인의 일부인 GitLab 저장소로 푸시됩니다. 

DevOps 도구 체인을 사용으로 설정하면 앱에 대한 팀 기반 개발 환경을 작성할 수 있습니다. 도구 체인을 작성하는 경우 앱 서비스는 소스 코드를 보고, 앱을 복제하여 이슈를 작성하고 관리할 수 있는 Git 저장소를 작성합니다. 또한 전용 Git Lab Lab 환경 및 지속적 Delivery Pipeline에 대한 액세스도 제공됩니다. 이는 사용자가 선택하는 배치 대상([Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 또는 [Virtual Server(VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial))에 맞게 사용자 정의됩니다.

{{site.data.keyword.cloud_notm}} 개발자 대시보드로부터 작성된 모든 도구 체인은 자동 배치로 구성됩니다.
{: note}

배치 대상을 선택하고 지속적 딜리버리를 구성하려면 다음 단계를 완료하십시오. 

1. 앱 세부사항 페이지에서 **지속적 딜리버리 구성**을 클릭하십시오. 
2. 배치 대상을 선택하십시오. 선택하는 대상의 지시사항에 따라 배치 대상을 설정하십시오.
  * **[IBM Kubernetes Service](/docs/containers?topic=containers-app)에 배치**합니다. 이 선택사항은 고가용성의 애플리케이션 컨테이너를 배치하고 관리하기 위해 작업자 노드라는 호스트 클러스터를 작성합니다. 클러스터를 작성하거나 기존 클러스터에 배치할 수 있습니다.
  * **Cloud Foundry에 배치**합니다. 이 선택사항은 기본 인프라를 관리할 필요 없이 클라우드 기본 앱을 배치할 수 있도록 합니다. 계정에 {{site.data.keyword.cfee_full_notm}}에 대한 액세스 권한이 있는 경우에는 **[퍼블릭 클라우드](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** 배치자 유형을 선택하거나, 사용자 엔터프라이즈 전용으로 Cloud Foundry 애플리케이션을 호스팅하는 격리된 환경을 생성하고 관리하는 데 사용할 수 있는 **[엔터프라이즈 환경](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)** 배치자 유형을 선택할 수 있습니다.
  * **Virtual Server에 배치**합니다. 이 선택사항은 가상 서버를 프로비저닝하고, 앱을 포함하는 이미지를 로드하고, DevOps 도구 체인을 작성하고 첫 번째 배치 사이클을 시작합니다.

배치 대상을 선택하고 구성하면 앱 세부사항 페이지에 지속적 딜리버리가 구성되었음이 표시됩니다. **저장소 보기**를 클릭하면 앱 소스 코드가 포함된 저장소를 확인할 수 있습니다. 

## 5단계. 앱 배치
{: #deploy-starterkit}

{{site.data.keyword.cloud_notm}} 개발자 대시보드에서 작성되는 모든 DevOps 도구 체인은 자동 배치를 사용하도록 구성됩니다.
{: note}

배치 대상을 선택한 후, 새 도구 체인의 파이프라인 컴포넌트를 열어 초기 빌드 및 배치 프로세스를 시작하고 나면 몇 분 내에 새 앱을 확인할 수 있습니다.

1. 앱 세부사항 페이지에서 **도구 체인 보기**를 클릭하십시오. 
2. 빌드를 시작하고 배치를 관리하며 로그 및 히스토리를 볼 수 있는 **Delivery Pipeline**을 클릭하십시오.

도구 체인이 적절히 구성되면 저장소의 마스터 분기에 대한 각 병합마다 빌드-배치 주기가 자동으로 시작됩니다. 자세한 정보는 [빌드 및 배치](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)를 참조하십시오.

[`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) 명령을 실행하면 명령행에서 앱을 배치할 수 있습니다. 자세한 정보는 [CLI를 사용하여 앱 배치](/docs/apps?topic=creating-apps-deploying-apps#deploy-cli)를 참조하십시오. 

## 6단계. 앱이 실행 중인지 확인
{: #verify-starterkit}

앱을 배치하고 나면 Delivery Pipeline 또는 명령행이 사용자를 앱의 URL로 이동시킵니다.

1. DevOps 도구 체인에서 **Delivery Pipeline**을 클릭한 후 **배치 단계**를 선택하십시오.
2. **로그 및 히스토리 보기**를 클릭하십시오.
3. 로그 파일에서 애플리케이션 URL을 찾으십시오.

    로그 파일의 끝에서 단어 `urls` 또는 `view`를 찾으십시오. 예를 들면, 로그 파일에서 `urls: my-app-devhost.mybluemix.net` 또는 `View the application health at: http://<ipaddress>:<port>/health`와 같은 행을 볼 수 있습니다.

4. 브라우저에서 해당 URL로 이동하십시오. 앱이 실행 중인 경우에는 `Congratulations` 또는 `{"status":"UP"}`와 같은 항목을 포함하는 메시지가 표시됩니다.

명령행을 사용하는 경우에는 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 명령을 사용하여 앱의 URL을 보십시오. 그 후 브라우저에서 해당 URL로 이동하십시오.
