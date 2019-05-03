---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, mobile, mobile application, starter kit, developer tools, DevOps toolchain, toolchain, create mobile app, mobile starter kit

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Creazione di un'applicazione mobile con un kit starter
{: #tutorial-mobile}

{{site.data.keyword.cloud}} offre kit starter mobili per aiutarti a creare rapidamente un'applicazione mobile. Seleziona un linguaggio, un framework e gli strumenti dai kit starter App Service per iniziare a lavorare con un'applicazione personalizzata preconfigurata. In questa esercitazione, imparerai a installare gli strumenti di cui hai bisogno, creare ed eseguire l'applicazione localmente e distribuirla sul cloud.
{: shortdesc}

## Passo 1. Prima di iniziare
{: #prereqs-mobile}

* Installa [{{site.data.keyword.dev_cli_short}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).
* Docker viene installato come parte degli strumenti per sviluppatori. Affinché i comandi di build funzionino è necessario che Docker sia in esecuzione. Devi creare un account Docker, eseguire l'applicazione Docker ed effettuare l'accesso.
* Se intendi distribuire la tua applicazione a [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), devi [preparare il tuo account {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Passo 2. Crea un'applicazione utilizzando {{site.data.keyword.dev_console}}
{: #create-mobile}

1. Crea un'applicazione {{site.data.keyword.dev_console}} in {{site.data.keyword.cloud_notm}}.
2. Dalla pagina dei [kit stater ](https://{DomainName}/developer/appservice/starter-kits/){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno") in {{site.data.keyword.dev_console}}, seleziona un kit starter in base alle funzioni che desideri. Ad esempio, per un'applicazione di linguaggio Watson, seleziona **Swift Kitura**.
3. Immetti il nome della tua applicazione. Per questa esercitazione, utilizza `WatsonApp`.
4. Facoltativo. Fornisci le tag per classificare la tua applicazione. Per ulteriori informazioni, consulta [Gestione delle tag](/docs/resources?topic=resources-tag).
5. Seleziona la tua piattaforma di linguaggio. Per questa esercitazione, utilizza `Swift`.
6. Seleziona il linguaggio e il framework. Alcuni kit starter potrebbero essere disponibili solo in un linguaggio.
7. Seleziona il tuo piano prezzi. È disponibile un'opzione gratuita che puoi utilizzare per questa esercitazione.
8. Fai clic su **Crea**.

## Passo 3. Aggiungi servizi (facoltativo)
{: #resources-mobile}

Puoi aggiungere servizi che migliorano la tua applicazione con la potenza cognitiva di Watson, aggiungere servizi mobili o servizi per la sicurezza. Per questa esercitazione, aggiungi una posizione per gestire i tuoi dati.

1. Nella pagina **App details**, fai clic su **Add service**.
2. Seleziona il tipo di servizio che desideri. Ad esempio, seleziona **Data** > **Next** > **Cloudant** > **Next**.
3. Seleziona il tuo piano prezzi. È disponibile un'opzione gratuita che puoi utilizzare per questa esercitazione.
4. Fai clic su **Crea**.

## Passo 4. Crea una toolchain DevOps
{: #toolchain-mobile}

L'abilitazione di una toolchain crea un ambiente di sviluppo basato sul team per la tua applicazione. Quando crei una toolchain, il servizio dell'applicazione crea un repository Git, in cui puoi visualizzare il codice sorgente, clonare la tua applicazione e creare e gestire i problemi. Hai anche accesso a un ambiente di laboratorio Git dedicato e a una pipeline di fornitura continua. Sono personalizzati per la destinazione di distribuzione che scegli, sia che si tratti di [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html) o [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers).

Tutte le toolchain che vengono create da un dashboard dello sviluppatore {{site.data.keyword.cloud_notm}} sono configurate per la distribuzione automatica.
{: note}

1. Nella pagina **App details**, fai clic su **Configure continous delivery**.
2. Seleziona un destinazione per la distribuzione. Configura la tua destinazione di distribuzione in base alle istruzioni per la destinazione che selezioni:
  * **Deploy to [IBM Kubernetes Service](/docs/apps/deploying?topic=creating-apps-containers-kube)**. Questa opzione crea un cluster di host, denominati nodi di lavoro, per distribuire e gestire contenitori delle applicazioni ad elevata disponibilità. Puoi creare un cluster o distribuire un cluster esistente.
  * **Deploy to Cloud Foundry**. Questa opzione distribuisce la tua applicazione nativa del cloud senza che tu debba gestire l'infrastruttura sottostante. Se il tuo account ha accesso a {{site.data.keyword.cfee_full_notm}}, puoi selezionare un tipo di deployer **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)** o **[Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**, che puoi utilizzare per creare e gestire ambienti isolati per ospitare applicazioni Cloud Foundry esclusivamente per la tua azienda.
  * **Deploy to a [Virtual Server](/docs/apps?topic=creating-apps-vsi-deploy)**. Questa opzione esegue il provisioning di un'istanza del server virtuale, carica un'immagine che include la tua applicazione, crea una toolchain DevOps e avvia il primo ciclo di distribuzione per tuo conto.

## Passo 5. Crea ed esegui l'applicazione localmente
{: #build-run-mobile}

La distribuzione della tua applicazione sul cloud nell'ultimo passo ha creato una toolchain. Una toolchain crea un repository Git per la tua applicazione in cui puoi trovare il codice. Segui questa procedura per accedere al tuo repository. Puoi creare localmente l'applicazione per il test prima di inviarla al cloud.

1. Nella pagina **App details**, fai clic su **Download code** o **Clone your repo** per utilizzare il tuo codice localmente.
2. Importa l'applicazione nel tuo ambiente di sviluppo integrato.
3. Modifica il codice.
4. Imposta l'[autenticazione Git](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) aggiungendo un token di accesso personale.
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

### Esecuzione della tua applicazione Swift in Xcode
{: #run_swift}

1. Apri il file `README.md` in un visualizzatore markdown per esaminare la procedura per configurare la tua applicazione.
2. Apri il tuo terminale e passa alla tua cartella dell'applicazione ed esegui i seguenti comandi:
    1. Esegui `pod setup` se hai bisogno di configurare il repository CocoaPods.
    2. Esegui `pod update` se hai bisogno di aggiornare i tuoi pod esistenti.
    3. Esegui `pod install` per installare i pod per la tua applicazione.
3. Apri il tuo progetto Xcode `<appname>.xcworkspace`.
4. Esegui la tua applicazione.

### Esecuzione della tua applicazione Cordova in Xcode
{: #run_cordova_xcode}

Se hai scelto di utilizzare Cordova come il tuo linguaggio di implementazione, segui queste istruzioni.

1. Apri il file `README.md` in un visualizzatore Markdown per configurare la tua applicazione.
2. Apri la tua applicazione `platforms/ios` in Xcode.
3. Esegui la tua applicazione.

### Esecuzione della tua applicazione Cordova in Android Studio
{: #run_cordova_studio}

Utilizza questa sezione se scegli di utilizzare Cordova come piattaforma della tua applicazione mobile.

1. Estrai il file `BasicProject-Cordova.zip`.
2. Apri il file `README.md` in un visualizzatore Markdown per configurare la tua applicazione.
3. Apri la tua applicazione `platforms/android` in Android Studio.
4. Esegui la tua applicazione.

### Esecuzione della tua applicazione Android in Android Studio
{: #run_android}

Utilizza questa sezione se scegli di utilizzare Android come piattaforma della tua applicazione mobile.

1. Apri il file `README.md` in un visualizzatore Markdown per configurare la tua applicazione.
2. Apri la tua applicazione `BasicProject-Android` in Android Studio.
3. Esegui la tua applicazione.

## Passo 6. Distribuisci la tua applicazione
{: #deploy-mobile}

### Distribuisci utilizzando una toolchain
{: #deploy-mobile-toolchain}

Puoi distribuire la tua applicazione a {{site.data.keyword.cloud_notm}} in diversi modi, ma una toolchain DevOps è il modo migliore per distribuire le applicazioni di produzione. Con una toolchain DevOps, puoi facilmente automatizzare le distribuzioni in molti ambienti e aggiungere rapidamente servizi di monitoraggio, registrazione e avvisi per aiutare a gestire la tua applicazione man mano che cresce.

Con una toolchain correttamente configurata, un ciclo di creazione-distribuzione viene avviato automaticamente con tutte le unioni al ramo master nel tuo repository. Tutte le toolchain che vengono create da un dashboard dello sviluppatore {{site.data.keyword.cloud_notm}} sono configurate per la distribuzione automatica.

Puoi anche distribuire manualmente la tua applicazione dalla tua toolchain DevOps:

1. Nella pagina **App details**, fai clic su **View toolchain**.

2. Fai clic su **Delivery Pipeline** dove puoi iniziare le creazioni, gestire la distribuzione e visualizzare i log e la cronologia.

### Distribuisci utilizzando {{site.data.keyword.dev_cli_short}}
{: #deploy-mobile-cli}

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
{: #verify-mobile}

Dopo che hai distribuito la tua applicazione, la Delivery Pipeline o la riga di comando ti indirizzano all'URL per la tua applicazione.

1. Dalla tua toolchain DevOps, fai clic su **Delivery Pipeline** e seleziona quindi **Deploy Stage**.
2. Fai clic su **View logs and history**.
3. Nel file di log, trova l'URL dell'applicazione:

    Alla fine del file di log, cerca la parola `urls` o `view`. Ad esempio, nel file di log potresti vedere una riga simile a `urls: my-app-devhost.mybluemix.net` o `View the application health at: http://<ipaddress>:<port>/health`.

4. Vai all'URL nel tuo browser. Se l'applicazione è in esecuzione, viene visualizzato un messaggio che include `Congratulations` o `{"status":"UP"}`.

Se stai utilizzando la riga di comando, esegui il comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) per visualizzare l'URL della tua applicazione. Vai quindi all'URL nel tuo browser.
