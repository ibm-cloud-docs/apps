---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-11-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# App völlig neu erstellen
{: #tutorial}

Sie können eine angepasste Anwendung mithilfe von Services und einer Laufzeit völlig neu erstellen. Sie erfahren, wie die erforderlichen Tools installiert werden, wie die App lokal erstellt und ausgeführt wird und wie sie in der Cloud bereitgestellt wird.
{: shortdesc}

## Schritt 1. Tools installieren
{: #install-tools}

Installieren Sie die [{{site.data.keyword.dev_cli_long}}](/docs/cli/index.html).

Docker wird als Teil der Developer Tools installiert. Docker muss ausgeführt werden, damit die Buildbefehle funktionieren. Sie müssen ein Docker-Konto erstellen, die Docker-App ausführen und sich anmelden.

## Schritt 2. App völlig neu erstellen
{: #create-devex}

Erstellen Sie eine angepasste App im {{site.data.keyword.cloud}}-Dashboard:

1. Wählen Sie im [{{site.data.keyword.cloud}}-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}) **Erstellen** aus, um eine angepasste Anwendung zu erstellen.

  Sie können eine angepasste App auch über die Seite [Starter-Kits ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/appservice/starter-kits/) im {{site.data.keyword.dev_console}} erstellen. Wählen Sie zum Erstellen einer angepassten Anwendung **Erstellen** aus.
  {: tip}

2. Geben Sie Ihren App-Namen ein. Verwenden Sie im Rahmen dieses Lernprogramms `CustomProject`.
3. Geben Sie einen eindeutigen Hostnamen ein, z. B. `abc-devhost`. Dieser Hostname gibt die Route Ihrer App an: `abc-devhost.mybluemix.net`.
4. Wählen Sie Ihre Sprache und Ihr Framework aus. Einige Starter-Kit sind möglicherweise nur ein einer Sprache verfügbar.
5. Wählen Sie Ihren Preisstrukturplan aus. Sie können für dieses Lernprogramm die kostenfreie Option verwenden.
6. Klicken Sie auf **Erstellen**.

## Schritt 3. Ressourcen hinzufügen (optional)
{: #add-services}

Sie können Ressourcen, die Ihre App mit der kognitiven Leistung von Watson funktional erweitern, mobile Services oder Sicherheitsservices hinzufügen. Im Rahmen dieses Lernprogramms fügen Sie eine Position für die Verwaltung Ihrer Daten hinzu.

1. Wählen Sie im App-Service-Fenster **Ressource hinzufügen** aus.
2. Wählen Sie den Typ des gewünschten Service aus. Wählen Sie beispielsweise **Daten** > **Weiter** > **Cloudant** > **Weiter** aus.
3. Wählen Sie Ihren Preisstrukturplan aus. Sie können für dieses Lernprogramm die kostenfreie Option verwenden.
4. Klicken Sie auf **Erstellen**.

## Schritt 4. Mit einer DevOps-Toolchain bereitstellen
{: #add-toolchain}

Durch das Aktivieren einer Toolchain wird eine teambasierte Entwicklungsumgebung für Ihre App erstellt. Wenn Sie eine Toolchain erstellen, erstellt der App-Service ein Git-Repository, in dem Sie Quellcode anzeigen, die App klonen und Problemmeldungen erstellen und verwalten können. Darüber hinaus verfügen Sie über Zugriff auf eine dedizierte Git-Laborumgebung und eine Continuous-Delivery-Pipeline. Diese sind an die ausgewählte Bereitstellungsplattform - z. B. Kubernetes oder Cloud Foundry - angepasst.

Continuous Delivery ist für manche Anwendungen aktiviert. Sie können Continuous Delivery aktivieren, um Builds, Tests und Bereitstellungen über die Delivery Pipeline und GitHub zu automatisieren.

1. Klicken Sie auf der Seite mit den App-Details auf **In Cloud bereitstellen**.
2. Wählen Sie eine Bereitstellungsmethode aus. Richten Sie Ihre Bereitstellungsmethode entsprechend den Anweisungen für die ausgewählte Methode ein:
  * Führen Sie die Bereitstellung in einem Kubernetes-Cluster aus. Erstellen Sie einen Cluster mit Hosts, die als Workerknoten bezeichnet werden, um hoch verfügbare Anwendungscontainer bereitzustellen und zu verwalten. Sie können ein Cluster erstellen oder in einem vorhandenen Cluster bereitstellen.
  * Führen Sie die Bereitstellung mit Cloud Foundry aus. Hier müssen Sie die zugrunde liegende Infrastruktur nicht verwalten.
  * Führen Sie die Bereitstellung in einer Virtual Server-Instanz aus.

Durch die Bereitstellung der App in der Cloud im letzten Schritt wird automatisch eine Toolchain erstellt. Die Toolchain erstellt ein Git-Repository für Ihre App, in dem Sie den Code finden können. Weitere Informationen finden Sie unter [Toolchains erstellen](/docs/services/ContinuousDelivery/toolchains_working.html).

## Schritt 5. App erstellen und lokal ausführen
{: #build-run}

Sie können die App zu Testzwecken auch lokal erstellen, bevor Sie sie mit Push-Operation in die Cloud übertragen.

1. Klicken Sie im App-Service-Fenster auf **Code herunterladen** oder **Repository klonen**, um lokal mit Ihrem Code zu arbeiten.
2. Importieren Sie die App in die integrierte Entwicklungsumgebung.
3. Ändern Sie den Code.
4. Richten Sie die [Git-Authentifizierung](/docs/services/ContinuousDelivery/git_working.html#git_authentication) ein, indem Sie ein persönliches Zugriffstoken hinzufügen.
5. Melden Sie sich bei der {{site.data.keyword.Bluemix}}-Befehlszeilenschnittstelle an. Wenn in Ihrer Organisation föderierte Anmeldungen verwendet werden, wählen Sie die Option `-sso` aus.

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
{: #deploy}

### Mit einer DevOps-Toolchain bereitstellen

Für die Bereitstellung der App in {{site.data.keyword.cloud_notm}} stehen mehrere Möglichkeiten zur Verfügung, eine DevOps-Toolchain ist jedoch für die Bereitstellung von Produktions-Apps am besten geeignet. Mit einer DevOps-Toolchain können Sie ohne großen Aufwand Bereitstellungen in vielen Umgebungen automatisieren und schnell Überwachungs-, Protokollierungs- und Alert-Services hinzufügen, die Sie bei der Verwaltung Ihrer ständig weiterentwickelten App unterstützen.

Bei einer ordnungsgemäß konfigurierten Toolchain startet mit jedem Vorgang der Zusammenführung mit dem Masterzweig in Ihrem Repository ein Erstellungs-/Bereitstellungszyklus. Alle über ein {{site.data.keyword.cloud_notm}} Developer-Dashboard erstellten Toolchains sind für die automatische Bereitstellung konfiguriert.

Sie können Ihre App auch manuell aus Ihrer DevOps-Toolchain heraus bereitstellen:

1. Klicken Sie im Fenster mit den App-Details auf **Toolchain anzeigen**.
2. Klicken Sie auf **Delivery Pipeline**. Hier können Sie Builds starten, die Bereitstellung verwalten sowie Protokolle und den Verlauf anzeigen.

Weitere Informationen finden Sie unter [Erstellen und bereitstellen](/docs/services/ContinuousDelivery/pipeline_build_deploy.html).

### Bereitstellung: {{site.data.keyword.dev_cli_short}} verwenden

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
{: #verify}

Nach der Bereitstellung der App verweist die DevOps-Pipeline bzw. die Befehlszeile auf die URL für Ihre App, z. B. `abc-devhost.mybluemix.net`. Rufen Sie diese URL im Browser auf.
