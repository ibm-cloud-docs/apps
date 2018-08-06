---

copyright:
  years: 2018
lastupdated: "2018-07-25"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Serverunabhängige Apps entwickeln
{: #serverless}

Für eine serverunabhängige Entwicklung können Sie das IBM FaaS-Angebot (Functions as a Service) {{site.data.keyword.openwhisk}} nutzen. Mit {{site.data.keyword.openwhisk_short}} können Sie Anwendungslogik als Reaktion auf Ereignisse oder direkte Aufrufe über Web-Apps oder mobile Apps über HTTP ausführen, ohne dass Server bereitgestellt oder verwaltet werden müssen. {{site.data.keyword.openwhisk_short}} führt Systemverwaltungsaufgaben wie automatische Skalierung, Verfügbarkeitsmanagement und Wartung aus, sodass Sie sich als Entwickler auf das Schreiben von Anwendungslogik konzentrieren können.
{:shortdesc}

Sie können die {{site.data.keyword.openwhisk_short}}-Benutzerschnittstelle oder die Befehlszeilenschnittstelle für die Anwendungsentwicklung verwenden. Beide enthalten ähnliche Anwendungsentwicklungsfunktionen. Die Befehlszeilenschnittstelle bietet weiterreichende Möglichkeiten zur Steuerung der Bereitstellung und der Operationen. Detailliertere Informationen zu {{site.data.keyword.openwhisk_short}} finden Sie in der umfassenden [Dokumentation](/docs/openwhisk/index.html).

## {{site.data.keyword.openwhisk_short}}-Benutzerschnittstelle
{: #ui}

Testen Sie {{site.data.keyword.openwhisk_short}} in Ihrem [Browser ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.{DomainName}/openwhisk/actions){:new_window}. Rufen Sie die Seite [Konzepte ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.{DomainName}/openwhisk/learn){:new_window} auf, die eine Kurzübersicht der {{site.data.keyword.openwhisk_short}}-Benutzerschnittstelle bietet.

## Entwicklung mit der Befehlszeilenschnittstelle
{: #openwhisk_start_configure_cli}

Weitere Informationen zur Verwendung der {{site.data.keyword.openwhisk_short}}-Befehlszeilenschnittstelle für die Installation und Entwicklung finden Sie in [{{site.data.keyword.openwhisk_short}}-Befehlszeilenschnittstelle einrichten ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.{DomainName}/openwhisk/cli){:new_window}.

## APIs und Datasets als Webaktionen verfügbar machen
{: #containers}

Standardmäßig definiert {{site.data.keyword.openwhisk_short}} Aktionen, für die ein Authentifizierungsschlüssel erforderlich ist. In mobilen Produktionsumgebungen ist häufig eine Berechtigung mobiler Clients auf der Basis von OAuth-Abläufen erforderlich, um APIs und bestimmte Datasets verfügbar zu machen.

{{site.data.keyword.openwhisk_short}} ermöglicht es Entwicklern, Funktionen als Web-Aktionen verfügbar zu machen, die annotiert werden, und so schnell webbasierte Anwendungen zu entwickeln. Sie können Back-End-Logik mit annotierten Aktionen programmieren, auf die Ihre Webanwendung anonym zugreifen kann, ohne dass ein {{site.data.keyword.openwhisk_short}}-Authentifizierungsschlüssel erforderlich ist.

Zum Verfügbarmachen einer Aktion als Web-Aktion rufen Sie die Registerkarte **Endpunkte** der Aktion auf und wählen Sie **Als Web-Aktion aktivieren** aus.

Nun können Benutzer über einen Browser oder eine cURL-Anforderung auf die Aktion zugreifen. Beispiel:

```
curl https://openwhisk.ng.bluemix.net/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

**Ausgabe:**

```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} stellt ein [SDK für Mobilgeräte](/docs/openwhisk/openwhisk_mobile_sdk.html#mobile-sdk) für iOS- und watchOS-Geräte bereit, mit dem mobile Apps ohne großen Aufwand ferne Auslöser senden und ferne Aktionen aufrufen können. Darüber hinaus steht ein [SDK für serverunabhänigige Frameworks ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/openwhisk/openwhisk_goserverless.html){:new_window} für serverunabhängige Anwendungen zur Verfügung.
