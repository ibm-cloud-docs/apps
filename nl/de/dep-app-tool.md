---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-02"

keywords: apps, deploy, deploying apps, toolchains, cli, cloud

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

Sie können Ihre Anwendungen mit einer DevOps-Toolchain oder über die Befehlszeilenschnittstelle (CLI) bereitstellen. Bei einer DevOps-Toolchain handelt es sich um einen Satz von Toolintegrationen. Die Befehlszeilenschnittstelle ist eine einfache Möglichkeit, Ihre Apps und Serviceinstanzen bereitzustellen.
{: shortdesc}

## Apps mittels DevOps-Toolchains bereitstellen
{: #toolchain-deploy-apps}

Offene Toolchains sind in den Public- und Dedicated-Umgebungen unter {{site.data.keyword.Bluemix}} verfügbar. Mit einer ordnungsgemäß konfigurierten Toolchain ist das Bereitstellen Ihrer App einfach. Bei einer ordnungsgemäß konfigurierten Toolchain startet mit jedem Vorgang der Zusammenführung mit dem Masterzweig in Ihrem Repository ein Erstellungs-/Bereitstellungszyklus.

Sie können auf folgenden Wegen eine Toolchain erstellen:
* Sie können eine Toolchain aus einer App heraus erstellen. Weitere Informationen finden Sie unter [App bereitstellen](/docs/apps?topic=creating-apps-tutorial-scratch#deploy-scratch).
* Sie können eine Toolchain mithilfe einer Vorlage erstellen. Weitere Informationen finden Sie unter [Toolchains erstellen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## Apps über die Befehlszeilenschnittstelle (CLI) bereitstellen
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}} bietet eine leistungsfähige Befehlszeilenschnittstelle (Command Line Interface, CLI) sowie Plug-ins und Entwicklertoolerweiterungen, die in die CLI integriert werden.

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

  5. Führen Sie in Ihrem neuen Verzeichnis mit dem Befehl [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) die Bereitstellung Ihrer App in {{site.data.keyword.cloud_notm}} durch.
    ```
    ibmcloud dev deploy <APP_NAME>
    ```
    {: codeblock}

  6. Greifen Sie auf Ihre App zu, indem Sie den Befehl [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) ausführen, mit dem die URL Ihrer App angezeigt wird. Anschließend rufen Sie die URL in Ihrem Browser auf.
