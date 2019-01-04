---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Eigenen Code in einem Kubernetes-Cluster bereitstellen
{: #tutorial}

Hier erfahren Sie, wie Sie eine App in {{site.data.keyword.cloud}} mithilfe Ihres vorhandenen App-Repositorys erstellen. Sie können Ihre vorhandene DevOps-Toolchain verbinden oder eine erstellen und eine App kontinuierlich an einen sicheren Container in einem Kubernetes-Cluster übergeben. Dieses Lernprogramm unterstützt Sie bei der Einrichtung einer DevOps-Pipeline für kontinuierliche Integration, sodass die Änderung automatisch erstellt und bis zu Ihrer bereitgestellten App im Kubernetes-Cluster weitergeleitet wird.
{: shortdesc}

Wenn Sie bereits ein Quellcode-Repository mit einer Codebasis für eine funktionierende Back-End-Anwendung haben, hilft Ihnen {{site.data.keyword.cloud_notm}} bei der Einordnung dieses Assets in die Gesamtheit aller Assets, die den Umfang Ihres gesamten Produkts darstellen. {{site.data.keyword.cloud_notm}} ermöglicht Ihnen die Nutzung eines skalierbaren DevOps-Workflows, wenn Sie die DevOps-Toolchain-Funktion verwenden. Dieses Lernprogramm hilft dem erfahrenen Anwendungs- oder DevOps-Entwickler beim Übernehmen und Konfigurieren eines Ziel-{{site.data.keyword.cloud_notm}}-Kubernetes-Clusters und beim Konfigurieren und Ausführen einer DevOps-Toolchain, alles unter Berücksichtigung bewährter Cloud-Verfahren.

Ein _Cluster_ ist eine Gruppe von Ressourcen, Workerknoten, Netzen und Speichereinheiten, die Apps hoch verfügbar halten. Nachdem Sie Ihren Cluster erstellt haben, können Sie Ihre Apps in Containern bereitstellen.
{: tip}

## Vorbereitende Schritte
{: #prereqs}

* Führen Sie zum Erstellen einer App die Schritte unter [Apps aus Ihrem eigenen Code-Repository erstellen](/docs/apps/tutorials/tutorial_byoc.html) durch.
* Klicken Sie im [{{site.data.keyword.cloud_notm}}-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}){: new_window} auf das Symbol **Menü** ![Menüsymbol](../../icons/icon_hamburger.svg) und wählen Sie **Container** aus, um [einen Kubernetes-Cluster zu konfigurieren](/docs/containers/container_index.html).
* Führen Sie die folgenden Befehle aus, um zu bestätigen, dass Ihre App in Docker ausgeführt wird:
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install`
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* Besuchen Sie dann Ihre URL, z. B. `http://localhost/springboothelloworld/sayhello`.   
Drücken Sie die Tastenkombination `Strg+C`, um die Docker-Ausführung zu stoppen.

## Optional. Ihrer App Ressourcen hinzufügen
{: #add_resources}

Fügen Sie Ihrer Anwendung eine Serviceressource hinzu und {{site.data.keyword.cloud_notm}} erstellt den Service für Sie. Dieser Bereitstellungsprozess kann für die verschiedenen Servicetypen unterschiedlich ablaufen. Ein Datenbankservice richtet beispielsweise eine Datenbank ein, während ein Push-Benachrichtigungsservice für mobile Anwendungen Konfigurationsinformationen erstellt. {{site.data.keyword.cloud_notm}} stellt Ihrer Anwendung mittels einer Serviceinstanz die Ressourcen eines Service zur Verfügung. Eine Serviceinstanz kann von mehreren Webanwendungen gemeinsam
genutzt werden.

Dieser Prozess stellt eine Serviceinstanz bereit, erstellt einen Ressourcenschlüssel (Berechtigungsnachweise) und stellt die Bindung an Ihre App her. Weitere Informationen finden Sie unter [Service Ihrer App hinzufügen](/docs/apps/reqnsi.html).

### Serviceberechtigungsnachweise in Ihre Umgebung kopieren

Nachdem Sie Ihrer App eine Serviceressource hinzugefügt haben, werden die Berechtigungsnachweise für diesen Service im Feld **Berechtigungsnachweise** angezeigt. Sie müssen die Berechtigungsnachweise in Ihre Bereitstellungsumgebung kopieren.

Weitere Informationen zum Kopieren von Berechtigungsnachweisen in Ihre Umgebung finden Sie unter [Berechtigungsnachweise Ihrer Kubernetes-Umgebung hinzufügen](/docs/apps/creds_kube.html).


## App mithilfe einer DevOps-Toolchain für die Bereitstellung vorbereiten
{: #connect_toolchain}

In diesem Schritt verbinden Sie eine DevOps-Toolchain mit der Anwendung und konfigurieren sie so, dass sie in einem Kubernetes-Cluster bereitgestellt wird, der im {{site.data.keyword.cloud_notm}}-Kubernetes-Service gehostet wird.

Die DevOps-Toolchain ist so flexibel, dass sie die gesteuerte Ausführung beliebiger Stages der Shell-Script-Ausführung erlaubt. Mit anderen Worten: Sie können fast alles mit einer DevOps-Toolchain machen. Hauptthema dieses Abschnitts ist die Bereitstellung Ihrer App in einem Kubernetes-Cluster. Er beschäftigt sich aber auch damit, sie für skalierte DevOps und bewährte Cloud-Verfahren zukunftssicher zu machen.

Die Erstellung einer Verknüpfung zwischen App, Toolchain und Repository ist ein Schritt zur Organisation Ihrer Produktassets. Außerdem hilft sie bei der Zusammenstellung einer Ansicht Ihres Quellenrepositorys mit Ihrem DevOps-Workflow, Ihren aktiven App-Instanzen und abhängigen Services über alle Ihre Bereitstellungsziele hinweg.

Auf der Seite für die Toolchain-Verbindung haben Sie mehrere Optionen:

* Verbinden Sie Ihre App mit einer vorhandenen Toolchain.
* Verbinden Sie Ihre App mit einer vorhandenen Toolchain, die nicht Ihr Repository enthält. Verbinden Sie dann später die Toolchain mit Ihrem Repository.
* Verbinden Sie Ihre App mit einer neuen Toolchain.

### Verbinden Sie Ihre App mit einer vorhandenen Toolchain
{: #connect_toolchain_repo}

Wenn Sie über eine oder mehrere DevOps-Toolchains verfügen, die bereits mit dem Git-Repository verbunden sind, das Sie während der App-Erstellung angegeben haben, werden diese Toolchains in der Tabelle **Mit Repository** angezeigt. Die Toolchain muss so konfiguriert sein, dass sie die Quelle aus dem Repository abruft, das Sie in der App definiert haben. Sehr wahrscheinlich möchten Sie eine dieser Toolchains für die Verbindung mit Ihrer App auswählen.

### Verbinden Sie Ihre App mit einer vorhandenen Toolchain, die nicht Ihr Repository enthält
{: #connect_toolchain_notrepo}

Wenn Sie über eine oder mehrere DevOps-Toolchains verfügen, die Ihrem Konto zugeordnet, aber nicht mit dem Git-Repository verbunden sind, das Sie während der App-Erstellung angegeben haben, werden diese Toolchains in der Tabelle mit der Bezeichnung **ohne Ihr Repository** angezeigt. Sie können eine dieser Toolchains auswählen und mit Ihrer App verbinden, aber Sie müssen auch Ihr Repository manuell dieser Toolchain hinzufügen.

Weitere Informationen zum Hinzufügen Ihres Repositorys zu Ihrer Toolchain finden Sie unter:

 * [Git-Repositorys und Issue Tracking konfigurieren](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitbluemix)
 * [GitHub konfigurieren](/docs/services/ContinuousDelivery/toolchains_integrations.html#github)
 * [GitLab konfigurieren](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitlab)


### Verbinden Sie Ihre App mit einer neuen Toolchain
{: #create_toolchain}

Sie haben die folgenden Optionen, um Ihre App mit einer neuen Toolchain zu verbinden:
* Wenn Sie keine DevOps-Toolchain völlig neu erstellen möchten, können Sie Ihren vorhandenen Code mit dem Befehl [`ibmcloud dev enable` cloudfähig machen.](/docs/cli/idt/commands.html#enable). Der Befehl generiert eine DevOps-Toolchain-Vorlage, die Sie in Ihrem Repository einchecken. Dann verwenden Sie diese Vorlage als Instruktionssatz für das, was die DevOps-Toolchain erstellt. Weitere Informationen finden Sie unter [Dokumentation zur Befehlszeilenschnittstelle](/docs/apps/create-deploy-cli.html#byoc).
* Erstellen Sie eine DevOps-Toolchain völlig neu in der Konsole. Wenn Sie die Erstellung der DevOps-Toolchain vollständig kontrollieren möchten, ohne dass Änderungen in Ihrem Code-Repository vorgenommen werden, erstellen Sie die Toolchain völlig neu. Weitere Informationen finden Sie unter [DevOps-Toolchain völlig neu erstellen](#create_toolchain_scratch).

#### DevOps-Toolchain völlig neu erstellen
{: #create_toolchain_scratch}

Wenn Sie eine Toolchain völlig neu erstellen und mit Ihrer App verbinden möchten, führen Sie die folgenden Schritte aus. Sie erstellen auch alle Integrationen zum Erstellen Ihrer App und für deren Bereitstellung im Kubernetes-Cluster. Die DevOps-Toolchain-Funktion bietet Vorlagen an, aber diese Schritte zeigen Ihnen, wie Sie eine DevOps-Toolchain völlig neu erstellen.

Wenn Sie sich dafür entscheiden, eine Toolchain aus Ihrer neuen App zu erstellen, wird die Seite [Toolchain erstellen](https://{DomainName}/devops/create) im [DevOps-Dashboard](https://{DomainName}/devops/) in einer neuen Registerkarte in Ihrem Browser geöffnet. Nachdem Sie Ihre Toolchain in dieser Registerkarte erstellt und konfiguriert haben, rufen Sie wieder die Seite **Toolchain verbinden** in Ihrer App auf und aktualisieren Sie die Seite.
{:tip}

1. Klicken Sie auf der Seite **Toolchain erstellen** auf die Vorlage **Eigene Toolchain erstellen**.
2. Geben Sie auf der Seite **Eigene Toolchain erstellen** einen Namen für Ihre Toolchain ein, wählen Sie eine Region und Ressourcengruppe (Standard) aus und klicken Sie auf **Erstellen**.

Es wird eine leere Toolchain ohne vorkonfigurierte Tools oder Integrationen erstellt. Fahren Sie mit dem Konfigurieren und Testen Ihrer neuen Toolchain fort, indem Sie die verbleibenden Schritte ausführen.

## GitHub-Integration hinzufügen

Sie können die DevOps-Toolchain mit GitHub-Integration konfigurieren, indem Sie die folgenden Schritte ausführen:

1. Klicken Sie in Ihrer DevOps-Toolchain-Vorlage auf **Tool hinzufügen**.
2. Wählen Sie **GitHub** aus (wenn sich Ihr Repository tatsächlich auf öffentlichem GitHub oder auf Enterprise-GitHub befindet).
3. Führen Sie auf der Seite **Integration konfigurieren** für GitHub die folgenden Schritte aus:
  * Wählen Sie die **GitHub-Server**-URL aus oder geben Sie sie ein.
  * Wenn eine Nachricht mitteilt, dass die Berechtigung für GitHub fehlt, klicken Sie auf **Berechtigen**. Klicken Sie dann auf der Seite **IBM Cloud-Toolchains berechtigen** auf **IBM Cloud berechtigen**. Geben Sie dann Ihr GitHub-Kennwort ein.
  * Wählen Sie **Bestehend** als **Repository-Typ** auf der Seite **Integration konfigurieren** aus, damit die DevOps-Toolchain das Repository mit einem Webhook konfiguriert und Ihr Repository _nicht_ aufspaltet oder kopiert.
  * Geben Sie Ihre **Repository-URL** ein. (Beispiel: `https://github.com/yourrepo/spring-boot-hello-world`).
  * Warten Sie einige Augenblicke, da Sie möglicherweise aufgefordert werden, GitHub die Berechtigung zu erteilen, der DevOps-Toolchain die Berechtigung zur Verwendung der GitHub-REST-API zum Konfigurieren Ihres Repositorys mit den für das Auslösen der Toolchain erforderlichen Webhooks zu erteilen.
  * Klicken Sie auf **Integration erstellen**.

Sie haben diese DevOps-Toolchain mit einer Integration für Ihr GitHub-Repository konfiguriert. Dies ermöglicht es der Toolchain, einen Webhook in Ihrem Repository zu setzen, sodass Pull-Anforderungen und Code-Push-Operationen in diesem Repository eine POST-Operation für die Toolchain auslösen. Sie können den neuen Webhook in den Einstellungen Ihres Repositorys sehen.

## Delivery Pipeline zum Erstellen, Testen und Bereitstellen Ihrer App hinzufügen

In der Delivery Pipeline wird der Großteil der Arbeit erledigt.

1. Klicken Sie auf **Tool hinzufügen**.
2. Wählen Sie **Delivery Pipeline** aus.
3. Führen Sie auf der Seite **Integration konfigurieren** für die Delivery Pipeline die folgenden Schritte aus:
 * Geben Sie "Continuous Integration" als Pipelinenamen ein.
 * Klicken Sie auf **Integration erstellen**.

Sie haben eine leere Delivery Pipeline erstellt. Als Nächstes definieren Sie Pipeline-Stages, um Ihre Eingaben (den Inhalt des GitHub-Repositorys) an ihr Ziel zu übertragen. Da in diesem Lernprogramm davon ausgegangen wird, dass Sie ein GitHub-Repository haben, das ein funktionierendes Docker-Image erstellt und einen IBM Containers-Kubernetes-Cluster als Ziel hat, erstellen Sie Pipeline-Stages mit Eingaben, Shell-Scripts und Ausgaben, mit denen dieser Zweck erreicht wird.

### Pipeline-Stage "Erstellen und veröffentlichen" konfigurieren

1. Klicken Sie auf die Delivery Pipeline, die Sie erstellt haben.
2. Klicken Sie auf der Seite für die Delivery Pipeline auf **Stage hinzufügen**.
3. Geben Sie in den Feldern auf der Registerkarte **Eingabe** auf der Seite **Stage-Konfiguration** Folgendes ein:
  * Geben Sie als Stagenamen **Build & Publish Docker Image** ein.
  * **Eingabetyp**: Wählen Sie **Git-Repository** aus.
  * **Git-Repository**: Wählen Sie Ihr GitHub-Repository aus.
  * **Zweig**: Wählen Sie den Zweig aus, den Sie für die kontinuierliche Integration verwenden.
4. Klicken Sie auf die Registerkarte **Jobs** und füllen Sie die Felder wie folgt aus:
  * Klicken Sie auf das Symbol **Job hinzufügen '+'** und wählen Sie **Build** als Jobtyp aus.
  * Geben Sie einen Namen ein, z. B. **Build & Publish**.
  * **Buildertyp**: Wählen Sie **Container-Registry** aus.
  * **IBM Cloud-Region**: Wählen Sie die Region aus, in der sich Ihr Kubernetes-Cluster befindet.
  * **API-Schlüssel**: Wählen Sie **Geben Sie einen vorhandenen API-Schlüssel ein** aus. Wenn Sie keinen Schlüssel haben oder Ihren API-Schlüssel nicht kennen, können Sie [einen API-Schlüssel abrufen](https://{DomainName}/iam/#/apikeys), indem Sie ein separates Browserfenster öffnen und zu **Verwalten** > **Sicherheit** > **Plattform-API-Schlüssel** navigieren. Dieser Schlüssel muss an einem sicheren Ort aufbewahrt werden.
  * **Kontoname**: Dieses Feld wird automatisch ausgefüllt, wenn Sie einen API-Schlüssel eingeben.
  * **Container-Registry-Namensbereich**: Geben Sie den [Container-Registry-Namensbereich](https://{DomainName}/containers-kubernetes/registry/namespaces) ein. (Sie finden ihn, indem Sie auf das Symbol **Menü** klicken ![Menüsymbol](../../icons/icon_hamburger.svg) und **Container** > **Registry** > **Namensbereiche** auswählen.)
  * **Docker-Image-Name**: Geben Sie **continuous** ein, da diese Pipeline-Build-Stage der kontinuierlichen Erstellung des Zweigs für die kontinuierliche Integration Ihres Repositorys dient.
  * **Build-Script**: Beachten Sie das Shell-Script. Es fehlen die App-Buildanweisungen für _Ihr_ Repository. Sie müssen nach der ersten Zeile `#!/bin/bash` eine oder mehrere Zeilen hinzufügen. Für ein Repository, das mithilfe von Maven erstellt wird, könnten Sie z. B. einige Zeilen ähnlich dem folgenden Beispiel hinzufügen:

    ```bash
    export JAVA_HOME=/opt/IBM/java8
    # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
    export MAVEN_OPTS="-Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
    mvn -B clean verify
    ```
    {: codeblock}
5. Klicken Sie auf **Speichern**. Ihre Pipeline-Stage "Erstellen und veröffentlichen" wird jetzt in Ihrer Toolchain angezeigt.

### Pipeline-Stage "Erstellen und veröffentlichen" testen

Klicken Sie auf das Symbol **Wiedergabe**, bis der Build erfolgreich ist. Sie wissen, dass es funktioniert, wenn die Stage grün wird und die Scriptausgabe Ihre Erwartungen erfüllt. Das Ziel dieser Stage ist die Veröffentlichung eines Docker-Images in Ihrem Image-Registry. Wenn das Script nicht genug für Sie anzeigt, können Sie das Image-Registry anzeigen, um die Veröffentlichung zu bestätigen, indem Sie auf das Symbol **Menü** ![Menüsymbol](../../icons/icon_hamburger.svg) klicken und dann **Container** > **Registry** > **Private Repositorys** auswählen. Bestätigen Sie anschließend, dass ein Repository aufgelistet wird, das mit dem Namen `/continuous` endet. (Sie erinnern sich: Das war der Imagename.)

### Pipeline-Stage "In Cluster bereitstellen" konfigurieren

Bis jetzt haben Sie ein Docker-Image in Ihrer privaten Docker-Image-Registry veröffentlicht. Jetzt ist es an der Zeit, eine Stage zu erstellen, die dieses Image in Ihrem Kubernetes-Cluster bereitstellt.

1. Klicken Sie auf der Seite für die Delivery Pipeline auf **Stage hinzufügen**.
2. Geben Sie in den Feldern auf der Registerkarte **Eingabe** auf der Seite **Stage-Konfiguration** Folgendes ein:
  * **Name**: Geben Sie **Deploy** ein.
  * **Eingabetyp **: Wählen Sie **Buildartifakte** aus.
  * **Stage**: Wählen Sie **Build & Publish Docker Image** aus.
  * **Job**: Wählen Sie **Build & Publish** aus.
  * **Stage-Auslöser**: Da es sich hier um Ihre Pipeline für kontinuierliche Integration handelt, wählen Sie den Standardwert **Jobs ausführen, wenn die vorherige Stage abgeschlossen ist** aus.
3. Klicken Sie auf die Registerkarte **Jobs** und füllen Sie die Felder wie folgt aus:
  * Klicken Sie auf das Symbol **Job hinzufügen '+'** und wählen Sie **Bereitstellung** als Jobtyp aus.
  * Geben Sie einen Namen ein, z. B. **Deploy to Continuous Integration Cluster**.
  * **Bereitstellertyp**: Wählen Sie **Kubernetes** aus.
  * **IBM Cloud-Region**: Wählen Sie die Region aus, in der sich Ihr Kubernetes-Cluster befindet.
  * **API-Schlüssel**: Wählen Sie **Geben Sie einen vorhandenen API-Schlüssel ein** aus. Wenn Sie keinen Schlüssel haben oder Ihren API-Schlüssel nicht kennen, können Sie [einen API-Schlüssel abrufen](https://{DomainName}/iam/#/apikeys), indem Sie ein separates Browserfenster öffnen und zu **Verwalten** > **Sicherheit** > **Plattform-API-Schlüssel** navigieren. Dieser Schlüssel muss an einem sicheren Ort aufbewahrt werden.
  * Akzeptieren Sie die verbleibenden Standardeinstellungen.
4. Klicken Sie auf **Speichern**. Ihre Pipeline-Stage "Deploy" wird jetzt in Ihrer Toolchain angezeigt.

### Pipeline-Stage "In Cluster bereitstellen" testen

Klicken Sie auf das Symbol **Wiedergabe**, bis der Build erfolgreich ist. Sie wissen, dass es funktioniert, wenn die Stage grün wird und die Scriptausgabe Ihre Erwartungen erfüllt. Sie können die Protokolle für die Stage anzeigen. Etwa am Ende der Protokolle finden Sie einen anklickbaren Link zur ausgeführten App. Allerdings kennen nur _Sie_ das Kontextstammverzeichnis und den Pfad Ihrer App. Hängen Sie den richtigen Pfad an, um zu bestätigen, dass sie funktioniert.
