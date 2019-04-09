---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-04"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Lernprogramm 'Einführung'
{: #tutorial-getting-started}

Sie können auf Unternehmen abgestimmte mobile und Webanwendungen in {{site.data.keyword.cloud}} erstellen und die Vorteile von Cloud-Erweiterungen nutzen, die von {{site.data.keyword.cloud_notm}} gehostet werden. Es stehen verschiedene Optionen für den Einstieg zur Auswahl. Erstellen Sie eine App mit einem Starter-Kit, das den Prozess für Sie verwaltet, oder wenn Ihre Pläne bereits festliegen, erstellen Sie eine völlig neue App mit den benötigten Ressourcen, oder verwenden Sie Ihr vorhandenes Repository und bringen Sie Ihren eigenen Code mit.
{: shortdesc}

## Vorbereitende Schritte
{: #prereqs-getting-started}

Sie können Ihre App mithilfe der {{site.data.keyword.cloud_notm}}-Konsole oder der Befehlszeilenschnittstelle (Command-Line Interface, CLI) erstellen. Wenn Sie die CLI verwenden möchten, lesen Sie den Abschnitt [Einführung in die {{site.data.keyword.cloud_notm}}-CLI](/docs/cli/index.html), der Installationsdetails enthält.

## Schritt 1. App erstellen
{: #create-getting-started}

Erstellen Sie eine App, indem Sie einen der folgenden Eingangspunkte auswählen:
* [Starter-Kit:](/docs/apps/tutorials/tutorial_starter-kit.html#tutorial-starterkit) Erstellen Sie eine App aus einer Auswahl von Starter-Kits für den App-Service, die den Prozess für Sie verwalten.
* [Angepasst:](/docs/apps/tutorials/tutorial_scratch.html#tutorial-scratch) Wenn Ihre Pläne bereits festliegen, erstellen Sie eine völlig neue angepasste App mit den benötigten Ressourcen, indem Sie ein leeres Starter-Kit verwenden.
* [Eigenen Code integrieren:](/docs/apps/tutorials/tutorial_byoc.html#tutorial-byoc) Sie können Ihren eigenen Code einbringen, indem Sie eine Verknüpfung zu einem eigenen vorhandenen Content-Repository herstellen. Ihre App und das Docker-Image müssen sich im selben Repository befinden.
* [CLI:](/docs/apps/create-deploy-cli.html#create-deploy-app-cli) Erstellen Sie eine angepasste oder eine Starter-Kit-App und stellen Sie sie bereit, indem Sie die CLI sowie Entwicklertools verwenden.
* [Codemuster:](/docs/apps/tutorials/tutorial_code-pattern.html#tutorial-codepattern) Verwenden Sie ein IBM Entwickler-Codemuster als Basis für die Erstellung Ihrer App.
* [{{site.data.keyword.cloud_notm}}-Katalog ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://cloud.ibm.com/catalog){: new_window}: Sie können den Katalog nach Apps und Services durchsuchen, die Sie erstellen und noch am selben Tag nutzen können.

## Schritt 2. Ressourcen hinzufügen
{: #resources-getting-started}

Wenn Sie zur Erstellung Ihrer App ein Starter-Kit verwenden, werden Ihre Ressourcen automatisch für Sie erstellt. Sie können Ihrer App noch weitere Ressourcen zuordnen, indem Sie auf der Seite "App-Details" auf **Ressource hinzufügen** klicken.

Führen Sie den folgenden Befehl aus, um einen Service zu Ihrer App hinzuzufügen und Ressourcen über die CLI zu nutzen. Sie können einen vorhandenen Service aus den Services auswählen, die bereits für Ihr Konto aktiviert sind, oder einen neuen Service hinzufügen. 
```
ibmcloud dev edit
```
{: codeblock}

Weitere Informationen finden Sie unter [Service Ihrer App hinzufügen](/docs/apps/reqnsi.html#add-resource).

## Schritt 3. App bereitstellen
{: #deploy-getting-started}

Sie können Ihre App über die Konsole oder über die Befehlszeile bereitstellen.

### Verwendung der Konsole
{: #console-getting-started}

Führen Sie die folgenden Schritte aus, um die App über die Konsole zu verwenden:

1. Klicken Sie auf der Seite **App-Details** auf **In Cloud bereitstellen**.
2. Wählen Sie eine Bereitstellungsmethode aus und klicken Sie auf **Erstellen**. {{site.data.keyword.cloud_notm}} erstellt automatisch eine offene Toolchain mit einem Git-Repository und einer Continuous Delivery-Pipeline.
3. Öffnen Sie die Pipeline-Stage Ihrer neuen Toolchain, um den Build- und Bereitstellungsprozess anzuzeigen, damit Sie Ihre neue App innerhalb weniger Minuten anzeigen können.

Weitere Informationen finden Sie im Inhaltsverzeichnis für verschiedene Bereitstellungsthemen im Abschnitt "App bereitstellen und integrieren".

### Verwendung der Befehlszeile
{: #cli-getting-started}

Führen Sie den Befehl `ibmcloud dev deploy` aus, um Ihre App über die Befehlszeile bereitzustellen. Weitere Informationen finden Sie in [Apps über die Befehlszeilenschnittstelle erstellen und bereitstellen](/docs/apps/create-deploy-cli.html#create-deploy-app-cli).

Jetzt sind Sie bereit für die iterative Entwicklung und Continuous Delivery.
