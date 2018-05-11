---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-03-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Grundlegende Webanwendung mit einem Starter-Kit erstellen
{: #tutorial}

Sie können ein Projekt aus einem grundlegenden Starter für Webanwendungen erstellen. Verwenden Sie diese Starter, um einen einfachen Web-Server für Node, Java oder Python mit einer Auswahl von Web-Frameworks zu erstellen. Sie erfahren, wie die erforderlichen Tools installiert werden, wie das Projekt lokal erstellt und ausgeführt wird und wie es in der Cloud bereitgestellt wird.
{: shortdesc}

## Schritt 1: Tools installieren
{: #before-you-begin}

Installieren Sie die [Entwicklertools ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.


## Schritt 2: Projekt erstellen
{: #create-devex}

Erstellen Sie ein Projekt in der {{site.data.keyword.cloud}}-{{site.data.keyword.dev_console}}:

1. Wählen Sie auf der Seite [Starter-Kits ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) in der {{site.data.keyword.dev_console}} ein Starter-Kit für Ihre Sprache aus. Wählen Sie beispielsweise für eine Node.js-Anwendung **Express.js Basic** und dann **Projekt erstellen** aus.

2. Geben Sie Ihren Projektnamen ein. Verwenden Sie im Rahmen dieses Lernprogramms `WebBasicProject`.   

3. Geben Sie einen eindeutigen Hostnamen ein, z. B. Ihre Initialen plus `-devhost`. Beispiel:

	```
	abc-devhost
	```

	Dieser Hostname ist die Route Ihres Projekts. Beispiel: `abc-devhost.mybluemix.net`

4. Wählen Sie Ihre Sprachplattform aus. Verwenden Sie im Rahmen dieses Lernprogramms `Node.js`.

5. Klicken Sie auf **Projekt erstellen**.

## Optional: Ressourcen hinzufügen
{: #add-services}

1. Wählen Sie in der Ansicht **Projektdetails** die Option **Ressource hinzufügen** aus.

2. Wählen Sie den Typ des gewünschten Service aus. Wählen Sie im Rahmen dieses Lernprogramms **Daten** > **Weiter** > **Cloudant NoSQL DB** > **Weiter** aus.

4. Klicken Sie auf **Erstellen**.

## Optional: DevOps-Toolchain erstellen
{: #add-toolchain}

Wenn Sie eine Toolchain aktivieren, wird eine teambasierte Entwicklungsumgebung für Ihr Projekt erstellt. Wenn Sie eine Toolchain erstellen, stellt der App-Service ein Git-Repository bereit, in dem Sie Quellcode anzeigen, Ihr Projekt klonen und Probleme erstellen und verwalten können. Sie haben außerdem Zugriff auf eine dedizierte Gitlab-Umgebung und eine Continuous Delivery-Pipeline, die an die ausgewählte Entwicklungsplattform angepasst wird, z. B. Kubernetes oder Cloud Foundry.

Continuous Delivery ist für manche Anwendungen aktiviert. Aktivieren Sie Continuous Delivery beispielsweise, um Builds, Tests und Bereitstellungen über die Delivery Pipeline und GitHub zu automatisieren.

1. Wählen Sie Ihr Projekt auf der Seite **Projekte** aus.

2. Klicken Sie auf **In Cloud bereitstellen**.

3. Wählen Sie eine Bereitstellungsmethode aus. Sie haben folgende Optionen:

	* Führen Sie die Bereitstellung in einem Kubernetes-Cluster aus. Richten Sie ein Cluster von Hosts, namens Workerknoten ein, um hoch verfügbare Anwendungscontainer bereitzustellen und zu verwalten. Sie können ein Cluster erstellen oder in einem vorhandenen Cluster bereitstellen.

	* Führen Sie die Bereitstellung mithilfe von Cloud Foundry aus, wo Sie die zugrunde liegende Infrastruktur nicht verwalten müssen.

## Schritt 3: Projektcode generieren
{: #generate-code}

Wenn Sie im vorherigen Schritt eine Toolchain erstellt haben, wurde ein Git-Repository für Ihr Projekt erstellt und Sie können den Code darin finden. Führen Sie die folgenden Schritte aus, um auf Ihr Repository zuzugreifen:

1. Wählen Sie Ihr Projekt auf der Seite **Projekte** aus.

2. Klicken Sie auf **Toolchain anzeigen**.

3. Klicken Sie auf die Karte **Git** unter der Überschrift **CODE**, um Ihr Repository zu öffnen, wo Sie Quellcode anzeigen und Ihr Projekt klonen können.

Falls keine Toolchain aktiviert ist, können Sie auf Ihren Code zugreifen, indem Sie die Quelle direkt in der Ansicht 'Projektdetails' herunterladen.

1. Wählen Sie Ihr Projekt auf der Seite **Projekte** aus.

2. Klicken Sie auf **Code herunterladen**, um Ihr Projektarchiv herunterzuladen.

## Schritt 4: Arbeit an Ihrer App beginnen
{: #code}

Beginnen Sie, mit Ihrem heruntergeladenen Projekt zu arbeiten:

1. Erweitern Sie die archivierte Datei.

2. Importieren Sie das Projekt in Ihre integrierte Entwicklungsumgebung (IDE).

3. Ändern Sie den Code wie gewünscht.

4. Verwenden Sie die {{site.data.keyword.dev_cli_notm}}, um Ihren Code zu erstellen und lokal auszuführen.


## Schritt 5: App erstellen und lokal ausführen
{: #build-run}

Fügen Sie Ihren eigenen Code hinzu, erstellen und führen Sie das Projekt aus. Sie können die Anwendung lokal auf Ihrem Hostsystem ausführen, wenn Sie die erforderlichen Buildtools installieren oder indem Sie die verfügbare Containerunterstützung in der {{site.data.keyword.dev_cli_notm}} verwenden.

### {{site.data.keyword.dev_cli_short}} verwenden

1. Installieren Sie die Knotenabhängigkeiten:

  ```
  npm install
  ```
  {: codeblock}

2. Bündeln Sie Ihren Front-End-Code in einem Modul:

  ```
  gulp
  ```
  {: codeblock}

3. Geben Sie den folgenden Befehl ein, um das Projekt in Ihrem aktuellen Projektverzeichnis zu erstellen:

  ```
  bx dev build
  ```
  {: codeblock}

4. Geben Sie den folgenden Befehl ein, um das Projekt in Ihrem aktuellen Projektverzeichnis auszuführen:

  ```
  bx dev run
  ```
  {: codeblock}

5. Öffnen Sie in Ihrem Browser die URL `http://localhost:3000` (Ihre Portnummer kann abhängig von der ausgewählten Laufzeit abweichen).


## Schritt 6: In der Cloud bereitstellen
{: #deploy}

### Bereitstellung mithilfe einer Toolchain
Es gibt verschiedene Wege, Ihre App in {{site.data.keyword.cloud_notm}} bereitzustellen, aber die Verwendung einer DevOps-Toolchain ist die beste Möglichkeit, Produktions-Apps zu implementieren. Mit einer DevOps-Toolchain können Sie Bereitstellungen in verschiedenen Umgebungen einfach automatisieren und schnell Überwachungs-, Protokollierungs- und Alert-Services hinzufügen, die Sie dabei unterstützen, Ihre immer in Entwicklung begriffene App zu verwalten.

Bei einer ordnungsgemäß konfigurierten Toolchain startet ein Erstellen-Bereitstellen-Zyklus automatisch mit jedem Zusammenführvorgang mit dem Masterzweig in Ihrem Repository. Alle in einem {{site.data.keyword.cloud_notm}}-Entwicklerdashboard erstellten Toolchains werden für die automatische Bereitstellung konfiguriert.

Sie können Ihre App auch manuell aus Ihrer DevOps-Toolchain heraus bereitstellen:

1. Wählen Sie Ihr Projekt auf der Seite **Projekte** aus.

2. Klicken Sie auf **Toolchain anzeigen**.

3. Zeigen Sie Ihre Delivery Pipeline an, in der Sie Builds starten, die Bereitstellung verwalten und Protokolle sowie den Verlauf anzeigen können.

### Bereitstellung mithilfe von {{site.data.keyword.dev_cli_short}}
Wenn Sie keine Toolchain verwenden, können Sie die Bereitstellung auch mithilfe der {{site.data.keyword.dev_cli_short}} vornehmen.

Geben Sie den folgenden Befehl ein, um Ihr Projekt in Cloud Foundry bereitzustellen:

  ```
  bx dev deploy
  ```
  {: codeblock}

Geben Sie den folgenden Befehl ein, um Ihr Projekt in einem Kubernetes-Cluster bereitzustellen:

```
bx dev deploy --target <container>
```
{: codeblock}

### App ausführen
Sobald die Anwendung bereitgestellt wurde, sehen Sie eine URL ähnlich `abc-devhost.mybluemix.net` in der DevOps-Pipeline oder im Terminal (wenn Sie eine Befehlszeile verwenden). Rufen Sie diese URL in Ihrem Browser auf.
