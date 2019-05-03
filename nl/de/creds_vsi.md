---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-14"

keywords: apps, credentials, virtual server instance, vsi, virtual machine, vm

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Berechtigungsnachweise Ihrer virtuellen Instanz oder lokalen Docker-Umgebung hinzufügen
{: #add-credentials-vsi}

Hier erfahren Sie, wie Sie Ihrer virtuellen Serverinstanz oder lokalen Docker-Bereitstellungsumgebung Serviceberechtigungsnachweise hinzufügen.
{: shortdesc}

## Ihr Code + Virtual Server-Instanz oder lokale Docker-Instanz
{: #credentials-byoc-vsi}

Sowohl bei einer VSI als auch einer lokalen Docker-Instanz gehört die Umgebung vollständig Ihnen. Beispielsweise können Sie Ihren Code wie im folgenden Beispiel schreiben und Ihrer Anwendung den Umgebungswert des Berechtigungsnachweises bei der Ausführung bereitstellen.
```
password = getEnvironment('password');
```
{: codeblock}

In Bash können Sie Ihren Code wie im folgenden Beispiel schreiben:
```bash
export password="someThingSensitive"
# run app locally.  If node, something like:
npm run start
```
{: codeblock}

In Docker können Sie Ihren Code wie im folgenden Beispiel schreiben:
```
docker run -p 80:8080 -e password="someThingSensitive"
```
{: codeblock}

## Starter-Kit + VSI (oder lokale Docker-Instanz)
{: #credentials-starterkit-vsi}

### Vorbereitung der virtuellen Serverinstanz

Die Umgebung ist vollständig unter Ihrer Kontrolle, so als ob Sie die Anwendung auf Ihrem Notebook ausführen. Mit anderen Worten: lokale Docker-Instanz. Da es sich bei der VSI aus der Perspektive der aktiven Anwendung um Bare Metal handelt, gibt es keine _geheimen Schlüssel_ (wie in Kubernetes) oder _Services_ (wie in Cloud Foundry).

### Vom Starter-Kit generierter Code
{: #starterkit-generated-code-vsi}

Code, der von einem Starter-Kit generiert wird, verfügt über die native Bibliothek `IBMCloudEnv`, die den Abruf von Umgebungswerten abstrahiert, sodass der Anwendungscode portierbar ist und auf mehreren Bereitstellungszielen ausgeführt werden kann. Bei virtueller oder lokaler Docker-Instanz muss diese Umgebung mit Werten vorbereitet werden, die der Bibliothek `IBMCloudEnv` gerecht werden und _nicht unbedingt_ aus tatsächlichen Umgebungsvariablen stammen.

Die `mappings.json`-Anweisungen, die in der Starter-Kit-generierten Ausgabe enthalten sind, enthalten Verweise auf eine lokale Datei, aus der die Bibliothek `IBMCloudEnv` die Werte beschafft, die die Anwendung verwenden kann.

Beachten Sie z. B. die letzte Zeile im folgenden Abschnitt aus der Datei `mappings.json`:
```json
"cloudant_apikey": {
  "searchPatterns": [
    "user-provided:blarg-cloudant-1538408663553:apikey",
    "cloudfoundry:$['cloudant'][0].credentials.apikey",
    "env:service_cloudant:$.apikey",
    "env:cloudant_apikey",
    "file:/server/localdev-config.json:$.cloudant_apikey"
  ]
},
```
{: codeblock}

Wenn Sie die Funktion "Continuous Delivery konfigurieren" verwenden, wenn Sie eine App erstellen, wird die Datei `/server/localdev-config.json` aus dem GitLab-Repository entfernt. Aus Sicherheitsgründen möchten Sie Ihre Berechtigungsnachweise nicht in ein Quellcode-Repository stellen.

Wenn Sie `git clone` für das erstellte GitLab-Repository verwenden, um die aktive Entwicklung zu starten, beachten Sie, dass die Datei `.gitignore` ausdrücklich die Datei `server/localdev-config.json` ignoriert, um ein versehentliches Einchecken einer Datei mit sensiblen Berechtigungsnachweisen zu verhindern. VSI _benötigt_ jedoch diese Datei, ebenso wie der Entwickler, der auf einem Notebook arbeitet.

Sie können die Datei `server/localdev-config.json` abrufen, indem Sie die folgenden Schritte ausführen:

1. Verwenden Sie `git clone` für das GitLab-Repository, das automatisch erstellt wurde, als Sie die Funktion "Continuous Delivery konfigurieren" verwendet haben.
2. Installieren Sie die [{{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle](/docs/cli?topic=cloud-cli-ibmcloud-cli), die das Plug-in `dev` enthält.
3. Verwenden Sie die `ibmcloud`-Befehlszeile, um sich bei {{site.data.keyword.cloud_notm}} anzumelden.
4. Führen Sie den Befehl `ibmcloud dev get-credentials` aus, der auf die Datei `cli-config.yml` verweist. Die Datei `cli-config.yml` enthält Informationen darüber, welcher Anwendungs- und Generierungsjob über die Berechtigungsnachweise verfügt.

Wenn ein Service zwischen der Verwendung der Funktion "Continuous Delivery konfigurieren" und der Ausführung des Befehls `ibmcloud dev get-credentials` aus der Anwendung entfernt wird, würde die heruntergeladene Datei `/server/localdev-config.json` nicht alle Berechtigungsnachweise enthalten, die Ihre ursprüngliche `git clone`-Codebasis möglicherweise benötigt.
{: tip}

Wenn Sie Ihre Anwendung in einem Docker-Container ausführen, können Sie die Datei `/server/localdev-config.json` vollständig entfernen und die Umgebungsvariablen in der Docker-Befehlszeile übergeben.

Beachten Sie im Abschnitt "cloudant_apikey" in der Datei `mappings.json` die Zeile `env:cloudant_apikey` vor der Zeile `file...`. Sie bedeutet, dass eine Umgebungsvariable mit dem Namen `cloudant_apikey` Vorrang vor dem Inhalt der Datei hat. Selbst wenn die Datei in dem von Ihnen erstellten Docker-Image vorhanden ist (was nicht erforderlich ist), können Sie Werte überschreiben, indem Sie sie in der Docker-Befehlszeile übergeben.

Beispiel:
```
docker run -p 80:8080 -e cloudant_apikey="someKeyValue"
```
{: codeblock}
