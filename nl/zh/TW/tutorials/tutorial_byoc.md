---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, byoc, code repository, continuous delivery, cli, deploy

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# 從您自己的程式碼儲存庫建立應用程式
{: #tutorial-byoc}

您可以使用現有的應用程式儲存庫，在 {{site.data.keyword.cloud}} 中建立應用程式。只需在建立應用程式期間提供儲存庫的 Web 鏈結、繼續新增資源，然後將 DevOps 工具鏈連接至應用程式以進行部署。
{: shortdesc}

## 開始之前
{: #prereqs-byoc}

請確定已備妥下列必要條件：

 * 安裝 [{{site.data.keyword.dev_cli_long}} 指令行介面 (CLI)](/docs/cli?topic=cloud-cli-ibmcloud-cli)。
 * 參閱[構成良好應用程式的要點？](/docs/apps?topic=creating-apps-best-practice)，以取得建立應用程式的最佳作法。
 * 您必須具有來自下列任何提供者的 Git 原始碼儲存庫：GitHub、GitHub Enterprise、Git Lab、BitBucket 或 Rational。
 * 如果您計劃將應用程式部署至 [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about)，則必須[準備 {{site.data.keyword.cloud_notm}} 帳戶](/docs/cloud-foundry?topic=cloud-foundry-prepare)。

## 步驟 1. 使用現有的儲存庫建立應用程式
{: #create-byoc}

若要建立應用程式並將其與原始檔儲存庫連接，請完成下列步驟：

1. 從[儀表板 ](https://{DomainName}){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")，按一下**應用程式**磚中的**建立應用程式**。
2. 為您的應用程式命名、選取資源群組，並選擇性地提供標記來分類應用程式。如需相關資訊，請參閱[使用標籤](/docs/resources?topic=resources-tag)。
3. 選取**自帶程式碼**，並提供 Git 儲存庫的 URL。您的應用程式及 Docker 映像檔必須位於相同的儲存庫中。
4. 按一下**建立**。即會顯示**應用程式詳細資料**頁面。
5. 選用。將[服務新增](/docs/apps?topic=creating-apps-add-resource)至應用程式。
6. 選用。如果您已在建立應用程式時提供標記，則可以按一下所顯示標記旁邊的**編輯**圖示 ![「編輯」圖示方法是](../../icons/edit-tagging.svg)以進行編輯。
7. 選用。按一下**檢視儲存庫**來檢視您的儲存庫。

## 步驟 2. 部署應用程式
{: #toolchain-byoc}

建立應用程式、工具鏈與儲存庫之間的鏈結，是邁向組織產品資產的一步。它也有助於用 DevOps 工作流程、執行中的應用程式實例，以及跨所有部署目標的相依服務，聚集您原始碼儲存庫的視圖。如需相關資訊，請參閱[建立工具鏈](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)。

您可以使用 {{site.data.keyword.cloud_notm}} 主控台或 CLI，來為應用程式配置持續交付。

### 使用主控台
{: #console-byoc-toolchain}

  1. 在**應用程式詳細資料**頁面上，按一下**配置持續交付**，將應用程式連接至 DevOps 工具鏈。即會顯示**部署應用程式**頁面。
  2. 如果您沒有現有的工具鏈，請按一下**建立工具鏈**。建立工具鏈之後，請使用瀏覽途徑回到**應用程式詳細資料**頁面，這表示持續交付已配置。
  3. 如果您具有現有的工具鏈，請選取它，然後按一下**啟用部署**。即會顯示**應用程式詳細資料**頁面，這表示持續交付已配置。

### 使用 CLI

您可以使用 `ibmcloud dev enable` 指令來產生 DevOps 工具鏈範本，然後您可以將其移入儲存庫，作為 DevOps 工具鏈要建立的指示集。 

  1. 在**應用程式詳細資料**頁面上，按一下**檢視儲存庫**，以在本端使用程式碼。
  2. 請執行下列指令：
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

如需相關資訊，請參閱[使用 CLI 建立及部署應用程式](/docs/apps?topic=creating-apps-create-deploy-app-cli)。

