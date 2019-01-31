---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-11-29"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Walkthrough della console per sviluppatori {{site.data.keyword.cloud_notm}}
{: #intro}

<!--I can't see how a customer needs to be walked through the experience without performing a specific task.-->


{{site.data.keyword.cloud}} Developer Experience consente a uno sviluppatore di applicazioni native cloud di creare un'applicazione da diversi kit starter, creare e connettere i principali servizi ottimizzati da {{site.data.keyword.Bluemix_notm}} e quindi scaricare rapidamente il codice di lavoro o configurare la fornitura continua. La Developer Experience fornisce una serie di console per sviluppatori in {{site.data.keyword.Bluemix_notm}} che ti consentono di creare, visualizzare, configurare e gestire la tua applicazione e di distribuirla a una pipeline Devops o di scaricarla per lo sviluppo locale.

Creando un'applicazione attraverso una console per sviluppatori {{site.data.keyword.cloud_notm}}, tutte le parti necessarie della tua applicazione vengono mantenute nel tuo account sul server {{site.data.keyword.cloud_notm}}.  In questo modo puoi spostarti avanti e indietro tra la GUI della console per sviluppatori e [{{site.data.keyword.dev_cli_notm}}](/docs/cli/idt/index.html) ogni volta tu scelga di farlo.

Le console per sviluppatori {{site.data.keyword.cloud_notm}} ti offrono un percorso trasparente per creare un'applicazione starter pronta per la produzione per il caso di utilizzo che selezioni. Diamo un'occhiata ai passi che potresti eseguire nel tuo percorso.

<!-- Ready to jump in?  Visit the [{{site.data.keyword.cloud_notm}} Web App developer console](https://{DomainName}/developer/appservice) to get started.
{: tip} -->

##Schermata Overview
{: #overview_screen}

La schermata Overview ti offre contenuti su misura per l'argomento o il canale specifico della console per sviluppatori in cui stai lavorando. Dalla schermata della panoramica puoi visualizzare la documentazione, accedere alle risorse di apprendimento, consultare i servizi, vedere i kit starter in primo piano o collegarti a una più ampia raccolta di kit starter. Fai clic su `Starter Kits` nella navigazione per accedere alla vista Starter Kits.

![Schermata Overview della console per sviluppatori](images/overview_screen.png "Schermata Overview") <br> *Schermata Overview della console per sviluppatori*

##Vista Starter Kits
{: #starter_kits_view}

La vista Starter Kits mostra la raccolta di kit starter specifici per un'area di casi di utilizzo.  Puoi fare clic sui vari link su una scheda del kit starter per visualizzare dimostrazioni e ulteriori informazioni.  Seleziona un kit starter per passare alla vista Create New App.

In alcuni casi, se selezioni un kit starter vengono visualizzati ulteriori dettagli.  In questo caso, fai semplicemente clic sul pulsante `Create` per passare alla vista Create New App.{: tip}

![Vista Starter Kits della console per sviluppatori](images/starter_kits_view.png "Vista Starter Kits") <br> *Vista Starter Kits della console per sviluppatori*

##Vista Create New App
{: #create_new_project_view}

Dalla vista Create New App immetti un nome per la tua applicazione, fornisci informazioni sulla distribuzione e sull'instradamento e selezioni un linguaggio. Nota che a destra puoi anche vedere i servizi di cui viene eseguito automaticamente il provisioning quando crei la tua applicazione insieme a piani tariffari e termini per ciascuno di essi.  Fai clic su `Create` per passare alla vista App Details.  Se non hai già effettuato l'accesso a {{site.data.keyword.cloud_notm}}, questo è il momento in cui dovrai farlo.

![Vista Create New App della console per sviluppatori](images/create_new_project_view.png "Vista Create New App") <br> *Vista Create New App della console per sviluppatori*

## Vista App Details
{: #project_details_view}

La vista App Details visualizza l'elenco dei servizi configurati per la tua applicazione. Per ciascun elemento nell'elenco, vengono visualizzati il nome del servizio, i link ad altre informazioni e un pulsante di *azioni* con tre punti allineati verticalmente. Le opzioni del pulsante di *azioni* comprendono la rimozione del servizio dall'applicazione, l'apertura del dashboard per il servizio e l'eliminazione del servizio. Nota che la rimozione di un'istanza del servizio rimuove solo l'associazione a questa applicazione e non elimina l'istanza del servizio.  Nota inoltre che le credenziali del servizio sono consolidate su questa vista, per cui non dovrai visitare le viste di ogni singola istanza del servizio per ottenerle. 

![Vista App Details della console per sviluppatori](images/project_details_view.png "Vista App Details") <br> *Vista App Details della console per sviluppatori*

La vista App Details ti consente inoltre di aggiungere alla tua applicazione servizi nuovi o esistenti che non facevano parte del kit starter originale. Per effettuare questa operazione, fai clic sul link `Add Resource` nella casella di elenco dei servizi.  I servizi disponibili dipendono dal tipo di applicazione e dai servizi disponibili in una regione, quindi non tutti i servizi possono essere associati a tutte le applicazioni.

![Finestra di dialogo Add Resource della console per sviluppatori](images/add_resource_dialog.png "Finestra di dialogo Add Resource") <br> *Finestra di dialogo Add Resource della console per sviluppatori*

Nella vista App Details hai accesso al tuo codice in due modi diversi:

*  [Consigliato] Fai clic sul pulsante `Deploy to Cloud` per eseguire il push del tuo codice a un repository e distribuire la tua applicazione a {{site.data.keyword.cloud_notm}}.  Per ulteriori informazioni sulla toolchain DevOps {{site.data.keyword.cloud_notm}}, fai clic [qui](/docs/services/ContinuousDelivery/toolchains_about.html#toolchains_about).
*  Per dare una rapida occhiata al tuo codice dell'applicazione, seleziona `Download Code` per produrre e scaricare il codice per la tua applicazione.

##Vista App List
{: #project_list_view}

Puoi vedere un elenco di tutte le applicazioni che hai creato dalla vista Apps List.  Da qui, puoi rinominare o eliminare le tue applicazioni. Fai clic sulla riga del nome di un'applicazione per ritornare alla vista App Details.

![Vista App List della console per sviluppatori](images/project_list_view.png "Vista App List") <br> *Vista App List della console per sviluppatori*
