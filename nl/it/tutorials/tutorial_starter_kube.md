---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Distribuzione di un'applicazione kit starter a un cluster Kubernetes
{: #tutorial-starterkit-kube}

Acquisisci informazioni su come creare un'applicazione in {{site.data.keyword.cloud}} utilizzando uno starter kit vuoto e una toolchain Kubernetes e fornire in modo continuo l'applicazione a un contenitore protetto in un cluster Kubernetes. La tua pipeline DevOps di integrazione continua può essere configurata in modo che le tue modifiche al codice vengano compilate e propagate automaticamente all'applicazione che si trova nel cluster Kube. Se già hai una pipeline, la puoi connettere alla tua applicazione.
{: shortdesc}

{{site.data.keyword.cloud_notm}} offre i kit starter che ti aiutano a creare le basi di un'applicazione che viene eseguita su Kubernetes. Quando utilizzi un kit starter, è facile seguire un modello di programmazione nativo del cloud che utilizza le prassi ottimali di {{site.data.keyword.cloud_notm}} per lo sviluppo di applicazioni. I kit starter generano applicazioni che rispettano il modello di programmazione nativo del cloud e includono scenari di test, controlli dell'integrità e metriche in ogni linguaggio di programmazione. Puoi anche eseguire il provisioning di servizi cloud che vengono quindi inizializzati nella tua applicazione generata.

Questa esercitazione utilizza l'opzione di distribuzione Kubernetes. In questa esercitazione, stiamo creando un'applicazione da un kit starter di base utilizzando Java + Spring, aggiungendo un'istanza del servizio Cloudant e distribuendola a {{site.data.keyword.cloud_notm}} utilizzando un ambiente Kubernetes.

Innanzitutto, vedi il seguente diagramma di flusso del kit starter e i suoi corrispondenti passi di panoramica.

![Diagramma di flusso del kit starter](../images/starterkit-flow.png) 

## Prima di iniziare
{: #prereqs-starterkit-kube}

* Crea un'applicazione **Java + Spring** utilizzando un [kit starter](/docs/apps/tutorials/tutorial_starter-kit.html#tutorial-starterkit).
* Installa la [CLI {{site.data.keyword.cloud_notm}}](/docs/cli/index.html).
* Configura [Docker ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://www.docker.com/get-started){: new_window}.

## Aggiunta di risorse alla tua applicazione
{: #resources-starterkit-kube}

Aggiungi una risorsa di servizio {{site.data.keyword.cloud_notm}} alla tua applicazione. La seguente procedura esegue il provisioning di un'istanza Cloudant, crea una chiave di risorsa (credenziali) e ne esegue il bind alla tua applicazione.

1. Nella pagina **App Details**, fai clic su **Add resource**.
2. Seleziona **Data** e fai clic su **Next**..
3. Seleziona **Cloudant** e fai clic su **Next**.
4. Nella pagina **Add Cloudant**, seleziona la regione (US-South), il gruppo di risorse (default) e il piano di prezzi (Lite - una singola istanza gratuita).
5. Fai clic su **Crea**. Viene visualizzata la pagina **App Details** e viene eseguito il provisioning dell'istanza Cloudant e il suo bind alla tua applicazione. Nota che la chiave di risorsa (credenziali) Cloudant viene aggiunta al campo **Credentials**.
6. Facoltativo. Se vuoi dare una rapida occhiata al tuo codice applicativo dopo che hai aggiunto le risorse, fai clic su **Download code**. Il tuo codice viene scaricato come un file `.zip` che contiene l'intera struttura del codice applicativo. Puoi facilmente estrarre il file ed eseguire il codice localmente utilizzando la {{site.data.keyword.dev_cli_notm}} o aggiungerlo al tuo repository di gestione del codice.

## Distribuzione della tua applicazione utilizzando una toolchain DevOps
{: #deploy-starterkit-kube}

Collega una toolchain DevOps all'applicazione e configurala in modo che venga distribuita a un cluster Kubernetes ospitato nel servizio Kubernetes {{site.data.keyword.cloud_notm}}.

1. Nella pagina **App Details**, fai clic su **Deploy to cloud**.
2. Nella pagina **Choose a deployment environment**, seleziona **Deploy to Kubernetes**.
3. Seleziona una regione e un cluster. Se non hai un cluster Kubernetes, fai clic su **Create cluster**.
  * Nella pagina **Create new cluster**, seleziona l'ubicazione, il tipo di cluster (gratuito), immetti un nome cluster e fai quindi clic su **Create cluster**.
  * Se necessario, attieniti alle istruzioni a schermo per ottenere l'accesso al tuo cluster.
  * Per creare la toolchain, attendi che il cluster indichi **READY**. Con la regione **US-South**, puoi eseguire il provisioning di un singolo cluster gratuito.
  * Ritorna alla pagina **Choose a deployment environment**.
4. Fai clic su **Next**. Viene visualizzata la pagina **Configure toolchain**.
5. Nella pagina **Configure toolchain**, immetti un nome toolchain, seleziona una regione, seleziona un gruppo di risorse e fai quindi clic su **Create**. Viene visualizzata la pagina **App Details**, insieme alle informazioni di distribuzione relative alla tua toolchain.

## Visualizzazione del tuo repository
{: #view-repo-starterkit-kube}

1. Nella pagina **App Details**, fai clic su **View repo**. Viene visualizzato il repository Git generato dal kit starter.
2. Facoltativo. Configura SSH sul tuo desktop attenendoti alle istruzioni a schermo.
3. Facoltativo. Crea un token di accesso personale sul tuo account attenendoti alle istruzioni a schermo.

## Visualizzazione di cronologia, log e strumenti della toolchain
{: #view-logs-starterkit-kube}

1. Una volta finita la fase di distribuzione, viene visualizzata la pagina **App Details**, insieme alle informazioni di distribuzione relative alla tua toolchain.
2. Accedi alla toolchain facendo clic su **View toolchain**. Viene visualizzata la scheda **Overview** della pagina del toolchain, che mostra gli strumenti inclusi con la toolchain. Questo esempio include i seguenti strumenti, che erano stati preselezionati nel kit starter quando era stata creata la toolchain.
  * Un programma di traccia dei lavori, per tracciare gli aggiornamenti e le modifiche al progetto.
  * Una repository Git che contiene il codice sorgente della tua applicazione.
  * Un'istanza Eclipse Orion, che è un IDE basato sul web per modificare la tua applicazione.
  * Una Delivery Pipeline che consiste in una fase personalizzabile di compilazione e distribuzione.
	 * La fase di compilazione (BUILD) inserisce nel contenitore l'applicazione. Più precisamente, la fase di compilazione:
	   * Clona il tuo repository GitLab.
	   * Crea l'applicazione.
	   * Crea l'immagine Docker.
	   * Pubblica l'immagine nel tuo registro contenitore privato.
	 * La fase di distribuzione (DEPLOY) richiama l'immagine contenitore dal tuo registro contenitore e ne esegue quindi la distribuzione al tuo cluster Kubernetes.
3. Fai clic su **Delivery Pipeline**. Vengono visualizzate le fasi della pipeline.
4. Nel tile **Deploy Stage**, fai clic su **View logs and history**.

## Verifica che la tua applicazione sia in esecuzione
{: #verify-starterkit-kube}

Dopo che hai distribuito la tua applicazione, la Delivery Pipeline o la riga di comando ti indirizzano all'URL per la tua applicazione.

1. Dalla tua toolchain DevOps, fai clic su **Delivery Pipeline** e seleziona quindi **Deploy Stage**.
2. Fai clic su **View logs and history**.
3. Nel file di log, trova l'URL dell'applicazione:

    Alla fine del file di log, cerca `View the application health at: http://<ipaddress>:<port>/health`.

4. Vai all'URL nel tuo browser. Se l'applicazione è in esecuzione, viene visualizzato un messaggio che include `Congratulations` o `{"status":"UP"}`.

Se stai utilizzando la riga di comando, esegui il comando [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) per visualizzare l'URL della tua applicazione. Vai quindi all'URL nel tuo browser.

## Passi successivi
{: #next-steps-startkit-kube notoc}

* Se riscontri degli errori con la distribuzione, controlla l'argomento di risoluzione dei problemi per i problemi noti come [exceeding storage quota](/docs/apps/ts_apps.html#exceed_quota) o scopri come [accedere ai log Kubernetes](/docs/apps/ts_apps.html#access_kube_logs) per cercare gli errori.

* Accedi alla configurazione del servizio nel tuo codice:
	- Puoi utilizzare l'annotazione _@Value_ oppure utilizzare il metodo _getProperty()_ della classe dell'ambiente framework Spring. Per ulteriori informazioni, vedi [Accesso alle credenziali](/docs/java-spring/configuration.html#configuration#accessing-credentials).

* Aggiungi nuove credenziali al tuo ambiente Kubernetes:
	- Quando aggiungi un altro servizio alla tua applicazione dopo che è stata creata la toolchain DevOps, queste credenziali di servizio non vengono aggiornate automaticamente alla tua applicazione distribuita e al tuo repository GitLab. Devi [aggiungere manualmente le credenziali](/docs/apps/creds_kube.html#sk_kube) all'ambiente di distribuzione.
