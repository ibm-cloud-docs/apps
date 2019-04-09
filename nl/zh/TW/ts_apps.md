---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-01"

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# 建立應用程式的疑難排解
{: #managingapps}

建立應用程式的一般問題，可能包括無法更新應用程式，或是未顯示雙位元組字元。在許多情況下，您可以遵照一些簡單的步驟，從這些問題回復。
{:shortdesc}

## 您有未儲存的變更
{: #ts_unsaved_changes}
{: troubleshoot}

當您按一下應用程式詳細資料頁面上的項目時，可能無法採取任何動作。您也可能會收到要先儲存變更才能繼續的提示。

在應用程式詳細資料頁面上嘗試檢查應用程式或服務時，會顯示下列錯誤訊息：
{: tsSymptoms}

`您有未儲存的變更。您確定要離開此頁面嗎？`

在運行環境窗格的**實例**或**記憶體配額**欄位上捲動滑鼠時，值就會變更。此行為是按照設計而來。不過，您會收到提示，提醒您在移至另一個頁面之前，要先儲存記憶體或實例設定。
{: tsCauses}

關閉訊息對話框，然後按一下運行環境窗格中的**重設**。
{: tsResolve}

## {{site.data.keyword.cloud_notm}} 地區之間的自動失效接手無法使用
{: #ts_failover}
{: troubleshoot}

您無法在 {{site.data.keyword.cloud}} 地區之間使用自動失效接手。不過，您可以使用支援在許多 IP 位址之間進行失效接手的 DNS 提供者，作為暫行解決方法。

當 {{site.data.keyword.cloud_notm}} 地區變成無法使用時，在該地區中執行的應用程式也會無法使用，即使相同應用程式正在另一個 {{site.data.keyword.cloud_notm}} 地區中執行亦然。
{: tsSymptoms}

{{site.data.keyword.cloud_notm}} 尚未提供從一個地區到另一個地區的自動失效接手。
{: tsCauses}

您可以使用支援在許多 IP 位址之間進行智慧型失效接手的 DNS 提供者，並且手動配置 DNS 設定，以啟用 {{site.data.keyword.cloud_notm}} 地區之間的自動失效接手。具有此特性的 DNS 提供者包括 NSONE、Akamai 和 Dyn。
{: tsResolve}

當您配置 DNS 設定時，必須指定應用程式執行所在之 {{site.data.keyword.cloud_notm}} 地區的公用 IP 位址。若要取得 {{site.data.keyword.cloud_notm}} 地區的公用 IP 位址，請使用 `nslookup` 指令。例如，您可以在指令行視窗鍵入下列指令。
```
nslookup cloud.ibm.com
```
{: codeblock}


## 無法重複使用已刪除應用程式的名稱
{: #ts_reuse_appname}
{: troubleshoot}

在您刪除應用程式之後，只有在刪除應用程式路徑之後才能重複使用應用程式名稱。

當您嘗試重複使用應用程式名稱時，會收到下列訊息：
{: tsSymptoms}

`The name is already used by another app.`

刪除應用程式時，不會自動刪除其路徑（即應用程式的 URL），也無法重複使用。您必須移至建立應用程式的空間來刪除路徑，才能重複使用。
{: tsCauses}

請完成下列步驟，以刪除未用的路徑：
{: tsResolve}

  1. 輸入下列指令，檢查路徑是否屬於現行空間：
     ```
    ibmcloud cf routes
    ```
    {: codeblock}

  2. 如果路徑不屬於現行空間，請輸入下列指令來切換至其所屬空間或組織：
     ```
    ibmcloud cf target -o org_name -s space_name
    ```
    {: codeblock}

  3. 輸入下列指令，來刪除應用程式路徑：
     ```
    ibmcloud cf delete-route domain_name -n host_name
    ```
    {: codeblock}

  例如：
  ```
  ibmcloud cf delete-route cf.cloud.ibm.com -n app001
  ```
  {: codeblock}

## 無法擷取組織中的空間
{: #ts_retrieve_space}
{: troubleshoot}

如果現行組織沒有與其相關聯的空間，則無法建立應用程式或服務。

嘗試在 {{site.data.keyword.cloud_notm}} 中建立應用程式時，您看到下列錯誤訊息：
{: tsSymptoms}

`BXNUI0515E: The spaces in the org weren't retrieved. Either a network connection problem occurred, or your current organization does not have a space associated with it.`

通常在您第一次嘗試從型錄建立應用程式或服務，但尚未建立空間時，會發生此錯誤。
{: tsCauses}

確定已在現行組織中建立空間。若要建立空間，請使用下列其中一種方法：
{: tsResolve}

* 從功能表列按一下**管理 > 帳戶**，然後選取 **Cloud Foundry 組織**。選取要在其中建立空間的組織，然後按一下**建立空間**。
* 在 Cloud Foundry 指令行介面中，鍵入 `cf create-space <space_name> -o <organization_name>`。

請重試。如果此訊息再次出現，請前往 [{{site.data.keyword.cloud_notm}} 狀態 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://ibm.biz/bluemixstatus){: new_window} 頁面，以檢查服務或元件是否有問題。

## 無法執行所要求的動作
{: #ts_authority}
{: troubleshoot}

您沒有適當的存取權，無法完成動作。

當您嘗試執行服務實例或應用程式實例的動作時，無法完成所要求的動作，並且看到下列其中一個錯誤訊息：
{: tsSymptoms}

`BXNUI0514E: You are not a developer for any of the spaces in the <orgName> organization.`

`Server error, status code: 403, error code: 10003, message: You are not authorized to perform the requested action.`

您沒有執行動作的適當權限層級。
{: tsCauses}

若要取得適當的權限層級，請使用下列其中一種方法。
{: tsResolve}

* 選取另一個您具有開發人員角色的組織及空間。
* 要求組織管理者將您的角色變更為開發人員，或建立空間，然後將開發人員角色指派給您。如需詳細資料，請參閱[管理組織和空間](/docs/admin/orgs_spaces.html#orgsspacesusers)。

## 因為授權錯誤，所以無法存取 {{site.data.keyword.cloud_notm}} 服務
{: #ts_vcap}
{: troubleshoot}

如果服務認證寫在您的應用程式中，則您的應用程式存取 {{site.data.keyword.cloud_notm}} 服務時可能會發生授權錯誤。

配置應用程式與 {{site.data.keyword.cloud_notm}} 服務通訊之後，即將應用程式部署至 {{site.data.keyword.cloud_notm}}。不過，您無法使用應用程式來存取 {{site.data.keyword.cloud_notm}} 服務，而且會收到授權錯誤。
{: tsSymptoms}

寫在應用程式中的認證可能不正確。每次重建服務時，用來存取它的認證都會變更。
{: tsCauses}

請使用 VCAP_SERVICES 環境變數中的連線參數，而不是將認證寫在應用程式中。使用 VCAP_SERVICES 環境變數中連線參數的方法，會視程式語言而改變。例如，針對 Node.js 應用程式，您可以使用下列指令：
{: tsResolve}

```
process.env.VCAP_SERVICES
```

如需可在其他程式語言中使用之指令的相關資訊，請參閱 [Java ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} 和 [Ruby ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window}。




## 收到 502 錯誤的閘道錯誤
{: #ts_502_error}
{: troubleshoot}

如果您在 {{site.data.keyword.cloud_notm}} 上與應用程式互動時，收到 `502 Bad Gateway` 錯誤，請檢查 {{site.data.keyword.cloud_notm}} 狀態頁面，然後採取適當的動作。

您收到開頭為 502 Bad Gateway 的錯誤訊息。例如，您可能會看到 `502 Bad Gateway: Registered endpoint failed to handle the request`。
{: tsSymptoms}

「錯誤的閘道」錯誤通常發生在您前往網站使用 Proxy 伺服器來儲存及轉遞來自管理網站之主要伺服器的資料時。主要伺服器及 Proxy 伺服器可能未適當連接。那麼，您會在瀏覽器視窗中看到 HTTP 狀態碼 502。此狀態碼表示網站的主要伺服器未收到它預期來自 Proxy 伺服器的 HTTP 實作。
{: tsCauses}

其他較少見的「錯誤的閘道」錯誤原因，包括網際網路服務供應商 (ISP) 脫離、不正確的防火牆配置及瀏覽器快取錯誤。

如果您懷疑 {{site.data.keyword.cloud_notm}} 服務已關閉，請先檢查 [{{site.data.keyword.cloud_notm}} 狀態 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://ibm.biz/bluemixstatus){: new_window} 頁面。[在另一個 {{site.data.keyword.cloud_notm}} 地區中使用服務](/docs/resources/connect_external_app#externalapp){: new_window}也許可以作為暫行解決方法。如果服務狀態正常，請嘗試下列步驟來解決問題：
{: tsResolve}

  * 重試動作：
    * 按鍵盤上的 F5，或按一下**重新整理**，來重新載入頁面。如果此步驟無效，請清除瀏覽器的快取及 Cookie，然後再重新載入。
    
    * 使用不同的瀏覽器。
    * 重新啟動路由器、數據機及電腦。將這些裝置重新開機可清除導致錯誤 502 的許多種錯誤。
  * 等待並於稍後再試一次。暫時發生的問題可能是由於網際網路服務供應商或 {{site.data.keyword.cloud_notm}} 服務所造成。您可能要等待暫時問題獲得解決。
  * 如果問題仍然存在，請與 {{site.data.keyword.cloud_notm}} 支援中心聯絡。如需相關資訊，請參閱[聯絡 {{site.data.keyword.cloud_notm}} 支援中心 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](/docs/support/index.html#contacting-bluemix-support){: new_window}。

## 已超出磁碟配額
{: #ts_disk_quota}
{: troubleshoot}

如果您已耗盡磁碟空間，可以手動修改磁碟配額以取得更多磁碟空間。

當您耗盡磁碟空間時，可能會看到一則指出已超出磁碟配額的訊息。為解決此問題，您可能已嘗試擴充應用程式實例以取得更多磁碟空間。例如，您可能透過變更應用程式詳細資料頁面上的記憶體配額，從 256 MB 擴充為 1256 MB。不過，因為磁碟配額保持不變，所以您並未取得更多磁碟空間。
{: tsSymptoms}

配置給應用程式的預設磁碟配額是 1 GB。如果您需要更多磁碟空間，則必須手動指定磁碟配額。
{: tsCauses}

請使用下列其中一種方法來指定您的磁碟配額。您可以指定的磁碟配額上限是 2 GB。如果 2 GB 仍然不夠，請嘗試使用外部服務，例如 [Object Storage](/docs/services/ObjectStorage/index.html)。
{: tsResolve}

  * 在 manifest.yml 檔案中，新增下列項目：
    
  ```yaml
	disk_quota: <disk_quota>
	```
  * 當您將應用程式推送至  {{site.data.keyword.cloud_notm}} 時，請使用 `ibmcloud cf push` 指令並搭配 **-k** 選項：

  ```
	ibmcloud cf push appname -p app_path -k <disk_quota>
	```
  {: codeblock}

## Android 應用程式無法收到 {{site.data.keyword.mobilepushshort}}
{: #ts_push}
{: troubleshoot}

在無法存取 Google 的特定地區中，Android 應用程式收不到您透過 IBM {{site.data.keyword.mobilepushshort}} 服務送出的通知。在此情況下，暫行解決方法是使用協力廠商服務。

為您的 {{site.data.keyword.cloud_notm}} 應用程式連結一個 {{site.data.keyword.mobilepushshort}} 服務，並將訊息傳送至已登錄的裝置。不過，在特定地區，Android 上開發的應用程式收不到您的通知。
{: tsSymptoms}

IBM {{site.data.keyword.mobilepushshort}} 服務使用「Google 雲端通訊 (GCM)」服務，將通知分派至 Android 上開發的行動應用程式。若要讓 Android 應用程式收到通知，行動應用程式必須可存取「Google 雲端通訊 (GCM)」服務。在 Android 應用程式無法呼叫到 GCM 服務的地區，Android 應用程式即收不到 {{site.data.keyword.mobilepushshort}}。
{: tsCauses}

暫行解決方法是使用不依賴 GCM 服務的協力廠商服務，例如 [Pushy ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://pushy.me){: new_window}、[getui ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://www.getui.com/){: new_window} 及 [jpush ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.jpush.cn/){: new_window}。
{: tsResolve}

## 已超出組織的服務限制
{: #ts_servicelimit}
{: troubleshoot}

如果您是精簡帳戶使用者，則在超出組織的服務限制時，可能無法在 {{site.data.keyword.cloud_notm}} 中建立應用程式。

嘗試在 {{site.data.keyword.cloud_notm}} 中建立應用程式時，會顯示下列錯誤訊息：
{: tsSymptoms}

`BXNUI2032E: 未建立 <service_instances> 資源。聯絡 Cloud Foundry 以建立資源時發生錯誤。Cloud Foundry 訊息："You have exceeded your organization's services limit."`

當您超出帳戶可用的服務實例數目限制時，就會發生此錯誤。
{: tsCauses}

請刪除任何不需要的服務實例，或移除您可以擁有的服務實例數目限制。
{: tsResolve}

  * 若要刪除服務實例，您可以使用 {{site.data.keyword.cloud_notm}} 主控台或指令行介面。

    若要使用 {{site.data.keyword.cloud_notm}} 主控台來刪除服務實例，請完成下列步驟：
	  1. 在資源清單中，按一下您要刪除之服務的**動作**功能表。
	  2. 按一下**刪除服務**。系統會提示您重新編譯打包服務實例所連結的應用程式。

    若要使用指令行介面來刪除服務實例，請完成下列步驟：
	  3. 將服務實例與應用程式取消連結。輸入 `cf unbind-service <appname> <service_instance_name>`。
	  4. 刪除服務實例。輸入 `cf delete-service <service_instance_name>`。
	  5. 刪除服務實例之後，您可能要重新編譯打包服務實例所連結的應用程式。輸入 `cf restage <appname>`。

  * 若要移除您可以擁有的服務實例數目的限制，請將您的「精簡」帳戶升級為計費帳戶。如需相關資訊，請參閱[升級帳戶](/docs/account/index.html#upgrade-to-paygo)。

## 執行檔無法在 {{site.data.keyword.cloud_notm}} 上執行
{: #ts_executable}
{: troubleshoot}

在不同環境中開發及建置的執行檔，可能無法在 {{site.data.keyword.cloud_notm}} 上執行。

在不同環境中開發及建置的執行檔，無法在 {{site.data.keyword.cloud_notm}} 上執行。
{: tsSymptoms}

如果您想要推送至 {{site.data.keyword.cloud_notm}} 的內容已經是執行檔，表示該內容先前就已建置好，不需要以 {{site.data.keyword.cloud_notm}} 為建置基礎。在此情況下，執行檔不需要任何建置套件，就可以在 {{site.data.keyword.cloud_notm}} 上執行。您必須明確地向 {{site.data.keyword.cloud_notm}} 指出不需要任何建置套件。
{: tsCauses}

當您將執行檔推送至 {{site.data.keyword.cloud_notm}} 時，必須指定 `null-buildpack`，表示不需要任何建置套件。請使用 **-b** 選項搭配 `ibmcloud cf push` 指令來指定 `null-buildpack`：
{: tsResolve}

```
ibmcloud cf push appname -p app_path -c <start_command> -b <null-buildpack>
```
{: codeblock}

例如：
```
ibmcloud cf push appname -p app_path -c ./RunMeNow -b https://github.com/ryandotsmith/null-buildpack
```
{: codeblock}

## 已超出組織的記憶體限制
{: #ts_outofmemory}
{: troubleshoot}

如果您是精簡帳戶使用者，則超出組織的記憶體限制時，您可能無法將應用程式部署至 {{site.data.keyword.cloud_notm}}。您可以減少應用程式所使用的記憶體，或增加帳戶的記憶體配額。「精簡」帳戶的記憶體配額上限為 256 MB，而且只能透過升級為計費帳戶來增加。

當您將應用程式部署至 {{site.data.keyword.cloud_notm}} 時，會顯示下列錯誤訊息：
{: tsSymptoms}

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.`

當組織剩餘的記憶體量少於您想要部署之應用程式所需的記憶體量時，就會發生這個錯誤。「精簡」帳戶的記憶體配額上限為 256 MB。
{: tsCauses}

您可以增加帳戶的記憶體配額，或減少應用程式所使用的記憶體。
{: tsResolve}

  * 若要增加帳戶的記憶體配額，請將「精簡」帳戶升級為計費帳戶。如需相關資訊，請參閱[升級帳戶](/docs/account/index.html#upgrade-to-paygo)。
  * 若要減少應用程式所使用的記憶體，請使用 {{site.data.keyword.cloud_notm}} 主控台或 Cloud Foundry 指令行介面。

    如果您使用 {{site.data.keyword.cloud_notm}} 主控台，請完成下列步驟：

    1. 從資源清單選取應用程式。即會開啟應用程式詳細資料頁面。
    2. 在「運行環境」窗格中，您可以針對您的應用程式減少記憶體上限及（或）應用程式實例的數目。

    如果您使用指令行介面，請完成下列步驟：

    1. 檢查有多少記憶體用於應用程式：
  	  ```
	    ibmcloud cf list
	    ```
      {: codeblock}

	    `ibmcloud cf list` 指令會列出您在現行空間中部署的所有應用程式。也會顯示每一個應用程式的狀態。

    2. 若要減少應用程式所使用的記憶體量，請減少應用程式實例的數目及（或）記憶體上限：
	    ```
	    ibmcloud cf push appname -p app_path -i instance_number -m memory_limit
     ```
      {: codeblock}

    3. 重新啟動應用程式，讓變更生效。

## 應用程式不會自動重新啟動
{: #ts_apps_not_auto_restarted}
{: troubleshoot}

當連結至應用程式的服務停止運作時，不會自動重新啟動應用程式。

當連結至應用程式的服務當機時，應用程式可能會發生運作中斷、異常狀況和連線失敗之類的問題。{{site.data.keyword.cloud_notm}} 不會自動重新啟動應用程式，以從這些問題回復。
{: tsSymptoms}

此行為是 Cloud Foundry 的設計。
{: tsCauses}

您可以在指令行介面中鍵入下列指令，以手動重新啟動應用程式：
{: tsResolve}

```
ibmcloud cf push appname -p app_path
```
{: codeblock}

此外，您可以將應用程式編碼成可識別運作中斷、異常狀況和連線失敗之類的問題，並從其中回復。

<!-- begin STAGING ONLY -->

## {{site.data.keyword.cloud_notm}} Live Sync 除錯不會從指令行啟動
{: #ts_no_debug}
{: troubleshoot}

您已使用指令行來啟用應用程式的「{{site.data.keyword.cloud_notm}} Live Sync 除錯」特性，但無法存取「除錯」介面。

您已藉由設定 **BLUEMIX_APP_MGMT_ENABLE** 環境變數，來為應用程式啟用「除錯」特性。不過，您無法存取位於 `app_url/bluemix-debug/manage` 的「除錯」使用者介面。
{: tsSymptoms}

在以下情況無法啟用「除錯」特性：
{: tsCauses}

  * 當 `manifest.yml` 包含指令屬性時
  * 當您使用 **-c** 選項，將應用程式推送至 {{site.data.keyword.cloud_notm}} 時

請使用下列其中一個選項來解決問題：
{: tsResolve}

  * 建議的作法是使用 IBM Node.js 建置套件來啟動應用程式。如需相關資訊，請參閱[將 Node.js 應用程式部署至 {{site.data.keyword.cloud_notm}}](/docs/runtimes/nodejs/index.html#nodejs_runtime) 主題的「啟動指令」一節。
  * 將 `manifest.yml` 中的指令屬性修訂為 command: null，或編輯您的推送指令以包含 `-c null`，來停用現有應用程式的指令。
  * 從 `manifest.yml` 移除 **command** 屬性。然後，從 {{site.data.keyword.cloud_notm}} 中刪除現行應用程式，然後重新推送應用程式。

<!-- end STAGING ONLY -->

## 在 {{site.data.keyword.cloud_notm}} 上找不到組織
{: #ts_orgs}
{: troubleshoot}

在使用 {{site.data.keyword.cloud_notm}} 地區時，可能找不到 {{site.data.keyword.cloud_notm}} 上的組織。

您可以順利登入 {{site.data.keyword.cloud_notm}} 主控台，但無法使用 Cloud Foundry 指令行介面來推送應用程式。
{: tsSymptoms}

嘗試使用 Cloud Foundry 指令行介面將應用程式推送至 {{site.data.keyword.cloud_notm}} 時，您看到下列其中一則錯誤訊息，且訊息中指定了組織名稱：

`尋找組織時發生錯誤`

`找不到組織`

這個問題會發生是因為未指定您要使用之地區的 API 端點，而您要尋找的組織可能是在不同的地區。
{: tsCauses}

如果您使用 Cloud Foundry 指令行介面將應用程式推送至 {{site.data.keyword.cloud_notm}}，請輸入 `cf api` 指令，並指定地區的 API 端點。例如，輸入下列指令以連接 {{site.data.keyword.cloud_notm}} 歐洲英國地區：
{: tsResolve}

```
cf api https://api.eu-gb.cf.cloud.ibm.com
```
{: codeblock}


## 無法建立應用程式路徑
{: #ts_hostistaken}
{: troubleshoot}

將應用程式部署至 {{site.data.keyword.cloud_notm}} 時，如果指定的主機名稱已被使用，則無法建立應用程式路徑。

將應用程式部署至 {{site.data.keyword.cloud_notm}} 時，您看到下列錯誤訊息：
{: tsSymptoms}

`Creating route hostname.domainname ... FAILED Server error, status code: 400, error code: 210003, message: The host is taken: hostname`

如果已使用指定的主機名稱，則會發生此問題。
{: tsCauses}

在您使用的網域內，您指定的主機名稱必須是唯一的。若要指定不同的主機名稱，請使用下列其中一種方法：
{: tsResolve}

  * 如果您使用 `manifest.yml` 檔案來部署應用程式，請在 host 選項中指定主機名稱。
    ```yaml
    host: host_name
	  ```

  * 如果您從命令提示字元部署應用程式，請使用 `ibmcloud cf push` 指令與 **-n** 選項。
    ```
    ibmcloud cf push appname -p app_path -n host_name
    ```
    {: codeblock}

## 無法使用 ibmcloud cf push 指令推送 WAR 應用程式
{: #ts_cf_war}
{: troubleshoot}

如果未正確指定應用程式位置，則可能無法使用 `ibmcloud cf push` 指令，將保存的 Web 應用程式部署至 {{site.data.keyword.cloud_notm}}。

使用 `ibmcloud cf push` 指令將 WAR 應用程式上傳至 {{site.data.keyword.cloud_notm}} 時，您看到下列錯誤訊息：
{: tsSymptoms}
`Staging error: cannot get instances since staging failed.`

如果未指定 WAR 檔，或未指定 WAR 檔的路徑，就可能會發生此問題。
{: tsCauses}

請使用 **-p** 選項來指定 WAR 檔，或新增 WAR 檔的路徑。例如：
{: tsResolve}

```
ibmcloud cf push MyUniqueAppName01 -p app.war
```
{: codeblock}

```
ibmcloud cf push MyUniqueAppName02 -p "./app.war"
```
{: codeblock}

如需 `ibmcloud cf push` 指令的相關資訊，請輸入 `ibmcloud cf push -h`。

## 將應用程式推送至 {{site.data.keyword.cloud_notm}} 後，未能適當地顯示雙位元組字元
{: #ts_doublebytes}
{: troubleshoot}

如果未適當配置 Servlet 或 JSP 檔的 Unicode 支援，則可能無法適當顯示雙位元組字元。

將應用程式推送至 {{site.data.keyword.cloud_notm}} 時，無法適當顯示應用程式內所指定的雙位元組字元。
{: tsSymptoms}

如果未適當配置 Servlet 或 JSP 檔的 Unicode 支援，就可能會發生此問題。
{: tsCauses}

您可以在 Servlet 或 JSP 檔中使用下列程式碼：
{: tsResolve}

  * 在 Servlet 原始檔中
  ```java
	response.setContentType("text/html; charset=UTF-8");
	```
  {: codeblock}

  * 在 JSP 中
  ```jsp
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```
  {: codeblock}

## 無法部署 Node.js 應用程式
{: #ts_nodejs_deploy}
{: troubleshoot}

當您更新 Node.js 應用程式或是將 Node.js 應用程式部署至 {{site.data.keyword.cloud_notm}} 時，可能會遇到問題。

當您更新 Node.js 應用程式或是將 Node.js 應用程式部署至 {{site.data.keyword.cloud_notm}} 時，可能會看到下列其中一則錯誤訊息：
{: tsSymptoms}

`應用程式未順利由任何可用的建置套件偵測到。`

`實例（索引 0）無法開始接受連線。`

`無法取得實例，因為編譯打包失敗。`

可能的原因如下：
{: tsCauses}

  * 未指定啟動指令。
  * 應用程式遺漏部署 Node.js 應用程式所需的檔案，或是放在非根目錄的資料夾中。

請根據問題的原因，使用下列其中一種方法：
{: tsResolve}

  * 以下列其中一種方法指定啟動指令：
     * 使用 Cloud Foundry 指令行介面。例如：
    ```
		  ibmcloud cf push MyUniqueNodejs01 -p app_path -c "node app.js"
		```
      {: codeblock}

    * 使用 [package.json ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://www.npmjs.com/package/jsonfile){: new_window} 檔案。例如：
	    ```json
		  {
        ...
  	    "scripts": {
	 		  "start": "node app.js"
 	    }
	    }
	    ```

    * 使用 `manifest.yml` 檔案。例如：
	    ```
		  applications:
      name: MyUniqueNodejs01
      ...
      command: node app.js
      ...
      ```

  * 確定 `package.json` 檔案存在於您的 Node.js 應用程式中，Node.js 建置套件才能辨識應用程式。請確定此檔案位在應用程式的根目錄中。下列範例顯示簡單的 `package.json` 檔案：
	```json
	{
        "name": "MyUniqueNodejs01",
        "version": "0.0.1",
        "description": "A sample package.json file",
        "dependencies": {
                "express": "3.4.x",
                "jade": "1.1.x"
        },
        "engines": {
                "node": "0.10.x"
        },
        "scripts": {
                  "start": "node app.js"
        }
 }
    ```

如需 Node.js 應用程式的相關提示，請參閱 [Tips for Node.js Applications ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window}。

## 將 {{site.data.keyword.cloud_notm}} Liberty 應用程式匯入至 Eclipse 之後，`server.xml` 檔案中出現配置錯誤
{: #ts_eclipse}
{: troubleshoot}

如果您在將 {{site.data.keyword.cloud_notm}} Liberty 應用程式匯入至 Eclipse 之後，於 `server.xml` 檔案中看到配置錯誤，則可能需要移除專案中的 `server.xml` 檔案。

將 {{site.data.keyword.cloud_notm}} Liberty 應用程式匯入至 Eclipse 之後，您會從「Eclipse 問題」視圖中，看到 `server.xml` 檔案內的配置錯誤。
{: tsSymptoms}

Liberty 建置套件會使用 `server.xml` 檔案來配置應用程式，並且在將 Liberty 應用程式推送至 {{site.data.keyword.cloud_notm}} 時產生 `runtime-vars.xml` 檔案。將應用程式匯入至 Eclipse 時，本端環境中沒有 `runtime-vars.xml` 檔案。
{: tsCauses}

您可以移除專案中的 server.xml 檔案，來解決此問題。將應用程式推送為 WAR 應用程式時，此建置套件會動態建立 `server.xml` 檔案。如需相關資訊，請參閱 [Liberty for Java](/docs/runtimes/liberty/index.html)。
{: tsResolve}

## 無法使用自訂建置套件來編譯打包應用程式
{: #ts_bp_compilation}
{: troubleshoot}

如果自訂建置套件中的 Script 不是執行檔，則可能無法使用該建置套件將應用程式部署至 {{site.data.keyword.cloud_notm}}。

使用自訂建置套件將應用程式部署至 {{site.data.keyword.cloud_notm}} 時，您會看到`無法編譯打包應用程式，因此沒有可顯示的實例`錯誤訊息。
{: tsSymptoms}

如果 Script（例如偵測 Script、編譯 Script 及釋放 Script）無法執行，就可能會發生此問題。
{: tsCauses}

您可以使用 [Git 更新 ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")](http://git-scm.com/docs/git-update-index){: new_window} 指令，將每一個 Script 的許可權變更為「可執行」。例如，您可以鍵入 `git update --chmod=+x script.sh`。
{: tsResolve}

## 在 {{site.data.keyword.cloud_notm}} Continuous Delivery 中無法從 Delivery Pipeline 部署應用程式
{: #ts_devops_to_bm}
{: troubleshoot}

 如果應用程式中沒有 `manifest.yml` 檔案，您可能無法在 {{site.data.keyword.contdelivery_short}} 中使用 {{site.data.keyword.deliverypipeline}} 來部署應用程式。

 當您在 {{site.data.keyword.contdelivery_short}} 中使用 {{site.data.keyword.deliverypipeline}} 來部署應用程式時，可能會顯示`偵測不到支援的應用程式類型`錯誤訊息。
 {: tsSymptoms}

 因為管線需要 `manifest.yml` 檔案，才能將應用程式部署至 {{site.data.keyword.cloud_notm}}，所以可能會發生此問題。
 {: tsCauses}

 若要解決此問題，您必須建立 `manifest.yml` 檔案。如需如何建立 `manifest.yml` 檔案的相關資訊，請參閱[應用程式資訊清單](/docs/manageapps/depapps.html#appmanifest)。
 {: tsResolve}

## 無法推送 Meteor 應用程式
{: #ts_meteor}
{: troubleshoot}

如果未正確指定建置套件，您可能無法將 Meteor 應用程式推送至 {{site.data.keyword.cloud_notm}}。

當您將 Meteor 應用程式部署至 {{site.data.keyword.cloud_notm}} 時，可能會看到此錯誤訊息：`無法編譯打包應用程式，因此沒有可顯示的實例。`
{: tsSymptoms}

此問題的發生原因是未針對 Meteor 應用程式提供內建的建置套件。您必須使用自訂建置套件。
{: tsCauses}

若要針對 Meteor 應用程式使用自訂建置套件，請使用下列其中一種方法：
{: tsResolve}

  * 如果您使用 `manifest.yml` 檔案來部署應用程式，請使用 buildpack 選項指定自訂建置套件的 URL 或名稱。例如：
  ```yaml
  buildpack: https://github.com/Sing-Li/bluemix-bp-meteor
  ```

  * 如果您從命令提示字元部署應用程式，請使用 `ibmcloud cf push` 指令，並使用 **-b** 選項來指定自訂建置套件。例如：
  ```
	ibmcloud cf push appname -p app_path -b https://github.com/Sing-Li/bluemix-bp-meteor
	```
  {: codeblock}

## 已超出儲存空間配額
{: #exceed_quota}

如果建置或部署工作失敗，且看到下列訊息，則您可以使用下列 CLI 指令來刪除映像檔。「狀態：未獲授權：您已超出儲存空間配額。請刪除一個以上的映像檔，或檢閱您的儲存空間配額及定價方案。」

* 安裝 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html)，如果您還沒有它的話。
* 使用 `ibmcloud login` 登入 {{site.data.keyword.cloud_notm}}，並將它指向您所在的空間。
* 使用 `ibmcloud cr images` 列出您的映像檔。
* 使用 `ibmcloud cr image-rm <respository>:<tag>` 來刪除任何未用的映像檔。
* 重新執行失敗的建置或部署工作。

## 存取 Kubernetes 日誌
{: #access_kube_logs}

如果應用程式不在執行中，且您無法存取性能端點，請嘗試查看叢集裡的日誌。
* 安裝 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html)，如果您還沒有它的話。
* 使用 `ibmcloud login` 登入 {{site.data.keyword.cloud_notm}}，並將它指向您所在的空間。
* 使用 `ibmcloud cs clusters` 列出您的叢集。
* 使用 `ibmcloud cs cluster-config <cluster-name>` 指向您的對應叢集。
* 匯出列出的環境變數。
* 使用 `kubectl get pods` 檢視您的 Pod。如果您需要安裝 `kubectl`，請參閱[安裝並設定 kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)。
* 您可以使用 `kubectl logs <pod-name>` 來檢視應用程式中的日誌。


## 啟動 `docker` 時失敗，並出現「找不到檔案」訊息
{: #docker_not_found}
{: troubleshoot}

當您嘗試啟動 Docker 時，會顯示下列錯誤訊息：
{: tsSymptoms}

```
An error exec: "docker": executable file not found in $PATH was encountered while building the Docker image.
```
{: screen}

Docker 用戶端未安裝，或是它已安裝但未啟動。
{: tsCauses}

請確定 [Docker](https://docs.docker.com/install/) 已安裝，然後啟動它。
{: tsResolve}


## 建置應用程式時失敗，並出現 Docker 錯誤
{: #build_error}
{: troubleshoot}

當您嘗試使用 `ibmcloud dev build` 指令建置應用程式時，它失敗並且出現 Docker 使用者名稱/密碼錯誤。
{: tsSymptoms}

使用了不正確的 Docker Hub 認證來進行鑑別。
{: tsCauses}

請在 Docker 用戶端中登出 Docker Hub。
{: tsResolve}


