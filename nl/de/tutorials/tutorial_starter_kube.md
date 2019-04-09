---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Starter-Kit-App in einem Kubernetes-Cluster bereitstellen
{: #tutorial-starterkit-kube}

Erfahren Sie, wie Sie eine App in {{site.data.keyword.cloud}} mit einem leeren Starter-Kit und einer Kubernetes-Toolchain erstellen und die App kontinuierlich an einen sicheren Container in einem Kubernetes-Cluster übergeben. Ihre DevOps-Pipeline für die kontinuierliche Integration kann so konfiguriert werden, dass Ihre Codeänderungen automatisch erstellt und an die App weitergegeben werden, die sich im Kubernetes-Cluster befindet. Wenn Sie bereits eine Pipeline haben, können Sie sie mit Ihrer App verbinden.
{: shortdesc}

{{site.data.keyword.cloud_notm}} bietet Starter-Kits, die Sie bei der Erstellung der Basis einer App unterstützen, die mit Kubernetes läuft. Wenn Sie ein Starter-Kit verwenden, ist es einfach, einem Modell für cloudnative Programmierung zu folgen, das bewährte Verfahren von {{site.data.keyword.cloud_notm}} für die Entwicklung von Apps verwendet. Starter-Kits generieren Apps, die dem Modell für cloudnative Programmierung folgen, und sie enthalten für jede Programmiersprache Testfälle, Statusprüfung und Metriken. Sie können auch Cloud-Services bereitstellen, die dann in Ihrer generierten Anwendung initialisiert werden.

Dieses Lernprogramm verwendet die Kubernetes-Bereitstellungsoption. In diesem Lernprogramm erstellen wir eine Anwendung aus einem Basis-Starter-Kit, indem wir Java + Spring verwenden, eine Cloudant-Serviceinstanz hinzufügen und sie in {{site.data.keyword.cloud_notm}} mithilfe einer Kubernetes-Umgebung bereitstellen.

Sehen Sie sich zuerst das folgende Starter-Kit-Ablaufdiagramm und die zugehörigen Übersichtsschritte an.

![Starter-Kit-Ablaufdiagramm](../images/starterkit-flow.png) 

## Vorbereitende Schritte
{: #prereqs-starterkit-kube}

* Erstellen Sie eine **Java + Spring**-App mithilfe eines [Starter-Kits](/docs/apps/tutorials/tutorial_starter-kit.html#tutorial-starterkit).
* Installieren Sie die [{{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle](/docs/cli/index.html).
* Richten Sie [Docker ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.docker.com/get-started){: new_window} ein.

## Ihrer App Ressourcen hinzufügen
{: #resources-starterkit-kube}

Fügen Sie Ihrer Anwendung eine {{site.data.keyword.cloud_notm}}-Serviceressource hinzu. Die folgenden Schritte stellen eine Cloudant-Instanz zur Verfügung, erstellen einen Ressourcenschlüssel (Berechtigungsnachweise) und stellen die Bindung an Ihre App her.

1. Klicken Sie auf der Seite mit den **App-Details** auf **Ressource hinzufügen**.
2. Wählen Sie **Daten** aus und klicken Sie auf **Weiter**.
3. Wählen Sie **Cloudant** aus und klicken Sie auf **Weiter**.
4. Wählen Sie auf der Seite **Cloudant hinzufügen** die Region (Vereinigte Staaten (Süden)), die Ressourcengruppe (Standard) und den Preistarif (Lite - eine kostenfreie Instanz) aus.
5. Klicken Sie auf **Erstellen**. Die Seite mit den **App-Details** wird angezeigt, und die Cloudant-Instanz wird eingerichtet und an Ihre App gebunden. Beachten Sie, dass der Cloudant-Ressourcenschlüssel (Berechtigungsnachweise) dem Feld **Berechtigungsnachweise** hinzugefügt wird.
6. Optional. Wenn Sie einen kurzen Blick auf Ihren App-Code werfen möchten, nachdem Sie Ressourcen hinzugefügt haben, klicken Sie auf **Code herunterladen**. Ihr Code wird in Form einer `.zip`-Datei heruntergeladen, die die vollständige App-Codestruktur enthält. Sie können die Datei einfach erstellen und den Code lokal mithilfe der {{site.data.keyword.dev_cli_notm}} ausführen oder Sie können ihn zu Ihrem Code-Management-Repository hinzufügen.

## App mithilfe einer DevOps-Toolchain bereitstellen
{: #deploy-starterkit-kube}

Verbinden Sie eine DevOps-Toolchain mit der Anwendung und konfigurieren Sie sie so, dass sie in einem Kubernetes-Cluster bereitgestellt wird, der im {{site.data.keyword.cloud_notm}}-Kubernetes-Service gehostet wird.

1. Klicken Sie auf der Seite mit den **App-Details** auf **In Cloud bereitstellen**.
2. Wählen Sie auf der Seite **Bereitstellungsumgebung auswählen** die Option **In Kubernetes bereitstellen** aus.
3. Wählen Sie eine Region und einen Cluster aus. Wenn Sie keinen Kubernetes-Cluster haben, klicken Sie auf **Cluster erstellen**.
  * Wählen Sie auf der Seite **Neuen Cluster erstellen** den Standort und den Clustertyp (kostenfrei) aus, geben Sie einen Clusternamen ein und klicken Sie dann auf **Cluster erstellen**.
  * Falls erforderlich, befolgen Sie die Anweisungen auf dem Bildschirm, um Zugriff auf Ihren Cluster zu erhalten.
  * Warten Sie, bis der Cluster anzeigt, dass er **BEREIT** ist, um die Toolchain zu erstellen. Mit der Region **Vereinigte Staaten (Süden))** können Sie einen kostenfreien Cluster bereitstellen.
  * Kehren Sie zur Seite **Bereitstellungsumgebung auswählen** zurück.
4. Klicken Sie auf **Weiter**. Die Seite **Toolchain konfigurieren** wird angezeigt.
5. Geben Sie auf der Seite **Toolchain konfigurieren** einen Toolchainnamen ein, wählen Sie eine Region aus, wählen Sie eine Ressourcengruppe aus und klicken Sie dann auf **Erstellen**. Die Seite mit den **App-Details** wird mit Bereitstellungsinformationen zu Ihrer Toolchain angezeigt.

## Repository anzeigen
{: #view-repo-starterkit-kube}

1. Klicken Sie auf der Seite mit den **App-Details** auf **Repository anzeigen**. Das vom Starter-Kit generierte Git-Repository wird angezeigt.
2. Optional. Konfigurieren Sie SSH auf Ihrem Desktop, indem Sie die Anweisungen auf dem Bildschirm befolgen.
3. Optional. Erstellen Sie ein persönliches Zugriffstoken für Ihr Konto, indem Sie die Anweisungen auf dem Bildschirm befolgen.

## Toolchain-Tools, Protokolle und Verlauf anzeigen
{: #view-logs-starterkit-kube}

1. Wenn die Bereitstellungsstage abgeschlossen ist, wird die Seite mit den **App-Details** mit Bereitstellungsinformationen zu Ihrer Toolchain angezeigt.
2. Greifen Sie auf die Toolchain zu, indem Sie auf **Toolchain anzeigen** klicken. Die Registerkarte **Übersicht** der Toolchainseite wird angezeigt, auf der die Tools aufgeführt werden, die in der Toolchain enthalten sind. Dieses Beispiel enthält die folgenden Tools, die im Starter-Kit vorausgewählt wurden, als die Toolchain erstellt wurde:
  * Ein Issues-Tracker zum Verfolgen von Projektaktualisierungen und -änderungen.
  * Ein Git-Repository, das den Quellcode Ihrer Anwendung enthält.
  * Eine Eclipse Orion-Instanz, bei der es sich um eine webbasierte IDE zum Bearbeiten Ihrer Anwendung handelt.
  * Eine Delivery Pipeline, die aus einer anpassbaren Build- und Bereitstellungsstage besteht.
	 * Die BUILD-Stage containerisiert die App. Genauer gesagt, werden in der Build-Stage:
	   * Ihr GitLab-Repository geklont.
	   * Die App erstellt.
	   * Das Docker-Image erstellt.
	   * Das Image in Ihrem privaten Container-Registry veröffentlicht.
	 * Die BEREITSTELLUNGsstage ruft das Container-Image aus Ihrem Container-Registry ab und stellt es dann in Ihrem Kubernetes-Cluster bereit.
3. Klicken Sie auf **Delivery Pipeline**. Die Pipeline-Stages werden angezeigt.
4. Klicken Sie in der Kachel **Bereitstellungsstage** auf **Protokolle und Verlauf anzeigen**.

## Ausführung der App verifizieren
{: #verify-starterkit-kube}

Nach der Bereitstellung der App verweist Sie die Delivery Pipeline oder die Befehlszeile auf die URL für Ihre App.

1. Klicken Sie in der Toolchain von DevOps auf **Delivery Pipeline** und wählen Sie **Bereitstellungsstage** aus.
2. Klicken Sie auf **Protokolle und Verlauf anzeigen**.
3. Suchen Sie in der Protokolldatei nach der Anwendungs-URL:

    Suchen Sie am Ende der Protokolldatei nach `Status der Anwendung ansehen unter: http://<ipaddress>:<port>/health`.

4. Rufen Sie die URL im Browser auf. Wenn die App ausgeführt wird, wird eine Nachricht anzeigt, die Folgendes enthält: `Congratulations` oder `{"status":"UP"}`.

Wenn Sie die Befehlszeile verwenden, führen Sie den Befehl [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) aus, um die URL der App anzuzeigen. Anschließend rufen Sie die URL in Ihrem Browser auf.

## Nächste Schritte
{: #next-steps-startkit-kube notoc}

* Wenn bei der Bereitstellung Fehler auftreten, suchen Sie im Abschnitt zur Fehlerbehebung nach bekannten Problemen wie der [Überschreitung des Speicherkontingents](/docs/apps/ts_apps.html#exceed_quota) oder erfahren Sie, wie Sie [auf Kubernetes-Protokolle zugreifen](/docs/apps/ts_apps.html#access_kube_logs), um nach Fehlern zu suchen.

* Greifen Sie auf die Servicekonfiguration in Ihrem Code zu:
	- Sie können die Anmerkung _@Value_ oder die Methode _getProperty()_ der Klasse 'Environment' des Spring-Frameworks verwenden. Weitere Informationen finden Sie unter [Auf Berechtigungsnachweise zugreifen](/docs/java-spring/configuration.html#configuration#accessing-credentials).

* Fügen Sie Ihrer Kubernetes-Umgebung neue Berechtigungsnachweise hinzu:
	- Wenn Sie Ihrer Anwendung nach der Erstellung der DevOps-Toolchain einen weiteren Service hinzufügen, werden Ihre bereitgestellte Anwendung und Ihr GitLab-Repository nicht automatisch mit dessen Serviceberechtigungsnachweisen aktualisiert. Sie müssen der Bereitstellungsumgebung [die Berechtigungsnachweise manuell hinzufügen](/docs/apps/creds_kube.html#sk_kube).
