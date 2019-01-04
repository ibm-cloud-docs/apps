---

copyright:
  years: 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Panoramica delle credenziali
{: #credentials_overview}

Acquisisci informazioni su come aggiungere manualmente delle credenziali di servizio al tuo ambiente di distribuzione.
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

In generale, vuoi che la tua logica dell'applicazione acquisisca le credenziali di servizio sensibili, quali le password o le chiavi API del database, dall'ambiente in cui la tua applicazione viene eseguita. In questo modo, non conservi le credenziali nel tuo repository del codice sorgente. I database nei tuoi ambienti di integrazione, pre-produzione e produzione continue sono isolati l'uno dall'altro.

Se crei un'applicazione utilizzando un modello di kit starter, l'ambiente viene preparato per tuo conto automaticamente. Non importa se la tua destinazione di distribuzione è:
  * [Kubernetes](/docs/apps/creds_kube.html)
  * [Cloud Foundry](/docs/apps/creds_cf.html)
  * [VSI (Virtual Server Instance) (anche docker locale)](/docs/apps/creds_vsi.html)
  
Viene fornita la procedura per come configurare l'ambiente. I kit starter generano del codice che utilizza una libreria dipendente per rendere il codice portatile per l'esecuzione su qualsiasi destinazione della distribuzione. Infine, non viene utilizzata alcuna logica di ramo per rilevare in quale destinazione di distribuzione è in esecuzione l'applicazione.

L'amministratore o l'ingegnere DevOps è poi responsabile della preparazione degli ambienti con i controlli di accesso e le configurazioni corretti per rendere disponibili per la tua applicazione i valori da essa richiesti.

"Deploy to cloud" è un passo una tantum che esegue le seguenti attività chiave:
 * Prepara il tuo ambiente di distribuzione di destinazione con servizi, risorse e credenziali.
 * Crea una toolchain DevOps per creare e distribuire la tua applicazione in tale ambiente, utilizzando il codice che fa correttamente riferimento alle credenziali nell'ambiente.

Devi tuttavia preparare l'ambiente di distribuzione di destinazione in uno qualsiasi dei seguenti scenari:
 * Porti il tuo codice personale.
 * Inizi da un modello di kit starter vuoto.
 * Aggiungi un servizio a un'applicazione basata sul kit starter _dopo_ che ne è stata eseguita la distribuzione.




