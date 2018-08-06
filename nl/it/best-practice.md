---

copyright:
  years: 2017, 2018
lastupdated: "2018-07-25"

---

# Cosa rende buona un'applicazione?
{: #best-practice}

Crea la tua applicazione in {{site.data.keyword.Bluemix_notm}} per usufruire di tutto ciò che è offerto dal cloud. Queste procedure consigliate possono aiutarti a garantire che le tue applicazioni siano pronte per il cloud.
{:shortdesc}

## Crea la tua applicazione in modo che sia indipendente dalla topologia

In un ambiente non cloud, la tua applicazione potrebbe utilizzare una particolare topologia di distribuzione. Tuttavia, la topologia della tua applicazione potrebbe cambiare nelle applicazioni cloud, poiché i servizi e le applicazioni pronti per il cloud consentono cambiamenti di scalabilità immediati. Le modifiche alla scalabilità includono ridimensionamento dinamico e ridimensionamento manuale del numero di istanze di un'applicazione.

Crea la tua applicazione in modo che sia il più possibile generica e senza stati, per impedire che l'applicazione subisca modifiche di scalabilità.

## Supponiamo che il file system locale non sia permanente

Non fare affidamento sui file scritti nel file system perché un'istanza dell'applicazione può essere spostata, eliminata o duplicata sul cloud. Se un'applicazione utilizza il file system locale come cache delle informazioni utilizzate di frequente, inclusi i log delle applicazioni, le informazioni vengono perse quando l'istanza viene arrestata e riavviata in una posizione diversa o in un'altra VM.

Invece che nel file system locale, puoi memorizzare
le informazioni in un servizio, quale un database SQL o NoSQL. In un ambiente cloud dinamico, è fondamentale anche che i tuoi log siano disponibili in un servizio avente durata superiore alle istanze dell'applicazione in cui vengono generati i log.

## Memorizza lo stato della sessione al di fuori della tua applicazione

Lo stato del tuo sistema è definito dai tuoi database e dallo spazio di archiviazione condiviso e non da ogni singola istanza dell'applicazione in esecuzione. Qualsiasi tipo di mancanza di stato limita la scalabilità di un'applicazione. Cerca di ridurre al minimo
l'impatto dello stato della sessione, memorizzandolo in un'ubicazione centralizzata
sul server.

Se non puoi eliminare del tutto lo stato della sessione, trasferiscilo in una memoria altamente disponibile esterna al tuo server delle applicazioni. Tra le memorie utilizzabili vi sono IBM WebSphere eXtreme Scale, Redis o Memcached oppure un database esterno.

## Utilizza un registro di servizio esterno per risolvere gli endpoint del servizio

Non partire dal presupposto che i servizi utilizzati dalla tua applicazione siano assegnati a determinati indirizzi IP o nomi host. I servizi potrebbero essere trasferiti o rigenerati nel tuo ambiente cloud e anche i nomi host e gli indirizzi IP possono cambiare.

L'estrazione di dipendenze specifiche dell'ambiente in una
serie di file di proprietà rappresenta un miglioramento, ma resta inappropriato. La migliore prassi prevede la risoluzione degli endpoint dei servizi attraverso il registro
di un servizio esterno o la delega dell'intera funzione di instradamento
al bus di un servizio o a un programma di bilanciamento dei carichi con un nome virtuale.

## Crea la tua applicazione utilizzando un'architettura a più regioni
{: #multiregion}

Esegui più istanze per evitare tempi di inattività in una singola regione, ma per fornire un'applicazione ancora più solida, valuta la possibilità di utilizzare un'architettura a più regioni.

## Assicurati di stare monitorando le tue applicazioni
{: #monitoring}

{{site.data.keyword.Bluemix_notm}} semplifica il monitoraggio della tua applicazione con servizi come [New Relic ![Icona link esterno](../icons/launch-glyph.svg)](http://newrelic.com/){: new_window}. Per ulteriori informazioni, vedi [Monitoraggio e registrazione](../monitor_log/logging.html#logging).

## Approfitta delle opzioni di supporto
{: #support}

Il piano prezzi a pagamento di {{site.data.keyword.Bluemix_notm}} offre una serie di diversi tipi di account con supporto a pagamento facoltativo. Indipendentemente dal tuo tipo di account, se prevedi di portare un'applicazione in produzione su {{site.data.keyword.Bluemix_notm}}, considera questa opzione.

Con o senza il supporto a pagamento, puoi ottenere assistenza come descritto in [Supporto](../get-support/howtogetsupport.html), che offre un'assicurazione contro problemi imprevisti.

## Evita API di infrastruttura nella tua applicazione

Se ti affidi a una specifica API di infrastruttura nella tua applicazione, la modifica dell'infrastruttura risulta più complessa, perché un'API di infrastruttura può fare riferimento a diversi livelli nel tuo stack di software.

Puoi invece affidarti ai prodotti open source o commerciali esistenti e lasciare le soluzioni PaaS nel livello PaaS in modo da mantenerle al di fuori del codice della tua applicazione.

## Utilizza protocolli standard

Non utilizzare protocolli oscuri che
richiedono una configurazione aggiuntiva per la resilienza.

Le applicazioni basate su protocolli standard hanno maggiore resilienza agli elementi di configurazione delegati alla piattaforma. I protocolli standard includono HTTP, SSL,
database standard, accodamento e connessioni ai servizi Web.

## Utilizza librerie compatibilità invece di funzioni specifiche del sistema operativo

Se hai già utilizzato
funzioni specifiche del sistema operativo, puoi risolvere il problema utilizzando librerie di compatibilità,
quali Cygwin e Mono. Cygwin è una libreria di compatibilità che fornisce una serie di strumenti Linux in un ambiente Windows. Mono è una libreria di compatibilità che fornisce le funzionalità di Windows .NET in Linux.

Evita le dipendenze specifiche del sistema operativo;
utilizza invece servizi forniti dall'infrastruttura middleware
o da fornitori di servizi.

## Crea script per il tuo processo di installazione

Nell'ambiente cloud dinamico, la tua applicazione potrebbe essere installata frequentemente su richiesta. Il processo di installazione deve avere script ed essere affidabile e i dati della configurazione
devono essere esternalizzati dagli script.

Acquisisci l'istallazione della tua applicazione come una serie uniforme di script indipendenti dal sistema operativo. Fa in modo che le dimensioni dell'installazione della tua applicazione restino contenute e preservane la portabilità, in modo che si adegui a differenti tecniche di automazione. Inoltre, riduci al minimo le dipendenze richieste dall'installazione dell'applicazione.

Per ulteriori informazioni sulle applicazioni pronte per il cloud, vedi [The 12-factor app ![Icona link esterno](../icons/launch-glyph.svg)](http://12factor.net/){: new_window}.


