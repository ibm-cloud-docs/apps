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

# Creazione di un microservizio
{: #tutorial-microservice}

Puoi creare un'applicazione da uno starter di base del microservizio. Utilizza questi starter per creare un backend del microservizio per Node, Java o Python con una scelta di framework web. Puoi vedere come installare gli strumenti di cui hai bisogno, creare ed eseguire l'applicazione localmente e distribuirla al cloud.
{: shortdesc}

## Passo 1. Installa gli strumenti
{: #prereqs-microservice}

* Installa gli [strumenti sviluppatore](/docs/cli/index.html#overview).
* Docker viene installato come parte degli strumenti per sviluppatori. Affinché i comandi di build funzionino è necessario che Docker sia in esecuzione. Devi creare un account Docker, eseguire l'applicazione Docker ed effettuare l'accesso.
* Se intendi distribuire la tua applicazione a [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about), devi [preparare il tuo account {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry/prepare-account.html#prepare).

## Passo 2. Crea un'applicazione
{: #create-microservice}

Crea un'applicazione in {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}:

1. Dalla pagina dei [Starter Kits ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/developer/appservice/starter-kits/) in {{site.data.keyword.dev_console}}, seleziona un kit starter per il tuo linguaggio. Ad esempio, per un'applicazione Node.js, vai a **Express.js Microservice** e fai clic su **Select Starter Kit**.
2. Immetti il nome della tua applicazione. Per questa esercitazione, utilizza `MicroserviceProject`.
3. Immetti un nome host univoco, ad esempio `abc-devhost`. Questo nome host è l'instradamento della tua applicazione, `abc-devhost.cloud.ibm.com`
4. Facoltativo. Fornisci le tag per classificare la tua applicazione. Per ulteriori informazioni, consulta [Gestione delle tag](/docs/resources/tagging_resources.html#tag).
5. Seleziona il linguaggio e il framework. Alcuni kit starter potrebbero essere disponibili solo in un linguaggio.
6. Seleziona il tuo piano prezzi. È disponibile un'opzione gratuita che puoi utilizzare per questa esercitazione.
7. Fai clic su **Crea**.

## Passo 3. Aggiungi risorse (facoltativo)
{: #resources-microservice}

Puoi aggiungere risorse che migliorano la tua applicazione con la potenza cognitiva di Watson, aggiungere servizi mobili o servizi per la sicurezza. Per questa esercitazione, aggiungi una posizione per gestire i tuoi dati.

1. Dalla finestra App Service, fai clic su **Add Resource**.
2. Seleziona il tipo di servizio che desideri. Ad esempio, seleziona **Data** > **Next** > **Cloudant** > **Next**.
3. Seleziona il tuo piano prezzi. È disponibile un'opzione gratuita che puoi utilizzare per questa esercitazione.
4. Fai clic su **Crea**.

## Passo 4. Crea una toolchain DevOps
{: #toolchain-microservice}

L'abilitazione di una toolchain crea un ambiente di sviluppo basato sul team per la tua applicazione. Quando crei una toolchain, il servizio dell'applicazione crea un repository Git, in cui puoi visualizzare il codice sorgente, clonare la tua applicazione e creare e gestire i problemi. Hai anche accesso a un ambiente di laboratorio Git dedicato e a una pipeline di fornitura continua. Sono personalizzati per l'ambiente di distribuzione che scegli, sia che si tratti di [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) o [Virtual Server (VSI)](/docs/vsi/vsi_index.html).

Tutte le toolchain che vengono create da un dashboard dello sviluppatore {{site.data.keyword.cloud_notm}} sono configurate per la distribuzione automatica.
{: note}

1. Dalla pagina App Details, fai clic su **Deploy to cloud**.
2. Seleziona un metodo di distribuzione. Configura il tuo metodo di distribuzione in base alle istruzioni per il metodo che scegli:
  * **Deploy to [Kubernetes](/docs/apps/deploying/containers.html#containers)**. Questa opzione crea un cluster di host, denominati nodi di lavoro, per distribuire e gestire contenitori delle applicazioni ad elevata disponibilità. Puoi creare un cluster o distribuire un cluster esistente.
  * **Deploy to Cloud Foundry**. Questa opzione distribuisce la tua applicazione nativa del cloud senza che tu debba gestire l'infrastruttura sottostante. Se il tuo account ha accesso a {{site.data.keyword.cfee_full_notm}}, puoi selezionare un tipo di deployer **[Public Cloud](/docs/cloud-foundry-public/about-cf.html#about-cf)** o **[Enterprise Environment](/docs/cloud-foundry-public/cfee.html#cfee)**, che puoi utilizzare per creare e gestire ambienti isolati per ospitare applicazioni Cloud Foundry esclusivamente per la tua azienda.
  * **Deploy to a [Virtual Server](/docs/apps/vsi-deploy.html#vsi-deploy)**. Questa opzione esegue il provisioning di un'istanza del server virtuale, carica un'immagine che include la tua applicazione, crea una toolchain DevOps e avvia il primo ciclo di distribuzione per tuo conto.

## Passo 5. Crea ed esegui l'applicazione localmente
{: #build-run-microservice}

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

7.  Ottieni le credenziali.

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

10.  Apri il tuo browser a `http://localhost:3000`. Il tuo numero di porta potrebbe essere diverso a seconda del runtime scelto.

## Passo 6. Distribuisci la tua applicazione
{: #deploy-microservice}

### Distribuisci utilizzando una toolchain
{: #deploy-microservice-toolchain}

Puoi distribuire la tua applicazione a {{site.data.keyword.cloud_notm}} in diversi modi, ma una toolchain DevOps è il modo migliore per distribuire le applicazioni di produzione. Con una toolchain DevOps, puoi facilmente automatizzare le distribuzioni in molti ambienti e aggiungere rapidamente servizi di monitoraggio, registrazione e avvisi per aiutare a gestire la tua applicazione man mano che cresce.

Con una toolchain correttamente configurata, un ciclo di creazione-distribuzione viene avviato automaticamente con tutte le unioni al ramo master nel tuo repository. Tutte le toolchain che vengono create da un dashboard dello sviluppatore {{site.data.keyword.cloud_notm}} sono configurate per la distribuzione automatica.

Puoi anche distribuire manualmente la tua applicazione dalla tua toolchain DevOps:

1. Dalla finestra dei dettagli dell'applicazione, fai clic su **View Toolchain**.

2. Fai clic su **Delivery pipeline** dove puoi iniziare le creazioni, gestire la distribuzione e visualizzare i log e la cronologia.

### Distribuisci utilizzando {{site.data.keyword.dev_cli_short}}
{: #deploy-microservice-cli}

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
{: #verify-microservice}

Dopo che hai distribuito la tua applicazione, la Delivery Pipeline o la riga di comando ti indirizzano all'URL per la tua applicazione.

1. Dalla tua toolchain DevOps, fai clic su **Delivery Pipeline** e seleziona quindi **Deploy Stage**.
2. Fai clic su **View logs and history**.
3. Nel file di log, trova l'URL dell'applicazione:

    Alla fine del file di log, cerca la parola `urls` o `view`. Ad esempio, potresti vedere una riga nel file di log simile a `urls: my-app-devhost.cloud.ibm.com` o `View the application health at: http://<ipaddress>:<port>/health`.

4. Vai all'URL nel tuo browser. Se l'applicazione è in esecuzione, viene visualizzato un messaggio che include `Congratulations` o `{"status":"UP"}`.

Se stai utilizzando la riga di comando, esegui il comando [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) per visualizzare l'URL della tua applicazione. Vai quindi all'URL nel tuo browser.
