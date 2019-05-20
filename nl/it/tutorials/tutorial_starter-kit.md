---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-10"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{: note .note}

# Creazione di un'applicazione con il kit starter
{: #tutorial-starterkit}

Puoi utilizzare un kit starter per avviare rapidamente la tua applicazione e prepararla per lo sviluppo futuro. Seleziona un kit starter e un linguaggio di programmazione, crea un'applicazione e configura quindi una toolchain DevOps per distribuire automaticamente la tua applicazione. Puoi anche scaricare il codice per l'ispezione immediata.
{: shortdesc}

Puoi creare un'applicazione da una selezione di kit starter, compreso uno vuoto se vuoi personalizzare tu stesso le opzioni di build. In entrambi i casi, una toolchain DevOps viene creata automaticamente per la distribuzione della tua applicazione. Puoi anche scaricare il codice per l'ispezione immediata.

{{site.data.keyword.cloud_notm}} ha portali per gli sviluppatori in diverse aree di interesse (come Watson, Security o Finance) o un canale digitale (come Mobile o Applicazioni Web). Puoi accedere a questi portali dall'icona **Menu** ![Icona Menu](../../icons/icon_hamburger.svg).

Ogni portale sviluppatori fornisce i kit starter rilevanti per l'area specifica del portale. I portali offrono flussi di lavoro coerenti e intuitivi per la creazione di un'applicazione funzionante pronta per la produzione in pochi minuti.

I kit starter sono disponibili in molte categorie, tra cui:
* [Watson ](https://{DomainName}/developer/watson/dashboard){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")
* [Apple ](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")
* [Mobile ](https://{DomainName}/developer/mobile/dashboard){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")
* [Web App ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")
* [Security ](https://{DomainName}/developer/security/dashboard){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")
* [Finance ](https://{DomainName}/developer/finance/dashboard){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")

Vedi [Cosa sono i kit starter?](/docs/apps?topic=creating-apps-starter-kits) per ulteriori informazioni.

## Passo 1. Installa gli strumenti
{: #prereqs-starterkit}

* Installa gli [strumenti sviluppatore](/docs/cli?topic=cloud-cli-ibmcloud-cli).
* Docker viene installato come parte degli strumenti per sviluppatori. Affinché i comandi di build funzionino è necessario che Docker sia in esecuzione. Devi creare un account Docker, eseguire l'applicazione Docker ed effettuare l'accesso.
* Se intendi distribuire la tua applicazione a {{site.data.keyword.cfee_full}}, devi [preparare il tuo account {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Passo 2. Crea un'applicazione
{: #create-starterkit}

I kit starter sono disponibili in molti linguaggi e framework in {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}. Puoi utilizzare i filtri di categoria, ad esempio linguaggio e tipo, per restringere la selezione.

1. Dalla pagina dei [kit starter](https://{DomainName}/developer/appservice/starter-kits/){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno") nella console {{site.data.keyword.dev_console}}, seleziona un kit starter e fai clic su **Create app**. 

    Per visualizzare ciò che è incluso nel kit starter, seleziona il tile e leggi i dettagli. Se vuoi utilizzare un kit starter vuoto e personalizzarlo, seleziona il tile **Create App**.
    {: tip}

2. Denomina la tua applicazione e seleziona un gruppo di risorse.

3. Facoltativo. Fornisci le tag per classificare la tua applicazione. Per ulteriori informazioni, consulta [Gestione delle tag](/docs/resources?topic=resources-tag).

4. Seleziona il linguaggio e il framework. Alcuni kit starter potrebbero essere disponibili solo in un linguaggio.

5. Fai clic su **Create**.

Ottimo inizio! Hai appena creato un'applicazione!

Per esaminare il tuo codice prima di aggiungere dei servizi o configurare la fornitura continua, fai clic su **Download code** nella pagina App details. Controlla il file `README.md` nel file compresso scaricato per scoprire se devi effettuare ulteriori azioni per rendere operativa la tua applicazione.
{: tip}

## Passo 3. Aggiungi servizi (facoltativo)
{: #resources-starterkit}

Se un kit starter richiede servizi specifici, sono disponibili dei servizi di cui viene eseguito il provisioning in automatico in modo che le istanze per tali servizi siano automaticamente create quando crei un'applicazione.

Puoi anche aggiungere servizi che migliorano la tua applicazione con la potenza cognitiva di Watson, aggiungere servizi mobili o servizi per la sicurezza. Per questa esercitazione, aggiungi una posizione per gestire i tuoi dati.

1. Sulla pagina App details, fai clic su **Create service** o **Connect existing services**, a seconda se hai già dei servizi che vuoi connettere a questa applicazione.
2. Seleziona il tipo di servizio che desideri e segui le istruzioni per aggiungere un servizio esistente alla tua applicazione o creare un'istanza del servizio.

Dopo aver aggiunto tutti i servizi desiderati, vengono visualizzati nella pagina App details.

## Passo 4. Seleziona una destinazione di distribuzione e configura la fornitura continua
{: #target-starterkit}

Quando selezioni una destinazione di distribuzione, una toolchain DevOps viene creata automaticamente per la tua applicazione. La toolchain include una pipeline di fornitura che indica lo stato di distribuzione della tua applicazione. La nuova applicazione generata viene trasmessa a un repository GitLab che fa parte della toolchain.

L'abilitazione di una toolchain DevOps crea un ambiente di sviluppo basato sul team per la tua applicazione. Quando crei una toolchain, il servizio dell'applicazione crea un repository Git, in cui puoi visualizzare il codice sorgente, clonare la tua applicazione e creare e gestire i problemi. Hai anche accesso a un ambiente di GitLab dedicato e a una pipeline di fornitura continua. Sono personalizzati per la destinazione di distribuzione che selezioni, sia che si tratti di [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) o [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Tutte le toolchain che vengono create da un dashboard dello sviluppatore {{site.data.keyword.cloud_notm}} sono configurate per la distribuzione automatica.
{: note}

Per selezionare la tua destinazione di distribuzione e per configurare la fornitura continua, completa questa procedura:

1. Nella pagina App details, fai clic su **Configure continuous delivery**.
2. Seleziona un destinazione per la distribuzione. Configura la tua destinazione di distribuzione in base alle istruzioni per la destinazione che selezioni:
  * **Deploy to [IBM Kubernetes Service](/docs/containers?topic=containers-app)**. Questa opzione crea un cluster di host, denominati nodi di lavoro, per distribuire e gestire contenitori delle applicazioni ad elevata disponibilità. Puoi creare un cluster o distribuire un cluster esistente.
  * **Deploy to Cloud Foundry**. Questa opzione distribuisce la tua applicazione nativa del cloud senza che tu debba gestire l'infrastruttura sottostante. Se il tuo account ha accesso a {{site.data.keyword.cfee_full_notm}}, puoi selezionare un tipo di deployer **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** o **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**, che puoi utilizzare per creare e gestire ambienti isolati per ospitare applicazioni Cloud Foundry esclusivamente per la tua azienda.
  * **Deploy to a Virtual Server**. Questa opzione esegue il provisioning di un'istanza del server virtuale, carica un'immagine che include la tua applicazione, crea una toolchain DevOps e avvia il primo ciclo di distribuzione per tuo conto.

Dopo aver selezionato e configurato la destinazione di distribuzione, la pagina App details indica che la fornitura continua è stata configurata. Puoi visualizzare il repository che contiene il codice di origine per la tua applicazione facendo clic su **View repo**.

## Passo 5. Distribuisci la tua applicazione
{: #deploy-starterkit}

Le toolchain DevOps che vengono create dal dashboard dello sviluppatore {{site.data.keyword.cloud_notm}} sono configurate per la distribuzione automatica.
{: note}

Dopo che hai selezionato la tua destinazione di distribuzione, apri il componente pipeline della tua nuova toolchain per iniziare il processo iniziale di creazione e distribuzione in modo da poter vedere la tua nuova applicazione nel giro di qualche minuto.

1. Dalla pagina App details, fai clic su **View toolchain**.
2. Fai clic su **Delivery Pipeline** dove puoi iniziare le creazioni, gestire la distribuzione e visualizzare i log e la cronologia.

Con una toolchain correttamente configurata, un ciclo di creazione-distribuzione viene avviato automaticamente con tutte le unioni al ramo master nel tuo repository. Per ulteriori informazioni, vedi [Creazione e distribuzione](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

Puoi distribuire la tua applicazione dalla riga di comando eseguendo il comando [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy). Per ulteriori informazioni, vedi [Distribuzione di applicazioni con la CLI](/docs/apps?topic=creating-apps-deploying-apps#deploy-cli).

## Passo 6. Verifica che la tua applicazione sia in esecuzione
{: #verify-starterkit}

Dopo che hai distribuito la tua applicazione, la Delivery Pipeline o la riga di comando ti indirizzano all'URL per la tua applicazione.

1. Dalla tua toolchain DevOps, fai clic su **Delivery Pipeline** e seleziona quindi **Deploy Stage**.
2. Fai clic su **View logs and history**.
3. Nel file di log, trova l'URL dell'applicazione:

    Alla fine del file di log, cerca la parola `urls` o `view`. Ad esempio, nel file di log potresti vedere una riga simile a `urls: my-app-devhost.mybluemix.net` o `View the application health at: http://<ipaddress>:<port>/health`.

4. Vai all'URL nel tuo browser. Se l'applicazione è in esecuzione, viene visualizzato un messaggio che include `Congratulations` o `{"status":"UP"}`.

Se stai utilizzando la riga di comando, esegui il comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) per visualizzare l'URL della tua applicazione. Vai quindi all'URL nel tuo browser.
