---

copyright:
  years: 2018
lastupdated: "2018-11-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Sviluppo di applicazioni
{: #intro}

La {{site.data.keyword.cloud_notm}} Developer Console aiuta gli sviluppatori a creare le applicazioni dai kit starter, a eseguire il provisioning e a collegare i servizi ottimizzati per {{site.data.keyword.cloud_notm}} chiave e a scaricare velocemente il codice di lavoro o a configurare la fornitura continua. Puoi creare, visualizzare, configurare e gestire la tua applicazione e scaricarne il codice. Utilizzando i kit starter puoi velocemente valutare e verificare i servizi {{site.data.keyword.cloud_notm}} con un'applicazione di esempio.
{:shortdesc}

## Cos'è un kit starter?
{: #starter_kits}

I kit starter sono ottimi per la generazione dinamica di un'applicazione di produzione di base nel linguaggio desiderato pronta per la distribuzione cloud. Ogni kit starter ha un linguaggio, un framework e un modello per uno specifico caso di utilizzo reale. Puoi riutilizzare il codice piuttosto che reinventarlo.

### Confronto di esempi e kit starter

Gli sviluppatori spesso si affidano a un codice prescritto come frammenti, dimostrazioni ed esempi. Come venire a sapere la differenza tra i frammenti, le dimostrazioni e gli esempi e i kit starter {{site.data.keyword.cloud_notm}}?

* **Frammento** - Un paio di righe di codice che viene spesso presentato in una IDE. I frammenti aiutano uno sviluppatore ad integrare una sintassi del linguaggio di programmazione o del supporto con una API definita.

* **Dimostrazione** - Il codice che è solitamente di elevata qualità e accuratezza e utilizza una gamma di servizi e punti di integrazione. Spesso richiede della configurazione e viene utilizzata per dimostrare un problema di business o una funzione della piattaforma. Le dimostrazioni possono valutare le fasi di adozione cloud. Alcune volte il suo codice viene incluso nel codice di produzione.

* **Esempio** - Il codice che è un piccolo esempio di una funzionalità, funzione, servizio o esperienza dell'utente specifici. Un esempio può essere riutilizzato o incluso in un'applicazione di produzione. Puoi utilizzare gli esempi per mostrare le funzionalità tecniche e gli approcci possibili per la risoluzione di problemi tecnici.

* **Kit starter {{site.data.keyword.cloud_notm}} ** - I kit starter sono modelli pronti per la produzione che puoi integrare con una serie di servizi per generare un asset pronto per la produzione. Quindi, puoi distribuirli a una pipeline DevOps e a un cluster Kubernetes. Un kit starter dispone di metadati descrittivi che ti forniscono informazioni sufficienti per sapere cosa fa. Dispone inoltre di istruzioni che indicano a {{site.data.keyword.cloud_notm}} cosa produrre. L'output può essere ulteriormente migliorato. Il contenuto del kit starter non è così complesso come una dimostrazione e non è banale come un frammento o un esempio. I kit starter vengono creati dinamicamente in base ai tuoi requisiti.

  I kit starter mostrano l'implementazione del modello chiave con un runtime, ad esempio Swift e Kitura. Possono includere un'esperienza utente semplice per sottolineare l'integrazione del servizio. I kit starter sono implementazioni personalizzabili di un caso di utilizzo sofisticato.

  I kit starter includono le istruzioni che consentono a {{site.data.keyword.cloud_notm}} di produrre automaticamente i progetti dell'applicazione di scaffolding con il codice portatile. Specificano inoltre che venga eseguito automaticamente il provisioning delle risorse quando crei un progetto.

## Risorse di provisioning automatico
{: #auto_privisioned_resources}

Se un kit starter specifica le risorse necessarie, {{site.data.keyword.cloud_notm}} crea automaticamente le istanze per quelle risorse quando crei il tuo progetto. Puoi eseguire manualmente il provisioning delle risorse o selezionare delle istanze della risorsa esistenti per ampliare il tuo progetto dopo che è stato creato. Puoi vedere un elenco di istanze del servizio associate al tuo progetto nella vista *Dettagli del progetto*, insieme alle credenziali nel caso ne avessi bisogno.

## Generazione del codice portatile
{: #portable_code}

La creazione di un'applicazione da un kit starter produce automaticamente il codice al tuo posto che ha un formato coerente ed è indipendente dal runtime. Puoi distribuire il codice nel tuo ambiente di scelta, ad esempio Kubernetes o Cloud Foundry, senza fare modifiche.

Il progetto include un file `README` che dispone dei dettagli tecnici del progetto e spiega cosa devi fare per avere la tua applicazione pronta per l'esecuzione.

Per ulteriori informazioni, vedi la [documentazione {{site.data.keyword.cloud_notm}} developer console per le risorse di apprendimento Apple](https://cloud.ibm.com/developer/appledevelopment/learning-resources).
{: tip}

### Quale contenuto dell'applicazione viene prodotto?
{: #content}

Il codice che un kit starter {{site.data.keyword.cloud_notm}} produce, ha quattro componenti fondamentali: la logica del caso di utilizzo, i componenti del linguaggio, l'abilitazione del servizio e l'abilitazione cloud. La generazione di questi componenti ti consente di risparmiare del tempo prezioso e ti assicura di stare utilizzando un'architettura all'avanguardia.

* **Logica del caso di utilizzo** è il codice di un particolare caso di utilizzo. Gli esempi includono il codice per un servizio chat di Watson Conversation o il codice per un'applicazione Visual recognition mobile.
* **Componenti del linguaggio** sono file e componenti del codice specifici per il linguaggio che selezioni per il tuo kit starter. Ad esempio, i programmatori node.js ha bisogno di un file `package.json` per la gestione della dipendenza e questo file viene automaticamente creato da {{site.data.keyword.cloud_notm}} Developer Experience.
* **Abilitazione del servizio** è il codice che consente alla tua applicazione di collegarsi al tuo progetto e di utilizzare i servizi che aggiungi ad esso. Esempi di elementi di abilitazione del servizio sono la gestione delle credenziali, il codice di inizializzazione e gli SDK specifici per il servizio.
* **Abilitazione cloud** è il codice che consente alla tua applicazione l'esecuzione su {{site.data.keyword.cloud_notm}}. Ad esempio, i grafici Helm che consentono alla tua applicazione l'esecuzione su un cluster Kubernetes {{site.data.keyword.cloud_notm}} in modo che rientri nella categoria di abilitazione del cloud.

L'applicazione prodotta da {{site.data.keyword.cloud_notm}} è strutturalmente solida e modella le procedure ottimali per la lingua che hai scelto per il tuo progetto. Per visualizzare i dettagli sui file e sulla struttura di un progetto dell'applicazione, consulta i seguenti argomenti.

* [File applicazione Java](/docs/apps/projects/java_project_contents.html)
* [File applicazione Node.js](/docs/apps/projects/node_project_contents.html)
* [File applicazione Python](/docs/apps/projects/python_project_contents.html)
* [File applicazione Swift](/docs/apps/projects/swift_project_contents.html).
