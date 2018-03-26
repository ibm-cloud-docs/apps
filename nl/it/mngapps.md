---

copyright:
  years: 2015, 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Controllo dello stato della tua applicazione
{: #manageapps}

Il tuo dashboard nella console {{site.data.keyword.Bluemix}} fornisce delle informazioni di riepilogo per le applicazioni da te create. Le informazioni di riepilogo includono nome, icona, URL, runtime, stato di esecuzione e istanze del servizio associate all'applicazione.
{:shortdesc}

## Descrizione dello stato della tua applicazione
{: #status}

Dal tuo dashboard, puoi visualizzare lo stato di ciascuna applicazione:

<dl>
<dt>
<strong>
Arrestato o Sconosciuto (grigio)
</strong>
</dt>
<dd>
La tua applicazione è arrestata oppure lo stato è sconosciuto. L'icona grigia indica che l'applicazione è arrestata oppure che lo stato è sconosciuto.
</dd>
<dt>
<strong>
In esecuzione (verde)
</strong>
</dt>
<dd>
La tua applicazione è in esecuzione. L'icona verde indica che l'applicazione è avviata e tutte le istanze sono in esecuzione.
</dd>
<dt>
<strong>
_Numero_  in esecuzione (giallo)
</strong>
</dt>
<dd>
L'applicazione è stata avviata ma non tutte le istanze sono in esecuzione. L'icona gialla indica che è in esecuzione meno del 100% delle istanze. Viene visualizzato il numero di istanze in esecuzione e il numero di istanze non riuscite.
</dd>
<dt>
<strong>
Non in esecuzione (rosso)
</strong>
</dt>
<dd>
La tua applicazione non è in esecuzione. L'icona rossa indica che l'applicazione è avviata, ma nessuna istanza è in esecuzione.
</dd>
</dl>

## Visualizzazione del dashboard dei dettagli dell'applicazione
{: #viewingapps}

Puoi visualizzare ulteriori informazioni su un'applicazione facendo clic sul suo nome nel dashboard. Quindi, puoi visualizzare la pagina Panoramica dell'applicazione.

Nella pagina Panoramica dell'applicazione, dopo che un'applicazione è stata distribuita, puoi avviare, arrestare o, in caso di applicazioni Web, modificare il numero di istanze e la quantità di memoria utilizzata dall'applicazione. Per le applicazioni Web, {{site.data.keyword.Bluemix_notm}} non ridimensiona automaticamente la tua applicazione in base al suo carico, quindi devi essere tu a gestire questo aspetto.

Le applicazioni possono essere ridistribuite se viene apportato un aggiornamento. Il meccanismo di aggiornamento dell'applicazione è uguale al meccanismo utilizzato per la sua originale distribuzione. {{site.data.keyword.Bluemix_notm}} arresta
tutte le istanze in esecuzione e le sostituisce con le nuove istanze automaticamente.
