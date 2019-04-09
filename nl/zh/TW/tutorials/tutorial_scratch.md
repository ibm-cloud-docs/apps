---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-11-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 從頭開始建立應用程式
{: #tutorial}

您可以使用服務及運行環境，來從頭開始建立自訂應用程式。您可以查看如何安裝所需的工具、在本端建置並執行應用程式，然後將它部署至雲端。
{: shortdesc}

## 步驟 1. 安裝工具
{: #install-tools}

安裝 [{{site.data.keyword.dev_cli_long}}](/docs/cli/index.html)。

Docker 會安裝為開發人員工具的一部分。Docker 必須在執行中，建置指令才能運作。您必須建立 Docker 帳戶、執行 Docker 應用程式，然後登入。

## 步驟 2. 從頭開始建立應用程式
{: #create-devex}

在 {{site.data.keyword.cloud}} 儀表板中建立自訂應用程式：

1. 從 [{{site.data.keyword.cloud}} 儀表板 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName})，選取**建立**來建立自訂應用程式。

  您也可以從 {{site.data.keyword.dev_console}} 的[入門範本套件 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/appservice/starter-kits/) 頁面中，選取**建立**來建立自訂應用程式。
  {: tip}

2. 輸入應用程式名稱。針對本指導教學，請使用 `CustomProject`。
3. 輸入唯一的主機名稱，例如 `abc-devhost`。這個主機名稱是您應用程式的路徑，也就是 `abc-devhost.mybluemix.net`。
4. 選取語言及架構。部分入門範本套件可能只提供一種語言。
5. 選取定價方案。您可以針對本指導教學使用免費選項。
6. 按一下**建立**。

## 步驟 3. 新增資源（選用）
{: #add-services}

您可以新增資源，藉由 Watson 的認知能力加強您的應用程式，也可以新增行動服務或安全服務。針對本指導教學，請新增工作區以便管理您的資料。

1. 從「應用程式服務」視窗中，按一下**新增資源**。
2. 選取您要的服務類型。例如，選取**資料** > **下一步** > **Cloudant** > **下一步**。
3. 選取定價方案。您可以針對本指導教學使用免費選項。
4. 按一下**建立**。

## 步驟 4. 使用 DevOps 工具鏈進行部署
{: #add-toolchain}

啟用工具鏈會為您的應用程式建立一個以團隊為基礎的開發環境。建立工具鏈時，應用程式服務會建立 Git 儲存庫，您可以在其中檢視原始碼、複製應用程式以及建立和管理問題。您也可以存取專用的 GitLab 環境，以及持續交付管線。它們針對您所選部署平台（Kubernetes 或 Cloud Foundry）經過自訂。

已針對部分應用程式啟用持續交付。您可以啟用持續交付，以透過 Delivery Pipeline 及 GitHub 自動建置、測試及部署。

1. 從「應用程式詳細資料」頁面中，按一下**部署至雲端**。
2. 選取部署方法。根據您所選方法的指示設定部署方法：
  * 部署至 Kubernetes 叢集。建立主機（稱為工作者節點）的叢集，以部署及管理高可用性的應用程式容器。您可以建立叢集或部署至現有的叢集。
  * 使用 Cloud Foundry 進行部署，如此便不需要管理基礎的基礎架構。
  * 部署至「虛擬伺服器實例」。

在前一個步驟中將應用程式部署至雲端時，會自動建立工具鏈。此工具鏈會為您的應用程式建立 Git 儲存庫，您可以在其中尋找程式碼。如需相關資訊，請參閱[建立工具鏈](/docs/services/ContinuousDelivery/toolchains_working.html)。

## 步驟 5. 在本端建置及執行應用程式
{: #build-run}

您也可以在本端建置應用程式以進行測試，然後再將它推送至雲端。

1. 從「應用程式服務」視窗中，按一下**下載程式碼**或**複製儲存庫**，以在本端使用程式碼。
2. 將應用程式匯入至整合開發環境。
3. 修改程式碼。
4. 新增個人存取記號來設定 [Git 鑑別](/docs/services/ContinuousDelivery/git_working.html#git_authentication)。
5. 登入 {{site.data.keyword.Bluemix}} 指令行介面。如果您的組織使用聯合登入，請使用 `-sso` 選項。

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. 設定您的組織及空間目標。

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. 取得認證。

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. 確定 Docker 在執行中，然後在本端開發容器中從目錄建置應用程式。

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. 在本端開發容器中執行應用程式。

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. 使用瀏覽器開啟 `http://localhost:3000`。您的埠號可能會根據選擇的運行環境而不同。

## 步驟 6. 部署應用程式
{: #deploy}

### 使用 DevOps 工具鏈進行部署

您有數種方式可以將應用程式部署至 {{site.data.keyword.cloud_notm}}，但 DevOps 工具鏈是部署正式作業應用程式的最佳方法。使用 DevOps 工具鏈，您可以輕鬆地自動部署到許多環境，並快速新增監視、記載和警示服務，以協助您在應用程式成長時進行管理。

使用適當配置的工具鏈，會自動開始建置、部署的循環，並且全都合併到您儲存庫的主要分支。從「{{site.data.keyword.cloud_notm}} 開發人員」儀表板建立的所有工具鏈，都會針對自動部署進行配置。

您也可以從 DevOps 工具鏈手動部署應用程式：

1. 從「應用程式詳細資料」視窗，按一下**檢視工具鏈**。
2. 按一下 **Delivery Pipeline**，您可以在其中啟動建置、管理部署，以及檢視日誌和歷程。

如需相關資訊，請參閱[建置並部署](/docs/services/ContinuousDelivery/pipeline_build_deploy.html)。

### 使用 {{site.data.keyword.dev_cli_short}} 進行部署

若要將應用程式部署至 Cloud Foundry，請輸入下列指令：
```
ibmcloud dev deploy
```
{: pre}

若要將應用程式部署至 Kubernetes 叢集，請輸入下列指令：
```
ibmcloud dev deploy --target <container>
```
{: pre}

## 步驟 7. 驗證應用程式在執行中
{: #verify}

部署應用程式之後，DevOps 管線或指令行會將您指向應用程式的 URL，例如 `abc-devhost.mybluemix.net`。請在瀏覽器中移至該 URL。
