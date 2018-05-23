---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-02"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 使用入門範本套件來建立行動應用程式
{: #tutorial}

您可以從行動基本入門範本建立行動應用程式。您將會看到如何安裝所需的工具，以及在 Xcode 和 Android Studio 中執行應用程式的步驟。
{: shortdesc}

## 安裝工具
{: #before-you-begin}

安裝[開發人員工具](/docs/cli/idt/index.html#create){: new_window}。

## 選擇如何建立應用程式
{: #choose_how}

您可以使用下列其中一種方法來建立應用程式：
- Web 型的 [{{site.data.keyword.dev_console}}](#create-devex)
- 本端指令驅動的 [{{site.data.keyword.dev_cli_notm}}](#create-cli)

## 使用 {{site.data.keyword.dev_console}} 建立應用程式
{: #create-devex}

1. 在 {{site.data.keyword.Bluemix}} 中建立 {{site.data.keyword.dev_console}} 應用程式。

    1. 從 {{site.data.keyword.dev_console}} 的[入門範本套件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) 頁面中，根據您要的功能選取入門範本套件。例如，若為 Watson 應用程式，請移至 **Watson 語言**，然後按一下**選取入門範本套件**。

    2. 輸入應用程式名稱。針對本指導教學，請使用 `WatsonApp`。   

    3. 選取語言平台。針對本指導教學，請使用 `Swift`。

    4. 按一下**建立**。

### 選用項目：新增服務
{: #add-services}

1. 在**應用程式**頁面中選取您的應用程式。

2. 按一下**新增服務**。

3. 選取您要的服務類型。針對本指導教學，請選取**安全** > **下一步** > **App ID** > **下一步**。

4. 輸入您的服務名稱，然後按一下**建立**。

5. 如需配置鑑別的相關資訊，請參閱[配置身分提供者 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/services/appid/identity-providers.html){: new_window}。

6. 如需配置分析的相關資訊，請參閱[開始使用 {{site.data.keyword.mobileanalytics_short}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/services/mobileanalytics/index.html){: new_window}。

7. 如需配置 {{site.data.keyword.cloudant_short_notm}} 的相關資訊，請參閱[開始使用 {{site.data.keyword.cloudant_short_notm}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/services/Cloudant/index.html){: new_window}。

8. 如需配置 {{site.data.keyword.objectstorageshort}} 的相關資訊，請參閱[開始使用 {{site.data.keyword.objectstorageshort}} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/services/ObjectStorage/index.html){: new_window}。

9. 如需新增推送通知的相關資訊，請參閱 [Push Notifications 文件](/docs/services/mobilepush/c_overview_push.html#overview-push)。

### 產生應用程式碼
{: #generate-code}

1. 在**應用程式**頁面中選取您的應用程式。

2. 按一下**下載程式碼**以下載您的應用程式保存檔。

### 開始使用您的應用程式
{: #code}

開始使用下載的應用程式：

1. 展開保存檔。

2. 導覽至新的應用程式目錄。

3. 使用 {{site.data.keyword.dev_cli_notm}} 繼續進行。


## 使用 {{site.data.keyword.dev_cli_notm}} 建立應用程式
{: #create-cli}

1. 確定您已安裝 [{{site.data.keyword.dev_cli_short}}](/docs/cli/idt/index.html)。

2. 在「終端機」提示下，導覽至您選擇的本端目錄，然後執行下列指令。

	```
	bx dev create
	```
	{: codeblock}

3. 當出現提示時，請提供下列值：

	* 選取應用程式類型「行動用戶端」，選項 2
	* 選取實作語言 iOS Swift，選項 3
	* 選取入門範本套件「行動應用程式：基本」，選項 1
	* 輸入應用程式的名稱：`MobileBasicProject`

    附註：實際選擇號碼可能會隨著工具加強而變。

4. 如果您要將服務新增至應用程式，請在問題提示處鍵入 `y`，並回答其餘的問題。

5. 順利建立並儲存 `MobileBasicProject` 之後，導覽至 `MobileBasicProject/MobileBasicProject-Swift` 資料夾。

### 在 Xcode 中執行 Swift 應用程式
{: #run_swift}

1. 在 Markdown 檢視器中開啟 `README.md` 檔案，以檢閱配置應用程式的步驟。

2. 開啟您的終端機並導覽至您的應用程式資料夾，然後執行下列指令：
    1. 如果您需要設定 CocoaPods 儲存庫，請執行 `pod setup`。
    2. 如果您需要更新現有的 Pod，請執行 `pod update`。
    3. 執行 `pod install` 來安裝應用程式的 Pod。

3. 開啟您的 `<appname>.xcworkspace` Xcode 工作區。

4. 執行應用程式。

### 在 Xcode 中執行 Cordova 應用程式
{: #run_cordova_xcode}

如果您選擇使用 Cordova 作為您的實作語言，請遵循這些指示。

1. 在 Markdown 檢視器中開啟 `README.md` 檔案，以配置應用程式。

2. 在 Xcode 中開啟 `platforms/ios` 應用程式。

3. 執行應用程式。

### 在 Android Studio 中執行 Cordova 應用程式
{: #run_cordova_studio}

如果您選擇使用 Cordova 作為行動應用程式的平台，請使用此區段。

1. 解壓縮 `BasicProject-Cordova.zip` 檔案。

2. 在 Markdown 檢視器中開啟 `README.md` 檔案，以配置應用程式。

3. 在 Android Studio 中開啟 `platforms/android` 應用程式。

4. 執行應用程式。

### 在 Android Studio 中執行 Android 應用程式
{: #run_android}

如果您選擇使用 Android 作為行動應用程式的平台，請使用此區段。

1. 在 Markdown 檢視器中開啟 `README.md` 檔案，以配置應用程式。

2. 在 Android Studio 中開啟 `BasicProject-Android` 應用程式。

3. 執行應用程式。
