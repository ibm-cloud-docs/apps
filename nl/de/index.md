---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-12"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Lernprogramm 'Einführung'
{: #create}

In {{site.data.keyword.Bluemix}} können Sie auf Unternehmen abgestimmte Mobil- und Webanwendungen erstellen und von {{site.data.keyword.Bluemix_notm}} gehostete Clouderweiterungen nutzen. Mit der {{site.data.keyword.Bluemix}}-Konsole und den Befehlszeilentools können Sie Ihre Apps erstellen, ausführen und bereitstellen. Sie können auf eine der folgenden Arten beginnen: Sie erstellen mit einem Starter-Kit eine App, die den Prozess für Sie verwaltet, oder - sofern Sie wissen, was Sie möchten - Sie erstellen Ihre App mit den benötigten Ressourcen.
{:shortdesc}

Mit einem Starter-Kit können Sie Ihre App schnell zum Einsatz bringen und auf zukünftige Entwicklungen vorbereiten. Wählen Sie ein Starter-Kit und eine Programmiersprache aus, erstellen Sie eine App und richten Sie dann eine DevOps-Toolchain ein, um Ihre App automatisch bereitzustellen. Sie können den Code auch für eine sofortige Überprüfung herunterladen.

Starter-Kits sind in vielen Kategorien verfügbar, darunter die folgenden:

* [Watson ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/developer/watson/dashboard){:new_window}
* [Apple ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/developer/appledevelopment/dashboard){:new_window}
* [Mobile ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/developer/mobile/dashboard){:new_window}
* [Web-App ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/developer/appservice/dashboard){:new_window}
* [Sicherheit ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/developer/security/dashboard){:new_window}
<!--* [Watson Data Platform developer console](https://console.bluemix.net/developer/dataplatform)-->
* [Finanzen ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/developer/finance/dashboard){:new_window}

## Vorbereitende Schritte

[Registrieren Sie sich ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net){: new_window} für ein {{site.data.keyword.cloud_notm}}-Konto. Geben Sie Ihre E-Mail-Adresse, Ihren Namen, Ihr Unternehmen, Ihre Region und Telefonnummer ein.

Sie benötigen keine Kreditkarte für eine Anmeldung bei einem kostenfreien Konto. Die Angabe einer Kreditkarte ermöglicht jedoch den Zugriff auf zusätzliche Ressourcen und macht es einfacher, alle Angebote von {{site.data.keyword.cloud_notm}} aufzurufen.

## Schritt 1: App erstellen
{: #project}

1. Klicken Sie auf das **Menüsymbol** ![Menüsymbol](../icons/icon_hamburger.svg) > **Web-Apps**.

2. Klicken Sie im Abschnitt **Im Web beginnen** auf **Einstieg**.

3. Wählen Sie das gewünschte Starter-Kit aus, lesen Sie die Details und klicken Sie auf **Erstellen**.

   Um anzuzeigen, was im Starter-Kit enthalten ist, erweitern Sie die Kachel im Dashboard 'App-Service-Starter-Kits'.
   {: tip}

4. Benennen Sie Ihre App, wählen Sie Ihre Sprache aus und klicken Sie auf **Erstellen**.

   Großartiger Start! Sie haben soeben eine App erstellt.

   Klicken Sie auf der Seite mit den App-Details auf **Code herunterladen**. Prüfen Sie die Datei `README.md` in der heruntergeladenen komprimierten Datei, um herauszufinden, ob Sie weitere Aktionen ausführen müssen, um Ihre Starter-App betriebsbereit zu machen.
   {: tip}

## Schritt 2: Ressourcen hinzufügen
{: #addResources}

Die meisten Starter-Kits weisen {{site.data.keyword.cloud_notm}} an, Ressourcen automatisch für Sie bereitzustellen. Sie können auch weitere Ressourcen Ihrer App zuordnen, indem Sie auf der Seite mit den App-Details auf **Ressource hinzufügen** klicken.

Verwenden Sie [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html), um Ihre App lokal zu entwickeln und auszuführen.
{: tip}

## Schritt 3: In {{site.data.keyword.cloud_notm}} bereitstellen
{: #deploy}

Klicken Sie auf der Seite mit den App-Details auf **In Cloud bereitstellen**, wählen Sie eine Bereitstellungsmethode aus (z. B. Kubernetes-Cluster oder Cloud Foundry-App) und klicken Sie auf **Erstellen**.{{site.data.keyword.cloud_notm}} erstellt automatisch eine offene Toolchain mit einem Git-Repository und einer Continuous Delivery-Pipeline. Öffnen Sie die Pipelinekomponente Ihrer neuen Toolchain, um den anfänglichen Erstellungs- und Bereitstellungsprozess zu starten, damit Sie Ihre neue App in wenigen Minuten anzeigen können.

Jetzt sind Sie bereit für die iterative Entwicklung und Continuous Delivery.
