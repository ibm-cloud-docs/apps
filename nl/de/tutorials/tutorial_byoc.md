---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

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

 * Installieren Sie die [{{site.data.keyword.dev_cli_long}}-Befehlszeilenschnittstelle](/docs/cli/index.html#overview).
 * Lesen Sie [Bewährte Verfahren (Best Practices) für die Erstellung guter Apps](/docs/apps/best-practice.html#best-practice), um bewährte Verfahren zum Erstellen von Apps kennenzulernen.
 * Sie müssen über ein Git-Quellcode-Repository von einem der folgenden Anbieter verfügen: GitHub, GitHub Enterprise, GitLab, BitBucket oder Rational.
 * Wenn Sie vorhaben, Ihre App in [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about) bereitzustellen, müssen Sie [Ihr {{site.data.keyword.cloud_notm}}-Konto vorbereiten](/docs/cloud-foundry/prepare-account.html#prepare).

## Schritt 1. Erstellen Sie eine App mit einem vorhandenen Repository
{: #create-byoc}

Führen Sie die folgenden Schritte aus, um eine App zu erstellen und sie mit Ihrem Quellenrepository zu verbinden:

1. Klicken Sie in Ihrem [Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}){: new_window} auf **Anwendung erstellen** in der Kachel **Apps**.
2. Benennen Sie Ihre App, wählen Sie eine Ressourcengruppe aus und geben Sie optional Tags an, um Ihre App zu klassifizieren. Weitere Informationen finden Sie in [Mit Tags arbeiten](/docs/resources/tagging_resources.html#tag).
3. Wählen Sie **Eigenen Code integrieren** aus und geben Sie die URL für Ihr Git-Repository an. Ihre App und das Docker-Image müssen sich im selben Repository befinden.
4. Klicken Sie auf **Erstellen**.

Die Seite mit den **App-Details** wird angezeigt. Von hier aus können Sie:
* [Ressourcen hinzufügen](/docs/apps/reqnsi.html#add-resource) (optional).
* Wenn Sie beim Erstellen der App Tags angegeben haben, können Sie diese bearbeiten, indem Sie auf das Symbol **Bearbeiten** ![Symbol 'Bearbeiten'](../../icons/edit-tagging.svg) neben den angezeigten Tags klicken.
* Ihre App mit einer DevOps-Toolchain verbinden, indem Sie auf **Mit DevOps-Toolchain verbinden** klicken. Wenn Sie noch nicht über eine Toolchain verfügen, wird die Seite **DevOps-Toolchain verbinden** geöffnet. Klicken Sie auf **DevOps-Toolchain erstellen**. An diesem Punkt wird die Seite [Toolchain erstellen](https://{DomainName}/devops/create) im [DevOps-Dashboard](https://{DomainName}/devops/) auf einer neuen Registerkarte in Ihrem Browser geöffnet. Nachdem Sie Ihre Toolchain in dieser Registerkarte erstellt und konfiguriert haben, rufen Sie wieder die Seite **Toolchain verbinden** in Ihrer App auf und aktualisieren Sie die Seite.
* Klicken Sie auf **Repository anzeigen**, um das Repository anzuzeigen.
* Weitere Informationen zu Toolchains oder zur App-Erstellung erhalten Sie, wenn Sie auf einen der zugehörigen Links auf der Seite mit den **App-Details** klicken.

## Schritt 2. Verbinden Sie Ihre App mit einer DevOps-Toolchain
{: #toolchain-byoc}

Die Erstellung einer Verknüpfung zwischen App, Toolchain und Repository ist ein Schritt zur Organisation Ihrer Produktassets. Außerdem hilft sie bei der Zusammenstellung einer Ansicht Ihres Quellenrepositorys mit Ihrem DevOps-Workflow, Ihren aktiven App-Instanzen und abhängigen Services über alle Ihre Bereitstellungsziele hinweg. Weitere Informationen finden Sie unter [Toolchains erstellen](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

Sie können Ihre App mit einer DevOps-Toolchain verbinden, indem Sie entweder die {{site.data.keyword.cloud_notm}}-Konsole oder die Befehlszeilenschnittstelle verwenden.

### Verwendung der Konsole
{: #console-byoc-toolchain}

  1. Verbinden Sie Ihre App mit einer DevOps-Toolchain, indem Sie auf **Mit DevOps-Toolchain verbinden** klicken. 
  
    Wenn Sie nicht über eine vorhandene Toolchain verfügen, klicken Sie auf **DevOps-Toolchain erstellen**. 
    
  2. Nachdem Sie Ihre Toolchain erstellt und konfiguriert haben, rufen Sie wieder die Seite "Toolchain verbinden" in Ihrer App auf und aktualisieren Sie die Seite. 

### Verwendung der Befehlszeilenschnittstelle

Sie können den Befehl `ibmcloud dev enable` verwenden, um eine DevOps-Toolchain-Vorlage zu generieren, die Sie in Ihrem Repository einchecken als Instruktionssatz für das, was die DevOps-Toolchain erstellen soll. 

  1. Klicken Sie im App-Service-Fenster auf **Code herunterladen** oder **Repository klonen**, um lokal mit Ihrem Code zu arbeiten.
  2. Führen Sie den folgenden Befehl aus:
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

Weitere Informationen finden Sie in [Apps über die Befehlszeilenschnittstelle erstellen und bereitstellen](/docs/apps/create-deploy-cli.html#create-deploy-app-cli).

## Schritt 3. App bereitstellen
{: #deploy-byoc}

Nachdem Sie eine DevOps-Toolchain mit Ihrer App verbunden haben, führen Sie die folgenden Schritte aus, um sie in {{site.data.keyword.cloud_notm}} bereitzustellen: 

1. Klicken Sie auf der Seite "App-Details" auf **In Cloud bereitstellen**.
2. Wählen Sie eine Bereitstellungsmethode aus. Richten Sie Ihre Bereitstellungsmethode entsprechend den Anweisungen für die ausgewählte Methode ein:
  * **Führen Sie die Bereitstellung in [Kubernetes](/docs/apps/deploying/containers.html#containers)** aus. Mit dieser Option wird ein Cluster mit Hosts erstellt, die als Workerknoten bezeichnet werden, um hoch verfügbare Anwendungscontainer bereitzustellen und zu verwalten. Sie können einen Cluster erstellen oder die Bereitstellung in einem vorhandenen Cluster ausführen.
  * **Führen Sie die Bereitstellung in Cloud Foundry aus**. Mit dieser Option wird Ihre Cloud-native App bereitgestellt, ohne dass Sie die zugrundeliegende Infrastruktur verwalten müssen. Wenn Ihr Konto über Zugriff auf {{site.data.keyword.cfee_full_notm}} verfügt, können Sie entweder den Bereitstellertyp **[Public Cloud](/docs/cloud-foundry-public/about-cf.html#about-cf)** oder den Bereitstellertyp **[Enterprise Environment](/docs/cloud-foundry-public/cfee.html#cfee)** auswählen, mit dem Sie isolierte Umgebungen für das Hosting von Cloud Foundry-Anwendungen exklusiv für Ihr Unternehmen erstellen und verwalten können.
  * **Führen Sie die Bereitstellung in einem [virtuellen Server](/docs/apps/vsi-deploy.html#vsi-deploy)** aus. Diese Option stellt eine virtuelle Serverinstanz bereit, lädt ein Image, das Ihre App enthält, erstellt eine DevOps-Toolchain und initiiert den ersten Bereitstellungszyklus für Sie.


