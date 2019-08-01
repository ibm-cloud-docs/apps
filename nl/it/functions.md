---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-29"

keywords: apps, serverless, serverless app, functions, cli, api, sdk, create serverless app, serverless app tutorial

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creazione di applicazioni senza server
{: #serverless}

Per lo sviluppo senza server, puoi utilizzare {{site.data.keyword.openwhisk}}, che è l'offerta FaaS (functions-as-a-service) di IBM. Puoi eseguire la logica dell'applicazione con {{site.data.keyword.openwhisk_short}} in risposta ad eventi o richiami diretti da applicazioni web o mobili su HTTP senza eseguire il provisioning o la gestione di server. {{site.data.keyword.openwhisk_short}} esegue l'amministrazione del sistema, come il ridimensionamento automatico, la gestione della disponibilità e la manutenzione in modo che tu, come sviluppatore, possa concentrarti sulla scrittura della logica dell'applicazione.
{:shortdesc}

Puoi sviluppare le tue applicazioni senza server utilizzando uno dei seguenti metodi:
* IU (interfaccia utente) {{site.data.keyword.openwhisk_short}}.
* CLI (command-line interface) {{site.data.keyword.openwhisk_short}}, che fornisce maggior controllo sulla tua distribuzione e le tue operazioni.
* Kit starter {{site.data.keyword.openwhisk_short}}, in cui puoi configurare la fornitura continua utilizzando una toolchain DevOps e una Delivery Pipeline.

Per informazioni più dettagliate su {{site.data.keyword.openwhisk_short}}, consulta la [documentazione](/docs/openwhisk?topic=cloud-functions-getting_started).


## Sviluppo con l'IU {{site.data.keyword.openwhisk_short}}
{: #serverless-apps-ui}

Prova {{site.data.keyword.openwhisk_short}} nel tuo [browser ](https://{DomainName}/functions/actions){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")}. Vai alla pagina [Concetti ](https://{DomainName}/functions/learn){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") per un'introduzione rapida dell'interfaccia utente {{site.data.keyword.openwhisk_short}}.

## Sviluppo con la CLI
{: #openwhisk_start_configure_cli}

Per ulteriori informazioni sull'installazione e sullo sviluppo con la CLI {{site.data.keyword.openwhisk_short}}, vedi [Configurazione della CLI {{site.data.keyword.openwhisk_short}}](https://{DomainName}/functions/cli){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno").

## Esposizione di API e dataset come azioni web
{: #expose-actions}

Per impostazione predefinita, {{site.data.keyword.openwhisk_short}} definisce le azioni che richiedono una chiave di autenticazione. Negli ambienti mobili di produzione, è spesso necessario autorizzare i client mobili basati sui flussi OAuth ad esporre API e specifici dataset.

{{site.data.keyword.openwhisk_short}} consente agli sviluppatori di esporre le proprie funzioni come azioni web, che sono annotate, per creare rapidamente applicazioni basate sul web. Puoi programmare la logica di back-end con azioni annotate a cui l'applicazione web può accedere in modo anonimo, senza richiedere una chiave di autenticazione {{site.data.keyword.openwhisk_short}}.

Per esporre un'azione come azione web, vai alla scheda **Endpoint** della tua azione e seleziona **Abilita come azione web**.

Ora, gli utenti possono raggiungere l'azione da una richiesta browser o cURL, ad esempio:
```
curl https://openwhisk.cloud.ibm.com/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

Output:
```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} fornisce un [SDK mobile](/docs/openwhisk?topic=cloud-functions-pkg_mobile_sdk) per dispositivi iOS e watchOS che consente alle applicazioni mobili di inviare facilmente trigger remoti e richiamare azioni remote.

## Creazione di applicazioni senza server utilizzando un kit starter
{: #serverless-starter}

Puoi utilizzare un kit starter per creare un'applicazione senza server, come ad esempio Python Example Serverless App. Per individuare i kit starter, completa questa procedura:

1. Vai alla pagina [App Service Starter Kits](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") nella console {{site.data.keyword.dev_console}}.
2. Immetti `serverless` nella barra di ricerca per filtrare l'elenco di kit starter.
3. Seleziona un kit starter senza server, come Python Example Serverless App.
4. Denomina la tua applicazione e seleziona un gruppo di risorse.
5. Facoltativo. Fornisci le tag per classificare la tua applicazione. Per ulteriori informazioni, consulta [Gestione delle tag](/docs/resources?topic=resources-tag).
6. Crea o seleziona un'istanza del servizio Cloudant esistente.
7. Facoltativo. Per ispezionare il tuo codice prima di aggiungere ulteriori servizi o distribuire la tua applicazione, fai clic su **View source code**. Controlla il file `README.md` per appurare se devi eseguire altre azioni per rendere operativa la tua applicazione.
8. Fai clic su **Crea**.

Ottimo inizio! Hai appena creato un'applicazione!

## Aggiungi servizi (facoltativo)
{: #serverless-services}

Se un kit starter richiede servizi specifici, sono disponibili dei servizi di cui viene eseguito il provisioning in automatico in modo che le istanze per tali servizi siano automaticamente create quando crei un'applicazione.

1. Sulla pagina App details, fai clic su **Create service** o **Connect existing services**, a seconda se hai già dei servizi che vuoi connettere a questa applicazione.
2. Seleziona il tipo di servizio che desideri e segui le istruzioni per aggiungere un servizio esistente alla tua applicazione o creare un'istanza del servizio.

Dopo aver aggiunto tutti i servizi desiderati, essi vengono visualizzati nella pagina App details.

## Distribuisci la tua applicazione
{: #serverless-deploy}

Per distribuire la tua applicazione, completa la seguente procedura:

1. Nella pagina App details, fai clic su **Deploy**.
2. Seleziona **Deploy to Cloud Functions** e fai clic su **Next**.
3. Nella pagina Configure toolchain, immetti un nome di tookchain, seleziona una regione e fai clic su **Create**. Dopo aver selezionato e configurato la destinazione di distribuzione, la pagina App details indica che la fornitura continua è stata configurata.
4. Facoltativo. Riesamina le azioni nella console {{site.data.keyword.openwhisk_short}} facendo clic sull'icona Actions ![Icona More Actions](../icons/action-menu-icon.svg) e selezionando **Open Cloud Functions**.
5. Facoltativo. Visualizza il repository che contiene il codice generato per la tua applicazione e i tuoi servizi facendo clic su **View repo**.

## Verifica che la tua applicazione sia distribuita
{: #serverless-verify}

Con una toolchain correttamente configurata, un ciclo di creazione-distribuzione viene avviato automaticamente con tutte le unioni al ramo master nel tuo repository. Per ulteriori informazioni, vedi [Creazione e distribuzione](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

Per verificare che la tua applicazione sia stata distribuita correttamente, completa la seguente procedura:

1. Dalla pagina App details, fai clic su **View toolchain**.
2. Fai clic su **Delivery Pipeline** dove puoi iniziare le creazioni, gestire la distribuzione e visualizzare i log e la cronologia.
3. Se la distribuzione ha esito positivo, ogni fase della pipeline indica **Stage Passed**.
4. Per visualizzare le informazioni sull'azione e sull'API, fai clic su **View logs and history** nel tile **Deploy Stage**.
