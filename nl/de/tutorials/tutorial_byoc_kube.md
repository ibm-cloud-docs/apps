---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, deploy, deploy to Kubernetes, cluster, delivery pipeline, toolchain

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Eigenen Code in einem Kubernetes-Cluster bereitstellen
{: #tutorial-byoc-kube}

Hier erfahren Sie, wie Sie eine Anwendung in {{site.data.keyword.cloud}} mithilfe Ihres vorhandenen App-Repositorys erstellen. Sie können Ihre vorhandene DevOps-Toolchain verbinden oder eine erstellen und eine App kontinuierlich an einen sicheren Container in einem Kubernetes-Cluster übergeben. Dieses Lernprogramm unterstützt Sie bei der Einrichtung einer DevOps-Pipeline für kontinuierliche Integration, sodass die Änderung automatisch erstellt und bis zu Ihrer bereitgestellten App im Kubernetes-Cluster weitergeleitet wird.
{: shortdesc}

Wenn Sie bereits ein Quellcode-Repository mit einer Codebasis für eine funktionierende Back-End-Anwendung haben, hilft Ihnen {{site.data.keyword.cloud_notm}} bei der Einordnung dieses Assets in die Gesamtheit aller Assets, die den Umfang Ihres gesamten Produkts darstellen. {{site.data.keyword.cloud_notm}} ermöglicht Ihnen die Nutzung eines skalierbaren DevOps-Workflows, wenn Sie die DevOps-Toolchain-Funktion verwenden. Dieses Lernprogramm hilft dem erfahrenen Anwendungs- oder DevOps-Entwickler beim Übernehmen und Konfigurieren eines Ziel-{{site.data.keyword.cloud_notm}}-Kubernetes-Clusters und beim Konfigurieren und Ausführen einer DevOps-Toolchain, alles unter Berücksichtigung bewährter Cloud-Verfahren.

Ein _Cluster_ ist eine Gruppe von Ressourcen, Workerknoten, Netzen und Speichereinheiten, die Apps hoch verfügbar halten. Nachdem Sie Ihren Cluster erstellt haben, können Sie Ihre Apps in Containern bereitstellen.
{: tip}

## Vorbereitende Schritte
{: #prereqs-byoc-kube}

* Erstellen Sie eine App. Weitere Informationen hierzu enthält [Apps aus Ihrem eigenen Code-Repository erstellen](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc).
* Klicken Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") auf das Symbol **Menü** ![Menüsymbol](../../icons/icon_hamburger.svg) und wählen Sie **Container** aus, um [einen Kubernetes-Cluster zu konfigurieren](/docs/containers?topic=containers-getting-started).
* Führen Sie die folgenden Befehle aus, um zu bestätigen, dass Ihre App in Docker ausgeführt wird:
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install`
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* Rufen Sie dann Ihre URL auf, wie z. B. `http://localhost/springboothelloworld/sayhello`. Drücken Sie die Tastenkombination Strg+C, um die Ausführung von Docker zu stoppen.

## Services Ihrer App hinzufügen (optional)
{: #resources-byoc-kube}

Fügen Sie Ihrer Anwendung einen Service hinzu und {{site.data.keyword.cloud_notm}} erstellt die Serviceinstanz für Sie. Dieser Bereitstellungsprozess kann für die verschiedenen Servicetypen unterschiedlich ablaufen. Ein Datenbankservice richtet beispielsweise eine Datenbank ein, während ein Push-Benachrichtigungsservice für mobile Anwendungen Konfigurationsinformationen erstellt. {{site.data.keyword.cloud_notm}} stellt Ihrer Anwendung mittels einer Serviceinstanz die Ressourcen eines Service zur Verfügung. Eine Serviceinstanz kann von mehreren Webanwendungen gemeinsam
genutzt werden.

Dieser Prozess stellt eine Serviceinstanz bereit, erstellt einen Ressourcenschlüssel (Berechtigungsnachweise) und stellt die Bindung an Ihre App her. Weitere Informationen finden Sie unter [Service Ihrer App hinzufügen](/docs/apps?topic=creating-apps-add-resource).

Nachdem Sie Ihrer App einen Service hinzugefügt haben, müssen Sie die Berechtigungsnachweise für den Service in Ihre Bereitstellungsumgebung kopieren. Weitere Informationen hierzu enthält [Berechtigungsnachweise Ihrer Kubernetes-Umgebung hinzufügen](/docs/apps?topic=creating-apps-add-credentials-kube).

## App für die Bereitstellung vorbereiten
{: #deploy-byoc-kube}

In diesem Schritt verbinden Sie eine DevOps-Toolchain mit der Anwendung und konfigurieren sie so, dass sie in einem Kubernetes-Cluster bereitgestellt wird, der im {{site.data.keyword.cloud_notm}}-Kubernetes-Service gehostet wird.

Die DevOps-Toolchain ist so flexibel, dass sie die gesteuerte Ausführung beliebiger Stages der Shell-Script-Ausführung erlaubt. Mit anderen Worten: Sie können fast alles mit einer DevOps-Toolchain machen. Hauptthema dieses Abschnitts ist die Bereitstellung Ihrer App in einem Kubernetes-Cluster. Er beschäftigt sich aber auch damit, sie für skalierte DevOps und bewährte Cloud-Verfahren zukunftssicher zu machen.

Die Erstellung einer Verknüpfung zwischen App, Toolchain und Repository ist ein Schritt zur Organisation Ihrer Produktassets. Außerdem hilft sie bei der Zusammenstellung einer Ansicht Ihres Quellenrepositorys mit Ihrem DevOps-Workflow, Ihren aktiven App-Instanzen und abhängigen Services über alle Ihre Bereitstellungsziele hinweg.

Auf der Seite zum Verbinden der Toolchain stehen mehrere Optionen zur Auswahl:

* Sie können Ihre App mit einer vorhandenen Toolchain verbinden.
* Sie können Ihre App mit einer vorhandenen Toolchain verbinden, die nicht Ihr Repository enthält. Sie verbinden die Toolchain dann zu einem späteren Zeitpunkt mit Ihrem Repository.
* Sie können Ihre App mit einer neuen Toolchain verbinden.

### Ihre App mit einer vorhandenen Toolchain verbinden
{: #connect_toolchain_repo}

Wenn Sie über eine oder mehrere DevOps-Toolchains verfügen, die bereits mit dem Git-Repository verbunden sind, das Sie während der App-Erstellung angegeben haben, werden diese Toolchains in der Tabelle **Mit Repository** angezeigt. Die Toolchain muss so konfiguriert sein, dass sie die Quelle aus dem Repository abruft, das Sie in der App definiert haben. Sehr wahrscheinlich möchten Sie eine dieser Toolchains für die Verbindung mit Ihrer App auswählen.

### Ihre App mit einer vorhandenen Toolchain verbinden, die nicht Ihr Repository enthält
{: #connect_toolchain_notrepo}

Wenn Sie über eine oder mehrere DevOps-Toolchains verfügen, die Ihrem Konto zugeordnet, aber nicht mit dem Git-Repository verbunden sind, das Sie während der App-Erstellung angegeben haben, werden diese Toolchains in der Tabelle **Ohne Ihr Repository** angezeigt. Sie können eine dieser Toolchains auswählen und mit Ihrer App verbinden, aber Sie müssen außerdem auch Ihr Repository manuell zu dieser Toolchain hinzufügen.

Weitere Informationen zum Hinzufügen Ihres Repositorys zu Ihrer Toolchain finden Sie unter:

 * [Git-Repositorys und Issue Tracking konfigurieren](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitbluemix)
 * [GitHub konfigurieren](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#github)
 * [GitLab konfigurieren](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab)


### Ihre App mit einer neuen Toolchain verbinden
{: #toolchain-byoc-kube-create}

Wenn Sie die Erstellung der DevOps-Toolchain vollständig unter Kontrolle haben möchten, ohne dass Änderungen in Ihrem Code-Repository vorgenommen werden, erstellen Sie die Toolchain von Grund auf völlig neu. Außerdem müssen Sie auch alle Integrationen zum Erstellen Ihrer App erstellen und stellen diese im Kubernetes-Cluster bereit. 

1. Klicken Sie auf der Seite 'Toolchain erstellen' auf die Vorlage **Eigene Toolchain erstellen**.
2. Geben Sie einen Namen für Ihre Toolchain ein, wählen Sie eine Region und eine Ressourcengruppe (Standard) aus und klicken Sie auf **Erstellen**.
3. Verwenden Sie, nachdem Sie die Toolchain erstellt haben, den Breadcrumb-Pfad in Ihrem Browser, um zur Seite **App-Details** zurückzukehren, wo angezeigt wird, dass Continuous Delivery konfiguriert ist.

Wenn Sie keine DevOps-Toolchain völlig neu erstellen möchten, können Sie Ihren vorhandenen Code mit dem Befehl [`ibmcloud dev enable` cloudfähig machen.](/docs/cli/idt?topic=cloud-cli-idt-cli#enable). Der Befehl generiert eine DevOps-Toolchain-Vorlage, die Sie in Ihrem Repository einchecken. Dann verwenden Sie diese Vorlage als Instruktionssatz für das, was die DevOps-Toolchain erstellen soll. Weitere Informationen finden Sie in der [Dokumentation zur Befehlszeilenschnittstelle](/docs/apps?topic=creating-apps-create-deploy-app-cli#byoc-cli).

## GitHub-Integration hinzufügen
{: #github-byoc-kube}

Konfigurieren Sie die DevOps-Toolchain mit einer Integration für Ihr GitHub-Repository für die Toolchain, um einen Webhook in Ihrem Repository zu setzen, sodass Pull-Anforderungen und Code-Push-Operationen in diesem Repository eine POST-Anforderung an die Toolchain senden. 

1. Klicken Sie in Ihrer DevOps-Toolchain-Vorlage auf **Tool hinzufügen**.
2. Wählen Sie **GitHub** aus, wenn sich Ihr Repository auf öffentlichem GitHub oder auf Enterprise-GitHub befindet.
3. Wählen Sie die GitHub-Server-URL aus oder geben Sie sie ein.
4. Möglicherweise wird eine Nachricht mit dem Inhalt angezeigt, dass diese URL auf GitHub nicht autorisiert ist. Falls dies der Fall ist, klicken Sie auf **Berechtigen**. Klicken Sie dann auf der Seite 'IBM Cloud-Toolchains berechtigen' auf **IBM Cloud berechtigen** und geben Sie Ihr GitHub-Kennwort ein.
5. Wählen Sie auf der Seite 'Integration konfigurieren' für den Repository-Typ die Option **Bestehend** aus, damit die DevOps-Toolchain das Repository mit einem Webhook konfiguriert und Ihr Repository nicht aufspaltet oder kopiert.
6. Geben Sie die URL für Ihr Repository ein, z. B. `https://github.com/yourrepo/spring-boot-hello-world`.
7. Nachdem einige Sekunden verstrichen sind, werden Sie möglicherweise aufgefordert, GitHub zu autorisieren, der DevOps-Toolchain die Berechtigung zur Verwendung der GitHub-REST-API zum Konfigurieren Ihres Repositorys mit den Webhooks erteilen, die zum Auslösen der Toolchain erforderlich sind.
8.  Klicken Sie auf **Integration erstellen**.

Sie können den neuen Webhook in den Repositoryeinstellungen anzeigen.

## Delivery Pipeline hinzufügen
{: #pipeline-byoc-kube}

1. Klicken Sie auf **Tool hinzufügen**.
2. Wählen Sie **Delivery Pipeline** aus.
3. Geben Sie `Continuous Integration` als Namen für die Pipeline ein und klicken Sie auf **Integration erstellen**.

## Pipeline-Stages konfigurieren
{: #pipelineconfig-byoc-kube}

Konfigurieren Sie die Pipeline-Stages, um Ihre Eingaben (d. h. den Inhalt des GitHub-Repositorys) an das richtige Ziel zu übertragen. Da in diesem Lernprogramm davon ausgegangen wird, dass Sie ein GitHub-Repository haben, das ein funktionierendes Docker-Image erstellt und einen IBM Containers-Kubernetes-Cluster verwendet, erstellen Sie Pipeline-Stages mit Eingaben, Shell-Scripts und Ausgaben, mit denen dieser Zweck erreicht wird.

1. Konfigurieren Sie Ihre Pipeline-Stage `Build and Publish`.
  1. Wählen Sie die von Ihnen erstellte Delivery Pipeline aus und klicken Sie auf **Stage hinzufügen**.
  2. Klicken Sie auf die Registerkarte **Eingabe** und füllen Sie dort die Felder wie folgt aus:
    * Geben Sie als Stagenamen `build and publish Docker image` ein.
    * Wählen Sie **Git-Repository** als Eingabetyp aus.
    * Wählen Sie Ihr GitHub-Repository aus.
    * Wählen Sie den Zweig aus, den Sie für die kontinuierliche Integration verwenden.
  3.  Klicken Sie erst auf die Registerkarte **Jobs** und dann auf **Job hinzufügen '+'** und füllen Sie die Felder wie folgt aus:
    * Wählen Sie **Erstellung** als Jobtyp aus.
    * Geben Sie als Namen `build and publish` ein.
    * Wählen Sie **Container-Registry** als Buildertyp aus.
    * Wählen Sie die Region aus, in der sich Ihr Kubernetes-Cluster befindet.
    * Wählen Sie die Option für die Eingabe eines vorhandenen API-Schlüssels aus. Wenn Sie über keinen API-Schlüssel verfügen, informieren Sie sich in [API-Schlüssel erstellen](/docs/iam?topic=iam-userapikey#create_user_key). 
    * Geben Sie den Namensbereich für die Container-Registry ein. Diesen finden Sie, indem Sie auf das Symbol **Menü** klicken ![Menüsymbol](../../icons/icon_hamburger.svg) und **Container** > **Registry** > **Namensbereiche** auswählen.
    * Geben Sie als Docker-Image-Namen die Bezeichnung `continuous` ein, da diese Pipeline-Build-Stage der kontinuierlichen Erstellung des Zweigs für die kontinuierliche Integration Ihres Repositorys dient.
    * Bearbeiten Sie das Script, indem Sie nach der ersten Zeile `#!/bin/bash` nach Bedarf eine oder mehrere Zeilen hinzufügen. Für ein Repository, das mithilfe von Maven erstellt wird, könnten Sie z. B. einige Zeilen ähnlich dem folgenden Beispiel hinzufügen:

      ```bash
      export JAVA_HOME=/opt/IBM/java8
      # Es wird empfohlen, MAVEN_OPTS, das Flag -B und die Phasen kurz vor 'install' zu stoppen:
      export MAVEN_OPTS="-  
      Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
      mvn -B clean verify
      ```
      {: codeblock}
  4. Klicken Sie auf **Speichern**. 
2. Testen Sie Ihre Pipeline-Stage `build and publish`, indem Sie auf das Symbol **Wiedergabe** klicken, bis der Build erfolgreich ist. Die Anzeige einer Stage in grün gibt an, dass der Build erfolgreich war. 
3. Konfigurieren Sie Ihre Pipeline-Stage `deploy to cluster`, um das Docker-Image in Ihrem Kubernetes-Cluster bereitzustellen. 
  1. Klicken Sie auf der Seite für die Delivery Pipeline auf **Stage hinzufügen**.
  2. Klicken Sie auf die Registerkarte **Eingabe** und füllen Sie dort die Felder wie folgt aus:
    * Geben Sie `deploy to cluster` als Namen ein.
    * Wählen Sie **Buildartefakte** als Eingabetyp aus.
    * Wählen Sie **Build & Publish Docker Image** als Stage aus.
    * Wählen Sie **Build & Publish** als Job aus.
    * Da es sich hier um Ihre Pipeline für kontinuierliche Integration handelt, übernehmen Sie als Wert für den Standardauslöser die Standardoption.
  3. Klicken Sie erst auf die Registerkarte **Jobs** und dann auf **Job hinzufügen '+'** und füllen Sie die Felder wie folgt aus:
    * Geben Sie `deploy to continuous integration cluster` als Namen ein.
    * Wählen Sie **Kubernetes** als Bereitstellertyp aus.
    * Wählen Sie die Region aus, in der sich Ihr Kubernetes-Cluster befindet.
    * Geben Sie Ihren vorhandenen API-Schlüssel ein. 
  4. Klicken Sie auf **Speichern**.
4. Testen Sie Ihre Pipeline-Stage `deploy to cluster`, indem Sie auf das Symbol **Wiedergabe** klicken, bis der Build erfolgreich ist. Die Anzeige einer Stage in grün gibt an, dass der Build erfolgreich war.

## Ausführung der App verifizieren
{: #verify-byoc-kube}

Nach der Bereitstellung der App verweist Sie die Delivery Pipeline oder die Befehlszeile auf die URL für Ihre App.

1. Klicken Sie in der Toolchain von DevOps auf **Delivery Pipeline** und wählen Sie **Bereitstellungsstage** aus.
2. Klicken Sie auf **Protokolle und Verlauf anzeigen**.
3. Suchen Sie in der Protokolldatei nach der Anwendungs-URL:

    Suchen Sie am Ende der Protokolldatei nach `Status der Anwendung ansehen unter: http://<ipaddress>:<port>/health`.

4. Rufen Sie die URL im Browser auf. Wenn die App ausgeführt wird, wird eine Nachricht anzeigt, die Folgendes enthält: `Congratulations` oder `{"status":"UP"}`.

Wenn Sie die Befehlszeile verwenden, führen Sie den Befehl [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) aus, um die URL der App anzuzeigen. Anschließend rufen Sie die URL in Ihrem Browser auf.
