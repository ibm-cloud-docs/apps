---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-07-22"

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

## Web-App
{: #web}

Das Web-App-Muster generiert Apps, die Webinhalte wie HTML, JavaScript und Stylesheets für den Web-Server bereitstellen. {{site.data.keyword.cloud_notm}} bietet eine Reihe von Web-App-Starter-Kits.

* Basic - stellt eine statische Datei `index.html`, ein Standard- und ein leeres Stylesheet und eine JavaScript-Datei bereit.
* React - ein umfangreiches Framework zum Erstellen von Benutzerschnittstellen. Die Quellendateien befinden sich im Verzeichnis `src/client/app`, werden mit WebPack kompiliert und im öffentlichen Verzeichnis bereitgestellt.

Sie können Starter-Kits für Web-App-Muster im [{{site.data.keyword.cloud_notm}} App Service-Entwicklerdashboard](https://console.bluemix.net/developer/appservice/dashboard) finden.

## Back-End for Front-End (BFF)
{: #bff}

Ein Back-End-for-Front-End-Muster (BFF) vereinfacht das Erstellen von Back-End-Code, der Geschäftsdaten und -Services auf eine Weise verfügbar macht, die den Benutzererwartungen für einen bestimmten App-Kanal entspricht, z. B. mobil oder im Web. Benutzer eines mobilen Geräts verwenden möglicherweise die Sprachsteuerung, während Benutzer eines Web-Browsers eher mit der Maus arbeiten. Sie können zwei Back-End-for-Front-End-Muster erstellen, eines für Mobilgeräte, das Services wie [{{site.data.keyword.conversationfull}} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://www.ibm.com/watson/ai-assistant/) umfasst, und eines für Webanwendungen, das eine ausgereiftere Benutzerschnittstelle aufweist.

In {{site.data.keyword.cloud_notm}} können Sie ein Back-End-for-Front-End-Muster mit einem mehrsprachigen Programmieransatz erstellen. Sie können Node.js, Swift, Java oder Python verwenden und sie mit Container-Services oder mithilfe serverloser Funktionen in einem Muster ausführen.

BFF verwaltet Datenpersistenz, Caching und Integration mit den folgenden hochwertigen Services.

* [{{site.data.keyword.ibmwatson}} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=watson)
* [{{site.data.keyword.iot_short_notm}} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=iot)
* [{{site.data.keyword.weather_short}} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/catalog/services/weather-company-data?taxonomyNavigation=apps)
* [{{site.data.keyword.sparks}} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/catalog/services/apache-spark?taxonomyNavigation=apps)

Das Back-End-for-Front-End-Muster macht eine API in den meisten Fällen mithilfe eines REST-Musters verfügbar, aber Sie können Ihr eigenes Back-End-for-Front-End-Muster so konzipieren, dass es aus einer Messaging-Architektur heraus mit {{site.data.keyword.messagehub}} arbeitet.

Wählen Sie ein BFF-Starter-Kit für die jeweiligen Sprach- und Frameworkanforderungen aus. Sie finden die Starter-Kits für BFF-Muster im [{{site.data.keyword.cloud_notm}} App Service-Entwicklerdashboard](https://console.bluemix.net/developer/appservice/dashboard).

## Mikroservice
{: #microservice}

Mikroservice-Apps bilden die Basis für das Erstellen von Back-End-Mikroservices, einschließlich eines grundlegenden Statusendpunkts und einer REST-API. Generierte Apps enthalten alle Abhängigkeiten, die sowohl für den Mikroservice selbst, als auch für alle angehängten Cloud-Services erforderlich sind.

Wählen Sie ein Mikroservice-Starter-Kit für die jeweiligen Sprach- und Frameworkanforderungen aus. Sie finden die Starter-Kits für Mikroservice-Muster im [{{site.data.keyword.cloud_notm}} App Service-Entwicklerdashboard](https://console.bluemix.net/developer/appservice/dashboard).

## Mobil
{: #mobile}

Apps für Mobilgeräte unterscheiden sich von den anderen Mustern, weil sie eine signifikante clientseitige Komponente enthalten. Das Muster könnte beispielsweise eine direkte Verbindung zu mobilen Services wie Push-Benachrichtigungen, Authentifizierung und Analysen für Mobilanwendungen umfassen. Mobile Services werden als MBaaS-Muster (Mobile Backend as a Service) bezeichnet. Sie können auch über ein dediziertes [BFF](#bff) verfügen.

{{site.data.keyword.cloud_notm}} bietet diverse Starter-Kits für Mobilgeräte für iOS Swift, Android und Cordova. Sie finden die Starter-Kits für das Muster für Mobilgeräte im [{{site.data.keyword.cloud_notm}} Mobile-Entwicklerdashboard](https://console.bluemix.net/developer/mobile/dashboard).

## Sprachen
{: #languages}

Die Starter-Kits in {{site.data.keyword.cloud_notm}} sind in verschiedenen Sprachen und Frameworks verfügbar. Cloud-Mikroservice-Starter-Kits bieten beispielsweise eine Node.js-Option, während Starter-Kits für die Datenanalyse Python oder Go umfassen können. Auf einige gängige Sprachen, die in {{site.data.keyword.cloud_notm}}-Starter-Kits verwendet werden, wird näher eingegangen.

|Programmiersprache | Beschreibung | Entwicklungsframeworks |
|-----|-----|-----|
|Java | [Java](../runtimes/liberty/getting-started.html) ist vor allem für das Erstellen von auf Unternehmen abgestimmten Anwendungen geeignet. Aber neue Features in Java 8, kombiniert mit weniger komplexen Laufzeiten wie Liberty und Frameworks wie Spring Boot, sorgen dafür, dass Java sich auch sehr gut zum Erstellen von Mikroservices eignet. Java ist eine gängige Programmiersprache für Android-Apps. | Spring, Liberty, Android |
|Swift | [Swift](../runtimes/swift/getting-started.html) ist eine moderne Programmiersprache, die 2014 entwickelt wurde und Objective C sowie Open-Source-Sprachen im Dezember 2015 ersetzen sollte. Heute wird sie zum Entwickeln von iOS, macOS, Web-Services und Systemsoftware unter Linux- und macOS-Betriebssystemen eingesetzt, die x86, ARM oder z/Architecture verwenden. Sie wird wie eine Scripting-Sprache geschrieben, wird jedoch kompiliert, um eine ähnlich hohe Leistung wie C mit geringer Prozessorauslastung zu erzielen. Sie ist sehr gut für Cloud-Laufzeiten geeignet. Sie verwendet ein starkes und statisches Typsystem, das Sie von Java kennen, aber gleichzeitig den funktionalen Stil und die asynchronen Routinen aus JavaScript. Sie ist in höchst leistungsfähig und die Quelle wird in nativen Code kompiliert, der die LLVM-Compiler-Toolchain verwendet. Sie kann Systembibliotheken anderer Sprachen, die in C geschrieben sind, problemlos nutzen. Da Swift zum Codieren von clientseitigen und serverseitigen Apps verwendet werden kann, setzen Entwickler diese Sprache ein, wenn sie ohne großen Aufwand Funktionen vom Client zum Server und umgekehrt migrieren müssen. | Kitura, iOS|
|Node.js | [Node.js](../runtimes/nodejs/getting-started.html) ist eine JavaScript-Laufzeit, die ein ereignisgesteuertes, nicht blockierendes Ein-/Ausgabe-Modell verwendet, wodurch sie schlank und effizient bleibt. Sie bietet einen hervorragenden Durchsatz sowie eine hervorragende Skalierbarkeit für Web-Anwendungen, Back-End-for-Front-End-Muster und Mikroservices. Das Node.js-Registry, npm, bietet Zugriff auf eine umfassende Sammlung von Open-Source-Modulen. Es stellt eine breite Palette von Features für eine schnellere Anwendungsentwicklung bereit. | Express|
|JavaScript|JavaScript erzeugt interaktive Effekte in Webseiten. JavaScript bildet zusammen mit HTML und CSS die Grundlage der meisten Webseiten. Eingeschlossen in ein Cordova-Plug-in kann JavaScript-Code native Gerätefunktionen optimal nutzen. Entwickler mit Web-Know-how können mobile Apps ohne großen Aufwand erstellen und App-Code kann bei Bedarf für Webabwendungen und mobile Anwendungen wiederverwendet werden.|Cordova|
|Python | [Python](../runtimes/python/getting-started.html) ist eine vielseitig einsetzbare, interpretierte Programmiersprache, die besonderen Wert auf Lesbarkeit legt. In Python können Programmierer Funktionen mit weniger Codezeilen implementieren als dies in anderen Sprachen möglich wäre. Bestimmte Features der Sprache machen es möglich, objektorientierten, funktionalen oder imperativen Code zu schreiben. Python wird gängigerweise zum Verarbeiten von natürlichen Sprachtasks eingesetzt. | Flask, Django|


