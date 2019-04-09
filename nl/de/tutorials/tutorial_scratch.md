---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# App völlig neu erstellen
{: #tutorial-scratch}

Sie können eine angepasste Anwendung mithilfe von Services und einer Laufzeit völlig neu erstellen.
{: shortdesc}

## Vorbereitende Schritte
{: #prereqs-scratch}

* Installieren Sie die [{{site.data.keyword.dev_cli_long}}](/docs/cli/index.html), die Docker enthalten. 
* Erstellen Sie ein Docker-Konto, führen Sie die Docker-App aus und melden Sie sich an. Docker muss ausgeführt werden, damit die Buildbefehle funktionieren.
* Wenn Sie vorhaben, Ihre App in [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about) bereitzustellen, müssen Sie [Ihr {{site.data.keyword.cloud_notm}}-Konto vorbereiten](/docs/cloud-foundry/prepare-account.html#prepare).

## App erstellen
{: #create-scratch}

1. Klicken Sie in Ihrem [{{site.data.keyword.cloud_notm}}-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com) im Apps-Widget auf **App erstellen**.

  Sie können eine angepasste App auch über die Seite [Starter-Kits ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/appservice/starter-kits/) in der {{site.data.keyword.dev_console}} erstellen.
  {: tip}

2. Geben Sie einen Namen für Ihre App ein. Für dieses Lernprogramm geben Sie `CustomProject` ein.
3. Geben Sie einen eindeutigen Hostnamen ein, z. B. `abc-devhost`. Der Hostname wird für die Route Ihrer App verwendet, z. B. `abc-devhost.cloud.ibm.com`.
4. Optional können Sie Tags angeben, um Ihre App zu klassifizieren. Weitere Informationen finden Sie in [Mit Tags arbeiten](/docs/resources/tagging_resources.html#tag).
5. Wählen Sie Ihre Sprache und Ihr Framework aus. Einige Starter-Kits sind möglicherweise in nur einer Sprache verfügbar.
6. Wählen Sie Ihren Preisstrukturplan aus. Sie können für dieses Lernprogramm die kostenfreie Option verwenden.
7. Klicken Sie auf **Erstellen**.

## Ressourcen hinzufügen (optional)
{: #resources-scratch}

Sie können Ressourcen, die Ihre App mit der kognitiven Leistung von Watson funktional erweitern, mobile Services oder Sicherheitsservices hinzufügen. Für dieses Lernprogramm können Sie einen Bereich hinzufügen, um Ihre Daten zu verwalten.

1. Wählen Sie im App-Service-Fenster **Ressource hinzufügen** aus.
2. Wählen Sie den Typ des gewünschten Service aus. Wählen Sie beispielsweise **Daten** > **Weiter** > **Cloudant** > **Weiter** aus.
3. Wählen Sie Ihren Preisstrukturplan aus. Sie können für dieses Lernprogramm die kostenfreie Option verwenden.
4. Klicken Sie auf **Erstellen**.

## App lokal erstellen und ausführen
{: #build-run-scratch}

Sie können die App auch lokal für Tests erstellen, bevor Sie sie in der Cloud bereitstellen.

1. Klicken Sie im App-Service-Fenster auf **Code herunterladen** oder **Repository klonen**, um lokal mit Ihrem Code zu arbeiten.
2. Importieren Sie die App in die integrierte Entwicklungsumgebung.
3. Ändern Sie den Code.
4. Richten Sie die [Git-Authentifizierung](/docs/services/ContinuousDelivery/git_working.html#git_authentication) ein, indem Sie ein persönliches Zugriffstoken hinzufügen.
5. Melden Sie sich bei der {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle (Command Line Interface, CLI) an. Wenn in Ihrer Organisation föderierte Anmeldungen verwendet werden, wählen Sie die Option `-sso` aus, z. B.:

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Führen Sie den folgenden Befehl aus, um Ihre Organisations- und Bereichsziele festzulegen.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. Führen Sie den folgenden Befehl aus, um die Berechtigungsnachweise abzurufen.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Stellen Sie sicher, dass Docker aktiv ist, und führen Sie den folgenden Befehl aus, um Ihre App in einem lokalen Entwicklungscontainer aus dem Verzeichnis zu erstellen.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Führen Sie den folgenden Befehl aus, um Ihre App in einem lokalen Entwicklungscontainer auszuführen.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. Rufen Sie `http://localhost:3000` in Ihrem Browser auf. Abhängig von der ausgewählten Laufzeit kann die Portnummer davon abweichen.

## App bereitstellen
{: #deploy-scratch}

Für die Bereitstellung der App in {{site.data.keyword.cloud_notm}} stehen mehrere Möglichkeiten zur Verfügung, eine DevOps-Toolchain ist jedoch für die Bereitstellung von Produktions-Apps am besten geeignet. Mit einer DevOps-Toolchain können Sie ohne großen Aufwand Bereitstellungen in vielen Umgebungen automatisieren und schnell Überwachungs-, Protokollierungs- und Alert-Services hinzufügen, die Sie bei der Verwaltung Ihrer ständig weiterentwickelten App unterstützen.

Durch das Aktivieren einer Toolchain wird eine teambasierte Entwicklungsumgebung für Ihre App erstellt. Wenn Sie eine Toolchain erstellen, erstellt der App-Service ein Git-Repository, in dem Sie Quellcode anzeigen, die App klonen und Problemmeldungen erstellen und verwalten können. Darüber hinaus verfügen Sie über Zugriff auf eine dedizierte Git-Laborumgebung und eine Continuous-Delivery-Pipeline. Diese sind an die ausgewählte Bereitstellungsumgebung angepasst, die Sie auswählen, ob [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) oder [virtueller Server](/docs/vsi/vsi_index.html).

Alle über ein {{site.data.keyword.cloud_notm}}-Entwicklerdashboard erstellten Toolchains sind für die automatische Bereitstellung konfiguriert.
{: note}

### Mit DevOps-Toolchain manuell bereitstellen

Bei einer ordnungsgemäß konfigurierten Toolchain startet mit jedem Vorgang der Zusammenführung mit dem Masterzweig in Ihrem Repository ein Erstellungs-/Bereitstellungszyklus. 

Sie können Ihre App auch manuell aus Ihrer DevOps-Toolchain heraus bereitstellen:

1. Klicken Sie im Fenster mit den App-Details auf **Toolchain anzeigen**.
2. Klicken Sie auf **Delivery Pipeline**. Hier können Sie Builds starten, die Bereitstellung verwalten sowie Protokolle und den Verlauf anzeigen.

Continuous Delivery ist für manche Anwendungen aktiviert. Sie können Continuous Delivery aktivieren, um Builds, Tests und Bereitstellungen über die Delivery Pipeline und GitHub zu automatisieren.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Build und Bereitstellung:](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy) mit Continuous Delivery.
* [Erstellen von Toolchains](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started) aus einer Vorlage.

### Automatische Bereitstellung mit einer DevOps-Toolchain

1. Klicken Sie auf der Seite "App-Details" auf **In Cloud bereitstellen**.
2. Wählen Sie eine Bereitstellungsmethode aus. Richten Sie Ihre Bereitstellungsmethode entsprechend den Anweisungen für die ausgewählte Methode ein:
  * **Führen Sie die Bereitstellung in [Kubernetes](/docs/apps/deploying/containers.html#containers)** aus. Mit dieser Option wird ein Cluster mit Hosts erstellt, die als Workerknoten bezeichnet werden, um hoch verfügbare Anwendungscontainer bereitzustellen und zu verwalten. Sie können einen Cluster erstellen oder die Bereitstellung in einem vorhandenen Cluster vornehmen.
  * **Führen Sie die Bereitstellung in Cloud Foundry aus**. Mit dieser Option wird Ihre Cloud-native App bereitgestellt, ohne dass Sie die zugrundeliegende Infrastruktur verwalten müssen. Wenn Ihr Konto über Zugriff auf {{site.data.keyword.cfee_full_notm}} verfügt, können Sie entweder den Bereitstellertyp **[Public Cloud](/docs/cloud-foundry-public/about-cf.html#about-cf)** oder den Bereitstellertyp **[Enterprise Environment](/docs/cloud-foundry-public/cfee.html#cfee)** auswählen, mit dem Sie isolierte Umgebungen für das Hosting von Cloud Foundry-Anwendungen exklusiv für Ihr Unternehmen erstellen und verwalten können.
  * **Führen Sie die Bereitstellung in einem [virtuellen Server](/docs/apps/vsi-deploy.html#vsi-deploy)** aus. Diese Option stellt eine virtuelle Serverinstanz bereit, lädt ein Image, das Ihre App enthält, erstellt eine DevOps-Toolchain und initiiert den ersten Bereitstellungszyklus für Sie.

Durch die Bereitstellung der App in der Cloud im letzten Schritt wird automatisch eine Toolchain erstellt. Die Toolchain erstellt ein Git-Repository für Ihre App, in dem Sie den Code finden können. 

### Bereitstellung: {{site.data.keyword.dev_cli_short}} verwenden
{: #deploy-scratch-cli}

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

## Ausführung der App verifizieren
{: #verify-scratch}

Nach der Bereitstellung der App verweist Sie die Delivery Pipeline oder die Befehlszeile auf die URL für Ihre App.

1. Klicken Sie in der Toolchain von DevOps auf **Delivery Pipeline** und wählen Sie **Bereitstellungsstage** aus.
2. Klicken Sie auf **Protokolle und Verlauf anzeigen**.
3. Suchen Sie in der Protokolldatei nach der Anwendungs-URL:

    Suchen Sie am Ende der Protokolldatei nach dem Wort `urls` oder `view`. Zum Beispiel wird in der Protokolldatei eine Zeile angezeigt, die `urls: my-app-devhost.cloud.ibm.com` ähnelt, oder `Status der Anwendung ansehen unter: http://<ipaddress>:<port>/health`.

4. Rufen Sie die URL im Browser auf. Wenn die App ausgeführt wird, wird eine Nachricht anzeigt, die Folgendes enthält: `Congratulations` oder `{"status":"UP"}`.

Wenn Sie die Befehlszeile verwenden, führen Sie den Befehl [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) aus, um die URL der App anzuzeigen. Anschließend rufen Sie die URL in Ihrem Browser auf.
