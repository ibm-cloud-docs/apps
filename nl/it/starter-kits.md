---

copyright:
  years: 2019
lastupdated: "2019-04-25"

keywords: developer tools, building apps, developer entry point, get started coding, starter kit

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Cosa sono i kit starter?
{: #starter-kits}

Un kit starter è un modello pronto per la produzione che è possibile integrare con una serie di servizi per generare un asset pronto per la produzione che può essere distribuito direttamente in una pipeline DevOps e in un cluster Kubernetes.
{:shortdesc}

## Cosa puoi fare con un kit starter?
{: #starter-overview}

I kit starter sono ideali per assemblare in modo dinamico un'applicazione di produzione di base nel linguaggio desiderato pronta per la distribuzione cloud. 

Un kit starter contiene metadati descrittivi che forniscono all'utente informazioni sufficienti per conoscere le funzionalità del kit. Contiene inoltre le istruzioni che indicano a {{site.data.keyword.cloud_notm}} cosa produrre. L'output è subito pronto per la produzione e può essere iterato per ulteriori miglioramenti, in base alle procedure consigliate da {{site.data.keyword.cloud_notm}}. Il contenuto del kit starter non è così complesso come una dimostrazione e non è banale come un frammento o un esempio. Le applicazioni sono create dinamicamente in base ai requisiti dello sviluppatore.

Ogni kit starter include un linguaggio, un framework e un modello per uno specifico caso di utilizzo. Puoi riutilizzare il codice piuttosto che reinventarlo. Se un kit starter richiede servici specifici, non c'è alcun problema. Con i servizi con provisioning automatico, {{site.data.keyword.cloud_notm}} crea automaticamente le istanze per quei servizi quando crei la tua applicazione. Puoi accedere ai kit starter dal dashboard o dalla CLI (command-line interface) {{site.data.keyword.cloud_notm}}.

Consulta le istruzioni per la [creazione di un'applicazione con un kit starter](/docs/apps?topic=creating-apps-tutorial-starterkit).

## Come i kit starter si differenziano dagli esempi?
I kit starter sono pronti per la produzione e si focalizzano sulla dimostrazione di un'implementazione del modello chiave utilizzando un runtime (ad esempio, Node.js e Express). In alcuni casi, i kit starter offrono un'esperienza utente semplice per sottolineare l'integrazione del servizio. In altri casi i kit starter rappresentano un'implementazione personalizzabile di un caso di utilizzo sofisticato.

* Un frammento è costituito da alcune righe di codice che vengono spesso presentate in un IDE. I frammenti aiutano uno sviluppatore ad integrare una sintassi del linguaggio di programmazione o del supporto con una API definita.
* Una dimostrazione è solitamente di alta qualità e fedeltà e utilizza una gamma di servizi e punti di integrazione. Spesso richiede del tempo di configurazione e viene utilizzata per dimostrare un problema di business o una funzione della piattaforma. La puoi utilizzare per valutare le fasi di adozione cloud. A volte è il codice che viene incluso nel codice di produzione.
* Un esempio è un piccolo esempio di funzionalità, funzione, servizio o percorso utente specifici. Puoi riutilizzare un esempio o includerlo in un'applicazione di produzione. In genere viene utilizzato per mostrare capacità tecniche e un possibile approccio alla risoluzione di un problema tecnico.

## Codice portatile
{: #portable-code}

La creazione di un'applicazione da un kit starter crea automaticamente il codice al tuo posto che ha un formato coerente ed è indipendente dal runtime. Puoi distribuire il codice nella destinazione di tua scelta, come Kubernetes o Cloud Foundry, senza apportare modifiche.

Puoi dare un'occhiata al codice della tua applicazione facendo clic su **Download code** nella pagina **App details** dell'applicazione. Il tuo codice viene scaricato come un file `.zip` che contiene l'intera struttura del codice dell'applicazione. Puoi facilmente estrarre il file ed eseguire il codice localmente utilizzando la {{site.data.keyword.dev_cli_notm}} o aggiungerlo al tuo repository di gestione del codice.

### Quale codice viene creato?
{: #what-code}

Quando crei direttamente un'applicazione o tramite l'aiuto di un kit starter, l'applicazione contiene il codice portatile. Il codice portatile contiene il codice di abilitazione cloud per più ambienti cloud.Puoi quindi creare il codice in quattro aree fondamentali:
* Codice che segue le procedure consigliate per un linguaggio specifico
* Codice che abilita l'esecuzione sul cloud dell'applicazione
* Codice che viene inizializzato per il collegamento ai servizi cloud
* Codice specifico per un caso di utilizzo

La generazione di questi componenti ti consente di risparmiare del tempo prezioso e ti assicura di stare utilizzando un'architettura all'avanguardia.

* La logica del caso di utilizzo fornisce funzioni per la funzione principale di un particolare caso di utilizzo. Gli esempi potrebbero essere il codice per un servizio chat di Watson Conversation o il codice per un'applicazione Visual recognition mobile.
* I componenti del linguaggio sono componenti di codice e file specifici per il linguaggio di programmazione che selezioni per il tuo kit starter. Ad esempio, i programmatori node.js hanno bisogno di un file package.json per la gestione della dipendenza e questo file viene automaticamente creato per te.
* L'abilitazione del servizio è un codice che consente alla tua applicazione di connettersi e utilizzare i servizi che aggiungi. Gestione delle credenziali, codice di inizializzazione e SDK specifici del servizio sono esempi di elementi di abilitazione del servizio.
* L'abilitazione cloud è il codice che consente alla tua applicazione di essere eseguita su {{site.data.keyword.cloud_notm}}. Ad esempio, i grafici Helm che consentono alla tua applicazione l'esecuzione su un cluster Kubernetes {{site.data.keyword.cloud_notm}}.

Quando crei un'applicazione da un kit starter {{site.data.keyword.cloud_notm}}, la tua applicazione inizia con un'architettura comprovata che riflette anche le procedure consigliate per il linguaggio che hai selezionato.

Ogni applicazione include un file readme che contiene i dettagli tecnici dell'applicazione e spiega cosa è necessario perché la tua applicazione sia in esecuzione se non lo è immediatamente.
{: tip}
