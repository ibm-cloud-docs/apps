---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-07-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Mobile Anwendung mit einem Starter-Kit erstellen
{: #tutorial}

{{site.data.keyword.Bluemix}} stellt Starter-Kits für Mobilgeräte bereit, die Sie bei der schnellen Erstellung einer mobilen App unterstützen. Wählen Sie in den Starter-Kits des App-Service eine Sprache, ein Framework und Tools aus, um mit der Arbeit mit einer vorkonfigurierten angepassten App zu beginnen. In diesem Lernprogramm erfahren Sie, wie Sie die erforderlichen Tools installieren, wie Sie die App erstellen und lokal ausführen und wie Sie die App in der Cloud bereitstellen.
{: shortdesc}

## Schritt 1: Tools installieren
{: #install-tools}

Installieren Sie die [Entwicklertools ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.

Docker wird als Teil der Entwicklertools installiert. Docker muss ausgeführt werden, damit die Buildbefehle funktionieren. Sie müssen ein Docker-Konto erstellen, die Docker-App ausführen und sich anmelden.

## Schritt 1: App mit {{site.data.keyword.dev_console}} erstellen
{: #create-devex}

1. Erstellen Sie eine {{site.data.keyword.dev_console}}-App in {{site.data.keyword.Bluemix}}.
2. Wählen Sie auf der Seite [Starter-Kits ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) in der {{site.data.keyword.dev_console}} ein Starter-Kit auf der Basis der gewünschten Features aus. Wählen Sie für eine Watson Language-Anwendung beispielsweise **Swift Kitura** aus.
3. Geben Sie Ihren App-Namen ein. Verwenden Sie im Rahmen dieses Lernprogramms `WatsonApp`.
4. Wählen Sie Ihre Sprachplattform aus. Verwenden Sie im Rahmen dieses Lernprogramms `Swift`.
5. Wählen Sie Ihre Sprache und Ihr Framework aus. Einige Starter-Kit sind möglicherweise nur ein einer Sprache verfügbar.
6. Wählen Sie Ihren Preisstrukturplan aus. Es steht eine kostenfreie Option zur Verfügung, die Sie für dieses Lernprogramm verwenden können.
7. Klicken Sie auf **Erstellen**.

## Schritt 3: Ressourcen hinzufügen (optional)
{: #add-services}

Sie können Ressourcen, die Ihre App mit der kognitiven Leistung von Watson funktional erweitern, mobile Services oder Sicherheitsservices hinzufügen. Im Rahmen dieses Lernprogramms fügen Sie eine Position für die Verwaltung Ihrer Daten hinzu.

1. Wählen Sie im Fenster des App-Service **Ressource hinzufügen** aus.
2. Wählen Sie den Typ des gewünschten Service aus. Wählen Sie beispielsweise **Daten** > **Weiter** > **Cloudant** > **Weiter** aus.
3. Wählen Sie Ihren Preisstrukturplan aus. Es steht eine kostenfreie Option zur Verfügung, die Sie für dieses Lernprogramm verwenden können.
4. Klicken Sie auf **Erstellen**.

## Schritt 4: DevOps-Toolchain erstellen
{: #add-toolchain}

Durch das Aktivieren einer Toolchain wird eine teambasierte Entwicklungsumgebung für Ihre App erstellt. Wenn Sie eine Toolchain erstellen, erstellt der App-Service ein Git-Repository, in dem Sie Quellcode anzeigen, die App klonen und Problemmeldungen erstellen und verwalten können. Darüber hinaus verfügen Sie über Zugriff auf eine dedizierte Git-Laborumgebung und eine Continuous-Delivery-Pipeline. Diese sind an die ausgewählte Bereitstellungsplattform - z. B. Kubernetes oder Cloud Foundry - angepasst.

Continuous Delivery ist für manche Anwendungen aktiviert. Sie können Continuous Delivery aktivieren, um Builds, Tests und Bereitstellungen über die Delivery Pipeline und GitHub zu automatisieren.

1. Klicken Sie im Fenster des App-Service auf **In Cloud bereitstellen**.
2. Wählen Sie eine Bereitstellungsmethode aus. Richten Sie die Bereitstellungsmethode ein, indem Sie die Anweisungen für die ausgewählte Methode ausführen.

    * Führen Sie die Bereitstellung für einen Kubernetes-Cluster aus. Erstellen Sie einen Cluster mit Hosts, die als Workerknoten bezeichnet werden, um hoch verfügbare Anwendungscontainer bereitzustellen und zu verwalten. Sie können ein Cluster erstellen oder in einem vorhandenen Cluster bereitstellen.

    * Führen Sie die Bereitstellung mit Cloud Foundry aus. Hier müssen Sie die zugrunde liegende Infrastruktur nicht verwalten.

## Schritt 5: App erstellen und lokal ausführen
{: #build-run}

Durch die Bereitstellung der App in der Cloud im letzten Schritt wurde eine Toolchain erstellt. Eine Toolchain erstellt ein Git-Repository für die App, in dem Sie den Code anzeigen können. Führen Sie diese Schritte aus, um auf Ihr Repository zuzugreifen. Sie können die App zu Testzwecken lokal erstellen, bevor Sie sie in der Cloud bereitstellen.

1. Klicken Sie im Fenster des App-Service auf **Code herunterladen** oder **Repository klonen**, um lokal mit dem Code zu arbeiten.
2. Importieren Sie die App in die integrierte Entwicklungsumgebung.
3. Ändern Sie den Code.
4. Richten Sie die [Git-Authentifizierung](/docs/services/ContinuousDelivery/git_working.html#git_authentication) ein, indem Sie ein persönliches Zugriffstoken hinzufügen.
5. Melden Sie sich bei der {{site.data.keyword.Bluemix}}-Befehlszeilenschnittstelle an. Wenn in Ihrer Organisation föderierte Anmeldungen verwendet werden, wählen Sie die Option `-sso` aus.

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Legen Sie die Zielorganisation und den Zielbereich fest.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7.  Rufen Sie die Berechtigungsnachweise ab.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Stellen Sie sicher, dass Docker ausgeführt wird, und erstellen Sie die App in einem lokalen Entwicklungscontainer im Verzeichnis.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Führen Sie die App in einem lokalen Entwicklungscontainer aus.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10.  Öffnen Sie in Ihrem Browser diese Adresse: `http://localhost:3000`. Abhängig von der ausgewählten Laufzeit kann die Portnummer davon abweichen.

### Swift-App in Xcode ausführen
{: #run_swift}

1. Öffnen Sie die Datei `README.md` in einem Markdown Viewer, um die Schritte zur Konfiguration Ihrer App zu überprüfen.
2. Öffnen Sie Ihr Terminal, navigieren Sie zu Ihrem App-Ordner und führen Sie die folgenden Befehle aus:
    1. Führen Sie `pod setup` aus, wenn Sie Ihr CocoaPods-Repository einrichten müssen.
    2. Führen Sie `pod update` aus, wenn Sie Ihre vorhandenen Pods aktualisieren müssen.
    3. Führen Sie `pod install` aus, um die Pods für Ihre App zu installieren.
3. Öffnen Sie Ihren Xcode-Arbeitsbereich `<appname>.xcworkspace`.
4. Führen Sie Ihre App aus.

### Cordova-App in Xcode ausführen
{: #run_cordova_xcode}

Falls Sie ausgewählt haben, Cordova als Ihre Implementierungssprache zu verwenden, befolgen Sie diese Anweisungen.

1. Öffnen Sie die Datei `README.md` in einem Markdown Viewer, um Ihre App zu konfigurieren.
2. Öffnen Sie Ihre App `platforms/ios` in Xcode.
3. Führen Sie Ihre App aus.

### Cordova-App in Android Studio ausführen
{: #run_cordova_studio}

Verwenden Sie diesen Abschnitt, wenn Sie Cordova als Plattform Ihrer mobilen App verwenden möchten.

1. Extrahieren Sie die Datei `BasicProject-Cordova.zip`.
2. Öffnen Sie die Datei `README.md` in einem Markdown Viewer, um Ihre App zu konfigurieren.
3. Öffnen Sie Ihre App `platforms/android` in Android Studio.
4. Führen Sie Ihre App aus.

### Android-App in Android Studio ausführen
{: #run_android}

Verwenden Sie diesen Abschnitt, wenn Sie Android als Plattform Ihrer mobilen App verwenden möchten.

1. Öffnen Sie die Datei `README.md` in einem Markdown Viewer, um Ihre App zu konfigurieren.
2. Öffnen Sie Ihre App `BasicProject-Android` in Android Studio.
3. Führen Sie Ihre App aus.

## Schritt 6: In der Cloud bereitstellen
{: #deploy}

### Bereitstellung: Toolchain verwenden

Für die Bereitstellung der App in {{site.data.keyword.cloud_notm}} stehen mehrere Möglichkeiten zur Verfügung, eine DevOps-Toolchain ist jedoch für die Bereitstellung von Produktions-Apps am besten geeignet. Mit einer DevOps-Toolchain können Sie ohne großen Aufwand Bereitstellungen in vielen Umgebungen automatisieren und schnell Überwachungs-, Protokollierungs- und Alert-Services hinzufügen, die Sie bei der Verwaltung Ihrer ständig weiterentwickelten App unterstützen.

Bei einer ordnungsgemäß konfigurierten Toolchain startet mit jedem Vorgang der Zusammenführung mit dem Masterzweig in Ihrem Repository ein Erstellungs-/Bereitstellungszyklus. Alle über ein {{site.data.keyword.cloud_notm}}-Entwicklerdashboard erstellten Toolchains sind für die automatische Bereitstellung konfiguriert.

Sie können Ihre App auch manuell aus Ihrer DevOps-Toolchain heraus bereitstellen:

1. Klicken Sie im Fenster mit den App-Details auf **Toolchain anzeigen**.

2. Klicken Sie auf **Delivery Pipeline**. Hier können Sie Builds starten, die Bereitstellung verwalten sowie Protokolle und den Verlauf anzeigen.

### Bereitstellung: {{site.data.keyword.dev_cli_short}} verwenden

Geben Sie den folgenden Befehl ein, um Ihre App in Cloud Foundry bereitzustellen:

```
ibmcloud dev deploy
```
{: pre}

Geben Sie den folgenden Befehl ein, um Ihre App in einem Kubernetes-Cluster bereitzustellen:

```
ibmcloud dev deploy --target <container>
```
{: pre}

## Schritt 7: Ausführung der App verifizieren
{: #verify}

Nach der Bereitstellung der App verweist die DevOps-Pipeline bzw. die Befehlszeile auf die URL für Ihre App, z. B. `abc-devhost.mybluemix.net`. Rufen Sie diese URL im Browser auf.
