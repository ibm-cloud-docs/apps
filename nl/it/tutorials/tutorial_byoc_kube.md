---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-05"

keywords: apps, deploy, deploy to kubernetes, cluster, delivery pipeline, toolchain, kube, deployment, custom code, kubernetes

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Distribuzione del tuo codice a un cluster Kubernetes
{: #tutorial-byoc-kube}

Acquisisci informazioni su come creare un'applicazione in {{site.data.keyword.cloud}} utilizzando il tuo repository di applicazioni esistente. Puoi connettere la tua toolchain DevOps esistente oppure crearne una e fornire in modo continuo un'applicazione a un contenitore protetto in un cluster Kubernetes. Questa esercitazione ti aiuta a configurare una pipeline DevOps di integrazione continua in modo che la modifica venga compilata e propagata automaticamente fino ad arrivare alla tua applicazione distribuita nel cluster Kubernetes.
{: shortdesc}

Quando già hai un repository di codice sorgente con una base di codice per un'applicazione di backend funzionante, {{site.data.keyword.cloud_notm}} ti aiuta a organizzare questo asset in una vista aggregata di tutti gli asset che costituiscono la portata del tuo intero prodotto. {{site.data.keyword.cloud_notm}} ti consente di essere operativo su un flusso di lavoro DevOps scalabile quando utilizzi la funzione di toolchain DevOps. Questa esercitazione aiuta lo sviluppatore esperto o l'ingegnere DevOps ad acquisire e configurare un {{site.data.keyword.containerlong}} di destinazione e configurare ed eseguire una toolchain DevOps, tutto sotto la guida delle prassi ottimali cloud.

Un _cluster_ è una serie di risorse, nodi di lavoro, reti e dispositivi di archiviazione che mantengono le applicazioni altamente disponibili. Dopo che hai creato il tuo cluster, puoi distribuire le tue applicazioni nei contenitori.
{: tip}

## Prima di iniziare
{: #prereqs-byoc-kube}

* [Crea un'applicazione dal tuo repository di codice](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc).
* Dalla [console {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno"), fai clic sull'icona **Menu** ![icona Menu](../../icons/icon_hamburger.svg) e seleziona **Containers** per [configurare un cluster Kubernetes](/docs/containers?topic=containers-getting-started).
* Conferma che la tua applicazione venga eseguita in Docker. I seguenti comandi sono degli esempi e non necessariamente dei passi che esistono nella tua applicazione:
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install`
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* Quindi, vai al tuo URL, ad esempio `http://localhost/springboothelloworld/sayhello`. Premi Ctrl+C per arrestare l'esecuzione di Docker.

## Aggiunta di servizi alla tua applicazione (facoltativo)
{: #resources-byoc-kube}

Dopo aver creato la tua applicazione, puoi aggiungere un servizio all'applicazione dalla pagina **App details**. {{site.data.keyword.cloud_notm}} crea automaticamente l'istanza del servizio. Il processo di provisioning può essere diverso per i diversi tipi di servizi. Ad esempio, un servizio database crea un database e un servizio di notifiche di push per le applicazioni mobili genera le informazioni di configurazione. {{site.data.keyword.cloud_notm}} fornisce le risorse di un servizio alla tua applicazione utilizzando un'istanza del servizio. Un'istanza del servizio può essere condivisa tra le applicazioni Web.

Questo processo esegue il provisioning di un'istanza del servizio, crea una chiave di risorsa (credenziali) e ne esegue il bind alla tua applicazione. Per ulteriori informazioni, vedi [Aggiunta di un servizio alla tua applicazione](/docs/apps?topic=creating-apps-add-resource).

Dopo aver aggiunto un servizio alla tua applicazione, devi [copiare le credenziali per il servizio nel tuo ambiente di distribuzione](/docs/apps?topic=creating-apps-credentials_overview).

## Preparazione della tua applicazione per la distribuzione
{: #deploy-byoc-kube}

In questo passo, connetti una toolchain DevOps all'applicazione e la configuri in modo da essere distribuita a un cluster Kubernetes ospitato nel {{site.data.keyword.containerlong}}.

La toolchain DevOps è abbastanza flessibile da consentire l'esecuzione gestita di fasi arbitrarie di esecuzione dello script di shell. In altre parole, puoi fare quasi tutto con una toolchain DevOps. L'ambito di questa sezione si concentra sulla distribuzione della tua applicazione su un cluster Kubernetes, tenendo al tempo stesso in mente le misure che saranno necessarie in futuro per il DevOps ridimensionato e le migliori prassi del cloud.

Stabilire una connessione tra la tua applicazione, la toolchain e il repository è un passo in avanti nell'organizzazione dei tuoi asset del prodotto. Aiuta anche ad aggregare una vista del tuo repository di origine con il tuo flusso di lavoro DevOps, le tue istanze dell'applicazione in esecuzione e i servizi dipendenti in tutte le tue destinazioni di distribuzione.

### Connessione di una toolchain DevOps esistente

Se hai già una toolchain DevOps, completa questa procedura:

1. Nella pagina **App details**, fai clic su **Configure continuous delivery**. Viene visualizzata la pagina **Deploy my app**.
2. Seleziona la toolchain che vuoi connettere alla tua applicazione e fai clic su **Enable deployment**. Viene visualizzata la pagina **App details**, che indica che la fornitura continua è configurata.

Se non vuoi creare una toolchain DevOps da zero, puoi abilitare al cloud il tuo codice esistente utilizzando il comando [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable). Il comando genera un template di toolchain DevOps che inserisci nel tuo repository. Utilizzi quindi tale template come l'insieme di istruzioni per ciò che crea la toolchain DevOps. Per ulteriori informazioni, vedi la [documentazione della CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli#byoc-cli).
{: tip}

### Creazione di una toolchain DevOps

Se vuoi controllare completamente la creazione della toolchain DevOps senza alcuna modifica nel repository del codice, crea la toolchain da zero. Crei anche tutte le integrazioni per creare la tua applicazione e distribuirla al cluster Kubernetes. 

1. Nella pagina **App details**, fai clic su **Create DevOps toolchain.** Viene visualizzata la pagina **Create a toolchain**.
2. Seleziona il template **Build your own toolchain**.
3. Nella pagina **Build your own toolchain**, immetti un nome per la tua toolchain, seleziona una regione e un gruppo di risorse (predefinito) e fai clic su **Create**.
4. Utilizza i breadcrumb nella finestra del browser per tornare alla pagina **App details**, che indica che la fornitura continua è configurata.
5. Nella pagina **App details**, fai clic su **View toolchain** per configurare la tua nuova toolchain DevOps.

### Aggiunta di un'integrazione GitHub
{: #github-byoc-kube}

Configura la toolchain DevOps con un'integrazione per il tuo repository GitHub per la toolchain. Questa operazione imposta un webhook nel tuo repository in modo che le richieste di pull e i push di codice in tale repository inviino un POST alla toolchain.

1. Nel tuo template di toolchain DevOps vuoto, fai clic su **Add a Tool**.
2. Seleziona **GitHub** se il tuo repository si trova su GitHub pubblico o su GitHub Enterprise.
3. Seleziona o immetti l'URL del server GitHub.
4. Potrebbe essere visualizzato il messaggio `Unauthorized on GitHub`. In questo caso, fai clic su **Authorize**. Quindi, nella pagina Authorize IBM Cloud Toolchains, fai clic su **Authorize IBM-Cloud** e immetti la tua password GitHub.
5. Nella pagina Configure the Integration, seleziona **Existing** per il tipo di repository in modo che la toolchain DevOps configuri il repository con un webhook e non crei alcun fork o copia del tuo repository.
6. Immetti il tuo URL repository, ad esempio `https://github.com/yourrepo/spring-boot-hello-world`.
7. Dopo qualche istante, ti potrebbe essere chiesto di autorizzare GitHub a concedere l'autorizzazione alla toolchain DevOps di utilizzare l'API REST GitHub per configurare il tuo repository con i webhook necessari per attivare la toolchain.
8.  Fai clic su **Crea integrazione**.

Puoi visualizzare il nuovo webhook dalle impostazioni del tuo repository.

### Aggiunta di una delivery pipeline
{: #pipeline-byoc-kube}

1. Fai clic su **Add a Tool**.
2. Seleziona **Delivery Pipeline**.
3. Immetti `Continuous Integration` per il nome della pipeline e fai clic su **Create Integration**.

### Configurazione delle fasi della tua pipeline
{: #pipelineconfig-byoc-kube}

Configura le fasi della pipeline per indirizzare il tuo input (il contenuto del repository GitHub) alla destinazione corretta. Poiché questa esercitazione presume che tu abbia un repository GitHub che produce un'immagine Docker funzionante e utilizza un {{site.data.keyword.containerlong}}, crei delle fasi della pipeline con input, script di shell e output che conseguono tale obiettivo.

1. Configura la fase della pipeline `build and publish`.
  1. Seleziona la delivery pipeline che hai creato e fai clic su **Add a Stage**.
  2. Fai clic sulla scheda **Input** e completa i campi nel seguente modo:
    * Immetti `build and publish Docker image` per il nome della fase.
    * Seleziona **Git repository** per il tipo di input.
    * Seleziona il tuo repository GitHub.
    * Seleziona il ramo che usi per l'integrazione continua.
  3.  Fai clic sulla scheda **Jobs**, fai clic su **Add Job '+'** e completa i campi nel seguente modo:
    * Seleziona **Build** per il tipo di lavoro.
    * Immetti `build and publish` per il nome.
    * Seleziona **Container Registry** per il tipo di builder.
    * Seleziona la regione in cui si trova il tuo cluster Kubernetes.
    * Seleziona **Enter an existing API key**. Se non hai una chiave API, consulta [Creazione di una chiave API](/docs/iam?topic=iam-userapikey#create_user_key). 
    * Immetti lo spazio dei nomi del registro contenitore, che puoi trovare facendo clic sull'icona **Menu** ![Icona Menu](../../icons/icon_hamburger.svg) e selezionando **Containers** > **Registry** > **Namespaces**.
    * Per il nome dell'immagine Docker, immetti `continuous` poiché questa fase di build della pipeline è per la build continua del ramo di integrazione continua del tuo repository.
    * Modifica lo script di build aggiungendo una o più righe dopo la prima riga `#!/bin/bash`. Ad esempio, per un repository creato utilizzando maven, potresti aggiungere delle righe simili al seguente esempio:

      ```bash
      export JAVA_HOME=/opt/IBM/java8
      # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
      export MAVEN_OPTS="-  
      Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
      mvn -B clean verify
      ```
      {: codeblock}
  4. Fai clic su **Salva**. 
2. Verifica la fase della tua pipeline `build and publish` facendo clic sull'icona **Play** fino a che la build non riesce. Una fase di colore verde indica che la build è riuscita. 
3. Configura la fase della pipeline `deploy to cluster` per distribuire l'immagine Docker al tuo cluster Kubernetes. 
  1. Nella pagina Delivery Pipeline, fai clic su **Add a Stage**.
  2. Fai clic sulla scheda **Input** e completa i campi nel seguente modo:
    * Immetti `deploy to cluster` per il nome.
    * Seleziona **Build artifacts** per il tipo di input.
    * Seleziona **Build & Publish Docker Image** per la fase.
    * Seleziona **Build & Publish** per il lavoro.
    * Poiché questa è la tua pipeline di integrazione continua, accetta l'opzione predefinita per il trigger della fase.
  3. Fai clic sulla scheda **Jobs**, fai clic su **Add Job '+'** e completa i campi nel seguente modo:
    * Immetti `deploy to continuous integration cluster` per il nome.
    * Seleziona **Kubernetes** per il tipo di deployer.
    * Seleziona la regione in cui si trova il tuo cluster Kubernetes.
    * Immetti la tua chiave API esistente. 
  4. Fai clic su **Salva**.
4. Verifica la fase della tua pipeline `deploy to cluster` facendo clic sull'icona **Play** fino a che la build non riesce. Una fase di colore verde indica che la build è riuscita.

## Verifica che la tua applicazione sia in esecuzione
{: #verify-byoc-kube}

La Delivery Pipeline o la riga di comando ti indirizzano all'URL della tua applicazione.

1. Dalla tua toolchain DevOps, fai clic su **Delivery Pipeline** e seleziona quindi **Deploy Stage**.
2. Fai clic su **View logs and history**.
3. Nel file di log, trova l'URL dell'applicazione. Alla fine del file di log, cerca la parola `urls` o `view`. Ad esempio, nel file di log potresti vedere una riga simile a `urls: my-app-devhost.mybluemix.net` o `View the application health at: http://<ipaddress>:<port>/health`.
4. Vai all'URL nel tuo browser. Se l'applicazione è in esecuzione, viene visualizzato un messaggio che include `Congratulations` o `{"status":"UP"}`.

Se stai utilizzando la riga di comando, esegui il comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) per aprire la pagina di un'applicazione distribuita manualmente nel tuo browser predefinito.

## Informazioni correlate

 * [Creazione delle toolchain](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)
 * [Configurazione di Git Repos and Issue Tracking](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#grit)
 * [Configurazione di GitHub](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#github)
 * [Configurazione di GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab)
