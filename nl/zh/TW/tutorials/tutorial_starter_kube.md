---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, starter kit, Kubernetes, cluster

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 將入門範本套件應用程式部署至 Kubernetes 叢集
{: #tutorial-starterkit-kube}

瞭解如何使用空白的入門範本套件和 Kubernetes 工具鏈在 {{site.data.keyword.cloud}} 中建立應用程式，並持續將應用程式遞送至 Kubernetes 叢集中的安全容器。您可以配置 Continuous Integration DevOps 管線，以自動建置程式碼變更，並將這些變更傳播到 Kubernetes 叢集裡的應用程式。如果您已有管線，則可以將它連接至應用程式。
{: shortdesc}

{{site.data.keyword.cloud_notm}} 提供入門範本套件，可協助您建置在 Kubernetes 上執行之應用程式的基礎。當您使用入門範本套件時，可以輕鬆地遵循雲端原生程式設計模型，該模型會使用 {{site.data.keyword.cloud_notm}} 最佳作法來開發應用程式。入門範本套件產生的應用程式會遵循雲端原生程式設計模型，而且它們包含每種程式設計語言中的測試案例、性能檢查及度量值。您也可以佈建雲端服務，然後在產生的應用程式中加以起始設定。

本指導教學使用 Kubernetes 部署目標。在本指導教學中，我們是從基本入門範本套件建立應用程式，方法為使用 Java + Spring、將 Cloudant 服務實例新增至其中，然後使用 IBM Kubernetes Service 將其部署至 {{site.data.keyword.cloud_notm}}。

首先，請參閱下列入門範本套件流程圖及其對應的概觀步驟。

![入門範本套件流程圖](../images/starterkit-flow.png) 

## 開始之前
{: #prereqs-starterkit-kube}

* 使用[入門範本套件](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit)來建立 **Java + Spring** 應用程式。
* 安裝 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli)。
* 設定 [Docker ](https://www.docker.com/get-started){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")。

## 將服務新增至應用程式
{: #resources-starterkit-kube}

將 {{site.data.keyword.cloud_notm}} 服務新增至應用程式。下列步驟會佈建 Cloudant 實例、建立資源金鑰 (credentials)，並將它連結至應用程式。

1. 在**應用程式詳細資料**頁面上，按一下**新增服務**。
2. 選取**資料**，然後按**下一步**。
3. 選取 **Cloudant**，然後按**下一步**。
4. 在**新增 Cloudant** 頁面上，選取地區（美國南部）、資源群組 (default)，以及定價方案（精簡 - 一個免費實例）。
5. 按一下**建立**。即會顯示**應用程式詳細資料**頁面，並佈建 Cloudant 實例，然後將其連結至應用程式。請注意，Cloudant 資源金鑰 (credentials) 會新增至**認證**欄位。
6. 選用。如果您想要在新增服務之後快速查看應用程式碼，請按一下**下載程式碼**。您的程式碼會下載為包含完整應用程式碼結構的 `.zip` 檔案。您可以使用 {{site.data.keyword.dev_cli_notm}} 輕鬆地解壓縮檔案並在本端執行程式碼，或將其新增至程式碼管理儲存庫。

## 使用 DevOps 工具鏈來部署應用程式
{: #deploy-starterkit-kube}

將 DevOps 工具鏈連接至應用程式，並將它配置為部署至 {{site.data.keyword.cloud_notm}} Kubernetes 服務中管理的 Kubernetes 叢集。

1. 在**應用程式詳細資料**頁面上，按一下**配置持續交付**。
2. 在**選取部署目標**頁面上，選取**部署至 IBM Kubernetes Service**。
3. 選取地區和叢集。如果您沒有 Kubernetes 叢集，請按一下**建立叢集**。
  * 在**建立新叢集**頁面上，選取位置、叢集類型（免費）、輸入叢集名稱，然後按一下**建立叢集**。
  * 必要的話，請遵循畫面上的指示，來取得叢集的存取權。
  * 等到叢集指出**備妥**，即可建立工具鏈。使用**美國南部**地區，您可以佈建一個免費叢集。
  * 回到**選取部署目標**頁面。
4. 按**下一步**。即會顯示**配置工具鏈**頁面。
5. 在**配置工具鏈**頁面上，輸入工具鏈名稱、選取地區、選取資源群組，然後按一下**建立**。即會顯示**應用程式詳細資料**頁面，以及有關工具鏈的部署資訊。

## 檢視儲存庫
{: #view-repo-starterkit-kube}

1. 在**應用程式詳細資料**頁面上，按一下**檢視儲存庫**。即會顯示入門範本套件產生的 Git 儲存庫。
2. 選用。遵循畫面上的指示，在桌面上配置 SSH。
3. 選用。遵循畫面上的指示，在帳戶上建立個人存取記號。

## 檢視工具鏈工具、日誌及歷程
{: #view-logs-starterkit-kube}

1. 部署階段完成時，即會顯示**應用程式詳細資料**頁面，以及有關工具鏈的部署資訊。
2. 按一下**檢視工具鏈**來存取工具鏈。即會顯示工具鏈頁面的**概觀**標籤，其中顯示工具鏈隨附的工具。此範例包含在建立工具鏈時，已在入門範本套件預先選取的下列工具：
  * 追蹤專案更新及變更用的問題追蹤程式。
  * 包含應用程式原始碼的 Git 儲存庫。
  * Eclipse Orion 實例，這是可編輯應用程式的 Web 型 IDE。
  * 由可自訂的建置並部署階段組成的 Delivery Pipeline。
	 * 「建置」階段會將應用程式容器化。更明確地說，建置階段會：
	   * 複製 GitLab 儲存庫。
	   * 建置應用程式。
	   * 建置 Docker 映像檔。
	   * 將映像檔發佈至專用 Container Registry。
	 * 「部署」階段會從 Container Registry 擷取容器映像檔，然後將其部署至 Kubernetes 叢集。
3. 按一下 **Delivery Pipeline**。即會顯示管線階段。
4. 在**部署階段**磚中，按一下**檢視日誌和歷程**。

## 驗證應用程式正在執行
{: #verify-starterkit-kube}

部署應用程式之後，Delivery Pipeline 或指令行會將您指向應用程式的 URL。

1. 從 DevOps 工具鏈中，按一下 **Delivery Pipeline**，然後選取**部署階段**。
2. 按一下**檢視日誌和歷程**。
3. 在日誌檔中，尋找應用程式 URL：

    在日誌檔結尾，搜尋 `View the application health at: http://<ipaddress>:<port>/health`。

4. 在瀏覽器中移至 URL。如果應用程式正在執行，則會顯示包含 `Congratulations` 或 `{"status":"UP"}` 的訊息。

如果您要使用指令行，請執行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 指令來檢視應用程式的 URL。然後，在瀏覽器中移至 URL。

## 後續步驟
{: #next-steps-startkit-kube notoc}

* 如果您在部署時遇到錯誤，請檢查疑難排解主題以找出[超出儲存空間配額](/docs/apps?topic=creating-apps-managingapps#exceed_quota)這類已知問題，或了解如何[存取 Kubernetes 日誌](/docs/apps?topic=creating-apps-managingapps#access_kube_logs)來尋找錯誤。

* 在程式碼中存取服務配置：
	- 您可以使用 _@Value_ 註釋，或使用 Spring 架構環境類別 _getProperty()_ 方法。如需相關資訊，請參閱[存取認證](/docs/java-spring?topic=java-spring-configuration#accessing-credentials)。

* 將新認證新增至 Kubernetes 環境：
	- 當您在建立 DevOps 工具鏈之後將另一個服務新增至應用程式時，那些服務認證並不會自動更新至已部署的應用程式及 GitLab 儲存庫。您必須[手動新增認證](/docs/apps?topic=creating-apps-add-credentials-kube)至部署環境。
