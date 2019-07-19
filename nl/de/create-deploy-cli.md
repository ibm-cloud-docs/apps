---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, create, build, deploy, cli, web app, microservice

subcollection: creating-apps

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Apps über die Befehlszeilenschnittstelle erstellen und bereitstellen
{: #create-deploy-app-cli}

Sie können die {{site.data.keyword.cloud}}-Befehlszeilenschnittstelle verwenden, um Ihre Anwendung zu erstellen und bereitzustellen. 

Sie können entweder eine Starter-App völlig neu erstellen oder Ihren vorhandenen App-Code cloudfähig machen. 
{: note}

## Vorbereitende Schritte
{: #prereqs-app-cli}

Sie müssen die {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle, das Plug-in {{site.data.keyword.dev_cli_notm}} für die Befehlszeilenschnittstelle und weitere empfohlene Plug-ins und Tools installieren. Weitere Informationen finden Sie in [Einführung in die IBM Cloud-Befehlszeilenschnittstelle](/docs/cli?topic=cloud-cli-ibmcloud-cli). 

## Starter-App völlig neu erstellen
{: #create-app-cli}

Das völlig neue Erstellen einer App ist sinnvoll, wenn Sie nicht bereits über vorhandenen Code verfügen, mit dem Sie beginnen können, und lieber mit einer Sprache oder einer Framework-Startervorlage beginnen möchten.

1. Führen Sie den Befehl [`ibmcloud dev create`](/docs/cli/idt?topic=cloud-cli-idt-cli#create) in dem von Ihnen ausgewählten Verzeichnis aus.
2. Wählen Sie **Back-End-Service / Web-App** als Anwendungstyp aus.
3. Wählen Sie **Node** als Sprachtyp aus.
4. Wählen Sie **Node.js-Web-App mit Express.js (Web-App)** als zu verwendendes Starter-Kit aus.
5. Geben Sie einen Namen für Ihre App ein und wählen Sie die zu verwendende Ressourcengruppe aus (falls erforderlich). Fügen Sie zum gegenwärtigen Zeitpunkt keine Services hinzu.
6. Wählen Sie die Option **IBM DevOps mit Cloud Foundry** aus, um eine DevOps-Toolchain zu erstellen. Möglicherweise müssen Sie SSH-Schlüssel konfigurieren, um diesen Schritt auszuführen.
  Wenn Sie für Ihren SSH-Schlüssel eine Kennphrase festgelegt haben, müssen Sie diesen Code eingeben.
  {: note}
7. Geben Sie einen eindeutigen Hostnamen ein, wie z. B. `abc-devhost`. Dieser Hostname gibt die Route Ihrer App an, wie z. B. `abc-devhost.mybluemix.net`.

Die gemeinsam genutzte Standarddomäne ist `mybluemix.net`, aber `appdomain.cloud` ist eine weitere Domänenoption, die Sie verwenden können. Weitere Informationen zur Migration auf `appdomain.cloud` finden Sie im Abschnitt zum [Aktualisieren Ihrer Domäne](/docs/apps/tutorials?topic=creating-apps-update-domain).
{: tip}

Die Erstellung der App und der Toolchain nimmt einige Sekunden in Anspruch.

## Bereitstellungs- und Cloudaktivierungsassets generieren
{: #byoc-cli}

Diese Option kann verwendet werden, wenn Sie bereits über eine vorhandene Codebasis verfügen und Assets für die Bereitstellung und die Cloudaktivierung für einen einzelnen Mikroservice oder eine einzelne Web-App generieren möchten, indem Sie [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable) verwenden. Beachten Sie, dass dieser Befehl in der Betaversion enthalten ist und nicht alle Sprachen und/oder App-Strukturen unterstützt werden. Die folgenden Anweisungen veranschaulichen, wie diese Funktionalität bei einem Beispielrepository verwendet wird. Die Schritte sind jedoch bei Ihrer eigenen Codebasis in etwa dieselben.

1. Melden Sie sich bei {{site.data.keyword.cloud_notm}} an, indem Sie `ibmcloud login` ausführen und anschließend eine Organisation und einen Bereich als Ziel auswählen.
2. Klonen Sie die [Hello World-Beispiel-App](https://github.com/IBM-Cloud/node-helloworld){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link"), indem Sie den folgenden Befehl im Verzeichnis Ihrer Wahl ausführen.

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

3. Navigieren Sie zu dem Verzeichnis, in dem Sie die Beispiel-App geklont haben, und führen Sie den Befehl [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable) aus.
4. Wählen Sie 'Weiter' aus, ohne zum gegenwärtigen Zeitpunkt Änderungen festzuschreiben (falls erforderlich).
5. Wählen Sie 'Weiter' aus, wenn Sie dazu aufgefordert werden, mit der erkannten Node-Sprache fortzufahren.
6. Wählen Sie die zu verwendende Ressourcengruppe aus (falls erforderlich). 
7. Wählen Sie die Option zum Erstellen einer neuen {{site.data.keyword.cloud_notm}}-App, die mit diesem Git-Repository verknüpft ist, aus. Details hierzu finden Sie unter **Wichtige Hinweise**.
8. Fügen Sie zum gegenwärtigen Zeitpunkt keine Services hinzu.
9. Warten Sie einige Sekunden, bis die Operationen abgeschlossen sind. 
10. Nachdem die Operationen abgeschlossen sind, führen Sie die Bereitstellungs- und Cloudaktivierungsdateien, die im App-Verzeichnis gespeichert werden, manuell zusammen. Sie können neue Dateien mit der Kennzeichnung `.merge` zusammenführen, indem Sie `git diff` oder ein ähnliches Tool verwenden.

### Wichtige Hinweise
 - Wenn Sie bereits eine {{site.data.keyword.cloud_notm}}-App mithilfe der {{site.data.keyword.cloud_notm}}-Konsole erstellt haben, führen Sie die Schritte 2 bis 5 im vorherigen Abschnitt in Ihrem App-Verzeichnis aus. Für Schritt 6 können Sie die Option auswählen, Ihren lokalen Code mit einer vorhandenen App zu verbinden.
 - Sie können auch Bereitstellungs- und Cloudaktivierungsdateien generieren, ohne dass eine Verbindung zu einer {{site.data.keyword.cloud_notm}}-App hergestellt wird, indem Sie [`ibmcloud dev enable --no-create`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable) ausführen.
 - Wenn Sie eine Toolchain und Bereitstellungsdateien manuell konfigurieren möchten, folgen Sie [dem Lernprogramm](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc-kube). Dies kann sinnvoll sein, wenn Sie versuchen, eine Continuous-Delivery-Toolchain für mehrere in Wechselbeziehung zueinander stehende Web-Apps oder Mikroservices zu konfigurieren.
 - Wenn Ihre vorhandene Codebasis noch nicht in einem Git-Repository enthalten ist, führen Sie die Schritte 2 bis 5 im vorherigen Abschnitt in Ihrem App-Verzeichnis aus. Für Schritt 6 können Sie die Option zum Erstellen einer neuen {{site.data.keyword.cloud_notm}}-App auswählen und sie für eine DevOps-Toolchain (für die es ein neu erstelltes GitLab-Repository gibt) bereitstellen.

## App erstellen und lokal ausführen
{: #build-run-app-cli}

Unabhängig von der für die Erstellung der App verwendeten Option können Sie sie nun erstellen und lokal ausführen.

1. Navigieren Sie zum Anwendungsverzeichnis und stellen Sie sicher, dass Docker auf dem verwendeten System ausgeführt wird.
2. Führen Sie den Befehl [`ibmcloud dev build`](/docs/cli/idt?topic=cloud-cli-idt-cli#build) aus, um die App zu erstellen.
3. Führen Sie den Befehl [`ibmcloud dev run`](/docs/cli/idt?topic=cloud-cli-idt-cli#run) aus, um die lokale Ausführung der App zu starten.
4. Sie können die lokal ausgeführte App unter `http://localhost:3000` oder einer ähnlichen URL anzeigen.
5. Drücken Sie die Tastenkombination **Strg+C**, um die App zu stoppen.

Sie können auch [zusammengesetzte Befehle](/docs/cli/idt?topic=cloud-cli-idt-cli#compound) wie `ibmcloud dev build/run` verwenden, um die Erstellung und Ausführung nacheinander zu veranlassen.
{: tip}

## Service hinzufügen und Code ändern
{: #resources-app-cli}

Die App kann nun lokal ausgeführt werden und Sie können einen Service hinzufügen und Code ändern. 

1. Führen Sie den Befehl [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit) aus.
2. Gehen Sie den Eingabeaufforderungen entsprechend vor, um einen neuen, datenbezogenen Service, wie z. B. {{site.data.keyword.cloudant_short_notm}}, zu erstellen und mit Ihrer App zu verbinden. Möglicherweise müssen Sie eine Region auswählen und die erforderliche Planung für den Service durchführen.
3. Sie können die Konfigurationsdateien, die bei der Erstellung des Service in Ihrem App-Verzeichnis gespeichert werden, manuell zusammenführen. Sie können diesen Schritt auch überspringen und später ausführen.
4. Aktualisieren Sie Ihren Code. Ändern Sie beispielsweise die Datei `/public/index.html` oder eine ähnliche Datei. Wenn Sie die `ExpressJS`-Beispielanwendung verwenden, können Sie die Zeichenfolge `Congratulations!` in `Hello World!` oder eine ähnliche Zeichenfolge ändern.
5. Speichern Sie die geänderten Dateien.

## In {{site.data.keyword.cloud_notm}} bereitstellen
{: #deploy-app-cli}

Abhängig von der Konfiguration Ihrer App stehen zwei Möglichkeiten für die Bereitstellung Ihrer {{site.data.keyword.cloud_notm}}-App zur Verfügung. 

### App mithilfe einer DevOps-Toolchain bereitstellen
Wenn Sie noch keine DevOps-Toolchain für Ihre App erstellt haben und Ihre App sich noch nicht in einem Git-Repository befindet, können Sie den Befehl [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit) ausführen. Folgen Sie den Eingabeaufforderungen für die DevOps-Konfiguration und führen Sie eine Bereitstellung für eine neue Toolchain durch (und erstellen Sie ein neues GitLab-Repository).

Nachdem Sie eine DevOps-Toolchain für Ihre App erstellt haben, müssen Sie zur Bereitstellung eines neuen Builds lediglich Ihren Code festschreiben und per Push-Operation in das Repository in der Toolchain übertragen. 

1. Führen Sie den Befehl `git add` aus.
2. Führen Sie den Befehl `git commit -m "made changes"` aus, um Änderungen festzuschreiben.
3. Führen Sie den Befehl `git push origin master` aus, um eine Push-Operation in den Masterzweig durchzuführen.
4. Zeigen Sie die DevOps-Toolchain für Ihre App über die {{site.data.keyword.cloud_notm}}-Konsole an. Sie können Toolchain-Details von der Seite **App-Details** in der {{site.data.keyword.cloud_notm}}-Konsole anzeigen, indem Sie den Befehl [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) im App-Verzeichnis ausführen.
5. Zeigen Sie die Pipeline in der Toolchain an, um sicherzustellen, dass ein neuer Build gestartet wurde.

### App manuell bereitstellen

Sie können Ihre App manuell bereitstellen, indem Sie den Befehl [`deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) verwenden. Führen Sie zum Beispiel die folgenden Schritte aus, um die App manuell in Kubernetes bereitzustellen.

1. Stellen Sie sicher, dass [ein Kubernetes-Cluster erstellt wurde](https://{DomainName}/containers-kubernetes/overview){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").
2. Führen Sie den Befehl [`ibmcloud dev deploy -t container`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) aus.
3. Bestätigen Sie den zu verwendenden Cluster- und Container-Image-Namen, wenn Sie dazu aufgefordert werden.
4. Warten Sie einige Minuten, bis die Bereitstellung abgeschlossen ist.

## App anzeigen
{: #view-app-cli}

1. Zum Anzeigen der URL Ihrer App, die in {{site.data.keyword.cloud_notm}} ausgeführt wird, führen Sie den Befehl [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) aus.
2. Zum Anzeigen von Details zu den Berechtigungsnachweisen, den Services und der Toolchain Ihrer App über die {{site.data.keyword.cloud_notm}}-Konsole führen Sie den Befehl [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) aus. 

**Wenn Sie Probleme melden oder Feedback geben möchten, können Sie den [{{site.data.keyword.cloud_notm}}-Tech-Slack-Kanal für Entwicklertools (#developer-tools)](https://ibm-cloud-tech.slack.com){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") aufrufen. Teamzugriff [hier](https://slack-invite-ibm-cloud-tech.mybluemix.net/){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") anfordern.**
