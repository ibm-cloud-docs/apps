---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, credentials

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# Übersicht über Berechtigungsnachweise
{: #credentials_overview}

Hier erfahren Sie, wie Sie Serviceberechtigungsnachweise Ihrer Bereitstellungsumgebung manuell hinzufügen.
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

Im Allgemeinen möchten Sie, dass Ihre Anwendungslogik sensible Serviceberechtigungsnachweise (z. B. Datenbank-API-Schlüssel oder Kennwörter) aus der Umgebung, in der Ihre Anwendung ausgeführt wird, übernimmt. Auf diese Weise haben Sie keine Berechtigungsnachweise in Ihrem Quellcode-Repository. Die Datenbanken in Ihren Umgebungen für kontinuierliche Integration, Vorproduktion und Produktion sind voneinander getrennt.

Wenn Sie eine App erstellen, indem Sie eine Starter-Kit-Vorlage verwenden, wird die Umgebung automatisch für Sie vorbereitet. Unabhängig davon, welches Ihr Bereitstellungsziel ist:
  * [Kubernetes](/docs/apps?topic=creating-apps-add-credentials-kube)
  * [Cloud Foundry Public oder Cloud Foundry Enterprise Environment](/docs/apps?topic=creating-apps-add-credentials-cf)
  * [Virtual Server-Instanz (auch lokale Docker-Instanz)](/docs/apps?topic=creating-apps-add-credentials-vsi)
  
Die Schritte für die Konfiguration der Umgebung werden bereitgestellt. Starter-Kits generieren Code, der eine abhängige Bibliothek verwendet, um den Code portierbar zu machen, damit er auf jedem der Bereitstellungsziele ausgeführt werden kann. Schließlich wird keine Verzweigungslogik verwendet, um festzustellen, in welchem Bereitstellungsziel die Anwendung ausgeführt wird.

Der Administrator oder DevOps-Entwickler ist dann für die Vorbereitung der Umgebungen mit den entsprechenden Zugriffssteuerungen und Konfigurationen zuständig, damit Ihrer Anwendung die erforderlichen Werte zur Verfügung stehen.

"Continuous Delivery konfigurieren" ist ein einmaliger Schritt, der die folgenden Hauptaufgaben durchführt:
 * Vorbereitung Ihres Bereitstellungsziels mit Services, Ressourcen und Berechtigungsnachweisen.
 * Erstellung einer DevOps-Toolchain zum Erstellen und Bereitstellen Ihrer App in dieser Umgebung, indem Code verwendet wird, der die Berechtigungsnachweise in der Umgebung korrekt referenziert.

Sie müssen das Bereitstellungsziel jedoch in den folgenden Szenarios vorbereiten:
 * Sie integrieren Ihren eigenen Code.
 * Sie beginnen mit einer leeren Starter-Kit-Vorlage.
 * Sie fügen einen Service einer Starter-Kit-basierten App hinzu, nachdem sie bereitgestellt wurde.

Die Umgebungsvorbereitung wird immer für alle Berechtigungsnachweise für alle Services durchgeführt, die einer App zugeordnet sind, und alle `Services` werden in der Datei `manifest.yml` aufgelistet, aber nicht alle Berechtigungsnachweisreferenzen werden in die Datei `mappings.json` gestellt. In diesen Fällen müssen Sie solche Referenzen selbst angeben. Nachdem Sie sich für ein Bereitstellungsziel entschieden haben und die Abstraktion der Bibliothek `IBMCloudEnv` nicht benötigen, lesen Sie den Abschnitt "Ihr Code + (Bereitstellungsziel)", der mit Ihrer Entscheidung übereinstimmt.
{: important}

Einige Starter-Kits enthalten gar keine Referenz auf die `IBMCloudEnv`-Abhängigkeit oder die Dateien `manifest.yml` und `mappings.json`.
{: important}
