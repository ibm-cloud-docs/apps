---

copyright:
  years: 2017, 2018
lastupdated: "2017-01-26"

---

{:shortdesc: .shortdesc}

# Apps hosten
{: #hosting}

Vorhandene Apps können Sie in IBM Cloud mit allen benötigten Infrastruktur- oder Plattformservices hosten. Bei vorhandenen Apps können Sie die Vorteile der {{site.data.keyword.Bluemix_notm}}-Infrastruktur für das Hosting von Apps nutzen, die Sie speziell für {{site.data.keyword.Bluemix_notm}} entwickelt haben.
{:shortdesc}

## Apps migrieren
{: #ht_hostapp}

Vorhandene Apps können Sie nach und nach auf {{site.data.keyword.Bluemix_notm}} migrieren, statt die Apps vollständig auf die Cloudumgebung umzustellen. Sie können zuerst einen Teil der App migrieren und danach mit dem Service 'Cloud Integration' eine Verbindung zu vorhandenen Daten oder einem System of Record herstellen.

Es kann erforderlich sein, für die {{site.data.keyword.Bluemix_notm}}-Apps auf Back-End-Daten oder -Services zuzugreifen, zum Beispiel auf ein System of Record (SOR, Kerndatensystem). In {{site.data.keyword.Bluemix_notm}} können Sie den Service 'Secure Gateway' zum Herstellen eines sicheren Tunnels zwischen einer {{site.data.keyword.Bluemix_notm}}-Organisation und dem Back-End-Netz eines Unternehmens verwenden. Mithilfe des Service können die Apps in {{site.data.keyword.Bluemix_notm}} auf die Daten und Services des Back-End-Netzes zugreifen. Details hierzu finden Sie unter [Reaching enterprise backend with Bluemix Secure Gateway via console ![Symbol für externen Link](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}.

{{site.data.keyword.Bluemix_notm}} kann bereits vorhandene Apps hosten und die gesamte benötigte Infrastruktur bereitstellen. Im [Katalog](https://console.bluemix.net/catalog/?taxonomyNavigation=apps) können Sie auswählen, ob Sie als Host für Ihre App einen Bare-Metal-Server oder einen virtuellen Server verwenden möchten. Eine [Bare-Metal](../bare-metal/index.html#about-bare-metal-servers)-Bereitstellung eignet sich am besten, wenn Sie einen dedizierten physischen Server für hohe Leistung benötigen. Eine [virtuelle](/vsi/vsi_index.html#provisioning-a-virtual-server) Bereitstellung ist am besten geeignet, wenn die Workload über geografische Regionen verteilt ist und Sie einen {{site.data.keyword.Bluemix_notm}}-Hypervisor zum Verwalten Ihrer Bereitstellungen verwenden möchten.

Sie können die einzelnen Komponenten einer App entweder komplett auf einmal oder nacheinander auf {{site.data.keyword.Bluemix_notm}} migrieren. Berücksichtigen Sie beim Migrieren Ihrer App unter anderem die folgenden Services, die Sie nutzen können:

* Wählen Sie den Typ des für Sie geeigneten [Speichers](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage) aus (Blockspeicher, Dateispeicher oder Objektspeicher).
* Wählen Sie den Typ des benötigten [Netzes](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork) aus.
* Wählen Sie einen Service für die [Containerisierung](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers) aus, um die Kubernetes-Technologie von {{site.data.keyword.Bluemix_notm}} zu nutzen.

## Nächste Schritte
{: #next-steps}

Falls Ihr Service in mehreren Regionen gehostet werden kann, können Sie auswählen, wo Ihre App gehostet werden soll. Registrieren Sie sich hierzu und fügen Sie Ihre angepassten URL-Angaben in Ihrer App in {{site.data.keyword.Bluemix_notm}} hinzu. Wählen Sie anschließend die Regionen aus, in denen Ihre App gehostet wird. Der Abschnitt [Apps aktualisieren](updapps.html) enthält weitere Informationen zur Bereitstellung Ihrer App.
