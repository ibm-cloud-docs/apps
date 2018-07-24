---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-07-12"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# Architetture comuni per le applicazioni cloud
{: #patterns}

I kit starter su {{site.data.keyword.cloud_notm}} ti aiutano a produrre le applicazioni con un'architettura comprovata. Le applicazioni sono tutti diverse, ma quando basi la tua applicazione su un noto modello architettonico, è più facile ottenere rapidamente un risultato affidabile. Quando crei un'applicazione da un kit starter, stai scegliendo uno dei diversi tipi di pattern insieme ai componenti, come un runtime, per compilare il modello.
{:shortdesc}

## Applicazione web
{: #web}

Il modello dell'applicazione web produce applicazioni che forniscono il contenuto web come HTML, JavaScript e i fogli di stile al server web. {{site.data.keyword.cloud_notm}} offre diversi kit starter dell'applicazione web.

* Basic - fornisce un file `index.html` statico, un foglio di stile vuoto e predefinito e un file JavaScript.
* React - un framework avanzato per creare le interfacce utente. I file di origine si trovano in `src/client/app` e vengono compilati con WebPack e forniti nella directory pubblica.

Puoi trovare i kit starter per il modello dell'applicazione nel [Dashboard dello sviluppatore dell'applicazione web{{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## BFF (backend-for-frontend)
{: #bff}

Il BFF (backend-for-frontend) ti aiuta a creare il codice di backend che espone i dati e i servizi di business in un modo che corrisponde alle aspettative dell'utente per un canale dell'applicazione specifico, come ad esempio mobile o web. Ad esempio, gli utenti su un dispositivo mobile possono utilizzare il controllo vocale, mentre gli utenti del browser web preferiscono puntare e fare clic. Puoi creare due BFF, uno per il dispositivo mobile che include servizi come [{{site.data.keyword.conversationfull}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/conversation.html) e uno per il dispositivo web che ha un'interfaccia utente più sofisticata.

In {{site.data.keyword.cloud_notm}}, puoi creare un BFF con l'approccio di programmazione poliglotta. Puoi utilizzare Node.js, Swift, Java o Python ed eseguirli in un modello con servizi contenitore o che utilizzano funzioni senza server.

Il BFF gestisce la persistenza dei dati, la memorizzazione nella cache e l'integrazione con i seguenti servizi ad alto valore.

* [{{site.data.keyword.ibmwatson}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=watson)
* [{{site.data.keyword.iot_short_notm}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=iot)
* [{{site.data.keyword.weather_short}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/services/weather-company-data?taxonomyNavigation=apps)
* [{{site.data.keyword.sparks}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/services/apache-spark?taxonomyNavigation=apps).

Il BFF espone un'API utilizzando più comunemente un modello REST, ma puoi progettare il tuo BFF per lavorare da un'architettura di messaggistica che utilizza {{site.data.keyword.messagehub}}.

Scegli un kit starter BFF per i tuoi requisiti di linguaggio e framework. Puoi trovare i kit starter per il modello BFF nel [Dashboard dello sviluppatore dell'applicazione web{{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## Microservizio
{: #microservice}

Le applicazioni del microservizio forniscono le basi per la creazione di microservizi di backend, inclusi un endpoint di integrità di base e l'API REST. Le applicazioni generate includono tutte le dipendenze richieste sia per il microservizio stesso sia per qualsiasi servizio cloud collegato.

Scegli un kit starter del microservizio per i tuoi requisiti di linguaggio e framework. Puoi trovare i kit starter per il modello del microservizio nel [Dashboard dello sviluppatore dell'applicazione web{{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## Mobile
{: #mobile}

Le applicazioni mobili sono diverse dagli altri modelli perché hanno un componente lato client significativo. Il modello potrebbe includere la connessione diretta a servizi mobili come le notifiche push, l'autenticazione e l'analisi mobile. I servizi mobili sono noti come modello MBaaS (Mobile Backend as a Service). Possono anche avere un [backend-for-frontend](#bff) dedicato.

{{site.data.keyword.cloud_notm}} offre diversi kit starter per dispositivo mobile per iOS Swift, Android e Cordova. Puoi trovare i kit starter per il modello del dispositivo mobile nel [Dashboard dello sviluppatore mobile {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/mobile/dashboard).

## Linguaggi
{: #languages}

Il kit starter {{site.data.keyword.cloud_notm}} viene fornito in molti linguaggi e framework disponibili. Ad esempio, i kit starter del microservizio cloud offrono un'opzione Node.js, mentre i kit starter strettamente collegati all'analisi dei dati possono includere Python o Go. Vengono illustrati alcuni linguaggi comuni utilizzati nei kit starter {{site.data.keyword.cloud_notm}}.

|Linguaggio programmazione | Descrizione | Framework di sviluppo |
|-----|-----|-----|
|Java | [Java](../runtimes/liberty/getting-started.html) è ottimo per la creazione di applicazioni a livello enterprise. Le nuove funzioni in Java 8, però, combinate con runtime più leggeri come Liberty e framework come Spring Boot, rendono Java anche una scelta perfetta per la creazione dei microservizi.  Java è un linguaggio di programmazione popolare per le applicazioni Android. | Spring, Liberty, Android |
|Swift | [Swift](../runtimes/swift/getting-started.html) è un linguaggio di programmazione moderno creato da nel 2014 e progettato per sostituire l'utilizzo di Objective C ed è open source dal dicembre del 2015. Oggi viene utilizzato per creare software per iOS, macOS, servizi web e sistemi sui sistemi operativi Linux e macOS che utilizzano l'architettura x86, ARM o z/Architecture. La scrittura è come quella di un linguaggio di script ma è compilato per ottenere elevate prestazioni simili a C con un basso utilizzo del processore. È ideale per i runtime cloud. Utilizza un sistema del tipo statico e sicuro che visualizzi in Java ma lo stile funzionale e le routine asincrone in JavaScript. Ha buone prestazioni e il sorgente viene compilato nel codice nativo che utilizza la toolchain del compilatore LLVM. Può facilmente utilizzare le librerie di sistema da altri linguaggi che sono scritte in C. Poiché Swift può essere utilizzato per codificare sia applicazioni lato server che client, gli sviluppatori utilizzano Swift quando hanno bisogno di migrare facilmente le funzioni dal client al server e viceversa. | Kitura, iOS|
|Node.js | [Node.js](../runtimes/nodejs/getting-started.html) è un runtime JavaScript che utilizza event-driven, un modello I/O non bloccante, rendendolo più leggero ed efficiente. Eccelle per quanto riguarda la velocità effettiva e la scalabilità per le applicazioni web, i modelli di backend-for-front-end e i microservizi. Il registro di pacchetti Node.js, npm, fornisce l'accesso a una grande raccolta di moduli open source. Fornisce un'ampia gamma di funzionalità per velocizzare lo sviluppo della tua applicazione. | Express|
|JavaScript|JavaScript crea effetti interattivi nelle pagine web. JavaScript con HTML e CSS è la base della maggior parte delle pagine web. Quando incluso in un plugin Cordova, il codice JavaScript può sfruttare al massimo le funzioni del dispositivo native. Gli sviluppatori con competenze web possono facilmente creare applicazioni mobili e dove il codice dell'applicazione appropriato può essere riutilizzato tra web e mobile.|Cordova|
|Python | [Python](../runtimes/python/getting-started.html) è un linguaggio di programmazione generale e interpretato che pone l'accento sulla leggibilità. Python consente ai programmatori di implementare le funzioni con meno righe di codice rispetto a quante potrebbero essere necessarie in altri linguaggi. Le funzioni nel linguaggio rendono possibile scrivere con codice orientato sul soggetto, funzionale o imperativo. Python è comunemente utilizzato per l'elaborazione delle attività del linguaggio naturali. | Flask, Django|


