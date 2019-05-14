---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-30"

keywords: apps, code pattern, DevOps, toolchain, service credentials, create app code pattern, app pattern

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 使用程式碼型樣來建立應用程式
{: #tutorial-codepattern}

您可以使用程式碼型樣來快速建立應用程式，並將它部署至 {{site.data.keyword.cloud}}。您可以在 GitHub 檢視程式碼，或在 {{site.data.keyword.cloud_notm}} 建立並建置應用程式，在這裡您可以使用 DevOps 工具鏈自動部署應用程式。
{: shortdesc}

## 步驟 1. 建立應用程式
{: #create-codepattern}

1. 移至 [IBM Developer ](https://developer.ibm.com/patterns/){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")，然後選取您要的程式碼型樣。例如，您可以選取[建置 MEAN Web 應用程式 ](https://developer.ibm.com/patterns/build-a-mean-web-app/){: new_window} ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示") 程式碼型樣。

2. 閱讀程式碼型樣的說明，以及檢視 GitHub 儲存庫和 `README.md` 檔案。若要檢視儲存庫，請按一下**取得程式碼**，以開啟程式碼型樣的 GitHub 儲存庫。

3. 使用下列任一個選項，開始建立應用程式。任一選項都會針對程式碼型樣開啟**建立應用程式**頁面。
    * 在程式碼型樣的頁面上，按一下 {{site.data.keyword.cloud_notm}} 上用於建置應用程式的鏈結。 
    * 在 GitHub 儲存庫的 `README.md` 檔案中，按一下用於使用入門範本套件建立應用程式的鏈結。 

4. 在**建立應用程式**頁面上，為您的應用程式命名、選取資源群組、選擇性地提供標記，然後按一下**建立**。如需標記的相關資訊，請參閱[使用標記](/docs/resources?topic=resources-tag)。

  若要回到程式碼型樣，請按一下**檢視程式碼型樣**。請檢查儲存庫中的 `README.md` 檔案，以找出您是否需要採取更多動作，以讓應用程式啟動並執行。
  {: tip}

## 步驟 2. 新增服務
{: #resources-codepattern}

您可以新增服務，藉由 Watson 的認知能力加強您的應用程式，也可以新增行動服務或安全服務。此處理程序會建立服務實例、建立資源金鑰（認證），並將它連結至應用程式。針對本指導教學，請新增工作區以便管理您的資料。

1. 在**應用程式詳細資料**頁面上，按一下**新增服務**。
2. 選取您要的服務類型。 
3. 選取定價方案。可以使用精簡選項。
4. 按一下**建立**。

## 步驟 3. 將服務認證複製至環境

將服務新增至應用程式之後，或者，如果應用程式需要任何服務，請注意，該服務的認證會顯示在**認證**方框中。您必須手動將認證複製至部署環境。

如需將認證複製至環境的相關資訊，請參閱[認證概觀](/docs/apps?topic=creating-apps-credentials_overview#credentials_overview)。

## 步驟 4. 部署至 {{site.data.keyword.cloud_notm}}
{: #deploy-codepattern}

您有數種方式可以將應用程式部署至 {{site.data.keyword.cloud_notm}}，但 DevOps 工具鏈是部署正式作業應用程式的最佳方法。使用 DevOps 工具鏈，您可以輕鬆地自動部署到許多環境，並快速新增監視、記載和警示服務，以協助您在應用程式成長時進行管理。

啟用工具鏈會為您的應用程式建立一個以團隊為基礎的開發環境。建立工具鏈時，應用程式服務會建立 Git 儲存庫，您可以在其中檢視原始碼、複製應用程式以及建立和管理問題。您也可以存取專用的 GitLab 環境，以及持續交付管線。它們是根據您所選取的部署目標（[Kubernetes](/docs/containers?topic=containers-getting-started)、[Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)、[{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) 或[虛擬伺服器 (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers)）進行自訂。

1. 在**應用程式詳細資料**頁面上，按一下**配置持續交付**。
2. 選取部署目標，選取按一下**建立**。{{site.data.keyword.cloud_notm}} 會自動建立開放式工具鏈，此工具鏈會完整地具備 Git 儲存庫及持續交付管線。
3. 開啟新工具鏈的管線階段，以檢視建置及部署處理程序，讓您可以在數分鐘內檢視新的應用程式。

如需部署應用程式的相關資訊，請參閱[部署應用程式](/docs/apps?topic=creating-apps-deploying-apps)。

如需部署目標、建置及管線的相關資訊，請參閱[建置及部署](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)。
