---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# App mit einem Starter-Kit erstellen
{: #tutorial-starterkit}

Mit einem Starter-Kit können Sie Ihre App schnell zum Einsatz bringen und auf zukünftige Entwicklungen vorbereiten. Wählen Sie ein Starter-Kit und eine Programmiersprache aus, erstellen Sie eine App und richten Sie dann eine DevOps-Toolchain ein, um Ihre App automatisch bereitzustellen. Sie können den Code auch für eine sofortige Überprüfung herunterladen.
{: shortdesc}

Sie können eine App aus einer Reihe von Starter-Kits erstellen, einschließlich eines leeren Starter-Kits, wenn Sie die Buildoptionen selbst anpassen möchten. In jedem Fall wird automatisch eine DevOps-Toolchain für die Bereitstellung Ihrer App erstellt. Sie können den Code auch für eine sofortige Überprüfung herunterladen.

Starter-Kits sind in vielen Kategorien verfügbar, darunter die folgenden:
* [Watson ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/watson/dashboard){:new_window}
* [Apple ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/appledevelopment/dashboard){:new_window}
* [Mobile ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/mobile/dashboard){:new_window}
* [Web-App ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/appservice/dashboard){:new_window}
* [Sicherheit ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/security/dashboard){:new_window}
* [Finanzen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/finance/dashboard){:new_window}

## Schritt 1. App erstellen
{: #create-starterkit}

1. Klicken Sie im [{{site.data.keyword.cloud}}-Dashboard](https://{DomainName}) auf das Symbol **Menü** ![Menüsymbol](../../icons/icon_hamburger.svg) > **Web-Apps**.

2. Klicken Sie im Abschnitt **Im Web beginnen** auf **Einstieg**.

3. Wählen Sie das gewünschte Starter-Kit aus, lesen Sie die Details und klicken Sie auf **Erstellen**.
    
    Um zu sehen, was im Starter-Kit enthalten ist, erweitern Sie die Kachel im Dashboard [App-Service-Starter-Kits ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/appservice/starter-kits){:new_window}. Die Starter-Kit-Option "Anwendung erstellen" kann als leere Starter-App verwendet und an Ihre Bedürfnisse angepasst werden.
    {: tip}

4. Benennen Sie Ihre App, wählen Sie eine Ressourcengruppe aus, geben Sie optional Tags an, wählen Sie die Sprache aus und klicken Sie auf **Erstellen**.
    
    Großartiger Start! Sie haben soeben eine App erstellt.

Klicken Sie auf der Seite "App-Details" auf **Code herunterladen**. Prüfen Sie die Datei `README.md` in der heruntergeladenen komprimierten Datei, um herauszufinden, ob Sie weitere Aktionen ausführen müssen, um Ihre Starter-App betriebsbereit zu machen.
{: tip}

Weitere Informationen finden Sie in den folgenden Abschnitten:
 * [Basis-Web-App mit einem Starter-Kit erstellen](/docs/apps/tutorials/tutorial_web.html#tutorial-webapp)
 * [Mit Tags arbeiten](/docs/resources/tagging_resources.html#tag)

## Schritt 2. Ressourcen hinzufügen
{: #resources-starterkit}

Sie können Ressourcen, die Ihre App mit der kognitiven Leistung von Watson funktional erweitern, mobile Services oder Sicherheitsservices hinzufügen. Im Rahmen dieses Lernprogramms fügen Sie eine Position für die Verwaltung Ihrer Daten hinzu.

1. Wählen Sie im Fenster des App-Service **Ressource hinzufügen** aus.
2. Wählen Sie den Typ des gewünschten Service aus. Wählen Sie beispielsweise **Daten** > **Weiter** > **Cloudant** > **Weiter** aus.
3. Wählen Sie Ihren Preisstrukturplan aus. Es steht eine kostenfreie Option zur Verfügung, die Sie für dieses Lernprogramm verwenden können.
4. Klicken Sie auf **Erstellen**.

## Schritt 3. In {{site.data.keyword.cloud_notm}} bereitstellen
{: #deploy-starterkit}

Klicken Sie auf der Seite "App-Details" auf **In Cloud bereitstellen**, wählen Sie eine Bereitstellungsumgebung aus und klicken Sie auf **Erstellen**. {{site.data.keyword.cloud_notm}} erstellt automatisch eine offene Toolchain mit einem Git-Repository und einer Continuous Delivery-Pipeline.

Durch das Aktivieren einer Toolchain wird eine teambasierte Entwicklungsumgebung für Ihre App erstellt. Wenn Sie eine Toolchain erstellen, erstellt der App-Service ein Git-Repository, in dem Sie Quellcode anzeigen, die App klonen und Problemmeldungen erstellen und verwalten können. Darüber hinaus verfügen Sie über Zugriff auf eine dedizierte Git-Laborumgebung und eine Continuous-Delivery-Pipeline. Diese sind an die ausgewählte Bereitstellungsumgebung angepasst, die Sie auswählen, ob [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) oder [Virtual Server (VSI)](/docs/vsi/vsi_index.html).

Nachdem Sie Ihre Bereitstellungsumgebung ausgewählt haben, öffnen Sie die Pipelinekomponente Ihrer neuen Toolchain, um den anfänglichen Erstellungs- und Bereitstellungsprozess zu starten, damit Sie Ihre neue App innerhalb weniger Minuten anzeigen können.

Alle über ein {{site.data.keyword.cloud_notm}}-Entwicklerdashboard erstellten Toolchains sind für die automatische Bereitstellung konfiguriert.
{: note}

Wenn Sie Ihre App über die Befehlszeile bereitstellen möchten, verwenden Sie `ibmcloud dev deploy`. Weitere Informationen finden Sie in [Apps über die Befehlszeilenschnittstelle erstellen und bereitstellen](/docs/apps/create-deploy-cli.html#create-deploy-app-cli).
