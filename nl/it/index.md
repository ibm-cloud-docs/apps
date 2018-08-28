---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-21"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Esercitazione introduttiva
{: #create}

In {{site.data.keyword.Bluemix}}, puoi creare applicazioni mobili e web a livello aziendale e sfruttare le estensioni cloud ospitate da {{site.data.keyword.Bluemix_notm}}. Puoi utilizzare la console {{site.data.keyword.Bluemix}} e gli strumenti della riga di comando per creare, eseguire e distribuire le tue applicazioni. Inizia a lavorare in due modi: creare un'applicazione con un kit starter che gestisca il processo per te oppure, se sai cosa vuoi, creare la tua applicazione con le risorse di cui hai bisogno.
{:shortdesc}

Puoi utilizzare un kit starter per iniziare ad utilizzare rapidamente la tua applicazione e a prepararla per lo sviluppo futuro. Scegli un kit starter e un linguaggio di programmazione, crea un'applicazione e configura quindi una toolchain DevOps per distribuire automaticamente la tua applicazione. Puoi anche scaricare il codice per l'ispezione immediata.

I kit starter sono disponibili in molte categorie, tra cui:

* [Watson ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/developer/watson/dashboard){:new_window}
* [Apple ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/developer/appledevelopment/dashboard){:new_window}
* [Mobile ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/developer/mobile/dashboard){:new_window}
* [Web App ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/developer/appservice/dashboard){:new_window}
* [Security ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/developer/security/dashboard){:new_window}
<!--* [Watson Data Platform developer console](https://console.bluemix.net/developer/dataplatform)-->
* [Finance ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/developer/finance/dashboard){:new_window}

## Prima di iniziare

[Registrati ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net){: new_window} per un account {{site.data.keyword.cloud_notm}}. Inserisci le informazioni relative a e-mail, nome, azienda, regione e numero di telefono.

Non ti serve una carta di credito per registrare un account gratuito. Inserirla però ti dà accesso a più risorse e ti rende più facile ottenere tutte le offerte di {{site.data.keyword.cloud_notm}}.

## Passo 1. Crea un'applicazione
{: #project}

1. Fai clic sull'icona **Menu** ![Icona menu](../icons/icon_hamburger.svg) > **Applicazioni Web**.

2. Fai clic su **Inizia subito** nella sezione **Inizia dal web**.

3. Seleziona un kit starter di tua scelta, leggi i dettagli e fai clic su **Crea**.

   Per visualizzare ciò che è incluso nel kit starter, espandi il tile nel dashboard dei kit starter del servizio dell'applicazione.
   {: tip}

4. Fornisci un nome alla tua applicazione, seleziona il tuo linguaggio e fai clic su **Crea**.

   Ottimo inizio! Hai appena creato un'applicazione.

   Per esaminare il tuo codice, fai clic su **Scarica codice** nella pagina dei dettagli dell'applicazione. Controlla il file `README.md` nel file compresso scaricato per scoprire se devi effettuare ulteriori azioni per rendere operativa la tua applicazione starter.
   {: tip}

## Passo 2. Aggiungi risorse
{: #addResources}

La maggior parte dei kit starter indicano a {{site.data.keyword.cloud_notm}} di eseguire automaticamente il provisioning delle risorse al tuo posto. Puoi anche associare ulteriori risorse alla tua applicazione facendo clic su **Aggiungi risorsa** nella pagina dei dettagli dell'applicazione.

Per sviluppare ed eseguire la tua applicazione localmente, utilizza la [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html)
{: tip}

## Passo 3. Distribuisci la tua applicazione
{: #deploy}

Fai clic su **Distribuisci a Cloud** nella pagina dei dettagli dell'applicazione, seleziona un metodo di distribuzione, ad esempio cluster Kubernetes o applicazione Cloud Foundry, e fai clic su **Crea**. {{site.data.keyword.cloud_notm}} crea automaticamente una toolchain aperta completa di un repository Git e della pipeline di fornitura continua. Visualizza il componente pipeline della tua nuova toolchain per iniziare a creare e distribuire il processo in modo che puoi visualizzare la tua nuova applicazione in pochi minuti.

Ora sei pronto per lo sviluppo iterativo e la distribuzione continua.
