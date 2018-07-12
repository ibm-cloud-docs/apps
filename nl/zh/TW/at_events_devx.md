---

copyright:
  years: 2016, 2018
lastupdated: "2018-06-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:table: .aria-labeledby="caption"}

# {{site.data.keyword.dev_console}} {{site.data.keyword.cloudaccesstrailshort}}events
{: #at_events}

身為安全性管理者、審核員或管理員的您，可以使用 {{site.data.keyword.cloudaccesstrailfull}} 服務追蹤使用者和應用程式在 {{site.data.keyword.Bluemix_notm}} 中與 {{site.data.keyword.dev_console}} 互動的情況。
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull_notm}} 服務會記錄由使用者起始，且會變更 {{site.data.keyword.Bluemix_notm}} 中服務狀態的活動。如需相關資訊，請參閱[關於 {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov )。

## 在哪裡檢視事件
{: #ui}

{{site.data.keyword.cloudaccesstrailshort}} 事件提供於 {{site.data.keyword.cloudaccesstrailshort}} 帳戶網域，這提供於產生 {{site.data.keyword.dev_console}} 事件的 {{site.data.keyword.Bluemix_notm}} 地區。

若要開始監視您使用者的動作，請參閱[入門指導教學](/docs/services/cloud-activity-tracker/index.html)。

## 事件清單
{: #events}

下表列出會產生事件的動作：

<table>
  <caption>產生事件的動作</caption>
  <tr>
    <th>動作</th>
	  <th>說明</th>
  <tr>
  <tr>
    <td>bluemix-developer-experience.app.create</td>
	  <td>當使用者建立應用程式時會產生事件。</td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.read</td>
	  <td>當下列任何狀況發生時會產生事件：</br><ul><li>使用者下載應用程式碼。</li> <li>使用者利用 {{site.data.keyword.dev_console}} CLI 下載認證檔。</li> <li>開發人員經驗基礎架構針對與應用程式相關聯的資源讀取認證。</li> <li>使用者檢視應用程式清單，例如，當使用者在 {{site.data.keyword.dev_console}} 主控台中或透過 {{site.data.keyword.dev_cli_short}} CLI 檢視應用程式清單時。</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.update</td>
	  <td>當下列任何狀況發生時會產生事件：</br><ul><li>應用程式的某個東西改變，例如，當使用者修改應用程式名稱時。</li><li>新資源佈建並新增至應用程式。</li><li>現有資源新增至應用程式。</li><li>從應用程式移除服務。</li><li>為應用程式產生程式碼。</li><li>透過開發人員經驗新增 DevOps 工具鏈，例如藉由選取 *Deploy to Cloud*。</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.delete</td>
	  <td>當使用者刪除應用程式時會產生事件。</td>
  </tr>
</table>
