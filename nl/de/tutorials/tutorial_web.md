---

copyright:
  years: 2015, 2019
lastupdated: "2019-04-02"

keywords: basic web app tutorial, apps, web app, starter kit, App Service, developer tools, DevOps toolchain, basic app, create basic web app

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Basis-Web-App mit einem Starter-Kit erstellen
{: #tutorial-webapp}

{{site.data.keyword.cloud}} stellt eine Reihe von Starter-Kits bereit, die Ihnen einen schnellen Einstieg in die Codierung ermöglichen. Wählen Sie in den App-Service-Starter-Kits eine Sprache, ein Framework und Tools aus, um mit der Arbeit mit einer vorkonfigurierten angepassten Anwendung zu beginnen. In diesem Lernprogramm werden die Schritte beschrieben, die erforderlich sind, um die benötigten Tools zu installieren, um die App anschließend zu erstellen und lokal auszuführen und um die App in der Cloud bereitzustellen.
{: shortdesc}

## Schritt 1. Tools installieren
{: #prereqs-webapp}

Installieren Sie die [Entwicklertools](/docs/cli?topic=cloud-cli-ibmcloud-cli).

Docker wird als Teil der Entwicklertools installiert. Docker muss ausgeführt werden, damit die Buildbefehle funktionieren. Sie müssen ein Docker-Konto erstellen, die Docker-App ausführen und sich anmelden.

## Schritt 2. Starter-Kit auswählen
{: #create-webapp}

Starter-Kits sind in der {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}} in vielen Sprachen und Frameworks verfügbar. Wählen Sie als Einstieg die Sprache aus, die für Ihr Projekt am besten geeignet ist.

1. Wählen Sie auf der Seite [Starter-Kits ](https://{DomainName}/developer/appservice/starter-kits/){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") in der {{site.data.keyword.dev_console}} ein Starter-Kit für Ihre Sprache aus.
2. Geben Sie den App-Namen und einen eindeutigen Hostnamen ein, z. B. `abc-devhost`. Dieser Hostname gibt die Route Ihrer App an: `abc-devhost.mybluemix.net`.
3. Optional. Geben Sie Tags an, um Ihre App zu klassifizieren. Weitere Informationen finden Sie in [Mit Tags arbeiten](/docs/resources?topic=resources-tag).
4. Wählen Sie Ihre Sprache und Ihr Framework aus. Einige Starter-Kit sind möglicherweise nur ein einer Sprache verfügbar.
5. Wählen Sie Ihren Preisstrukturplan aus. Es steht eine kostenfreie Option zur Verfügung, die Sie für dieses Lernprogramm verwenden können.
6. Klicken Sie auf **Erstellen**.

Die gemeinsam genutzte Standarddomäne ist `mybluemix.net`, aber `appdomain.cloud` ist eine weitere Domänenoption, die Sie verwenden können. Weitere Informationen zur Migration auf `appdomain.cloud` finden Sie im Abschnitt zum [Aktualisieren Ihrer Domäne](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).
{: tip}

## Schritt 3. Services hinzufügen (optional)
{: #resources-webapp}

Sie können Services, die Ihre App mit der kognitiven Leistung von Watson funktional erweitern, mobile Services oder Sicherheitsservices hinzufügen. Im Rahmen dieses Lernprogramms fügen Sie eine Position für die Verwaltung Ihrer Daten hinzu.

1. Klicken Sie auf der Seite **App-Details** auf **Services hinzufügen**.
2. Wählen Sie den Typ des gewünschten Service aus. Wählen Sie beispielsweise **Daten** > **Weiter** > **Cloudant** > **Weiter** aus.
3. Wählen Sie Ihren Preisstrukturplan aus. Es steht eine kostenfreie Option zur Verfügung, die Sie für dieses Lernprogramm verwenden können.
4. Klicken Sie auf **Erstellen**.

## Schritt 4. DevOps-Toolchain erstellen
{: #toolchain-webapp}

Durch das Aktivieren einer Toolchain wird eine teambasierte Entwicklungsumgebung für Ihre App erstellt. Wenn Sie eine Toolchain erstellen, erstellt der App-Service ein Git-Repository, in dem Sie Quellcode anzeigen, die App klonen und Problemmeldungen erstellen und verwalten können. Darüber hinaus verfügen Sie über Zugriff auf eine dedizierte Git-Laborumgebung und eine Continuous-Delivery-Pipeline. Diese sind an das Bereitstellungsziel angepasst, das Sie auswählen, ob [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) oder [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers).

Continuous Delivery ist für manche Anwendungen aktiviert. Sie können Continuous Delivery aktivieren, um Builds, Tests und Bereitstellungen über die Delivery Pipeline und GitHub zu automatisieren.

Klicken Sie auf **Continuous Delivery konfigurieren** auf der Seite **App-Details**, wählen Sie ein Bereitstellungsziel aus und klicken Sie auf **Erstellen**. {{site.data.keyword.cloud_notm}} erstellt automatisch eine offene Toolchain mit einem Git-Repository und einer Continuous Delivery-Pipeline.

Nachdem Sie Ihr Bereitstellungsziel ausgewählt haben, öffnen Sie die Pipelinekomponente Ihrer neuen Toolchain, um den anfänglichen Erstellungs- und Bereitstellungsprozess zu starten, damit Sie Ihre neue App innerhalb weniger Minuten anzeigen können.

Weitere Informationen finden Sie unter [Toolchains erstellen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## Schritt 5. App erstellen und lokal ausführen
{: #build-run-webapp}

Durch die Bereitstellung der App in der Cloud im letzten Schritt wurde eine Toolchain erstellt. Eine Toolchain erstellt ein Git-Repository für die App, in dem Sie den Code anzeigen können. Führen Sie diese Schritte aus, um auf Ihr Repository zuzugreifen. Sie können die App zu Testzwecken lokal erstellen, bevor Sie sie in der Cloud bereitstellen.

1. Klicken Sie auf der Seite **App-Details** auf **Code herunterladen** oder **Repository klonen**, um lokal mit Ihrem Code zu arbeiten.
2. Importieren Sie die App in die integrierte Entwicklungsumgebung.
3. Ändern Sie den Code.
4. Richten Sie die [Git-Authentifizierung](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) ein, indem Sie ein persönliches Zugriffstoken hinzufügen.
5. Melden Sie sich bei der {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle an. Wenn in Ihrer Organisation föderierte Anmeldungen verwendet werden, wählen Sie die Option `-sso` aus.

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Legen Sie die Zielorganisation und den Zielbereich fest.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. Rufen Sie die Berechtigungsnachweise ab.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Stellen Sie sicher, dass Docker ausgeführt wird, und erstellen Sie die App in einem lokalen Entwicklungscontainer im Verzeichnis.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Führen Sie die App in einem lokalen Entwicklungscontainer aus.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. Öffnen Sie in Ihrem Browser diese Adresse: `http://localhost:3000`. Abhängig von der ausgewählten Laufzeit kann die Portnummer davon abweichen.

## Schritt 6. App bereitstellen
{: #deploy-webapp}

### Bereitstellung: Toolchain verwenden
{: #deploy-webapp-toolchain}

Für die Bereitstellung der App in {{site.data.keyword.cloud_notm}} stehen mehrere Möglichkeiten zur Verfügung, eine DevOps-Toolchain ist jedoch für die Bereitstellung von Produktions-Apps am besten geeignet. Mit einer DevOps-Toolchain können Sie ohne großen Aufwand Bereitstellungen in vielen Umgebungen automatisieren und schnell Überwachungs-, Protokollierungs- und Alert-Services hinzufügen, die Sie bei der Verwaltung Ihrer ständig weiterentwickelten App unterstützen.

Bei einer ordnungsgemäß konfigurierten Toolchain startet mit jedem Vorgang der Zusammenführung mit dem Masterzweig in Ihrem Repository ein Erstellungs-/Bereitstellungszyklus. Alle über ein {{site.data.keyword.cloud_notm}}-Entwicklerdashboard erstellten Toolchains sind für die automatische Bereitstellung konfiguriert.

Sie können Ihre App auch manuell aus Ihrer DevOps-Toolchain heraus bereitstellen:

1. Klicken Sie auf der Seite **App-Details** auf **Toolchain anzeigen**.
2. Klicken Sie auf **Delivery Pipeline**. Hier können Sie Builds starten, die Bereitstellung verwalten sowie Protokolle und den Verlauf anzeigen.

Weitere Informationen finden Sie unter [Erstellen und bereitstellen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

### Bereitstellung: {{site.data.keyword.dev_cli_short}} verwenden
{: #deploy-webapp-cli}

Geben Sie den folgenden Befehl ein, um Ihre App in Cloud Foundry bereitzustellen:
```
ibmcloud dev deploy
```
{: pre}

Geben Sie den folgenden Befehl ein, um Ihre App in einem Kubernetes-Cluster bereitzustellen:
```
ibmcloud dev deploy --target <container>
```
{: pre}

## Schritt 7. Ausführung der App verifizieren
{: #verify-webapp}

Nach der Bereitstellung der App verweist Sie die Delivery Pipeline oder die Befehlszeile auf die URL für Ihre App.

1. Klicken Sie in der Toolchain von DevOps auf **Delivery Pipeline** und wählen Sie **Bereitstellungsstage** aus.
2. Klicken Sie auf **Protokolle und Verlauf anzeigen**.
3. Suchen Sie in der Protokolldatei nach der Anwendungs-URL:

    Suchen Sie am Ende der Protokolldatei nach dem Wort `urls` oder `view` (bzw. 'ansehen'). Zum Beispiel wird in der Protokolldatei möglicherweise eine Zeile ähnlich der folgenden angezeigt: `urls: my-app-devhost.mybluemix.net` oder `Status der Anwendung ansehen unter: http://<ipaddress>:<port>/health`.

4. Rufen Sie die URL im Browser auf. Wenn die App ausgeführt wird, wird eine Nachricht anzeigt, die Folgendes enthält: `Congratulations` oder `{"status":"UP"}`.

Wenn Sie die Befehlszeile verwenden, führen Sie den Befehl [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) aus, um die URL der App anzuzeigen. Anschließend rufen Sie die URL in Ihrem Browser auf.
