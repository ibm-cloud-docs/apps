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

# Creazione e distribuzione delle applicazioni utilizzando la CLI 
{: #developing}

Puoi utilizzare la CLI (command-line interface) {{site.data.keyword.Bluemix}} per creare e distribuire la tua applicazione.
{:shortdesc}

## Prima di iniziare
{: #prereqs}

Installa la CLI {{site.data.keyword.Bluemix_notm}}, il plug-in CLI {{site.data.keyword.dev_cli_notm}} e gli altri plugin e strumenti consigliati. Per ulteriori informazioni, vedi [Introduzione alla CLI IBM Cloud](/docs/cli/index.html). 

## Creazione della tua applicazione
{: #create}

Puoi creare una nuova applicazione da zero o creare un'applicazione abilitata cloud utilizzando il tuo codice esistente. 

### Creazione di un'applicazione da zero

1. Esegui il comando [`ibmcloud dev create`](/docs/cli/idt/commands.html#create) nella directory di tua scelta.
2. Seleziona **Backend Service / Web App** come tipo di applicazione.
3. Seleziona **Node** come tipo di linguaggio.
4. Seleziona **Express.js Basic (Web App)** come kit starter da utilizzare.
5. Immetti un nome per la tua applicazione e seleziona il gruppo di risorse che vuoi utilizzare (se necessario). Non aggiungere servizi per ora.
6. Seleziona l'opzione **IBM DevOps, using Cloud Foundry** per creare una toolchain DevOps. Potrebbe essere necessario impostare le chiavi SSH per completare questo passo.
7. Immetti un nome host univoco, ad esempio `abc-devhost`. Questo nome host è la rotta della tua applicazione, `abc-devhost.mybluemix.net`.

La creazione dell'applicazione e della toolchain richiede alcuni secondi. Puoi monitorare lo stato nel prompt dei comandi.

### Creazione di un'applicazione utilizzando il codice esistente

1. Clona l'[applicazione di esempio Hello World](https://github.com/IBM-Cloud/node-helloworld) immettendo il seguente comando nella directory di tua scelta.

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

2. Passa alla directory in cui hai clonato l'applicazione di esempio ed esegui il comando [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable).
3. Seleziona di continuare senza eseguire il commit delle modifiche a GitHub per ora.
4. Seleziona di continuare quando ti viene richiesto di procedere con il linguaggio Node che viene rilevato.
5. Seleziona il gruppo di risorse che vuoi utilizzare (se necessario). Non aggiungere servizi per ora.
6. Attendere alcuni secondi per la creazione dell'applicazione. 
7. Puoi scegliere di unire manualmente i file di distribuzione e di configurazione che vengono salvati nella directory dell'applicazione quando la crei. Oppure puoi saltare questo passo per ora.

## Creazione della tua applicazione ed esecuzione in locale
{: #build-run}

Indipendentemente da quale opzione hai utilizzato per creare la tua applicazione, puoi ora crearla ed eseguirla localmente.

1. Passa alla directory della tua applicazione e assicurati che Docker sia in esecuzione sul tuo sistema.
2. Esegui il comando [`ibmcloud dev build`](/docs/cli/idt/commands.html#build) per creare la tua applicazione.
3. Esegui il comando [`ibmcloud dev run`](/docs/cli/idt/commands.html#run) per avviare l'esecuzione della tua applicazione localmente.
4. Vedi se la tua applicazione viene eseguita in locale all'indirizzo `http://localhost:3000` o in un URL simile.
5. Premi i tasti **Ctrl+C** per arrestare la tua applicazione.

Puoi anche utilizzare i [comandi compound](/docs/cli/idt/commands.html#compound) come `ibmcloud dev build/run` per emettere successivamente una build dopo l'esecuzione.
{: tip}

## Aggiunta di un servizio e modifica del codice
{: #add-service}

Ora che la tua applicazione viene eseguita in locale, puoi aggiungere un servizio e modificare il codice. 

1. Esegui il comando [`ibmcloud dev edit`](/docs/cli/idt/commands.html#edit).
2. Segui le istruzioni per creare e collegare un nuovo servizio correlato ai dati alla tua applicazione, come ad esempio {{site.data.keyword.cloudant_short_notm}}. Potresti dover selezionare una regione e un piano per il servizio.
3. Puoi scegliere di unire manualmente la distribuzione e la configurazione che vengono salvate nella tua directory dell'applicazione quando crei il servizio. Oppure puoi saltare questo passo per ora.
4. Apporta una modifica al tuo codice. Ad esempio, modifica il file `/public/index.html` o un file simile. Se stai utilizzando l'applicazione `ExpressJS` di esempio, puoi modificare la stringa `Congratulations!` con qualcosa come `Hello World!`.
5. Salva tutti i file modificati.

## Distribuzione a {{site.data.keyword.Bluemix_notm}}
{: #deploy}

Puoi distribuire la tua applicazione {{site.data.keyword.Bluemix_notm}} in uno di questi due modi, a seconda di come è configurata la tua applicazione. 

### Distribuzione della tua applicazione utilizzando una toolchain DevOps

Se hai precedentemente creato una toolchain DevOps per la tua applicazione, la distribuzione di una nuova build è semplice come il commit e il push del tuo codice al repository nella tua toolchain. 

1. Esegui il comando `git add .`.
2. Esegui il comando `git commit -m "made changes"` per eseguire il commit delle modifiche.
3. Esegui il comando `git push origin master` per eseguire il push al ramo master.
4. Visualizza la toolchain DevOps per la tua applicazione dalla console {{site.data.keyword.Bluemix_notm}}. Puoi visualizzare la toolchain in un browser web eseguendo il comando [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) dalla directory app e facendo clic su **View Toolchain**.
5. Visualizza la pipeline nella toolchain per verificare che sia stata avviata una nuova build.

### Distribuzione manuale della tua applicazione

Puoi distribuire manualmente la tua applicazione utilizzando il comando [`deploy`](/docs/cli/idt/commands.html#deploy). Ad esempio, utilizza la seguente procedura per distribuire manualmente la tua applicazione a Kubernetes.

1. Assicurati di [aver creato un cluster Kubernetes](https://console.bluemix.net/containers-kubernetes/overview).
2. Esegui il comando [`ibmcloud dev deploy -t container`](/docs/cli/idt/commands.html#deploy).
3. Quando richiesto, conferma il nome dell'immagine del contenitore e il cluster da utilizzare.
4. Attendi alcuni minuti per il completamento della distribuzione.

## Visualizzazione della tua applicazione
{: #view}

1. Per visualizzare l'URL della tua applicazione in esecuzione in {{site.data.keyword.Bluemix_notm}}, esegui il comando [`ibmcloud dev view`](/docs/cli/idt/commands.html#view).
2. Per visualizzare i dettagli sulle credenziali della tua applicazione e la toolchain dalla console {{site.data.keyword.Bluemix_notm}}, esegui il comando [`ibmcloud dev console`](/docs/cli/idt/commands.html#console). 

