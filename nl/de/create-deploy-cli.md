---
copyright:

  years: 2018

lastupdated: "2018-10-02"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}

# Apps über die Befehlszeilenschnittstelle erstellen und bereitstellen
{: #developing}

Sie können eine App über die Befehlszeilenschnittstelle (CLI) von {{site.data.keyword.Bluemix}} erstellen und bereitstellen.
{:shortdesc}

## Vorbereitende Schritte
{: #prereqs}

Installieren Sie die {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle, das Plug-in {{site.data.keyword.dev_cli_notm}} für die Befehlszeilenschnittstelle und weitere empfohlene Plug-ins und Tools. Weitere Informationen finden Sie in [Einführung in die IBM Cloud-Befehlszeilenschnittstelle](/docs/cli/index.html). 

## App erstellen
{: #create}

Sie können eine App völlig neu erstellen oder mithilfe Ihres vorhandenen Codes eine cloudfähige App erstellen. 

### App völlig neu erstellen

1. Führen Sie den Befehl [`ibmcloud dev create`](/docs/cli/idt/commands.html#create) in dem von Ihnen ausgewählten Verzeichnis aus.
2. Wählen Sie **Back-End-Service / Web-App** als Anwendungstyp aus.
3. Wählen Sie **Node** als Sprachtyp aus.
4. Wählen Sie **Express.js Basic (Web App)** als zu verwendendes Starter-Kit aus.
5. Geben Sie einen Namen für die App ein und wählen Sie die zu verwendende Ressourcengruppe aus (falls erforderlich). Fügen Sie zum gegenwärtigen Zeitpunkt keine Services hinzu.
6. Wählen Sie die Option **IBM DevOps mit Cloud Foundry** aus, um eine DevOps-Toolchain zu erstellen. Möglicherweise müssen Sie SSH-Schlüssel konfigurieren, um diesen Schritt auszuführen.
7. Geben Sie einen eindeutigen Hostnamen ein, z. B. `abc-devhost`. Dieser Hostname gibt die Route Ihrer App an: `abc-devhost.mybluemix.net`.

Die Erstellung der App und der Toolchain nimmt einige Sekunden in Anspruch. Sie können den Status in der Eingabeaufforderung verfolgen.

### App mithilfe des vorhandenen Codes erstellen

1. Klonen Sie die [Hello World-Beispiel-App](https://github.com/IBM-Cloud/node-helloworld), indem Sie den folgenden Befehl in dem von Ihnen ausgewählten Verzeichnis ausführen.

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

2. Navigieren Sie zu dem Verzeichnis, in dem Sie die Beispiel-App geklont haben, und führen Sie den Befehl [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable) aus.
3. Wählen Sie 'Weiter' aus, um die Verarbeitung zum gegenwärtigen Zeitpunkt ohne Festschreiben der Änderungen in GitHub fortzusetzen.
4. Wählen Sie 'Weiter' aus, wenn Sie dazu aufgefordert werden, mit der erkannten Node-Sprache fortzufahren.
5. Wählen Sie die zu verwendende Ressourcengruppe aus (falls erforderlich). Fügen Sie zum gegenwärtigen Zeitpunkt keine Services hinzu.
6. Warten Sie einige Sekunden, bis die App erstellt ist. 
7. Sie können die Bereitstellungs- und Konfigurationsdateien, die bei der Erstellung der App im App-Verzeichnis gespeichert werden, manuell zusammenführen. Sie können diesen Schritt auch überspringen und später ausführen.

## App erstellen und lokal ausführen
{: #build-run}

Unabhängig von der für die Erstellung der App verwendeten Option können Sie sie nun erstellen und lokal ausführen.

1. Navigieren Sie zum Anwendungsverzeichnis und stellen Sie sicher, dass Docker auf dem verwendeten System ausgeführt wird.
2. Führen Sie den Befehl [`ibmcloud dev build`](/docs/cli/idt/commands.html#build) aus, um die App zu erstellen.
3. Führen Sie den Befehl [`ibmcloud dev run`](/docs/cli/idt/commands.html#run) aus, um die lokale Ausführung der App zu starten.
4. Sie können die lokal ausgeführte App über `http://localhost:3000` oder eine entsprechende URL anzeigen.
5. Drücken Sie die Tastenkombination **Strg+C**, um die App zu stoppen.

Sie können auch [zusammengesetzte Befehle](/docs/cli/idt/commands.html#compound) wie `ibmcloud dev build/run` verwenden, um die Erstellung und Ausführung nacheinander zu veranlassen.
{: tip}

## Service hinzufügen und Code ändern
{: #add-service}

Die App kann nun lokal ausgeführt werden und Sie können einen Service hinzufügen und Code ändern. 

1. Führen Sie den Befehl [`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit) aus.
2. Gehen Sie den Eingabeaufforderungen entsprechend vor, um einen neuen, datenbezogenen Service, wie z. B. {{site.data.keyword.cloudant_short_notm}}, zu erstellen und mit Ihrer App zu verbinden. Möglicherweise müssen Sie eine Region auswählen und die erforderliche Planung für den Service durchführen.
3. Sie können die Bereitstellungs- und Konfigurationsdateien, die bei der Erstellung des Service im App-Verzeichnis gespeichert werden, manuell zusammenführen. Sie können diesen Schritt auch überspringen und später ausführen.
4. Nehmen Sie eine Änderung im Code vor. Ändern Sie beispielsweise die Datei `/public/index.html` oder eine ähnliche Datei. Wenn Sie die `ExpressJS`-Beispielanwendung verwenden, können Sie die Zeichenfolge `Congratulations!` in `Hello World!` oder eine ähnliche Zeichenfolge ändern.
5. Speichern Sie die geänderten Dateien.

## In {{site.data.keyword.Bluemix_notm}} bereitstellen
{: #deploy}

Abhängig von der Konfiguration Ihrer App stehen zwei Möglichkeiten für die Bereitstellung in {{site.data.keyword.Bluemix_notm}} zur Verfügung. 

### App mithilfe einer DevOps-Toolchain bereitstellen

Wenn Sie zuvor eine DevOps-Toolchain für Ihre App erstellt haben, müssen Sie zur Bereitstellung eines neuen Builds lediglich den Code festschreiben und per Push-Operation in das Repository in der Toolchain übertragen. 

1. Führen Sie den Befehl `git add` aus.
2. Führen Sie den Befehl `git commit -m "made changes"` aus, um Änderungen festzuschreiben.
3. Führen Sie den Befehl `git push origin master` aus, um eine Push-Operation in den Masterzweig durchzuführen.
4. Zeigen Sie die DevOps-Toolchain für Ihre App über die {{site.data.keyword.Bluemix_notm}}-Konsole an. Sie können die Toolchain in einem Web-Browser anzeigen, indem Sie den Befehl [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) im App-Verzeichnis ausführen und auf **Toolchain anzeigen** klicken.
5. Zeigen Sie die Pipeline in der Toolchain an, um sicherzustellen, dass ein neuer Build gestartet wurde.

### App manuell bereitstellen

Sie können Ihre App manuell bereitstellen, indem Sie den Befehl [`deploy`](/docs/cli/idt/commands.html#deploy) verwenden. Führen Sie zum Beispiel die folgenden Schritte aus, um die App manuell in Kubernetes bereitzustellen.

1. Stellen Sie sicher, dass [ein Kubernetes-Cluster erstellt wurde](https://console.bluemix.net/containers-kubernetes/overview).
2. Führen Sie den Befehl [`ibmcloud dev deploy -t container`](/docs/cli/idt/commands.html#deploy) aus.
3. Bestätigen Sie den zu verwendenden Cluster- und Container-Image-Namen, wenn Sie dazu aufgefordert werden.
4. Warten Sie einige Minuten, bis die Bereitstellung abgeschlossen ist.

## App anzeigen
{: #view}

1. Zum Anzeigen der URL Ihrer App, die in {{site.data.keyword.Bluemix_notm}} ausgeführt wird, führen Sie den Befehl [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) aus.
2. Zum Anzeigen von Details zu den Berechtigungsnachweisen, den Services und der Toolchain Ihrer App über die {{site.data.keyword.Bluemix_notm}}-Konsole führen Sie den Befehl [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) aus. 

