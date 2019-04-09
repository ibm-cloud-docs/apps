---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creazione di un'applicazione con un modello di codice
{: #tutorial-codepattern}

Puoi utilizzare un modello di codice per creare rapidamente la tua applicazione e distribuirla a {{site.data.keyword.cloud}}. Puoi visualizzare il codice in GitHub o creare e compilare un'applicazione su {{site.data.keyword.cloud_notm}}, dove puoi utilizzare una toolchain DevOps per distribuire automaticamente la tua applicazione.
{: shortdesc}

## Passo 1. Crea un'applicazione
{: #create-codepattern}

1. Vai a [IBM Developer ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/patterns/){:new_window} e seleziona il modello di codice che desideri. Ad esempio, puoi selezionare il modello di codice [Build a MEAN Web App ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/patterns/build-a-mean-web-app/){:new_window}.

2. Leggi la descrizione del modello di codice e visualizza il repository GitHub e il file `README.md`. Per visualizzare il repository, fai clic su **Get the code**, che apre il repository GitHub per il modello di codice.

3. Avvia la creazione di un'applicazione utilizzando l'una o l'altra delle seguenti opzioni. Entrambe le opzioni aprono la pagina **Create app** per il modello di codice.
    * Nella pagina del modello di codice, fai clic sul link per creare un'applicazione su {{site.data.keyword.cloud_notm}}. 
    * Nel file `README.md` nel repository GitHub, fai clic sul link per utilizzare un kit starter per creare l'applicazione. 

4. Nella pagina **Create app**, denomina la tua applicazione, seleziona un gruppo di risorse, fornisci (facoltativamente) delle tag e fai clic su **Create**. Per ulteriori informazioni sulle tag, vedi [Gestione delle tag](/docs/resources/tagging_resources.html#tag).

  Per tornare al modello di codice, fai clic su **View code pattern**. Controlla il file `README.md` nel repository per appurare se devi eseguire altre azioni per rendere operativa la tua applicazione.
  {: tip}

## Passo 2. Aggiunta di risorse
{: #resources-codepattern}

Puoi aggiungere risorse che migliorano la tua applicazione con la potenza cognitiva di Watson, aggiungere servizi mobili o servizi per la sicurezza. Questo processo crea un'istanza della risorsa, crea una chiave di risorsa (credenziali) e ne esegue l'associazione mediante bind alla tua applicazione. Per questa esercitazione, aggiungi una posizione per gestire i tuoi dati.

1. Dalla pagina **App details**, fai clic su **Add resource**.
2. Seleziona il tipo di risorsa che desideri. 
3. Seleziona il tuo piano prezzi. È disponibile un'opzione lite.
4. Fai clic su **Create**.

## Passo 3. Copia delle credenziali del servizio nel tuo ambiente

Dopo che hai aggiunto una risorsa alla tua applicazione, o se è richiesto qualsiasi altro servizio per la tua applicazione, nota che le credenziali per tale servizio sono visualizzate nella casella **Credentials**. Devi copiare manualmente le credenziali nel tuo ambiente di sviluppo.

Per ulteriori informazioni sulla copia delle credenziali nel tuo ambiente, vedi [Panoramica delle credenziali](/docs/apps/creds_overview.html#credentials_overview).

## Passo 4. Distribuzione a {{site.data.keyword.cloud_notm}}
{: #deploy-codepattern}

Puoi distribuire la tua applicazione a {{site.data.keyword.cloud_notm}} in diversi modi, ma una toolchain DevOps è il modo migliore per distribuire le applicazioni di produzione. Con una toolchain DevOps, puoi facilmente automatizzare le distribuzioni in molti ambienti e aggiungere rapidamente servizi di monitoraggio, registrazione e avvisi per aiutare a gestire la tua applicazione man mano che cresce.

L'abilitazione di una toolchain crea un ambiente di sviluppo basato sul team per la tua applicazione. Quando crei una toolchain, il servizio dell'applicazione crea un repository Git, in cui puoi visualizzare il codice sorgente, clonare la tua applicazione e creare e gestire i problemi. Hai anche accesso a un ambiente di laboratorio Git dedicato e a una pipeline di fornitura continua. Sono personalizzati per l'ambiente di distribuzione che scegli, sia che si tratti di [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) o [Virtual Server (VSI)](/docs/vsi/vsi_index.html).

1. Nella pagina **App details**, fai clic su **Deploy to cloud**.
2. Seleziona un metodo di distribuzione e fai clic su **Create**. {{site.data.keyword.cloud_notm}} crea automaticamente una toolchain aperta completa di un repository Git e della pipeline di fornitura continua.
3. Apri la fase pipeline della tua nuova toolchain per visualizzare il processo di creazione e sviluppo in modo da poter vedere la tua nuova applicazione nel giro di qualche minuto.

Per ulteriori informazioni sui metodi di distribuzione, sulle creazioni e sulle pipeline, vedi [Creazione e distribuzione](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy).
