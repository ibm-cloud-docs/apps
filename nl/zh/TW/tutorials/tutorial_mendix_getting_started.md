---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-06"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# 使用 Mendix 建立應用程式
{: #create-mendix}

Mendix 是低程式碼開發環境及工具集，它能協助您更快速地遞送多裝置應用程式、使用更少開發資源，並且在 {{site.data.keyword.cloud}} 上執行。藉由選取 Mendix 低程式碼入門範本套件，您會被引導以在 Mendix Platform 上設定帳戶、啟動專案，以及在 Cloud Foundry 或 Kubernetes 叢集裡選取部署環境。
{: shortdesc}

## 選取入門範本套件
{: #starterkit-mendix}

1. 從「[{{site.data.keyword.cloud_notm}} 應用程式服務」儀表板 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/appservice/dashboard){: new_window} 中，按一下**開始使用**。
2. 從下列其中一個種類選取 Mendix 低程式碼入門範本套件：
  * [Mobile ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/appservice/starter-kits/mendix-mobile-app)
  * [Watson Web or Mobile App ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson)
  * [Web App ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://{DomainName}/developer/appservice/starter-kits/mendix-web-app)
3. 按一下**建立應用程式**。
4. 在**應用程式詳細資料**頁面上，將應用程式命名，並選擇性地提供標記來分類應用程式。如需相關資訊，請參閱[使用標籤](/docs/resources/tagging_resources.html#tag)。
5. 按一下**建立**。


## 授權 IBM 在 Mendix 上建立專案並鏈結帳戶
{: #link-mendix-account}

如果您尚未使用 Mendix 搭配 {{site.data.keyword.cloud_notm}}，則您會被引導至 Mendix Platform 註冊及授權 {{site.data.keyword.cloud_notm}} 代表您在 Mendix Platform 上建立新專案。這個專案會鏈結至 {{site.data.keyword.cloud_notm}}，因此部署會自動導向 {{site.data.keyword.cloud_notm}}。

1. 如果您看到訊息：「若要完成應用程式建立，需要 Mendix 使用者帳戶。您要現在鏈結您的帳戶嗎？」，請按一下**鏈結帳戶**。
2. 在 Mendix 確認頁面上，選取**我同意接受 Mendix 隱私權條款**，然後按一下**確認**。
3. 看到提示時，提供您的電子郵件位址、密碼及國家/地區，然後按一下**建立**。
4. 在**授權存取您的 Mendix 帳戶**頁面上，按一下**授權**。

授權完成之後，您的瀏覽器會回到正在建立的 Mendix 應用程式。即會顯示**選擇部署環境**頁面。

## 選取 Mendix 應用程式的部署選項
{: #select-deployment}

1. 在**選擇部署環境**頁面上，選取 Cloud Foundry，或其中一個在 {{site.data.keyword.cloud_notm}} 上執行的 Kubernetes 叢集。如果您的帳戶可以存取 {{site.data.keyword.cfee_full_notm}}，則可以選取**[公用雲端](/docs/cloud-foundry-public/about-cf.html#about-cf)**或**[企業環境](/docs/cloud-foundry-public/cfee.html#cfee)**的 Cloud Foundry 部署人員類型，用來建立及管理用於管理專供您企業使用的 Cloud Foundry 應用程式的隔離環境。
2. 選用。如果您沒有 Kubernetes 叢集，可以現在建立一個。
3. 在**配置工具鏈**頁面上，選取您的地區及資源群組，然後按一下**建立**。

即會建立 DevOps 工具鏈。工具鏈會在 {{site.data.keyword.cloud_notm}} 環境中整合 Mendix Platform 內的 Mendix 專案。預設應用程式會部署至您的目標部署，以便您可以驗證應用程式已在 DevOps 工具鏈完成時順利部署。

Mendix Cloud Foundry 部署需要 PostGRES 資料庫服務，該服務沒有精簡層級。如果您想要使用精簡帳戶評估 Mendix 入門範本套件，可以將目標設為試用 Kubernetes 叢集。
{: tip}

如果您已選取 Kubernetes 叢集以進行部署，請參閱 [Mendix Kubernetes 指導教學](/docs/apps/tutorials/tutorial_mendix_kubernetes.html#deploy-mendix-kube)，了解如何配置叢集以供正式作業使用。


## 繼續 Mendix 開發及部署生命週期
{: #dev-lifecycle-mendix}

Mendix 是低程式碼的編寫環境。開發生命週期會需要您在 Mendix Modeler 桌面應用程式中開啟專案。

1. 從您的 {{site.data.keyword.cloud_notm}} 應用程式，按一下**在 Mendix 上編輯**。
2. 在 Mendix Web 入口網站中，按一下 **Edit in Desktop Modeler**。
  Mendix 應用程式會在 Desktop Modeler 中開啟。
3. 編輯您的 Mendix 應用程式，然後儲存變更。
4. 使用 Mendix Desktop Modeler 應用程式的 **Run** 功能表，選取 **Run** 選項。
  即會建立部署套件並上傳到 Mendix。建立部署套件之後，您可以將應用程式部署至 {{site.data.keyword.cloud_notm}}。
5. 若要部署您的 Mendix 應用程式，請回到 {{site.data.keyword.cloud_notm}} 上的**應用程式詳細資料**頁面，然後按一下**部署應用程式**。
  這個動作會啟動您應用程式的 DevOps 工具鏈，它會從 Mendix 取回最新的部署，並將它部署至您的目標環境。部署完成之後，最新版的應用程式會自動啟動並變成可用。

藉由在 {{site.data.keyword.cloud_notm}} 上的**應用程式詳細資料**頁面中按一下**部署應用程式**，所有 Mendix 應用程式都會部署至 {{site.data.keyword.cloud_notm}}。請不要透過 IBM DevOps 介面手動呼叫 Mendix 工具鏈。透過 DevOps 介面手動啟動工具鏈，可能會導致因為缺乏對 Mendix 部署很重要之必要 meta 資料，而使部署失敗。視您應用程式的狀態而定，可能會在 DevOps 工具鏈啟動期間失敗，或在已部署的應用程式中發生錯誤。如果您手動啟動工具鏈而遭遇失敗，您可以藉由在 {{site.data.keyword.cloud_notm}} 上的**應用程式詳細資料**頁面中，按一下**部署應用程式**來還原應用程式部署。這個動作會為 Mendix 應用程式觸發完整的 DevOps 流程，這會包含必要的 meta 資料。
{: tip}

## 後續步驟 
{: #next-steps-mendix}

若要將您的應用程式部署至 {{site.data.keyword.containerlong_notm}}，請配置應用程式以便進行正式作業部署。如需相關資訊，請參閱 [Mendix Kubernetes 指導教學](/docs/apps/tutorials/tutorial_mendix_kubernetes.html#deploy-mendix-kube)。 
