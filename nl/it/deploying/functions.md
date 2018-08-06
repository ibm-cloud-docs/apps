---

copyright:
  years: 2018
lastupdated: "2018-07-25"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Sviluppo di applicazioni senza server
{: #serverless}

Per lo sviluppo senza server, puoi utilizzare l'offerta FaaS (Functions as a Service) di IBM, {{site.data.keyword.openwhisk}}. Puoi eseguire la logica dell'applicazione con {{site.data.keyword.openwhisk_short}} in risposta a eventi o chiamate dirette provenienti da applicazioni web o mobili su HTTP senza provisioning o gestione dei server. {{site.data.keyword.openwhisk_short}} effettua la gestione del sistema come il ridimensionamento automatico, la gestione della disponibilità e la manutenzione in modo che tu, come sviluppatore, possa concentrarti sulla scrittura della logica dell'applicazione.
{:shortdesc}

Per sviluppare le tue applicazioni, puoi utilizzare l'interfaccia utente (IU) o l'interfaccia riga di comando (CLI) di {{site.data.keyword.openwhisk_short}}. Entrambe hanno capacità simili per lo sviluppo di applicazioni. La CLI offre un maggiore controllo sulla distribuzione e sulle operazioni. Per informazioni più dettagliate su {{site.data.keyword.openwhisk_short}}, consulta la [documentazione](/docs/openwhisk/index.html) completa.

## Interfaccia utente di {{site.data.keyword.openwhisk_short}}
{: #ui}

Prova {{site.data.keyword.openwhisk_short}} nel tuo [browser ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.{DomainName}/openwhisk/actions){:new_window}. Vai alla pagina [Concetti ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.{DomainName}/openwhisk/learn){:new_window} per un'introduzione rapida dell'interfaccia utente {{site.data.keyword.openwhisk_short}}.

## Sviluppo con la CLI
{: #openwhisk_start_configure_cli}

Per ulteriori informazioni sull'installazione e sullo sviluppo con la CLI {{site.data.keyword.openwhisk_short}}, vedi [Configurazione della CLI {{site.data.keyword.openwhisk_short}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.{DomainName}/openwhisk/cli){:new_window}.

## Esposizione di API e dataset come azioni web
{: #containers}

Per impostazione predefinita, {{site.data.keyword.openwhisk_short}} definisce le azioni che richiedono una chiave di autenticazione. Negli ambienti mobili di produzione, è spesso necessario autorizzare i client mobili basati sui flussi OAuth ad esporre API e specifici dataset.

{{site.data.keyword.openwhisk_short}} consente agli sviluppatori di esporre le proprie funzioni come azioni web, che sono annotate, per creare rapidamente applicazioni basate sul web. Puoi programmare la logica di back-end con azioni annotate a cui l'applicazione web può accedere in modo anonimo, senza richiedere una chiave di autenticazione {{site.data.keyword.openwhisk_short}}.

Per esporre un'azione come azione web, vai alla scheda **Endpoint** della tua azione e seleziona **Abilita come azione web**.

Ora, gli utenti possono raggiungere l'azione da una richiesta browser o cURL, ad esempio:

```
curl https://openwhisk.ng.bluemix.net/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

**Output:**

```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} fornisce un [SDK mobile](/docs/openwhisk/openwhisk_mobile_sdk.html#mobile-sdk) per dispositivi iOS e watchOS che consente alle applicazioni mobili di inviare facilmente trigger remoti e richiamare azioni remote. Fornisce anche un [SDK serverless framework ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/openwhisk/openwhisk_goserverless.html){:new_window} che abilita le applicazioni senza server.
