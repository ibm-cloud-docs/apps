---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-07-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creazione di un'applicazione personalizzata
{: #tutorial}

Puoi creare un'applicazione personalizzata utilizzando i servizi e un runtime. Puoi vedere come installare gli strumenti di cui hai bisogno, creare ed eseguire l'applicazione localmente e distribuirla al cloud.
{: shortdesc}

## Passo 1: Installa gli strumenti
{: #install-tools}

Installa gli [strumenti per sviluppatori ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.

Docker viene installato come parte degli strumenti per sviluppatori. Affinché i comandi di build funzionino è necessario che Docker sia in esecuzione. Devi creare un account Docker, eseguire l'applicazione Docker ed effettuare l'accesso.

## Passo 2: Crea un'applicazione
{: #create-devex}

Crea un'applicazione in {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}:

1. Dalla pagina dei [Starter Kits ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) in {{site.data.keyword.dev_console}}, seleziona **Create** per creare un'applicazione personalizzata.

2. Immetti il nome della tua applicazione. Per questa esercitazione, utilizza `CustomProject`.
3. Immetti un nome host univoco, ad esempio `abc-devhost`. Questo nome host è la rotta della tua applicazione, `abc-devhost.mybluemix.net`
4. Seleziona il linguaggio e il framework. Alcuni kit starter potrebbero essere disponibili solo in un linguaggio.
5. Seleziona il tuo piano prezzi. È disponibile un'opzione gratuita che puoi utilizzare per questa esercitazione.
6. Fai clic su **Create**.

## Passo 3: Aggiungi risorse (facoltativo)
{: #add-services}

Puoi aggiungere risorse che migliorano la tua applicazione con la potenza cognitiva di Watson, aggiungere servizi mobili o servizi per la sicurezza. Per questa esercitazione, aggiungi una posizione per gestire i tuoi dati.

1. Dalla finestra del servizio dell'applicazione, fai clic su **Add Resource**.
2. Seleziona il tipo di servizio che desideri. Ad esempio, seleziona **Data** > **Next** > **Cloudant** > **Next**.
3. Seleziona il tuo piano prezzi. È disponibile un'opzione gratuita che puoi utilizzare per questa esercitazione.
4. Fai clic su **Crea**.

## Passo 4: Crea una toolchain DevOps
{: #add-toolchain}

L'abilitazione di una toolchain crea un ambiente di sviluppo basato sul team per la tua applicazione. Quando crei una toolchain, il servizio dell'applicazione crea un repository Git, in cui puoi visualizzare il codice sorgente, clonare la tua applicazione e creare e gestire i problemi. Hai anche accesso a un ambiente di laboratorio Git dedicato e a una pipeline di fornitura continua. Questi sono personalizzati per la piattaforma di distribuzione che scegli, che si tratti di Kubernetes o Cloud Foundry.

La fornitura continua è abilitata per alcune applicazioni. Puoi abilitare la fornitura continua per automatizzare le creazioni, i test e le distribuzioni tramite Delivery Pipeline e GitHub.

1. Dalla finestra del servizio dell'applicazione, fai clic su **Deploy to Cloud**.
2. Seleziona un metodo di distribuzione. Imposta il metodo di distribuzione in base alle istruzioni per il metodo scelto.

    * Distribuisci a un cluster Kubernetes. Crea un cluster di host, chiamati nodi di lavoro, per distribuire e gestire contenitori dell'applicazione a elevata disponibilità. Puoi creare un cluster o distribuire un cluster esistente.

    * Distribuisci con Cloud Foundry, dove non è necessario gestire l'infrastruttura sottostante.

## Passo 5: Crea ed esegui l'applicazione localmente
{: #build-run}

La distribuzione della tua applicazione sul cloud nell'ultimo passo ha creato una toolchain. Una toolchain crea un repository Git per la tua applicazione in cui puoi trovare il codice. Segui questa procedura per accedere al tuo repository. Puoi creare localmente l'applicazione per il test prima di inviarla al cloud.

1. Dalla finestra del servizio dell'applicazione, fai clic su **Download Code** o **Clone your repo** per lavorare con il codice in locale.
2. Importa l'applicazione nel tuo ambiente di sviluppo integrato.
3. Modifica il codice.
4. Imposta l'[autenticazione Git](/docs/services/ContinuousDelivery/git_working.html#git_authentication) aggiungendo un token di accesso personale.
5. Accedi all'interfaccia riga di comando {{site.data.keyword.Bluemix}}. Se la tua organizzazione utilizza gli accessi federati, usa l'opzione `-sso`.

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

## Passo 6: Distribuisci al cloud
{: #deploy}

### Distribuisci utilizzando una toolchain

Puoi distribuire la tua applicazione a {{site.data.keyword.cloud_notm}} in diversi modi, ma una toolchain DevOps è il modo migliore per distribuire le applicazioni di produzione. Con una toolchain DevOps, puoi facilmente automatizzare le distribuzioni in molti ambienti e aggiungere rapidamente servizi di monitoraggio, registrazione e avvisi per aiutare a gestire la tua applicazione man mano che cresce.

Con una toolchain correttamente configurata, un ciclo di creazione-distribuzione viene avviato automaticamente con tutte le unioni al ramo master nel tuo repository. Tutte le toolchain che vengono create da un dashboard di sviluppo {{site.data.keyword.cloud_notm}} sono configurate per la distribuzione automatica.

Puoi anche distribuire manualmente la tua applicazione dalla tua toolchain DevOps:

1. Dalla finestra dei dettagli dell'applicazione, fai clic su **View Toolchain**.

2. Fai clic su **Delivery pipeline** dove puoi iniziare le creazioni, gestire la distribuzione e visualizzare i log e la cronologia.

### Distribuisci utilizzando {{site.data.keyword.dev_cli_short}}

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

## Passo 7: Verifica che la tua applicazione sia in esecuzione
{: #verify}

Dopo aver distribuito la tua applicazione, la pipeline DevOps o la riga di comando ti indirizzano all'URL della tua applicazione, ad esempio `abc-devhost.mybluemix.net`. Vai a tale URL nel tuo browser.
