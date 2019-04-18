---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, byoc, code repository, continuous delivery, cli, deploy

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Apps aus Ihrem eigenen Code-Repository erstellen
{: #tutorial-byoc}

Sie können eine Anwendung in {{site.data.keyword.cloud}} erstellen, indem Sie Ihr vorhandenes Anwendungsrepository verwenden. Geben Sie einfach den Web-Link zu Ihrem Repository während der Anwendungserstellung an, fügen Sie Ressourcen hinzu und verbinden Sie anschließend eine DevOps-Toolchain mit Ihrer Anwendung für die Bereitstellung.
{: shortdesc}

## Vorbereitende Schritte
{: #prereqs-byoc}

Stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

 * Installieren Sie die [{{site.data.keyword.dev_cli_long}}-Befehlszeilenschnittstelle](/docs/cli?topic=cloud-cli-ibmcloud-cli).
 * Lesen Sie [Bewährte Verfahren (Best Practices) für die Erstellung guter Apps](/docs/apps?topic=creating-apps-best-practice), um bewährte Verfahren zum Erstellen von Apps kennenzulernen.
 * Sie müssen über ein Git-Quellcode-Repository von einem der folgenden Anbieter verfügen: GitHub, GitHub Enterprise, GitLab, BitBucket oder Rational.
 * Wenn Sie vorhaben, Ihre App in [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about) bereitzustellen, müssen Sie [Ihr {{site.data.keyword.cloud_notm}}-Konto vorbereiten](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Schritt 1. Erstellen Sie eine App mit einem vorhandenen Repository
{: #create-byoc}

Führen Sie die folgenden Schritte aus, um eine App zu erstellen und sie mit Ihrem Quellenrepository zu verbinden:

1. Klicken Sie in Ihrem [Dashboard ](https://{DomainName}){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") auf **Anwendung erstellen** in der Kachel **Apps**.
2. Benennen Sie Ihre App, wählen Sie eine Ressourcengruppe aus und geben Sie optional Tags an, um Ihre App zu klassifizieren. Weitere Informationen finden Sie in [Mit Tags arbeiten](/docs/resources?topic=resources-tag).
3. Wählen Sie **Eigenen Code integrieren** aus und geben Sie die URL für Ihr Git-Repository an. Ihre App und das Docker-Image müssen sich im selben Repository befinden.
4. Klicken Sie auf **Erstellen**. Die Seite **App-Details** wird angezeigt.
5. Optional. Sie können Ihrer App [Services hinzufügen](/docs/apps?topic=creating-apps-add-resource).
6. Optional. Wenn Sie beim Erstellen der App Tags angegeben haben, können Sie diese bearbeiten, indem Sie auf das Symbol **Bearbeiten** ![Symbol 'Bearbeiten'](../../icons/edit-tagging.svg) neben den angezeigten Tags klicken.
7. Optional. Klicken Sie auf **Repository anzeigen**, um das Repository anzuzeigen.

## Schritt 2. App bereitstellen
{: #toolchain-byoc}

Die Erstellung einer Verknüpfung zwischen App, Toolchain und Repository ist ein Schritt zur Organisation Ihrer Produktassets. Außerdem hilft sie bei der Zusammenstellung einer Ansicht Ihres Quellenrepositorys mit Ihrem DevOps-Workflow, Ihren aktiven App-Instanzen und abhängigen Services über alle Ihre Bereitstellungsziele hinweg. Weitere Informationen finden Sie unter [Toolchains erstellen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

Sie können Continuous Delivery für Ihre App konfigurieren, indem Sie entweder die {{site.data.keyword.cloud_notm}}-Konsole oder die Befehlszeilenschnittstelle verwenden.

### Verwendung der Konsole
{: #console-byoc-toolchain}

  1. Stellen Sie auf der Seite **App-Details** eine Verbindung zwischen Ihrer App und einer DevOps-Toolchain her, indem Sie auf **Continuous Delivery konfigurieren** klicken. Die Seite **App bereitstellen** wird angezeigt.
  2. Wenn Sie nicht über eine vorhandene Toolchain verfügen, klicken Sie auf **Toolchain erstellen**. Verwenden Sie, nachdem Sie die Toolchain erstellt haben, den Breadcrumb-Pfad, um zur Seite **App-Details** zurückzukehren, wo angezeigt wird, dass Continuous Delivery konfiguriert ist.
  3. Wenn Sie über eine vorhandene Toolchain verfügen, wählen Sie sie aus und klicken Sie dann auf **Bereitstellung aktivieren**. Die Seite **App-Details** wird angezeigt und zeigt an, dass Continuous Delivery konfiguriert ist.

### Verwendung der Befehlszeilenschnittstelle

Sie können den Befehl `ibmcloud dev enable` verwenden, um eine DevOps-Toolchain-Vorlage zu generieren, die Sie in Ihrem Repository einchecken als Instruktionssatz für das, was die DevOps-Toolchain erstellen soll. 

  1. Klicken Sie auf der Seite **App-Details** auf **Repository anzeigen**, um lokal mit Ihrem Code zu arbeiten.
  2. Führen Sie den folgenden Befehl aus:
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

Weitere Informationen finden Sie in [Apps über die Befehlszeilenschnittstelle erstellen und bereitstellen](/docs/apps?topic=creating-apps-create-deploy-app-cli).

