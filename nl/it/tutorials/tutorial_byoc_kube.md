---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Distribuzione del tuo codice a un cluster Kubernetes
{: #tutorial}

Acquisisci informazioni su come creare un'applicazione in {{site.data.keyword.cloud}} utilizzando il tuo repository di applicazioni esistente. Puoi connettere la tua toolchain DevOps esistente oppure crearne una e fornire in modo continuo un'applicazione a un contenitore protetto in un cluster Kubernetes. Questa esercitazione ti aiuta a configurare una pipeline DevOps di integrazione continua in modo che la modifica venga compilata e propagata automaticamente fino ad arrivare alla tua applicazione distribuita nel cluster Kubernetes.
{: shortdesc}

Quando già hai un repository di codice sorgente con una base di codice per un'applicazione di backend funzionante, {{site.data.keyword.cloud_notm}} ti aiuta a organizzare questo asset in una vista aggregata di tutti gli asset che costituiscono la portata del tuo intero prodotto. {{site.data.keyword.cloud_notm}} ti consente di essere operativo su un flusso di lavoro DevOps scalabile quando utilizzi la funzione di toolchain DevOps. Questa esercitazione aiuta lo sviluppatore esperto o l'ingegnere DevOps ad acquisire e configurare un cluster Kubernetes {{site.data.keyword.cloud_notm}} di destinazione e configurare ed eseguire una toolchain DevOps, tutto sotto la guida delle prassi ottimali cloud.

Un _cluster_ è una serie di risorse, nodi di lavoro, reti e dispositivi di archiviazione che mantengono le applicazioni altamente disponibili. Dopo che hai creato il tuo cluster, puoi distribuire le tue applicazioni nei contenitori.
{: tip}

## Prima di iniziare
{: #prereqs}

* Attieniti alla procedura per [Creazione di applicazioni dal tuo repository di codice](/docs/apps/tutorials/tutorial_byoc.html) per creare un'applicazione.
* Dal [dashboard {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}){: new_window}, fai clic sull'icona **Menu** ![Icona Menu](../../icons/icon_hamburger.svg) e seleziona **Containers** per [configurare un cluster Kubernetes](/docs/containers/container_index.html).
* Per confermare che la tua applicazione sia eseguita in Docker, esegui questi comandi:
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install`
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* Visita quindi il tuo URL, come ad esempio `http://localhost/springboothelloworld/sayhello`.   
Premi `Ctrl+C` per arrestare l'esecuzione del Docker.

## Facoltativo. Aggiunta di risorse alla tua applicazione
{: #add_resources}

Aggiungi una risorsa di servizio alla tua applicazione e {{site.data.keyword.cloud_notm}} crea il servizio per tuo conto. Il processo di provisioning può essere diverso per i diversi tipi di servizi. Ad esempio, un servizio database crea un database e un
servizio di notifiche di push per le applicazioni mobili genera le informazioni di configurazione. {{site.data.keyword.cloud_notm}} fornisce le risorse di un servizio alla tua applicazione utilizzando un'istanza del servizio. Un'istanza del servizio può essere condivisa tra le
applicazioni Web.

Questo processo esegue il provisioning di un'istanza del servizio, crea una chiave di risorsa (credenziali) e ne esegue il bind alla tua applicazione. Per ulteriori informazioni, vedi [Aggiunta di un servizio alla tua applicazione](/docs/apps/reqnsi.html).

### Copia delle credenziali di servizio nel tuo ambiente

Dopo che hai aggiunto una risorsa di servizio alla tua applicazione, nota che le credenziali per tale servizio sono visualizzate nella casella **Credenziali**. Devi copiare le credenziali nel tuo ambiente di distribuzione.

Per ulteriori informazioni sulla copia di credenziali nel tuo ambiente, vedi [Aggiunta di credenziali al tuo ambiente Kubernetes](/docs/apps/creds_kube.html).


## Preparazione della tua applicazione per la distribuzione utilizzando una toolchain DevOps
{: #connect_toolchain}

In questo passo, connetti una toolchain DevOps all'applicazione e la configuri per essere distribuita a un cluster Kubernetes che è ospitato nel servizio Kubernetes {{site.data.keyword.cloud_notm}}.

La toolchain DevOps è abbastanza flessibile da consentire l'esecuzione gestita di fasi arbitrarie di esecuzione dello script di shell. In altre parole, puoi fare quasi tutto con una toolchain DevOps. L'ambito di questa sezione si concentra sulla distribuzione della tua applicazione su un cluster Kubernetes, tenendo al tempo stesso in mente le misure che saranno necessarie in futuro per il DevOps ridimensionato e le migliori prassi del cloud.

Stabilire una connessione tra la tua applicazione, la toolchain e il repository è un passo in avanti nell'organizzazione dei tuoi asset del prodotto. Aiuta anche ad aggregare una vista del tuo repository di origine con il tuo flusso di lavoro DevOps, le tue istanze dell'applicazione in esecuzione e i servizi dipendenti in tutte le tue destinazioni di distribuzione. 

Nella pagina Connect Toolchain, disponi di alcune opzioni:

* Connetti la tua applicazione a una toolchain esistente.
* Connetti la tua applicazione a una toolchain esistente che non contiene il tuo repository. Connetti quindi la toolchain al tuo repository in un secondo momento.
* Connetti la tua applicazione a una nuova toolchain.

### Connetti la tua applicazione a una toolchain esistente
{: #connect_toolchain_repo}

Se hai una o più toolchain DevOps che sono già connesse al repository Git che hai specificato durante la creazione della tua applicazione, tali toolchain sono visualizzate nella tabella **With repo**. La toolchain deve essere configurata per richiamare l'origine dallo stesso repository che hai definito nell'applicazione. Molto probabilmente vuoi selezionare una di queste toolchain da connettere alla tua applicazione.

### Connetti la tua applicazione a una toolchain esistente che non contiene il tuo repository
{: #connect_toolchain_notrepo}

Se hai una o più toolchain DevOps che sono associate al tuo account, ma non sono connesse al repository Git che hai specificato durante la creazione della tua applicazione, tali toolchain sono visualizzate nella tabella etichettata **without your repo**. Puoi selezionare una di queste toolchain e connetterla alla tua applicazione ma devi anche aggiungere manualmente il tuo repository a tale toolchain.

Per ulteriori informazioni sull'aggiunta del tuo repository alla tua toolchain, vedi:

 * [Configurazione di Git Repos and Issue Tracking](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitbluemix)
 * [Configurazione di GitHub](/docs/services/ContinuousDelivery/toolchains_integrations.html#github)
 * [Configurazione di GitLab](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitlab)


### Connetti la tua applicazione a una nuova toolchain
{: #create_toolchain}

Disponi di queste opzioni per connettere la tua applicazione ad una nuova toolchain:
* Se non vuoi creare una toolchain DevOps da zero, puoi abilitare al cloud il tuo codice esistente utilizzando il comando [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable). Il comando genera un modello di toolchain DevOps che inserisci nel tuo repository. Utilizzi quindi tale modello come l'insieme di istruzioni per ciò che crea la toolchain DevOps. Per ulteriori informazioni, vedi la [documentazione della CLI](/docs/apps/create-deploy-cli.html#byoc).
* Crea una toolchain DevOps da zero all'interno della console. Se vuoi controllare completamente la creazione della toolchain DevOps senza alcuna modifica nel repository del codice, crea la toolchain da zero. Per ulteriori informazioni, vedi [Creazione di una toolchain DevOps da zero](#create_toolchain_scratch).

#### Creazione di una toolchain DevOps da zero
{: #create_toolchain_scratch}

Se vuoi creare una toolchain da zero e connetterla alla tua applicazione, completa questa procedura. Crei anche tutte le integrazioni per creare la tua applicazione e distribuirla al cluster Kubernetes. La funzione toolchain DevOps offre dei modelli, ma questa procedura mostra come configurare una toolchain DevOps da zero.

Quando scegli di creare una toolchain dalla tua nuova applicazione, la pagina [Create a Toolchain](https://{DomainName}/devops/create) viene aperta nel [dashboard DevOps](https://{DomainName}/devops/) in una nuova scheda nel tuo browser. Dopo che hai creato e configurato la tua toolchain in tale scheda, devi tornare alla pagina **Connect a toolchain** nella tua applicazione e aggiornare la pagina.
{:tip}

1. Nella pagina **Create a Toolchain**, fai clic sul modello **Build your own toolchain**.
2. Nella pagina **Build your own toolchain**, immetti un nome per la tua toolchain, seleziona una regione e un gruppo di risorse (predefinito) e fai clic su **Create**.

Viene creata una toolchain vuota senza strumenti o integrazioni preconfigurati. Continua a configurare e testare la tua nuova toolchain completando i passi rimanenti.

## Aggiunta di un'integrazione GitHub

Puoi configurare la toolchain DevOps con l'integrazione GitHub utilizzando la seguente procedura:

1. Nel tuo modello di toolchain DevOps, fai clic su **Add a Tool**.
2. Seleziona **GitHub** (se il tuo repository si trova in effetti sul GitHub pubblico o su Enterprise GitHub).
3. Nella pagina **Configure the Integration** per GitHub, completa la seguente procedura:
  * Seleziona (o immetti) l'URL del **GitHub Server**.
  * Se vedi un messaggio "Unauthorized on GitHub", fai clic su **Authorize**. Quindi, nella pagina **Authorize IBM Cloud Toolchains**, fai clic su **Authorize IBM-Cloud**. Immetti quindi la tua password GitHub.
  * Nella pagina **Configure the Integration**, seleziona **Existing** per **Repository Type** in modo che la toolchain DevOps configuri il repository con un webhook e _non_ crei fork o copie del tuo repository.
  * Immetti il tuo URL repository (**Repository URL**). Ad esempio, `https://github.com/yourrepo/spring-boot-hello-world`).
  * Attendi qualche minuto; ti potrebbe essere richiesto di autorizzare GitHub a concedere l'autorizzazione alla toolchain DevOps di utilizzare la API REST GitHub per configurare il tuo repository con i webhook che sono necessari per attivare la toolchain.
  * Fai clic su **Crea integrazione**.

Hai configurato questa toolchain DevOps con un'integrazione per il tuo repository GitHub. In questo modo, alla toolchain è consentito impostare un webhook nel tuo repository in modo che le richieste di pull e i push di codice in tale repository attivino un POST alla toolchain. Puoi guardare nelle impostazioni del tuo repository per vedere il nuovo webhook.

## Aggiunta di una Delivery Pipeline per creare, testare e distribuire la tua applicazione

La Delivery Pipeline è dove viene eseguita la maggior parte del lavoro.

1. Fai clic su **Add a Tool**.
2. Seleziona **Delivery Pipeline**.
3. Nella pagina **Configure the Integration** per Delivery Pipeline, completa questa procedura:
 * Immetti "Continuous Integration" per il nome della pipeline.
 * Fai clic su **Crea integrazione**.

Hai creato una delivery pipeline vuota. Definisci quindi le fasi della pipeline per indirizzare il tuo input (il contenuto del repository GitHub) alla sua destinazione. Poiché questa esercitazione presume che tu abbia un repository GitHub che produce un'immagine Docker funzionante e utilizza un cluster Kubernetes di IBM Containers, crei delle fasi della pipeline con input, script di shell e output che conseguono tale obiettivo.

### Configurazione della fase della pipeline "Build and Publish"

1. Fai clic sulla delivery pipeline che hai creato.
2. Nella pagina della delivery pipeline, fai clic su **Add a Stage**.
3. Nella scheda **Input** della pagina **Stage Configuration**, completa i campi nel seguente modo:
  * Per Stage Name, immetti **Build & Publish Docker Image**.
  * **Input type**: seleziona **Git repository**.
  * **Git repository**: Seleziona il tuo repository GitHub.
  * **Branch**: seleziona il ramo che usi per l'integrazione continua.
4. Fai clic sulla scheda **Jobs** e completa i campi nel seguente modo:
  * Fai clic sull'icona **Add Job '+'** e seleziona **Build** per il tipo di lavoro.
  * Immetti un nome, come ad esempio **Build & Publish**.
  * **Builder type**: seleziona **Container Registry**.
  * **IBM Cloud region**: seleziona la regione dove si trova il tuo cluster Kubernetes.
  * **API key**: seleziona **Enter an existing API key**. Se non hai una chiave o non conosci la tua chiave API, puoi [ottenere una chiave API](https://{DomainName}/iam/#/apikeys) aprendo una finestra del browser separata e andando a **Manage** > **Security** > **Platform API Keys**. Assicurati di tenere questa chiave in un posto sicuro.
  * **Account name**: questo campo viene completato automaticamente quando immetti una chiave API.
  * **Container Registry namespace**: immetti lo [spazio dei nomi del registro contenitori](https://{DomainName}/containers-kubernetes/registry/namespaces) (puoi trovarlo facendo clic sull'icona **Menu** ![Icona Menu](../../icons/icon_hamburger.svg) e selezionando **Containers** > **Registry** > **Namespaces**).
  * **Docker image name**: immetti **continuous** poiché questa fase di build della pipeline è per la build continua del ramo di integrazione continuo del tuo repository.
  * **Build script**: nota lo script di shell. Non ha le istruzioni di build dell'applicazione per il _tuo_ repository. Devi aggiungere una riga o più dopo la prima riga `#!/bin/bash`. Ad esempio, per un repository creato utilizzando maven, potresti aggiungere delle righe simili al seguente esempio:

    ```bash
    export JAVA_HOME=/opt/IBM/java8
    # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
    export MAVEN_OPTS="-Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
    mvn -B clean verify
    ```
    {: codeblock}
5. Fai clic su **Save**. La tua fase della pipeline "Build and Publish" ora compare nella tua toolchain.

### Esecuzione di test della tua fase di pipeline "Build and Publish"

Fai clic sull'icona **Play** fino a che la compilazione (build) non riesce. Sai che funziona quando la fase diventa verde e l'output dello script conferma le tue aspettative. L'obiettivo in questa fase è pubblicare un'immagine Docker nel tuo registro delle immagini. Se non ritieni sufficiente quanto visualizzato dallo script, puoi visualizzare il registro immagini per confermare la pubblicazione facendo clic sull'icona **Menu** ![Icona Menu](../../icons/icon_hamburger.svg) e selezionando quindi **Containers** > **Registry** > **Private Repositories**. Conferma quindi che sia elencato un repository che termina con il nome `/continuous`. (Ricorda, questo era il nome dell'immagine).

### Configurazione della fase della pipeline "Deploy to Cluster"

Finora, hai pubblicato un'immagine Docker nel tuo registro delle immagini Docker privato. Ora, è il momento di creare una fase che distribuisce questa immagine al tuo cluster Kubernetes.

1. Nella pagina della delivery pipeline, fai clic su **Add a Stage**.
2. Nella scheda **Input** della pagina **Stage Configuration**, completa i campi nel seguente modo:
  * **Name**: immetti **Deploy**.
  * **Input type**: seleziona **Build artifacts**.
  * **Stage**: seleziona **Build & Publish Docker Image**.
  * **Job**: seleziona **Build & Publish**.
  * **Stage trigger**: poiché questa è la tua pipeline di integrazione continua, seleziona il valore **Run jobs then the previous stage is completed** predefinito.
3. Fai clic sulla scheda **Jobs** e completa i campi nel seguente modo:
  * Fai clic sull'icona **Add Job '+'** e seleziona **Deploy** per il tipo di lavoro.
  * Immetti un nome, come ad esempio **Deploy to Continuous Integration Cluster**.
  * **Deployer type**: seleziona **Kubernetes**.
  * **IBM Cloud region**: seleziona la regione dove si trova il tuo cluster Kubernetes.
  * **API key**: seleziona **Enter an existing API key**. Se non hai una chiave o non conosci la tua chiave API, puoi [ottenere una chiave API](https://{DomainName}/iam/#/apikeys) aprendo una finestra del browser separata e andando a **Manage** > **Security** > **Platform API Keys**. Assicurati di tenere questa chiave in un posto sicuro.
  * Accetta le restanti impostazioni predefinite.
4. Fai clic su **Save**. La tua fase di pipeline "Deploy" ora appare nella tua toolchain.

### Esecuzione di test della tua fase di pipeline "Deploy to Cluster"

Fai clic sull'icona **Play** fino a che la compilazione (build) non riesce. Sai che funziona quando la fase diventa verde e l'output dello script conferma le tue aspettative. Puoi visualizzare i log per la fase. Verso la fine dei log, trova un link selezionabile all'applicazione in esecuzione. Tuttavia, solo _tu_ conosci la root di contesto e il percorso della tua applicazione. Accoda il percorso corretto per confermarne l'esecuzione.
