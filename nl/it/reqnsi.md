---

copyright:
  years: 2015, 2018
lastupdated: "2018-08-27"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}

# Aggiunta di un servizio alla tua applicazione
{: #add_service}

Quando crei un'applicazione con {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.dev_console}}, puoi aggiungere risorse dalla pagina di panoramica dell'applicazione. Tuttavia, puoi anche fornirle direttamente dal catalogo {{site.data.keyword.Bluemix_notm}}, fuori dal contesto della tua applicazione.
{: shortdesc}

Puoi richiedere un'istanza della risorsa e utilizzarla indipendentemente dalla tua applicazione o puoi aggiungere l'istanza della risorsa alla tua applicazione dalla pagina della panoramica dell'applicazione. Puoi fornire un particolare tipo di risorsa (un servizio) direttamente dal catalogo {{site.data.keyword.Bluemix_notm}}.

## Rilevamento servizi
{: #discover_services}

Puoi visualizzare tutti i servizi disponibili in {{site.data.keyword.Bluemix_notm}}
nei seguenti modi:

* Dalla console {{site.data.keyword.Bluemix_notm}}. Visualizza il catalogo {{site.data.keyword.Bluemix_notm}}.
* Dall'interfaccia della riga di comando ibmcloud. Utilizza il comando `ibmcloud service offerings`.
* Dalla tua applicazione. Utilizza l'[API di servizi GET /v2/services ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window}.

Puoi selezionare il servizio di cui hai bisogno quando sviluppi le applicazioni. Una volta selezionato, {{site.data.keyword.Bluemix_notm}} esegue il provisioning del servizio. Il processo di provisioning può essere diverso per i diversi tipi di servizi. Ad esempio, un servizio database crea un database e un
servizio di notifiche di push per le applicazioni mobili genera le informazioni di configurazione.

{{site.data.keyword.Bluemix_notm}} fornisce le risorse di un servizio alla tua applicazione utilizzando un'istanza del servizio. Un'istanza del servizio può essere condivisa tra le
applicazioni Web.

Se vi sono dei servizi disponibili in altre regioni, potrai utilizzare anche tali
servizi. Questi servizi devono essere accessibili da Internet e avere degli endpoint API. Per utilizzare
questi servizi, devi codificare manualmente l'applicazione nello stesso modo in cui codifichi le applicazioni
esterne o gli strumenti di terze parti per utilizzare i servizi {{site.data.keyword.Bluemix_notm}}. Per ulteriori informazioni, vedi [Abilitazione di applicazioni esterne e strumenti di terze parti all'utilizzo di servizi {{site.data.keyword.Bluemix_notm}}](#accser_external).

## Richiesta di una nuova istanza del servizio
{: #req_instance}

Per richiedere una nuova istanza del servizio, devi utilizzare l'interfaccia utente di {{site.data.keyword.Bluemix_notm}} o l'interfaccia della riga di comando {{site.data.keyword.Bluemix_notm}}.

**Nota:** quando specifichi il nome del servizio, evita caratteri diversi dai caratteri alfabetici o numerici, altrimenti i risultati potrebbero essere imprevedibili.

Se utilizzi l'interfaccia utente di {{site.data.keyword.Bluemix_notm}}
per richiedere un'istanza del servizio, completa la seguente procedura:

1. Nel catalogo {{site.data.keyword.Bluemix_notm}}, fai clic sul tile del servizio che desideri aggiungere. Viene visualizzata la pagina dei dettagli.

2. Immetti un nome nel campo **Nome servizio**. Viene fornito un nome predefinito. Puoi modificare il nome nel campo o lasciarlo invariato.

3. Completa le selezioni o i campi aggiuntivi e fai quindi clic su **CREA**.

Se utilizzi l'interfaccia della riga di comando {{site.data.keyword.Bluemix_notm}} per richiedere un'istanza del servizio, scarica la tua applicazione localmente, apri la riga di comando e modifica la directory app.

1. Immetti il seguente comando per aggiungere un servizio alla tua applicazione. Puoi selezionare un servizio esistente da uno già abilitato sul tuo account o aggiungerne uno nuovo.

  ```bash
  ibmcloud dev edit
  ```
  {: pre}

2. Segui le istruzioni per selezionare un gruppo di risorse e per creare e collegare un nuovo servizio correlato ai dati alla tua applicazione, ad esempio Cloudant. Potresti dover selezionare una regione e un piano per il servizio.
3. Quando il servizio viene creato, diversi file, incluse le credenziali, vengono aggiunti alla directory dell'applicazione per facilitarti ad integrare il servizio nella tua applicazione. Puoi unire manualmente tutti file o ignorare questo passo per ora.

Puoi eseguire il bind a un'istanza del servizio per le sole istanze dell'applicazione che si trovano nello stesso spazio od organizzazione. Tuttavia, puoi utilizzare istanze di servizio provenienti da altri spazi od organizzazioni seguendo le modalità adottate dalle applicazioni esterne. Invece di creare un bind, utilizza le credenziali per configurare direttamente l'istanza della tua applicazione. Per ulteriori informazioni sull'uso dei servizi {{site.data.keyword.Bluemix_notm}} da parte delle applicazioni esterne, vedi [Abilitazione di applicazioni esterne all'utilizzo dei servizi {{site.data.keyword.Bluemix_notm}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](#accser_external){: new_window}.

## Configurazione della tua applicazione
{: #config}

Dopo aver eseguito il bind di un'istanza del servizio all'applicazione, devi configurare
l'applicazione in modo da interagire con il servizio.

Ciascun servizio potrebbe richiedere un meccanismo differente per comunicare con le applicazioni. Questi
meccanismi sono documentati come parte della definizione del servizio a scopo informativo quando sviluppi le
applicazioni. Per congruenza, i meccanismi sono richiesti perché la tua applicazione interagisca con il
servizio.

* Per interagire con i servizi del database, utilizza le informazioni fornite da {{site.data.keyword.Bluemix_notm}}, quali ID utente, password
e l'URI di accesso per l'applicazione.
* Per interagire con i servizi di back-end mobili, utilizza le informazioni fornite da {{site.data.keyword.Bluemix_notm}}, quali l'identità dell'applicazione
(ID applicazione), le informazioni di sicurezza specifiche per il client e l'URI di accesso per
l'applicazione. I servizi mobili funzionano spesso in contesto reciproco in modo che le informazioni di contesto, come il nome dello sviluppatore dell'applicazione e l'utente che utilizza l'applicazione, possano essere condivise tra la serie di servizi.
* Per interagire con le applicazioni Web o il codice cloud lato server per le applicazioni mobili, utilizza le
informazioni fornite da {{site.data.keyword.Bluemix_notm}}, quali le
credenziali di runtime nella variabile di ambiente *VCAP_SERVICES*
dell'applicazione. Il valore della variabile di ambiente *VCAP_SERVICES* è la
serializzazione di un oggetto JSON. La variabile contiene i dati di runtime richiesti per interagire con i servizi
a cui è associata l'applicazione. Il formato dei dati è differente per i
diversi servizi. Potresti dover leggere la documentazione del servizio in merito a cosa aspettarsi
e come interpretare ogni elemento di informazione.

Se si verifica un arresto anomalo di un servizio di cui esegui il bind a un'applicazione,
l'esecuzione dell'applicazione potrebbe essere arrestata oppure potrebbero verificarsi per essa delle condizioni di errore. {{site.data.keyword.Bluemix_notm}} non riavvia automaticamente l'applicazione per eseguire un ripristino da tali problemi. Valuta una codifica della tua applicazione per identificare interruzioni, eccezioni ed errori di connessione e per eseguire il ripristino da tali condizioni. Per ulteriori informazioni, vedi [Le applicazioni non si riavviano automaticamente](/docs/troubleshoot/ts_apps.html#ts_apps_not_auto_restarted).

## Accesso ai servizi negli ambienti di distribuzione di {{site.data.keyword.Bluemix_notm}}
{: #migrate_instance}

{{site.data.keyword.Bluemix_notm}} offre molte opzioni di distribuzione e puoi accedere a un servizio in esecuzione in un ambiente da un ambiente diverso. Ad esempio, se hai un servizio in esecuzione in Cloud Foundry, puoi accedere a tale servizio da un'applicazione che è in esecuzione in un cluster Kubernetes.

### Esempio: accesso a un servizio Cloud Foundry da un pod Kubernetes

Per accedere a un servizio Cloud Foundry da un pod in un cluster Kubernetes, devi eseguire il bind del servizio al tuo cluster per memorizzare le credenziali del servizio in un segreto Kubernetes. Quindi, puoi rendere queste informazioni disponibili alla tua applicazione. 
{: shortdesc}

Le credenziali del servizio memorizzate in un segreto Kubernetes sono codificate in base64 e crittografate in etcd per impostazione predefinita. 

**Importante**: non indicare o esporre le credenziali del servizio direttamente nel tuo file YAML di distribuzione. I file YAML di distribuzione non sono progettati per contenere dati sensibili e non crittografano le credenziali del servizio per impostazione predefinita. Per memorizzare e accedere correttamente a queste informazioni, devi utilizzare un segreto Kubernetes. 

1. [Esegui il bind del servizio al tuo cluster](/docs/containers/cs_integrations.html#adding_cluster). 
2. Per accedere alle credenziali del servizio dal tuo pod dell'applicazione, scegli tra le seguenti opzioni. 
   - [Monta il segreto come volume sul tuo pod](#mount_secret)
   - [Fai riferimento al segreto nelle variabili di ambiente](#reference_secret)

## Abilitazione di applicazioni esterne
{: #accser_external}

Potresti disporre di applicazioni create ed eseguite
all'esterno di {{site.data.keyword.Bluemix_notm}},
o utilizzare strumenti di terze parti. Se i servizi {{site.data.keyword.Bluemix_notm}} forniscono chiavi del servizio accessibili da Internet, puoi utilizzare questi servizi con le tue applicazioni locali e con gli strumenti di terze parti.

I seguenti servizi forniscono le chiavi del servizio per l'utilizzo esterno:

* {{site.data.keyword.amashort_old}} <!--Advanced Mobile Access-->
* {{site.data.keyword.alchemyapishort}} <!--AlchemyAPI-->
* {{site.data.keyword.alertnotificationshort}} <!--Alert Notification-->
* {{site.data.keyword.sparks}} <!--Analytics for Apache Spark-->
* {{site.data.keyword.appseccloudshort}} <!--Application Security on Cloud-->
* {{site.data.keyword.blockchain}} <!--Blockchain-->
* {{site.data.keyword.cloudant}} <!--Cloudant&reg; NoSQL DB-->
* {{site.data.keyword.iotmapinsights_short}} <!--Context Mapping-->
* {{site.data.keyword.conversationshort}} <!--Conversation-->
* {{site.data.keyword.dashdbshort}} <!--dashDB-->
* {{site.data.keyword.discoveryshort}} <!--Discovery-->
* {{site.data.keyword.documentconversionshort}} <!--Document Conversion-->
* {{site.data.keyword.iotdriverinsights_short}} <!--Driver Behavior-->
* {{site.data.keyword.geospatialshort_Geospatial}} <!--Geospatial Analytics-->
* {{site.data.keyword.GlobalizationPipeline_short}} <!--Globalization Pipeline-->
* {{site.data.keyword.appconserviceshort}} <!--IBM&reg; App Connect-->
* {{site.data.keyword.dataworks_short}} <!--IBM&reg; Data Connect-->
* {{site.data.keyword.graphshort}} <!--IBM&reg; Graph-->
* {{site.data.keyword.iotelectronics_full}} <!--IBM&reg; IoT for Electronics-->
* {{site.data.keyword.twittershort}} <!--Insights for Twitter-->
* {{site.data.keyword.iot4auto_short}} <!--IoT for Automotive-->
* {{site.data.keyword.iotinsurance_short}} <!--IoT for Insurance-->
* {{site.data.keyword.languagetranslatorshort}} <!--Language Translator-->
* {{site.data.keyword.dwl_short}} <!--Lift-->
* {{site.data.keyword.messagehub}} <!--Message Hub-->
* {{site.data.keyword.mobileanalytics_short}} <!--Mobile Analytics-->
* {{site.data.keyword.nlclassifiershort}} <!--Natural Language Classifier-->
* {{site.data.keyword.objectstorageshort}} <!--Object Storage-->
* {{site.data.keyword.personalityinsightsshort}} <!--Personality Insights-->
* {{site.data.keyword.HybridConnect_short}} <!--Product Insights-->
* {{site.data.keyword.mobilepush}} <!--Push-->
* {{site.data.keyword.retrieveandrankshort}} <!--Retrieve and Rank-->
* {{site.data.keyword.speechtotextshort}} <!-- Speech to Text-->
* {{site.data.keyword.streaminganalyticsshort}} <!--Streaming Analytics-->
* {{site.data.keyword.texttospeechshort}} <!--Text to Speech-->
* {{site.data.keyword.toneanalyzershort}} <!--Tone Analyzer-->
* {{site.data.keyword.tradeoffanalyticsshort}} <!--Tradeoff Analytics-->
* {{site.data.keyword.weather_short}} <!--Weather Company Data-->
* {{site.data.keyword.workloadscheduler}} <!--Workload Scheduler-->

Per abilitare un'applicazione esterna o uno strumento di terze parti
a utilizzare un servizio {{site.data.keyword.Bluemix_notm}},
completa la seguente procedura:

1. Richiedi un'istanza del servizio.
    1. Nel Dashboard dell'interfaccia utente di {{site.data.keyword.Bluemix_notm}}, fai clic su **Crea risorsa**. Viene visualizzato il catalogo.
    2. Dal catalogo, seleziona il servizio che vuoi facendo clic sul relativo tile. Viene visualizzata la pagina dei dettagli.
    3. Nella finestra del servizio, lascia la selezione predefinita dell'elenco **Connetti a:**: su **Lascia senza binding**. Questa selezione significa che il servizio non viene connesso a un'applicazione {{site.data.keyword.Bluemix_notm}}.
    4. Opera le altre selezioni come necessario. Quindi, fai clic su **Crea**. Viene creata un'istanza del servizio e viene visualizzato il dashboard del servizio.
2. Nel Dashboard del servizio, puoi selezionare **Credenziali del servizio** per visualizzare o aggiungere credenziali in formato JSON. Seleziona un insieme di credenziali e fai clic su **Visualizza credenziali** nella colonna Azioni. Utilizza la chiave API visualizzata come credenziali per stabilire una
connessione all'istanza del servizio.

La tua applicazione che viene eseguita esternamente a {{site.data.keyword.Bluemix_notm}} può
ora accedere al servizio {{site.data.keyword.Bluemix_notm}}.

**Nota:** se vuoi eliminare delle istanze del servizio oppure controllare le informazioni di fatturazione, devi tornare indietro al Dashboard nell'interfaccia utente per gestire le istanze del servizio.

## Creazione di un'istanza del servizio fornito dall'utente
{: #user_provide_services}

Puoi avere dei servizi che sono gestiti esternamente a {{site.data.keyword.Bluemix_notm}}. Se hai delle credenziali per accedere a questi servizi esterni da internet, puoi creare delle istanze del servizio fornito dall'utente {{site.data.keyword.Bluemix_notm}} per rappresentare le risorse esterne e comunicare con esse.

Per creare un'istanza del servizio fornito dall'utente ed eseguirne il bind a un'applicazione, completa la seguente procedura:

1. Crea un'istanza del servizio fornito dall'utente utilizzando il comando `ibmcloud service user-provided-create`:
    * Per creare un'istanza del servizio fornito dall'utente generale, utilizza l'opzione **-p** e
separa i nomi parametro con delle virgole. L'interfaccia riga di comando `ibmcloud` ti richiede quindi ciascun parametro alla volta. Ad esempio:
        ```
        ibmcloud service user-provided-create testups1 -p "host, port, dbname, username, password"
        host> pubsub01.example.com
        port> 1234
        dbname> sampledb01
        username> pubsubuser
        password> p@$$w0rd
        Creating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * Per creare un'istanza del servizio che scarica informazioni in un software di gestione di log di terze parti, utilizza l'opzione `-l`. Specifica la destinazione fornita dal software di gestione dei log di terze parti. Ad esempio:

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example.com
        Creating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

    Se vuoi aggiornare uno o più parametri dell'istanza del servizio fornito dall'utente, utilizza il comando `ibmcloud service user-provided-update`.

    * Per aggiornare un'istanza del servizio fornito dall'utente, utilizza l'opzione **-p**
e specifica le chiavi e i valori di parametro in un oggetto JSON. Ad esempio:

        ```
        ibmcloud service user-provided-update testups1 -p "{\"username\":\"pubsubuser2\",\"password\":\"p@$$w0rd2\"}"
        Updating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * Per creare un'istanza del servizio che scarica informazioni in un software di gestione di log di terze parti, utilizza l'opzione `-l`. Ad esempio:

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example2.com
        Updating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

2. Esegui il bind dell'istanza del servizio alla tua applicazione utilizzando il comando `ibmcloud service bind`. Ad esempio:

	```
	ibmcloud service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

Ora puoi configurare la tua applicazione per utilizzare i servizi esterni. Per informazioni su come configurare la tua applicazione per interagire con un servizio, vedi [Configurazione della tua applicazione per l'interazione con un servizio ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](#config){: new_window}.

