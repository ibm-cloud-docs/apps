---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Distribuzione della tua applicazione Mendix su {{site.data.keyword.containerlong_notm}}
{: #deploy-mendix-kube}

Per impostazione predefinita, le applicazioni Mendix che indirizzano la distribuzione a {{site.data.keyword.containerlong}} sono impostate in una modalità di valutazione. Questa modalità ti consente di iniziare a creare un'applicazione rapidamente e di eseguire la distribuzione al cloud ma non configura la persistenza dei dati o le configurazioni Kubernetes avanzate. Questa esercitazione ti illustra le varie fasi della configurazione di un ambiente di produzione impostando un volume di archiviazione persistente in Kubernetes con il servizio {{site.data.keyword.cos_full_notm}}.
{: shortdesc}

## Prima di iniziare
{: #prereqs-mendix-kube}

- Crea la tua applicazione Mendix. Per ulteriori informazioni, vedi [Creazione di applicazioni con Mendix](/docs/apps/tutorials/tutorial_mendix_getting_started.html#create-mendix).
- Installa la [CLI (command-line interface) {{site.data.keyword.dev_cli_notm}}](/docs/cli/index.html), che include la CLI {{site.data.keyword.containershort_notm}}.
- Accedi alla CLI `ibmcloud` e configura `kubectl` per l'[accesso al cluster Kubernetes](/docs/containers/cs_tutorials.html#cs_cluster_tutorial_lesson3).

## Creazione di un'istanza del servizio Cloud Object Storage
{: #cos-mendix-kube}

Inizia dalla pagina dei dettagli della tua applicazione e utilizza i seguenti passi:
1. Fai clic su **Add Resource**.
2. Seleziona **Storage** e fai clic su **Next**.
3. Seleziona quindi l'opzione **Cloud Object Storage** e fai clic su **Next**.
4. Ti vengono presentati i piani di prezzi per la tua istanza {{site.data.keyword.cos_full_notm}}. Seleziona il piano di prezzi più adatto alle tue esigenze e fai quindi clic su **Crea** per creare un'istanza del servizio {{site.data.keyword.cos_full_notm}} per l'utilizzo con la tua applicazione Mendix.

  Se preferisci utilizzare un'istanza esistente del servizio {{site.data.keyword.cos_full_notm}}, fai clic su **Add Resource** e seleziona l'istanza esistente per l'utilizzo da parte della tua applicazione.
  {: tip}

## Creazione di un bucket di archiviazione
{: #storage-bucket-mendix-kube}

Dopo che un'istanza del servizio {{site.data.keyword.cos_full_notm}} è stata associata alla tua applicazione Mendix, devi creare un bucket di archiviazione dove possono essere salvati i tuoi dati. Per creare un bucket, fai clic su **...** per l'istanza {{site.data.keyword.cos_full_notm}} e seleziona **Open Dashboard**.  

Il dashboard del servizio {{site.data.keyword.cos_full_notm}} viene aperto in una nuova finestra, nella scheda **Buckets**. Fai clic su **Create Bucket** e attieniti alla procedura per creare un bucket utilizzando un nome univoco. Ai fini di questa esercitazione, crea un bucket denominato `my-mendix-bucket`.

## Configurazione dell'archiviazione persistente
{: #kube-storage-mendix}

Attieniti quindi alla documentazione per [Archiviazione dei dati su {{site.data.keyword.cos_full_notm}}](/docs/containers/cs_storage_cos.html#object_storage). `PersistentVolumeClaim` e `PersistentVolume` vengono creati all'interno del tuo cluster Kubernetes e possono essere utilizzati dall'istanza del database PostGres che è in esecuzione all'interno del tuo cluster come parte dell'applicazione Mendix. Assicurati di creare il `PersistentVolumeClaim` utilizzando il bucket `my-mendix-bucket` come descritto nel passo precedente e riesamina il nome del `PersistentVolumeClaim` per l'utilizzo nel passo successivo.

## Modifica del file `postgres-deployment.yaml`
{: #postgres-deploy-mendix}

Una volta configurato un volume persistente per il tuo cluster Kubernetes, il passo successivo consiste nel modificare la distribuzione del database PostGres che è in esecuzione all'interno del tuo cluster. Prima di tutto, devi modificare i file nel repository Git che erano stati creati come parte del passo di integrazione della toolchain IBM DevOps. Per trovare il repository Git, torna alla pagina dei dettagli dell'applicazione e fai clic sul link dell'URL Git dal tile **Deployment details**.  

Puoi clonare il repository Git sulla tua macchina locale oppure apportare le seguenti modifiche nell'editor online. Apri il file `chart/{app name}/templates/postgres-deployment.yaml` (sostituisci `{app name}` con il nome della tua applicazione Mendix). Il file non ha alcuna voce `volumeMount` o `volumes` esistente per impostazione predefinita e, pertanto, tutti i dati vengono archiviati in memoria all'interno del pod di distribuzione in esecuzione. Devi aggiungere entrambe le voci `volumeMount` e `volumes` al file `deployment.yaml` di Kubernetes in modo che i dati vengano salvati nel bucket {{site.data.keyword.cos_full_notm}} e non vadano perduti in caso di riavvio del pod. 

Vedi il seguente `postgres-deployment.yaml` di esempio che include le voci `volumeMount` e `volumes`.  
```yaml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: "{appname}-postgres"
spec:
  replicas: 1
  template:
    metadata:
      labels:
        service: "{appname}-postgres"
    spec:
      containers:
        - name: "{appname}-postgres"
          image: postgres:10.1
          ports:
            - containerPort: 5432
          env:
            - name: POSTGRES_DB
              value: db0
            - name: POSTGRES_USER
              value: mendix
            - name: POSTGRES_PASSWORD
              value: mendix
          volumeMounts:
            - mountPath: "/var/lib/postgresql/data"
              name: "mendix-data"
      volumes:
        - name: mendix-data
          persistentVolumeClaim:
            claimName: {pvc-name}
```

Assicurati di sostituire `{pvc-name}` con il nome del tuo `PersistentVolumeClaim` dal passo precedenze e fai attenzione a non sovrascrivere il nome della tua applicazione, che è già impostato nel file all'interno del tuo repository Git. Esegui quindi il commit delle tue modifiche nuovamente con il repository Git.

## Ridistribuzione
{: #redeploy-mendix-kube}

Dopo l'esecuzione del commit delle modifiche al tuo file `postgres-deployment.yaml` nuovamente con il repository, viene automaticamente attivata una nuova esecuzione della pipeline DevOps. Essa, tuttavia, distribuisce di nuovo l'applicazione predefinita. Devi ridistribuire la versione più recente dell'applicazione Mendix in modo che la versione più recente della tua applicazione venga distribuita con le modifiche più recenti ai volumi persistenti.

Per rieseguire la distribuzione, vai alla pagina dei dettagli della tua applicazione e fai clic su **Deploy Application** all'interno del tile **Deployment details**. Se la distribuzione non riesce all'interno della toolchain DevOps con un errore che indica che non è stato possibile trovare il file `.mda` dell'applicazione, devi eseguirne nuovamente l'esportazione da Mendix. Puoi eseguire l'esportazione procedendo in tal senso dall'applicazione desktop Mendix Modeler oppure facendo clic su **Edit on Mendix**. Quindi, all'interno dell'interfaccia web Mendix, vai alla sezione **Environments** e attieniti alla procedura dopo che hai fatto clic su **Create package from teamserver**. Dopo che la tua applicazione è stata esportata da Mendix, torna alla pagina dei dettagli dell'applicazione e fai nuovamente clic su **Deploy Application**. L'ultima applicazione esportata viene distribuita al tuo cluster Kubernetes utilizzando la toolchain DevOps {{site.data.keyword.cloud}}. Dopo che la distribuzione è stata completata correttamente, la tua applicazione è attiva e pronta per l'uso di produzione.

## Verifica che la tua applicazione sia in esecuzione
{: #verify-mendix-kube}

Dopo che hai distribuito la tua applicazione, la Delivery Pipeline o la riga di comando ti indirizzano all'URL per la tua applicazione.

1. Dalla tua toolchain DevOps, fai clic su **Delivery Pipeline** e seleziona quindi **Deploy Stage**.
2. Fai clic su **View logs and history**.
3. Nel file di log, trova l'URL dell'applicazione:

    Alla fine del file di log, cerca la parola `urls` o `view`. Ad esempio, potresti vedere una riga nel file di log simile a `urls: my-app-devhost.cloud.ibm.com` o `View the application health at: http://<ipaddress>:<port>/health`.

4. Vai all'URL nel tuo browser. Se l'applicazione è in esecuzione, viene visualizzato un messaggio che include `Congratulations` o `{"status":"UP"}`.

Se stai utilizzando la riga di comando, esegui il comando [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) per visualizzare l'URL della tua applicazione. Vai quindi all'URL nel tuo browser.

## Informazioni aggiuntive
{: #more-info-mendix-kube}

Per ulteriori dettagli relativi all'architettura per quanto riguarda l'esecuzione di applicazioni Mendix in ambienti Kubernetes, riesamina la sezione [Run Mendix on Kubernetes](https://docs.mendix.com/developerportal/deploy/run-mendix-on-kubernetes) della documentazione utente di Mendix.
