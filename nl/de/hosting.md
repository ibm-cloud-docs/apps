---

copyright:
  years: 2017, 2019
lastupdated: "2019-05-10"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Hosting-Umgebung auswählen
{: #hosting}

Vorhandene Apps können Sie unter {{site.data.keyword.cloud}} mit allen benötigten Infrastruktur- oder Plattformservices hosten.
{:shortdesc}

Mit {{site.data.keyword.Bluemix_notm}} müssen Sie keine hohen Investitionen mehr in Hardware tätigen, um eine neue App zu testen oder zu betreiben. Stattdessen übernehmen wir die gesamte Verwaltung für Sie und berechnen nur, wovon Sie auch tatsächlich Gebrauch machen. Ihre Cloud-Server-Umgebung bildet die Grundlage Ihrer Infrastrukturebene. Sie können eine einzelne Option oder aber eine Kombination für komplexere Umgebungen auswählen. 

Für das Hosting Ihrer Apps stehen Ihnen diverse Möglichkeiten offen, wodurch Sie genau so viel Kontrolle über die Infrastruktur erhalten, wie Sie wünschen oder wie erforderlich ist. Sie können Ihre App auf eine der folgenden Arten ausführen:

  * Als Docker-Container in einem Kubernetes-Cluster
  * Als Cloud Foundry-App
  * Als serverlose Funktion
  * Als VMware
  * Als virtuelle Maschine (VM)
  * Auf leistungsfähigen {{site.data.keyword.baremetal_short}}-Instanzen 

Die folgende Tabelle enthält eine Zusammenfassung Ihrer Berechnungsoptionen.

| Option | Beschreibung | 
|--------|---------------|
| [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started) | Kombiniert Docker-Container, die Kubernetes-Technologie, ein intuitives Benutzererlebnis sowie integrierte Sicherheit und Isolation, um die Bereitstellung, den Betrieb, die Skalierung und die Überwachung containerisierter Apps in einem Cluster von Rechenhosts zu automatisieren. |
| [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) | Ermöglicht die bedarfsgesteuerte Instanziierung mehrerer isolierter, auf Unternehmen abgestimmter Cloud Foundry-Plattformen. |
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-getting_started) | Eine 'Functions-as-a-Service'-Programmierungsplattform (FaaS), die auf Apache OpenWhisk basiert. |
| [{{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started) | Ermöglicht die rasche und nahtlose Integration oder Migration von lokalen VMware-Workloads mithilfe einer skalierbaren, sicheren und leistungsstarken Infrastruktur und der branchenweit führenden Technologie für Hybridvirtualisierung von VMware. |
| [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-public-virtual-servers) | Skalierbare virtuelle Server, die mit dedizierten Cores und Hauptspeicherzuordnungen gekauft werden. |
| [{{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-bm-getting-started)  | Stündliche oder monatliche Berechnung von Servern mit einem einzigen Tenant, die Ihnen zugeordnet sind und in keiner Hinsicht (einschließlich Serverressourcen) gemeinsam mit anderen Kunden genutzt werden. |
{: caption="Tabelle 1. Berechnungsoptionen" caption-side="top"}

