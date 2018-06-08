---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-22"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 스타터 킷을 사용한 모바일 애플리케이션 작성
{: #tutorial}

모바일 기본 스타터로부터 모바일 앱을 작성할 수 있습니다. 필요한 도구를 설치하는 방법 및 앱을 Xcode 및 Android Studio에서 실행하는 단계를 알아볼 수 있습니다.
{: shortdesc}

## 도구 설치
{: #before-you-begin}

[개발자 도구](/docs/cli/idt/index.html#create){: new_window}를 설치하십시오.

## 앱 작성 방법 선택
{: #choose_how}

다음 방법 중 하나를 사용하여 앱을 작성할 수 있습니다.
- 웹 기반 [{{site.data.keyword.dev_console}}](#create-devex)
- 로컬 명령 중심 [{{site.data.keyword.dev_cli_notm}}](#create-cli)

## {{site.data.keyword.dev_console}}을 사용하여 앱 작성
{: #create-devex}

1. {{site.data.keyword.Bluemix}}에 {{site.data.keyword.dev_console}} 앱을 작성하십시오.

    1. {{site.data.keyword.dev_console}}의 [스타터 킷 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) 페이지에서 원하는 기능에 따라 스타터 킷을 선택하십시오. 예를 들어, Watson Language 애플리케이션인 경우에는 **Watson Language**로 이동하여 **스타터 킷 선택**을 클릭하십시오.

    2. 앱 이름을 입력하십시오. 이 튜토리얼의 경우 `WatsonApp`을 사용하십시오.   

    3. 언어 플랫폼을 선택하십시오. 이 튜토리얼의 경우에는 `Swift`를 사용하십시오.

    4. **작성**을 클릭하십시오.

### 선택사항: 서비스 추가
{: #add-services}

1. **앱** 페이지에서 앱을 선택하십시오.

2. **서비스 추가**를 클릭하십시오.

3. 원하는 서비스의 종류를 선택하십시오. 이 튜토리얼의 경우에는 **보안** > **다음** > **앱 ID** > **다음**을 선택하십시오.

4. 서비스 이름을 입력하고 **작성**을 클릭하십시오.

5. 인증 구성에 대한 자세한 정보는 [ID 제공자 구성 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/services/appid/identity-providers.html){: new_window}을 참조하십시오.

6. 분석 구성에 대한 자세한 정보는 [{{site.data.keyword.mobileanalytics_short}} 시작하기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/services/mobileanalytics/index.html){: new_window}를 참조하십시오.

7. {{site.data.keyword.cloudant_short_notm}} 구성에 대한 자세한 정보는 [{{site.data.keyword.cloudant_short_notm}} 시작하기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/services/Cloudant/index.html){: new_window}를 참조하십시오.

8. {{site.data.keyword.objectstorageshort}} 구성에 대한 자세한 정보는 [{{site.data.keyword.objectstorageshort}} 시작하기 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](/docs/services/ObjectStorage/index.html){: new_window}를 참조하십시오.

9. 푸시 알림 추가에 대한 자세한 정보는 [푸시 알림 문서](/docs/services/mobilepush/c_overview_push.html#overview-push)를 참조하십시오.

### 앱 코드 생성
{: #generate-code}

1. **앱** 페이지에서 앱을 선택하십시오.

2. 앱 아카이브를 다운로드하려면 **코드 다운로드**를 클릭하십시오.

### 앱에 대한 작업 시작
{: #code}

다운로드한 앱에 대해 작업을 시작하십시오.

1. 아카이브된 파일을 펼치십시오.

2. 새 앱 디렉토리로 이동하십시오.

3. {{site.data.keyword.dev_cli_notm}}을 사용하여 진행하십시오.


## {{site.data.keyword.dev_cli_notm}}을 사용하여 앱 작성
{: #create-cli}

1. [{{site.data.keyword.dev_cli_short}}](/docs/cli/idt/index.html)을 설치했는지 확인하십시오.

2. 터미널 프롬프트에서 원하는 로컬 디렉토리로 이동한 후 다음 명령을 실행하십시오.

	```
	ibmcloud dev create
	```
	{: codeblock}

3. 프롬프트가 표시되면 다음 값을 제공하십시오.

	* "모바일 클라이언트"의 앱 유형 선택(옵션 2)
	* 구현 언어를 "iOS Swift"로 선택(옵션 3)
	* "모바일 앱: Basic" 스타터 킷 선택(옵션 1)
	* 앱 이름 입력: `MobileBasicProject`

    참고: 실제 선택 번호는 도구 업데이트에 따라 변경될 수 있습니다.

4. 앱에 서비스를 추가하려는 경우 질문 프롬프트에서 `y`를 입력하고 나머지 질문에 답하십시오.

5. `MobileBasicProject`가 작성되어 저장되고 나면 `MobileBasicProject/MobileBasicProject-Swift` 폴더로 이동하십시오.

### Xcode에서 Swift 앱 실행
{: #run_swift}

1. 마크다운 뷰어에서 `README.md` 파일을 열어 앱 구성 단계를 검토하십시오.

2. 터미널을 열고 앱 폴더로 이동한 후 다음 명령을 실행하십시오.
    1. CocoaPods 저장소를 설정해야 하는 경우 `pod setup`을 실행하십시오.
    2. 기존 팟(Pod)을 업데이트해야 하는 경우 `pod update`를 실행하십시오.
    3. 앱에 대한 팟(Pod)을 설치하려면 `pod install`을 실행하십시오.

3. `<appname>.xcworkspace` Xcode 작업공간을 여십시오.

4. 앱을 실행하십시오.

### Xcode에서 Cordova 앱 실행
{: #run_cordova_xcode}

구현 언어로 Cordova를 사용하도록 선택한 경우에는 다음 지시사항을 따르십시오.

1. 마크다운 뷰어에서 `README.md` 파일을 열어 앱을 구성하십시오.

2. Xcode에서 `platforms/ios` 앱을 여십시오.

3. 앱을 실행하십시오.

### Android Studio에서 Cordova 앱 실행
{: #run_cordova_studio}

모바일 앱의 플랫폼으로 Cordova를 사용하도록 선택한 경우에는 이 섹션을 사용하십시오.

1. `BasicProject-Cordova.zip` 파일의 압축을 푸십시오.

2. 마크다운 뷰어에서 `README.md` 파일을 열어 앱을 구성하십시오.

3. Android Studio에서 `platforms/android` 앱을 여십시오.

4. 앱을 실행하십시오.

### Android Studio에서 Android 앱 실행
{: #run_android}

모바일 앱의 플랫폼으로 Android를 사용하도록 선택한 경우에는 이 섹션을 사용하십시오.

1. 마크다운 뷰어에서 `README.md` 파일을 열어 앱을 구성하십시오.

2. Android Studio에서 `BasicProject-Android` 앱을 여십시오.

3. 앱을 실행하십시오.
