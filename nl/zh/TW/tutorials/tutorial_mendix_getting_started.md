---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-03"

keywords: apps, Mendix, starter kit, developer tools, Mendix app, create mendix app

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note .note}

# 使用 Mendix 建立應用程式
{: #create-mendix}

Mendix 是低程式碼開發環境及工具集，它能協助您更快速地遞送多裝置應用程式、使用更少開發資源，並且在 {{site.data.keyword.cloud}} 上執行。藉由選取 Mendix 低程式碼入門範本套件，系統會引導您在 Mendix Platform 上設定帳戶、啟動專案，以及選取 Cloud Foundry 或 Kubernetes 叢集的部署目標。
{: shortdesc}

## 選取入門範本套件
{: #starterkit-mendix}

1. 從「[{{site.data.keyword.cloud_notm}} 應用程式服務」儀表板 ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示") 中，按一下**開始使用**。
2. 從下列其中一個種類選取 Mendix 低程式碼入門範本套件：
  * [行動 ](https://{DomainName}/developer/appservice/starter-kits/mendix-mobile-app){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")
  * [Watson Web or Mobile App ](https://{DomainName}/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")
  * [Web 應用程式 ](https://{DomainName}/developer/appservice/starter-kits/mendix-web-app){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")
3. 按一下**建立應用程式**。
4. 在**應用程式詳細資料**頁面上，將應用程式命名，並選擇性地提供標記來分類應用程式。如需相關資訊，請參閱[使用標籤](/docs/resources?topic=resources-tag)。
5. 按一下**建立**。

## 授權 IBM 在 Mendix 上建立專案並鏈結帳戶
{: #link-mendix-account}

如果您尚未使用 Mendix 搭配 {{site.data.keyword.cloud_notm}}，則您會被引導至 Mendix Platform 註冊及授權 {{site.data.keyword.cloud_notm}} 代表您在 Mendix Platform 上建立新專案。這個專案會鏈結至 {{site.data.keyword.cloud_notm}}，因此部署會自動導向 {{site.data.keyword.cloud_notm}}。

1. 如果您看到此訊息，請按一下**鏈結帳戶**。
  ```
  「若要完成應用程式建立，需要 Mendix 使用者帳戶。您要現在鏈結您的帳戶嗎？」
  ```
  {: screen}

2. 在 Mendix 確認頁面上，選取**我同意接受 Mendix 隱私權條款**，然後按一下**確認**。
3. 看到提示時，提供您的電子郵件位址、密碼及國家/地區，然後按一下**建立**。
4. 在**授權存取您的 Mendix 帳戶**頁面上，按一下**授權**。

授權完成之後，您的瀏覽器會回到正在建立的 Mendix 應用程式。即會顯示**選取部署目標**頁面。

## 選取 Mendix 應用程式的部署目標
{: #select-deployment}

1. 在**選取部署目標**頁面上，選取 Cloud Foundry，或其中一個在 {{site.data.keyword.cloud_notm}} 上執行的 Kubernetes 叢集。如果您的帳戶可以存取 {{site.data.keyword.cfee_full_notm}}，則可以選取**[公用雲端](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)**或**[企業環境](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**的 Cloud Foundry 部署人員類型，用來建立及管理用於管理專供您企業使用的 Cloud Foundry 應用程式的隔離環境。
2. 選用。如果您沒有 Kubernetes 叢集，可以現在建立一個。
3. 在**配置工具鏈**頁面上，選取您的地區及資源群組，然後按一下**建立**。

即會建立 DevOps 工具鏈。工具鏈會在 {{site.data.keyword.cloud_notm}} 環境中整合 Mendix Platform 內的 Mendix 專案。預設應用程式會部署至部署目標，讓您可以驗證應用程式在 DevOps 工具鏈完成時已順利部署。

Mendix Cloud Foundry 部署需要 PostGRES 資料庫服務，該服務沒有精簡層級。如果您想要使用精簡帳戶評估 Mendix 入門範本套件，可以將目標設為試用 Kubernetes 叢集。
{: tip}

如果您已選取 Kubernetes 叢集以進行部署，請參閱 [Mendix Kubernetes 指導教學](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube)，了解如何配置叢集以供正式作業使用。

## 繼續 Mendix 開發及部署生命週期
{: #dev-lifecycle-mendix}

Mendix 是低程式碼的編寫環境。開發生命週期會需要您在 Mendix Modeler 桌面應用程式中開啟專案。

1. 從您的 {{site.data.keyword.cloud_notm}} 應用程式，按一下**在 Mendix 上編輯**。
2. 在 Mendix Web 入口網站中，按一下 **Edit in Desktop Modeler**。Mendix 應用程式會在 Desktop Modeler 中開啟。
3. 編輯您的 Mendix 應用程式，然後儲存變更。
4. 使用 Mendix Desktop Modeler 應用程式的 **Run** 功能表，選取 **Run** 選項。即會建立部署套件並上傳到 Mendix。建立部署套件之後，您可以將應用程式部署至 {{site.data.keyword.cloud_notm}}。
5. 若要部署 Mendix 應用程式，請回到 {{site.data.keyword.cloud_notm}} 上的**應用程式詳細資料**頁面，然後按一下**部署**。這個動作會啟動您應用程式的 DevOps 工具鏈，它會從 Mendix 取回最新的部署，並將它部署至您的目標環境。部署完成之後，最新版的應用程式會自動啟動並變成可用。

在 {{site.data.keyword.cloud_notm}} 上的**應用程式詳細資料**頁面中按一下**配置持續交付**，所有 Mendix 應用程式即會部署至 {{site.data.keyword.cloud_notm}}。請不要透過 IBM DevOps 介面手動呼叫 Mendix 工具鏈。透過 DevOps 介面手動啟動工具鏈，可能會導致因為缺乏對 Mendix 部署很重要之必要 meta 資料，而使部署失敗。視您應用程式的狀態而定，可能會在 DevOps 工具鏈啟動期間失敗，或在已部署的應用程式中發生錯誤。

如果您手動啟動工具鏈而遭遇失敗，您可以在 {{site.data.keyword.cloud_notm}} 上的**應用程式詳細資料**頁面中，按一下**配置持續交付**來還原應用程式部署。這個動作會為 Mendix 應用程式觸發完整的 DevOps 流程，這會包含必要的 meta 資料。
{: tip}

## 選用項目：配置 {{site.data.keyword.cos_full_notm}} 
{: #mendix-cos}

部分使用者可能想要配置其部署的 Mendix 應用程式，以將 {{site.data.keyword.cos_full}} 用於持續性儲存空間及檔案上傳。{{site.data.keyword.cos_full_notm}} 是 S3 相容物件儲存空間服務。若要利用 S3 相容檔案儲存空間，Mendix 應用程式必須在配置了持續交付之後定義下列環境變數，才能存取 {{site.data.keyword.cos_full_notm}} 實例：

* `S3_ACCESS_KEY_ID` - S3 金鑰，其為 {{site.data.keyword.cos_full_notm}} 認證的一部分
* `S3_SECRET_ACCESS_KEY` - S3 秘密金鑰，其為 {{site.data.keyword.cos_full_notm}} 認證的一部分
* `S3_BUCKET_NAME` - S3 儲存空間儲存區
* `S3_ENDPOINT` - S3 儲存空間端點
* `S3_USE_V2_AUTH` - 值為 `true`

如需 {{site.data.keyword.cos_full_notm}} 儲存區及金鑰的相關資訊，請參閱 [{{site.data.keyword.cos_full_notm}} API 文件](/docs/services/cloud-object-storage?topic=cloud-object-storage-gs-dev)。如需地區及跨地區端點值的相關資訊，請參閱 [{{site.data.keyword.cos_full_notm}} 文件](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints)。如需 S3 相容儲存空間支援 Mendix 的相關資訊，請參閱 [Mendix 建置套件文件](https://github.com/mendix/cf-mendix-buildpack#s3-settings){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")。

### Cloud Foundry 應用程式的 {{site.data.keyword.cos_full_notm}} 設定
{: cos-cfapps}

請完成下列步驟，進行 Cloud Foundry 部署：

1. 部署 Cloud Foundry 時，使用 `cf set-env` 指令來設定下列環境變數：

  ```
    ibmcloud cf set-env <YOUR_APP> S3_ACCESS_KEY_ID <YOUR_KEY>
    ibmcloud cf set-env <YOUR_APP> S3_SECRET_ACCESS_KEY <YOUR_SECRET_KEY>
    ibmcloud cf set-env <YOUR_APP> S3_BUCKET_NAME <YOUR_BUCKET>
    ibmcloud cf set-env <YOUR_APP> S3_ENDPOINT s3.us-south.cloud-object-storage.appdomain.cloud
    ibmcloud cf set-env <YOUR_APP> S3_USE_V2_AUTH true
  ```

2. 在指定所有這些值之後，請重新編譯打包 Cloud Foundry 應用程式，以套用新值。

  ```
    ibmcloud cf restage <YOUR_APP>
  ```

### Kubernetes 應用程式的 {{site.data.keyword.cos_full_notm}} 設定
{: #cos-kubeapps}

請針對 Kubernetes 部署完成下列步驟：

1. 將 `S3_ACCESS_KEY_ID` 及 `S3_SECRET_ACCESS_KEY` 環境變數設為叢集中的 Kubernetes 密碼值。如需建立 Kubernetes 密碼的相關資訊，請參閱 [{{site.data.keyword.containershort_notm}} 文件](/docs/containers?topic=containers-service-binding#adding_app)。

2. 除了任何現有值之外，也請指定環境變數作為 `mendix-app.yaml` 檔中的其他環境變數，而此檔案位於 Git 儲存庫的 `chart/<appname>/templates` 資料夾內。密碼名稱必須符合已在前一個步驟中建立的名稱。

  ```
    env:
      - name: S3_ACCESS_KEY_ID
        valueFrom:
          secretKeyRef:
            name: "mendix-s3-key"
            key: db-endpoint
      - name: S3_SECRET_ACCESS_KEY
        valueFrom:
          secretKeyRef:
            name: "mendix-s3-secret-key"
            key: db-endpoint
      - name: S3_ENDPOINT
        value: "s3.us-south.cloud-object-storage.appdomain.cloud"
      - name: S3_USE_V2_AUTH
        value: "true"
  ```

3. 在套用 Kubernetes 變更之後，請導覽至**應用程式詳細資料**頁面，並按一下**部署**，來重新部署您的應用程式。 

## 後續步驟 
{: #next-steps-mendix}

若要將您的應用程式部署至 {{site.data.keyword.containerlong_notm}}，請配置應用程式以便進行正式作業部署。如需相關資訊，請參閱 [Mendix Kubernetes 指導教學](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube)。 
