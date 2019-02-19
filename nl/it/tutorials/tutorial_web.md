---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creazione di un'applicazione web di base con un kit starter
{: #tutorial-webapp}

{{site.data.keyword.cloud}} offre molti kit starter per aiutarti a codificare rapidamente. Scegli un linguaggio, un framework e gli strumenti dai kit starter del servizio dell'applicazione per iniziare a lavorare con un'applicazione personalizzata preconfigurata. In questa esercitazione, vengono illustrati i passi per installare gli strumenti di cui hai bisogno, creare ed eseguire l'applicazione localmente e distribuirla sul cloud.
{: shortdesc}

## Passo 1. Installa gli strumenti
{: #prereqs-webapp}

Installa gli [strumenti sviluppatore](/docs/cli/index.html#overview).

Docker viene installato come parte degli strumenti per sviluppatori. Affinché i comandi di build funzionino è necessario che Docker sia in esecuzione. Devi creare un account Docker, eseguire l'applicazione Docker ed effettuare l'accesso.

## Passo 2. Seleziona un kit starter
{: #create-webapp}

I kit starter sono disponibili in molti linguaggi e framework in {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}. Per iniziare, seleziona il linguaggio più adatto al tuo progetto.

1. Dalla pagina dei [starter kits ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/developer/appservice/starter-kits/) in {{site.data.keyword.dev_console}}, seleziona un kit starter per il tuo linguaggio.
2. Immetti il nome della tua applicazione e un nome host univoco, ad esempio `abc-devhost`. Questo nome host è l'instradamento della tua applicazione, `abc-devhost.cloud.ibm.com`
3. Facoltativo. Fornisci le tag per classificare la tua applicazione. Per ulteriori informazioni, consulta [Gestione delle tag](/docs/resources/tagging_resources.html#tag).
4. Seleziona il linguaggio e il framework. Alcuni kit starter potrebbero essere disponibili solo in un linguaggio.
5. Seleziona il tuo piano prezzi. È disponibile un'opzione gratuita che puoi utilizzare per questa esercitazione.
6. Fai clic su **Create**.

## Passo 3. Aggiungi risorse (facoltativo)
{: #resources-webapp}

Puoi aggiungere risorse che migliorano la tua applicazione con la potenza cognitiva di Watson, aggiungere servizi mobili o servizi per la sicurezza. Per questa esercitazione, aggiungi una posizione per gestire i tuoi dati.

1. Dalla finestra App Service, fai clic su **Add Resource**.
2. Seleziona il tipo di servizio che desideri. Ad esempio, seleziona **Data** > **Next** > **Cloudant** > **Next**.
3. Seleziona il tuo piano prezzi. È disponibile un'opzione gratuita che puoi utilizzare per questa esercitazione.
4. Fai clic su **Create**.

## Passo 4. Crea una toolchain DevOps
{: #toolchain-webapp}

L'abilitazione di una toolchain crea un ambiente di sviluppo basato sul team per la tua applicazione. Quando crei una toolchain, il servizio dell'applicazione crea un repository Git, in cui puoi visualizzare il codice sorgente, clonare la tua applicazione e creare e gestire i problemi. Hai anche accesso a un ambiente di laboratorio Git dedicato e a una pipeline di fornitura continua. Sono personalizzati per l'ambiente di distribuzione che scegli, sia che si tratti di [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) o [Virtual Server (VSI)](/docs/vsi/vsi_index.html).

La fornitura continua è abilitata per alcune applicazioni. Puoi abilitare la fornitura continua per automatizzare le creazioni, i test e le distribuzioni tramite Delivery Pipeline e GitHub.

Fai clic su **Deploy to Cloud** nella pagina App details, seleziona un ambiente di distribuzione e fai clic su **Create**. {{site.data.keyword.cloud_notm}} crea automaticamente una toolchain aperta completa di un repository Git e della pipeline di fornitura continua.

Dopo che hai selezionato il tuo ambiente di distribuzione, apri il componente pipeline della tua nuova toolchain per iniziare il processo iniziale di creazione e distribuzione in modo da poter vedere la tua nuova applicazione nel giro di qualche minuto.

Per ulteriori informazioni, vedi [Creazione delle toolchain](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

## Passo 5. Crea ed esegui l'applicazione localmente
{: #build-run-webapp}

La distribuzione della tua applicazione sul cloud nell'ultimo passo ha creato una toolchain. Una toolchain crea un repository Git per la tua applicazione in cui puoi trovare il codice. Segui questa procedura per accedere al tuo repository. Puoi creare localmente l'applicazione per il test prima di inviarla al cloud.

1. Dalla finestra App Service, fai clic su **Download Code** o **Clone your repo** per lavorare con il tuo codice in locale.
2. Importa l'applicazione nel tuo ambiente di sviluppo integrato.
3. Modifica il codice.
4. Imposta l'[autenticazione Git](/docs/services/ContinuousDelivery/git_working.html#git_authentication) aggiungendo un token di accesso personale.
5. Accedi all'interfaccia riga di comando {{site.data.keyword.cloud_notm}}. Se la tua organizzazione utilizza gli accessi federati, usa l'opzione `-sso`.

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Imposta le destinazioni per la tua organizzazione e il tuo spazio.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. Ottieni le credenziali.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Assicurati che Docker sia in esecuzione e crea la tua applicazione in un contenitore di sviluppo locale dalla directory.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Esegui la tua applicazione in un contenitore di sviluppo locale.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. Apri il tuo browser a `http://localhost:3000`. Il tuo numero di porta potrebbe essere diverso a seconda del runtime scelto.

## Passo 6. Distribuisci la tua applicazione
{: #deploy-webapp}

### Distribuisci utilizzando una toolchain
{: #deploy-webapp-toolchain}

Puoi distribuire la tua applicazione a {{site.data.keyword.cloud_notm}} in diversi modi, ma una toolchain DevOps è il modo migliore per distribuire le applicazioni di produzione. Con una toolchain DevOps, puoi facilmente automatizzare le distribuzioni in molti ambienti e aggiungere rapidamente servizi di monitoraggio, registrazione e avvisi per aiutare a gestire la tua applicazione man mano che cresce.

Con una toolchain correttamente configurata, un ciclo di creazione-distribuzione viene avviato automaticamente con tutte le unioni al ramo master nel tuo repository. Tutte le toolchain che vengono create da un dashboard di sviluppo {{site.data.keyword.cloud_notm}} sono configurate per la distribuzione automatica.

Puoi anche distribuire manualmente la tua applicazione dalla tua toolchain DevOps:

1. Dalla finestra dei dettagli dell'applicazione, fai clic su **View Toolchain**.
2. Fai clic su **Delivery pipeline** dove puoi iniziare le creazioni, gestire la distribuzione e visualizzare i log e la cronologia.

Per ulteriori informazioni, vedi [Creazione e distribuzione](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy).

### Distribuisci utilizzando {{site.data.keyword.dev_cli_short}}
{: #deploy-webapp-cli}

Per distribuire la tua applicazione a Cloud Foundry, immetti il seguente comando:
```
ibmcloud dev deploy
```
{: pre}

Per distribuire la tua applicazione a un cluster Kubernetes, immetti il seguente comando:
```
ibmcloud dev deploy --target <container>
```
{: pre}

## Passo 7. Verifica che la tua applicazione sia in esecuzione
{: #verify-webapp}

Dopo che hai distribuito la tua applicazione, la Delivery Pipeline o la riga di comando ti indirizzano all'URL per la tua applicazione.

1. Dalla tua toolchain DevOps, fai clic su **Delivery Pipeline** e seleziona quindi **Deploy Stage**.
2. Fai clic su **View logs and history**.
3. Nel file di log, trova l'URL dell'applicazione:

    Alla fine del file di log, cerca la parola `urls` o `view`. Ad esempio, potresti vedere una riga nel file di log simile a `urls: my-app-devhost.cloud.ibm.com` o `View the application health at: http://<ipaddress>:<port>/health`.

4. Vai all'URL nel tuo browser. Se l'applicazione è in esecuzione, viene visualizzato un messaggio che include `Congratulations` o `{"status":"UP"}`.

Se stai utilizzando la riga di comando, esegui il comando [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) per visualizzare l'URL della tua applicazione. Vai quindi all'URL nel tuo browser.
