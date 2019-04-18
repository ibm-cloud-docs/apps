---

copyright:
  years: 2018
lastupdated: "2018-11-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# App-Entwicklung
{: #intro}

Die {{site.data.keyword.cloud_notm}}-Entwicklerkonsole unterstützt Entwickler bei der Erstellung von Apps auf Basis von Starter-Kits, bei der Bereitstellung und Verbindung wichtiger für {{site.data.keyword.cloud_notm}} optimierter Services und beim raschen Download von Code oder beim Einrichten von Continuous Delivery. Sie können Ihre App erstellen, anzeigen, konfigurieren und verwalten sowie den Code Ihrer App herunterladen. Durch den Einsatz von Starter-Kits können Sie {{site.data.keyword.cloud_notm}}-Services mit einer Beispielapp schnell bewerten und testen.
{:shortdesc}

## Was ist ein Starter-Kit?
{: #starter_kits}

Starter-Kits eignen sich hervorragend für die dynamische Zusammenstellung eines Gerüsts für eine Produktions-App in der Sprache Ihrer Wahl, das in der Cloud bereitgestellt werden kann. Jedes Starter-Kit umfasst eine Sprache, ein Framework und ein Muster für einen bestimmten realen Anwendungsfall. Der Code muss nicht neu entwickelt werden, sondern kann wiederverwendet werden.

### Beispiele und Starter-Kits vergleichen

Entwickler verwenden häufig bereits vorab geschriebenen Code wie z. B. Snippets, Demonstrationen und Beispiele. Wie können Snippets, Demonstrationen und Beispiele sowie {{site.data.keyword.cloud_notm}}-Starter-Kits voneinander unterschieden werden?

* **Snippet** - Wenige Zeilen mit Code, der häufig in einer IDE dargestellt wird. Snippets unterstützen einen Entwickler bei der Integration einer Programmiersprachensyntax oder einer definierten API.

* **Demonstration** - Code, der üblicherweise qualitativ hochwertig und inhaltstreu ist und eine Reihe von Services und Integrationspunkten verwendet. Er erfordert häufig eine gewisse Rüstzeit und wird eingesetzt, um ein Geschäftsproblem zu veranschaulichen oder ein Plattformfeature vorzuführen. Demonstrationen dienen zur Bewertung der Phasen (Stages) bei der Cloudeinführung. In bestimmten Fällen wird ihr Code in den Produktionscode eingebunden.

* **Beispiel** - Code, bei dem es sich um ein kompaktes Beispiel eines bestimmten Features, einer bestimmten Funktion, eines bestimmten Service oder einer bestimmten User Journey handelt. Ein Beispiel kann wiederverwendet werden oder in einer Produktionsanwendung enthalten sein. Sie können Beispiele verwenden, um technische Funktionen und mögliche Ansätze zur Lösung technischer Probleme zu zeigen.

* **{{site.data.keyword.cloud_notm}}-Starter-Kit** - Starter-Kits sind produktionsbereite Muster, die Sie mit einer Gruppe von Services integrieren können, um ein produktionsbereites Asset zu generieren. Anschließend können diese Komponenten direkt in einer DevOps-Pipeline und in einem Kubernetes-Cluster bereitgestellt werden. Ein Starter-Kit verfügt über beschreibende Metadaten, die Ihnen genügend Informationen über den Aufbau und die Funktionalität des Kits liefern. Es enthält außerdem Anweisungen, in denen angegeben ist, welche Elemente mit {{site.data.keyword.cloud_notm}} erzeugt werden sollen. Die Ausgabe kann funktional erweitert werden. Der Inhalt eines Starter-Kits ist nicht so komplex wie eine Demonstration und nicht so einfach strukturiert wie ein Snippet oder ein Beispiel. Starter-Kits werden abhängig von Ihren Anforderungen dynamisch erstellt.

  Starter-Kits enthalten eine grundlegende Musterimplementierung mit einer Laufzeitkomponente wie beispielsweise Swift oder Kitura. Sie können eine einfache Benutzererfahrung enthalten, mit der die Integration des Service hervorgehoben wird. Bei Starter-Kits handelt es sich um anpassbare Implementierungen eines komplexen Anwendungsfalls.

  Starter-Kits umfassen Anweisungen, mit denen {{site.data.keyword.cloud_notm}} automatisch gerüstbasierte App-Projekte mit portierbarem Code erzeugen kann. Sie enthalten außerdem Angaben zu Ressourcen, die bei der Projekterstellung automatisch bereitgestellt werden sollen.

## Automatisch bereitgestellte Ressourcen
{: #auto_privisioned_resources}

Wenn ein Starter-Kit erforderliche Ressourcen angibt, erstellt {{site.data.keyword.cloud_notm}} automatisch Instanzen dieser Ressourcen, wenn Sie Ihr Projekt erstellen. Dabei können Sie Ressourcen manuell bereitstellen oder vorhandene Ressourceninstanzen auswählen, um Ihr Projekt nach der Erstellung zu erweitern. In der Ansicht mit den *Projektdetails* können Sie eine Liste mit Serviceinstanzen anzeigen, die Ihrem Projekt zugeordnet sind. Außerdem sind dort die ggf. erforderlichen Berechtigungsnachweise aufgeführt.

## Portierbaren Code generieren
{: #portable_code}

Beim Erstellen einer App aus einem Starter-Kit wird automatisch Code für Sie erstellt, der ein konsistentes Format hat und laufzeitunabhängig ist. Sie können den Code in der Umgebung Ihrer Wahl bereitstellen, z. B. in Kubernetes oder Cloud Foundry, ohne Änderungen daran vorzunehmen.

Das Projekt umfasst eine `README`-Datei, die technische Details des Projekts enthält und in der erläutert wird, welche Schritte ausgeführt werden müssen, um Ihre App sofort einsatzbereit zu machen.

Weitere Informationen finden Sie in der [{{site.data.keyword.cloud_notm}}-Entwicklerkonsole für die Apple-Ausbildungsressourcen](https://cloud.ibm.com/developer/appledevelopment/learning-resources).
{: tip}

### Welcher App-Inhalt wird erstellt?
{: #content}

Der vom {{site.data.keyword.cloud_notm}}-Starter-Kit generierte Code umfasst vier grundlegende Komponenten: Anwendungsfalllogik, Sprachkomponenten, Serviceaktivierung und Cloudaktivierung. Das Generieren dieser Komponenten spart Ihnen wertvolle Zeit und stellt sicher, dass Sie mit der leistungsfähigsten Architektur arbeiten.

* Die **Anwendungsfalllogik** stellt den Code für einen bestimmten Anwendungsfall dar. Die Beispiele umfassen u. a. den Code für einen Watson Conversation-Chat-Bot oder den Code für eine mobile App für die visuelle Erkennung.
* Bei den **Sprachkomponenten** handelt es sich um Codekomponenten und Dateien, die speziell für die Sprache gelten, die Sie für Ihr Starter-Kit ausgewählt haben. Beispielsweise benötigen Node.js-Programmierer die Datei `package.json` für das Abhängigkeitsmanagement. Diese Datei wird automatisch in der {{site.data.keyword.cloud_notm}} Developer Experience erstellt.
* Bei der **Serviceaktivierung** handelt es sich um Code, der Ihrer App die Herstellung einer Verbindung zu Ihrem Projekt und die Nutzung der Services ermöglicht, die Sie hinzugefügt haben. Als Beispiele für Serviceaktivierungselemente können das Management von Berechtigungsnachweisen, der Initialisierungscode und servicespezifische SDKs aufgeführt werden.
* Bei der **Cloudaktivierung** handelt es sich um Code, der Ihrer App die Ausführung unter {{site.data.keyword.cloud_notm}} ermöglicht. Helm-Diagramme, die Ihrer App die Ausführung in einem {{site.data.keyword.cloud_notm}}-Kubernetes-Cluster ermöglichen, gehören z. B. der Cloudaktivierungskategorie an.

Die von {{site.data.keyword.cloud_notm}} generierte App ist mit einer robusten Architektur ausgestattet und bildet die Best Practices für die Sprache ab, die Sie für Ihr Projekt ausgewählt haben. Zur Anzeige der Details zu den Dateien und zur Struktur eines App-Projekts finden Sie in den folgenden Abschnitten.

* [Java-App-Dateien](/docs/apps/projects/java_project_contents.html)
* [Node.js-App-Dateien](/docs/apps/projects/node_project_contents.html)
* [Python-App-Dateien](/docs/apps/projects/python_project_contents.html)
* [Swift-App-Dateien](/docs/apps/projects/swift_project_contents.html)
