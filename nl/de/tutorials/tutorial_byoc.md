---

copyright:
  years: 2018
lastupdated: "2018-11-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Apps aus Ihrem eigenen Code-Repository erstellen
{: #code-repo}

Sie können eine Anwendung in {{site.data.keyword.cloud}} erstellen, indem Sie Ihr vorhandenes Anwendungsrepository verwenden. Geben Sie einfach den Web-Link zu Ihrem Repository während der Anwendungserstellung an, fügen Sie Ressourcen hinzu und verbinden Sie anschließend eine DevOps-Toolchain mit Ihrer Anwendung für die Bereitstellung.
{: shortdesc}

## Vorbereitende Schritte
{: #prereqs}

Stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

 * Installieren Sie die [{{site.data.keyword.dev_cli_long}}-Befehlszeilenschnittstelle](/docs/cli/index.html).
 * Lesen Sie [Bewährte Verfahren (Best Practices) für die Erstellung guter Apps](/docs/apps/best-practice.html), um bewährte Verfahren zum Erstellen von Apps kennenzulernen.
 * Sie müssen über ein Git-Quellcode-Repository von einem der folgenden Anbieter verfügen: GitHub, GitHub Enterprise, GitLab, BitBucket oder Rational.

## Schritt 1. Erstellen Sie eine App mit einem vorhandenen Repository
{: #create}

Führen Sie die folgenden Schritte aus, um eine App zu erstellen und sie mit Ihrem Quellenrepository zu verbinden:

1. Klicken Sie in Ihrem [Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}){: new_window} auf **Anwendung erstellen** in der Kachel **Apps**.
2. Benennen Sie Ihre App und wählen Sie eine Ressourcengruppe aus.
3. Wählen Sie **Eigenen Code integrieren** aus und geben Sie die URL für Ihr Git-Repository an. Ihre App und das Docker-Image müssen sich im selben Repository befinden.
4. Klicken Sie auf **Erstellen**.

Die Seite mit den **App-Details** wird angezeigt. Von hier aus können Sie:
* [Ressourcen hinzufügen](/docs/apps/reqnsi.html) (optional).
* Ihre App mit einer DevOps-Toolchain verbinden, indem Sie auf **Mit DevOps-Toolchain verbinden** klicken. Wenn Sie noch nicht über eine Toolchain verfügen, wird die Seite **DevOps-Toolchain verbinden** geöffnet. Klicken Sie auf **DevOps-Toolchain erstellen**. An diesem Punkt wird die Seite [Toolchain erstellen](https://{DomainName}/devops/create) im [DevOps-Dashboard](https://{DomainName}/devops/) auf einer neuen Registerkarte in Ihrem Browser geöffnet. Nachdem Sie Ihre Toolchain auf dieser Registerkarte erstellt und konfiguriert haben, müssen Sie zur Seite **Toolchain verbinden** in Ihrer App zurückkehren und die Seite aktualisieren. Weitere Informationen finden Sie unter [App mit einer neuen Toolchain verbinden](#create_toolchain).
* Klicken Sie auf **Repository anzeigen**, um das Repository anzuzeigen.
* Weitere Informationen zu Toolchains oder zur App-Erstellung erhalten Sie, wenn Sie auf einen der zugehörigen Links auf der Seite mit den **App-Details** klicken.

## Schritt 2. Verbinden Sie Ihre App mit einer DevOps-Toolchain
{: #connect_toolchain}

Die Erstellung einer Verknüpfung zwischen App, Toolchain und Repository ist ein Schritt zur Organisation Ihrer Produktassets. Außerdem hilft sie bei der Zusammenstellung einer Ansicht Ihrer Quelle mit Ihrem DevOps-Workflow, Ihren aktiven App-Instanzen und abhängigen Services über alle Ihre Bereitstellungsziele hinweg. Weitere Informationen finden Sie unter [App mit einer neuen Toolchain verbinden](/docs/services/ContinuousDelivery/toolchains_working.html).

Sie können Ihre App mit einer DevOps-Toolchain verbinden, indem Sie entweder die {{site.data.keyword.cloud_notm}}-Konsole oder die Befehlszeilenschnittstelle verwenden. 

### Verwendung der Konsole

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

Weitere Informationen finden Sie in [Apps über die Befehlszeilenschnittstelle erstellen und bereitstellen](/docs/apps/create-deploy-cli.html#developing).

## Schritt 3. App bereitstellen
{: #deploy_app}

Nachdem Sie eine DevOps-Toolchain mit Ihrer App verbunden haben, führen Sie die folgenden Schritte aus, um sie in {{site.data.keyword.cloud_notm}} bereitzustellen: 

1. Klicken Sie auf der Seite mit den App-Details auf **In Cloud bereitstellen**.
2. Wählen Sie eine Bereitstellungsmethode aus. 

    * [Führen Sie die Bereitstellung in einem Kubernetes-Cluster aus](/docs/apps/tutorials/tutorial_byoc_kube.html).  Erstellen Sie einen Cluster mit Hosts, die als Workerknoten bezeichnet werden, um hoch verfügbare Anwendungscontainer bereitzustellen und zu verwalten. Sie können ein Cluster erstellen oder in einem vorhandenen Cluster bereitstellen.
    * Führen Sie die Bereitstellung mit Cloud Foundry aus. Hier müssen Sie die zugrunde liegende Infrastruktur nicht verwalten.
    * Führen Sie die Bereitstellung in einer [virtuellen Serverinstanz](/docs/apps/vsi-deploy.html) aus.


