---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Übersicht über Berechtigungsnachweise
{: #credentials_overview}

Hier erfahren Sie, wie Sie Serviceberechtigungsnachweise Ihrer Bereitstellungsumgebung manuell hinzufügen.
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

Im Allgemeinen möchten Sie, dass Ihre Anwendungslogik sensible Serviceberechtigungsnachweise (z. B. Datenbank-API-Schlüssel oder Kennwörter) aus der Umgebung, in der Ihre Anwendung ausgeführt wird, übernimmt. Auf diese Weise haben Sie keine Berechtigungsnachweise in Ihrem Quellcode-Repository. Die Datenbanken in Ihren Umgebungen für kontinuierliche Integration, Vorproduktion und Produktion sind voneinander getrennt.

Wenn Sie eine App erstellen, indem Sie eine Starter-Kit-Vorlage verwenden, wird die Umgebung automatisch für Sie vorbereitet. Unabhängig davon, welches Ihr Bereitstellungsziel ist:
  * [Kubernetes](/docs/apps/creds_kube.html#add-credentials-kube)
  * [Cloud Foundry Public oder Cloud Foundry Enterprise Environment](/docs/apps/creds_cf.html#add-credentials-cf)
  * [Virtual Server-Instanz (auch lokale Docker-Instanz)](/docs/apps/creds_vsi.html#add-credentials-vsi)
  
Die Schritte für die Konfiguration der Umgebung werden bereitgestellt. Starter-Kits generieren Code, der eine abhängige Bibliothek verwendet, um den Code portierbar zu machen, damit er auf jedem der Bereitstellungsziele ausgeführt werden kann. Schließlich wird keine Verzweigungslogik verwendet, um festzustellen, in welchem Bereitstellungsziel die Anwendung ausgeführt wird.

Der Administrator oder DevOps-Entwickler ist dann für die Vorbereitung der Umgebungen mit den entsprechenden Zugriffssteuerungen und Konfigurationen zuständig, damit Ihrer Anwendung die erforderlichen Werte zur Verfügung stehen.

"In Cloud bereitstellen" ist ein einmaliger Schritt, der die folgenden Hauptaufgaben durchführt:
 * Vorbereitung Ihrer Zielbereitstellungsumgebung mit Services, Ressourcen und Berechtigungsnachweisen.
 * Erstellung einer DevOps-Toolchain zum Erstellen und Bereitstellen Ihrer App in dieser Umgebung, indem Code verwendet wird, der die Berechtigungsnachweise in der Umgebung korrekt referenziert.

Sie müssen die Zielbereitstellungsumgebung jedoch in den folgenden Szenarios vorbereiten:
 * Sie integrieren Ihren eigenen Code.
 * Sie beginnen mit einer leeren Starter-Kit-Vorlage.
 * Sie fügen einen Service einer Starter-Kit-basierten App hinzu, _nachdem_ sie bereitgestellt wurde.




