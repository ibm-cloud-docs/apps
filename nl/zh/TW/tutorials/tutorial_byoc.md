---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-30"

keywords: byoc, code repository, continuous delivery, cli, deploy, create app custom repo, custom repo, existing repo, custom code

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

如果現有儲存庫中有一個應用程式，您可以使用空白的入門範本套件，在 {{site.data.keyword.cloud_notm}} 中建立應用程式記錄，並將應用程式連接至來源儲存庫及您的 DevOps 工具鏈。
{: shortdesc}

您可以從 {{site.data.keyword.cloud_notm}} 儀表板或從任何空白的入門範本套件開始。在您命名應用程式並選取資源群組之後，請選取**自帶程式碼**起點，提供包含程式碼的 Git 儲存庫 URL，然後按一下**建立**。

您可以連接現有的 DevOps 工具鏈或建立一個，並持續將應用程式遞送至您所選擇的部署目標，例如，Kubernetes 或 Cloud Foundry。

## 開始之前
{: #prereqs-byoc}

請確定已備妥下列必要條件：

 * 安裝 [{{site.data.keyword.dev_cli_long}} 指令行介面 (CLI)](/docs/cli?topic=cloud-cli-ibmcloud-cli)。
 * 參閱[構成良好應用程式的要點？](/docs/apps?topic=creating-apps-best-practice)，以取得建立應用程式的最佳作法。
 * 您必須具有來自下列任何提供者的 Git 原始碼儲存庫：GitHub、GitHub Enterprise、Git Lab、BitBucket 或 Rational。
 * 如果您計劃將應用程式部署至 [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about)，則必須[準備 {{site.data.keyword.cloud_notm}} 帳戶](/docs/cloud-foundry?topic=cloud-foundry-prepare)。

## 使用現有的儲存庫建立應用程式
{: #create-byoc}

若要建立應用程式並將其與原始檔儲存庫連接，請完成下列步驟：

1. 從 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")，按一下**應用程式**磚中的**建立應用程式**。
2. 為您的應用程式命名、選取資源群組，並選擇性地提供標記來分類應用程式。如需相關資訊，請參閱[使用標籤](/docs/resources?topic=resources-tag)。
3. 選取**自帶程式碼**，並提供 Git 儲存庫的 URL。您的應用程式及 Docker 映像檔必須位於相同的儲存庫中。
4. 按一下**建立**。即會顯示**應用程式詳細資料**頁面。
5. 選用。將[服務新增](/docs/apps?topic=creating-apps-add-resource)至應用程式。
6. 選用。按一下**新增標籤**，可將標籤新增至此應用程式，或者按一下所顯示標籤旁的**編輯**圖示 ![「編輯」圖示](../../icons/edit-tagging.svg) 來編輯標籤。
7. 選用。按一下**檢視儲存庫**來檢視您的儲存庫。

## 部署應用程式
{: #toolchain-byoc}

建立應用程式、工具鏈與儲存庫之間的鏈結，是邁向組織產品資產的一步。它也有助於用 DevOps 工作流程、執行中的應用程式實例，以及跨所有部署目標的相依服務，聚集您原始碼儲存庫的視圖。如需相關資訊，請參閱[建立工具鏈](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)。

您可以使用 {{site.data.keyword.cloud_notm}} 主控台或 CLI，來為應用程式配置持續交付。

### 使用主控台
{: #console-byoc-toolchain}

#### 如果已經有想要連接至應用程式的 DevOps 工具鏈，請完成下列步驟：

1. 在**應用程式詳細資料**頁面上，按一下**配置持續交付**。即會顯示**部署應用程式**頁面。
2. 選取您要連接至應用程式的工具鏈，然後按一下**啟用部署**。即會顯示**應用程式詳細資料**頁面，這表示持續交付已配置。

#### 如果您沒有此應用程式的 DevOps 工具鏈，請完成下列步驟：

1. 在**應用程式詳細資料**頁面上，按一下**建立 DevOps 工具鏈**。即會顯示**建立工具鏈**頁面。
2. [建立工具鏈](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)。
3. 在瀏覽器視窗中使用瀏覽途徑可回到**應用程式詳細資料**頁面，這表示持續交付已配置。

### 使用 CLI
{: #cli-byoc-toolchain}

您可以使用 `ibmcloud dev enable` 指令來產生 DevOps 工具鏈範本，然後您可以將其移入儲存庫，作為 DevOps 工具鏈要建立的指示集。 

  1. 在**應用程式詳細資料**頁面上，按一下**檢視儲存庫**，以在本端使用程式碼。
  2. 請執行下列指令：
    
    ```
    ibmcloud dev enable
```
   {: codeblock}

如需部署應用程式的相關資訊，請參閱[部署應用程式](/docs/apps?topic=creating-apps-deploying-apps)。

## 驗證應用程式正在執行
{: #verify-byoc-app}

Delivery Pipeline 或指令行會將您指向應用程式的 URL。

1. 從 DevOps 工具鏈中，按一下 **Delivery Pipeline**，然後選取**部署階段**。
2. 按一下**檢視日誌和歷程**。
3. 在日誌檔中，尋找應用程式 URL。在日誌檔結尾，搜尋單字 `urls` 或 `view`。例如，您可能會看到日誌檔中有一行類似於 `urls: my-app-devhost.mybluemix.net`，或 `View the application health at: http://<ipaddress>:<port>/health`。
4. 在瀏覽器中移至 URL。如果應用程式正在執行，則會顯示包含 `Congratulations` 或 `{"status":"UP"}` 的訊息。

如果您使用指令行，請執行 [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 指令，在預設瀏覽器中開啟已手動部署之應用程式的頁面。
