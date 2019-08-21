---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-18"

keywords: apps, deploy, deploying apps, toolchain, cli, cloud, devops, deployment, git, push

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# 部署應用程式
{: #deploying-apps}

您可以使用 DevOps 工具鏈，將應用程式部署至 {{site.data.keyword.cloud}}。使用 DevOps 工具鏈，您可以自動部署到許多環境，並快速新增監視、記載、見解和警示服務，以協助您在應用程式成長時進行管理。您可以使用 {{site.data.keyword.cloud_notm}} Web 主控台或指令行介面 (CLI)，來配置持續交付及部署應用程式。
{: shortdesc}

DevOps 工具鏈為您的應用程式提供以團隊為基礎的開發環境。建立工具鏈時，應用程式服務會建立 Git 儲存庫，您可以在其中檢視原始碼、複製應用程式以及建立和管理問題。您也可以存取專用的 GitLab 環境，以及持續交付管線。它們是根據您所選取的部署目標（[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虛擬伺服器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial)）進行自訂。

## 使用 {{site.data.keyword.cloud_notm}} 主控台
{: deploy-console}

{{site.data.keyword.cloud_notm}} 提供 Web 主控台，您可以在其中使用 DevOps 工具鏈，來配置持續交付及部署應用程式。

### 開始之前
{: deploy-console-before}

開始之前，請使用 [{{site.data.keyword.cloud_notm}} 儀表板](https://{DomainName}){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")，來[建立應用程式](/docs/apps?topic=creating-apps-getting-started)及[新增服務](/docs/apps?topic=creating-apps-getting-started#resources-getting-started)。

### 自動部署應用程式
{: deploy-console-auto}

從 {{site.data.keyword.cloud_notm}} 開發人員儀表板建立的所有工具鏈，都會針對自動部署進行配置。
{: note}

1. 在**應用程式詳細資料**頁面上，按一下**配置持續交付**。
2. 選取一個部署目標。根據您所選目標的指示設定部署目標：
  * **部署至 IBM Kubernetes Service**。此選項會建立主機（稱為工作者節點）的叢集，以部署及管理高可用性的應用程式容器。您可以建立叢集或部署至現有的叢集。如需相關資訊，請參閱[將應用程式部署至 Kubernetes 叢集](/docs/containers?topic=containers-app)。
  * **部署至 Cloud Foundry**。此選項會部署雲端原生應用程式，而您不需要管理基本基礎架構。如果您的帳戶可以存取 {{site.data.keyword.cfee_full_notm}}，則可以選取**公用雲端**或**企業環境**的部署者類型，用來建立及管理用於管理專供您企業使用的 Cloud Foundry 應用程式的隔離環境。如需相關資訊，請參閱[將應用程式部署至 Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps) 及[將應用程式部署至 {{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)。
  * **部署至虛擬伺服器**。此選項會佈建虛擬伺服器實例、載入包含您應用程式的映像檔、建立 DevOps 工具鏈，以及為您起始第一個部署週期。如需相關資訊，請參閱[將應用程式部署至虛擬伺服器](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server)。

    部分入門範本套件可以進行 VSI 部署。若要使用此特性，請移至 [{{site.data.keyword.cloud_notm}} 儀表板](https://{DomainName})，然後在**應用程式**磚按一下**建立應用程式**。
    {: note}

### 手動部署應用程式
{: deploy-console-manual}

使用適當配置的工具鏈，建置-部署的循環會自動開始，並且全都合併到您儲存庫的主要分支。 

您也可以從 DevOps 工具鏈手動部署應用程式：

1. 在**應用程式詳細資料**頁面上，按一下**檢視工具鏈**。
2. 按一下 **Delivery Pipeline**，您可以在其中啟動建置、管理部署，以及檢視日誌和歷程。

即會自動針對部分應用程式啟用持續交付。您可以啟用持續交付，以透過 Delivery Pipeline 及 GitHub 自動建置、測試及部署。

如需相關資訊，請參閱：
* [建置及部署](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)
* [建立工具鏈](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)

## 使用 {{site.data.keyword.dev_cli_short}} CLI
{: #deploy-cli}

{{site.data.keyword.cloud_notm}} 提供強健的 CLI 及外掛程式，來協助簡化開發人員的工作流程。您可以用兩種方式之一來部署 {{site.data.keyword.cloud_notm}} 應用程式，視應用程式的配置方式而定。

### 開始之前
{: #deploy-cli-before}

開始之前，[請下載並安裝 {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started)。

Cygwin 不支援 CLI。請在非 Cygwin 指令行視窗的視窗中使用此工具。
{: important}

  1. 將您應用程式的程式碼下載至新的目錄，以設定開發環境。

  2. 切換至您程式碼所在的目錄。

  3.  更新您的應用程式碼。例如，若您使用 {{site.data.keyword.cloud_notm}} 範例應用程式，而且您的應用程式包含 `src/main/webapp/index.html` 檔，則可以修改它，並編輯 `Thanks for creating ...` 這行。請先確定應用程式在本端執行，再將它部署至 {{site.data.keyword.cloud_notm}}。

    也請檢閱 `README.md` 檔，其中包含建置指示這類詳細資料。

    如果您的應用程式是 Liberty 應用程式，則必須先建置它，再重新部署。
    {: note}

  4. 使用您的 IBM ID 登入 {{site.data.keyword.cloud_notm}} CLI。如果您有多個帳戶，則系統會提示您選取要使用的帳戶。如果您未使用 `-r` 旗標來指定地區，則必須同時選取地區。
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    如果您的認證遭到拒絕，您可能是使用聯合 ID。若要使用聯合 ID 來登入，請使用 `--sso` 旗標。如需相關資訊，請參閱[使用聯合 ID 登入](/docs/iam/federated_id?topic=iam-federated_id#federated_id)。
    {: tip}

### 自動部署應用程式
{: #deploy-cli-auto}

如果您未建立應用程式的 DevOps 工具鏈，且您的應用程式尚不在 Git 儲存庫中，則可以執行 [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit) 指令。請遵循「配置 DevOps」的提示，然後部署至新的工具鏈（並建立新的 GitLab 儲存庫）。

您為應用程式建立 DevOps 工具鏈之後，部署新的建置就很簡單，只需要確定並推送程式碼至工具鏈中的儲存庫。 

1. 準備確定變更。
    ```
    git add .
    ```
2. 確定變更並顯示簡短訊息。
    ```
    git commit -m "made changes"
    ```
3. 將主要分支上的確定推送至遠端儲存庫。
    ```
    git push origin master
    ```
4. 從 {{site.data.keyword.cloud_notm}} 主控台，檢視應用程式的 DevOps 工具鏈。您可以從 {{site.data.keyword.cloud_notm}} 主控台中的**應用程式詳細資料**頁面檢視工具鏈詳細資料，方法是從應用程式目錄執行 [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) 指令。
5. 檢視工具鏈內的管線，以驗證已啟動新的建置。

### 手動部署應用程式
{: #deploy-cli-manual}

您可以使用 [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) 指令，將應用程式手動部署至 {{site.data.keyword.cloud_notm}}。

  ```
ibmcloud dev deploy
```
  {: codeblock}

### 相關資訊
{: #deploy-cli-related}

如需使用 CLI 將應用程式部署至 {{site.data.keyword.cloud_notm}} 的相關資訊，請參閱：

* [Deploying to {{site.data.keyword.cloud_notm}} environments with {{site.data.keyword.dev_cli_short}} CLI](https://www.ibm.com/cloud/blog/deploying-to-ibm-cloud-environments-with-ibm-cloud-developer-tools-cli){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")
