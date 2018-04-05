---

copyright:
  years: 2017, 2018
lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Apps migrieren und hosten
{: #hosting}

Vorhandene Apps können Sie unter {{site.data.keyword.Bluemix}} mit allen benötigten Infrastruktur- oder Plattformservices hosten. Sie können Ihre App auch inkrementell zu {{site.data.keyword.Bluemix_notm}} migrieren, statt sie in einem Gang komplett in die Cloudumgebung zu schieben. 

## Apps migrieren
{: #migrating}

Wenn Ihre App auf Ihre lokalen Daten oder Services zugreifen soll, können Sie mit [{{site.data.keyword.SecureGatewayfull}}](../services/SecureGateway/secure_gateway.html) einen sicheren Tunnel zwischen einer {{site.data.keyword.Bluemix_notm}}-Organisation und Ihrem Unternehmens-Back-End einrichten. Details hierzu finden Sie unter [Reaching enterprise backend with {{site.data.keyword.Bluemix_notm}} Secure Gateway via console ](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg).

Wenn Sie Unterstützung bei der Migration benötigen, sind [IBM Cloud Migration Services](https://www.ibm.com/cloud/migration-services){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") verfügbar. 

## Apps hosten
{: #ht_hostapp}

Im {{site.data.keyword.Bluemix_notm}}-[Katalog](https://console.bluemix.net/catalog/?taxonomyNavigation=apps){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") können Sie eine verwaltete Umgebung wie Kubernetes oder Cloud Foundry auswählen oder Ihre App direkt auf einem Bare-Metal- oder virtuellen Server hosten. 

In einer virtuellen Bereitstellung werden die meisten Operationen Ihrer App von {{site.data.keyword.Bluemix_notm}} verwaltet. Eine [virtuelle](../vsi/vsi_about.html) Bereitstellung ist am besten geeignet, wenn die Workload über geografische Regionen verteilt ist und Sie einen {{site.data.keyword.Bluemix_notm}}-Hypervisor zum Verwalten Ihrer Bereitstellungen verwenden möchten. Eine [Bare-Metal](../bare-metal/index.html)-Bereitstellung eignet sich am besten, wenn Sie direkten Zugriff auf einen dedizierten physischen Server für hohe Leistung benötigen. 

Folgende Optionen stehen unter Umständen ebenfalls zur Verfügung: 
* Auswahl des geeigneten Typs von [Speicher](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") (Blockspeicher, Dateispeicher oder Objektspeicher). 
* Auswahl des erforderlichen Typs von [Netzwerk](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link"). 
* Auswahl eines [Containerisierungsservice](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link"), um die Kubernetes-Technologie von {{site.data.keyword.Bluemix_notm}} zu nutzen. 
