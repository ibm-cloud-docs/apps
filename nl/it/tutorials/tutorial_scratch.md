---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Creazione di un'applicazione da zero
{: #tutorial-scratch}

Puoi creare un'applicazione personalizzata da zero utilizzando i servizi e un runtime. 
{: shortdesc}

## Prima di iniziare
{: #prereqs-scratch}

* Installa la [{{site.data.keyword.dev_cli_long}}](/docs/cli/index.html#overview), che include Docker. 
* Crea un account Docker, esegui l'applicazione Docker ed esegui l'accesso. Affinché i comandi di build funzionino è necessario che Docker sia in esecuzione.
* Se intendi distribuire la tua applicazione a [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about), devi [preparare il tuo account {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry/prepare-account.html#prepare).

## Creazione della tua applicazione
{: #create-scratch}

1. Dal tuo [dashboard {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://cloud.ibm.com), fai clic su **Crea un'applicazione** nel widget Applicazioni.

  Puoi anche creare un'applicazione personalizzata dalla pagina [Kit starter ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/developer/appservice/starter-kits/) nella {{site.data.keyword.dev_console}}.
  {: tip}

2. Immetti un nome per la tua applicazione. Per questa esercitazione, immetti `CustomProject`.
3. Immetti un nome host univoco, ad esempio `abc-devhost`. Il nome host viene utilizzato per l'instradamento della tua applicazione, ad esempio `abc-devhost.cloud.ibm.com`
4. Puoi, facoltativamente, fornire le tag per classificare la tua applicazione. Per ulteriori informazioni, consulta [Gestione delle tag](/docs/resources/tagging_resources.html#tag).
5. Seleziona il linguaggio e il framework. Alcuni kit starter potrebbero essere disponibili in un solo linguaggio.
6. Seleziona il tuo piano prezzi. Per questa esercitazione, puoi usare l'opzione gratuita.
7. Fai clic su **Create**.

## Aggiunta di risorse (facoltativo)
{: #resources-scratch}

Puoi aggiungere risorse che migliorano la tua applicazione con la potenza cognitiva di Watson, aggiungere servizi mobili o servizi per la sicurezza. Per questa esercitazione, puoi aggiungere un'ubicazione per gestire i tuoi dati.

1. Dalla finestra App Service, fai clic su **Add Resource**.
2. Seleziona il tipo di servizio che desideri. Ad esempio, seleziona **Data** > **Next** > **Cloudant** > **Next**.
3. Seleziona il tuo piano prezzi. Per questa esercitazione, puoi usare l'opzione gratuita.
4. Fai clic su **Create**.

## Creazione ed esecuzione dell'applicazione localmente
{: #build-run-scratch}

Puoi anche creare l'applicazione localmente per la verifica prima di distribuirla al cloud.

1. Dalla finestra App Service, fai clic su **Download Code** o **Clone your repo** per lavorare con il tuo codice in locale.
2. Importa l'applicazione nel tuo ambiente di sviluppo integrato.
3. Modifica il codice.
4. Imposta l'[autenticazione Git](/docs/services/ContinuousDelivery/git_working.html#git_authentication) aggiungendo un token di accesso personale.
5. Accedi all'interfaccia riga di comando (o CLI, command-line interface) {{site.data.keyword.cloud_notm}}. Se la tua organizzazione utilizza accessi federati, utilizza l'opzione `-sso`, ad esempio:

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Esegui il seguente comando per impostare le tue destinazioni di organizzazione e spazio.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. Esegui il seguente comando per richiamare le credenziali.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Assicurati che il Docker sia in esecuzione ed esegui il seguente comando per creare la tua applicazione in un contenitore di sviluppo locale dalla directory.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Esegui il seguente comando per eseguire la tua applicazione in un contenitore di sviluppo locale.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. Vai a `http://localhost:3000` nel tuo browser. Il tuo numero di porta potrebbe essere diverso a seconda del runtime scelto.

## Distribuzione della tua applicazione
{: #deploy-scratch}

Puoi distribuire la tua applicazione a {{site.data.keyword.cloud_notm}} in diversi modi, ma una toolchain DevOps è il modo migliore per distribuire le applicazioni di produzione. Con una toolchain DevOps, puoi facilmente automatizzare le distribuzioni in molti ambienti e aggiungere rapidamente servizi di monitoraggio, registrazione e avvisi per aiutare a gestire la tua applicazione man mano che cresce.

L'abilitazione di una toolchain crea un ambiente di sviluppo basato sul team per la tua applicazione. Quando crei una toolchain, il servizio dell'applicazione crea un repository Git, in cui puoi visualizzare il codice sorgente, clonare la tua applicazione e creare e gestire i problemi. Hai anche accesso a un ambiente di laboratorio Git dedicato e a una pipeline di fornitura continua. Sono personalizzati per l'ambiente di distribuzione che scegli, sia che si tratti di [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) o [Virtual Server (VSI)](/docs/vsi/vsi_index.html).

Tutte le toolchain che vengono create da un dashboard dello sviluppatore {{site.data.keyword.cloud_notm}} sono configurate per la distribuzione automatica.
{: note}

### Distribuzione manuale con una toolchain DevOps

Con una toolchain correttamente configurata, un ciclo di creazione-distribuzione viene avviato automaticamente con tutte le unioni al ramo master nel tuo repository. 

Puoi anche distribuire manualmente la tua applicazione dalla tua toolchain DevOps:

1. Dalla finestra dei dettagli dell'applicazione, fai clic su **View Toolchain**.
2. Fai clic su **Delivery pipeline** dove puoi iniziare le creazioni, gestire la distribuzione e visualizzare i log e la cronologia.

La fornitura continua è abilitata per alcune applicazioni. Puoi abilitare la fornitura continua per automatizzare le creazioni, i test e le distribuzioni tramite Delivery Pipeline e GitHub.

Per ulteriori informazioni, vedi:
* [Creazione e distribuzione ](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy) con Continuous Delivery.
* [Creazione di toolchain](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started) da un template.

### Distribuzione automatica con una toolchain DevOps

1. Dalla pagina App Details, fai clic su **Deploy to Cloud**.
2. Seleziona un metodo di distribuzione. Configura il tuo metodo di distribuzione in base alle istruzioni per il metodo che scegli:
  * **Deploy to [Kubernetes](/docs/apps/deploying/containers.html#containers)**. Questa opzione crea un cluster di host, denominati nodi di lavoro, per distribuire e gestire contenitori delle applicazioni ad elevata disponibilità. Puoi creare un cluster o distribuire un cluster esistente.
  * **Deploy to Cloud Foundry**. Questa opzione distribuisce la tua applicazione nativa del cloud senza che tu debba gestire l'infrastruttura sottostante. Se il tuo account ha accesso a {{site.data.keyword.cfee_full_notm}}, puoi selezionare un tipo di deployer **[Public Cloud](/docs/cloud-foundry-public/about-cf.html#about-cf)** o **[Enterprise Environment](/docs/cloud-foundry-public/cfee.html#cfee)**, che puoi utilizzare per creare e gestire ambienti isolati per ospitare applicazioni Cloud Foundry esclusivamente per la tua azienda.
  * **Deploy to a [Virtual Server](/docs/apps/vsi-deploy.html#vsi-deploy)**. Questa opzione esegue il provisioning di un'istanza del server virtuale, carica un'immagine che include la tua applicazione, crea una toolchain DevOps e avvia il primo ciclo di distribuzione per tuo conto.

La distribuzione della tua applicazione sul cloud nell'ultimo passo crea una toolchain automaticamente. La toolchain crea un repository Git per la tua applicazione dove puoi trovare il codice. 

### Distribuisci utilizzando {{site.data.keyword.dev_cli_short}}
{: #deploy-scratch-cli}

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

## Verifica che la tua applicazione sia in esecuzione
{: #verify-scratch}

Dopo che hai distribuito la tua applicazione, la Delivery Pipeline o la riga di comando ti indirizzano all'URL per la tua applicazione.

1. Dalla tua toolchain DevOps, fai clic su **Delivery Pipeline** e seleziona quindi **Deploy Stage**.
2. Fai clic su **View logs and history**.
3. Nel file di log, trova l'URL dell'applicazione:

    Alla fine del file di log, cerca la parola `urls` o `view`. Ad esempio, potresti vedere una riga nel file di log simile a `urls: my-app-devhost.cloud.ibm.com` o `View the application health at: http://<ipaddress>:<port>/health`.

4. Vai all'URL nel tuo browser. Se l'applicazione è in esecuzione, viene visualizzato un messaggio che include `Congratulations` o `{"status":"UP"}`.

Se stai utilizzando la riga di comando, esegui il comando [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) per visualizzare l'URL della tua applicazione. Vai quindi all'URL nel tuo browser.
