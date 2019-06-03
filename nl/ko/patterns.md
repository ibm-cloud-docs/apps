---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-22"

keywords: supported architecture, supported languages cloud, web app, microservices, mobile, programming languages, app types, common architecture, cloud app

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# 클라우드 앱의 공통 아키텍처
{: #patterns}

{{site.data.keyword.cloud_notm}}의 스타터 킷은 검증된 아키텍처를 사용하여 앱을 작성하는 데 도움을 줍니다. 각 앱은 서로 다르지만, 알려진 아키텍처 패턴을 앱의 기초로 사용하면 신뢰할 수 있는 결과를 신속히 얻을 수 있습니다. 스타터 킷으로부터 앱을 작성하는 경우 런타임과 같은 컴포넌트와 함께 여러 가지 다양한 패턴 유형 중에 하나를 선택하여 패턴을 채웁니다.
{:shortdesc}

## 웹 앱
{: #web}

웹 앱 패턴은 HTML, JavaScript 및 스타일시트와 같은 웹 컨텐츠를 웹 서버에 제공하는 앱을 작성합니다. {{site.data.keyword.cloud_notm}}는 여러 웹 앱 스타터 킷을 제공합니다.

* Basic - 정적 `index.html` 파일, 빈 기본 스타일시트 및 JavaScript 파일을 제공합니다.
* React - 사용자 인터페이스 빌드를 위한 세련된 프레임워크입니다. 소스 파일은 `src/client/app`에 있으며, webpack으로 컴파일되고 공용 디렉토리에서 제공됩니다.

웹 앱 패턴의 스타터 킷은 [{{site.data.keyword.cloud_notm}} 앱 서비스 개발자 대시보드](https://{DomainName}/developer/appservice/dashboard){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")에서 찾을 수 있습니다.

## 마이크로서비스
{: #microservice}

마이크로서비스 앱은 기본 상태 엔드포인트 및 REST API를 포함하는 백엔드 마이크로서비스를 빌드하는 데 필요한 기반을 제공합니다. 생성되는 앱에는 마이크로서비스 자체 및 연결된 클라우드 서비스 둘 다에 필요한 모든 종속 항목이 포함되어 있습니다.

언어 및 프레임워크 요구사항에 맞는 마이크로서비스 스타터 킷을 선택하십시오. 마이크로서비스 패턴의 스타터 킷은 [{{site.data.keyword.cloud_notm}} 앱 서비스 개발자 대시보드](https://{DomainName}/developer/appservice/dashboard){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")에서 찾을 수 있습니다.

## 모바일
{: #mobile}

모바일 앱은 중요한 클라이언트 측 컴포넌트를 포함하고 있으므로 다른 패턴과는 다릅니다. 이 패턴은 푸시 알림, 인증 및 모바일 분석과 같은 모바일 서비스에 대한 직접 연결을 포함할 수 있습니다. 모바일 서비스를 MBaaS(Mobile Backend as a Service) 또는 MBaaS 패턴이라고 합니다. 또한 전용 프론트 엔드를 위한 백엔드를 갖추고 있을 수 있습니다.

{{site.data.keyword.cloud_notm}}에서는 몇 가지 iOS Swift, Android 및 Cordova용 모바일 스타터 킷을 제공합니다. 모바일 패턴의 스타터 킷은 [{{site.data.keyword.cloud_notm}} 모바일 개발자 대시보드](https://{DomainName}/developer/mobile/dashboard){: new_window} ![외부 링크 아이콘](../icons/launch-glyph.svg "외부 링크 아이콘")에서 찾을 수 있습니다.

## 언어
{: #languages}

{{site.data.keyword.cloud_notm}}에서는 다양한 언어 및 프레임워크에서 사용 가능한 스타터 킷을 제공합니다. 예를 들어, 클라우드 마이크로서비스 스타터 킷은 Node.js 옵션을 제공하는 반면, 데이터 분석과 깊이 관련된 스타터 킷은 Python 또는 Go를 포함할 수 있습니다. 여기에는 {{site.data.keyword.cloud_notm}} 스타터 킷에서 사용된 몇 가지 일반적인 언어가 언급되어 있습니다.

|프로그래밍 언어 |설명 |개발 프레임워크 |
|-----|-----|-----|
|Java |[Java](/docs/runtimes/liberty?topic=liberty-getting-started)는 엔터프라이즈급 애플리케이션을 빌드할 때 매우 유용합니다. 그러나 Java 8에서 새 기능이 도입되면서 Liberty 등의 경량 런타임 및 Spring Boot 등의 프레임워크와의 결합을 통해 Java가 마이크로서비스 빌드에도 적합하게 되었습니다. Java는 Android 앱에서 널리 사용되는 프로그래밍 언어입니다. |Spring, Liberty, Android |
|Swift |[Swift](/docs/runtimes/swift?topic=Swift-getting-started)는 Objective C를 대체하도록 디자인된 2014년에 제작된 신규 프로그래밍 언어이며 2015년 12월에 오픈 소스로 전환되었습니다. 현재는 iOS, macOS, 웹 서비스의 빌드와 x86, ARM 또는 z/Architecture를 사용하는 Linux 및 macOS 운영 체제의 시스템 소프트웨어 빌드에 사용됩니다. 이는 스크립팅 언어와 유사하게 작성되지만 낮은 프로세서 사용량으로 C와 유사한 고성능을 얻을 수 있도록 컴파일되며 클라우드 런타임에 적합합니다. 이 언어는 Java에서 볼 수 있는 강한 정적 유형 시스템을 사용하지만 JavaScript에서 볼 수 있는 함수 스타일 및 비동기 루틴을 사용합니다. 성능 면에서 매우 뛰어난 언어로, 소스는 LLVM 컴파일러 도구 체인을 사용하는 네이티브 코드로 컴파일됩니다. 또한 C로 작성된 다른 언어의 시스템 라이브러리를 쉽게 사용할 수 있습니다. Swift는 클라이언트 측 앱과 서버 측 앱을 코딩하는 데 모두 사용할 수 있으므로, 개발자들은 보통 클라이언트에서 서버 또는 그 반대로 함수를 쉽게 마이그레이션해야 하는 경우 Swift를 사용합니다. |Kitura, iOS|
|Node.js |[Node.js](/docs/runtimes/nodejs?topicid=Nodejs-getting-started)는 이벤트 중심의 비차단 I/O 모델을 사용하는 JavaScript 런타임으로, 경량이고 효율적입니다. 이는 웹 애플리케이션, 프론트 엔드를 위한 백엔드 패턴 및 마이크로서비스의 처리량 및 확장성 면에서 뛰어납니다. Node.js의 패키지 레지스트리(npm)는 대규모 오픈 소스 모듈 콜렉션에 대한 액세스를 제공하며 애플리케이션 개발을 가속화할 수 있는 광범위한 기능을 제공합니다. |Express|
|JavaScript|JavaScript는 웹 페이지에서 대화식 효과를 작성합니다. JavaScript, HTML 및 CSS는 대부분의 웹 페이지의 기초입니다. JavaScript 코드는 Cordova 플러그인으로 랩핑되면 기본 디바이스 함수를 최대한 활용할 수 있습니다. 웹 기술을 가진 개발자는 모바일 앱을 쉽게 작성할 수 있으며, 해당 앱 코드를 웹 및 모바일에서 재사용할 수 있습니다.| Cordova|
|Python |[Python](/docs/runtimes/python?topic=Python-getting_started)은 가독성에 중점을 둔 범용의 인터프리트(interpreted) 프로그래밍 언어입니다. Python을 사용하면 프로그래머가 다른 언어보다 적은 코드 행으로 함수를 구현할 수 있습니다. 이러한 언어 특성으로 인해 객체 지향형, 함수형 또는 명령형 코드를 작성할 수 있습니다. Python은 일반적으로 자연어 태스크의 처리에 사용됩니다. |Flask, Django|


