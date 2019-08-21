---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-17"

keywords: apps, mobile, mobile app, starter kit, developer tools, devops toolchain, toolchain, create mobile app, mobile starter kit, android, ios, swift, xcode

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 모바일 앱 작성
{: #tutorial-mobile}

{{site.data.keyword.cloud}}는 모바일 애플리케이션을 빠르게 작성할 수 있도록 모바일 스타터 킷을 제공합니다. 모바일 스타터 킷에서 언어, 프레임워크 및 도구를 선택하여 사전 구성된 앱에 대한 작업을 시작하십시오. 또는 기본 스타터 킷을 사용하여 사용자 정의 모바일 앱을 작성할 수 있습니다.
{: shortdesc}

## 시작하기 전에
{: #prereqs-mobile}

[{{site.data.keyword.dev_cli_long}} 명령행 인터페이스(CLI)](/docs/cli?topic=cloud-cli-getting-started)를 설치하십시오.

## 스타터 킷을 사용한 모바일 앱 작성
{: #create-mobile}

스타터 킷을 사용하여 모바일 앱을 작성하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.dev_console}}의 [모바일 스타터 킷](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘") 페이지에서 원하는 기능에 따라 스타터 킷을 선택하십시오. 예를 들어, **Watson 시작적 인식**을 선택하십시오.
2. 앱 이름을 입력하십시오. 이 튜토리얼의 경우 `WatsonApp`을 사용하십시오.
3. 선택사항. 앱을 분류하기 위한 태그를 제공하십시오. 자세한 정보는 [태그에 대한 작업](/docs/resources?topic=resources-tag)을 참조하십시오.
4. 플랫폼을 선택하십시오. 이 튜토리얼의 경우에는 **iOS Swift**를 선택하십시오. 일부 스타터 킷은 하나의 언어로만 사용 가능할 수 있습니다.
5. 가격 플랜을 선택하십시오. 이 튜토리얼의 경우 **Lite** 옵션을 사용하십시오. 서비스가 필요한 경우, 스타터 킷에 자동으로 정의됩니다.
6. **작성**을 클릭하십시오.

## 사용자 정의 모바일 앱 작성
{: #create-mobile-basic}

사용자 정의 모바일 앱을 작성하려면 다음 단계를 완료하십시오.

1. {{site.data.keyword.dev_console}}의 [모바일 스타터 킷](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘") 페이지에서 **앱 작성** 타일을 선택하십시오.
2. 앱의 이름을 입력하십시오. 이 튜토리얼의 경우에는 `CustomMobile`을 사용하십시오.
3. 앱을 분류하기 위한 태그를 선택적으로 제공할 수 있습니다. 자세한 정보는 [태그에 대한 작업](/docs/resources?topic=resources-tag)을 참조하십시오.
4. 시작점으로 **새 앱 작성**을 선택하십시오.
5. **모바일**을 앱 유형으로 선택하십시오.
6. 언어 및 프레임워크를 선택하십시오. 일부 스타터 킷은 하나의 언어로만 사용 가능할 수 있습니다.
7. 가격 플랜을 선택하십시오. 이 튜토리얼의 경우 무료 옵션을 사용할 수 있습니다.
8. **작성**을 클릭하십시오.

## CLI를 사용한 모바일 앱 작성
{: #create-mobile-cli}

[{{site.data.keyword.dev_cli_long}} CLI](/docs/cli?topic=cloud-cli-getting-started)를 사용하여 모바일 앱을 작성하려면 다음 단계를 완료하십시오.

1. 터미널을 열고 앱을 작성할 디렉토리로 이동하십시오.
2. `ibmcloud dev create` 명령을 실행하십시오.
3. 앱 유형 목록에서 **모바일 앱** 옵션을 선택하십시오.
4. 목록에서 모바일 플랫폼, 즉, Android 또는 Swift를 선택하십시오.
5. 스타터 킷을 선택하십시오.
6. 앱의 이름을 입력하십시오.
7. 서비스가 추가되면 각 서비스에 대해 지역 및 가격 플랜을 선택하라는 프롬프트가 표시됩니다.

현재 작업 디렉토리에 앱이 작성됩니다.

## 서비스 추가(선택사항)
{: #resources-mobile}

선택한 스타터 킷에 따라 일부 서비스가 이미 앱에 연결되어 있을 수 있습니다. Watson의 코그너티브 기능으로 앱을 향상시키는 서비스를 추가하거나 모바일 서비스 또는 보안 서비스를 추가할 수 있습니다. 이 튜토리얼의 경우 데이터를 관리할 위치를 추가하십시오.

앱에 서비스를 추가하려면 다음 단계를 완료하십시오.

1. **앱 세부사항** 페이지에서 **서비스 작성**을 클릭하십시오.
2. 원하는 서비스의 종류를 선택하십시오. 예를 들어, **데이터베이스** > **다음** > **Cloudant** > **다음**을 선택하십시오.
3. 가격 플랜을 선택하십시오. 이 튜토리얼의 경우 **Lite** 옵션을 사용하십시오.
4. **작성**을 클릭하십시오.

## 코드 다운로드
{: #mobile-download-code}

앱 코드를 다운로드하여 로컬로 작업하려면 다음 단계를 완료하십시오.

1. **앱 세부사항** 페이지에서 **코드 다운로드**를 클릭하십시오.
2. 앱을 통합된 개발 환경으로 가져오십시오.
3. 코드를 수정한 후 저장하십시오.

## 모바일 앱 실행
{: #run-mobile-app}

### Xcode에서 Swift 앱 실행
{: #run_swift}

iOS Swift를 구현 언어로 사용하는 경우, 다음 단계를 완료하십시오.

1. 마크다운 뷰어에서 `README.md` 파일을 열어 앱 구성 단계를 검토하십시오.
2. 터미널을 열고 앱 폴더로 이동한 후 다음 명령을 실행하십시오.
    1. CocoaPods 저장소를 설정해야 하는 경우 `pod setup`을 실행하십시오.
    2. 기존 팟(Pod)을 업데이트해야 하는 경우 `pod update`를 실행하십시오.
    3. 앱에 대한 팟(Pod)을 설치하려면 `pod install`을 실행하십시오.
3. `<appname>.xcworkspace` Xcode 작업공간을 여십시오.
4. 앱을 실행하십시오.

### Android Studio에서 Android 앱 실행
{: #run_android}

Android를 모바일 앱의 플랫폼으로 사용하는 경우, 다음 단계를 완료하십시오.

1. 마크다운 뷰어에서 `README.md` 파일을 열어 앱을 구성하십시오.
2. Android Studio에서 `BasicProject-Android` 앱을 여십시오.
3. 앱을 실행하십시오.

## 관련 정보
{: #related-mobile}

다음 튜토리얼을 탐색하여 모바일 앱에 대해 자세히 알아볼 수 있습니다.

 * [푸시 알림을 사용한 iOS 모바일 애플리케이션](/docs/tutorials?topic=solution-tutorials-ios-mobile-push-analytics)
 * [푸시 알림을 사용한 Android 네이티브 모바일 애플리케이션](/docs/tutorials?topic=solution-tutorials-android-mobile-push-analytics)
 * [서버리스 백엔드를 사용한 모바일 애플리케이션](/docs/tutorials?topic=solution-tutorials-serverless-mobile-backend)
