---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-06"

keywords: apps, deploy, deploying apps, toolchain, cli, cloud, devops, deployment, git, push

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Distribuzione delle applicazioni
{: #deploying-apps}

Puoi distribuire la tua applicazione a {{site.data.keyword.cloud}} utilizzando una toolchain DevOps. Con una toolchain DevOps, puoi automatizzare le distribuzioni in molti ambienti e aggiungere rapidamente servizi di monitoraggio, registrazione, informazioni approfondite e avvisi per aiutare a gestire la tua applicazione man mano che cresce. Puoi configurare la fornitura continua e la distribuzione della tua applicazione utilizzando l'interfaccia di riga di comando (o CLI, command-line interface) o la console web {{site.data.keyword.cloud_notm}}.
{: shortdesc}

Una toolchain DevOps fornisce un ambiente di sviluppo basato sul team per la tua applicazione. Quando crei una toolchain, il servizio dell'applicazione crea un repository Git, in cui puoi visualizzare il codice sorgente, clonare la tua applicazione e creare e gestire i problemi. Hai anche accesso a un ambiente di GitLab dedicato e a una pipeline di fornitura continua. Sono personalizzati per la destinazione di distribuzione che selezioni, sia che si tratti di [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) o [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Tutte le toolchain che vengono create dal dashboard dello sviluppatore {{site.data.keyword.cloud_notm}} sono configurate per la distribuzione automatica.
{: note}

## Utilizzo della console {{site.data.keyword.cloud_notm}}
{: deploy-console}

{{site.data.keyword.cloud_notm}} fornisce una console web in cui puoi configurare la fornitura continua e distribuire la tua applicazione utilizzando una toolchain DevOps.

### Prima di iniziare
{: deploy-console-before}

Prima di cominciare, utilizza il [Dashboard {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") per [creare la tua applicazione](/docs/apps?topic=creating-apps-tutorial-getting-started#create-getting-started) e [aggiungere i servizi](/docs/apps?topic=creating-apps-tutorial-getting-started#resources-getting-started).

### Distribuzione automatica della tua applicazione
{: deploy-console-auto}

1. Nella pagina **App details**, fai clic su **Configure continuous delivery**.
2. Seleziona un destinazione per la distribuzione. Configura la tua destinazione di distribuzione in base alle istruzioni per la destinazione che selezioni:
  * **Deploy to IBM Kubernetes Service**. Questa opzione crea un cluster di host, denominati nodi di lavoro, per distribuire e gestire contenitori delle applicazioni ad elevata disponibilità. Puoi creare un cluster o distribuire un cluster esistente. Per ulteriori informazioni, vedi [Distribuzione delle applicazioni ai cluster Kubernetes](/docs/containers?topic=containers-app).
  * **Deploy to Cloud Foundry**. Questa opzione distribuisce la tua applicazione nativa del cloud senza che tu debba gestire l'infrastruttura sottostante. Se il tuo account ha accesso a {{site.data.keyword.cfee_full_notm}}, puoi selezionare un tipo di deployer **Public Cloud** o **Enterprise Environment**, che puoi utilizzare per creare e gestire ambienti isolati per ospitare applicazioni Cloud Foundry esclusivamente per la tua azienda. Per ulteriori informazioni, vedi [Distribuzione delle applicazioni a Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps) e [Distribuzione delle applicazioni a {{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps).
  * **Deploy to a Virtual Server**. Questa opzione esegue il provisioning di un'istanza del server virtuale, carica un'immagine che include la tua applicazione, crea una toolchain DevOps e avvia il primo ciclo di distribuzione per tuo conto. Per ulteriori informazioni, vedi [Distribuzione delle applicazioni a un server virtuale](/docs/apps?topic=creating-apps-vsi-deploy).

### Distribuzione manuale della tua applicazione
{: deploy-console-manual}

Con una toolchain correttamente configurata, un ciclo di creazione-distribuzione viene avviato automaticamente con tutte le unioni al ramo master nel tuo repository. 

Puoi anche distribuire manualmente la tua applicazione dalla tua toolchain DevOps:

1. Nella pagina **App details**, fai clic su **View toolchain**.
2. Fai clic su **Delivery Pipeline** dove puoi iniziare le creazioni, gestire la distribuzione e visualizzare i log e la cronologia.

La fornitura continua è abilitata automaticamente per alcune applicazioni. Puoi abilitare la fornitura continua per automatizzare le creazioni, i test e le distribuzioni tramite Delivery Pipeline e GitHub.

Per ulteriori informazioni, vedi:
* [Creazione e distribuzione](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).
* [Creazione delle toolchain](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)

## Utilizzo della CLI {{site.data.keyword.dev_cli_short}}
{: #deploy-cli}

{{site.data.keyword.cloud_notm}} fornisce una CLI e dei plugin solidi per semplificare il flusso di lavoro dello sviluppatore. Puoi distribuire la tua applicazione {{site.data.keyword.cloud_notm}} in uno di questi due modi, a seconda di come è configurata.

### Prima di iniziare
{: #deploy-cli-before}

Prima di iniziare, [scarica e installa la CLI {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).

La CLI non è supportata da Cygwin. Utilizza lo strumento in una finestra diversa da quella della riga di comando Cygwin.
{: important}

  1. Scarica il codice per la tua applicazione in una nuova directory per configurare il tuo ambiente di sviluppo.

  2. Passa alla directory in cui si trova il codice.

  3.  Aggiorna il tuo codice applicazione. Ad esempio, se stai utilizzando un'applicazione di esempio {{site.data.keyword.cloud_notm}} che contiene il file `src/main/webapp/index.html`, puoi modificarlo con la riga `Thanks for creating ...`. Assicurati che l'applicazione venga eseguita localmente prima di distribuirla a {{site.data.keyword.cloud_notm}}.

    Prendi nota del file `manifest.yml`. Quando distribuisci la tua applicazione a {{site.data.keyword.cloud_notm}}, questo file viene utilizzato per determinare l'URL, l'allocazione di memoria, il numero di istanze e altri parametri fondamentali della tua applicazione.

    Controlla inoltre il file `README.md`, che contiene dettagli come le istruzioni di creazione.

    Se la tua applicazione è un'applicazione Liberty, devi crearla prima di ridistribuirla.
    {: note}

  4. Accedi alla CLI {{site.data.keyword.cloud_notm}} con il tuo ID IBM. Se hai più account, ti viene richiesto di selezionare quale account utilizzare. Se non specifichi una regione con l'indicatore `-r`, devi selezionare anche una regione.
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    Se le tue credenziali vengono rifiutate, è possibile che tu stia utilizzando un ID federato. Per eseguire l'accesso con un ID federato, utilizza l'indicatore `--sso`. Per ulteriori informazioni, vedi [Accesso con un ID federato](/docs/iam/federated_id?topic=iam-federated_id#federated_id).
    {: tip}

### Distribuzione automatica della tua applicazione
{: #deploy-cli-auto}

Se non hai ancora creato un toolchain DevOps per la tua applicazione e la tua applicazione non si trova ancora in un repository Git, puoi eseguire il comando [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit). Segui i prompt per "Configure DevOps" ed esegui la distribuzione a una nuova toolchain (e crea un nuovo repository GitLab).

Dopo che hai creato una toolchain DevOps per la tua applicazione, distribuire una nuova build è semplice come eseguire il commit e il push del tuo codice al repository nella tua toolchain. 

1. Prepara le modifiche di cui eseguire il commit.
    ```
    git add .
    ```
2. Esegui il commit delle modifiche con un breve messaggio.
    ```
    git commit -m "made changes"
    ```
3. Esegui il push dei commit sul ramo master al repository remoto.
    ```
    git push origin master
    ```
4. Visualizza la toolchain DevOps per la tua applicazione dalla console {{site.data.keyword.cloud_notm}}. Puoi visualizzare i dettagli della toolchain dalla pagina **App details** nella console {{site.data.keyword.cloud_notm}} eseguendo il comando [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) dalla directory dell'applicazione.
5. Visualizza la pipeline nella toolchain per verificare che sia stata avviata una nuova build.

### Distribuzione manuale della tua applicazione
{: #deploy-cli-manual}

Puoi distribuire manualmente la tua applicazione a {{site.data.keyword.cloud_notm}} utilizzando il comando [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).

  ```
  ibmcloud dev deploy <APP_NAME>
  ```
  {: codeblock}

### Informazioni correlate
{: #deploy-cli-related}

Per ulteriori informazioni sulla distribuzione della tua applicazione a {{site.data.keyword.cloud_notm}} utilizzando la CLI, vedi:

* [Deploying to IBM Cloud Environments with {{site.data.keyword.dev_cli_short}} CLI](https://www.ibm.com/blogs/bluemix/2019/01/deploying-to-ibm-cloud-environments-with-ibm-cloud-developer-tools-cli/){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")
