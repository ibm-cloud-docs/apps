---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:table: .aria-labeledby="caption"}

# {{site.data.keyword.dev_console}}Eventi {{site.data.keyword.cloudaccesstrailshort}} 
{: #at_events}

In qualità di responsabile della sicurezza, revisore o gestore, puoi utilizzare il servizio {{site.data.keyword.cloudaccesstrailfull}} per tracciare come gli utenti e le applicazioni interagiscono con la {{site.data.keyword.dev_console}} in {{site.data.keyword.cloud}}.
{: shortdesc}

Il servizio {{site.data.keyword.cloudaccesstrailfull_notm}} registra le attività avviate dall'utente che modificano lo stato di un servizio in {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Informazioni su {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov).

## Dove visualizzare gli eventi
{: #view-events-ui}

Gli eventi {{site.data.keyword.cloudaccesstrailshort}} sono disponibili nel dominio dell'account {{site.data.keyword.cloudaccesstrailshort}} disponibile nella regione di {{site.data.keyword.cloud_notm}} in cui sono stati generati gli eventi {{site.data.keyword.dev_console}}.

Per iniziare a monitorare le azioni del tuo utente, vedi l'[esercitazione introduttiva](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla).

## Elenco di eventi
{: #events}

La seguente tabella elenca le azioni che generano un evento:

<table>
  <caption>Azioni che generano eventi</caption>
  <tr>
    <th>Azioni</th>
	  <th>Descrizione</th>
  <tr>
  <tr>
    <td>bluemix-developer-experience.app.create</td>
	  <td>Viene generato un evento quando un utente crea un'applicazione.</td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.read</td>
	  <td>Viene generato un evento quando si verifica una qualsiasi delle seguenti situazioni: </br><ul><li>Un utente scarica il codice dell'applicazione.</li> <li>Un utente scarica il file delle credenziali utilizzando la CLI {{site.data.keyword.dev_console}}.</li> <li>L'infrastruttura dell'esperienza di sviluppo legge le credenziali delle risorse associate a un'applicazione.</li> <li>Un utente visualizza l'elenco delle applicazioni, ad esempio, quando l'utente visualizza l'elenco delle applicazioni nella console {{site.data.keyword.dev_console}} o tramite la CLI {{site.data.keyword.dev_cli_short}}.</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.update</td>
	  <td>Viene generato un evento quando si verifica una qualsiasi delle seguenti situazioni: </br><ul><li>Viene modificato qualcosa riguardo l'applicazione, ad esempio, quando un utente modifica il nome dell'applicazione. </li><li>Una nuova risorsa viene creata e aggiunta a un'applicazione.</li><li>Una risorsa esistente viene aggiunta a un'applicazione.</li><li>Un servizio viene rimosso da un'applicazione.</li><li>Viene generato il codice per un'applicazione.</li><li>Una toolchain DevOps viene aggiunta tramite l'esperienza di sviluppo, ad esempio, selezionando *Distribuisci a Cloud*.</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.delete</td>
	  <td>Viene generato un evento quando un utente elimina un'applicazione.</td>
  </tr>
</table>
