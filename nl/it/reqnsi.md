---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-15"

keywords: apps, services, add service, application

subcollection: creating-apps

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{:note: .note}

# Aggiunta di un servizio alla tua applicazione
{: #add-resource}

Quando crei un'applicazione con {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}, puoi aggiungere i servizi dalla pagina App details. Tuttavia, puoi anche fornirle direttamente dal catalogo {{site.data.keyword.cloud_notm}}, fuori dal contesto della tua applicazione.
{: shortdesc}

Puoi richiedere un'istanza del servizio e utilizzarla indipendentemente dalla tua applicazione o puoi aggiungere l'istanza del servizio alla tua applicazione dalla pagina App details. Puoi eseguire il provisioning di uno specifico tipo di servizio direttamente dal catalogo {{site.data.keyword.cloud_notm}}.

## Rilevamento del servizio 
{: #discover-resources}

Puoi visualizzare tutti i servizi disponibili in {{site.data.keyword.cloud_notm}}
nei seguenti modi:

* Dalla console {{site.data.keyword.cloud_notm}}. Visualizza il catalogo {{site.data.keyword.cloud_notm}}.
* Dalla riga di comando. Utilizza il comando `ibmcloud service offerings`.
* Dalla tua applicazione. Utilizza l'[API di servizi GET /v2/services ](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno").

Puoi selezionare il servizio di cui hai bisogno quando sviluppi le applicazioni. Una volta selezionato, {{site.data.keyword.cloud_notm}} esegue il provisioning del servizio. Il processo di provisioning può essere diverso per i diversi tipi di servizi. Ad esempio, un servizio database crea un database e un
servizio di notifiche di push per le applicazioni mobili genera le informazioni di configurazione.

{{site.data.keyword.cloud_notm}} fornisce le risorse di un servizio alla tua applicazione utilizzando un'istanza del servizio. Un'istanza del servizio può essere condivisa tra le
applicazioni Web.

Se vi sono dei servizi disponibili in altre regioni, potrai utilizzare anche tali
servizi. Questi servizi devono essere accessibili da Internet e avere degli endpoint API. Per utilizzare
questi servizi, devi codificare manualmente l'applicazione nello stesso modo in cui codifichi le applicazioni
esterne o gli strumenti di terze parti per utilizzare i servizi {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, consulta [Collegare i servizi alle applicazioni esterne](/docs/resources?topic=resources-externalapp).

## Richiesta di una nuova istanza del servizio
{: #request-instance}

Per richiedere una nuova istanza del servizio, devi utilizzare l'interfaccia utente di {{site.data.keyword.cloud_notm}} o l'interfaccia della riga di comando {{site.data.keyword.cloud_notm}}.

Quando specifichi il nome del servizio, evita caratteri diversi dai caratteri alfabetici o numerici, altrimenti i risultati potrebbero essere imprevedibili.
{: note}

Se utilizzi l'interfaccia utente di {{site.data.keyword.cloud_notm}}
per richiedere un'istanza del servizio, completa la seguente procedura:

1. Nel catalogo {{site.data.keyword.cloud_notm}}, fai clic sul tile del servizio che desideri aggiungere. Viene visualizzata la pagina dei dettagli.

2. Immetti un nome nel campo **Nome servizio**. Viene fornito un nome predefinito. Puoi modificare il nome nel campo o lasciarlo invariato.

3. Completa le selezioni o i campi aggiuntivi e fai quindi clic su **CREA**.

Se utilizzi l'interfaccia della riga di comando {{site.data.keyword.cloud_notm}} per richiedere un'istanza del servizio, scarica la tua applicazione localmente, apri la riga di comando e modifica la directory app.

1. Immetti il seguente comando per aggiungere un servizio alla tua applicazione. Puoi selezionare un servizio esistente da uno già abilitato sul tuo account o aggiungerne uno nuovo.

  ```bash
  ibmcloud dev edit
  ```
  {: pre}

2. Segui le istruzioni per selezionare un gruppo di risorse e per creare e collegare un nuovo servizio correlato ai dati alla tua applicazione, ad esempio Cloudant. Potresti dover selezionare una regione e un piano per il servizio.
3. Quando il servizio viene creato, diversi file, incluse le credenziali, vengono aggiunti alla directory dell'applicazione per facilitarti ad integrare il servizio nella tua applicazione. Puoi unire manualmente tutti file o ignorare questo passo per ora.

Puoi eseguire il bind a un'istanza del servizio per le sole istanze dell'applicazione che si trovano nello stesso spazio od organizzazione. Tuttavia, puoi utilizzare istanze di servizio provenienti da altri spazi od organizzazioni seguendo le modalità adottate dalle applicazioni esterne. Invece di creare un bind, utilizza le credenziali per configurare direttamente l'istanza della tua applicazione. Per ulteriori informazioni sull'uso dei servizi {{site.data.keyword.cloud_notm}} da parte delle applicazioni esterne, vedi [Abilitazione di applicazioni esterne all'utilizzo dei servizi {{site.data.keyword.cloud_notm}} ](/docs/resources?topic=resources-externalapp#externalapp).

## Configurazione della tua applicazione
{: #configure-app}

Dopo aver eseguito il bind di un'istanza del servizio all'applicazione, devi configurare
l'applicazione in modo da interagire con il servizio.

Ciascun servizio potrebbe richiedere un meccanismo differente per comunicare con le applicazioni. Questi
meccanismi sono documentati come parte della definizione del servizio a scopo informativo quando sviluppi le
applicazioni. Per congruenza, i meccanismi sono richiesti perché la tua applicazione interagisca con il
servizio.

* Per interagire con i servizi del database, utilizza le informazioni fornite da {{site.data.keyword.cloud_notm}}, quali ID utente, password
e l'URI di accesso per l'applicazione.
* Per interagire con i servizi di backend mobili, utilizza le informazioni fornite da {{site.data.keyword.cloud_notm}}, quali l'identità dell'applicazione
(ID applicazione), le informazioni di sicurezza specifiche per il client e l'URI di accesso per
l'applicazione. I servizi mobili funzionano spesso in contesto reciproco in modo che le informazioni di contesto, come il nome dello sviluppatore dell'applicazione e l'utente che utilizza l'applicazione, possano essere condivise tra la serie di servizi.
* Per interagire con le applicazioni Web o il codice cloud lato server per le applicazioni mobili, utilizza le
informazioni fornite da {{site.data.keyword.cloud_notm}}, quali le
credenziali di runtime nella variabile di ambiente *VCAP_SERVICES*
dell'applicazione. Il valore della variabile di ambiente *VCAP_SERVICES* è la
serializzazione di un oggetto JSON. La variabile contiene i dati di runtime richiesti per interagire con i servizi
a cui è associata l'applicazione. Il formato dei dati è differente per i
diversi servizi. Potresti dover leggere la documentazione del servizio in merito a cosa aspettarsi
e come interpretare ogni elemento di informazione.

Se si verifica un arresto anomalo di un servizio di cui esegui il bind a un'applicazione,
l'esecuzione dell'applicazione potrebbe essere arrestata oppure potrebbero verificarsi per essa delle condizioni di errore. {{site.data.keyword.cloud_notm}} non riavvia automaticamente l'applicazione per eseguire un ripristino da tali problemi. Valuta una codifica della tua applicazione per identificare interruzioni, eccezioni ed errori di connessione e per eseguire il ripristino da tali condizioni. Per ulteriori informazioni, vedi [Le applicazioni non si riavviano automaticamente](/docs/apps/troubleshoot?topic=creating-apps-managingapps#ts_apps_not_auto_restarted).

## Accesso ai servizi negli ambienti di distribuzione di {{site.data.keyword.cloud_notm}}
{: #migrate_instance}

{{site.data.keyword.cloud_notm}} offre molte opzioni di distribuzione e puoi accedere a un servizio in esecuzione in un ambiente da un ambiente diverso. Ad esempio, se hai un servizio in esecuzione in Cloud Foundry, puoi accedere a tale servizio da un'applicazione che è in esecuzione in un cluster Kubernetes.

### Esempio: accesso a un servizio Cloud Foundry da un pod Kubernetes

Per accedere a un servizio Cloud Foundry da un pod in un cluster Kubernetes, devi eseguire il bind del servizio al tuo cluster per memorizzare le credenziali del servizio in un segreto Kubernetes. Quindi, puoi rendere queste informazioni disponibili alla tua applicazione. 
{: shortdesc}

Le credenziali del servizio memorizzate in un segreto Kubernetes sono codificate in base64 e crittografate in etcd per impostazione predefinita. 

**Importante**: non indicare o esporre le credenziali del servizio direttamente nel tuo file YAML di distribuzione. I file YAML di distribuzione non sono progettati per contenere dati sensibili e non crittografano le credenziali del servizio per impostazione predefinita. Per memorizzare e accedere correttamente a queste informazioni, devi utilizzare un segreto Kubernetes. 

1. [Esegui il bind del servizio al tuo cluster](/docs/containers?topic=containers-integrations#adding_cluster). 
2. Per accedere alle credenziali del servizio dal tuo pod dell'applicazione, scegli tra le seguenti opzioni. 
   - Monta il segreto come un volume al tuo pod
   - Fai riferimento al segreto nelle variabili di ambiente

## Creazione di un'istanza del servizio fornito dall'utente
{: #user_provide_services}

Puoi avere dei servizi che sono gestiti esternamente a {{site.data.keyword.cloud_notm}}. Se hai delle credenziali per accedere a questi servizi esterni da internet, puoi creare delle istanze del servizio fornito dall'utente {{site.data.keyword.cloud_notm}} per rappresentare le risorse esterne e comunicare con esse.

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

Ora puoi configurare la tua applicazione per utilizzare i servizi esterni. Per informazioni su come configurare la tua applicazione per interagire con un servizio, vedi [Configurazione della tua applicazione per l'interazione con un servizio](/docs/apps?topic=creating-apps-add-resource#configure-app).
