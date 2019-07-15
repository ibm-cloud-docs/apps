---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-04"

keywords: apps, applications, activity tracking events

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:deprecated: .deprecated}
{:table: .aria-labeledby="caption"}

# {{site.data.keyword.dev_console}}Eventi {{site.data.keyword.cloudaccesstrailshort}} 
{: #at_events}

In qualità di responsabile della sicurezza, revisore o gestore, puoi utilizzare il servizio {{site.data.keyword.cloudaccesstrailfull}} per tracciare come gli utenti e le applicazioni interagiscono con la {{site.data.keyword.dev_console}} in {{site.data.keyword.cloud}}.
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} è obsoleto. A partire dal 9 maggio 2019, non puoi eseguire il provisioning delle nuove istanze di {{site.data.keyword.cloudaccesstrailshort}} e l'accesso alle istanze del piano *Lite* sarà rimosso. Le istanze del piano Premium esistenti sono supportate fino al 30 settembre 2019. Per continuare a monitorare l'attività del tuo account {{site.data.keyword.cloud_notm}}, esegui il provisioning di un'istanza di [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

Il servizio {{site.data.keyword.cloudaccesstrailfull_notm}} registra le attività avviate dall'utente che modificano lo stato di un servizio in {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Informazioni su {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov).

## Dove visualizzare gli eventi
{: #view-events-ui}

Gli eventi {{site.data.keyword.cloudaccesstrailshort}} sono disponibili nel dominio dell'account {{site.data.keyword.cloudaccesstrailshort}} disponibile nella regione di {{site.data.keyword.cloud_notm}} in cui sono stati generati gli eventi {{site.data.keyword.dev_console}}.

Per iniziare a monitorare le azioni del tuo utente, consulta l'[Esercitazione introduttiva](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started).

## Elenco di eventi
{: #events}

La seguente tabella elenca le azioni che generano un evento:

|Azioni	|Descrizione	|
|-----|-------------|
|bluemix-developer-experience.app.create |Viene generato un evento quando un utente crea un'applicazione.|
|bluemix-developer-experience.app.read |Viene generato un evento quando si verifica una qualsiasi delle seguenti situazioni:<br><br>Un utente scarica il codice dell'applicazione.<br><br>Un utente scarica il file delle credenziali utilizzando la CLI {{site.data.keyword.dev_console}}.<br><br>L'infrastruttura {{site.data.keyword.cloud_notm}} legge le credenziali dei servizi associati a un'applicazione.<br><br>Un utente visualizza l'elenco di applicazioni. Ad esempio, un utente visualizza l'elenco di applicazioni nella console {{site.data.keyword.dev_console}} o tramite la CLI {{site.data.keyword.dev_cli_short}}.|
|bluemix-developer-experience.app.update |Viene generato un evento quando si verifica una qualsiasi delle seguenti situazioni:<br><br>Qualcosa che riguarda le modifiche dell'applicazione. Ad esempio, un utente modifica il nome dell'applicazione.<br><br>Viene creato e aggiunto un nuovo servizio a un'applicazione.<br><br>Un servizio esistente viene aggiunto a un'applicazione.<br><br>Un servizio viene rimosso da un'applicazione.<br><br>Viene generato il codice per un'applicazione.<br><br>Una toolchain DevOps viene aggiunta tramite la console {{site.data.keyword.cloud_notm}}. Ad esempio un utente seleziona **Configure continuous delivery** dalla pagina App details.|
|bluemix-developer-experience.app.delete |Viene generato un evento quando un utente elimina un'applicazione.|
{: caption="Tabella 1. Azioni che generano eventi " caption-side="top"}
