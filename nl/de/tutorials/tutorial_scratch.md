---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-10"

keywords: scratch, developer tools, custom app, app tutorial, verify app running, run app local

subcollection: creating-apps

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

* Installieren Sie die [{{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli), die Docker enthalten. 
* Erstellen Sie ein Docker-Konto, führen Sie die Docker-App aus und melden Sie sich an. Docker muss ausgeführt werden, damit die Buildbefehle funktionieren.
* Wenn Sie vorhaben, Ihre App in {{site.data.keyword.cfee_full}} bereitzustellen, müssen Sie [Ihr {{site.data.keyword.cloud_notm}}-Konto vorbereiten](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## App erstellen
{: #create-scratch}

1. Klicken Sie in Ihrem [{{site.data.keyword.cloud_notm}}-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}) im Apps-Widget auf **App erstellen**.

  Sie können eine angepasste App auch über die Seite [Starter-Kits ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/appservice/starter-kits/) in der {{site.data.keyword.dev_console}} erstellen.
  {: tip}

2. Geben Sie einen Namen für Ihre App ein. Für dieses Lernprogramm geben Sie `CustomProject` ein.
3. Optional können Sie Tags angeben, um Ihre App zu klassifizieren. Weitere Informationen finden Sie in [Mit Tags arbeiten](/docs/resources?topic=resources-tag).
4. Wählen Sie Ihre Sprache und Ihr Framework aus. Einige Starter-Kits sind möglicherweise in nur einer Sprache verfügbar.
5. Wählen Sie Ihren Preisstrukturplan aus. Sie können für dieses Lernprogramm die kostenfreie Option verwenden.
6. Klicken Sie auf **Erstellen**.

## Services hinzufügen (optional)
{: #resources-scratch}

Sie können Services, die Ihre App mit der kognitiven Leistung von Watson funktional erweitern, mobile Services oder Sicherheitsservices hinzufügen. Für dieses Lernprogramm können Sie einen Bereich hinzufügen, um Ihre Daten zu verwalten.

1. Klicken Sie auf der Seite **App-Details** auf **Service hinzufügen**.
2. Wählen Sie den Typ des gewünschten Service aus. Wählen Sie beispielsweise **Daten** > **Weiter** > **Cloudant** > **Weiter** aus.
3. Wählen Sie Ihren Preisstrukturplan aus. Sie können für dieses Lernprogramm die kostenfreie Option verwenden.
4. Klicken Sie auf **Erstellen**.

## App lokal erstellen und ausführen
{: #build-run-scratch}

Sie können die App auch lokal für Tests erstellen, bevor Sie sie in der Cloud bereitstellen.

1. Klicken Sie auf der Seite **App-Details** auf **Code herunterladen** oder **Repository klonen**, um lokal mit Ihrem Code zu arbeiten.
2. Importieren Sie die App in die integrierte Entwicklungsumgebung.
3. Ändern Sie den Code.
4. Richten Sie die [Git-Authentifizierung](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) ein, indem Sie ein persönliches Zugriffstoken hinzufügen.
5. Melden Sie sich bei der {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle (Command Line Interface, CLI) an. Wenn in Ihrer Organisation föderierte Anmeldungen verwendet werden, verwenden Sie die Option `-sso`. Beispiel:

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

Wenn Sie ein Bereitstellungsziel auswählen, wird automatisch eine DevOps-Toolchain für Ihre App erstellt. Die Toolchain enthält eine Delivery Pipeline, die den Bereitstellungsstatus Ihrer App anzeigt. Die neu generierte App wird in ein GitLab-Repository verschoben, das Teil der Toolchain ist.

Durch das Aktivieren einer DevOps-Toolchain wird eine teambasierte Entwicklungsumgebung für Ihre App erstellt. Wenn Sie eine Toolchain erstellen, erstellt der App-Service ein Git-Repository, in dem Sie Quellcode anzeigen, die App klonen und Problemmeldungen erstellen und verwalten können. Darüber hinaus verfügen Sie über Zugriff auf eine dedizierte GitLab-Umgebung  und eine Continuous-Delivery-Pipeline. Diese sind an das Bereitstellungsziel angepasst, das Sie auswählen, ob [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) oder [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Alle über ein {{site.data.keyword.cloud_notm}}-Entwicklerdashboard erstellten Toolchains sind für die automatische Bereitstellung konfiguriert.
{: note}

Führen Sie die folgenden Schritte aus, um Ihr Bereitstellungsziel auszuwählen und Continuous Delivery zu konfigurieren:

1. Klicken Sie auf der Detailseite der App auf **Continuous Delivery konfigurieren**.
2. Wählen Sie ein Bereitstellungsziel aus. Richten Sie Ihr Bereitstellungsziel entsprechend den Anweisungen für das ausgewählte Ziel ein:
  * **Führen Sie die Bereitstellung im [IBM Kubernetes Service](/docs/containers?topic=containers-app)** aus. Mit dieser Option wird ein Cluster mit Hosts erstellt, die als Workerknoten bezeichnet werden, um hoch verfügbare Anwendungscontainer bereitzustellen und zu verwalten. Sie können einen Cluster erstellen oder die Bereitstellung in einem vorhandenen Cluster vornehmen.
  * **Führen Sie die Bereitstellung in Cloud Foundry aus**. Mit dieser Option wird Ihre Cloud-native App bereitgestellt, ohne dass Sie die zugrundeliegende Infrastruktur verwalten müssen. Wenn Ihr Konto über Zugriff auf {{site.data.keyword.cfee_full_notm}} verfügt, können Sie entweder den Bereitstellertyp **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** oder den Bereitstellertyp **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)** auswählen, mit dem Sie isolierte Umgebungen für das Hosting von Cloud Foundry-Anwendungen exklusiv für Ihr Unternehmen erstellen und verwalten können.
  * **Führen Sie die Bereitstellung in einer virtuellen Serverinstanz aus**. Diese Option stellt eine virtuelle Serverinstanz bereit, lädt ein Image, das Ihre App enthält, erstellt eine DevOps-Toolchain und initiiert den ersten Bereitstellungszyklus für Sie.

Nachdem Sie das Bereitstellungsziel ausgewählt und konfiguriert haben, wird auf der Detailseite der App angezeigt, dass Continuous Delivery konfiguriert ist. Wenn Sie das Repository anzeigen möchten, das den Quellcode für Ihre App enthält, klicken Sie auf **Repository anzeigen**.

Wenn Sie Ihre App über die Befehlszeile bereitstellen möchten, verwenden Sie `ibmcloud dev deploy`. Weitere Informationen finden Sie in [Apps über die Befehlszeilenschnittstelle erstellen und bereitstellen](/docs/apps?topic=creating-apps-create-deploy-app-cli).

Weitere Informationen zum Bereitstellen Ihrer App finden Sie unter [Apps bereitstellen](/docs/apps?topic=creating-apps-deploying-apps).

## Ausführung der App verifizieren
{: #verify-scratch}

Nach der Bereitstellung der App verweist Sie die Delivery Pipeline oder die Befehlszeile auf die URL für Ihre App.

1. Klicken Sie in der Toolchain von DevOps auf **Delivery Pipeline** und wählen Sie **Bereitstellungsstage** aus.
2. Klicken Sie auf **Protokolle und Verlauf anzeigen**.
3. Suchen Sie in der Protokolldatei nach der Anwendungs-URL:

   Suchen Sie am Ende der Protokolldatei nach dem Wort `urls` oder `view` (bzw. 'ansehen'). Zum Beispiel wird in der Protokolldatei möglicherweise eine Zeile ähnlich der folgenden angezeigt: `urls: my-app-devhost.mybluemix.net` oder `Status der Anwendung ansehen unter: http://<ipaddress>:<port>/health`.

4. Rufen Sie die URL im Browser auf. Wenn die App ausgeführt wird, wird eine Nachricht anzeigt, die Folgendes enthält: `Congratulations` oder `{"status":"UP"}`.

Wenn Sie die Befehlszeile verwenden, führen Sie den Befehl [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) aus, um die URL der App anzuzeigen. Anschließend rufen Sie die URL in Ihrem Browser auf.

