---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# 雲端開發的建議階段
{: #development_process}

雲端應用程式開發人員會經歷開發程序中的四個基本階段：開始、撰寫程式碼、交付及管理。目標是快速產生可運作的應用程式，然後使用來自正式作業應用程式的回饋，以持續反覆進行撰寫程式碼或交付的循環，直到您的應用程式與使用者產生共鳴為止。
{: shortdesc}

![開發流程](images/dev_flow_overview.png "開發流程") 圖 1. 開發程序的階段

在某些情況下，「執行」會列為個別的階段，但在這裡它與「交付」和「管理」階段結合。

讓我們更深入瞭解在開發流程中使用 {{site.data.keyword.cloud}} 的最佳方式。

## 開始使用
{: #get_started}

請從 {{site.data.keyword.cloud_notm}}「開發人員」儀表板建置您的應用程式，您可以在這裡選取與使用案例相關的入門範本套件，並選擇程式設計語言。{{site.data.keyword.cloud_notm}} 會使用入門範本套件中的指示來自動建立所需的資源，以及建立語言特有且與運行環境無關的應用程式，以作為正式作業應用程式的基礎。若要完成開始使用階段，請從「開發人員」儀表板中按一下**部署至雲端**。按一下即可建立 DevOps 工具鏈，並具有完整的程式碼儲存庫，當中移入您的應用程式原始碼及部署管線。

![開始使用](images/dev_get_started.png "開始使用") 圖 2. 開始使用流程

當您使用**部署至雲端**按鈕來設定 DevOps 工具鏈時，請選取您的運行環境平台，例如 Kubernetes 或 Cloud Foundry。從 {{site.data.keyword.cloud_notm}} 產生的入門範本套件應用程式與運行環境無關，且不需要進行修改。
{: tip}

## 在本端開發
{: #develop_locally}

建立入門範本套件應用程式及工具鏈之後，即可開始在本端開發。將程式碼從儲存庫複製到本端工作站，並匯入至 IDE。使用 {{site.data.keyword.dev_cli_long}} 可在您的本端機器上建置、執行及測試雲端應用程式。{{site.data.keyword.dev_cli_notm}} 會為您建立及管理本端容器。當您準備好看到應用程式正在雲端上執行時，請推送至您的雲端儲存庫，並合併所做的變更。

![在本端開發](images/dev_code_locally.png "在本端開發") 圖 3. 在本端開發流程

{{site.data.keyword.dev_cli_notm}} 的基本函數是 `ibmcloud dev build` 和 `ibmcloud dev run`，但 CLI 提供了更多函數。如需詳細資料，請參閱 [{{site.data.keyword.dev_cli_notm}}](/docs/cli/index.html)。
{: tip}

## 在 {{site.data.keyword.cloud_notm}} 中交付和管理
{: #deliver_and_manage}

將變更合併至雲端儲存庫，會在您先前建立的 DevOps 工具鏈中開始一個建置與部署的循環。您的應用程式會在幾分鐘之後在雲端執行。

若要檢查 DevOps 管線的狀態，請使用 Delivery Pipeline 儀表板。若要檢查應用程式的整體狀態，請參閱帳戶的 {{site.data.keyword.cloud_notm}} 儀表板。
{: tip}

開始使用體驗所產生的工具鏈具有您進行協同作業、以團隊為基礎的持續交付時所需要的基本元件。不過，{{site.data.keyword.cloud_notm}} 提供一組廣泛的 DevOps 服務，您可以將它們新增至工具鏈中，以加強交付、監視、記載、警示。

![交付和管理](images/dev_deliver_and_manage.png "交付和管理") 圖 4. 交付和管理流程

進一步瞭解 [{{site.data.keyword.cloud_notm}} 上的持續開發](/docs/services/ContinuousDelivery/index.html#cd_getting_started)。

## 組合在一起

![處理程序詳細資料](images/dev_process_detail.png "處理程序詳細資料") 圖 5. 完整的開發處理程序
