---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-10"

keywords: apps, credentials, service, add service credentials, environment, deployment

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# Aggiunta manuale di credenziali del servizio al tuo ambiente di distribuzione
{: #credentials_overview}

Vuoi che la tua logica dell'applicazione acquisisca le credenziali di servizio sensibili, quali le password o le chiavi API del database, dall'ambiente in cui la tua applicazione viene eseguita. In questo modo, non devi conservare le credenziali nel tuo repository del codice sorgente.
{: shortdesc}

Se crei un'applicazione utilizzando un kit starter, l'ambiente viene preparato per tuo conto automaticamente. Quando connetti un servizio al tuo kit starter prima di distribuire la tua applicazione, le credenziali del servizio vengono automaticamente aggiunte al tuo ambiente.
{ :tip}

Devi aggiungere manualmente le credenziali del servizio al tuo ambiente di distribuzione nei seguenti scenari:

 * Porti il tuo codice personale.
 * Aggiungi un servizio a un'applicazione basata sul kit starter dopo che ne è stata eseguita la distribuzione.

Il processo per l'aggiunta delle credenziali del servizio dipende dalla destinazione di distribuzione e dal tuo linguaggio di programmazione. Per ulteriori informazioni sulla configurazione delle credenziali del servizio per la tua destinazione di distribuzione, vedi la documentazione specifica per il tuo ambiente host:

  * [{{site.data.keyword.containershort}}](/docs/containers?topic=containers-service-binding#adding_app)
  * Cloud Foundry Public o {{site.data.keyword.cfee_full}}
  * VSI (Virtual server instance) (contenitore Docker locale)

Molti linguaggi e framework forniscono delle librerie standard per le configurazioni specifiche per l'ambiente e l'applicazione. Per ulteriori informazioni, vedi le seguenti guide di programmazione:

* [Java: Gestione delle credenziali del servizio](/docs/java?topic=cloud-native-configuration)
* [Configurazione dell'ambiente Node.js](/docs/node?topic=nodejs-configure-nodejs)
* [Configurazione dell'ambiente Spring](/docs/java?topic=java-spring-configuration)
* [Configurazione dell'ambiente Swift](/docs/swift?topic=swift-configuration)
* [Configurazione dell'ambiente Go](/docs/go?topic=go-configure-go-env)
