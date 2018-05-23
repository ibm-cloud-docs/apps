---

copyright:
  years: 2017, 2018
lastupdated: "2018-05-02"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Esercitazione introduttiva
{: #create}

In {{site.data.keyword.Bluemix}}, puoi creare applicazioni mobili e web a livello aziendale e sfruttare le estensioni cloud ospitate da {{site.data.keyword.Bluemix_notm}}. Puoi utilizzare la console {{site.data.keyword.Bluemix}} e gli strumenti della riga di comando per creare, eseguire e distribuire le tue applicazioni. Puoi iniziare in uno dei seguenti due modi: creare un'applicazione con un kit starter che gestisce il processo per te o, se sai quello che vuoi, creare la tua applicazione con le risorse necessarie.
{:shortdesc}

Puoi utilizzare un kit starter per iniziare ad utilizzare rapidamente la tua applicazione e a prepararla per lo sviluppo futuro. Scegli un kit starter e un linguaggio di programmazione, crea un'applicazione e configura quindi una toolchain DevOps per distribuire automaticamente la tua applicazione. Puoi anche scaricare il codice per l'ispezione immediata.

I kit starter sono disponibili in molte categorie, tra cui:

* [Watson](https://console.bluemix.net/developer/watson){:new_window}
* [Apple](https://console.bluemix.net/developer/appledevelopment){:new_window}
* [Mobile](https://console.bluemix.net/developer/mobile){:new_window}
* [Applicazione web](https://console.bluemix.net/developer/appservice){:new_window}
* [Sicurezza](https://console.bluemix.net/developer/security){:new_window}
<!--* [Watson Data Platform developer console](https://console.bluemix.net/developer/dataplatform)-->
* [Elemento finanziario](https://console.bluemix.net/developer/finance){:new_window}

## Prima di iniziare

[Registrati](https://console.bluemix.net){: new_window} per un account {{site.data.keyword.cloud_notm}}. Inserisci le informazioni relative a e-mail, nome, azienda, regione e numero di telefono.

Non ti serve una carta di credito per registrare un account gratuito, ma inserirla ti fornisce l'accesso a più risorse e ti rende più semplice sapere tutto quello che {{site.data.keyword.cloud_notm}} ha da offrire.

## Passo 1: Crea un'applicazione
{: #project}

1. Fai clic sull'icona **Menu** ![Icona menu](../icons/icon_hamburger.svg) > **Applicazioni Web**.

2. Fai clic su **Inizia subito** nella sezione **Inizia dal web**.

3. Seleziona un kit starter di tua scelta, leggi i dettagli e fai clic su **Crea**.

  Per visualizzare ciò che è incluso nel kit starter, espandi il tile nel dashboard dei kit starter del servizio dell'applicazione.
  {: tip}

4. Fornisci un nome alla tua applicazione, seleziona il tuo linguaggio e fai clic su **Crea**.

Ottimo inizio! Hai appena creato un'applicazione.

Per esaminare il tuo codice, fai clic su **Scarica codice** nella pagina dei dettagli dell'applicazione. Controlla il file `README.md` nel file compresso scaricato per scoprire se devi effettuare ulteriori azioni per avere la tua applicazione starter in esecuzione.
{: tip}

## Passo 2: Aggiungi risorse
{: #addResources}

La maggior parte dei kit starter indicano a {{site.data.keyword.cloud_notm}} di eseguire automaticamente il provisioning delle risorse al tuo posto. Puoi anche associare ulteriori risorse alla tua applicazione facendo clic su **Aggiungi risorsa** nella pagina dei dettagli dell'applicazione.

Per sviluppare ed eseguire la tua applicazione localmente, utilizza la [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html)
{: tip}

## Passo 3: Distribuisci a {{site.data.keyword.cloud_notm}}
{: #deploy}

Fai clic su **Distribuisci a Cloud** nella pagina dei dettagli dell'applicazione, seleziona un metodo di distribuzione (ad esempio cluster Kubernetes o applicazione Cloud Foundry) e fai clic su **Crea**. {{site.data.keyword.cloud_notm}} crea automaticamente una toolchain aperta che dispone di un repository Git e della pipeline di fornitura continua. Visualizza il componente pipeline della tua nuova toolchain per iniziare a creare e distribuire il processo in modo che puoi visualizzare la tua nuova applicazione in esecuzione in pochi minuti.

Ora sei pronto per lo sviluppo iterativo e la distribuzione continua.
