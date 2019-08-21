---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-29"

keywords: apps, serverless, serverless app, functions, cli, api, sdk, create serverless app, serverless app tutorial

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# 建立無伺服器應用程式
{: #serverless}

對於無伺服器開發，您可以使用 {{site.data.keyword.openwhisk}}，這是 IBM 函數即服務 (FaaS) 供應項目。您可以使用 {{site.data.keyword.openwhisk_short}} 執行應用程式邏輯以回應事件，或透過 HTTP 導向來自 Web 或行動應用程式的呼叫，而不必佈建或管理伺服器。{{site.data.keyword.openwhisk_short}} 會執行系統管理，例如自動擴充、可用性管理及維護，以便身為開發人員的您可以專注於撰寫應用程式邏輯。
{:shortdesc}

可以使用下列兩種方法之一來開發無伺服器應用程式：
* {{site.data.keyword.openwhisk_short}} 使用者介面（使用者介面）。
* {{site.data.keyword.openwhisk_short}} 指令行介面 (CLI)，用於提供對部署和作業的更多控制權。
* {{site.data.keyword.openwhisk_short}} 入門範本套件，可在其中使用 DevOps 工具鏈和 Delivery Pipeline 配置持續交付。

如需 {{site.data.keyword.openwhisk_short}} 的詳細資訊，請參閱[文件](/docs/openwhisk?topic=cloud-functions-getting_started)。


## 使用 {{site.data.keyword.openwhisk_short}} 使用者介面進行開發
{: #serverless-apps-ui}

在您的[瀏覽器](https://{DomainName}/functions/actions){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 中試用 {{site.data.keyword.openwhisk_short}}。移至[概念 ](https://{DomainName}/functions/learn){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 頁面，以取得 {{site.data.keyword.openwhisk_short}} 使用者介面的快速導覽。

## 使用 CLI 進行開發
{: #openwhisk_start_configure_cli}

若要進一步瞭解如何使用 {{site.data.keyword.openwhisk_short}} CLI 來安裝及開發，請參閱[設定 {{site.data.keyword.openwhisk_short}} CLI ](https://{DomainName}/functions/cli){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。

## 將 API 及資料集公開為 Web 動作
{: #expose-actions}

依預設，{{site.data.keyword.openwhisk_short}} 會定義需要鑑別金鑰的動作。在正式作業的行動環境中，經常必須根據 OAuth 流程授權行動用戶端，以公開 API 及特定資料集。

{{site.data.keyword.openwhisk_short}} 讓開發人員能將它們的函數公開為 Web 動作（會加上註釋）以快速建置 Web 應用程式。您可以用已加上註釋的動作來進行後端邏輯程式設計，您的 Web 應用程式可以匿名地存取這些動作，而不需要 {{site.data.keyword.openwhisk_short}} 鑑別金鑰。

若要將動作公開為 Web 動作，請移至動作的**端點**標籤，然後選取**啟用為 Web 動作**。

現在，使用者可以從瀏覽器或 cURL 要求呼叫到動作，例如：
```
curl https://openwhisk.cloud.ibm.com/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

輸出：
```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} 為 iOS 及 watchOS 裝置提供[行動 SDK](/docs/openwhisk?topic=cloud-functions-pkg_mobile_sdk)，讓行動應用程式能輕鬆地傳送遠端觸發程式及呼叫遠端動作。

## 使用入門範本套件建立無伺服器應用程式
{: #serverless-starter}

您可以使用入門範本套件來建立無伺服器應用程式，如 Python 範例無伺服器應用程式。若要找到入門範本套件，請完成以下步驟：

1. 移至 {{site.data.keyword.dev_console}} 主控台中的[應用程式服務入門範本套件](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 頁面。
2. 在搜尋列中鍵入 `serverless` 以過濾入門範本套件的清單。
3. 選取一個無伺服器入門範本套件，如 Python 範例無伺服器應用程式。
4. 命名應用程式，並選取資源群組。
5. 選用。提供標記以分類應用程式。如需相關資訊，請參閱[使用標籤](/docs/resources?topic=resources-tag)。
6. 建立新的或選取現有的 Cloudant 服務實例。
7. 選用。若要在新增更多服務或部署應用程式之前檢查程式碼，請按一下**檢視原始檔**。請檢查 `README.md` 檔案，以找出您是否需要採取更多動作，以讓應用程式啟動並執行。
  
8. 按一下**建立**。

很棒的開始！您剛剛已建立應用程式！

## 新增服務（選用）
{: #serverless-services}

如果入門範本套件需要特定的服務，則提供自動佈建的服務，以在建立應用程式時自動建立這些服務的實例。

1. 在「應用程式詳細資料」頁面上，按一下**建立服務**或**連接現有的服務**（視是否已有要連接至此應用程式的服務而定）。
2. 選取您要的服務類型，並遵循將現有服務新增至應用程式或建立服務實例的提示。

新增所需的所有服務後，這些服務將顯示在「應用程式詳細資料」頁面中。

## 部署應用程式
{: #serverless-deploy}

若要部署應用程式，請完成以下步驟：

1. 在「應用程式詳細資料」頁面上，按一下**部署**。
2. 選取**部署到 Cloud Functions**，然後按一下**下一步**。
3. 在「配置工具鏈」頁面上，輸入工具鏈名稱，選取地區，然後按一下**建立**。在您選取及配置部署目標之後，「應用程式詳細資料」頁面會指出已配置持續交付。
4. 選用。在 {{site.data.keyword.openwhisk_short}} 主控台中，按一下「動作」圖示 ![「其他動作」圖示](../icons/action-menu-icon.svg) 並選取**開啟 Cloud Functions** 來檢閱動作。
5. 選用。按一下**檢視儲存庫**，以檢視包含應用程式及服務之產生程式碼的儲存庫。

## 驗證應用程式是否已部署
{: #serverless-verify}

使用適當配置的工具鏈，建置-部署的循環會自動開始，並且全都合併到您儲存庫的主要分支。如需相關資訊，請參閱[建置並部署](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)。

若要驗證應用程式是否已順利部署，請完成以下步驟：

1. 在「應用程式詳細資料」頁面上按一下**檢視工具鏈**。
2. 按一下 **Delivery Pipeline**，您可以在其中啟動建置、管理部署，以及檢視日誌和歷程。
3. 如果部署成功，每個管線階段會指示**階段通過**。
4. 若要檢視動作和 API 資訊，請按一下**部署階段**磚中的**檢視日誌和歷程**。
