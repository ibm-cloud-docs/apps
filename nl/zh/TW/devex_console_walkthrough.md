---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-11-29"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# {{site.data.keyword.cloud_notm}} 開發人員主控台逐步演練
{: #intro}

<!--I can't see how a customer needs to be walked through the experience without performing a specific task.-->


{{site.data.keyword.cloud}} Developer Experience 可讓雲端原生應用程式開發人員從各種入門範本套件建立應用程式、佈建並連接重要 {{site.data.keyword.Bluemix_notm}} 最佳化服務，然後快速下載工作碼或設定持續交付。Developer Experience 在 {{site.data.keyword.Bluemix_notm}} 內提供一組開發人員主控台，可讓您建立、檢視、配置及管理應用程式，以及將它部署至 DevOps 管線，或下載以進行本端開發。

透過 {{site.data.keyword.cloud_notm}} 開發人員主控台建立應用程式時，應用程式的所有必要部分都會在您的帳戶下，在 {{site.data.keyword.cloud_notm}} 伺服器上進行維護。因此，您可以選擇在開發人員主控台 GUI 和 [{{site.data.keyword.dev_cli_notm}}](/docs/cli/idt/index.html) 之間來回移動。

{{site.data.keyword.cloud_notm}} 開發人員主控台讓您平順地為選取的使用案例，建置可正式作業的入門範本應用程式。讓我們來看看在此過程中您可能採取的步驟。

<!-- Ready to jump in?  Visit the [{{site.data.keyword.cloud_notm}} Web App developer console](https://{DomainName}/developer/appservice) to get started.
{: tip} -->

##概觀畫面
{: #overview_screen}

「概觀」畫面提供您針對您處理中的主題或開發人員主控台頻道焦點量身訂做的內容。從概觀畫面，您可以查看文件、存取學習資源、瀏覽服務、查看特色入門範本套件，或鏈結至較大的入門範本套件集合。請按一下導覽中的`入門範本套件`，以進入「入門範本套件」視圖。

![開發人員主控台的「概觀」畫面](images/overview_screen.png "「概觀」畫面") <br> *開發人員主控台的「概觀」畫面*

##入門範本套件視圖
{: #starter_kits_view}

「入門範本套件」視圖顯示某使用案例區域所特定的入門範本套件集合。您可以按一下入門範本套件卡上的各種鏈結，查看示範及相關資訊。請選取入門範本套件以移至「建立新的應用程式」視圖。

在部分情況下，選取入門範本套件會提供您關於入門範本套件的更多詳細資料。如果是這種情況，只要按一下`建立`按鈕，即可移至「建立新的應用程式」視圖。
{: tip}

![開發人員主控台的「入門範本套件」視圖](images/starter_kits_view.png "「入門範本套件」視圖") <br> *開發人員主控台的「入門範本套件」視圖*

##建立新的應用程式視圖
{: #create_new_project_view}

從「建立新的應用程式」視圖，命名您的應用程式、提供部署及路徑資訊，然後選取語言。請注意，在右邊您也可以看到當您建立應用程式時會自動佈建的服務，以及每一者的定價方案及條款。按一下`建立`，以移至「應用程式詳細資料」視圖。如果您尚未登入 {{site.data.keyword.cloud_notm}}，此時您需要這麼做。

![開發人員主控台的「建立新的應用程式」視圖](images/create_new_project_view.png "「建立新的應用程式」視圖") <br> *開發人員主控台的「建立新的應用程式」視圖*

## 應用程式詳細資料視圖
{: #project_details_view}

「應用程式詳細資料」視圖會顯示針對您的應用程式配置的服務清單。針對清單中的每個項目，您會看到服務名稱、其他資訊的鏈結，以及具有三個垂直對齊點的*動作* 按鈕。*動作* 按鈕選項包括從應用程式移除服務、開啟服務的儀表板，以及刪除服務。請注意，移除服務實例只會移除對此應用程式的關聯，並不會刪除服務實例。此外，請注意服務認證會在此視圖上合併，因此您不必造訪每個個別服務實例視圖即可取得。

![開發人員主控台的「應用程式詳細資料」視圖](images/project_details_view.png "「應用程式詳細資料」視圖") <br> *開發人員主控台的「應用程式詳細資料」視圖*

「應用程式詳細資料」視圖也容許您將不屬於原始入門範本套件的新服務或現有服務新增至應用程式。請在服務清單框中按一下`新增資源`鏈結，以完成此作業。可用的服務取決於地區中可用的應用程式及服務類型，因此並非所有服務都可用來與所有應用程式相關聯。

![開發人員主控台的「新增資源」對話框](images/add_resource_dialog.png "「新增資源」對話框") <br> *開發人員主控台的「新增資源」對話框*

在「應用程式詳細資料」視圖上，您可以用兩種方式存取程式碼：

*  [建議] 按一下`部署至雲端`按鈕，將您的程式碼推送到儲存庫，然後將您的應用程式部署至 {{site.data.keyword.cloud_notm}}。如需 {{site.data.keyword.cloud_notm}} DevOps 工具鏈的相關資訊，請按一下[這裡](/docs/services/ContinuousDelivery/toolchains_about.html#toolchains_about)。
*  若要快速查看應用程式碼，請選取`下載程式碼`以產生並下載應用程式的程式碼。

##應用程式清單視圖
{: #project_list_view}

您可以從「應用程式清單」視圖查看所建立的所有應用程式清單。您可以從這裡重新命名或刪除應用程式。請按一下應用程式名稱列，以回到「應用程式詳細資料」視圖。

![開發人員主控台的「應用程式清單」視圖](images/project_list_view.png "「應用程式清單」視圖") <br> *開發人員主控台的「應用程式清單」視圖*
