---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creazione di un'applicazione con il kit starter
{: #tutorial-starterkit}

Puoi utilizzare un kit starter per iniziare ad utilizzare rapidamente la tua applicazione e a prepararla per lo sviluppo futuro. Scegli un kit starter e un linguaggio di programmazione, crea un'applicazione e configura quindi una toolchain DevOps per distribuire automaticamente la tua applicazione. Puoi anche scaricare il codice per l'ispezione immediata.
{: shortdesc}

Puoi creare un'applicazione da una selezione di kit starter, compreso uno vuoto se vuoi personalizzare tu stesso le opzioni di build. In entrambi i casi, una toolchain DevOps viene creata automaticamente per la distribuzione della tua applicazione. Puoi anche scaricare il codice per l'ispezione immediata.

I kit starter sono disponibili in molte categorie, tra cui:
* [Watson ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/developer/watson/dashboard){:new_window}
* [Apple ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/developer/appledevelopment/dashboard){:new_window}
* [Mobile ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/developer/mobile/dashboard){:new_window}
* [Web App ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/developer/appservice/dashboard){:new_window}
* [Security ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/developer/security/dashboard){:new_window}
* [Finance ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/developer/finance/dashboard){:new_window}

## Passo 1. Crea un'applicazione
{: #create-starterkit}

1. Dal [dashboard {{site.data.keyword.cloud}}](https://{DomainName}), fai clic sull'icona **Menu** ![Icona Menu](../../icons/icon_hamburger.svg) > **Applicazioni Web**.

2. Fai clic su **Get Started** nella sezione **Start from the Web**.

3. Seleziona un kit starter di tua scelta, leggi i dettagli e fai clic su **Create**.
    
    Per visualizzare ciò che è incluso nel kit starter, espandi il tile nel dashboard [App Service Starter Kits ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/developer/appservice/starter-kits){:new_window}. L'opzione di kit starter "Crea app" può essere utilizzata come un'applicazione starter vuota e personalizzata ulteriormente in modo da soddisfare le tue esigenze.
    {: tip}

4. Denomina la tua applicazione, seleziona un gruppo di risorse, fornisci (facoltativamente) delle tag, seleziona il tuo linguaggio e fai clic su **Create**.
    
    Ottimo inizio! Hai appena creato un'applicazione.

Per esaminare il tuo codice, fai clic su **Download Code** nella pagina dei dettagli dell'applicazione. Controlla il file `README.md` nel file compresso scaricato per scoprire se devi effettuare ulteriori azioni per rendere operativa la tua applicazione starter.
{: tip}

Per ulteriori informazioni, vedi i seguenti argomenti:
 * [Creazione di un'applicazione web di base con un kit starter](/docs/apps/tutorials/tutorial_web.html#tutorial-webapp)
 * [Gestione delle tag](/docs/resources/tagging_resources.html#tag)

## Passo 2. Aggiunta di risorse
{: #resources-starterkit}

Puoi aggiungere risorse che migliorano la tua applicazione con la potenza cognitiva di Watson, aggiungere servizi mobili o servizi per la sicurezza. Per questa esercitazione, aggiungi una posizione per gestire i tuoi dati.

1. Dalla finestra App Service, fai clic su **Add Resource**.
2. Seleziona il tipo di servizio che desideri. Ad esempio, seleziona **Data** > **Next** > **Cloudant** > **Next**.
3. Seleziona il tuo piano prezzi. È disponibile un'opzione gratuita che puoi utilizzare per questa esercitazione.
4. Fai clic su **Create**.

## Passo 3. Distribuisci a {{site.data.keyword.cloud_notm}}
{: #deploy-starterkit}

Fai clic su **Deploy to Cloud** nella pagina App details, seleziona un ambiente di distribuzione e fai clic su **Create**. {{site.data.keyword.cloud_notm}} crea automaticamente una toolchain aperta completa di un repository Git e della pipeline di fornitura continua.

L'abilitazione di una toolchain crea un ambiente di sviluppo basato sul team per la tua applicazione. Quando crei una toolchain, il servizio dell'applicazione crea un repository Git, in cui puoi visualizzare il codice sorgente, clonare la tua applicazione e creare e gestire i problemi. Hai anche accesso a un ambiente di laboratorio Git dedicato e a una pipeline di fornitura continua. Sono personalizzati per l'ambiente di distribuzione che scegli, sia che si tratti di [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) o [Virtual Server (VSI)](/docs/vsi/vsi_index.html).

Dopo che hai selezionato il tuo ambiente di distribuzione, apri il componente pipeline della tua nuova toolchain per iniziare il processo iniziale di creazione e distribuzione in modo da poter vedere la tua nuova applicazione nel giro di qualche minuto.

Tutte le toolchain che vengono create da un dashboard dello sviluppatore {{site.data.keyword.cloud_notm}} sono configurate per la distribuzione automatica.
{: note}

Per distribuire la tua applicazione con la riga di comando, utilizza `ibmcloud dev deploy`. Per ulteriori informazioni, vedi [Creazione e distribuzione delle applicazioni utilizzando la CLI](/docs/apps/create-deploy-cli.html#create-deploy-app-cli).
