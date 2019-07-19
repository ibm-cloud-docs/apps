---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, create, build, deploy, cli, web app, microservice

subcollection: creating-apps

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# 使用 CLI 建立及部署應用程式
{: #create-deploy-app-cli}

您可以使用 {{site.data.keyword.cloud}} 指令行介面 (CLI) 來建立及部署應用程式。 

您可以從頭開始建立入門範本應用程式，或對現有的應用程式碼啟用雲端功能。
{: note}

## 開始之前
{: #prereqs-app-cli}

您必須安裝 {{site.data.keyword.cloud_notm}} CLI、{{site.data.keyword.dev_cli_notm}} CLI 外掛程式，以及其他建議的外掛程式和工具。如需相關資訊，請參閱[開始使用 IBM Cloud CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli)。 

## 從頭開始建立入門範本應用程式
{: #create-app-cli}

如果您還沒有現有程式碼可以開始，而且寧願從某種語言或架構入門範本開始，則從頭開始建立應用程式非常實用。

1. 在您選擇的目錄中執行 [`ibmcloud dev create`](/docs/cli/idt?topic=cloud-cli-idt-cli#create) 指令。
2. 選取**後端服務 / Web 應用程式**作為應用程式類型。
3. 選取 **Node** 作為語言類型。
4. 選取**搭配 Express.js 的 Node.js Web 應用程式（Web 應用程式）**作為要使用的入門範本套件。
5. 輸入應用程式的名稱，然後選取您要使用的資源群組（必要的話）。目前請不要新增服務。
6. 選取 **IBM DevOps，使用 Cloud Foundry** 選項來建立 DevOps 工具鏈。您可能需要設定 SSH 金鑰，才能完成此步驟。如果您設定 SSH 金鑰的通行詞組，則需要輸入此代碼。
  {: note}
7. 輸入唯一的主機名稱，例如 `abc-devhost`。這個主機名稱是您應用程式的路徑，例如 `abc-devhost.mybluemix.net`。

預設共用網域是 `mybluemix.net`，而 `appdomain.cloud` 是您可以使用的另一個網域選項。如需移轉至 `appdomain.cloud` 的相關資訊，請參閱[更新網域](/docs/apps/tutorials?topic=creating-apps-update-domain)。
{: tip}

建立應用程式及工具鏈需要幾秒鐘才能完成。

## 產生部署及雲端啟用資產
{: #byoc-cli}

如果您已有現有的程式碼庫，且想要使用 [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable)，為單一微服務或 Web 應用程式產生部署及雲端啟用資產，則可以使用此選項。請注意，這個指令目前為測試版，而且並未支援所有語言及/或應用程式結構。下列指示說明如何使用此功能與範例儲存庫搭配，但是對於您自己的程式碼庫，步驟大致相同。

1. 執行 `ibmcloud login` 來登入 {{site.data.keyword.cloud_notm}}，然後將組織與空間設為目標。
2. 在您選擇的目錄中執行下列指令，以複製 [Hello World 範例應用程式](https://github.com/IBM-Cloud/node-helloworld){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

3. 導覽至您複製範例應用程式的目錄，然後執行 [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable) 指令。
4. 目前選取要繼續而不確定變更（必要的話）。
5. 當系統提示您以偵測到的 Node 語言繼續時，選取要繼續。
6. 選取您要使用的資源群組（必要的話）。 
7. 選取建立鏈結至此 Git 儲存庫之新 {{site.data.keyword.cloud_notm}} 應用程式的選項。如需詳細資料，請參閱**重要注意事項**。
8. 目前請不要新增服務。
9. 等待幾秒讓作業完成。 
10. 作業完成之後，手動合併部署與儲存至應用程式目錄的雲端啟用檔案。使用 `git diff` 或類似的工具，合併標示為 `.merge` 的新檔案。

### 重要注意事項
 - 如果您已使用 {{site.data.keyword.cloud_notm}} 主控台建立 {{site.data.keyword.cloud_notm}} 應用程式，請在應用程式目錄中遵循前一節的步驟 2 - 5。對於步驟 6，您可以選取將本端程式碼連接至現有應用程式的選項。
 - 您也可以選擇執行 [`ibmcloud dev enable --no-create`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable)，產生部署和雲端啟用檔案，而不連接至 {{site.data.keyword.cloud_notm}} 應用程式。
 - 若要手動配置工具鏈和部署檔案，請遵循[本指導教學](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc-kube)。如果您嘗試針對多個相互關聯的 Web 應用程式或微服務配置 Continuous Delivery 工具鏈，這可能很有用。
 - 如果現有的程式碼庫尚不在 Git 儲存庫中，請在應用程式目錄中遵循前一節的步驟 2 - 5。對於步驟 6，您可以選取建立新 {{site.data.keyword.cloud_notm}} 應用程式，並將它部署至 DevOps 工具鏈（具有新建立之 GitLab 儲存庫）的選項。

## 建置應用程式並在本端執行它
{: #build-run-app-cli}

不論您用來建立應用程式的選項為何，您現在可以建置它並在本端執行。

1. 導覽至您的應用程式目錄，並確定 Docker 正在系統上執行。
2. 執行 [`ibmcloud dev build`](/docs/cli/idt?topic=cloud-cli-idt-cli#build) 指令，以建置應用程式。
3. 執行 [`ibmcloud dev run`](/docs/cli/idt?topic=cloud-cli-idt-cli#run) 指令，以開始在本端執行應用程式。
4. 在 `http://localhost:3000` 或類似的 URL 檢視在本端執行的應用程式。
5. 按 **Ctrl+C** 鍵可停止應用程式。

您也可以使用[複合指令](/docs/cli/idt?topic=cloud-cli-idt-cli#compound)，例如 `ibmcloud dev build/run`，循序地發出建置，然後執行。
{: tip}

## 新增服務及修改程式碼
{: #resources-app-cli}

既然您的應用程式可以在本端執行，便可以新增服務然後修改部分程式碼。 

1. 執行 [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit) 指令。
2. 遵循提示以建立新的資料相關服務，並將它連接至您的應用程式，例如 {{site.data.keyword.cloudant_short_notm}}。您可能需要為服務選取地區及方案。
3. 您可以選擇手動合併在建立服務時儲存到應用程式目錄的配置檔。或者，您可以目前先跳過此步驟。
4. 更新程式碼。例如，修改 `/public/index.html` 檔或類似檔案。如果您使用範例 `ExpressJS` 應用程式，可以變更 `Congratulations!` 字串，成為像是 `Hello World!` 的字串。
5. 儲存您已修改的任何檔案。

## 部署至 {{site.data.keyword.cloud_notm}}
{: #deploy-app-cli}

您可以用兩種方式之一來部署 {{site.data.keyword.cloud_notm}} 應用程式，視應用程式的配置方式而定。 

### 使用 DevOps 工具鏈來部署應用程式
如果您尚未建立應用程式的 DevOps 工具鏈，且您的應用程式尚不在 Git 儲存庫中，則可以執行 [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit) 指令。請遵循「配置 DevOps」的提示，然後部署至新的工具鏈（並建立新的 GitLab 儲存庫）。

您為應用程式建立 DevOps 工具鏈之後，部署新的建置就很簡單，只需要確定並推送程式碼至工具鏈中的儲存庫。 

1. 執行 `git add .` 指令。
2. 執行 `git commit -m "made changes"` 指令來確定變更。
3. 執行 `git push origin master` 指令來推送至主節點分支。
4. 從 {{site.data.keyword.cloud_notm}} 主控台，檢視應用程式的 DevOps 工具鏈。您可以從 {{site.data.keyword.cloud_notm}} 主控台中的**應用程式詳細資料**頁面檢視工具鏈詳細資料，方法是從應用程式目錄執行 [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) 指令。
5. 檢視工具鏈內的管線，以驗證已啟動新的建置。

### 手動部署應用程式

您可以使用 [`deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) 指令，以手動部署應用程式。例如，使用下列步驟，將應用程式手動部署至 Kubernetes。

1. 確定您已[建立 Kubernetes 叢集](https://{DomainName}/containers-kubernetes/overview){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。
2. 執行 [`ibmcloud dev deploy -t container`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) 指令。
3. 收到提示時，確認要使用的叢集和容器映像檔名稱。
4. 等待幾分鐘讓部署完成。

## 檢視應用程式
{: #view-app-cli}

1. 若要檢視在 {{site.data.keyword.cloud_notm}} 上執行之應用程式的 URL，請執行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 指令。
2. 若要從 {{site.data.keyword.cloud_notm}} 主控台檢視應用程式的認證、服務和工具鏈詳細資料，請執行 [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) 指令。 

**若要報告問題或提供意見，您可以使用 [{{site.data.keyword.cloud_notm}} Tech 的 Slack - #developer-tools 頻道](https://ibm-cloud-tech.slack.com){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。在[這裡](https://slack-invite-ibm-cloud-tech.mybluemix.net/){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 要求團隊存取。**
