---

copyright:
  years: 2018
lastupdated: "2018-11-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Creazione di applicazioni dal tuo repository di codice
{: #code-repo}

Puoi creare un'applicazione in {{site.data.keyword.cloud}} utilizzando il tuo repository dell'applicazione esistente. Fornisci semplicemente il collegamento web al tuo repository durante la creazione dell'applicazione, continua aggiungendo risorse e connetti quindi una toolchain DevOps alla tua applicazione per la distribuzione.
{: shortdesc}

## Prima di iniziare
{: #prereqs}

Assicurati di avere i seguenti prerequisiti pronti per essere utilizzati:

 * Installa la [CLI (command-line interface) {{site.data.keyword.dev_cli_long}}](/docs/cli/index.html).
 * Vedi [Cosa rende buona un'applicazione?](/docs/apps/best-practice.html) per le prassi ottimali per la creazione di applicazioni.
 * Devi disporre di un repository di codice sorgente Git da uno qualsiasi dei seguenti provider: GitHub, GitHub Enterprise, GitLab, BitBucket o Rational.

## Passo 1: Crea un'applicazione con un repository esistente
{: #create}

Per creare un'applicazione e connetterla al tuo repository di origine, completa questa procedura:

1. Dal tuo dashboard [ ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}){: new_window}, fai clic su **Crea un'applicazione** nel tile **Applicazioni**.
2. Denomina la tua applicazione e seleziona un gruppo di risorse.
3. Seleziona **Porta il tuo codice** e fornisci l'URL al tuo repository Git. La tua applicazione e l'immagine Docker si devono trovare nello stesso repository.
4. Fai clic su **Create**.

Viene visualizzata la pagina **App Details**. Da qui puoi:
* [Aggiungere risorse](/docs/apps/reqnsi.html) (facoltativo).
* Connettere la tua applicazione a una toolchain DevOps facendo clic su **Connect to DevOps toolchain**. Se non hai già una toolchain, viene aperta la pagina **Connect DevOps Toolchain**. Fai clic su **Create DevOps toolchain**. A questo punto, viene aperta la pagina [Create a Toolchain](https://{DomainName}/devops/create) nel dashboard [DevOps](https://{DomainName}/devops/) in una nuova scheda nel tuo browser. Dopo che hai creato e configurato la tua toolchain in tale scheda, devi tornare alla pagina **Connect a toolchain** nella tua applicazione e aggiornare la pagina. Per ulteriori informazioni, vedi [Connetti la tua applicazione a una nuova toolchain](#create_toolchain).
* Visualizza il tuo repository facendo clic su **View repo**.
* Acquisisci ulteriori informazioni sulle toolchain o sull'esperienza di creazione di applicazioni facendo clic su uno qualsiasi dei link correlati nella pagina **App Details**.

## Passo 2: Connetti la tua applicazione a una toolchain DevOps
{: #connect_toolchain}

Stabilire una connessione tra la tua applicazione, la toolchain e il repository è un passo in avanti nell'organizzazione dei tuoi asset del prodotto. Aiuta anche ad aggregare una vista del tuo repository di origine con il tuo flusso di lavoro DevOps, le tue istanze dell'applicazione in esecuzione e i servizi dipendenti in tutte le tue destinazioni di distribuzione. Per ulteriori informazioni, vedi [Connetti la tua applicazione a una nuova toolchain](/docs/services/ContinuousDelivery/toolchains_working.html).

Puoi connettere la tua applicazione a una toolchain DevOps utilizzando la CLI oppure la console {{site.data.keyword.cloud_notm}}. 

### Utilizzo della console

  1. Connettere la tua applicazione a una toolchain DevOps facendo clic su **Connect to DevOps toolchain**.  
  
    Se non hai una toolchain esistente, fai clic su **Create DevOps toolchain**. 
    
  2. Dopo che hai creato e configurato la tua toolchain, torna alla pagina Connect a toolchain nella tua applicazione e aggiorna la pagina. 

### Utilizzo della CLI

Puoi utilizzare il comando `ibmcloud dev enable` per generare un modello di toolchain DevOps che inserisci nel tuo repository come un insieme di istruzioni che indica quello che la toolchain DevOps deve creare. 

  1. Dalla finestra App Service, fai clic su **Download Code** o **Clone your repo** per lavorare con il tuo codice in locale.
  2. Immetti il seguente comando:
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

Per ulteriori informazioni, vedi [Creazione e distribuzione delle applicazioni utilizzando la CLI](/docs/apps/create-deploy-cli.html#developing).

## Passo 3. Distribuisci la tua applicazione
{: #deploy_app}

Dopo che hai collegato una toolchain DevOps alla tua applicazione, completa la seguente procedura per distribuirla a {{site.data.keyword.cloud_notm}}: 

1. Dalla pagina App Details, fai clic su **Deploy to Cloud**.
2. Seleziona un metodo di distribuzione. 

    * [Distribuisci ad un cluster Kubernetes](/docs/apps/tutorials/tutorial_byoc_kube.html). Crea un cluster di host, chiamati nodi di lavoro, per distribuire e gestire contenitori dell'applicazione a elevata disponibilità. Puoi creare un cluster o distribuire un cluster esistente.
    * Distribuisci con Cloud Foundry, dove non è necessario gestire l'infrastruttura sottostante.
    * Distribuisci a una [VSI (virtual server instance)](/docs/apps/vsi-deploy.html).


