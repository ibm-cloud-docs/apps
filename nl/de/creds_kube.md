---

copyright:
  years: 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# Berechtigungsnachweise Ihrer Kubernetes-Umgebung hinzufügen
{: #add_credentials}

Hier erfahren Sie, wie Sie Serviceberechtigungsnachweise Ihrer Kubernetes-Bereitstellungsumgebung hinzufügen.
{: shortdesc}

In den folgenden Szenarios müssen Sie Ihrer Bereitstellungsumgebung Serviceberechtigungsnachweise manuell hinzufügen:
 * Sie integrieren Ihren eigenen Code.
 * Sie beginnen mit einer leeren Starter-Kit-Vorlage.
 * Sie fügen einen Service einer Starter-Kit-basierten App hinzu, _nachdem_ sie bereitgestellt wurde.

## Ihr Code + Kubernetes
{: #byoc_kube}

<!-- (Refer to the ["Code it Right"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#code-it-right) and ["Prepare the Environment"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#prepare-the-environment) sections.  But translate a bit so we're only mentioning editing a `deployment.yml` file, not the "deployment.yml section of the script in the Deploy pipeline stage configuration".) -->

### Codieren Sie richtig

Als Vorsichtsmaßnahme können Sie Ihre Anwendung so codieren, dass ihre Umgebung vollständig im Haupteingangspunkt Ihrer Anwendung ist. Sie möchten keine Anwendung in einen Cluster weiterleiten, dessen Umgebung nicht vollständig ist, um Ausfälle Ihres Produkts zu vermeiden. Möglicherweise kann die Anwendung nicht gestartet werden, und Ihre Kubernetes-Konfiguration kann solche Ausfälle automatisch verhindern.

Nehmen Sie an, Sie haben die beiden folgenden Umgebungsvariablen:
* `SECRET`
* `NOT_SECRET`

Bei einer Datenbank könnten Ihre Variablen `APIKEY` und `DB_URL` sein, wobei die erstere sensibel ist und die letztere nicht.

In Java könnten Sie in den Haupteingangspunkt der Anwendung etwa Folgendes schreiben:
```java
if (System.getenv("SECRET") == null) {
    throw new RuntimeException("Environment variable 'SECRET' is not set!");
}
// and many more checks...
```
{: codeblock}

Ein ähnliches Beispiel in Node:
```js
if (!process.env.SECRET) {
    console.error('ENVIRONMENT variable "SECRET" is not set!');
    process.exit(1);
}
// and many more checks...
```
{: codeblock}

### Vorbereitung der Umgebung

In der Kubernetes-Datei `deployment.yml` können die Umgebungsvariablen oder eine _Referenz auf einen geheimen Schlüssel im Cluster_ definiert werden.

#### Einrichtung der Bereitstellung für das Abrufen von Berechtigungsnachweisen aus der Umgebung

Fügen Sie im Abschnitt mit `kind: Deployment` den folgenden Beispielcode auf einer Einrückungsstufe nach `spec.template.spec.containers` hinzu:
```yaml
env:
  - name: SECRET
    valueFrom:
      secretKeyRef:
          name: name-secret
          key: KEY_SECRET
  - name: NOT_SECRET
    value: "I'm not a secret"
```
{: codeblock}

* Klicken Sie auf **Speichern**.

Konfigurieren Sie den Cluster so, dass der Parameter _secretKeyRef_ mit dem Namen `name-secret` und dem Schlüssel `KEY_SECRET` in einen Wert aufgelöst wird.

#### Vorausgesetzte Tools installieren

Verwenden Sie ein Terminal Ihrer Workstation zum Installieren der folgenden Tools:

1. Installieren Sie die [{{site.data.keyword.dev_cli_long}}-Befehlszeilenschnittstelle](/docs/cli/index.html).
2. Melden Sie sich mit dem Befehl `ibmcloud login` an.
3. Stellen Sie eine Verbindung zu Ihrem Cluster her, indem Sie `ibmcloud cs cluster-config {ihr_cluster_name}` ausführen.
4. Kopieren Sie den Befehl `export` und fügen Sie ihn ein, um ihn von einem Terminal aus auszuführen.

#### Geheimen Schlüssel im Cluster definieren

Die {{site.data.keyword.dev_cli_notm}} stellen `kubectl` bereit, das Sie ausführen können, da Sie mit Ihrem Kubernetes-Cluster verbunden sind.

Verwenden Sie die folgenden `kubectl`-Befehle, um den auflösbaren geheimen Schlüssel zu definieren:
```console
echo -n 'This is the secret.  Shhhhh!' > ./KEY_SECRET
```
{: codeblock}

```console
kubectl create secret generic name-secret --from-file=./KEY_SECRET
```
{: codeblock}

Da der Kubernetes-Cluster jetzt mit einem auflösbaren geheimen Schlüssel vorbereitet ist, können Sie Ihre Anwendung so aktualisieren, dass sie die Umgebungsvariablen verwendet, die in der Datei `deployment.yml` definiert sind.

## Starter-Kit-App + Kubernetes
{: #sk_kube}

1. Rufen Sie die Seite Ihrer App mit den **App-Details** auf.
2. Wählen Sie zum Erstellen einer Instanz von Cloud Object Storage **Ressource hinzufügen** > **Speicher** > **Cloud Object Storage** > **Lite-Plan (kostenfrei)** > **Erstellen** aus.
3. Klicken Sie auf `Code herunterladen`, um Ihr Projekt mit den injizierten Code-Snippets neu zu generieren.
4. Wenn Sie auf die Berechtigungsnachweise lokal zugreifen möchten, kopieren Sie die folgenden Dateien aus der neu generierten `.zip`-Datei auf Ihren lokalen Git-Klon (und ersetzen Sie dabei bereits vorhandene Versionen), um auf die Berechtigungsnachweise zuzugreifen. Sie müssen immer noch einen geheimen Kubernetes-Schlüssel in Ihrem Cluster erstellen, um die Berechtigungsnachweise zu hosten.

	- `chart/{appName}/bindings.yaml` - Generiert eine Umgebungsvariable in Ihrem Kubernetes-Cluster, die auf Ihren geheimen Schlüssel verweist.
	- `src/main/resources/localdev-config.json` - Auf Berechtigungsnachweise während der lokalen Ausführung Ihrer App zugreifen.
  - `src/main/resources/mappings.json` - Eine Zuordnung für die Bereitstellung des Zugriffs auf die Methode [`env.getProperty()`](/docs/java-spring/configuration.html#configuration#accessing-credentials) für den Zugriff auf Ihre Umgebungsvariablen aus dem Code.
  - `manifest.yml` - Diese Datei bindet Ihren Service an Ihre Cloud Foundry-Anwendung.

Wenn Sie sich später für eine Bereitstellung einer Cloud Foundry-Anwendung mit einer Resource Controller-Ressource entscheiden (die sich in einer Ressourcengruppe und nicht in einer Organisation oder einem Bereich befindet), müssen Sie eine weitere Datei kopieren.
{: note}

5. [Zeigen Sie](https://cloud.ibm.com/containers-kubernetes/clusters) Ihren Kubernetes-Cluster mit der entsprechenden Region an (Vereinigte Staaten (Süden), wenn er kostenfrei war).
6. Klicken Sie in Ihren Cluster und wählen Sie **Kubernetes-Dashboard** oben rechts aus, um Ihr Cluster-Dashboard anzuzeigen.
7. Blättern Sie nach unten, bis Sie einen Abschnitt mit der Bezeichnung **Geheime Schlüssel** sehen. Sie können einen geheimen Schlüssel für Ihre {{site.data.keyword.cloudant_short_notm}}-Serviceinstanz mit der folgenden Konvention sehen: `binding-{appName}-{serviceName}-{zeitmarke}`. In der Datei `chart/{appName}/bindings.yaml` können Sie den entsprechenden geheimen {{site.data.keyword.cloudant_short_notm}}-Schlüssel finden.
8. Sie können jetzt einen entsprechenden geheimen Schlüssel für Ihre Cloud Object Storage-Instanz mit dem Namen erstellen, der bereits in der Datei `chart/{appName}/bindings.yaml` generiert wurde und etwa wie folgt aussieht: `binding-create-app-ktibr-cloudobjectstor-1538170732311`.
9. Rufen Sie die Seite mit den **App-Details** im Dashboard auf und kopieren Sie die Berechtigungsnachweise für die Cloud Object Storage-Instanz. Es folgt ein Beispiel für eine Berechtigungsnachweisausgabe:
```yaml
{
  "apikey": "hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg",
  "endpoints": "https://cos-service.bluemix.net/endpoints",
  "resource_instance_id": "crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"
}    
```
{: codeblock}

10. Stellen Sie sicher, dass Ihr Cluster unter Verwendung von `ibmcloud cs cluster-config {ihr_cluster_name}` konfiguriert und der Befehl in den nachfolgenden Anweisungen exportiert wird.
11. Verwenden Sie den Befehl `echo`, um die Berechtigungsnachweise in eine Bindungsdatei (`binding`) zu stellen.
  ```console
  echo -n '{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://cos-service.bluemix.net/endpoints","resource_instance_id":"crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}' > ./binding

  ```
  {: codeblock}

12. Erstellen Sie den geheimen Schlüssel mit `kubectl create secret generic binding-create-app-ktibr-cloudobjectstor-15381707323113 --from-file=./binding`. Wenn Sie in Ihr Kubernetes-Cluster-Dashboard zurückkehren, können Sie den von Ihnen erstellten geheimen Schlüssel sehen.

Wenn die Bereitstellung in eine Cloud Foundry-Anwendung erfolgt, müssen Sie einen vom Benutzer zur Verfügung gestellten Service erstellen, wenn Sie eine Resource Controller-Instanz verwenden (wenn sich die Ressource in einer Ressourcengruppe und nicht in einer Organisation oder einem Bereich befindet).
{: note}
  
  ```console
  ibmcloud cf create-user-provided-service create-app-ktibr-cloudobjectstor-1538170732311 -p `{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://cos-service.bluemix.net/endpoints","resource_instance_id":"crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}`
  ```
  {: codeblock}

  Der Name Ihres vom Benutzer zur Verfügung gestellten Service befindet sich in der Datei `manifest.yml` mit dem entsprechenden Instanznamen.

13. Sie können jetzt über die Umgebungsvariablen über die Methode `env.getProperty` auf ihren geheimen Schlüssel zugreifen, wenn Ihre Anwendung in Ihrem Kubernetes-Cluster ausgeführt wird.

### Vorbereitung des Kubernetes-Clusters

Verwenden Sie die Funktion **In Cloud bereitstellen**, um Ihre App in Ihrem IBM Containers-Kubernetes-Cluster bereitzustellen. Die Funktion bereitet Ihren Kubernetes-Cluster mit geheimen Schlüsseln für die Berechtigungsnachweise der Ressourcen vor, die Ihrer App zugeordnet sind. Sie können die Ergebnisse der Clustervorbereitung anzeigen, indem Sie die folgenden Schritte ausführen:

1. Führen Sie den folgenden Befehl aus, um die Ergebnisse anzuzeigen: `kubectl get secrets`:
  ```
  NAME                                   TYPE                                  DATA      AGE
  binding-blarg-cloudant-1538408663553   Opaque                                1         13m
  bluemix-default-secret                 kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-international   kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-regional        kubernetes.io/dockerconfigjson        1         17d
  default-token-xfd5n                    kubernetes.io/service-account-token   3         17d
  ```
  {: screen}

  Sie können [weitere Informationen zu geheimen Schlüsseln](https://kubernetes.io/docs/concepts/configuration/secret/) anzeigen.   {: tip}

2. Beachten Sie, dass der Name des geheimen Schlüssels der Ressourcenname ist.
3. Zeigen Sie ausführliche Informationen zu dem geheimen Schlüssel unter Verwendung von `kubectl get secret binding-blarg-cloudant-1538408663553 -o=yaml` an:

  ```
  apiVersion: v1
  data:
    binding: eyJhcGlrZXkiOiI4RFprT3VMVnduVkExWW1HODFnazNQMjZOeThlNWFWbjVhaFpZLVVEOHQ1NCIsImhvc3QiOiI1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJpYW1fYXBpa2V5X2Rlc2NyaXB0aW9uIjoiQXV0byBnZW5lcmF0ZWQgYXBpa2V5IGR1cmluZyByZXNvdXJjZS1rZXkgb3BlcmF0aW9uIGZvciBJbnN0YW5jZSAtIGNybjp2MTpibHVlbWl4OnB1YmxpYzpjbG91ZGFudG5vc3FsZGI6dXMtc291dGg6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzpiZmEzNDJkZC00YjZmLTRkZmUtYTM1YS05MTA4ZmIwZWM1NzE6OiIsImlhbV9hcGlrZXlfbmFtZSI6ImF1dG8tZ2VuZXJhdGVkLWFwaWtleS01MzI3ZWMxZC0wOWE1LTQyMzctOTczNS03ZTAxZmU3NDFiYzciLCJpYW1fcm9sZV9jcm4iOiJjcm46djE6Ymx1ZW1peDpwdWJsaWM6aWFtOjo6OnNlcnZpY2VSb2xlOldyaXRlciIsImlhbV9zZXJ2aWNlaWRfY3JuIjoiY3JuOnYxOmJsdWVtaXg6cHVibGljOmlhbS1pZGVudGl0eTo6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzo6c2VydmljZWlkOlNlcnZpY2VJZC1mNWRhMjMwYy1kNDE0LTQ4NTQtYjE1Yi00MmJmZmRhYWVmNWIiLCJwYXNzd29yZCI6ImY4MjU2ZDJhODYyMjI5NzViZDI3Mjc1MjEzMTY4YTQyNzBhNDZmMmEyOGQ5NDkyMjRhYzFjOTc3NjMwMWNlZTYiLCJwb3J0Ijo0NDMsInVybCI6Imh0dHBzOi8vNTlhYTdiMWEtNWFhYi00ZjJkLTlhNzMtOGMzYjI5NDA4Zjk2LWJsdWVtaXg6ZjgyNTZkMmE4NjIyMjk3NWJkMjcyNzUyMTMxNjhhNDI3MGE0NmYyYTI4ZDk0OTIyNGFjMWM5Nzc2MzAxY2VlNkA1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJ1c2VybmFtZSI6IjU5YWE3YjFhLTVhYWItNGYyZC05YTczLThjM2IyOTQwOGY5Ni1ibHVlbWl4In0=
  kind: Secret
  metadata:
    annotations:
      service-instance-id: 'crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::'
      service-key-id: 5327ec1d-09a5-4237-9735-7e01fe741bc7
    creationTimestamp: 2018-10-01T15:45:02Z
    name: binding-blarg-cloudant-1538408663553
    namespace: default
    resourceVersion: "155591"
    selfLink: /api/v1/namespaces/default/secrets/binding-blarg-cloudant-1538408663553
    uid: f5e7885c-c590-11e8-ad83-8e37f3f3216f
  type: Opaque
  ```
  {: screen}

  Hinter `binding` steht der Base64-codierte Wert des geheimen Schlüssels. Das Dekodieren zeigt, dass es sich nur um das unformatierte JSON aus den Berechtigungsnachweisen (`credentials`) der Ressourceninstanz handelt, plus einige `iam_...` -Werte:
  ```
  {
    "apikey": "8DZkOuLVwnVA1YmG81gk3P26Ny8e5aVn5ahZY-UD8t54",
    "host": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "iam_apikey_description": "Auto generated apikey during resource-key operation for Instance - crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::",
    "iam_apikey_name": "auto-generated-apikey-5327ec1d-09a5-4237-9735-7e01fe741bc7",
    "iam_role_crn": "crn:v1:bluemix:public:iam::::serviceRole:Writer",
    "iam_serviceid_crn": "crn:v1:bluemix:public:iam-identity::a/480fd1ec14ac540c5bc37da799a63437::serviceid:ServiceId-f5da230c-d414-4854-b15b-42bffdaaef5b",
    "password": "f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6",
    "port": 443,
    "url": "https://59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix:f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6@59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "username": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix"
  }
  ```
  {: screen}

Der geheime Kubernetes-Schlüssel kann von Ihrem Anwendungscode nicht abgerufen werden, es sei denn, die Datei `deployment.yml` deklariert einen `env`-Wert, der auf den geheimen Schlüssel verweist. Wenn Sie ein Starter-Kit verwenden, wird solcher Code automatisch generiert.

### Vom Starter-Kit generierter Code
{: #sk_kube_generated_code}

In diesem Fall haben Sie diese Anwendung aus einem Starter-Kit erstellt. Der Code, der aus einem Starter-Kit generiert wird, ist portierbar, um lokal, in Cloud Foundry oder in Kubernetes ausgeführt werden zu können. Die Bibliothek `IBMCloudEnv` wird verwendet, um eine Abstraktionsebene zwischen dem Anwendungscode und dem Abrufen der Umgebungsvariablen bereitzustellen, die die Berechtigungsnachweise für die Ressourcen (Serviceinstanzen) enthalten.

Der Code, der aus dem Starter-Kit erstellt wird, weist eine Abhängigkeit für die Bibliothek `IBMCloudEnv` auf und erzeugt die folgende Ausgabe:

* Eine Datei `bindings.yml`, die inline in der Datei `deployment.yml` enthalten ist, mit diesem Inhalt:
  ```yaml
   - name: service_cloudant
     valueFrom:
     secretKeyRef:
        name: binding-blarg-cloudant-1538408663553
        key: binding
        optional: true
  ```
  {: codeblock}

  Mit `secretKeyRef.name` wird der definierte geheime Kubernetes-Schlüssel für die Anwendung als eine einfache Umgebungsvariable im Anwendungscode verfügbar gemacht.

* Die Anweisungen für die Bibliothek `IBMCloudEnv` sind in einer Datei `mappings.json` eingebunden, die sich in der vom Starter-Kit generierten Codebasis befindet. Die Datei `mappings.json` verfügt über individuelle Definitionen für jeden Berechtigungsnachweis:
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

  Die Datei `mappings.json` verwendet die `JSONPath`-Syntax und die Reihenfolge des `searchPatterns`-Arrays, um die `IBMCloudEnv`-Logik zu steuern.

* Verwenden Sie den folgenden Code, um den Cloudant-API-Schlüssel (Pseudocode) abzurufen:
  ```java
  cloudantApiKey = IBMCloudEnv.getValue('cloudant_apikey');
  ```
  {: codeblock}

Die Bibliothek `IBMCloudEnv` erkennt automatisch, ob Ihre Anwendung in Kubernetes, Cloud Foundry oder einer virtuellen Serverinstanz (wird wie eine lokale Docker-Instanz behandelt) ausgeführt wird, und wendet das richtige Suchmuster (`searchPattern`) an, um den zurückzugebenden Wert zu finden.

Daher ist die Datei `mappings.json` als _die verbindliche Liste_ vorkonfigurierter und sofort verfügbarer Werte aus der Umgebung zu betrachten, in der Ihre App ausgeführt werden soll. Die Werte werden in der Umgebung für den Cluster gefüllt, den Sie zum Zeitpunkt der Verwendung der Funktion **In Cloud bereitstellen** als Ziel verwendet haben.

**Vorsicht**: Zum Zeitpunkt der Erstellung dieser Dokumentation wird die Umgebungsvorbereitung _immer_ für alle Berechtigungsnachweise für alle Ressourcen ausgeführt, die einer App zugeordnet sind, aber _nicht alle `env`-Referenzen_ werden in die Datei `bindings.yml` oder `mappings.json` gestellt. In diesen Fällen müssen Sie solche Referenzen selbst angeben. Wenn Sie sich bereits für eine Zielbereitstellung entschieden haben und die Abstraktion der Bibliothek `IBMCloudEnv` nicht benötigen, lesen Sie den Abschnitt "Ihr Code + (Zielbereitstellung)", der mit Ihrer Entscheidung übereinstimmt.

Einige Starter-Kits enthalten gar keine Referenz auf die `IBMCloudEnv`-Abhängigkeit oder die Dateien `manifest.yml` und `mappings.json`.
{: note}
