---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-20"

keywords: getting started apps, create app tutorial, add services, deploy apps, create app, app tutorial

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Lernprogramm 'Einführung'
{: #getting-started}

Sie können auf Unternehmen abgestimmte mobile und Webanwendungen in {{site.data.keyword.cloud}} erstellen und die Vorteile von Cloud-Erweiterungen nutzen, die von {{site.data.keyword.cloud_notm}} gehostet werden. Es stehen verschiedene Optionen für den Einstieg zur Auswahl. Erstellen Sie eine App mit einem Starter-Kit, das den Prozess für Sie verwaltet, oder wenn Ihre Pläne bereits festliegen, erstellen Sie eine völlig neue App mit den benötigten Ressourcen, oder verwenden Sie Ihr vorhandenes Repository und bringen Sie Ihren eigenen Code mit.
{: shortdesc}

Unabhängig davon, ob Sie [vorhandenen Code](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc) haben, den Sie modernisieren und in die Cloud bringen möchten, oder ob Sie eine [von Grund auf neue Anwendung](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit) entwickeln, können Sie das schnell wachsende Ökosystem verfügbarer Services und Laufzeitframeworks in {{site.data.keyword.cloud_notm}} nutzen.

Benötigen Sie Hilfe bei der Entscheidung, wo Sie anfangen sollen? Das folgende Diagramm stellt eine Übersicht zum Erstellen von Apps bereit, unabhängig davon, ob Sie ein Starter-Kit oder Ihren eigenen Code in {{site.data.keyword.cloud_notm}} verwenden.

![Übersicht der Entwicklererfahrung](images/dev-journey.png "Übersicht zum Erstellen von Apps in {{site.data.keyword.cloud_notm}}")

## Vorbereitende Schritte
{: #prereqs-getting-started}

Sie können Ihre App mithilfe der {{site.data.keyword.cloud_notm}}-Konsole oder der Befehlszeilenschnittstelle (Command-Line Interface, CLI) erstellen. Wenn Sie die Befehlszeilenschnittstelle verwenden möchten, lesen Sie die [Installationsschritte](/docs/cli?topic=cloud-cli-getting-started).

## Schritt 1. App erstellen
{: #create-getting-started}

Erstellen Sie eine App, indem Sie einen der folgenden Eingangspunkte auswählen:

* [Vorkonfigurierte Starter-Kits](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit) sind Anwendungsfall-spezifisch und bieten Ihnen einsatzbereite Apps in unterschiedlichen Programmiersprachen und Architekturmustern.
* Mit [Basis-Starter-Kits](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch) können Sie Ihre App erstellen, indem Sie den App-Typ (Mobile oder Back-End), die Sprache und das Framework, die Services und das Bereitstellungsziel auswählen.
* [Integrieren Sie eigenen Code](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc), indem Sie Ihr eigenes vorhandenes Content-Repository verlinken. Ihre App und das Docker-Image müssen sich im selben Repository befinden.
* Mit der [{{site.data.keyword.dev_cli_long}}-Befehlszeilenschnittstelle (CLI)](/docs/apps?topic=creating-apps-create-deploy-app-cli) können Sie Ihre App mithilfe der Befehlszeilenschnittstelle erstellen und bereitstellen.
* Durchblättern oder durchsuchen Sie den [{{site.data.keyword.cloud_notm}}-Katalog](https://{DomainName}/catalog){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") nach Apps und Services, die Sie erstellen und noch am selben Tag verwenden können.
* [IBM Developer-Codemuster ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://developer.ibm.com/patterns/){:new_window} helfen Ihnen, Ihre App schnell zu erstellen und in {{site.data.keyword.cloud_notm}} bereitzustellen. Weitere Informationen finden Sie unter [Codemuster](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern).

## Schritt 2. Services hinzufügen
{: #resources-getting-started}

Wenn Sie zur Erstellung Ihrer App ein Starter-Kit verwenden, werden die obligatorischen Services automatisch für Sie erstellt. Auf der Seite **App-Details** der Konsole können Sie weitere Services mit Ihrer App verbinden. Diese werden angezeigt, sobald Sie die App erstellen.

Wenn Sie Services hinzufügen möchten, nachdem Sie Ihre App erstellt haben, wechseln Sie in das [{{site.data.keyword.cloud_notm}}-Dashboard, ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}) suchen Sie Ihre App und klicken Sie dann auf den Namen Ihrer App. Die Seite **App-Details** wird angezeigt und Sie können eine Serviceinstanz erstellen oder vorhandene Services verbinden.

Oder Sie können den folgenden Befehl ausführen, um über die CLI einen Service zu Ihrer App hinzuzufügen. Sie können einen vorhandenen Service aus den Services auswählen, der bereits für Ihr Konto aktiviert ist, oder einen Service hinzufügen.
```
ibmcloud dev edit
```
{: codeblock}

Weitere Informationen finden Sie unter [Service Ihrer App hinzufügen](/docs/apps?topic=creating-apps-add-resource).

## Schritt 3. App bereitstellen
{: #deploy-getting-started}

Sie können Ihre App über die Konsole oder über die CLI bereitstellen.

### Verwendung der Konsole
{: #console-getting-started}

Führen Sie die folgenden Schritte aus, um die App über die Konsole zu verwenden:

1. Klicken Sie auf der Seite **App-Details** auf **Continuous Delivery konfigurieren**.
2. Wählen Sie ein Bereitstellungsziel aus, wählen Sie die Toolchaineinstellungen aus und klicken Sie auf **Erstellen**. {{site.data.keyword.cloud_notm}} erstellt automatisch eine offene Toolchain mit einem Git-Repository und einer Continuous Delivery-Pipeline.
3. Öffnen Sie die Pipeline-Stage Ihrer neuen Toolchain, um den Build- und Bereitstellungsprozess anzuzeigen, damit Sie Ihre neue App innerhalb weniger Minuten anzeigen können.

Weitere Informationen finden Sie unter [Apps bereitstellen](/docs/apps?topic=creating-apps-deploying-apps).

### Verwendung der Befehlszeilenschnittstelle
{: #cli-getting-started}

Führen Sie den Befehl `ibmcloud dev deploy` aus, um Ihre App über die CLI bereitzustellen. Weitere Informationen finden Sie in [Apps über die Befehlszeilenschnittstelle erstellen und bereitstellen](/docs/apps?topic=creating-apps-create-deploy-app-cli).

Jetzt sind Sie bereit für die iterative Entwicklung und Continuous Delivery.

Weitere Informationen zum Bereitstellen Ihrer App finden Sie unter [Apps bereitstellen](/docs/apps?topic=creating-apps-deploying-apps).

## Zugehörige Informationen
{: #related-getting-started}

[Programmierhandbücher](https://{DomainName}/docs/home/build){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") sind in verschiedenen Sprachen verfügbar, um Ihnen den Start zu erleichtern. Es besteht eine Vielzahl von Optionen für das Hosten Ihrer Apps mit der {{site.data.keyword.cloud_notm}}-Infrastruktur, von {{site.data.keyword.baremetal_short}} bis hin zur Ausführung als serverunabhängige Funktion.
