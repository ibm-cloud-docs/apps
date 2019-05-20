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

# 將服務認證手動新增至部署環境
{: #credentials_overview}

您想要應用程式邏輯從執行應用程式的環境中，獲得機密服務認證，例如資料庫 API 金鑰或密碼。如此一來，您就不需要將認證保存在原始碼儲存庫中。
{: shortdesc}

如果您使用入門範本套件來建立應用程式，則會自動為您準備環境。當您在部署應用程式之前將服務連接至入門範本套件時，會自動將服務認證新增至環境。
{: tip}

在下列一項情境中，您必須手動將服務認證新增至部署環境：

 * 自帶程式碼。
 * 在部署應用程式之後，將服務新增至入門範本套件型應用程式。

服務認證新增處理程序取決於部署目標及程式設計語言。如需配置部署目標服務認證的相關資訊，請參閱管理環境特有的文件：

  * [{{site.data.keyword.containershort}}](/docs/containers?topic=containers-service-binding#adding_app)
  * Cloud Foundry Public 或 {{site.data.keyword.cfee_full}}
  * 虛擬伺服器實例（本端 Docker 容器）

許多語言及架構都提供應用程式特定及環境特定配置的標準程式庫。如需相關資訊，請參閱下列程式設計手冊：

* [Java：使用服務認證](/docs/java?topic=cloud-native-configuration)
* [配置 Node.js 環境](/docs/node?topic=nodejs-configure-nodejs)
* [配置 Spring 環境](/docs/java?topic=java-spring-configuration)
* [配置 Swift 環境](/docs/swift?topic=swift-configuration)
* [配置 Go 環境](/docs/go?topic=go-configure-go-env)
