---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-10"

keywords: apps, credentials, service, add service credentials, environment, deployment

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# Serviceberechtigungsnachweise Ihrer Bereitstellungsumgebung manuell hinzufügen
{: #credentials_overview}

Es ist wünschenswert, dass Ihre Anwendungslogik sensible Serviceberechtigungsnachweise (z. B. Datenbank-API-Schlüssel oder Kennwörter) aus der Umgebung, in der Ihre Anwendung ausgeführt wird, übernimmt. Auf diese Weise Berechtigungsnachweise nicht in Ihrem Quellcode-Repository aufbewahrt werden.
{: shortdesc}

Wenn Sie eine App erstellen, indem Sie ein Starter-Kit verwenden, wird die Umgebung automatisch für Sie vorbereitet. Wenn Sie einen Service mit Ihrem Starter-Kit verbinden, bevor Sie Ihre App bereitstellen, werden Ihrer Umgebung die Serviceberechtigungsnachweise automatisch hinzugefügt.
{ :tip}

In jedem der folgenden Szenarios müssen Sie Ihrer Bereitstellungsumgebung die Serviceberechtigungsnachweise manuell hinzufügen:

 * Sie integrieren Ihren eigenen Code.
 * Sie fügen einer Starter-Kit-basierten App einen Service hinzu, nachdem die App bereitgestellt worden ist.

Der Prozess zum Hinzufügen der Serviceberechtigungsnachweise ist von Ihrem Bereitstellungsziel und von Ihrer Programmiersprache abhängig. Weitere Informationen zum Konfigurieren von Serviceberechtigungsnachweisen für Ihr Bereitstellungsziel enthält die Dokumentation für Ihre jeweilige Hosting-Umgebung:

  * [{{site.data.keyword.containershort}}](/docs/containers?topic=containers-service-binding#adding_app)
  * Cloud Foundry Public oder {{site.data.keyword.cfee_full}}
  * Virtuelle Serverinstanz (lokaler Docker-Container)

Viele Sprachen und Frameworks bieten Standardbibliotheken für anwendungs- wie auch für umgebungsspezifische Konfigurationen. Weitere Informationen enthalten die folgenden Leitfäden zur Programmierung:

* [Java: Mit Serviceberechtigungsnachweisen arbeiten](/docs/java?topic=cloud-native-configuration)
* [Node.js-Umgebung konfigurieren](/docs/node?topic=nodejs-configure-nodejs)
* [Spring-Umgebung konfigurieren](/docs/java?topic=java-spring-configuration)
* [Swift-Umgebung konfigurieren](/docs/swift?topic=swift-configuration)
* [Go-Umgebung konfigurieren](/docs/go?topic=go-configure-go-env)
