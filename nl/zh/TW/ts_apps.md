---

copyright:
  years: 2015, 2019
lastupdated: "2019-05-08"

keywords: apps, application, troubleshooting, debug apps, known issues, debug, help, configuration, app, troubleshoot, error, errors, failure, failed, fail, issues, applications

subcollection: creating-apps

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

## 我的應用程式是在不同網域中進行管理
{: #domains-ts}
{: troubleshoot}

我的部分應用程式是在 `mybluemix.net` 網域中進行管理，但其他應用程式是在 `appdomain.cloud` 網域中進行管理。

我的現有應用程式是在 `mybluemix.net` 網域中進行管理，但我的更新應用程式是在 `appdomain.cloud` 網域中進行管理。
{: tsSymptoms}

cloud.ibm.com 上提供新的主機名稱選項 `*.appdomain.cloud`。

先前，`mybluemix.net` 網域用於管理各種部署目標中的應用程式，例如 {{site.data.keyword.containerlong_notm}} 或 Cloud Foundry。您已在 `mybluemix.net` 上管理的任何應用程式都不會受到影響。

Cloud Foundry 應用程式的子網域是 `cf.appdomain.cloud`。您部署至 {{site.data.keyword.containerlong_notm}} 之應用程式的子網域是 `containers.appdomain.cloud`。

如需相關資訊，請參閱[管理網域](/docs/apps?topic=creating-apps-update-domain)。

## 您有未儲存的變更
{: #ts_unsaved_changes}
{: troubleshoot}

當您按一下應用程式詳細資料頁面上的項目時，可能無法執行任何動作。您也可能會收到要先儲存變更才能繼續的提示。

在應用程式詳細資料頁面上嘗試檢查應用程式或服務時，會顯示下列錯誤訊息：
{: tsSymptoms}

`您有未儲存的變更。您確定要離開此頁面嗎？`

在運行環境窗格的**實例**或**記憶體配額**欄位上捲動滑鼠時，值就會變更。此行為是按照設計而來。不過，您會收到提示，提醒您在移至另一個頁面之前，要先儲存記憶體或實例設定。
{: tsCauses}

關閉訊息視窗，然後按一下運行環境窗格中的**重設**。
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

如需可在其他程式語言中使用之指令的相關資訊，請參閱 [Java ](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 和 [Ruby ](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。




## 收到 502 錯誤的閘道錯誤
{: #ts_502_error}
{: troubleshoot}

如果您在 {{site.data.keyword.cloud_notm}} 上與應用程式互動時，收到 `502 Bad Gateway` 錯誤，請檢查 {{site.data.keyword.cloud_notm}} 狀態頁面，然後採取適當的動作。

您收到開頭為 502 Bad Gateway 的錯誤訊息。例如，您可能會看到 `502 Bad Gateway: Registered endpoint failed to handle the request`。
{: tsSymptoms}

「錯誤的閘道」錯誤通常發生在您前往網站使用 Proxy 伺服器來儲存及轉遞來自管理網站之主要伺服器的資料時。主要伺服器及 Proxy 伺服器可能未適當連接。那麼，您會在瀏覽器視窗中看到 HTTP 狀態碼 502。此狀態碼表示網站的主要伺服器未收到它預期來自 Proxy 伺服器的 HTTP 實作。
{: tsCauses}

其他較少見的「錯誤的閘道」錯誤原因，包括網際網路服務供應商 (ISP) 脫離、不正確的防火牆配置及瀏覽器快取錯誤。

如果您懷疑 {{site.data.keyword.cloud_notm}} 服務已關閉，請先檢查 [{{site.data.keyword.cloud_notm}} 狀態 ](https://cloud.ibm.com/status){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 頁面。[在另一個 {{site.data.keyword.cloud_notm}} 地區中使用服務](/docs/resources/connect_external_app?topic=resources-externalapp){: new_window}也許可以作為暫行解決方法。如果服務狀態正常，請嘗試下列步驟來解決問題：
{: tsResolve}

  * 重試動作：
    * 按鍵盤上的 F5，或按一下**重新整理**，來重新載入頁面。如果此步驟無效，請清除瀏覽器的快取及 Cookie，然後再重新載入。
    
    * 使用不同的瀏覽器。
    * 重新啟動路由器、數據機及電腦。將這些裝置重新開機可清除導致錯誤 502 的許多種錯誤。
  * 等待並於稍後再試一次。暫時發生的問題可能是由於網際網路服務供應商或 {{site.data.keyword.cloud_notm}} 服務所造成。您可能要等待暫時問題獲得解決。
  * 如果問題仍然存在，請與 {{site.data.keyword.cloud_notm}} 支援中心聯絡。如需相關資訊，請參閱[聯絡 {{site.data.keyword.cloud_notm}} 支援中心 ](/docs/get-support?topic=get-support-getting-customer-support){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。

## Android 應用程式無法收到 {{site.data.keyword.mobilepushshort}}
{: #ts_push}
{: troubleshoot}

在無法存取 Google 的特定地區中，Android 應用程式收不到您透過 IBM {{site.data.keyword.mobilepushshort}} 服務送出的通知。在此情況下，暫行解決方法是使用協力廠商服務。

為您的 {{site.data.keyword.cloud_notm}} 應用程式連結一個 {{site.data.keyword.mobilepushshort}} 服務，並將訊息傳送至已登錄的裝置。不過，在特定地區，Android 上開發的應用程式收不到您的通知。
{: tsSymptoms}

IBM {{site.data.keyword.mobilepushshort}} 服務使用「Google 雲端通訊 (GCM)」服務，將通知分派至 Android 上開發的行動應用程式。若要讓 Android 應用程式收到通知，行動應用程式必須可存取「Google 雲端通訊 (GCM)」服務。在 Android 應用程式無法呼叫到 GCM 服務的地區，Android 應用程式即收不到 {{site.data.keyword.mobilepushshort}}。
{: tsCauses}

暫行解決方法是使用不依賴 GCM 服務的協力廠商服務，例如 [Pushy ](https://pushy.me){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")、[getui ](http://www.getui.com/){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 及 [jpush ](https://www.jpush.cn/){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。
{: tsResolve}

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

    * 使用 [package.json ](https://www.npmjs.com/package/jsonfile){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 檔案。例如：
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

如需 Node.js 應用程式的相關提示，請參閱 [Tips for Node.js Applications ](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。

## 將 {{site.data.keyword.cloud_notm}} Liberty 應用程式匯入至 Eclipse 之後，`server.xml` 檔案中出現配置錯誤
{: #ts_eclipse}
{: troubleshoot}

如果您在將 {{site.data.keyword.cloud_notm}} Liberty 應用程式匯入至 Eclipse 之後，於 `server.xml` 檔案中看到配置錯誤，則可能需要移除專案中的 `server.xml` 檔案。

將 {{site.data.keyword.cloud_notm}} Liberty 應用程式匯入至 Eclipse 之後，您會從「Eclipse 問題」視圖中，看到 `server.xml` 檔案內的配置錯誤。
{: tsSymptoms}

Liberty 建置套件會使用 `server.xml` 檔案來配置應用程式，並且在將 Liberty 應用程式推送至 {{site.data.keyword.cloud_notm}} 時產生 `runtime-vars.xml` 檔案。將應用程式匯入至 Eclipse 時，本端環境中沒有 `runtime-vars.xml` 檔案。
{: tsCauses}

您可以移除專案中的 server.xml 檔案，來解決此問題。將應用程式推送為 WAR 應用程式時，此建置套件會動態建立 `server.xml` 檔案。如需相關資訊，請參閱 [Liberty for Java](/docs/runtimes/liberty?topic=liberty-liberty_runtime#liberty_runtime)。
{: tsResolve}

## 無法使用自訂建置套件來編譯打包應用程式
{: #ts_bp_compilation}
{: troubleshoot}

如果自訂建置套件中的 Script 不是執行檔，則可能無法使用該建置套件將應用程式部署至 {{site.data.keyword.cloud_notm}}。

使用自訂建置套件將應用程式部署至 {{site.data.keyword.cloud_notm}} 時，您會看到`無法編譯打包應用程式，因此沒有可顯示的實例`錯誤訊息。
{: tsSymptoms}

如果 Script（例如偵測 Script、編譯 Script 及釋放 Script）無法執行，就可能會發生此問題。
{: tsCauses}

您可以使用 [Git 更新 ](http://git-scm.com/docs/git-update-index){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 指令，將每一個 Script 的許可權變更為「可執行」。例如，您可以鍵入 `git update --chmod=+x script.sh`。
{: tsResolve}

## 在 {{site.data.keyword.cloud_notm}} Continuous Delivery 中無法從 Delivery Pipeline 部署應用程式
{: #ts_devops_to_bm}
{: troubleshoot}

 如果應用程式中沒有 `manifest.yml` 檔案，您可能無法在 {{site.data.keyword.contdelivery_short}} 中使用 {{site.data.keyword.deliverypipeline}} 來部署應用程式。

 當您在 {{site.data.keyword.contdelivery_short}} 中使用 {{site.data.keyword.deliverypipeline}} 來部署應用程式時，可能會顯示`偵測不到支援的應用程式類型`錯誤訊息。
 {: tsSymptoms}

 因為管線需要 `manifest.yml` 檔案，才能將應用程式部署至 {{site.data.keyword.cloud_notm}}，所以可能會發生此問題。
 {: tsCauses}

 若要解決此問題，您必須建立 `manifest.yml` 檔案。如需如何建立 `manifest.yml` 檔案的相關資訊，請參閱[應用程式資訊清單](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest)。
 {: tsResolve}

## 已超出您的儲存空間配額
{: #exceed_quota}

如果建置或部署工作失敗，且看到下列訊息，則您可以使用下列 CLI 指令來刪除映像檔。`狀態：未獲授權：您已超出儲存空間配額。請刪除一個以上的映像檔，或檢閱您的儲存空間配額及定價方案。`

* 如果您還沒有 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli)，請安裝它。
* 使用 `ibmcloud login` 登入 {{site.data.keyword.cloud_notm}}，並將它指向您所在的空間。
* 使用 `ibmcloud cr images` 列出您的映像檔。
* 使用 `ibmcloud cr image-rm <respository>:<tag>` 來刪除任何未用的映像檔。
* 重新執行失敗的建置或部署工作。

## 存取 Kubernetes 日誌
{: #access_kube_logs}

如果應用程式不在執行中，且您無法存取性能端點，請嘗試查看叢集裡的日誌。
* 如果您還沒有 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli)，請安裝它。
* 使用 `ibmcloud login` 登入 {{site.data.keyword.cloud_notm}}，並將它指向您所在的空間。
* 使用 `ibmcloud cs clusters` 列出您的叢集。
* 使用 `ibmcloud cs cluster-config <cluster-name>` 指向您的對應叢集。
* 匯出列出的環境變數。
* 使用 `kubectl get pods` 檢視您的 Pod。如果需要安裝 `kubectl`，請參閱[安裝及設定 kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。
* 您可以使用 `kubectl logs <pod-name>` 來檢視應用程式中的日誌。

## 啟動 `docker` 失敗，並出現「找不到檔案」訊息
{: #docker_not_found}
{: troubleshoot}

嘗試啟動 Docker 時，顯示下列錯誤訊息：
{: tsSymptoms}

```
An error exec: "docker": executable file not found in $PATH was encountered while the Docker image is building.
```
{: screen}

Docker 用戶端未安裝，或是它已安裝但未啟動。
{: tsCauses}

確定 [Docker](https://docs.docker.com/install/){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 已安裝，並啟動它。
{: tsResolve}

## 建置應用程式失敗，並出現 Docker 錯誤
{: #build_error}
{: troubleshoot}

當您嘗試使用 `ibmcloud dev build` 指令建置應用程式時，它失敗並且出現 Docker 使用者名稱/密碼錯誤。
{: tsSymptoms}

使用了不正確的 Docker Hub 認證來進行鑑別。
{: tsCauses}

請在 Docker 用戶端中登出 Docker Hub。
{: tsResolve}
