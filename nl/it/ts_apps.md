---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-17"

keywords: apps, application, troubleshooting, debug apps, known issues, debug, help, configuration, app, troubleshoot, error, errors, failure, failed, fail, issues, applications

subcollection: creating-apps

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Risoluzione dei problemi relativi alla creazione delle applicazioni
{: #managingapps}

I problemi generali con la creazione delle applicazioni potrebbero includere applicazioni che non possono essere aggiornate o caratteri double-byte che non vengono visualizzati. In molti casi, puoi risolvere questi problemi seguendo pochi semplici passi.
{:shortdesc}

## Le mie applicazioni sono ospitate in domini diversi
{: #domains-ts}
{: troubleshoot}

Alcune delle mie applicazioni sono ospitate nel dominio `mybluemix.net`, ma altre nel dominio `appdomain.cloud`.

Le mie applicazioni esistenti sono ospitate nel dominio `mybluemix.net`, ma le applicazioni più recenti sono ospitate nel dominio `appdomain.cloud`.
{: tsSymptoms}

È disponibile una nuova opzione di nome host `*.appdomain.cloud` su cloud.ibm.com.

In precedenza, il dominio `mybluemix.net` veniva utilizzato per ospitare le applicazioni in varie destinazioni di distribuzione, ad esempio {{site.data.keyword.containerlong_notm}} o Cloud Foundry. Tutte le applicazioni che hai ospitato su `mybluemix.net` non sono interessate.

Il dominio secondario per le applicazioni Cloud Foundry è `cf.appdomain.cloud`. Il dominio secondario per le applicazioni che distribuisci a {{site.data.keyword.containerlong_notm}} è `containers.appdomain.cloud`.

Per ulteriori informazioni, vedi [Gestione dei tuoi domini](/docs/apps?topic=creating-apps-update-domain).

## Non hai salvato delle modifiche
{: #ts_unsaved_changes}
{: troubleshoot}

Quando fai clic sugli elementi nella pagina dei dettagli dell'applicazione, potresti non essere in grado di eseguire alcuna azione. Ti potrebbe anche essere richiesto di salvare le modifiche prima di poter continuare.

Quando provi a controllare la tua applicazione o i tuoi servizi nella pagina dei dettagli dell'applicazione, viene visualizzato il seguente messaggio di errore:
{: tsSymptoms}

`You have unsaved changes. Are you sure you want to leave this page?`

Quando passi il puntatore del tuo mouse sui campi **ISTANZE** o **QUOTA DI MEMORIA** nel riquadro di runtime, i valori cambiano. Questa è la modalità di funzionamento prevista. Tuttavia, ti viene richiesto di salvare le impostazioni di memoria o istanza prima di andare a un'altra pagina.
{: tsCauses}

Chiudi la finestra del messaggio e fai clic su **REIMPOSTA** nel tuo riquadro di runtime.
{: tsResolve}

## Impossibile accedere ai servizi {{site.data.keyword.cloud_notm}} a causa di errori di autorizzazione
{: #ts_vcap}
{: troubleshoot}

Gli errori di autorizzazione potrebbero verificarsi quando la tua applicazione accede a un servizio {{site.data.keyword.cloud_notm}} e le credenziali del servizio sono hardcoded nell'applicazione.

Dopo aver configurato l'applicazione per comunicare con un servizio {{site.data.keyword.cloud_notm}}, distribuisci l'applicazione a {{site.data.keyword.cloud_notm}}. Tuttavia, non riesci a utilizzare l'applicazione per accedere al servizio {{site.data.keyword.cloud_notm}} e ricevi un messaggio di errore.
{: tsSymptoms}

Le credenziali hardcoded nell'applicazione potrebbero non essere corrette. Ogni volta che il servizio viene ricreato, le credenziali per accedervi cambiano.
{: tsCauses}

Invece di impostare come hardcoded le credenziali nella tua applicazione, utilizza i parametri di connessione dalla variabile di ambiente VCAP_SERVICES. I metodi per utilizzare i parametri di connessione dalla variabile di ambiente VCAP_SERVICES variano a seconda dei linguaggi di programmazione. Ad esempio, per le applicazioni Node.js, puoi utilizzare il seguente comando:
{: tsResolve}

```
process.env.VCAP_SERVICES
```

Per ulteriori informazioni sui comandi che puoi utilizzare in altri linguaggi di programmazione, vedi [Java ](https://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") e [Ruby ](https://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno").

## Ricezione di errori 502 Bad Gateway
{: #ts_502_error}
{: troubleshoot}

Se ricevi degli errori `502 Bad Gateway` quando interagisci con le applicazioni in {{site.data.keyword.cloud_notm}}, controlla la pagina dello stato {{site.data.keyword.cloud_notm}} ed esegui quindi le azioni appropriate.

Ricevi dei messaggi di errore che iniziano con 502 Bad Gateway. Ad esempio, potresti vedere `502 Bad Gateway: Registered endpoint failed to handle the request.`
{: tsSymptoms}

Un errore Bad Gateway di solito si verifica quando visiti un sito Web che utilizza un server proxy per memorizzare e inoltrare i dati dal server principale che ospita il sito. Il server principale e il server proxy potrebbero non connettersi correttamente. Pertanto visualizzi il codice di stato HTTP 502 nella finestra del
browser. Questo codice di stato indica che il server principale del sito non ha ricevuto l'implementazione HTTP prevista dal server proxy.
{: tsCauses}

Altre cause meno comuni di un errore Bad Gateway sono interruzioni ISP (Internet Service Provider), configurazioni firewall non valide ed errori della cache del browser.

Se sospetti che un servizio {{site.data.keyword.cloud_notm}} è inattivo, controlla prima la pagina [Stato {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/status){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno"). Una soluzione temporanea potrebbe essere quella di [utilizzare il servizio in un'altra regione {{site.data.keyword.cloud_notm}}](/docs/resources/connect_external_app?topic=resources-externalapp){: new_window}. Se lo stato del servizio è normale,
prova le seguenti operazioni per risolvere il problema:
{: tsResolve}

  * Ritenta l'azione:
    * Ricarica la pagina premendo F5 sulla tastiera o facendo clic su **Aggiorna**. Se questa operazione non funziona, cancella la cache e i cookie del tuo browser e ricarica di nuovo la pagina.
    * Utilizza un browser differente.
    * Riavvia il router, il modem e il computer. Il riavvio di questi
dispositivi può cancellare i diversi errori che portano all'errore 502.
  * Attendi e riprova in seguito. Possono verificarsi dei problemi temporanei con il tuo provider dei servizi internet o con i servizi {{site.data.keyword.cloud_notm}}. Puoi attendere finché i problemi non vengono risolti.
  * Se il problema persiste, contatta il supporto {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Come contattare il supporto {{site.data.keyword.cloud_notm}}](/docs/get-support?topic=get-support-getting-customer-support){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno").

## Le applicazioni Android non possono ricevere {{site.data.keyword.mobilepushshort}}
{: #ts_push}
{: troubleshoot}

In alcune regioni in cui Google non è accessibile, le applicazioni Android non possono ricevere le notifiche che invii tramite il servizio IBM {{site.data.keyword.mobilepushshort}}. In questo caso, una soluzione potrebbe consistere nell'utilizzare servizi di terze parti.

Esegui il bind di un servizio {{site.data.keyword.mobilepushshort}} per la tua applicazione {{site.data.keyword.cloud_notm}} e invii un messaggio ai dispositivi registrati. Tuttavia, le applicazioni sviluppate su Android non possono ricevere le tue notifiche in determinate regioni.
{: tsSymptoms}

Il servizio IBM {{site.data.keyword.mobilepushshort}} utilizza il servizio GCM (Google Cloud Messaging) per inviare notifiche alle applicazioni mobili sviluppate su Android. Per consentire alle applicazioni Android di ricevere le notifiche,
è necessario che il servizio GCM (Google Cloud Messaging) sia accessibile dalle applicazioni
mobili. Nelle regioni in cui le applicazioni Android non possono raggiungere il servizio GCM, tali applicazioni non potranno ricevere {{site.data.keyword.mobilepushshort}}.
{: tsCauses}

Come soluzione temporanea, utilizza servizi di terze parti che non si basano sul servizio GCM, ad esempio, [Pushy](https://pushy.me/){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") e [jpush](https://www.jiguang.cn/en/){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno").
{: tsResolve}

## I caratteri double-byte non vengono visualizzati correttamente quando si distribuiscono le applicazioni a {{site.data.keyword.cloud_notm}}
{: #ts_doublebytes}
{: troubleshoot}

I caratteri double-byte potrebbero non essere visualizzati correttamente se il supporto Unicode non è adeguatamente configurato per i file servlet o JSP.

Quando un'applicazione viene distribuita a {{site.data.keyword.cloud_notm}}, i caratteri double-byte specificati all'interno dell'applicazione non vengono visualizzati correttamente.
{: tsSymptoms}

Il problema può verificarsi se il supporto Unicode non è configurato correttamente per i file servlet o JSP.
{: tsCauses}

Puoi utilizzare il seguente codice nel tuo file servlet o JSP:
{: tsResolve}

  * Nel file di origine servlet
  ```java
	response.setContentType("text/html; charset=UTF-8");
	```
  {: codeblock}

  * Nel JSP
  ```jsp
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```
  {: codeblock}

## Impossibile distribuire le applicazioni Node.js
{: #ts_nodejs_deploy}
{: troubleshoot}

Potresti riscontrare dei problemi quando aggiorni un'applicazione Node.js o la distribuisci a {{site.data.keyword.cloud_notm}}.

Quando aggiorni un'applicazione Node.js o distribuisci la tua applicazione Node.js
a {{site.data.keyword.cloud_notm}},
potresti visualizzare uno dei seguenti messaggi di errore:
{: tsSymptoms}

`An app was not successfully detected by any available buildpack.`

`Instance (index 0) failed to start accepting connections.`

`Cannot get instances since staging failed.`

Di seguito sono riportate le cause possibili:
{: tsCauses}

  * Il comando di avvio non è specificato.
  * I file richiesti per distribuire un'applicazione Node.js non sono presenti nell'applicazione o si trovano in una cartella diversa dalla directory root.

Utilizza uno dei seguenti metodi in base alla causa del problema:
{: tsResolve}

  * Specifica il comando di avvio utilizzando uno dei seguenti metodi:
     * Utilizza l'interfaccia riga di comando Cloud Foundry. Ad esempio:
      ```
		  ibmcloud cf push MyUniqueNodejs01 -p app_path -c "node app.js"
		  ```
      {: codeblock}

    * Utilizza il file [package.json ](https://www.npmjs.com/package/jsonfile){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno"). Ad esempio:
	    ```json
		  {
        ...
  	    "scripts": {
	 		  "start": "node app.js"
 	   }
	    }
	    ```

    * Utilizza il file `manifest.yml`. Ad esempio:
	    ```
		  applications:
  name: MyUniqueNodejs01
  ...
      command: node app.js
  ...
      ```

  * Assicurati che nella tua applicazione Node.js sia presente un file  `package.json` in modo che il pacchetto di build Node.js possa riconoscere l'applicazione. Assicurati inoltre che questo file si trovi nella directory root della tua applicazione.
    Il seguente
                                                  esempio mostra un semplice file
                                                  `package.json`:
	```json
	{
        "name": "MyUniqueNodejs01",
        "version": "0.0.1",
        "description": "A sample package.json file",
        "dependencies": {
                "express": "3.4.x",
                "jade": "1.1.x"
        },
        "engines": {
                "node": "0.10.x"
        },
        "scripts": {
                  "start": "node app.js"
        }
 }
    ```

Per ulteriori suggerimenti relativi alle applicazioni Node.js, vedi [Tips for Node.js Applications ](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno").

## Sono presenti degli errori di configurazione nel file `server.xml` dopo aver importato un'applicazione {{site.data.keyword.cloud_notm}} Liberty in Eclipse
{: #ts_eclipse}
{: troubleshoot}

Se vedi degli errori di configurazione nel file `server.xml` dopo aver importato un'applicazione {{site.data.keyword.cloud_notm}} Liberty in Eclipse, potresti dover rimuovere il file `server.xml` dal progetto.

Dopo aver importato un'applicazione {{site.data.keyword.cloud_notm}} Liberty in Eclipse, vedi degli errori di configurazione nel file `server.xml` dalla vista Problemi di Eclipse.
{: tsSymptoms}

Il pacchetto di build Liberty utilizza il file `server.xml` per configurare l'applicazione e genera un file `runtime-vars.xml` quando viene eseguito il push dell'applicazione Liberty a {{site.data.keyword.cloud_notm}}. Quando importi l'applicazione in Eclipse, il file `runtime-vars.xml` non esiste nel tuo ambiente locale.
{: tsCauses}

Puoi risolvere questo problema rimuovendo il file server.xml dal progetto. Il pacchetto di build crea il file `server.xml` dinamicamente quando
esegui il push dell'applicazione come un'applicazione WAR. Per ulteriori informazioni, vedi [Liberty for Java](/docs/runtimes/liberty?topic=liberty-liberty_runtime#liberty_runtime).
{: tsResolve}

## Impossibile preparare l'applicazione utilizzando i pacchetti di build personalizzati
{: #ts_bp_compilation}
{: troubleshoot}

Potresti non riuscire a distribuire un'applicazione a {{site.data.keyword.cloud_notm}} con un pacchetto di build personalizzato se gli script in questo pacchetto non sono file eseguibili.

Quando distribuisci un'applicazione a {{site.data.keyword.cloud_notm}} con un pacchetto di build personalizzato, visualizzi il messaggio di errore `La preparazione dell'applicazione non è riuscita e, pertanto, non ci sono istanze da visualizzare.`
{: tsSymptoms}

Questo problema potrebbe verificarsi se gli script, ad esempio lo script di rilevamento, lo script di compilazione e lo script di rilascio, non sono eseguibili.
{: tsCauses}

Puoi utilizzare il comando [Git update ](https://git-scm.com/docs/git-update-index){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") per modificare l'autorizzazione di ciascuno script in eseguibile. Ad esempio, puoi immettere `git update --chmod=+x script.sh`.
{: tsResolve}

## Impossibile distribuire un'applicazione da Delivery Pipeline in {{site.data.keyword.cloud_notm}} Continuous Delivery
{: #ts_devops_to_bm}
{: troubleshoot}

 Potresti non riuscire a distribuire la tua applicazione con {{site.data.keyword.deliverypipeline}} in {{site.data.keyword.contdelivery_short}} se il file `manifest.yml` non è presente nella tua applicazione.

 Quando distribuisci un'applicazione con {{site.data.keyword.deliverypipeline}} in {{site.data.keyword.contdelivery_short}}, potresti visualizzare il messaggio di errore `Unable to detect a supported application type`.
 {: tsSymptoms}

 Questo problema potrebbe verificarsi perché la pipeline richiede un file `manifest.yml` per distribuire un'applicazione a {{site.data.keyword.cloud_notm}}.
 {: tsCauses}

 Per risolvere questo problema, devi creare un file `manifest.yml`. Per ulteriori informazioni su come creare un file `manifest.yml`,
vedi [Manifest
dell'applicazione](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest).
 {: tsResolve}

## Hai superato la tua quota di archiviazione
{: #exceed_quota}

Se i lavori di build o di distribuzione non riescono, e vedi il seguente messaggio, puoi eliminare le tue immagini con i seguenti comandi CLI. `Status: unauthorized: You have exceeded your storage quota. Delete one or more images, or review your storage quota and pricing plan.`

* Installa la [CLI {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-getting-started) se non lo hai ancora fatto.
* Accedi a {{site.data.keyword.cloud_notm}} utilizzando `ibmcloud login` e indica come sua destinazione lo spazio in cui ti trovi.
* Elenca le tue immagini utilizzando `ibmcloud cr images`.
* Elimina le eventuali immagini inutilizzate servendoti di `ibmcloud cr image-rm <respository>:<tag>`.
* Esegui nuovamente il lavoro di build o di distribuzione che non era riuscito.

## Accesso ai log Kubernetes
{: #access_kube_logs}

Se l'applicazione non è in esecuzione e non riesci ad accedere all'endpoint di integrità, prova a guardare i log nel cluster.
* Installa la [CLI {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-getting-started) se non lo hai ancora fatto.
* Accedi a {{site.data.keyword.cloud_notm}} utilizzando `ibmcloud login` e indica come sua destinazione lo spazio in cui ti trovi.
* Elenca i tuoi cluster utilizzando `ibmcloud cs clusters`,
* Indica come destinazione il tuo cluster corrispondente utilizzando `ibmcloud cs cluster-config <cluster-name>`.
* Esporta la variabile di ambiente che è elencata.
* Visualizza i tuoi pod utilizzando `kubectl get pods`. Se devi installare `kubectl`, vedi [Install and set up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno").
* Puoi visualizzare i log nella tua applicazione utilizzando `kubectl logs <pod-name>.`

## L'avvio di `docker` ha esito negativo e viene restituito il messaggio file not found
{: #docker_not_found}
{: troubleshoot}

Quando provi ad avviare Docker, viene visualizzato il seguente messaggio di errore:
{: tsSymptoms}

```
È stato riscontrato un errore exec: "docker": executable file not found in $PATH durante la creazione dell'immagine Docker.
```
{: screen}

Il client Docker non è installato oppure è installato ma non è stato avviato.
{: tsCauses}

Assicurati che [Docker](https://docs.docker.com/install/){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") sia installato e avvialo.
{: tsResolve}

## La creazione di un'applicazione non riesce con l'errore Docker
{: #build_error}
{: troubleshoot}

Quando provi a creare un'applicazione con il comando `ibmcloud dev build`, l'operazione non riesce con un errore nomeutente/password Docker. 
{: tsSymptoms}

Si stanno utilizzando delle credenziali Docker Hub non corrette per l'autenticazione. 
{: tsCauses}

Disconnettiti da Docker Hub nel client Docker.
{: tsResolve}
