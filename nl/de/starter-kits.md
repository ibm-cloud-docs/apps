---

copyright:
  years: 2019
lastupdated: "2019-05-09"

keywords: developer tools, building apps, developer entry point, get started coding, starter kit

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Was sind Starter-Kits?
{: #starter-kits}

Ein Starter-Kit ist ein einsatzbereites Muster, das in ein Servicepaket integriert werden kann, um ein einsatzbereites Asset zu generieren, das direkt in einer DevOps-Pipeline und einem Kubernetes-Cluster bereitgestellt werden kann. Starter-Kits eignen sich hervorragend für die dynamische Zusammenstellung eines Gerüsts für eine Produktionsanwendung in der Sprache Ihrer Wahl, das in der Cloud bereitgestellt werden kann. 
{:shortdesc}

Ein Starter-Kit enthält Metadaten, die den Aufbau und die Funktionalität des Kits beschreiben. Es enthält außerdem Informationen, die {{site.data.keyword.cloud_notm}} unterrichten, was erzeugt werden soll. Die Ausgabe ist ohne Vorbereitungs- oder Anpassungsaufwand einsatzbereit und kann für weitere Erweiterungen auf der Basis von {{site.data.keyword.cloud_notm}} Best Practices iteriert werden. Der Inhalt eines Starter-Kits ist weniger komplex als eine Demonstration, jedoch nicht so einfach strukturiert wie ein Snippet oder ein Beispiel. Apps werden basierend auf den Anforderungen des Entwicklers dynamisch erstellt.

Jedes Starter-Kit umfasst eine Sprache, ein Framework und ein Muster für einen bestimmten Anwendungsfall. Der Code muss nicht neu entwickelt werden, sondern kann wiederverwendet werden. Wenn für ein Starter-Kit bestimmte Services erforderlich sind, stehen automatisch bereitgestellte Services zur Verfügung, so dass bei der Erstellung Ihrer App automatisch Instanzen für diese Services erstellt werden.

## Inwiefern unterscheiden sich Starter-Kits von Beispielen?
{: #compare}

Starter-Kits sind einsatzfähig und legen einen Schwerpunkt auf der Veranschaulichung einer zentralen Musterimplementierung durch Verwendung einer Laufzeit (z.B. Node.js oder Express). In einigen Fällen können Starter-Kits eine einfache Benutzererfahrung enthalten, mit der die Integration des Service hervorgehoben wird. In anderen Fällen stellen die Starter-Kits eine anpassbare Implementierung eines hoch entwickelten Anwendungsfalls dar.

Ein Snippet ist eine Reihe von Codezeilen, häufig in einer IDE dargestellt. Snippets unterstützen einen Entwickler bei der Integration einer Programmiersprachensyntax oder einer definierten API. Eine Demonstration ist meist von hoher Qualität und Inhaltstreue und verwendet eine Reihe von Services und Integrationspunkten. Häufig erfordert sie eine gewisse Rüstzeit; sie wird eingesetzt, um ein Geschäftsproblem zu veranschaulichen oder ein Plattformfeature vorzuführen. Sie können sie zur Bewertung von Phasen (Stages) der Cloudeinführung verwenden. In einigen Fällen handelt es sich um Code, der in den Produktionscode eingebunden wird. Ein Beispiel umfasst nur ein bestimmtes Merkmal, eine Funktion, einen Service oder eine User Journey. Ein Beispiel kann wiederverwendet oder in eine Produktionsanwendung aufgenommen werden. In der Regel wird es verwendet, um technische Funktionen und einen möglichen Ansatz zur Lösung eines technischen Problems aufzuzeigen.

## Portierbarer Code
{: #portable-code}

Beim Erstellen einer App aus einem Starter-Kit wird automatisch Code für Sie erstellt, der ein konsistentes Format hat und laufzeitunabhängig ist. Sie können den Code in einem Ziel Ihrer Wahl implementieren, z. B. Kubernetes oder Cloud Foundry, ohne Änderungen vorzunehmen.

Portierbarer Code enthält Cloudaktivierungscode für mehrere Cloudumgebungen. Sie können Code produzieren, der den Best Practices (bewährten Verfahren) für eine bestimmte Sprache entspricht und konkret für einen Anwendungsfall entwickelt wurde. 

* Die Anwendungsfalllogik stellt Funktionen für die Kernfunktion eines bestimmten Anwendungsfalls bereit. Die Beispiele können u.a. den Code für einen Watson Conversation-Chat-Bot oder für eine mobile App zur visuellen Erkennung umfassen.
* Bei den Sprachkomponenten handelt es sich um für die Programmiersprache spezifische Codekomponenten und Dateien, die Sie für Ihr Starter-Kit auswählen. Beispielsweise benötigen node.js-Programmierer eine package.json-Datei für das Abhängigkeitsmanagement. Diese Datei wird automatisch für Sie erstellt.
* Die Serviceaktivierung ist Code, der es Ihrer App ermöglicht, eine Verbindung zu den von Ihnen hinzugefügten Services herzustellen und diese zu verwenden. Beispiele für Elemente der Serviceaktivierung können Berechtigungsnachweismanagement, Initialisierungscode oder servicespezifische SDKs sein.
* Bei der Cloudaktivierung handelt es sich um Code, mit dem Ihre App in {{site.data.keyword.cloud_notm}} ausgeführt werden kann. Das können z. B. Helm-Diagramme sein, mit denen Ihre App in einem {{site.data.keyword.cloud_notm}} Kubernetes-Cluster ausgeführt werden kann.

Sie können Ihren App-Code anzeigen, indem Sie auf der Detailseite der App auf **Code herunterladen** klicken. Ihr Code wird in Form einer `.zip`-Datei heruntergeladen, die die vollständige App-Codestruktur enthält. Sie können die Datei extrahieren und den Code lokal mithilfe der {{site.data.keyword.dev_cli_notm}} ausführen oder Sie können ihn zu Ihrem Code-Management-Repository hinzufügen.

Jede App enthält eine Readme-Datei mit technischen Details zur App und Erklärungen dazu, was zur Ausführung Ihrer App erforderlich ist, sofern es sich nicht um eine sofort einsatzbereite App handelt.
{: tip}
