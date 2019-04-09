---

copyright:
  years: 2017, 2018
lastupdated: "2017-01-26"

---

{:shortdesc: .shortdesc}

# 管理應用程式
{: #hosting}

如果您具有現有應用程式，則可以在具有所有必要基礎架構或平台服務的 IBM Cloud 上進行管理。對於現有的應用程式，您可以充分運用 {{site.data.keyword.Bluemix_notm}} 基礎架構來管理專為 {{site.data.keyword.Bluemix_notm}} 所開發的應用程式。
{:shortdesc}

## 移轉應用程式
{: #ht_hostapp}

對於現有的應用程式，您可以漸進式地將應用程式移轉至 {{site.data.keyword.Bluemix_notm}}，而不要將應用程式全面轉移至雲端環境。您可以先移轉應用程式的某個部分，並使用 Cloud Integration 服務以連接至現有資料或記錄系統。

針對 {{site.data.keyword.Bluemix_notm}} 應用程式，您可能需要存取後端資料或服務（例如記錄系統）。在 {{site.data.keyword.Bluemix_notm}} 中，您可以使用 Secure Gateway 服務以在 {{site.data.keyword.Bluemix_notm}} 組織與企業後端網路之間建立安全通道。服務可讓 {{site.data.keyword.Bluemix_notm}} 上的應用程式存取後端網路的資料及服務。如需詳細資料，請參閱 [Reaching enterprise backend with Bluemix Secure Gateway via console ![外部鏈結圖示](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}。

{{site.data.keyword.Bluemix_notm}} 可以管理您的現有應用程式，並提供您所需要的所有基礎架構。在[型錄](https://console.bluemix.net/catalog/?taxonomyNavigation=apps)中，您可以選擇在裸機伺服器還是虛擬伺服器上管理應用程式。如果您需要較高效能的專用實體伺服器，則[裸機](../bare-metal/index.html#about-bare-metal-servers)部署是最佳選擇。如果您的工作負載分布在各個地理區域，且想要使用 {{site.data.keyword.Bluemix_notm}} Hypervisor 來管理部署，則[虛擬](/vsi/vsi_index.html#provisioning-a-virtual-server)部署是最佳選擇。

您可以同時或依元件逐一將應用程式的各部分移轉至 {{site.data.keyword.Bluemix_notm}}。請查看我們在您移轉應用程式時所提供的一些服務。

* 從區塊儲存空間、檔案儲存空間或物件儲存空間中，選取適合您的[儲存空間](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage)類型。
* 選取您所需的[網路](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork)類型。
* 選取[容器化](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers)服務，以充分運用 {{site.data.keyword.Bluemix_notm}} Kubernetes 技術。

## 後續步驟
{: #next-steps}

如果可以在多個地區中管理您的服務，則可以選取應用程式管理所在的位置。若要做到這點，請將您的自訂 URL 資訊登錄並新增於 {{site.data.keyword.Bluemix_notm}} 內的應用程式中。然後即可選取應用程式管理所在的地區。請參閱[更新應用程式](updapps.html)以取得如何部署應用程式的相關資訊。
