---

copyright:
  years: 2017, 2018
lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 移轉及管理應用程式
{: #hosting}

如果您具有現有應用程式，則可以在具有所有必要基礎架構或平台服務的 {{site.data.keyword.Bluemix}} 上進行管理。您也可以漸進式地將應用程式移轉至 {{site.data.keyword.Bluemix_notm}}，而不要一次將應用程式全都移轉至雲端環境。

## 移轉應用程式
{: #migrating}

如果您的應用程式需要存取內部部署資料或服務，可以使用 [{{site.data.keyword.SecureGatewayfull}}](../services/SecureGateway/secure_gateway.html)，在 {{site.data.keyword.Bluemix_notm}} 組織與企業後端網路之間建立安全通道。如需詳細資料，請參閱[透過主控台使用 {{site.data.keyword.Bluemix_notm}} Secure Gateway 來連接企業後端 ](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg)。

如果您在移轉時需要協助，則可以使用 [IBM Cloud Migration Services ](https://www.ibm.com/cloud/migration-services){: new_window}![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。

## 管理應用程式
{: #ht_hostapp}

在 {{site.data.keyword.Bluemix_notm}} [型錄](https://console.bluemix.net/catalog/?taxonomyNavigation=apps){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 中，您可以選擇受管理環境，例如 Kibernetes 或 Cloud Foundry，或者可以直接在裸機或虛擬伺服器上管理應用程式。

在虛擬部署上，大部分的應用程式作業是由 {{site.data.keyword.Bluemix_notm}} 進行管理。如果您的工作負載分布在各個地理區域，且想要使用 {{site.data.keyword.Bluemix_notm}} Hypervisor 來管理部署，則[虛擬](../vsi/vsi_about.html)部署是最佳選擇。如果您需要直接存取專用實體伺服器以獲得較高效能，[裸機](../bare-metal/index.html)部署是最佳選擇。

您也有許多選項可以：
* 從 Block Storage、File Storage 或 Object Storage，選取適合您的[儲存空間](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 類型。
* 選取您需要的[網路](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")。
* 選取[容器化](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 服務，以充分運用 {{site.data.keyword.Bluemix_notm}} Kubernetes 技術。
