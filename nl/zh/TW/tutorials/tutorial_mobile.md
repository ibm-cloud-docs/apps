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

# 建立行動應用程式
{: #tutorial-mobile}

{{site.data.keyword.cloud}} 提供行動入門範本套件，以協助您快速建立行動應用程式。請從行動入門範本套件選取語言、架構及工具，以開始使用預先配置的應用程式。或者，您可以使用基本入門範本套件來建立自訂的行動應用程式。
{: shortdesc}

## 開始之前
{: #prereqs-mobile}

安裝 [{{site.data.keyword.dev_cli_long}} 指令行介面 (CLI)](/docs/cli?topic=cloud-cli-getting-started)。

## 使用入門範本套件建立行動應用程式
{: #create-mobile}

若要使用入門範本套件來建立行動應用程式，請完成下列步驟：

1. 從 {{site.data.keyword.dev_console}} 的[行動入門範本套件](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示") 頁面，根據您要的特性選取入門範本套件。例如，選取 **Watson Visual Recognition**。
2. 輸入應用程式名稱。針對本指導教學，請使用 `WatsonApp`。
3. 選用。提供標記以分類應用程式。如需相關資訊，請參閱[使用標籤](/docs/resources?topic=resources-tag)。
4. 選取平台。針對本指導教學，請選取 **iOS Swift**。部分入門範本套件可能只提供一種語言。
5. 選取定價方案。針對本指導教學，請使用**精簡**選項。如果需要任何服務，這些服務會自動定義在入門範本套件中。
6. 按一下**建立**。

## 建立自訂行動應用程式
{: #create-mobile-basic}

若要建立自訂行動應用程式，請完成下列步驟：

1. 從 {{site.data.keyword.dev_console}} 的[行動入門範本套件](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示") 頁面，選取**建立應用程式**磚。
2. 輸入應用程式的名稱。針對本指導教學，請鍵入 `CustomMobile`。
3. 您可以選擇性地提供標記來分類應用程式。如需相關資訊，請參閱[使用標籤](/docs/resources?topic=resources-tag)。
4. 選取**建立新應用程式**作為起始點。
5. 選取**行動**作為應用程式類型。
6. 選取語言及架構。部分入門範本套件可能只提供一種語言。
7. 選取定價方案。您可以針對本指導教學使用免費選項。
8. 按一下**建立**。

## 使用 CLI 建立行動應用程式
{: #create-mobile-cli}

若要使用 [{{site.data.keyword.dev_cli_long}} CLI](/docs/cli?topic=cloud-cli-getting-started) 建立行動應用程式，請完成下列步驟：

1. 開啟終端機，並導覽至要在其中建立應用程式的目錄。
2. 執行 `ibmcloud dev create` 指令。
3. 從應用程式類型清單中，選取**行動應用程式**選項。
4. 從清單中，選取行動平台：Android 或 Swift。
5. 選取入門範本套件。
6. 輸入應用程式的名稱。
7. 如果已新增服務，則系統會提示您為每個服務選取地區和定價方案。

應用程式會在現行工作目錄中建立。

## 新增服務（選用）
{: #resources-mobile}

視您選取的入門範本套件而定，部分服務可能已連接至您的應用程式。您可以新增服務，藉由 Watson 的認知能力加強您的應用程式，也可以新增行動服務或安全服務。針對本指導教學，請新增工作區以便管理您的資料。

若要將服務新增至應用程式，請完成下列步驟：

1. 在**應用程式詳細資料**頁面上，按一下**建立服務**。
2. 選取您要的服務類型。例如，選取**資料庫** > **下一步** > **Cloudant** > **下一步**。
3. 選取定價方案。針對本指導教學，請使用**精簡**選項。
4. 按一下**建立**。

## 下載程式碼
{: #mobile-download-code}

若要下載應用程式碼並在本端使用它，請完成下列步驟：

1. 在**應用程式詳細資料**頁面上，按一下**下載程式碼**。
2. 將應用程式匯入至整合開發環境。
3. 修改並儲存程式碼。

## 執行行動應用程式
{: #run-mobile-app}

### 在 Xcode 中執行 Swift 應用程式
{: #run_swift}

如果您使用 iOS Swift 作為實作語言，請完成下列步驟：

1. 在 Markdown 檢視器中開啟 `README.md` 檔案，以檢閱配置應用程式的步驟。
2. 開啟您的終端機並導覽至應用程式資料夾，然後執行下列指令：
    1. 如果您需要設定 CocoaPods 儲存庫，請執行 `pod setup`。
    2. 如果您需要更新現有的 Pod，請執行 `pod update`。
    3. 執行 `pod install` 來安裝應用程式的 Pod。
3. 開啟您的 `<appname>.xcworkspace` Xcode 工作區。
4. 執行應用程式。

### 在 Android Studio 中執行 Android 應用程式
{: #run_android}

如果您使用 Android 作為行動應用程式的平台，請完成下列步驟：

1. 在 Markdown 檢視器中開啟 `README.md` 檔案，以配置應用程式。
2. 在 Android Studio 中開啟 `BasicProject-Android` 應用程式。
3. 執行應用程式。

## 相關資訊
{: #related-mobile}

您可以透過瀏覽下列指導教學來進一步瞭解行動應用程式：

 * [iOS 行動應用程式與 Push Notifications](/docs/tutorials?topic=solution-tutorials-ios-mobile-push-analytics)
 * [Android 原生行動行動應用程式與 Push Notifications](/docs/tutorials?topic=solution-tutorials-android-mobile-push-analytics)
 * [行動應用程式與無伺服器後端](/docs/tutorials?topic=solution-tutorials-serverless-mobile-backend)
