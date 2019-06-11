---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-06"

keywords: apps, deploy, deploying apps, toolchain, cli, cloud, devops, deployment, git, push

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Apps bereitstellen
{: #deploying-apps}

Sie können Ihre App mithilfe einer DevOps-Toolchain in {{site.data.keyword.cloud}} bereitstellen. Mit einer DevOps-Toolchain können Sie Bereitstellungen in vielen Umgebungen automatisieren und schnell Überwachungs-, Protokollierungs-, Insights- und Alert-Services hinzufügen, die Sie bei der Verwaltung Ihrer ständig weiterentwickelten App unterstützen. Sie können Continuous Delivery für Ihre App konfigurieren und Ihre App bereitstellen, indem Sie entweder die {{site.data.keyword.cloud_notm}}-Webkonsole oder die Befehlszeilenschnittstelle verwenden.
{: shortdesc}

Eine DevOps-Toolchain stellt eine teambasierte Entwicklungsumgebung für Ihre App zur Verfügung. Wenn Sie eine Toolchain erstellen, erstellt der App-Service ein Git-Repository, in dem Sie Quellcode anzeigen, die App klonen und Problemmeldungen erstellen und verwalten können. Darüber hinaus verfügen Sie über Zugriff auf eine dedizierte GitLab-Umgebung  und eine Continuous-Delivery-Pipeline. Diese sind an das Bereitstellungsziel angepasst, das Sie auswählen, ob [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) oder [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Alle über das {{site.data.keyword.cloud_notm}}-Entwicklerdashboard erstellten Toolchains sind für die automatische Bereitstellung konfiguriert.
{: note}

## Verwendung der {{site.data.keyword.cloud_notm}}-Konsole
{: deploy-console}

{{site.data.keyword.cloud_notm}} bietet eine Webkonsole, in der Sie Continous Delivery konfigurieren und Ihre App mithilfe einer DevOps-Toolchain  bereitstellen können.

### Vorbereitende Schritte
{: deploy-console-before}

Zur Vorbereitung müssen Sie mit dem [{{site.data.keyword.cloud_notm}}-Dashboard](https://{DomainName}){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") Ihre [App erstellen](/docs/apps?topic=creating-apps-tutorial-getting-started#create-getting-started) und [Services hinzufügen](/docs/apps?topic=creating-apps-tutorial-getting-started#resources-getting-started).

### App automatisch bereitstellen
{: deploy-console-auto}

1. Klicken Sie auf der Seite **App-Details** auf **Continuous Delivery konfigurieren**.
2. Wählen Sie ein Bereitstellungsziel aus. Richten Sie Ihr Bereitstellungsziel entsprechend den Anweisungen für das ausgewählte Ziel ein:
  * **Führen Sie die Bereitstellung im IBM Kubernetes Service aus**. Mit dieser Option wird ein Cluster mit Hosts erstellt, die als Workerknoten bezeichnet werden, um hoch verfügbare Anwendungscontainer bereitzustellen und zu verwalten. Sie können einen Cluster erstellen oder die Bereitstellung in einem vorhandenen Cluster vornehmen. Weitere Informationen finden Sie unter [Apps in Kubernetes-Clustern bereitstellen](/docs/containers?topic=containers-app).
  * **Führen Sie die Bereitstellung in Cloud Foundry aus**. Mit dieser Option wird Ihre Cloud-native App bereitgestellt, ohne dass Sie die zugrundeliegende Infrastruktur verwalten müssen. Wenn Ihr Konto über Zugriff auf {{site.data.keyword.cfee_full_notm}} verfügt, können Sie entweder den Bereitstellertyp **Public Cloud** oder den Bereitstellertyp **Enterprise Environment** auswählen, mit dem Sie isolierte Umgebungen für das Hosting von Cloud Foundry-Anwendungen exklusiv für Ihr Unternehmen erstellen und verwalten können. Zusätzliche Angaben enthalten die Abschnitte [Apps in Cloud Foundry Public bereitstellen](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps) und [Apps in {{site.data.keyword.cfee_full_notm}} bereitstellen](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps).
  * **Führen Sie die Bereitstellung in einer virtuellen Serverinstanz aus**. Diese Option stellt eine virtuelle Serverinstanz bereit, lädt ein Image, das Ihre App enthält, erstellt eine DevOps-Toolchain und initiiert den ersten Bereitstellungszyklus für Sie. Weitere Informationen finden Sie unter [Apps auf einem virtuellen Server bereitstellen](/docs/apps?topic=creating-apps-vsi-deploy).

### App manuell bereitstellen
{: deploy-console-manual}

Bei einer ordnungsgemäß konfigurierten Toolchain startet mit jedem Vorgang der Zusammenführung mit dem Masterzweig in Ihrem Repository ein Erstellungs-/Bereitstellungszyklus. 

Sie können Ihre App auch manuell aus Ihrer DevOps-Toolchain heraus bereitstellen:

1. Klicken Sie auf der Seite **App-Details** auf **Toolchain anzeigen**.
2. Klicken Sie auf **Delivery Pipeline**. Hier können Sie Builds starten, die Bereitstellung verwalten sowie Protokolle und den Verlauf anzeigen.

Continuous Delivery ist für manche automatisch Anwendungen aktiviert. Sie können Continuous Delivery aktivieren, um Builds, Tests und Bereitstellungen über die Delivery Pipeline und GitHub zu automatisieren.

Weitere Informationen finden Sie in den folgenden Abschnitten:
* [Build und Bereitstellung](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)
* [Toolchains erstellen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)

## Verwendung der {{site.data.keyword.dev_cli_short}}-Befehlszeilenschnittstelle
{: #deploy-cli}

{{site.data.keyword.cloud_notm}} bietet eine leistungsfähige Befehlszeilenschnittstelle und leistungsfähige Plug-ins, die den Workflow eines Anwendungsentwicklers vereinfachen. Abhängig von der Konfiguration Ihrer App stehen zwei Möglichkeiten für die Bereitstellung Ihrer {{site.data.keyword.cloud_notm}}-App zur Verfügung.

### Vorbereitende Schritte
{: #deploy-cli-before}

Bevor Sie beginnen, müssen Sie die {{site.data.keyword.cloud_notm}}-CLI [herunterladen und installieren](/docs/cli?topic=cloud-cli-ibmcloud-cli).

Die Befehlszeilenschnittstelle wird von Cygwin nicht unterstützt. Verwenden Sie das Tool in einem anderen Fenster als dem Cygwin-Befehlszeilenfenster.
{: important}

  1. Laden Sie den Code für Ihre App in ein neues Verzeichnis herunter, um Ihre Entwicklungsumgebung einzurichten.

  2. Wechseln Sie in das Verzeichnis, in dem sich Ihr Code befindet.

  3.  Aktualisieren Sie Ihren App-Code. Beispiel: Wenn Sie eine {{site.data.keyword.cloud_notm}}-Beispielanwendung verwenden und Ihre App die Datei `src/main/webapp/index.html` enthält, können Sie diese ändern und den `Dankestext` bearbeiten. Prüfen Sie, ob sich die App lokal ausführen lässt, bevor Sie sie in {{site.data.keyword.cloud_notm}} bereitstellen.

    Beachten Sie die Datei `manifest.yml`. Wenn Sie Ihre App in {{site.data.keyword.cloud_notm}} bereitstellen, dient diese Datei zur Ermittlung der URL Ihrer Anwendung, der Speicherzuordnung, Anzahl der Instanzen und anderer wichtiger Parameter.

    Prüfen Sie außerdem den Inhalt der `README.md`-Datei, die Details wie z. B. Erstellungsanweisungen enthält.

    Wenn es sich bei Ihrer Anwendung um eine Liberty-App handelt, müssen Sie sie erstellen, bevor Sie sie erneut bereitstellen.
    {: note}

  4. Melden Sie sich mit Ihrer IBMid bei der {{site.data.keyword.cloud_notm}}-CLI an. Wenn Sie über mehrere Konten verfügen, werden Sie aufgefordert, das Konto auszuwählen, das verwendet werden soll. Wenn Sie keine Region mit dem Flag `-r` angeben, müssen Sie auch eine Region auswählen.
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    Wenn Ihre Berechtigungsnachweise zurückgewiesen werden, verwenden Sie möglicherweise eine föderierte ID. Verwenden Sie für die Anmeldung mit einer föderierten ID das Flag `--sso`. Weitere Informationen finden Sie unter [Mit föderierter ID anmelden](/docs/iam/federated_id?topic=iam-federated_id#federated_id).
    {: tip}

### App automatisch bereitstellen
{: #deploy-cli-auto}

Wenn Sie keine DevOps-Toolchain für Ihre App erstellt haben und Ihre App sich noch nicht in einem Git-Repository befindet, können Sie den Befehl [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit) ausführen. Folgen Sie den Eingabeaufforderungen für die DevOps-Konfiguration und führen Sie eine Bereitstellung für eine neue Toolchain durch (und erstellen Sie ein neues GitLab-Repository).

Nachdem Sie eine DevOps-Toolchain für Ihre App erstellt haben, müssen Sie zur Bereitstellung eines neuen Builds lediglich Ihren Code festschreiben und per Push-Operation in das Repository in der Toolchain übertragen. 

1. Bereiten Sie die festzuschreibenden Änderungen vor.
    ```
    git add .
    ```
2. Schreiben Sie die Änderungen zusammen mit einer kurzen Nachricht fest.
    ```
    git commit -m "made changes"
    ```
3. Übertragen Sie die Festschreibungen für den Masterzweig mit einer Push-Operation an das ferne Repository.
    ```
    git push origin master
    ```
4. Zeigen Sie die DevOps-Toolchain für Ihre App über die {{site.data.keyword.cloud_notm}}-Konsole an. Sie können Toolchain-Details von der Seite **App-Details** in der {{site.data.keyword.cloud_notm}}-Konsole anzeigen, indem Sie den Befehl [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) im App-Verzeichnis ausführen.
5. Zeigen Sie die Pipeline in der Toolchain an, um sicherzustellen, dass ein neuer Build gestartet wurde.

### App manuell bereitstellen
{: #deploy-cli-manual}

Sie können Ihre App manuell in {{site.data.keyword.cloud_notm}} bereitstellen, indem Sie den Befehl [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) ausführen.

  ```
  ibmcloud dev deploy <APP_NAME>
  ```
  {: codeblock}

### Zugehörige Informationen
{: #deploy-cli-related}

Weitere Informationen zum Bereitstellen Ihrer App in {{site.data.keyword.cloud_notm}} mithilfe der Befehlszeilenschnittstelle finden Sie im folgenden Blogbeitrag:

* [Deploying to IBM Cloud Environments with {{site.data.keyword.dev_cli_short}} CLI](https://www.ibm.com/cloud/blog/deploying-to-ibm-cloud-environments-with-ibm-cloud-developer-tools-cli){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")
