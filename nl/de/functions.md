---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-29"

keywords: apps, serverless, serverless app, functions, cli, api, sdk, create serverless app, serverless app tutorial

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Serverunabhängige Apps entwickeln
{: #serverless}

Für eine serverunabhängige Entwicklung können Sie das IBM FaaS-Angebot (Functions which is Service) {{site.data.keyword.openwhisk}} nutzen. Mit {{site.data.keyword.openwhisk_short}} können Sie Anwendungslogik als Reaktion auf Ereignisse oder direkte Aufrufe über Web-Apps oder mobile Apps über HTTP ausführen, ohne dass Server bereitgestellt oder verwaltet werden müssen. {{site.data.keyword.openwhisk_short}} führt Systemverwaltungsaufgaben wie automatische Skalierung, Verfügbarkeitsmanagement und Wartung aus, sodass Sie sich als Entwickler auf das Schreiben von App-Logik konzentrieren können.
{:shortdesc}

Sie können Ihre serverunabhängigen Apps mit einer der folgenden Methoden entwickeln:
* {{site.data.keyword.openwhisk_short}}-Benutzerschnittstelle (UI).
* {{site.data.keyword.openwhisk_short}}-Befehlszeilenschnittstelle (CLI), die weiterreichende Möglichkeiten zur Steuerung der Bereitstellung und der Operationen bietet.
* {{site.data.keyword.openwhisk_short}}-Starter-Kit, mit dem Sie Continuous Delivery mithilfe einer DevOps-Toolchain und Delivery Pipeline konfigurieren können.

Detailliertere Informationen zu {{site.data.keyword.openwhisk_short}} finden Sie in der [-Dokumentation](/docs/openwhisk?topic=cloud-functions-getting_started).


## Entwicklung mit der {{site.data.keyword.openwhisk_short}}-Befehlszeilenschnittstelle
{: #serverless-apps-ui}

Testen Sie {{site.data.keyword.openwhisk_short}} in Ihrem [Browser](https://{DomainName}/functions/actions){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")}. Rufen Sie die Seite [Konzepte ](https://{DomainName}/functions/learn){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") auf, die eine Kurzübersicht der {{site.data.keyword.openwhisk_short}}-Benutzerschnittstelle bietet.

## Entwicklung mit der Befehlszeilenschnittstelle
{: #openwhisk_start_configure_cli}

Weitere Informationen zur Verwendung der {{site.data.keyword.openwhisk_short}}-CLI bei der Installation und Entwicklung finden Sie unter [{{site.data.keyword.openwhisk_short}}-Befehlszeilenschnittstelle einrichten](https://{DomainName}/functions/cli){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").

## APIs und Datasets als Webaktionen verfügbar machen
{: #expose-actions}

Standardmäßig definiert {{site.data.keyword.openwhisk_short}} Aktionen, für die ein Authentifizierungsschlüssel erforderlich ist. In mobilen Produktionsumgebungen ist häufig eine Berechtigung mobiler Clients auf der Basis von OAuth-Abläufen erforderlich, um APIs und bestimmte Datasets verfügbar zu machen.

{{site.data.keyword.openwhisk_short}} ermöglicht es Entwicklern, Funktionen als Web-Aktionen verfügbar zu machen, die annotiert werden, und so schnell webbasierte Apps zu entwickeln. Sie können Back-End-Logik mit annotierten Aktionen programmieren, auf die Ihre Web-App anonym zugreifen kann, ohne dass ein {{site.data.keyword.openwhisk_short}}-Authentifizierungsschlüssel erforderlich ist.

Zum Verfügbarmachen einer Aktion als Web-Aktion rufen Sie die Registerkarte **Endpunkte** der Aktion auf und wählen Sie **Als Web-Aktion aktivieren** aus.

Nun können Benutzer über einen Browser oder eine cURL-Anforderung auf die Aktion zugreifen. Beispiel:
```
curl https://openwhisk.cloud.ibm.com/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

Ausgabe:
```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} stellt ein [SDK für Mobilgeräte](/docs/openwhisk?topic=cloud-functions-pkg_mobile_sdk) für iOS- und watchOS-Geräte bereit, mit dem mobile Apps ohne großen Aufwand ferne Auslöser senden und ferne Aktionen aufrufen können.

## Serverunabhängige Apps mit einem Starter-Kit erstellen
{: #serverless-starter}

Sie können mit einem Starter-Kit eine serverunabhängige App erstellen, zum Beispiel 'Python Example Serverless App'. Führen Sie die folgenden Schritte aus, um Starter-Kits zu suchen:

1. Rufen Sie die Seite [App-Service-Starter-Kits](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") in der {{site.data.keyword.dev_console}}-Konsole auf.
2. Geben Sie in die Suchleiste `serverunabhängig` ein, um die Liste der Starter-Kits zu filtern.
3. Wählen Sie ein serverunabhängiges Starter-Kit aus, zum Beispiel 'Python Example Serverless App'.
4. Benennen Sie Ihre App und wählen Sie eine Ressourcengruppe aus.
5. Optional. Geben Sie Tags an, um Ihre App zu klassifizieren. Weitere Informationen finden Sie in [Mit Tags arbeiten](/docs/resources?topic=resources-tag).
6. Erstellen Sie eine Cloudant-Serviceinstanz oder wählen Sie eine vorhandene Cloudant-Serviceinstanz aus.
7. Optional. Um Ihren Code zu überprüfen, bevor Sie weitere Services hinzufügen oder Ihre App entwickeln, klicken Sie auf **Quellcode anzeigen**. Prüfen Sie die Datei `README.md`, um herauszufinden, ob weitere Aktionen durchgeführt werden müssen, um die App betriebsbereit zu machen.
8. Klicken Sie auf **Erstellen**.

Großartiger Start! Sie haben soeben eine App erstellt!

## Services hinzufügen (optional)
{: #serverless-services}

Wenn für ein Starter-Kit bestimmte Services erforderlich sind, stehen automatisch bereitgestellte Services zur Verfügung, so dass bei der Erstellung Ihrer App automatisch Instanzen für diese Services erstellt werden.

1. Klicken Sie auf der Detailseite der App abhängig davon, ob Sie bereits über Services verfügen, die Sie mit dieser App verbinden möchten, auf **Service erstellen** oder auf **Vorhandene Services verbinden**.
2. Wählen Sie die Art des gewünschten Service aus und folgen Sie den Anweisungen, um entweder eine Serviceinstanz zu erstellen oder aber einen vorhandenen Service zu Ihrer App hinzuzufügen.

Nachdem Sie alle gewünschten Services hinzugefügt haben, werden die Services auf der Detailseite der App angezeigt.

## Ihre App bereitstellen
{: #serverless-deploy}

Führen Sie die folgenden Schritte aus, um Ihre App bereitzustellen:

1. Klicken Sie auf der Detailseite der App auf **Bereitstellen**.
2. Wählen Sie **In Cloudfunktionen bereitstellen** aus und klicken Sie auf **Weiter**.
3. Geben Sie auf der Seite zur Konfiguration der Toolchain einen Toolchain-Namen ein, wählen Sie eine Region aus und klicken Sie auf **Erstellen**. Nachdem Sie das Bereitstellungsziel ausgewählt und konfiguriert haben, wird auf der Detailseite der App angezeigt, dass Continuous Delivery konfiguriert ist.
4. Optional. Überprüfen Sie die Aktionen in der {{site.data.keyword.openwhisk_short}}-Konsole, indem Sie auf das Aktionssymbol ![Symbol für weitere Aktionen](../icons/action-menu-icon.svg) klicken und **Cloudfunktionen öffnen** auswählen.
5. Optional. Wenn Sie das Repository anzeigen möchten, das den generierten Code für Ihre App und Services enthält, klicken Sie auf **Repository anzeigen**.

## Bereitstellung Ihrer App verifizieren
{: #serverless-verify}

Bei einer ordnungsgemäß konfigurierten Toolchain startet mit jedem Vorgang der Zusammenführung mit dem Masterzweig in Ihrem Repository ein Erstellungs-/Bereitstellungszyklus. Weitere Informationen finden Sie unter [Erstellen und bereitstellen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

Führen Sie die folgenden Schritte aus, um zu verifizieren, dass Ihre App erfolgreich bereitgestellt wurde:

1. Klicken Sie auf der Detailseite der App auf **Toolchain anzeigen**.
2. Klicken Sie auf **Delivery Pipeline**. Hier können Sie Builds starten, die Bereitstellung verwalten sowie Protokolle und den Verlauf anzeigen.
3. Wenn die Bereitstellung erfolgreich ist, zeigt jede Pipeline-Stage **Stage Passed** (Staging bestanden) an.
4. Um die Aktion und die API-Informationen anzuzeigen, klicken Sie in der Kachel **Bereitstellungsstage** auf **Protokolle und Verlauf anzeigen**.
