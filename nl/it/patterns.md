---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-02"

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

Il modello dell'applicazione web produce applicazioni che forniscono il contenuto web come HTML, JavaScript e i fogli di calcolo al server web. Esistono molti kit starter dell'applicazione web.

* Basic - fornisce un file `index.html` statico, un foglio di calcolo vuoto e predefinito e un file JavaScript.
* React - un framework avanzato per creare le interfacce utente. I file di origine si trovano in `src/client/app` e vengono compilati con WebPack e forniti nella directory pubblica.

Puoi trovare i kit starter per il modello dell'applicazione nel [Dashboard dello sviluppatore dell'applicazione web{{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## Backend for Frontend
{: #bff}

Il modello Backend for Frontend (BFF) ti aiuta a creare il codice di backend che espone i dati e i servizi di business in un modo che corrisponde alle aspettative dell'utente per un canale dell'applicazione specifico, ad esempio mobile o web. Ad esempio, gli utenti che usano un dispositivo mobile potrebbero utilizzare il controllo vocale, mentre gli utenti che utilizzano la tua applicazione tramite il browser web preferiscono puntare e fare clic. Puoi creare due BFF, uno per il dispositivo mobile che include servizi come [{{site.data.keyword.conversationfull}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.ibm.com/watson/developercloud/conversation.html) e uno per il dispositivo web che ha un'interfaccia utente più sofisticata.

In {{site.data.keyword.cloud_notm}}, puoi creare un BFF con l'approccio di programmazione poliglotta. Puoi utilizzare Node.js, Swift, Java o Python ed eseguirli in un modello con servizi contenitore o che utilizzano funzioni senza server.

Il BFF gestisce la persistenza dei dati, la memorizzazione nella cache e l'integrazione con i servizi di elevato valore come [{{site.data.keyword.ibmwatson}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=watson), [{{site.data.keyword.iot_short_notm}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=iot), [{{site.data.keyword.weather_short}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/services/weather-company-data?taxonomyNavigation=apps) e [{{site.data.keyword.sparks}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/catalog/services/apache-spark?taxonomyNavigation=apps).

Il BFF espone un'API utilizzando più comunemente un modello REST, ma puoi progettare il tuo BFF per lavorare da un'architettura di messaggistica che utilizza {{site.data.keyword.messagehub}}.

Esistono molti kit starter BFF tra cui puoi scegliere in base ai tuoi requisiti di linguaggio e framework. Puoi trovare i kit starter per il modello BFF nel [Dashboard dello sviluppatore dell'applicazione web{{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## Microservizio
{: #microservice}

Le applicazioni del microservizio forniscono le basi per la creazione di microservizi di backend, inclusi un endpoint di integrità di base e l'API REST. Le applicazioni generate contengono tutte le dipendenze richieste sia per il microservizio stesso che per gli eventuali servizi cloud collegati.

Esistono molti kit starter del microservizio tra cui puoi scegliere in base ai tuoi requisiti di linguaggio e framework.  Puoi trovare i kit starter per il modello del microservizio nel [Dashboard dello sviluppatore dell'applicazione web{{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## Mobile
{: #mobile}

Le applicazioni mobili sono diverse dagli altri modelli perché hanno un componente lato client significativo. Il modello potrebbe includere la connessione diretta a servizi mobili come le notifiche push, l'autenticazione e l'analisi mobile, noti come modello MBaaS (Mobile Backend as a Service) o potrebbe avere un [Backend for Frontend](#bff) dedicato.

{{site.data.keyword.cloud_notm}} offre diversi kit starter per dispositivo mobile per iOS Swift, Android e Cordova. Puoi trovare i kit starter per il modello del dispositivo mobile nel [Dashboard dello sviluppatore mobile {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/mobile/dashboard).

## Linguaggi
{: #languages}

Il kit starter {{site.data.keyword.cloud_notm}} viene fornito in molti linguaggi e framework disponibili. Ad esempio, i kit starter del microservizio cloud offrono un'opzione Node.js, mentre i kit starter strettamente collegati all'analisi dei dati possono includere Python o Go. Vengono illustrati alcuni linguaggi comuni utilizzati nei kit starter {{site.data.keyword.cloud_notm}}.


|Linguaggio programmazione | Descrizione | Framework di sviluppo |
|-----|-----|-----|
|Java | [Java](../runtimes/liberty/getting-started.html) dispone di funzionalità comprovate per la creazione delle applicazioni a livello aziendale. Ma le nuove funzionalità in Java 8, combinate con runtime più leggeri come Liberty e framework come Spring Boot, rendono anche Java perfettamente adatto alla creazione dei microservizi.  In aggiunta, Java è un linguaggio di programmazione popolare per le applicazioni Android. | Spring, Liberty, Android |
|Swift | [Swift](../runtimes/swift/getting-started.html) è un linguaggio di programmazione moderno creato da Apple nel 2014 progettato per sostituire l'utilizzo di Objective C ed è open source da dicembre 2015. Oggi viene utilizzato per creare software per iOS, macOS, servizi web e sistemi sui sistemi operativi Linux e macOS che utilizzano l'architettura x86, ARM o z/Architecture. Scrive come un linguaggio di scripting, ma è compilato per ottenere alte prestazioni simili a C con un basso costo di gestione che lo rende ideale per i runtime del cloud. Utilizza un sistema del tipo statico e sicuro che visualizzi in Java ma lo stile funzionale e le routine asincrone in JavaScript. È molto performante e l'origine viene compilata nel codice nativo che utilizza la toolchain del compilatore LLVM e può facilmente utilizzare le librerie di sistema esterne scritte in C. Da quando Swift può essere utilizzato per codificare sia applicazioni lato server che client, gli sviluppatori utilizzano Swift quando hanno bisogno di migrare facilmente le funzioni dal client al server e viceversa. | Kitura, iOS|
|Node.js | [Node.js](../runtimes/nodejs/getting-started.html) è un runtime JavaScript che utilizza event-driven, un modello non bloccante, rendendolo più leggero ed efficiente, eccellendo per velocità effettiva e scalabilità per le applicazioni web, i modelli di backend-for-front-end e i microservizi. L'ecosistema di pacchetti Node.js, npm, fornisce l'accesso a una grande raccolta di moduli open source, fornendo un'ampia gamma di funzionalità per velocizzare lo sviluppo della tua applicazione. | Express|
|JavaScript|JavaScript crea effetti interattivi nelle pagine web. JavaScript con HTML e CSS è la base della maggior parte delle pagine web. Quando incluso in un plugin Cordova, il codice JavaScript può sfruttare al massimo le funzioni del dispositivo native. Gli sviluppatori con competenze web possono facilmente creare applicazioni mobili e dove il codice dell'applicazione appropriato può essere riutilizzato tra web e mobile.|Cordova|
|Python | [Python](../runtimes/python/getting-started.html) è un linguaggio di programmazione generale e interpretato che pone l'accento sulla leggibilità. Python consente ai programmatori di implementare le funzioni con meno righe di codice rispetto a quello richiesto da altri linguaggi. Le funzioni nel linguaggio rendono possibile scrivere con codice orientato sul soggetto, funzionale o imperativo. Python è comunemente utilizzato per l'elaborazione delle attività del linguaggio naturali. | Flask, Django|


