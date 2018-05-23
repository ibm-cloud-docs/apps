---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-02"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creazione di un'applicazione di base con un kit starter
{: #tutorial}

Puoi creare un'applicazione da uno starter web di base. Utilizza questi starter per configurare un server web semplice per Node, Java o Python con una scelta di framework web. Puoi vedere come installare gli strumenti di cui hai bisogno, creare ed eseguire l'applicazione localmente e distribuirla al cloud.
{: shortdesc}

## Passo 1: Installa gli strumenti
{: #before-you-begin}

Installa gli [strumenti per sviluppatori ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.


## Passo 2: Crea un'applicazione
{: #create-devex}

Crea un'applicazione in {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}:

1. Dalla pagina dei [Starter Kits ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) in {{site.data.keyword.dev_console}}, seleziona un kit starter per il tuo linguaggio. Ad esempio, per un'applicazione Node.js, seleziona **Express.js Basic** e quindi **Create**.

2. Immetti il nome della tua applicazione. Per questa esercitazione, utilizza `WebBasicProject`.   

3. Immetti un nome host univoco, come ad esempio le tue iniziali più `-devhost`. Ad esempio:

	```
	abc-devhost
	```

	Questo nome host è la rotta della tua applicazione. Ad esempio, `abc-devhost.mybluemix.net`

4. Seleziona la tua piattaforma di linguaggio. Per questa esercitazione, utilizza `Node.js`.

5. Fai clic su **Crea**.

## Facoltativo: aggiungi risorse
{: #add-services}

1. Dalla vista **App Details**, fai clic su **Add Resource**.

2. Seleziona il tipo di servizio che desideri. Per questa esercitazione, seleziona **Data** > **Next** > **Cloudant NoSQL DB** > **Next**.

3. Fai clic su **Crea**.

## Facoltativo: crea toolchain DevOps
{: #add-toolchain}

L'abilitazione di una toolchain crea un ambiente di sviluppo basato sul team per la tua applicazione. Quando crei una toolchain, il servizio dell'applicazione eseguirà il provisioning di un repository Git, dove puoi visualizzare il codice sorgente, clonare la tua applicazione e creare e gestire i problemi. Hai anche accesso a un ambiente Gitlab dedicato e a una pipeline di fornitura continua che viene personalizzata per la piattaforma di distribuzione che scegli, come Kubernetes o Cloud Foundry.

La fornitura continua è abilitata per alcune applicazioni. Potresti voler abilitare la fornitura continua per automatizzare le creazioni, i test e le distribuzioni tramite Delivery Pipeline e GitHub.

1. Seleziona la tua applicazione nella pagina **Apps**.

2. Fai clic su **Deploy to Cloud**.

3. Seleziona un metodo di distribuzione. Puoi scegliere uno tra:

	* Distribuisci a un cluster Kubernetes. Esegui il provisioning di un cluster di host, nodi di lavoro richiamati, per distribuire e gestire i contenitori dell'applicazione ad elevata disponibilità. Puoi creare un cluster o distribuire un cluster esistente.

	* Distribuisci utilizzando Cloud Foundry, dove non devi gestire l'infrastruttura sottostante.

## Passo 3: Genera il tuo codice applicazione
{: #generate-code}

Se hai creato una toolchain nel passo precedente, è stato creato un repository Git per la tua applicazione e puoi trovare il codice lì. Segui queste istruzioni per accedere al tuo repository:

1. Seleziona la tua applicazione nella pagina **Apps**.

2. Fai clic su **View Toolchain**.

3. Fai clic sulla scheda **Git** nell'intestazione **CODE** per aprire il tuo repository, dove puoi visualizzare il codice sorgente e clonare la tua applicazione.

Se una toolchain non è abilitata, puoi accedere al tuo codice scaricando il sorgente direttamente dalla vista dei dettagli dell'applicazione.

1. Seleziona la tua applicazione nella pagina **Apps**.

2. Fai clic su **Download Code** per scaricare il tuo archivio dell'applicazione.

## Fase 4: Inizia ad utilizzare la tua applicazione
{: #code}

Inizia ad utilizzare la tua applicazione scaricata:

1. Espandi il file archiviato.

2. Importa l'applicazione nella tua IDE.

3. Modifica il codice.

4. Utilizza {{site.data.keyword.dev_cli_notm}} per creare ed eseguire il tuo codice localmente.

## Passo 5: Crea ed esegui l'applicazione localmente
{: #build-run}

Aggiungi il tuo codice, crea ed esegui l'applicazione. Puoi eseguire l'applicazione localmente sul tuo sistema host se installi gli strumenti di build necessari o utilizzando il supporto del contenitore disponibile in {{site.data.keyword.dev_cli_notm}}.

### Utilizzo di {{site.data.keyword.dev_cli_short}}

1. Installa le dipendenze del nodo:

  ```
  npm install
  ```
  {: codeblock}

2. Integra il tuo codice frontend in un modulo:

  ```
  gulp
  ```
  {: codeblock}

3. Per creare l'applicazione nella tua directory dell'applicazione corrente, immetti il seguente comando:

  ```
  bx dev build
  ```
  {: codeblock}

4. Per eseguire l'applicazione nella tua directory dell'applicazione corrente, immetti il seguente comando:

  ```
  bx dev run
  ```
  {: codeblock}

5. Apri il tuo browser a `http://localhost:3000`. Il tuo numero porta può essere diverso, a seconda del tuo runtime selezionato.


## Passo 6: Distribuisci al cloud
{: #deploy}

### Distribuisci utilizzando una toolchain
Esistono diversi modi per distribuire la tua applicazione a {{site.data.keyword.cloud_notm}} ma l'utilizzo di una toolchain DevOps è il modo migliore per distribuire le applicazioni di produzione. Una toolchain DevOps consente di automatizzare facilmente le distribuzioni a più ambienti e di aggiungere rapidamente i servizi di monitoraggio, registrazione e segnalazione per aiutarti nella gestione della tua applicazione come cresce.

Con una toolchain correttamente configurata, un ciclo di creazione-distribuzione viene avviato automaticamente con tutte le unioni al ramo master nel tuo repository. Tutte le toolchain create da un dashboard di sviluppo {{site.data.keyword.cloud_notm}} sono configurate per la distribuzione automatica.

Puoi anche distribuire manualmente la tua applicazione dalla tua toolchain DevOps:

1. Seleziona la tua applicazione nella pagina **Apps**.

2. Fai clic su **View Toolchain**.

3. Visualizza la tua pipeline di fornitura dove puoi iniziare a creare, gestire la distribuzione e a visualizzare i log e la cronologia.

### Distribuisci utilizzando {{site.data.keyword.dev_cli_short}}
Se scegli di non utilizzare una toolchain, puoi anche distribuire utilizzando {{site.data.keyword.dev_cli_short}}.

Per distribuire la tua applicazione a Cloud Foundry, immetti il seguente comando:

  ```
  bx dev deploy
  ```
  {: codeblock}

Per distribuire la tua applicazione a un cluster Kubernetes, immetti il seguente comando:

```
bx dev deploy --target <container>
```
{: codeblock}

### Visualizza la tua applicazione in esecuzione
Una volta distribuita l'applicazione, vedrai un URL simile a `abc-devhost.mybluemix.net` nella pipeline DevOps o nel terminale (se stai utilizzando la riga di comando). Visita questo URL nel tuo browser.
