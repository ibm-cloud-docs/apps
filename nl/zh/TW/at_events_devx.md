---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-04"

keywords: apps, applications, activity tracking events

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:deprecated: .deprecated}
{:table: .aria-labeledby="caption"}

# {{site.data.keyword.dev_console}} {{site.data.keyword.cloudaccesstrailshort}}events
{: #at_events}

身為安全性管理者、審核員或管理員的您，可以使用 {{site.data.keyword.cloudaccesstrailfull}} 服務追蹤使用者和應用程式在 {{site.data.keyword.cloud}} 中與 {{site.data.keyword.dev_console}} 互動的情況。
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} 已淘汰。從 2019 年 5 月 9 日開始，您無法佈建新的 {{site.data.keyword.cloudaccesstrailshort}} 實例，而且將移除對*精簡* 方案實例的存取。現有的超值方案實例將支援到 2019 年 9 月 30 日為止。若要繼續監視 {{site.data.keyword.cloud_notm}} 帳戶的活動，請佈建 [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) 的實例。
{: deprecated}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服務會記錄由使用者啟動，且會變更 {{site.data.keyword.cloud_notm}} 中服務狀態的活動。如需相關資訊，請參閱[關於 {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov)。

## 在哪裡檢視事件
{: #view-events-ui}

{{site.data.keyword.cloudaccesstrailshort}} 事件提供於 {{site.data.keyword.cloudaccesstrailshort}} 帳戶網域，這提供於產生 {{site.data.keyword.dev_console}} 事件的 {{site.data.keyword.cloud_notm}} 地區。

若要開始監視您使用者的動作，請參閱[入門指導教學](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started)。

## 事件清單
{: #events}

下表列出會產生事件的動作：

|動作|說明	|
|-----|-------------|
|bluemix-developer-experience.app.create|當使用者建立應用程式時會產生事件。|
|bluemix-developer-experience.app.read|當下列任何狀況發生時會產生事件：<br><br>使用者下載應用程式碼。<br><br>使用者利用 {{site.data.keyword.dev_console}} CLI 下載認證檔。<br><br>{{site.data.keyword.cloud_notm}} 基礎架構針對與應用程式相關聯的服務讀取認證。<br><br>使用者檢視應用程式的清單。例如，使用者在 {{site.data.keyword.dev_console}} 主控台中或透過 {{site.data.keyword.dev_cli_short}} CLI 檢視應用程式清單。|
|bluemix-developer-experience.app.update|當下列任何狀況發生時會產生事件：<br><br>應用程式的某個東西改變。例如，使用者修改應用程式名稱。<br><br>新的服務已建立並新增至應用程式。<br><br>現有服務新增至應用程式。<br><br>從應用程式移除服務。<br><br>為應用程式產生程式碼。<br><br>DevOps 工具鏈是透過 {{site.data.keyword.cloud_notm}} 主控台新增。例如，使用者從「應用程式詳細資料」頁面選取**配置持續交付**。|
|bluemix-developer-experience.app.delete|當使用者刪除應用程式時會產生事件。|
{: caption="表 1. 產生事件的動作" caption-side="top"}
