---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-30"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# App mit einem Starter-Kit erstellen
{: #tutorial-starterkit}

Mit einem Starter-Kit können Sie Ihre Anwendung schnell zum Einsatz bringen und auf zukünftige Entwicklungen vorbereiten. Wählen Sie ein Starter-Kit und eine Programmiersprache aus, erstellen Sie eine App und richten Sie dann eine DevOps-Toolchain ein, um Ihre App automatisch bereitzustellen. Sie können den Code auch für eine sofortige Überprüfung herunterladen.
{: shortdesc}

Sie können eine App aus einer Reihe von Starter-Kits erstellen, einschließlich eines leeren Starter-Kits, wenn Sie die Buildoptionen selbst anpassen möchten. In jedem Fall wird automatisch eine DevOps-Toolchain für die Bereitstellung Ihrer App erstellt. Sie können den Code auch für eine sofortige Überprüfung herunterladen.

{{site.data.keyword.cloud_notm}} verfügt über Entwicklerportale in verschiedenen Interessengebieten (wie Watson, Sicherheit oder Finanzen) oder einem digitalen Vertriebskanal (z. B. mobile oder Web-Apps). Über das Symbol **Menü** ![Menüsymbol](../../icons/icon_hamburger.svg) können Sie auf diese Portale zugreifen.

Jedes Entwicklerportal stellt Starter-Kits zur Verfügung, die für den Schwerpunktbereich des jeweiligen Portals relevant sind. Die Portale bieten konsistente, intuitive Workflows zur minutenschnellen Erstellung einer funktionierenden, produktionsbereiten App.

Starter-Kits sind in vielen Kategorien verfügbar, darunter die folgenden:
* [Watson ](https://{DomainName}/developer/watson/dashboard){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")
* [Apple ](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")
* [Mobile ](https://{DomainName}/developer/mobile/dashboard){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")
* [Web-App ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")
* [Sicherheit ](https://{DomainName}/developer/security/dashboard){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")
* [Finanzen ](https://{DomainName}/developer/finance/dashboard){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")

[Lesen Sie mehr](/docs/apps?topic=creating-apps-starter-kits) zu den Starter-Kits.

## Schritt 1. App erstellen
{: #create-starterkit}

1. Klicken Sie im [{{site.data.keyword.cloud}}-Dashboard](https://{DomainName}){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") auf das Symbol **Menü** ![Menüsymbol](../../icons/icon_hamburger.svg) > **Web-Apps**.

2. Klicken Sie im Abschnitt **Im Web beginnen** auf **Einstieg**.

3. Wählen Sie das gewünschte Starter-Kit aus, lesen Sie die Details und klicken Sie auf **Erstellen**.
    
    Um zu sehen, was im Starter-Kit enthalten ist, erweitern Sie die Kachel im Dashboard [App-Service-Starter-Kits ](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link"). Die Starter-Kit-Option "Anwendung erstellen" kann als leere Starter-App verwendet und an Ihre Bedürfnisse angepasst werden.
    {: tip}

4. Benennen Sie Ihre App, wählen Sie eine Ressourcengruppe aus, geben Sie optional Tags an, wählen Sie die Sprache aus und klicken Sie auf **Erstellen**.
    
    Großartiger Start! Sie haben soeben eine App erstellt.

Klicken Sie auf **Code herunterladen** auf der Seite **App-Details**, um Ihren Code zu überprüfen. Prüfen Sie die Datei `README.md` in der heruntergeladenen komprimierten Datei, um herauszufinden, ob Sie weitere Aktionen ausführen müssen, um Ihre Starter-App betriebsbereit zu machen.
{: tip}

Weitere Informationen finden Sie in den folgenden Abschnitten:
 * [Basis-Web-App mit einem Starter-Kit erstellen](/docs/apps/tutorials?topic=creating-apps-tutorial-webapp)
 * [Mit Tags arbeiten](/docs/resources?topic=resources-tag)

## Schritt 2. Services hinzufügen
{: #resources-starterkit}

Sie können Services, die Ihre App mit der kognitiven Leistung von Watson funktional erweitern, mobile Services oder Sicherheitsservices hinzufügen. Im Rahmen dieses Lernprogramms fügen Sie eine Position für die Verwaltung Ihrer Daten hinzu.

1. Klicken Sie auf der Seite **App-Details** auf **Service hinzufügen**.
2. Wählen Sie den Typ des gewünschten Service aus. Wählen Sie beispielsweise **Daten** > **Weiter** > **Cloudant** > **Weiter** aus.
3. Wählen Sie Ihren Preisstrukturplan aus. Es steht eine kostenfreie Option zur Verfügung, die Sie für dieses Lernprogramm verwenden können.
4. Klicken Sie auf **Erstellen**.

## Schritt 3. In {{site.data.keyword.cloud_notm}} bereitstellen
{: #deploy-starterkit}

Klicken Sie auf **Continuous Delivery konfigurieren** auf der Seite **App-Details**, wählen Sie ein Bereitstellungsziel aus und klicken Sie auf **Erstellen**. {{site.data.keyword.cloud_notm}} erstellt automatisch eine offene Toolchain mit einem Git-Repository und einer Continuous Delivery-Pipeline.

Durch das Aktivieren einer Toolchain wird eine teambasierte Entwicklungsumgebung für Ihre App erstellt. Wenn Sie eine Toolchain erstellen, erstellt der App-Service ein Git-Repository, in dem Sie Quellcode anzeigen, die App klonen und Problemmeldungen erstellen und verwalten können. Darüber hinaus verfügen Sie über Zugriff auf eine dedizierte Git-Laborumgebung und eine Continuous-Delivery-Pipeline. Diese sind an das Bereitstellungsziel angepasst, das Sie auswählen, ob [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) oder [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers).

Nachdem Sie Ihr Bereitstellungsziel ausgewählt haben, öffnen Sie die Pipelinekomponente Ihrer neuen Toolchain, um den anfänglichen Erstellungs- und Bereitstellungsprozess zu starten, damit Sie Ihre neue App innerhalb weniger Minuten anzeigen können.

Alle über ein {{site.data.keyword.cloud_notm}}-Entwicklerdashboard erstellten Toolchains sind für die automatische Bereitstellung konfiguriert.
{: note}

Wenn Sie Ihre App über die Befehlszeile bereitstellen möchten, verwenden Sie `ibmcloud dev deploy`. Weitere Informationen finden Sie in [Apps über die Befehlszeilenschnittstelle erstellen und bereitstellen](/docs/apps?topic=creating-apps-create-deploy-app-cli).

Weitere Informationen zum Bereitstellen Ihrer App finden Sie unter [Apps bereitstellen](/docs/apps?topic=creating-apps-deploying-apps).
