---

copyright:
  years: 2018
lastupdated: "2018-03-16"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Le fasi consigliate di sviluppo cloud
{: #development_process}

Gli sviluppatori dell'applicazione cloud passano attraverso quattro fasi fondamentali nel processo di sviluppo: inizio, codice, fornitura e gestione. Il flusso è interattivo e rapido. L'obiettivo è di produrre un'applicazione un minimo utilizzabile e di utilizzare il feedback dall'applicazione di produzione per eseguire l'iterazione in modo continuo del codice o del ciclo di fornitura finché la tua applicazione trova il favore degli utenti.
{: shortdesc}

![Flusso di sviluppo](images/dev_flow_overview.png "Flusso di sviluppo") Figura 1. Fasi del processo di sviluppo

In alcuni casi, "esegui" viene richiamato in una fase separata ma qui lo combiniamo con le fasi di gestione e fornitura.

Diamo un'occhiata da vicino al modo migliore di utilizzare {{site.data.keyword.cloud_notm}} nel tuo flusso di sviluppo.

##Inizia subito
{: #get_started}

Inizia a creare la tua applicazione dai dashboard dello sviluppatore {{site.data.keyword.cloud_notm}}, dove puoi selezionare un kit starter correlato al caso di utilizzo e scegliere un linguaggio di programmazione. {{site.data.keyword.cloud_notm}} utilizza le istruzioni dal kit starter per eseguire automaticamente il provisioning delle risorse necessarie e creare un progetto dell'applicazione indipendente dal runtime e di uno specifico linguaggio che si basa sulla tua applicazione di produzione. Per completare la fase iniziale, fai clic su **Distribuisci al cloud** dal dashboard dello sviluppatore. Con un solo clic crea una toolchain DevOps completa con un repository di codice che viene popolato con il codice di origine della tua applicazione e la pipeline di distribuzione.

![Introduzione](images/dev_get_started.png "Introduzione") Figura 2. Flusso iniziale

Quando utilizzi il pulsante **Distribuisci al cloud** per configurare la tua toolchain DevOps, seleziona la tua piattaforma di runtime, ad esempio Kubernetes o Cloud Foundry. L'applicazione starter prodotta da {{site.data.keyword.cloud_notm}} è indipendente dal runtime e non è necessario modificarla.
{: tip}

##Sviluppa localmente
{: #develop_locally}

Dopo aver creato la toolchain e il progetto dell'applicazione starter, inizia il tuo sviluppo localmente. Clona il codice dal tuo repository in una workstation locale e importalo nella tua IDE. Utilizza {{site.data.keyword.dev_cli_notm}} per creare, eseguire e verificare la tua applicazione cloud sulla tua macchina locale. {{site.data.keyword.dev_cli_notm}} crea e gestisce un contenitore locale per te. Quando sei pronto per visualizzare la tua applicazione in esecuzione nel cloud, esegui il push del tuo repository cloud e unisci le tue modifiche.

![Sviluppa localmente](images/dev_code_locally.png "Sviluppa localmente") Figura 3. Sviluppa localmente il flusso

Le funzioni di base per {{site.data.keyword.dev_cli_notm}} sono `bx dev build` e `bx dev run`, ma la CLI offre molto di più. Consulta [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html) per ulteriori dettagli.
{: tip}

##Fornisci e gestisci in {{site.data.keyword.cloud_notm}}
{: #deliver_and_manage}

L'unione delle modifiche al tuo repository cloud avvia un ciclo di creazione e distribuzione nella toolchain DevOps che hai creato precedentemente. La tua applicazione è in esecuzione nel cloud dopo pochi minuti.

Per controllare lo stato della tua pipeline DevOps, utilizza il tuo dashboard Delivery Pipeline. Per controllare lo stato generale della tua applicazione, consulta il dashboard {{site.data.keyword.cloud_notm}} per il tuo account.
{: tip}

La toolchain prodotta dalla tua esperienza introduttiva ha i componenti di base necessari per la fornitura continua basata sul team e collaborativa. Tuttavia, {{site.data.keyword.cloud_notm}} offre un'ampia serie di servizi DevOps che puoi aggiungere nella tua toolchain per migliorare la fornitura, il monitoraggio, la registrazione e l'avviso.

![Fornisci e gestisci](images/dev_deliver_and_manage.png "Fornisci e gestisci") Figura 4. Fornitura e gestione del flusso

Ulteriori informazioni sullo [sviluppo continuo su {{site.data.keyword.cloud_notm}}](../services/ContinuousDelivery/index.html#cd_getting_started).

## Conclusioni finali

![Dettagli del processo](images/dev_process_detail.png "Dettagli del processo") Figura 5. Processo di sviluppo end-to-end
