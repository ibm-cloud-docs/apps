---

copyright:
  years: 2017, 2019
lastupdated: "2019-03-29"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Apps migrieren und hosten
{: #hosting}

Vorhandene Apps können Sie unter {{site.data.keyword.cloud}} mit allen benötigten Infrastruktur- oder Plattformservices hosten. Sie können Ihre App auch inkrementell zu {{site.data.keyword.cloud_notm}} migrieren, statt sie in einem Gang komplett in die Cloudumgebung zu schieben.

## Apps migrieren
{: #migrating}

Wenn Ihre App auf Ihre lokalen Daten oder Services zugreifen soll, können Sie mit [{{site.data.keyword.SecureGatewayfull}}](/docs/services/SecureGateway?topic=securegateway-getting-started-with-sg#getting-started-with-sg) einen sicheren Tunnel zwischen einer {{site.data.keyword.cloud_notm}}-Organisation und Ihrem Unternehmens-Back-End einrichten. Details hierzu finden Sie unter [Reaching enterprise backend with {{site.data.keyword.cloud_notm}} Secure Gateway via console ](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").

Wenn Sie Unterstützung bei der Migration benötigen, sind [{{site.data.keyword.cloud_notm}} Migrationsservices ](https://www.ibm.com/cloud/migration-services){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") verfügbar.

## Apps hosten
{: #ht_hostapp}

Im {{site.data.keyword.cloud_notm}}-[Katalog](https://{DomainName}/catalog/?taxonomyNavigation=apps){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") können Sie eine verwaltete Umgebung wie Kubernetes oder Cloud Foundry auswählen oder Sie können Ihre App direkt auf einem Bare-Metal- oder virtuellen Server hosten.

In einer virtuellen Bereitstellung werden die meisten Operationen Ihrer App von {{site.data.keyword.cloud_notm}} verwaltet. Eine [virtuelle](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers) Bereitstellung ist am besten geeignet, wenn die Workload über geografische Regionen verteilt ist und Sie einen {{site.data.keyword.cloud_notm}}-Hypervisor zum Verwalten Ihrer Bereitstellungen verwenden möchten. Eine [Bare-Metal](/docs/bare-metal?topic=bare-metal-bm-getting-started#getting-started)-Bereitstellung eignet sich am besten, wenn Sie direkten Zugriff auf einen dedizierten physischen Server für hohe Leistung benötigen.

Folgende Optionen stehen unter Umständen ebenfalls zur Verfügung:
* Auswahl des geeigneten Typs von [Speicher](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") (Blockspeicher, Dateispeicher oder Objektspeicher).
* Auswahl des erforderlichen Typs von [Netz](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")}.
* Auswahl eines [Containerisierungsservice](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=containers){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link"), um die Kubernetes-Technologie von {{site.data.keyword.cloud_notm}} zu nutzen.
