---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-04"

keywords: apps, credentials, kubernetes, kube, add, custom, deployment.yml, cluster, deployment, environment, kubectl, secret

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# Aggiunta di credenziali al tuo ambiente Kubernetes
{: #add-credentials-kube}

Acquisisci informazioni su come aggiungere credenziali del servizio al tuo ambiente di distribuzione Kubernetes.
{: shortdesc}

Devi aggiungere manualmente le credenziali del servizio al tuo ambiente di distribuzione in questi scenari:
 * Porti il tuo codice personale.
 * Inizi da un template di kit starter vuoto.
 * Aggiungi un servizio a un'applicazione basata sul kit starter _dopo_ che ne è stata eseguita la distribuzione.

## Il tuo codice + Kubernetes
{: #credentials-byoc-kube}

<!-- (Refer to the ["Code it Right"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#code-it-right) and ["Prepare the Environment"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#prepare-the-environment) sections.  But translate a bit so we're only mentioning editing a `deployment.yml` file, not the "deployment.yml section of the script in the Deploy pipeline stage configuration".) -->

### Codifica nel modo corretto

Come precauzione, puoi codificare la tua applicazione per confermare che il suo ambiente è completo nel punto di ingresso principale della tua applicazione. Evita di promuovere un'applicazione in un cluster il cui ambiente non è completo per evitare interruzioni del servizio per il tuo prodotto. L'avvio dell'applicazione potrebbe essere rifiutato e la tua configurazione Kubernetes può automaticamente prevenire tali interruzioni del servizio.

Presumi di avere le due variabili di ambiente di seguito indicate:
* `SECRET`
* `NOT_SECRET`

Per un database, le tue variabili possono essere `APIKEY` e `DB_URL`, dove la prima è sensibile e la seconda no.

In Java, potresti voler scrivere qualcosa nel punto d'ingresso dell'applicazione principale come:
```java
if (System.getenv("SECRET") == null) {
    throw new RuntimeException("Environment variable 'SECRET' is not set!");
}
// and many more checks...
```
{: codeblock}

In Node, vedi un esempio simile:
```js
if (!process.env.SECRET) {
    console.error('ENVIRONMENT variable "SECRET" is not set!');
    process.exit(1);
}
// and many more checks...
```
{: codeblock}

### Prepara l'ambiente

nel file `deployment.yml` Kubernetes, possono essere definite le variabili di ambiente o un _riferimento a un segreto nel cluster_.

#### Imposta la distribuzione per ottenere le credenziali dall'ambiente

Nella sezione con `kind: Deployment`, aggiungi il seguente codice di esempio a un livello del rientro dopo `spec.template.spec.containers`:
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

* Fai clic su **Save**.

Configura il cluster in modo che la _secretKeyRef_ con il nome `name-secret` e la chiave `KEY_SECRET` venga risolta in un valore.

#### Installazione degli strumenti prerequisiti

Utilizza un terminale sulla tua workstation per installare i seguenti strumenti:

1. Installa la [CLI {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).
2. Esegui l'accesso utilizzando il comando `ibmcloud login`.
3. Stabilisci una connessione al tuo cluster eseguendo `ibmcloud cs cluster-config {your_cluster_name}`.
4. Copia e incolla il comando `export` per eseguirlo da un terminale.

#### Definisci il segreto nel cluster

La {{site.data.keyword.dev_cli_notm}} fornisce `kubectl`, che puoi eseguire perché sei connesso al tuo cluster Kubernetes.

Per definire il segreto risolvibile, utilizza questi comandi `kubectl`:
```console
echo -n 'This is the secret.  Shhhhh!' > ./KEY_SECRET
```
{: codeblock}

```console
kubectl create secret generic name-secret --from-file=./KEY_SECRET
```
{: codeblock}

Ora che il cluster Kubernetes è preparato con un segreto risolvibile, puoi aggiornare la tua applicazione per utilizzare le variabili di ambiente che sono definite nel file `deployment.yml`.

## Applicazione kit starter e Kubernetes
{: #credentials-starterkit-kube}

1. Vai alla pagina **App details** della tua applicazione.

2. Per creare un'istanza di Cloud Object Storage, seleziona **Add service** > **Storage** > **Cloud Object Storage** > **Lite plan (Free)** > **Create**.

3. Fai clic su **Download code** per rigenerare la tua applicazione con i frammenti di codice inseriti.

4. Per accedere alle credenziali localmente, copia e sostituisci i seguenti file dal file `.zip` appena generato al tuo clone Git locale per accedere alle credenziali. Devi ancora creare un segreto Kubernetes nel tuo cluster per ospitare le credenziali.

   - `chart/{appName}/bindings.yaml` - genera una variabile di ambiente nel tuo cluster Kubernetes che punta al tuo segreto.
   - `src/main/resources/localdev-config.json` - Accedi alle credenziali mentre esegui la tua applicazione in locale.
   - `src/main/resources/mappings.json` - un'associazione per fornire l'accesso al metodo [`env.getProperty()`](/docs/java-spring?topic=java-spring-configuration#accessing-credentials) per accedere alle tue variabili di ambiente dal codice.
   - `manifest.yml` - questo file esegue il bind del tuo servizio alla tua applicazione Cloud Foundry.

  Se in un secondo momento scegli di eseguire una distribuzione a un'applicazione Cloud Foundry con una risorsa Resource Controller (che si trova in un gruppo di risorse invece che in un'organizzazione o uno spazio), devi copiare un altro file.
  {: note}

5. [Visualizza il tuo cluster Kubernetes](https://{DomainName}/kubernetes/clusters){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") con la regione corrispondente (Stati Uniti Sud se era gratuito).

6. Fai clic nel tuo cluster e seleziona **Kubernetes Dashboard** nell'angolo superiore destro per visualizzare il tuo dashboard del cluster.

7. Scorri verso il basso fino a visualizzare una sezione denominata **Secrets**. Puoi vedere un segreto per la tua istanza del servizio {{site.data.keyword.cloudant_short_notm}} che utilizza la seguente convenzione `binding-{appName}-{serviceName}-{timestamp}`. Nel file `chart/{appName}/bindings.yaml`, puoi trovare il segreto {{site.data.keyword.cloudant_short_notm}} corrispondente.

8. Ora puoi crearne uno corrispondente per la tua istanza Cloud Object Storage con il nome di segreto che è già generato in `chart/{appName}/bindings.yaml`, che è qualcosa simile a `binding-create-app-ktibr-cloudobjectstor-1538170732311`.

9. Vai alla pagina **App details** nel dashboard e copia le credenziali per l'istanza Cloud Object Storage. Vedi il seguente output di credenziali di esempio:
  ```yaml
  {
    "apikey": "hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg",
    "endpoints": "https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints",
    "resource_instance_id": "crn:v1:staging:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"
  }    
  ```
  {: codeblock}

10. Assicurati che il tuo cluster sia configurato utilizzando `ibmcloud cs cluster-config {your_cluster_name}` ed esportando il comando nelle istruzioni che seguono:

11. Utilizza il comando `echo` per posizionare le credenziali in un file `binding`.
  ```console
  echo -n '{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints","resource_instance_id":"crn:v1:staging:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}' > ./binding

  ```
  {: codeblock}

12. Crea il segreto con `kubectl create secret generic binding-create-app-ktibr-cloudobjectstor-15381707323113 --from-file=./binding`. Se torni al tuo dashboard cluster Kubernetes, puoi vedere il segreto che hai creato.

  Se stai eseguendo la distribuzione a un'applicazione Cloud Foundry, devi creare un servizio fornito dall'utente se stai utilizzando un'istanza Resource Controller (se la risorsa si trova in un gruppo di risorse invece che in un'organizzazione o uno spazio). 
  {: note}
  
  ```console
  ibmcloud cf create-user-provided-service create-app-ktibr-cloudobjectstor-1538170732311 -p `{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://control.cloud-object-storage.cloud.ibm.com/v2/endpoints","resource_instance_id":"ccrn:v1:staging:public:cloud-object-storage:global::a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}`
  ```
  {: codeblock}

  Il nome del tuo servizio fornito dall'utente è disponibile nel file `manifest.yml` con il nome istanza corrispondente.

13. Ora puoi accedere al tuo segreto tramite le variabili di ambiente mediante il metodo `env.getProperty` quando la tua applicazione è in esecuzione nel cluster Kubernetes.

### Come viene preparato il cluster Kubernetes

Utilizza la funzione **Configure continuous delivery** per distribuire la tua applicazione al tuo cluster IBM Kubernetes. La funzione prepara il tuo cluster Kubernetes con i segreti per le credenziali delle risorse associate alla tua applicazione. Puoi osservare i risultati della preparazione del cluster completando i seguenti passi:

1. Esegui questo comando per visualizzare i risultati: `kubectl get secrets`:
  ```
  NAME                                   TYPE                                  DATA      AGE
  binding-blarg-cloudant-1538408663553   Opaque                                1         13m
  bluemix-default-secret                 kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-international   kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-regional        kubernetes.io/dockerconfigjson        1         17d
  default-token-xfd5n                    kubernetes.io/service-account-token   3         17d
  ```
  {: screen}

  Puoi visualizzare [ulteriore documentazione sui segreti](https://kubernetes.io/docs/concepts/configuration/secret/).
  {: tip}

2. Osserva che il nome del segreto è il nome della risorsa.
3. Visualizza le informazioni dettagliate sul segreto utilizzando `kubectl get secret binding-blarg-cloudant-1538408663553 -o=yaml`:

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

  `binding` è il valore con codifica base64 del segreto. La sua decodifica rivela che è semplicemente il JSON non elaborato dalle credenziali (`credentials`) dell'istanza del servizio, più alcuni valori `iam_...`:
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

Il segreto Kubernetes non è richiamabile dal codice dell'applicazione a meno che `deployment.yml` non dichiari un valore `env` che fa riferimento al segreto. Quando utilizzi un kit starter, tale codice viene generato automaticamente.

### Il codice generato dal kit starter
{: #credentials-starterkit-kube-gencode}

In questo caso, hai creato questa applicazione da un kit starter. Il codice generato da un kit starter è fatto per essere portatile per un'esecuzione in locale, in Cloud Foundry o in Kubernetes. La libreria `IBMCloudEnv` viene utilizzata per fornire un livello di astrazione tra il codice dell'applicazione e il richiamo delle variabili di ambiente che detengono le credenziali per le istanze del servizio.

Il codice creato dal kit starter ha una dipendenza per la libreria `IBMCloudEnv` e produce il seguente output:

* Un file `bindings.yml`, che è incluso come parte integrante nel file `deployment.yml`, con questo contenuto:
  ```yaml
   - name: service_cloudant
     valueFrom:
     secretKeyRef:
        name: binding-blarg-cloudant-1538408663553
        key: binding
        optional: true
  ```
  {: codeblock}

  `secretKeyRef.name` espone il segreto Kubernetes definito in modo che sia richiamabile dall'applicazione come una semplice variabile di ambiente nel codice dell'applicazione.

* Le istruzioni per la libreria `IBMCloudEnv` vengono incapsulate in un file `mappings.json`, che è la base di codice generata dal kit starter. `mappings.json` ha delle singole definizioni per ciascuna credenziale:
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

  Il file `mappings.json` utilizza la sintassi `jsonpath` e l'ordine dell'array `searchPatterns` per guidare la logica `IBMCloudEnv`.

* Utilizza il seguente codice per richiamare la chiave API Cloudant (pseudocodice):
  ```java
  cloudantApiKey = IBMCloudEnv.getValue('cloudant_apikey');
  ```
  {: codeblock}

La libreria `IBMCloudEnv` rileva automaticamente se la tua applicazione è in esecuzione in Kubernetes, Cloud Foundry o una VSI (Virtual Server Instance) (trattata in modo uguale a un docker locale) e applica il `searchPattern` corretto per trovare il valore da restituire.

Pertanto, il file `mappings.json` deve essere considerato _l'elenco definitivo_ di valori immediatamente disponibili e preconfigurati provenienti dall'ambiente in cui deve essere eseguita la tua applicazione. I valori vengono compilati nell'ambiente per il cluster da te selezionato quando hai utilizzato la funzione **Configure continuous delivery**.
