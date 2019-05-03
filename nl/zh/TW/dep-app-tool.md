---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-02"

keywords: apps, deploy, deploying apps, toolchains, cli, cloud

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

您可以使用 DevOps 工具鏈或指令行介面 (CLI) 來部署應用程式。DevOps 工具鏈是一組整合的工具。CLI 是部署應用程式和服務實例的簡單方法。
{: shortdesc}

## 使用 DevOps 工具鏈部署應用程式
{: #toolchain-deploy-apps}

開放式工具鏈可用於 {{site.data.keyword.Bluemix}} 上的「公用」和「專用」環境。使用適當配置的工具鏈，部署應用程式便很輕鬆。會自動開始建置並部署的循環，並且全都合併到您儲存庫的主要分支。

您可以使用下列方式來建立工具鏈：
* 從應用程式建立工具鏈。如需相關資訊，請參閱[部署應用程式](/docs/apps?topic=creating-apps-tutorial-scratch#deploy-scratch)。
* 使用範本來建立工具鏈。如需相關資訊，請參閱[建立工具鏈](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)。

## 使用 CLI 來部署應用程式
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}} 提供強健的 CLI，以及與 CLI 整合的外掛程式和開發人員工具延伸規格。

開始之前，[請下載並安裝 {{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-ibmcloud-cli)。

Cygwin 不支援 CLI。請在非 Cygwin 指令行視窗的視窗中使用此工具。
{: important}

  1. 將您應用程式的程式碼下載至新的目錄，以設定開發環境。

  2. 切換至您程式碼所在的目錄。

  3.  更新您的應用程式碼。例如，若您使用 {{site.data.keyword.cloud_notm}} 範例應用程式，而且您的應用程式包含 `src/main/webapp/index.html` 檔，則可以修改它，並編輯 `Thanks for creating ...` 這行。請先確定應用程式在本端執行，再將它部署至 {{site.data.keyword.cloud_notm}}。

    記下 `manifest.yml` 檔案。將應用程式部署至 {{site.data.keyword.cloud_notm}} 時，此檔案用來決定您應用程式的 URL、記憶體配置、實例數以及其他重要參數。

    也請檢閱 `README.md` 檔，其中包含建置指示這類詳細資料。

    如果您的應用程式是 Liberty 應用程式，則必須先建置它，再重新部署。
  {: note}

  4. 使用您的 IBM ID 登入 {{site.data.keyword.cloud_notm}} CLI。如果您有多個帳戶，則系統會提示您選取要使用的帳戶。如果您未使用 `-r` 旗標來指定地區，則必須同時選擇地區。
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    如果您的認證遭到拒絕，您可能是使用聯合 ID。若要使用聯合 ID 來登入，請使用 `--sso` 旗標。如需相關資訊，請參閱[使用聯合 ID 登入](/docs/iam/federated_id?topic=iam-federated_id#federated_id)。
    {: tip}

  5. 從您的新目錄，使用 [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) 指令以將應用程式部署至 {{site.data.keyword.cloud_notm}}。
    ```
    ibmcloud dev deploy <APP_NAME>
    ```
    {: codeblock}

  6. 執行 [`ibmcloud devview`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) 指令來檢視您應用程式的 URL，以存取您的應用程式。然後，在瀏覽器中移至 URL。
