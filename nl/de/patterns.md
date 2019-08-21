---

copyright:
  years: 2016, 2019
lastupdated: "2019-07-17"

keywords: supported architecture, supported languages cloud, web app, microservices, mobile, programming languages, app types, common architecture, cloud app, developer console, app service

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# Gängige Architekturen für Cloud-Apps
{: #patterns}

Starter-Kits unter {{site.data.keyword.cloud_notm}} helfen Ihnen dabei, Apps mit einer bewährten Architektur zu erzeugen. Apps sind alle unterschiedlich, aber wenn Sie Ihrer ein bekanntes Architekturmuster zugrunde legen, ist es einfacher, schnell ein zuverlässiges Ergebnis zu erhalten. Wenn Sie eine App aus einem Starter-Kit erstellen, wählen Sie neben einem Mustertyp auch Komponenten wie eine Laufzeit aus, um das Muster zu füllen.
{:shortdesc}

## Web-Apps
{: #web}

Das Web-App-Muster generiert Apps, die Webinhalte wie HTML, JavaScript und Stylesheets für den Web-Server bereitstellen. {{site.data.keyword.cloud_notm}} bietet eine Reihe von Web-App-Starter-Kits.

* Basic - stellt eine statische Datei `index.html`, ein Standard- und ein leeres Stylesheet und eine JavaScript-Datei bereit.
* React - ein umfangreiches Framework zum Erstellen von Benutzerschnittstellen. Die Quellendateien befinden sich im Verzeichnis `src/client/app`, werden mit WebPack kompiliert und im öffentlichen Verzeichnis bereitgestellt.

Sie finden Starter-Kits für das Web-App-Muster in der [{{site.data.keyword.cloud_notm}} App-Service-Entwicklerkonsole](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").

## Microservice-Apps
{: #microservice}

Mikroservice-Apps bilden die Basis für das Erstellen von Back-End-Mikroservices, einschließlich eines grundlegenden Statusendpunkts und einer REST-API. Generierte Apps enthalten alle Abhängigkeiten, die sowohl für den Mikroservice selbst, als auch für alle angehängten Cloud-Services erforderlich sind.

Wählen Sie ein Mikroservice-Starter-Kit für die jeweiligen Sprach- und Frameworkanforderungen aus. Sie finden Starter-Kits für das Microservice-Muster in der [{{site.data.keyword.cloud_notm}} App-Service-Entwicklerkonsole](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").

## Mobile Apps
{: #mobile}

Apps für Mobilgeräte unterscheiden sich von den anderen Mustern, weil sie eine signifikante clientseitige Komponente enthalten. Das Muster könnte beispielsweise eine direkte Verbindung zu mobilen Services wie Push-Benachrichtigungen, Authentifizierung und Analysen für Mobilanwendungen umfassen. Mobile Services werden als MBaaS-Muster (Mobile Backend as a Service) bezeichnet. Sie können auch über ein dediziertes Back-End-for-Front-End verfügen.

{{site.data.keyword.cloud_notm}} bietet mehrere mobile Starter-Kits für iOS Swift und Android an. Sie finden Starter-Kits für die Muster für Mobilgeräte in der [{{site.data.keyword.cloud_notm}} Mobile-Entwicklerkonsole](https://{DomainName}/developer/mobile/dashboard){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").

Zusätzlich können Sie eine benutzerdefinierte mobile App erstellen, indem Sie ein Basis-Starter-Kit verwenden und den mobilen App-Typ auswählen. Weitere Informationen hierzu finden Sie im Abschnitt [Mobile App erstellen](/docs/apps?topic=creating-apps-tutorial-mobile).

## Sprachbasierte Apps
{: #languages}

Die Starter-Kits in {{site.data.keyword.cloud_notm}} sind in verschiedenen Sprachen und Frameworks verfügbar. Cloud-Mikroservice-Starter-Kits bieten beispielsweise eine Node.js-Option, während Starter-Kits für die Datenanalyse Python oder Go umfassen können. Auf einige gängige Sprachen, die in {{site.data.keyword.cloud_notm}}-Starter-Kits verwendet werden, wird näher eingegangen.

|Programmiersprache | Beschreibung | Entwicklungsframeworks |
|-----|-----|-----|
|Java | [Java](/docs/runtimes/liberty?topic=liberty-getting-started) ist vor allem für das Erstellen von auf Unternehmen abgestimmten Apps geeignet. Aber neue Features in Java 8, kombiniert mit weniger komplexen Laufzeiten wie Liberty und Frameworks wie Spring Boot, sorgen dafür, dass Java sich auch sehr gut zum Erstellen von Mikroservices eignet. Java ist eine gängige Programmiersprache für Android-Apps. | Spring, Liberty, Android |
|Swift | [Swift](/docs/runtimes/swift?topic=Swift-getting-started) ist eine moderne Programmiersprache, die 2014 entwickelt wurde und Objective C sowie Open-Source-Sprachen im Dezember 2015 ersetzen sollte. Heute wird sie zum Entwickeln von iOS, macOS, Web-Services und Systemsoftware unter Linux- und macOS-Betriebssystemen eingesetzt, die x86, ARM oder z/Architecture verwenden. Sie wird wie eine Scripting-Sprache geschrieben, wird jedoch kompiliert, um eine ähnlich hohe Leistung wie C mit geringer Prozessorauslastung zu erzielen. Sie ist sehr gut für Cloud-Laufzeiten geeignet. Sie verwendet ein starkes und statisches Typsystem, das Sie von Java kennen, aber gleichzeitig den funktionalen Stil und die asynchronen Routinen aus JavaScript. Sie ist in höchst leistungsfähig und die Quelle wird in nativen Code kompiliert, der die LLVM-Compiler-Toolchain verwendet. Sie kann Systembibliotheken anderer Sprachen, die in C geschrieben sind, problemlos nutzen. Da Swift zum Codieren von clientseitigen und serverseitigen Apps verwendet werden kann, setzen Entwickler diese Sprache ein, wenn sie ohne großen Aufwand Funktionen vom Client zum Server und umgekehrt migrieren müssen. | Kitura, iOS|
|Node.js | [Node.js](/docs/runtimes/nodejs?topicid=Nodejs-getting-started) ist eine JavaScript-Laufzeit, die ein ereignisgesteuertes, nicht blockierendes Ein-/Ausgabe-Modell verwendet, wodurch sie schlank und effizient bleibt. Sie bietet einen hervorragenden Durchsatz sowie eine hervorragende Skalierbarkeit für Web-Apps, Back-End-for-Front-End-Muster und Mikroservices. Das Node.js-Registry, npm, bietet Zugriff auf eine umfassende Sammlung von Open-Source-Modulen. Es stellt eine breite Palette von Features für eine schnellere App-Entwicklung bereit. | Express|
|Python | [Python](/docs/runtimes/python?topic=Python-getting_started) ist eine vielseitig einsetzbare, interpretierte Programmiersprache, die besonderen Wert auf Lesbarkeit legt. In Python können Programmierer Funktionen mit weniger Codezeilen implementieren als dies in anderen Sprachen möglich wäre. Bestimmte Features der Sprache machen es möglich, objektorientierten, funktionalen oder imperativen Code zu schreiben. Python wird gängigerweise zum Verarbeiten von natürlichen Sprachtasks eingesetzt. | Flask, Django |
{: caption="Tabelle 1. Sprachen, die in Starter-Kits verwendet werden" caption-side="top"}
