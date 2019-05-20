---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-10"

keywords: apps, credentials, service, add service credentials, environment, deployment

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# 배치 환경에 수동으로 서비스 인증 정보 추가
{: #credentials_overview}

애플리케이션이 실행되는 환경에서 애플리케이션 로직으로 민감한 서비스 인증 정보(예: 데이터베이스 API 키 또는 비밀번호)를 가져오려고 합니다. 이 경우 소스 코드 저장소에 인증 정보를 보존할 필요가 없습니다.
{: shortdesc}

스타터 킷을 사용하여 앱을 작성하는 경우에는 환경이 자동으로 준비됩니다. 앱 배치 전에 서비스를 스타터 킷에 연결하면 서비스 인증 정보가 자동으로 환경에 추가됩니다.
{ :tip}

다음 경우에는 배치 환경에 서비스 인증 정보를 수동으로 추가해야 합니다. 

 * 자체 코드를 가져옵니다.
 * 앱이 배치된 후 스타터 킷 기반 앱에 서비스를 추가합니다. 

서비스 인증 정보를 추가하는 프로세스는 배치 대상과 프로그래밍 언어에 따라 다릅니다. 배치 대상에 대한 서비스 인증 정보의 구성에 관한 자세한 정보는 호스팅 환경 관련 문서를 참조하십시오. 

  * [{{site.data.keyword.containershort}}](/docs/containers?topic=containers-service-binding#adding_app)
  * Cloud Foundry 퍼블릭 또는 {{site.data.keyword.cfee_full}}
  * Virtual Server 인스턴스(로컬 Docker 컨테이너)

여러 언어 및 프레임워크에서는 애플리케이션별 구성 및 환경별 구성 모두에 대해 표준 라이브러리를 제공합니다. 자세한 정보는 다음 프로그래밍 안내서를 참조하십시오.

* [Java: 서비스 인증 정보에 대한 작업](/docs/java?topic=cloud-native-configuration)
* [Node.js 환경 구성](/docs/node?topic=nodejs-configure-nodejs)
* [Spring 환경 구성](/docs/java?topic=java-spring-configuration)
* [Swift 환경 구성](/docs/swift?topic=swift-configuration)
* [Go 환경 구성](/docs/go?topic=go-configure-go-env)
