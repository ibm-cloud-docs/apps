---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# 管理應用程式
{: #hosting}

如果您具有現有應用程式，則可以在具有所有必要基礎架構或平台服務的 IBM Cloud 上進行管理。您也可以充分運用 {{site.data.keyword.Bluemix_notm}} 基礎架構來管理專為 {{site.data.keyword.Bluemix_notm}} 所開發的應用程式。
{:shortdesc}

## 移轉應用程式
{: #ht_hostapp}

您可以漸進式地將應用程式移轉至 {{site.data.keyword.Bluemix_notm}}，而不要將應用程式全面轉移至雲端環境。您可以先移轉應用程式的某個部分，並使用 Cloud Integration 服務以連接至現有資料或記錄系統。

針對 {{site.data.keyword.Bluemix_notm}} 應用程式，您可能需要存取後端資料或服務（例如記錄系統）。在 {{site.data.keyword.Bluemix_notm}} 中，您可以使用 Secure Gateway 服務以在 {{site.data.keyword.Bluemix_notm}} 組織與企業後端網路之間建立安全通道。服務可讓 {{site.data.keyword.Bluemix_notm}} 上的應用程式存取後端網路的資料及服務。如需詳細資料，請參閱 [Reaching enterprise backend with Bluemix Secure Gateway via console ![外部鏈結圖示](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}。

{{site.data.keyword.Bluemix_notm}} 可以管理您的現有應用程式，並提供 {{site.data.keyword.Bluemix_notm}} 中的所有基礎架構。在[型錄](https://console.bluemix.net/catalog/?taxonomyNavigation=apps)中，您可以選擇在裸機伺服器還是虛擬伺服器上管理雲端上的應用程式。

您可以同時或依元件逐一將應用程式的各部分移轉至 {{site.data.keyword.Bluemix_notm}}。請查看我們在您移轉應用程式時所提供的一些服務。

* 從區塊儲存空間、檔案儲存空間或物件儲存空間中，選取適合您的[儲存空間](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage)類型。
* 選取您所需的[網路](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork)類型。
* 選取[容器化](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers)服務，以充分運用 {{site.data.keyword.Bluemix_notm}} Kubernetes 技術。

## 後續步驟
{: #next-steps}

如果可以在多個地區中管理您的服務，則可以選取應用程式管理所在的位置。在[更新應用程式](updapps.html)中，您可以選取應用程式管理所在的地區，以及編輯自訂 URL。
