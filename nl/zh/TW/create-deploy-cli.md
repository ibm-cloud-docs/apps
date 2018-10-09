---
copyright:

  years: 2018

lastupdated: "2018-10-02"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}

# 使用 CLI 建立及部署應用程式
{: #developing}

您可以使用 {{site.data.keyword.Bluemix}} 指令行介面 (CLI) 來建立及部署應用程式。
{:shortdesc}

## 開始之前
{: #prereqs}

請安裝 {{site.data.keyword.Bluemix_notm}} CLI、{{site.data.keyword.dev_cli_notm}} CLI 外掛程式，及其他建議的外掛程式和工具。如需相關資訊，請參閱[開始使用 IBM Cloud CLI](/docs/cli/index.html)。 

## 建立應用程式
{: #create}

您可以從頭開始建立新的應用程式，或使用現有程式碼建立具有雲端功能的應用程式。 

### 從頭開始建立應用程式

1. 在您選擇的目錄中執行 [`ibmcloud dev create`](/docs/cli/idt/commands.html#create) 指令。
2. 選取**後端服務 / Web 應用程式**作為應用程式類型。
3. 選取 **Node** 作為語言類型。
4. 選取 **Express.js Basic (Web App)** 作為要使用的入門範本套件。
5. 輸入應用程式的名稱，並選取您要使用的資源群組（必要的話）。目前請不要新增服務。
6. 選取 **IBM DevOps，使用 Cloud Foundry** 選項來建立 DevOps 工具鏈。您可能需要設定 SSH 金鑰，才能完成此步驟。
7. 輸入唯一的主機名稱，例如 `abc-devhost`。這個主機名稱是您應用程式的路徑，`abc-devhost.mybluemix.net`。

建立應用程式及工具鏈需要幾秒鐘才能完成。您可以在命令提示字元監視狀態。

### 使用現有程式碼建立應用程式

1. 在您選擇的目錄中執行下列指令，以複製 [Hello World 範例應用程式](https://github.com/IBM-Cloud/node-helloworld)。

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

2. 導覽至您複製範例應用程式的目錄，然後執行 [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable) 指令。
3. 選取繼續而不現在確定變更至 GitHub。
4. 當系統提示您以偵測到的 Node 語言繼續時，選取要繼續。
5. 選取您要使用的資源群組（必要的話）。目前請不要新增服務。
6. 等待幾秒鐘讓應用程式建立。 
7. 您可以選擇手動合併在建立應用程式時儲存到應用程式目錄的部署和配置檔。或者，您可以目前先跳過此步驟。

## 建置應用程式並在本端執行它
{: #build-run}

不論您用來建立應用程式的選項為何，您現在可以建置它並在本端執行。

1. 導覽至您的應用程式目錄，並確定 Docker 正在系統上執行。
2. 執行 [`ibmcloud dev build`](/docs/cli/idt/commands.html#build) 指令，以建置應用程式。
3. 執行 [`ibmcloud dev run`](/docs/cli/idt/commands.html#run) 指令，以開始在本端執行應用程式。
4. 在 `http://localhost:3000` 或類似的 URL 檢視本端執行的應用程式。
5. 按 **Ctrl+C** 鍵可停止應用程式。

您也可以使用[複合指令](/docs/cli/idt/commands.html#compound)，例如 `ibmcloud dev build/run`，來循序地發出建置，然後執行。
{: tip}

## 新增服務及修改程式碼
{: #add-service}

既然您的應用程式可以在本端執行，便可以新增服務然後修改部分程式碼。 

1. 執行 [`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit) 指令。
2. 遵循提示以建立新的資料相關服務並將它連接至您的應用程式，例如 {{site.data.keyword.cloudant_short_notm}}。您可能需要為服務選取地區及方案。
3. 您可以選擇手動合併在建立服務時儲存到應用程式目錄的部署和配置。或者，您可以目前先跳過此步驟。
4. 變更程式碼。例如，修改 `/public/index.html` 檔或類似檔案。如果您使用範例 `ExpressJS` 應用程式，可以變更 `Congratulations!` 字串，成為像是 `Hello World!` 的字串。
5. 儲存您已修改的任何檔案。

## 部署至 {{site.data.keyword.Bluemix_notm}}
{: #deploy}

您可以用兩種方式之一來部署應用程式至 {{site.data.keyword.Bluemix_notm}}，視應用程式的配置方式而定。 

### 使用 DevOps 工具鏈來部署應用程式

如果您先前為應用程式建立了 DevOps 工具鏈，那麼部署新的建置就很簡單，只需要確定並推送程式碼至工具鏈中的儲存庫。 

1. 執行 `git add .` 指令。
2. 執行 `git commit -m "made changes"` 指令來確定變更。
3. 執行 `git push origin master` 指令來推送至主節點分支。
4. 從 {{site.data.keyword.Bluemix_notm}} 主控台，檢視應用程式的 DevOps 工具鏈。您可以藉由從應用程式目錄執行 [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) 指令，然後按一下**檢視工具鏈**，以在 Web 瀏覽器中檢視工具鏈。
5. 檢視工具鏈內的管線，以驗證已啟動新的建置。

### 手動部署應用程式

您可以使用 [`deploy`](/docs/cli/idt/commands.html#deploy) 指令，以手動部署應用程式。例如，使用下列步驟，將應用程式手動部署至 Kubernetes。

1. 確定您已[建立 Kubernetes 叢集](https://console.bluemix.net/containers-kubernetes/overview)。
2. 執行 [`ibmcloud dev deploy -t container`](/docs/cli/idt/commands.html#deploy) 指令。
3. 收到提示時，確認要使用的叢集和容器映像檔名稱。
4. 等待幾分鐘讓部署完成。

## 檢視應用程式
{: #view}

1. 若要檢視在 {{site.data.keyword.Bluemix_notm}} 上執行之應用程式的 URL，請執行 [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) 指令。
2. 若要從 {{site.data.keyword.Bluemix_notm}} 主控台檢視應用程式的認證、服務和工具鏈詳細資料，請執行 [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) 指令。 

