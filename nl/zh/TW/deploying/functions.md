---

copyright:
  years: 2018
lastupdated: "2018-07-25"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 建立無伺服器應用程式
{: #serverless}

要進行無伺服器開發，您可以使用 IBM 的函數即服務 (FaaS) 供應項目 {{site.data.keyword.openwhisk}}。您可以使用 {{site.data.keyword.openwhisk_short}} 執行應用程式邏輯以回應事件，或透過 HTTP 導向來自 Web 或行動應用程式的呼叫，而不必佈建或管理伺服器。{{site.data.keyword.openwhisk_short}} 會執行系統管理，例如自動擴充、可用性管理及維護，以便身為開發人員的您可以專注於撰寫應用程式邏輯。
{:shortdesc}

您可以使用 {{site.data.keyword.openwhisk_short}} 使用者介面 (UI) 或指令行介面 (CLI) 來開發應用程式。兩者都具有類似的應用程式開發功能。CLI 提供部署與作業的更多控制。如需 {{site.data.keyword.openwhisk_short}} 的更多詳細資訊，請參閱完整的[文件](/docs/openwhisk/index.html)。

## {{site.data.keyword.openwhisk_short}} 使用者介面
{: #ui}

在您的[瀏覽器 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.{DomainName}/openwhisk/actions){:new_window} 試用 {{site.data.keyword.openwhisk_short}}。移至[概念 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.{DomainName}/openwhisk/learn){:new_window} 頁面，以取得 {{site.data.keyword.openwhisk_short}} 使用者介面的快速導覽。

## 使用 CLI 進行開發
{: #openwhisk_start_configure_cli}

若要進一步瞭解如何使用 {{site.data.keyword.openwhisk_short}} CLI 來安裝及開發，請參閱[設定 {{site.data.keyword.openwhisk_short}} CLI ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://console.{DomainName}/openwhisk/cli){:new_window}。

## 將 API 及資料集公開為 Web 動作
{: #containers}

依預設，{{site.data.keyword.openwhisk_short}} 會定義需要鑑別金鑰的動作。在正式作業的行動環境中，經常必須根據 OAuth 流程授權行動用戶端，以公開 API 及特定資料集。

{{site.data.keyword.openwhisk_short}} 讓開發人員能將它們的函數公開為 Web 動作（會加上註釋）以快速建置 Web 應用程式。您可以用已加上註釋的動作來進行後端邏輯程式設計，您的 Web 應用程式可以匿名地存取這些動作，而不需要 {{site.data.keyword.openwhisk_short}} 鑑別金鑰。

若要將動作公開為 Web 動作，請移至動作的**端點**標籤，然後選取**啟用為 Web 動作**。

現在，使用者可以從瀏覽器或 cURL 要求聯繫動作，例如：

```
curl https://openwhisk.ng.bluemix.net/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

**輸出：**

```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} 為 iOS 及 watchOS 裝置提供[行動 SDK](/docs/openwhisk/openwhisk_mobile_sdk.html#mobile-sdk)，讓行動應用程式能輕鬆地傳送遠端觸發程式及呼叫遠端動作。它也提供[無伺服器架構 SDK ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](/docs/openwhisk/openwhisk_goserverless.html){:new_window} 以啟用無伺服器應用程式。
