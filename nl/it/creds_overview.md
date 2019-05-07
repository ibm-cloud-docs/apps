---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-25"

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

# Aggiunta di credenziali del servizio al tuo ambiente di distribuzione
{: #credentials_overview}

Acquisisci informazioni su come aggiungere manualmente delle credenziali di servizio al tuo ambiente di distribuzione.
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

In generale, vuoi che la tua logica dell'applicazione acquisisca le credenziali di servizio sensibili, quali le password o le chiavi API del database, dall'ambiente in cui la tua applicazione viene eseguita. In questo modo, non conservi le credenziali nel tuo repository del codice sorgente. I database nei tuoi ambienti di integrazione, pre-produzione e produzione continue sono isolati l'uno dall'altro.

Se crei un'applicazione utilizzando un modello di kit starter, l'ambiente viene preparato per tuo conto automaticamente. Non importa se la tua destinazione di distribuzione è:
<!-- Add links to the new topics in the /docs/resources repo when available-->
  * Kubernetes
  * Cloud Foundry pubblico o Cloud Foundry Enterprise Environment 
  * VSI (Virtual Server Instance) (anche docker locale) 
  
Viene fornita la procedura per come configurare l'ambiente. I kit starter generano del codice che utilizza una libreria dipendente per rendere il codice portatile per l'esecuzione su qualsiasi destinazione della distribuzione. Infine, non viene utilizzata alcuna logica di ramo per rilevare in quale destinazione di distribuzione è in esecuzione l'applicazione.

L'amministratore o l'ingegnere DevOps è poi responsabile della preparazione degli ambienti con i controlli di accesso e le configurazioni corretti per rendere disponibili per la tua applicazione i valori da essa richiesti.

"Configure continuous delivery" è un passo una tantum che esegue le seguenti attività chiave:
 * Prepara la tua destinazione di distribuzione con servizi, risorse e credenziali.
 * Crea una toolchain DevOps per creare e distribuire la tua applicazione in tale ambiente, utilizzando il codice che fa correttamente riferimento alle credenziali nell'ambiente.

Devi tuttavia preparare la tua destinazione di distribuzione in uno qualsiasi dei seguenti scenari:
 * Porti il tuo codice personale.
 * Inizi da un template di kit starter vuoto.
 * Aggiungi un servizio a un'applicazione basata sul kit starter dopo che ne è stata eseguita la distribuzione.

La preparazione dell'ambiente viene sempre eseguita per tutte le credenziali per tutti i servizi associati a un'applicazione e tutti i servizi (`services`) sono elencati nel file `manifest.yml`, ma non tutti i riferimenti di credenziali vengono inseriti nel file `mappings.json`. In questi casi, devi inserire tali riferimenti personalmente. Dopo che hai deciso in merito alla destinazione di distribuzione e non hai bisogno dell'astrazione della libreria `IBMCloudEnv`, consulta la sezione "Il tuo codice + (destinazione di distribuzione)" adatta alla tua decisione.
{: important}

Alcuni kit starter non includono per niente il riferimento alla dipendenza `IBMCloudEnv` e ai file `manifest.yml` o `mappings.json`.
{: important}
