---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-20"

keywords: byoc, code repository, continuous delivery, cli, deploy, create app custom repo, custom repo, existing repo, custom code

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

Se disponi di un'applicazione in un repository esistente, puoi utilizzare un kit starter di base per creare un record dell'applicazione in {{site.data.keyword.cloud_notm}} e collegare l'applicazione al tuo repository di origine e alla tua toolchain DevOps.
{: shortdesc}

Puoi iniziare dal dashboard {{site.data.keyword.cloud_notm}} o da qualsiasi kit starter di base. Dopo aver fornito un nome alla tua applicazione e selezionato un gruppo di risorse, seleziona il punto di partenza **Porta il tuo codice**, fornisci l'URL del repository Git che contiene il tuo codice e fai clic su **Create**.

Puoi connettere la tua toolchain DevOps esistente oppure crearne una e fornire in modo continuo la tua applicazione alla destinazione di distribuzione di tua scelta, come ad esempio Kubernetes o Cloud Foundry.

## Prima di iniziare
{: #prereqs-byoc}

Assicurati di avere i seguenti prerequisiti pronti per essere utilizzati:

 * Installa la [CLI (command-line interface) {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-getting-started).
 * Vedi [Cosa rende buona un'applicazione?](/docs/apps?topic=creating-apps-best-practice) per le prassi ottimali per la creazione di applicazioni.
 * Devi disporre di un repository di codice sorgente Git da uno qualsiasi dei seguenti provider: GitHub, GitHub Enterprise, GitLab, BitBucket o Rational.
 * Se intendi distribuire la tua applicazione a [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), devi [preparare il tuo account {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Creazione di un'applicazione con un repository esistente
{: #create-byoc}

Per creare un'applicazione e connetterla al tuo repository di origine, completa questa procedura:

1. Dalla [Console {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno"), fai clic su **Create an app** nel tile **Apps**.
2. Denomina la tua applicazione, seleziona un gruppo di risorse e facoltativamente fornisci delle tag per classificare la tua applicazione. Per ulteriori informazioni, consulta [Gestione delle tag](/docs/resources?topic=resources-tag).
3. Seleziona **Bring your own code** e fornisci l'URL al tuo repository Git. La tua applicazione e l'immagine Docker si devono trovare nello stesso repository.
4. Fai clic su **Create**. Viene visualizzata la pagina **App details**.
5. Facoltativo. [Aggiungi dei servizi](/docs/apps?topic=creating-apps-add-resource) alla tua applicazione.
6. Facoltativo. Puoi aggiungere tag a questa applicazione facendo clic su **Add tags** o puoi modificare le tag facendo clic sull'icona **Edit** ![Icona Edit](../../icons/edit-tagging.svg) che si trova accanto alle tag visualizzate.
7. Facoltativo. Visualizza il tuo repository facendo clic su **View repo**.

## Distribuzione della tua applicazione
{: #toolchain-byoc}

Stabilire una connessione tra la tua applicazione, la toolchain e il repository è un passo in avanti nell'organizzazione dei tuoi asset del prodotto. Aiuta anche ad aggregare una vista del tuo repository di origine con il tuo flusso di lavoro DevOps, le tue istanze dell'applicazione in esecuzione e i servizi dipendenti in tutte le tue destinazioni di distribuzione. Per ulteriori informazioni, vedi [Creazione delle toolchain](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

Puoi configurare la fornitura continua per la tua applicazione utilizzando la CLI oppure la console {{site.data.keyword.cloud_notm}}.

### Utilizzo della console
{: #console-byoc-toolchain}

#### Se hai già una toolchain DevOps che vuoi connettere alla tua applicazione, completa questa procedura:

1. Nella pagina **App details**, fai clic su **Configure continuous delivery**. Viene visualizzata la pagina **Deploy my app**.
2. Seleziona la toolchain che vuoi connettere alla tua applicazione e fai clic su **Enable deployment**. Viene visualizzata la pagina **App details**, che indica che la fornitura continua è configurata.

#### Se non hai una toolchain DevOps per questa applicazione, completa la seguente procedura:

1. Nella pagina **App details**, fai clic su **Create DevOps toolchain.** Viene visualizzata la pagina **Create a toolchain**.
2. [Crea la toolchain](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).
3. Utilizza i breadcrumb nella finestra del browser per tornare alla pagina **App details**, che indica che la fornitura continua è configurata.

### Utilizzo della CLI
{: #cli-byoc-toolchain}

Puoi utilizzare il comando `ibmcloud dev enable` per generare un template della toolchain DevOps che inserisci nel tuo repository come insieme di istruzioni che indica quello che la toolchain DevOps deve creare. 

  1. Nella pagina **App details**, fai clic su **View repo** per utilizzare il tuo codice localmente.
  2. Immetti il seguente comando:
    
    ```
    ibmcloud dev enable
    ```
   {: codeblock}

Per ulteriori informazioni sulla distribuzione della tua applicazione, vedi [Distribuzione delle applicazioni](/docs/apps?topic=creating-apps-deploying-apps).

## Verifica che la tua applicazione sia in esecuzione
{: #verify-byoc-app}

La Delivery Pipeline o la riga di comando ti indirizzano all'URL della tua applicazione.

1. Dalla tua toolchain DevOps, fai clic su **Delivery Pipeline** e seleziona quindi **Deploy Stage**.
2. Fai clic su **View logs and history**.
3. Nel file di log, trova l'URL dell'applicazione. Alla fine del file di log, cerca la parola `urls` o `view`. Ad esempio, nel file di log potresti vedere una riga simile a `urls: my-app-devhost.mybluemix.net` o `View the application health at: http://<ipaddress>:<port>/health`.
4. Vai all'URL nel tuo browser. Se l'applicazione è in esecuzione, viene visualizzato un messaggio che include `Congratulations` o `{"status":"UP"}`.

Se stai utilizzando la riga di comando, esegui il comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) per aprire la pagina di un'applicazione distribuita manualmente nel tuo browser predefinito.
