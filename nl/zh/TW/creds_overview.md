---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, credentials

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# 認證概觀
{: #credentials_overview}

了解如何手動將服務認證新增至部署環境。
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

一般而言，您想要應用程式邏輯從執行應用程式的環境中，獲得機密服務認證，例如資料庫 API 金鑰或密碼。如此一來，您就不會將認證保存在原始碼儲存庫中。Continuous Integration、正式作業前及正式作業環境中的資料庫會彼此隔離。

如果您使用入門範本套件範本來建立應用程式，則會自動為您準備環境。不論您的部署目標是：
  * [Kubernetes](/docs/apps?topic=creating-apps-add-credentials-kube)
  * [Cloud Foundry Public 或 Cloud Foundry Enterprise Environment](/docs/apps?topic=creating-apps-add-credentials-cf)
  * [虛擬伺服器實例（亦即本端 Docker）](/docs/apps?topic=creating-apps-add-credentials-vsi)
  
這些步驟是針對如何配置環境而提供。入門範本套件會產生程式碼來使用相依程式庫，讓程式碼成為可攜式，以在任何部署目標上執行。最後，不會使用任何分支邏輯來偵測執行應用程式的部署目標。

然後，管理者或 DevOps 工程師負責以適當的存取控制和配置來準備環境，讓應用程式所需的值可供其使用。

「配置持續交付」是一次性的步驟，可執行下列主要作業：
 * 以服務、資源及認證來準備部署目標。
 * 藉由使用正確參照環境中之認證的程式碼，建立 DevOps 工具鏈，以建置應用程式並將其部署至該環境。

不過，您必須在下列任何情境中準備部署目標：
 * 自帶程式碼。
 * 從空白的入門範本套件範本開始。
 * 將服務新增至已部署且以入門範本套件為基礎的應用程式。

環境準備一律會針對與應用程式相關聯之所有服務的所有認證來執行，而且 `manifest.yml` 中會列出所有 `services`，但並非所有認證參照都會放入 `mappings.json` 檔案中。在這些情況下，您需要自己放置這類參照。決定部署目標之後，而且不需要 `IBMCloudEnv` 程式庫抽象化的話，請參閱適用於您決策的「您的程式碼 +（部署目標）」一節。
{: important}

部分入門範本套件完全不包括 `IBMCloudEnv` 相依關係、`manifest.yml` 或 `mappings.json` 檔案的參照。
{: important}
