---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-23"

keywords: getting started apps, create app tutorial, add services, deploy apps, create app, app tutorial

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Esercitazione introduttiva
{: #tutorial-getting-started}

Puoi creare delle applicazioni web e mobili pronte per l'azienda in {{site.data.keyword.cloud}} e avvalerti delle estensioni cloud ospitate da {{site.data.keyword.cloud_notm}}. Hai diverse opzioni per iniziare a lavorare. Crea un'applicazione con un kit starter che gestisce il processo per tuo conto oppure, se sai cosa desideri, inizia da zero e crea la tua applicazione con le risorse di cui hai bisogno oppure utilizza il tuo repository esistente e porta il tuo codice.
{: shortdesc}

Sia che tu abbia del [codice esistente](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc) che vuoi modernizzare e portare nel cloud o che stia sviluppando una [nuova applicazione](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit), puoi attingere all'ecosistema in rapida crescita dei servizi disponibili e dei framework runtime in {{site.data.keyword.cloud_notm}}.

Hai bisogno di aiuto per decidere da dove iniziare? Vedi questo diagramma per alcune idee!

![Panoramica sull'esperienza degli sviluppatori](images/dev-journey.png "Panoramica sull'esperienza degli sviluppatori")

## Prima di iniziare
{: #prereqs-getting-started}

Puoi creare la tua applicazione utilizzando l'interfaccia di riga di comando (o CLI, command-line interface) o la console {{site.data.keyword.cloud_notm}}. Se desideri utilizzare la CLI, vedi la [procedura di installazione](/docs/cli?topic=cloud-cli-ibmcloud-cli).

## Passo 1. Crea la tua applicazione
{: #create-getting-started}

Crea un'applicazione selezionando uno dei seguenti punti di ingresso:

* I [kit starter](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit) sono specifici per il caso di utilizzo e producono applicazioni pronte per la produzione in vari linguaggi di programmazione e modelli architetturali.
* I [modelli di codice IBM Developer ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://developer.ibm.com/patterns/){:new_window} ti aiutano a creare rapidamente la tua applicazione e a distribuirla in {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Modelli di codice](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern).
* [Porta il tuo codice](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc) collegandoti al tuo repository di contenuti esistente. La tua applicazione e l'immagine Docker si devono trovare nello stesso repository.
* Se sai cosa desideri, crea da zero un'[applicazione personalizzata](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch) con i servizi di cui hai bisogno utilizzando un kit starter vuoto.
* Crea e distribuisci un'applicazione personalizzata o kit starter utilizzando la [CLI e gli strumenti per gli sviluppatori](/docs/apps?topic=creating-apps-create-deploy-app-cli).
* Sfoglia o cerca nel [catalogo {{site.data.keyword.cloud_notm}}](https://{DomainName}/catalog){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") le applicazioni e i servizi che puoi creare e iniziare a utilizzare oggi stesso.

## Passo 2. Aggiungi i servizi
{: #resources-getting-started}

Quando utilizzi un kit starter per creare la tua applicazione, i servizi obbligatori vengono creati automaticamente per tuo conto. Puoi connettere più servizi alla tua applicazione nella console dalla pagina **App details**, che viene visualizzata appena crei l'applicazione.

Se vuoi aggiungere dei servizi dopo aver creato la tua applicazione, vai al [dashboard {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}), individua la tua applicazione e fai quindi clic sul suo nome. Viene visualizzata la pagina **App details** dove puoi creare un'istanza del servizio o connettere dei servizi esistenti.

Oppure puoi eseguire il seguente comando per aggiungere un servizio alla tua applicazione utilizzando la CLI. Puoi selezionare un servizio esistente da uno già abilitato sul tuo account o aggiungere un servizio.
```
ibmcloud dev edit
```
{: codeblock}

Per ulteriori informazioni, vedi [Aggiunta di un servizio alla tua applicazione](/docs/apps?topic=creating-apps-add-resource).

## Passo 3. Distribuisci la tua applicazione
{: #deploy-getting-started}

Puoi distribuire la tua applicazione utilizzando la console o la CLI.

### Utilizzo della console
{: #console-getting-started}

Per distribuire la tua applicazione utilizzando la console, completa la seguente procedura:

1. Nella pagina **App details**, fai clic su **Configure continuous delivery**.
2. Seleziona una destinazione di distribuzione, le impostazioni della toolchain e fai clic su **Create**. {{site.data.keyword.cloud_notm}} crea automaticamente una toolchain aperta completa di un repository Git e della pipeline di fornitura continua.
3. Apri la fase pipeline della tua nuova toolchain per visualizzare il processo di creazione e sviluppo in modo da poter vedere la tua nuova applicazione nel giro di qualche minuto.

Per ulteriori informazioni, consulta la tabella dei contenuti per diversi argomenti di distribuzione nella sezione "Distribuzione e integrazione delle applicazioni".

### Utilizzo della CLI
{: #cli-getting-started}

Per distribuire la tua applicazione utilizzando la CLI, esegui il comando `ibmcloud dev deploy`. Per ulteriori informazioni, vedi [Creazione e distribuzione delle applicazioni utilizzando la CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli).

Ora sei pronto per lo sviluppo iterativo e la fornitura continua.

## Informazioni correlate
{: #related-getting-started}

Le [Guide alla programmazione](https://{DomainName}/docs/home/build){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") sono disponibili per linguaggio per aiutarti ad essere operativo. Hai molte opzioni per ospitare le tue applicazioni con l'infrastruttura {{site.data.keyword.cloud_notm}} dai {{site.data.keyword.baremetal_short}} da eseguire come una funzione senza server.
