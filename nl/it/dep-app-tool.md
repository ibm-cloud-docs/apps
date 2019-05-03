---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-02"

keywords: apps, deploy, deploying apps, toolchains, cli, cloud

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

Puoi distribuire le tue applicazioni con una toolchain DevOps o con la CLI (command-line interface). Una toolchain DevOps è un insieme di integrazioni degli strumenti. La CLI è un modo semplice per distribuire le tue applicazioni e istanze del servizio.
{: shortdesc}

## Distribuzione di applicazioni mediante le toolchain DevOps
{: #toolchain-deploy-apps}

Le toolchain aperte sono disponibili negli ambienti pubblico e dedicato in {{site.data.keyword.Bluemix}}. Con una toolchain correttamente configurata, distribuire la tua applicazione è semplice. Un ciclo di creazione-distribuzione viene avviato automaticamente con tutte le unioni al ramo master nel tuo repository.

Puoi creare una toolchain in questi modi:
* Crea una toolchain da un'applicazione. Per ulteriori informazioni, vedi [Distribuzione della tua applicazione](/docs/apps?topic=creating-apps-tutorial-scratch#deploy-scratch).
* Utilizza un template per creare una toolchain. Per ulteriori informazioni, vedi [Creazione delle toolchain](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## Distribuzione di applicazioni mediante la CLI
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}} fornisce una solida CLI e i plug-in e le estensioni degli strumenti per sviluppatori che si integrano con la CLI.

Prima di iniziare, [scarica e installa la CLI {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).

La CLI non è supportata da Cygwin. Utilizza lo strumento in una finestra diversa da quella della riga di comando di Cygwin.
{: important}

  1. Scarica il codice per la tua applicazione in una nuova directory per configurare il tuo ambiente di sviluppo.

  2. Passa alla directory in cui si trova il codice.

  3.  Aggiorna il codice della tua applicazione. Ad esempio, se stai utilizzando un'applicazione di esempio {{site.data.keyword.cloud_notm}} e la tua applicazione contiene il file `src/main/webapp/index.html`, puoi modificarlo e cambiare la riga `Thanks for creating ...`. Assicurati che l'applicazione venga eseguita localmente prima di distribuirla in {{site.data.keyword.cloud_notm}}.

    Prendi nota del file `manifest.yml`. Quando distribuisci la tua applicazione in {{site.data.keyword.cloud_notm}}, questo file viene utilizzato per determinare l'URL, l'allocazione di memoria, il numero di istanze e altri parametri fondamentali della tua applicazione.

    Esamina anche il file `README.md`, che contiene dettagli come le istruzioni di creazione.

    Se la tua applicazione è un'applicazione Liberty, devi crearla prima di distribuirla di nuovo.
    {: note}

  4. Accedi alla CLI {{site.data.keyword.cloud_notm}} con il tuo ID IBM. Se hai più account, ti viene richiesto di selezionare quale account utilizzare. Se non specifichi una regione con l'indicatore `-r`, devi scegliere anche una regione.
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    Se le tue credenziali vengono rifiutate, è possibile che tu stia utilizzando un ID federato. Per eseguire l'accesso con un ID federato, utilizza l'indicatore `--sso`. Per ulteriori informazioni, vedi [Accesso con un ID federato](/docs/iam/federated_id?topic=iam-federated_id#federated_id).
    {: tip}

  5. Dalla tua nuova directory, distribuisci la tua applicazione a {{site.data.keyword.cloud_notm}} utilizzando il comando [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).
    ```
    ibmcloud dev deploy <APP_NAME>
    ```
    {: codeblock}

  6. Accedi alla tua applicazione eseguendo il [comando `ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) per visualizzare l'URL della tua applicazione. Vai quindi all'URL nel tuo browser.
