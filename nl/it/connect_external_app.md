---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-05"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{: tip: .tip}

# Collegare i servizi alle applicazioni esterne
{: #externalapp}

Potresti disporre di applicazioni create ed eseguite
all'esterno di {{site.data.keyword.Bluemix_notm}},
o utilizzare strumenti di terze parti. Se i servizi {{site.data.keyword.Bluemix_notm}} forniscono chiavi del servizio accessibili da Internet, puoi utilizzare questi servizi con le tue applicazioni locali e con gli strumenti di terze parti.

I seguenti servizi forniscono le chiavi del servizio per l'utilizzo esterno:

* {{site.data.keyword.alertnotificationshort}} <!--Alert Notification-->
* {{site.data.keyword.sparks}} <!--Analytics for Apache Spark-->
* {{site.data.keyword.blockchain}} <!--Blockchain-->
* {{site.data.keyword.cloudant}} <!--Cloudant&reg; NoSQL DB-->
* {{site.data.keyword.conversationshort}} <!--Conversation-->
* {{site.data.keyword.discoveryshort}} <!--Discovery-->
* {{site.data.keyword.geospatialshort_Geospatial}} <!--Geospatial Analytics-->
* {{site.data.keyword.GlobalizationPipeline_short}} <!--Globalization Pipeline-->
* {{site.data.keyword.appconserviceshort}} <!--IBM&reg; App Connect-->
* {{site.data.keyword.languagetranslatorshort}} <!--Language Translator-->
* {{site.data.keyword.dwl_short}} <!--Lift-->
* {{site.data.keyword.messagehub}} <!--Message Hub-->
* {{site.data.keyword.nlclassifiershort}} <!--Natural Language Classifier-->
* {{site.data.keyword.objectstorageshort}} <!--Object Storage-->
* {{site.data.keyword.personalityinsightsshort}} <!--Personality Insights-->
* {{site.data.keyword.mobilepush}} <!--Push-->
* {{site.data.keyword.speechtotextshort}} <!-- Speech to Text-->
* {{site.data.keyword.streaminganalyticsshort}} <!--Streaming Analytics-->
* {{site.data.keyword.texttospeechshort}} <!--Text to Speech-->
* {{site.data.keyword.toneanalyzershort}} <!--Tone Analyzer-->
* {{site.data.keyword.weather_short}} <!--Weather Company Data-->
* {{site.data.keyword.workloadscheduler}} <!--Workload Scheduler-->

Per abilitare un'applicazione esterna o uno strumento di terze parti a utilizzare un servizio {{site.data.keyword.Bluemix_notm}}, completa la seguente procedura:

1. Crea un'istanza del servizio.
    1. Fai clic su **Catalogo**.
    2. Dal catalogo, seleziona il servizio che vuoi facendo clic sul relativo tile. 
    3. Seleziona l'ubicazione e l'organizzazione e lo spazio o il gruppo di risorse, quindi fai clic su **Crea**.
2. Dalla pagina dei dettagli del servizio, seleziona **Credenziali del servizio** per visualizzare o aggiungere le credenziali nel formato JSON. 
    * Per creare nuove credenziali, seleziona **Nuova credenziale** e facoltativamente aggiungi i parametri di configurazione manualmente o importa un file in formato JSON, quindi fai clic su **Aggiungi**. Seleziona **Visualizza credenziali** per salvare le credenziali per il collegamento alla tua applicazione esterna.
    * Seleziona un insieme di credenziali e fai clic su **Visualizza credenziali** nella colonna Azioni se già esiste.  
3. Utilizza la chiave API visualizzata come credenziali per stabilire una
connessione all'istanza del servizio.

La tua applicazione che viene eseguita esternamente a {{site.data.keyword.Bluemix_notm}} può ora accedere al servizio {{site.data.keyword.Bluemix_notm}}.

Se vuoi eliminare delle istanze del servizio oppure controllare le informazioni di fatturazione, devi tornare indietro al Dashboard nell'interfaccia utente per gestire le istanze del servizio.
{: tip}
