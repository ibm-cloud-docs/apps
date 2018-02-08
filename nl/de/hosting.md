---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# Apps hosten
{: #hosting}

Vorhandene Apps können Sie in IBM Cloud mit allen benötigten Infrastruktur- oder Plattformservices hosten. Die {{site.data.keyword.Bluemix_notm}}-Infrastruktur kann auch für das Hosting von Apps genutzt werden, die Sie speziell für {{site.data.keyword.Bluemix_notm}} entwickelt haben.
{:shortdesc}

## Apps migrieren
{: #ht_hostapp}

Sie können Ihre Apps nach und nach auf {{site.data.keyword.Bluemix_notm}} migrieren, statt die Apps komplett auf die Cloudumgebung umzustellen. Sie können zuerst einen Teil der App migrieren und danach mit dem Service 'Cloud Integration' eine Verbindung zu vorhandenen Daten oder einem System of Record herstellen.

Es kann erforderlich sein, für die {{site.data.keyword.Bluemix_notm}}-Apps auf Back-End-Daten oder -Services zuzugreifen, zum Beispiel auf ein System of Record (SOR, Kerndatensystem). In {{site.data.keyword.Bluemix_notm}} können Sie den Service 'Secure Gateway' zum Herstellen eines sicheren Tunnels zwischen einer {{site.data.keyword.Bluemix_notm}}-Organisation und dem Back-End-Netz des Unternehmens verwenden. Mithilfe des Service können die Apps in {{site.data.keyword.Bluemix_notm}} auf die Daten und Services des Back-End-Netzes zugreifen. Details hierzu finden Sie unter [Reaching enterprise backend with Bluemix Secure Gateway via console ![Symbol für externen Link](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}.

{{site.data.keyword.Bluemix_notm}} kann bereits vorhandene Apps hosten und die gesamte Infrastruktur in {{site.data.keyword.Bluemix_notm}} bereitstellen. Im [Katalog](https://console.bluemix.net/catalog/?taxonomyNavigation=apps) können Sie auswählen, ob Sie als Host für Ihre App die Cloud auf einem Bare-Metal-Server oder einen virtuellen Server verwenden wollen.

Sie können die einzelnen Komponenten einer App entweder komplett auf einmal oder nacheinander auf {{site.data.keyword.Bluemix_notm}} migrieren. Berücksichtigen Sie beim Migrieren Ihrer App unter anderem die folgenden Services, die Sie nutzen können:

* Wählen Sie den Typ des für Sie geeigneten [Speichers](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage) aus (Blockspeicher, Dateispeicher oder Objektspeicher).
* Wählen Sie den Typ des benötigten [Netzes](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork) aus.
* Wählen Sie einen Service für die [Containerisierung](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers) aus, um die Kubernetes-Technologie von {{site.data.keyword.Bluemix_notm}} zu nutzen.

## Nächste Schritte
{: #next-steps}

Falls Ihr Service in mehreren Regionen gehostet werden kann, können Sie auswählen, wo Ihre App gehostet werden soll. Im Abschnitt [Apps aktualisieren](updapps.html) erfahren Sie, wie Sie die Regionen auswählen, in denen Ihre App gehostet wird, und wie Sie die angepasste URL bearbeiten.
