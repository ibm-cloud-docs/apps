---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, byoc, code repository, continuous delivery, cli, deploy

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Creazione di applicazioni dal tuo repository di codice
{: #tutorial-byoc}

Puoi creare un'applicazione in {{site.data.keyword.cloud}} utilizzando il tuo repository dell'applicazione esistente. Fornisci semplicemente il collegamento web al tuo repository durante la creazione dell'applicazione, continua aggiungendo risorse e connetti quindi una toolchain DevOps alla tua applicazione per la distribuzione.
{: shortdesc}

## Prima di iniziare
{: #prereqs-byoc}

Assicurati di avere i seguenti prerequisiti pronti per essere utilizzati:

 * Installa la [CLI (command-line interface) {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).
 * Vedi [Cosa rende buona un'applicazione?](/docs/apps?topic=creating-apps-best-practice) per le prassi ottimali per la creazione di applicazioni.
 * Devi disporre di un repository di codice sorgente Git da uno qualsiasi dei seguenti provider: GitHub, GitHub Enterprise, GitLab, BitBucket o Rational.
 * Se intendi distribuire la tua applicazione a [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), devi [preparare il tuo account {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Passo 1: Crea un'applicazione con un repository esistente
{: #create-byoc}

Per creare un'applicazione e connetterla al tuo repository di origine, completa questa procedura:

1. Dal tuo [dashboard](https://{DomainName}){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno"), fai clic su **Create an app** nel tile **Apps**.
2. Denomina la tua applicazione, seleziona un gruppo di risorse e, facoltativamente, fornisci delle tag per classificare la tua applicazione. Per ulteriori informazioni, consulta [Gestione delle tag](/docs/resources?topic=resources-tag).
3. Seleziona **Bring your own code** e fornisci l'URL al tuo repository Git. La tua applicazione e l'immagine Docker si devono trovare nello stesso repository.
4. Fai clic su **Create**. Viene visualizzata la pagina **App details**. 
5. Facoltativo. [Aggiungi servizi](/docs/apps?topic=creating-apps-add-resource) alla tua applicazione.
6. Facoltativo. Se hai fornito delle tag quando hai creato l'applicazione, puoi modificarle facendo clic sull'icona **Edit** ![Icona Modifica](../../icons/edit-tagging.svg) che si trova accanto alle tag visualizzate.
7. Facoltativo. Visualizza il tuo repository facendo clic su **View repo**.

## Passo 2. Distribuisci la tua applicazione
{: #toolchain-byoc}

Stabilire una connessione tra la tua applicazione, la toolchain e il repository è un passo in avanti nell'organizzazione dei tuoi asset del prodotto. Aiuta anche ad aggregare una vista del tuo repository di origine con il tuo flusso di lavoro DevOps, le tue istanze dell'applicazione in esecuzione e i servizi dipendenti in tutte le tue destinazioni di distribuzione. Per ulteriori informazioni, vedi [Creazione delle toolchain](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

Puoi configurare la fornitura continua per la tua applicazione utilizzando la CLI oppure la console {{site.data.keyword.cloud_notm}}.

### Utilizzo della console
{: #console-byoc-toolchain}

  1. Sulla pagina **App details**, connetti la tua applicazione a una toolchain DevOps facendo clic su **Configure continuous delivery**. Viene visualizzata la pagina **Deploy my app**. 
  2. Se non hai una toolchain esistente, fai clic su **Create a toolchain**. Dopo aver creato la toolchain, utilizza i breadcrumb per tornare alla pagina **App details**, che indica che la fornitura continua è configurata.
  3. Se hai una toolchain esistente, selezionala e poi fai clic su **Enable deployment**. Viene visualizzata la pagina **App details**, che indica che la fornitura continua è configurata. 

### Utilizzo della CLI

Puoi utilizzare il comando `ibmcloud dev enable` per generare un template della toolchain DevOps che inserisci nel tuo repository come insieme di istruzioni che indica quello che la toolchain DevOps deve creare. 

  1. Nella pagina **App details**, fai clic su **View repo** per utilizzare il tuo codice localmente. 
  2. Immetti il seguente comando:
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

Per ulteriori informazioni, vedi [Creazione e distribuzione delle applicazioni utilizzando la CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli).

