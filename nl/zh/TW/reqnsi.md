---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-15"

keywords: apps, services, add service, application

subcollection: creating-apps

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{:note: .note}

# 將服務新增至應用程式
{: #add-resource}

使用 {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}} 建立應用程式時，您可以從「應用程式詳細資料」頁面新增服務。不過，您也可以從應用程式的環境定義之外，直接從 {{site.data.keyword.cloud_notm}} 型錄佈建它們。
{: shortdesc}

您可以要求服務的實例，並單獨於應用程式之外使用，也可以從「應用程式詳細資料」頁面，將服務實例新增至應用程式。您可以直接從 {{site.data.keyword.cloud_notm}} 型錄佈建特定類型的服務。

## 探索服務
{: #discover-resources}

您可以用下列方式查看 {{site.data.keyword.cloud_notm}} 中可用的所有服務：


* 從 {{site.data.keyword.cloud_notm}} 主控台。檢視 {{site.data.keyword.cloud_notm}} 型錄。
* 從指令行。使用 `ibmcloud service offerings` 指令。
* 從您自己的應用程式。請使用 [GET /v2/services Services API ](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。

在開發應用程式時，您可以選取需要的服務。選取它之後，{{site.data.keyword.cloud_notm}} 會佈建服務。不同類型的服務，佈建處理程序可能不同。例如，資料庫服務會建立資料庫，而行動應用程式的推送通知服務則會產生配置資訊。


{{site.data.keyword.cloud_notm}} 會透過使用服務實例，將服務資源提供給應用程式。服務實例可以在 Web 應用程式之間共用。

如果在其他地區中管理的服務能用於那些地區，則您也可以使用那些服務。這些服務必須可從網際網路存取，並具有 API 端點。您必須用您編碼外部應用程式或協力廠商工具以使用 {{site.data.keyword.cloud_notm}} 服務的相同方式，手動編碼應用程式來使用這些服務。如需相關資訊，請參閱[將服務連接至外部應用程式](/docs/resources?topic=resources-externalapp)。

## 要求新的服務實例
{: #request-instance}

若要要求新的服務實例，您必須使用 {{site.data.keyword.cloud_notm}} 使用者介面或 {{site.data.keyword.cloud_notm}} 指令行介面。

當您指定服務名稱時，請避免非英文字母或數值字元的字元，因為結果可能無法預期。
{: note}

如果您使用 {{site.data.keyword.cloud_notm}} 使用者介面來要求服務實例，請完成下列步驟：

1. 在 {{site.data.keyword.cloud_notm}} 型錄中，按一下您要新增的服務磚。即會開啟「服務詳細資料」頁面。

2. 在**服務名稱**欄位鍵入名稱。會提供預設名稱。您可以在欄位中變更名稱，或是將它保留不變。

3. 完成其他欄位或選擇，然後按一下**建立**。

如果您使用 {{site.data.keyword.cloud_notm}} 指令行介面來要求服務實例，請下載應用程式、在本端開啟指令行，然後切換至應用程式目錄。

1. 執行下列指令，以將服務新增至應用程式。您可以從帳戶上已啟用的服務選取現有服務，或是新增一個服務。

  ```bash
  ibmcloud dev edit
  ```
  {: pre}

2. 遵循提示以選取資源群組，及建立新的資料相關服務並將它連接至您的應用程式，例如 Cloudant。您可能需要為服務選取地區及方案。
3. 建立服務時，會將數個檔案（包括認證）新增至您的應用程式目錄，以協助您將服務整合到應用程式。您可以手動合併任何檔案，或是目前先跳過此步驟。

您可以將服務實例僅連結至位於相同空間或組織中的應用程式實例。然而，使用其他空間或組織中的服務實例的方式，與使用外部應用程式的方式一樣。請使用認證直接配置應用程式實例，而非建立連結。如需外部應用程式如何使用 {{site.data.keyword.cloud_notm}} 服務的相關資訊，請參閱[讓外部應用程式能使用 {{site.data.keyword.cloud_notm}} 服務](/docs/resources?topic=resources-externalapp#externalapp)。

## 配置應用程式
{: #configure-app}

將服務實例連結至應用程式之後，您必須配置應用程式以與服務互動。

每一個服務可能需要不同的機制來和應用程式通訊。
這些機制記載於服務定義的一部分，以在您開發應用程式時作為參考資訊。
為了一致性，必須要有機制，您的應用程式才能與服務互動。


* 若要與資料庫服務互動，請使用 {{site.data.keyword.cloud_notm}} 所提供的資訊（例如，使用者 ID、密碼，以及應用程式的存取 URI）。
* 若要與行動後端服務互動，請使用 {{site.data.keyword.cloud_notm}} 所提供的資訊（例如，應用程式身分（應用程式 ID）、用戶端特有的安全資訊，以及應用程式的存取 URI）。行動服務通常會彼此合作，以便環境定義資訊（例如，應用程式開發人員的名稱，以及使用應用程式的使用者）能在服務集之間共用。
* 若要與 Web 應用程式或是行動應用程式的伺服器端雲端程式碼互動，請使用 {{site.data.keyword.cloud_notm}} 所提供的資訊（例如，應用程式的 *VCAP_SERVICES* 環境變數中的運行環境認證）。*VCAP_SERVICES*
環境變數的值是 JSON 物件的序列化。
變數包含與應用程式所連結之服務互動時所需要的運行環境資料。
不同服務會有不同的資料格式。
您可能需要閱讀服務文件，以瞭解預期的內容，以及如何解譯每一份資訊。


如果您連結至應用程式的服務當機，應用程式可能會停止執行或發生錯誤。{{site.data.keyword.cloud_notm}} 不會自動重新啟動應用程式，以從這些問題回復。請考慮將應用程式編碼成可識別運作中斷、異常狀況和連線失敗並從其中回復。如需相關資訊，請參閱[不會自動重新啟動應用程式](/docs/apps/troubleshoot?topic=creating-apps-managingapps#ts_apps_not_auto_restarted)。

## 跨 {{site.data.keyword.cloud_notm}} 部署環境存取服務
{: #migrate_instance}

{{site.data.keyword.cloud_notm}} 提供了許多部署選項，您可以從某個環境，存取不同環境中執行的服務。例如，如果您的服務是在 Cloud Foundry 中執行，則可以從在 Kubernetes 叢集裡執行的應用程式存取該服務。

### 範例：從 Kubernetes Pod 存取 Cloud Foundry 服務

若要從 Kubernetes 叢集裡的 Pod 存取 Cloud Foundry 服務，您必須將服務連結至叢集，以便將服務認證儲存在 Kubernetes 密碼中。然後，您便可以將此資訊提供給應用程式使用。
{: shortdesc}

依預設，儲存在 Kubernetes 密碼的服務認證是以 base64 編碼，並在 etcd 中加密。 

**重要事項**：請不要直接在部署 YAML 檔案中參照或公開您的服務認證。部署 YAML 檔案的設計並不是為了保留機密資料，且依預設不會加密您的服務認證。若要適當地儲存及存取此資訊，您必須使用 Kubernetes 密碼。 

1. [將服務連結至您的叢集](/docs/containers?topic=containers-integrations#adding_cluster)。 
2. 若要從應用程式 Pod 存取服務認證，請在下列選項之間進行選擇。 
   - 將密碼以磁區形式裝載至 Pod
   - 在環境變數中參照密碼

## 建立使用者提供的服務實例
{: #user_provide_services}

您的服務可能是在 {{site.data.keyword.cloud_notm}} 外部進行管理。如果您有認證可從網際網路存取那些外部服務，則可以建立 {{site.data.keyword.cloud_notm}} 使用者提供的服務實例來代表外部服務並與之通訊。

若要建立使用者提供的服務實例，並將它連結至應用程式，請完成下列步驟：

1. 使用 `ibmcloud service user-provided-create` 指令，建立使用者提供的服務實例：
    * 若要建立一般使用者提供的服務實例，請使用 **-p** 選項，並使用逗點區隔參數名稱。`ibmcloud` 指令行介面接著會提示您依次輸入每一個參數。例如：
        ```
        ibmcloud service user-provided-create testups1 -p "host, port, dbname, username, password"
        host> pubsub01.example.com
        port> 1234
        dbname> sampledb01
        username> pubsubuser
        password> p@$$w0rd
        Creating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * 若要建立將資訊排除至協力廠商日誌管理軟體的服務實例，請使用 `-l` 選項。請指定協力廠商日誌管理軟體提供的目的地。例如：

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example.com
        Creating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

    如果您要更新使用者提供服務實例的一個以上參數，請使用 `ibmcloud service user-provided-update`。

    * 若要更新一般使用者提供的服務實例，請使用 **-p** 選項，並在 JSON 物件中指定參數索引鍵和值。例如：

        ```
        ibmcloud service user-provided-update testups1 -p "{\"username\":\"pubsubuser2\",\"password\":\"p@$$w0rd2\"}"
        Updating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * 若要建立將資訊排除至協力廠商日誌管理軟體的服務實例，請使用 `-l` 選項。例如：

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example2.com
        Updating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

2. 使用 `ibmcloud service bind` 指令，將服務實例連結至應用程式。例如：

	```
	ibmcloud service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

您現在可以將應用程式配置成使用外部服務。如需如何配置應用程式以與服務互動的相關資訊，請參閱[配置應用程式以與服務互動](/docs/apps?topic=creating-apps-add-resource#configure-app)。
