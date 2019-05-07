---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-25"

keywords: apps, create, build, deploy, cli, web app, microservice, deploy cli, deploy command line, build app local, developer tools, ibmcloud dev create

subcollection: creating-apps

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Creazione e distribuzione delle applicazioni utilizzando la CLI
{: #create-deploy-app-cli}

Puoi utilizzare la CLI (command-line interface) {{site.data.keyword.cloud}} per creare e distribuire la tua applicazione. 

Puoi creare un'applicazione starter da zero oppure abilitare al cloud il tuo codice dell'applicazione esistente. 
{: note}

## Prima di iniziare
{: #prereqs-app-cli}

Devi installare la CLI {{site.data.keyword.cloud_notm}}, il plug-in CLI {{site.data.keyword.dev_cli_notm}} e gli altri plug-in e strumenti consigliati. Per ulteriori informazioni, vedi [Introduzione alla CLI IBM Cloud](/docs/cli?topic=cloud-cli-ibmcloud-cli). 

## Creazione di un'applicazione starter da zero
{: #create-app-cli}

La creazione di un'applicazione da zero è utile se, per iniziare, non hai già del codice esistente e vuoi piuttosto iniziare da un template starter di framework o linguaggio.

1. Esegui il comando [`ibmcloud dev create`](/docs/cli/idt?topic=cloud-cli-idt-cli#create) nella directory di tua scelta.
2. Seleziona **Backend Service / Web App** come tipo di applicazione.
3. Seleziona **Node** come tipo di linguaggio.
4. Seleziona **Node.js Web App with Express.js (Web App)** come kit starter da utilizzare.
5. Immetti un nome per la tua applicazione e seleziona il gruppo di risorse che vuoi utilizzare (se necessario). Non aggiungere servizi, per ora.
6. Seleziona l'opzione **IBM DevOps, deploy to Cloud Foundry buildpacks** per creare una toolchain DevOps. Potrebbe essere necessario impostare le chiavi SSH per completare questo passo.
  Se imposti una passphrase per la tua chiave SSH, ti viene richiesto di immettere questo codice.
  {: note}
7. Attieniti alle istruzioni rimanenti per:
  * Selezionare una regione per la tua toolchain.
  * Immettere un nome per il nome toolchain DevOps.
  * Immettere un nome per il nome host.

La creazione dell'applicazione e della toolchain richiede alcuni secondi.

## Generazione di asset di abilitazione di distribuzione e cloud
{: #byoc-cli}

Questa opzione può essere utilizzata se già hai una base di codice esistente e vuoi generare degli asset di abilitazione del cloud e di distribuzione per un singolo microservizio o una singola applicazione web utilizzando [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable). Nota che questo comando è in fase Beta e non tutte le lingue e/o strutture dell'applicazione sono supportate. Le seguenti istruzioni illustrano come utilizzare questa funzionalità con un repository di esempio, ma la procedura è più o meno la stessa per la tua base di codice.

1. Accedi a {{site.data.keyword.cloud_notm}} eseguendo `ibmcloud login` e seleziona quindi un'organizzazione e uno spazio di destinazione.
2. Clona l'[applicazione di esempio Hello World](https://github.com/IBM-Cloud/node-helloworld){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") immettendo il seguente comando nella directory di tua scelta.

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

3. Passa alla directory in cui hai clonato l'applicazione di esempio ed esegui il comando [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable).
4. Seleziona di continuare senza eseguire il commit delle modifiche per ora (se necessario).
5. Seleziona di continuare quando ti viene richiesto di procedere con il linguaggio Node che viene rilevato.
6. Seleziona il gruppo di risorse che vuoi utilizzare (se necessario). 
7. Seleziona l'opzione per creare una nuova applicazione {{site.data.keyword.cloud_notm}} collegata a questo repository Git. Per i dettagli, vedi **Note importanti**.
8. Non aggiungere servizi, per ora.
9. Attendi alcuni secondi per il completamento delle operazioni. 
10. Una volta che le operazioni sono state completate, unisci manualmente i file di abilitazione del cloud e di distribuzione che vengono salvati nella directory dell'applicazione. Unisci i nuovi file contrassegnati con `.merge` utilizzando `git diff` o uno strumento simile.

### Note importanti
 - Se già hai creato un'applicazione {{site.data.keyword.cloud_notm}} utilizzando la console {{site.data.keyword.cloud_notm}}, attieniti ai passi da 2 a 5 nella sezione precedente nella directory della tua applicazione. Per il passo 6, puoi selezionare l'opzione di connettere il tuo codice locale a un'applicazione esistente.
 - Puoi anche scegliere di generare i file di distribuzione e di abilitazione cloud senza stabilire una connessione a un'applicazione {{site.data.keyword.cloud_notm}} eseguendo [`ibmcloud dev enable --no-create`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable).
 - Per configurare manualmente una toolchain e i file di distribuzione, attieniti all'[esercitazione](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc-kube). Può essere molto utile se stai provando a configurare una toolchain Continuous Delivery per più di un microservizio o di un'applicazione web intercorrelati.
 - Se la tua base di codice esistente non è già in un repository Git, attieniti ai passi da 2 a 5 nella sezione precedente nella tua directory dell'applicazione. Per il passo 6, puoi selezionare l'opzione di creare una nuova applicazione {{site.data.keyword.cloud_notm}} e distribuirla a una toolchain DevOps (che ha un repository GitLab appena creato).

## Creazione della tua applicazione ed esecuzione in locale
{: #build-run-app-cli}

Indipendentemente da quale opzione hai utilizzato per creare la tua applicazione, puoi ora crearla ed eseguirla localmente.

1. Passa alla directory della tua applicazione e assicurati che Docker sia in esecuzione sul tuo sistema.
2. Esegui il comando [`ibmcloud dev build`](/docs/cli/idt?topic=cloud-cli-idt-cli#build) per creare la tua applicazione.
3. Esegui il comando [`ibmcloud dev run`](/docs/cli/idt?topic=cloud-cli-idt-cli#run) per avviare l'esecuzione della tua applicazione localmente.
4. Visualizza la tua applicazione che è in esecuzione localmente su `http://localhost:3000` o un URL simile.
5. Premi i tasti **Ctrl+C** per arrestare la tua applicazione.

Puoi anche utilizzare i [comandi compound](/docs/cli/idt?topic=cloud-cli-idt-cli#compound) come `ibmcloud dev build/run` per emettere successivamente una build dopo l'esecuzione.
{: tip}

## Aggiunta di un servizio e modifica del codice
{: #resources-app-cli}

Ora che la tua applicazione viene eseguita in locale, puoi aggiungere un servizio e modificare il codice. 

1. Esegui il comando [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit).
2. Segui le istruzioni per creare e collegare un nuovo servizio correlato ai dati alla tua applicazione, come ad esempio {{site.data.keyword.cloudant_short_notm}}. Potresti dover selezionare una regione e un piano per il servizio.
3. Puoi scegliere di unire manualmente i file di configurazione che vengono salvati nella tua directory dell'applicazione quando crei il servizio. Oppure puoi saltare questo passo per ora.
4. Aggiorna il tuo codice. Ad esempio, modifica il file `/public/index.html` o un file simile. Se stai utilizzando l'applicazione `ExpressJS` di esempio, puoi modificare la stringa `Congratulations!` con qualcosa come `Hello World!`.
5. Salva tutti i file modificati.

## Distribuzione a {{site.data.keyword.cloud_notm}}
{: #deploy-app-cli}

Puoi distribuire la tua applicazione {{site.data.keyword.cloud_notm}} in uno di questi due modi, a seconda di come è configurata. 

### Distribuzione della tua applicazione utilizzando una toolchain DevOps
Se non hai ancora creato un toolchain DevOps per la tua applicazione e la tua applicazione non si trova ancora in un repository Git, puoi eseguire il comando [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit). Segui i prompt per "Configure DevOps" ed esegui la distribuzione a una nuova toolchain (e crea un nuovo repository GitLab).

Dopo che hai creato una toolchain DevOps per la tua applicazione, distribuire una nuova build è semplice come eseguire il commit e il push del tuo codice al repository nella tua toolchain. 

1. Esegui il comando `git add .`.
2. Esegui il comando `git commit -m "made changes"` per eseguire il commit delle modifiche.
3. Esegui il comando `git push origin master` per eseguire il push al ramo master.
4. Visualizza la toolchain DevOps per la tua applicazione dalla console {{site.data.keyword.cloud_notm}}. Puoi visualizzare i dettagli della toolchain dalla pagina **App details** nella console {{site.data.keyword.cloud_notm}} eseguendo il comando [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) dalla directory dell'applicazione.
5. Visualizza la pipeline nella toolchain per verificare che sia stata avviata una nuova build.

### Distribuzione manuale della tua applicazione

Puoi distribuire manualmente la tua applicazione utilizzando il comando [`deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy). Ad esempio, utilizza la seguente procedura per distribuire manualmente la tua applicazione a Kubernetes.

1. Assicurati di aver [creato un cluster Kubernetes](https://{DomainName}/kubernetes/overview){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno").
2. Esegui il comando [`ibmcloud dev deploy -t container`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).
3. Quando richiesto, conferma il nome dell'immagine del contenitore e il cluster da utilizzare.
4. Attendi alcuni minuti per il completamento della distribuzione.

## Visualizzazione della tua applicazione
{: #view-app-cli}

1. Per visualizzare l'URL della tua applicazione in esecuzione in {{site.data.keyword.cloud_notm}}, esegui il comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view).
2. Per visualizzare i dettagli sulle credenziali della tua applicazione e la toolchain dalla console {{site.data.keyword.cloud_notm}}, esegui il comando [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console). 

**Per segnalare problemi o fornire un feedback, puoi utilizzare [{{site.data.keyword.cloud_notm}} Tech's Slack - #developer-tools channel](https://ibm-cloud-tech.slack.com/){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno"). Richiedi l'accesso al team [qui](https://slack-invite-ibm-cloud-tech.mybluemix.net/){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno").**
