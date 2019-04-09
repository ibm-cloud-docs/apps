---

copyright:
  years: 2015, 2019
lastupdated: "2019-01-30"

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

I problemi generali con la creazione delle applicazioni potrebbero includere applicazioni che non possono essere aggiornate o caratteri a doppio byte che non vengono visualizzati. In molti casi, puoi risolvere questi problemi seguendo pochi semplici passi.
{:shortdesc}

## Non hai salvato delle modifiche
{: #ts_unsaved_changes}
{: troubleshoot}

Quando fai clic sugli elementi nella pagina dei dettagli dell'applicazione, potresti non riuscire ad eseguire le azioni. È possibile che ti venga richiesto di salvare le modifiche prima di poter continuare.

Quando tenti di controllare la tua applicazione o i tuoi servizi nella pagina dei dettagli dell'applicazione, viene visualizzato il seguente messaggio di errore:
{: tsSymptoms}

`You have unsaved changes. Are you sure you want to leave this page?`

Quando passi il mouse sui campi **ISTANZE** o **QUOTA DI MEMORIA** nel riquadro del runtime, i valori cambiano. Questo è il funzionamento progettato. Tuttavia ti viene richiesto di salvare le impostazioni della memoria o dell'istanza prima di passare a un'altra pagina.
{: tsCauses}

Chiudi la finestra di dialogo del messaggio e fai clic su **RESET** nel tuo riquadro di runtime.
{: tsResolve}

## Il failover automatico tra le regioni {{site.data.keyword.cloud_notm}} non è disponibile
{: #ts_failover}
{: troubleshoot}

Non riesci a utilizzare il failover automatico tra le regioni {{site.data.keyword.cloud}}. Tuttavia, come soluzione alternativa, puoi utilizzare un provider DNS che supporti il failover tra molti indirizzi IP.

Quando una regione {{site.data.keyword.cloud_notm}} non è più disponibile, anche le applicazioni in esecuzione in tale regione non saranno più disponibili, anche se le stesse applicazioni sono in esecuzione in un'altra regione {{site.data.keyword.cloud_notm}}.
{: tsSymptoms}

{{site.data.keyword.cloud_notm}} non fornisce ancora il failover automatico da una regione all'altra.
{: tsCauses}

Puoi utilizzare un provider DNS che supporti il failover intelligente tra più indirizzi IP e configurare manualmente le tue impostazioni DNS per abilitare il failover automatico tra le regioni {{site.data.keyword.cloud_notm}}. I provider DNS con questa funzione comprendono NSONE, Akamai e Dyn.
{: tsResolve}

Quando configuri le tue impostazioni DNS, devi specificare gli indirizzi IP pubblici delle regioni {{site.data.keyword.cloud_notm}} in cui sono esecuzione le tue applicazioni. Per ottenere l'indirizzo IP pubblico di una regione {{site.data.keyword.cloud_notm}}, utilizza il comando `nslookup`. Ad esempio, puoi immettere il seguente comando in una finestra della riga di comando.
```
nslookup cloud.ibm.com
```
{: codeblock}


## Impossibile riutilizzare i nomi di applicazioni eliminate
{: #ts_reuse_appname}
{: troubleshoot}

Dopo aver eliminato un'applicazione, puoi riutilizzarne il nome solo dopo aver eliminato la rotta dell'applicazione.

Quando tenti di riutilizzare il nome applicazione, ricevi il seguente messaggio:
{: tsSymptoms}

`Il nome è già utilizzato da un'altra applicazione.`

Quando si elimina un'applicazione, la sua rotta, ossia l'URL dell'applicazione, non viene eliminata automaticamente e non è disponibile per il riutilizzo. Per poterlo riutilizzare, devi accedere allo spazio in cui è stata creata l'applicazione per eliminare la rotta.
{: tsCauses}

Per eliminare la rotta non utilizzata, completa la seguente procedura:
{: tsResolve}

  1. Controlla se la rotta appartiene allo spazio corrente immettendo il seguente comando:
    ```
    ibmcloud cf routes
    ```
    {: codeblock}

  2. Se la rotta non appartiene allo spazio corrente, passa allo spazio o all'organizzazione a cui appartiene immettendo il seguente comando:
    ```
    ibmcloud cf target -o org_name -s space_name
    ```
    {: codeblock}

  3. Elimina la rotta dell'applicazione immettendo il seguente comando:
    ```
    ibmcloud cf delete-route domain_name -n host_name
    ```
    {: codeblock}

  Ad esempio:
  ```
  ibmcloud cf delete-route cf.cloud.ibm.com -n app001
  ```
  {: codeblock}

## Impossibile richiamare gli spazi in un'organizzazione
{: #ts_retrieve_space}
{: troubleshoot}

Non puoi creare un'applicazione o un servizio se alla tua organizzazione corrente non è associato alcuno spazio.

Quando tenti di creare un'applicazione in {{site.data.keyword.cloud_notm}}, viene visualizzato il seguente messaggio di errore:
{: tsSymptoms}

`BXNUI0515E: Gli spazi nell'organizzazione non sono stati recuperati. Si è verificato un problema di rete oppure la tua organizzazione corrente non dispone di uno spazio associato ad essa.`

Questo errore si verifica spesso la prima volta che si tenta di creare un'applicazione o un servizio dal Catalogo quando ancora non è stato creato uno spazio.
{: tsCauses}

Assicurati di aver creato uno spazio nella tua organizzazione corrente. Per creare uno spazio, utilizza uno dei seguenti metodi:
{: tsResolve}

* Dalla barra dei menu, fai clic su **Gestisci > Account** e seleziona **Organizzazioni Cloud Foundry**. Seleziona l'organizzazione in cui vuoi creare lo spazio e fai clic su **Crea uno spazio**.
* Nell'interfaccia riga di comando Cloud Foundry, immetti `cf create-space <space_name> -o <organization_name>`.

Riprova. Se visualizzi di nuovo questo messaggio, vai alla pagina sugli [stati di {{site.data.keyword.cloud_notm}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://ibm.biz/bluemixstatus){: new_window} per controllare se un servizio o un componente ha qualche problema.

## Impossibile effettuare le azioni richieste
{: #ts_authority}
{: troubleshoot}

Non puoi completare le azioni senza un'autorizzazione di accesso appropriata.

Quando tenti di eseguire azioni per un'istanza del servizio o un'istanza dell'applicazione, non riesci a completare le azioni richieste e visualizzai uno dei seguenti messaggi di errore:
{: tsSymptoms}

`BXNUI0514E: Non sei uno sviluppatore per nessuno degli spazi nell'organizzazione <orgName>.`

`Errore server, codice di stato: 403, codice di errore: 10003, messaggio: Non sei autorizzato a effettuare l'azione richiesta.`

Non disponi del livello di autorità adeguato per eseguire le azioni.
{: tsCauses}

Per ottenere il livello di autorità appropriato, utilizza uno dei seguenti metodi.
{: tsResolve}

* Seleziona un'altra organizzazione e uno spazio per cui disponi del ruolo di sviluppatore.
* Chiedi al gestore organizzazione di modificare il tuo ruolo in sviluppatore oppure di creare uno spazio e assegnarti quindi un ruolo sviluppatore. Consulta [Gestione di organizzazioni e spazi](/docs/admin/orgs_spaces.html) per i dettagli.

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

Per ulteriori informazioni sui comandi che puoi utilizzare in altri linguaggi di programmazione, vedi [Java ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} e [Ruby ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window}.

## Ricezione di errori 502 Bad Gateway
{: #ts_502_error}
{: troubleshoot}

Se ricevi degli errori `502 Bad Gateway` quando interagisci con le applicazioni su {{site.data.keyword.cloud_notm}}, controlla la pagina degli stati di {{site.data.keyword.cloud_notm}} ed effettua le operazioni appropriate.

Ricevi dei messaggi di errore che iniziano con 502 Bad Gateway. Ad esempio, potresti vedere `502 Bad Gateway: Registered endpoint failed to handle the request.`
{: tsSymptoms}

Un errore Bad Gateway di solito si verifica quando visiti un sito Web che utilizza un server proxy per memorizzare e inoltrare i dati dal server principale che ospita il sito. Il server principale e il server proxy potrebbero non connettersi correttamente. Pertanto visualizzi il codice di stato HTTP 502 nella finestra del
browser. Questo codice di stato indica che il server principale del sito non ha ricevuto l'implementazione HTTP prevista dal server proxy.
{: tsCauses}

Altre cause meno comuni di un errore Bad Gateway sono interruzioni ISP (Internet Service Provider), configurazioni firewall non valide ed errori della cache del browser.

Se sospetti che un servizio {{site.data.keyword.cloud_notm}} sia inattivo, controlla prima la pagina sugli [stati di {{site.data.keyword.cloud_notm}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://ibm.biz/bluemixstatus){: new_window}. Una soluzione potrebbe essere quella di utilizzare il servizio in un'altra regione {{site.data.keyword.cloud_notm}}. Informazioni dettagliate sono disponibili in [Utilizzo dei servizi in un'altra regione ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](/docs/services/reqnsi.html#cross_region_service){: new_window}. Se lo stato del servizio è normale,
prova le seguenti operazioni per risolvere il problema:
{: tsResolve}

  * Ritenta l'azione:
    * Ricarica la pagina premendo F5 sulla tastiera o facendo clic su **Aggiorna**. Se questa operazione non funziona, cancella la cache e i cookie del tuo browser e ricarica di nuovo la pagina.
    * Utilizza un browser differente.
    * Riavvia il router, il modem e il computer. Il riavvio di questi
dispositivi può cancellare i diversi errori che portano all'errore 502.
  * Attendi e riprova in seguito. Possono verificarsi dei problemi temporanei con il tuo provider dei servizi internet o con i servizi {{site.data.keyword.cloud_notm}}. Puoi attendere finché i problemi non vengono risolti.
  * Se il problema persiste, contatta il supporto {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Come contattare il supporto {{site.data.keyword.cloud_notm}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](/docs/support/index.html#contacting-bluemix-support){: new_window}.

## Quota disco superata
{: #ts_disk_quota}
{: troubleshoot}

Se esaurisci lo spazio su disco, puoi modificare manualmente la quota per
ottenere ulteriore spazio sul disco.

Se esaurisci lo spazio su disco, potresti visualizzare un messaggio
che indica che la quota di disco è stata superata. Per risolvere il problema,
potresti aver tentato di ridimensionare la tua istanza dell'applicazione per ottenere ulteriore spazio
su disco. Ad esempio, avresti potuto eseguire il ridimensionamento da 256 a 1256 MB modificando la quota di memoria nella pagina dei dettagli dell'applicazione. Tuttavia, poiché la quota di disco è rimasta la stessa, non hai ottenuto ulteriore spazio su disco.
{: tsSymptoms}

La quota di disco predefinita assegnata a un'applicazione è 1
GB. Se hai bisogno di più spazio su disco, devi specificare manualmente la
quota di disco.
{: tsCauses}

Utilizza uno dei seguenti metodi per specificare la quota disco. La quota di disco massima che puoi specificare è 2 GB. Se 2 GB non è ancora
sufficiente, prova un servizio esterno come [Object Store](/docs/services/ObjectStorage/index.html).
{: tsResolve}

  * Nel file manifest.yml, aggiungi la seguente voce:
  ```yaml
	disk_quota: <quota_disco>
	```
  * Utilizza l'opzione **-k** con il comando `ibmcloud cf push` quando esegui il push della tua applicazione a {{site.data.keyword.cloud_notm}}:

  ```
	ibmcloud cf push appname -p app_path -k <disk_quota>
	```
  {: codeblock}

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

Come soluzione temporanea, utilizza servizi di terze parti che non si basano sul servizio GCM, ad esempio [Pushy ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://pushy.me){: new_window}, [getui ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://www.getui.com/){: new_window} e [jpush ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.jpush.cn/){: new_window}.
{: tsResolve}

## Limite dei servizi dell'organizzazione superato
{: #ts_servicelimit}
{: troubleshoot}

Se utilizzi un account utente Lite, potresti non riuscire a creare un'applicazione in {{site.data.keyword.cloud_notm}} se hai superato il limite dei servizi della tua organizzazione.

Quando tenti di creare un'applicazione in {{site.data.keyword.cloud_notm}}, viene visualizzato il seguente messaggio di errore:
{: tsSymptoms}

`BXNUI2032E: La risorsa <service_instances> non è stata creata. Si è verificato un errore mentre Cloud Foundry stava venendo contattato per creare la risorsa. Messaggio di Cloud Foundry: "È stato superato il limite
dei servizi dell'organizzazione."`

Questo errore si verifica quando superi il limite per il numero di istanze del servizio che puoi avere per l'account.
{: tsCauses}

Elimina tutte le istanze dei servizi che non sono necessarie o rimuovi il limite per il numero di istanze del servizio che puoi avere.
{: tsResolve}

  * Per eliminare un'istanza dei servizi, puoi utilizzare la console {{site.data.keyword.cloud_notm}} o l'interfaccia riga di comando.

    Per utilizzare la console {{site.data.keyword.cloud_notm}} per eliminare un'istanza del servizio, completa la seguente procedura:
	  1. Nell'elenco risorse, fai clic sul menu **Azioni** per il servizio che vuoi eliminare.
	  2. Fai clic su **Elimina servizio**. Ti viene richiesto di preparare nuovamente l'applicazione a cui era associata l'istanza del servizio.

    Per utilizzare l'interfaccia riga di comando per eliminare un'istanza del
servizio, completa la seguente procedura:
	  3. Annulla il bind dell'istanza del servizio da un'applicazione. Immetti `cf unbind-service <appname> <service_instance_name>`.
	  4. Elimina l'istanza del servizio. Immetti `cf delete-service <service_instance_name>`.
	  5. Dopo che hai eliminato l'istanza del servizio, potresti voler ripreparare la tua applicazione a cui era associata mediante bind l'istanza del servizio. Immetti `cf restage <appname>`.

  * Per rimuovere il limite sul numero di istanze del servizio che puoi avere, aggiorna il tuo account Lite a un account fatturabile. Per ulteriori informazioni, vedi [Aggiornamento del tuo account](/docs/account/index.html#upgrade-to-paygo).

## Impossibile eseguire i file eseguibili su {{site.data.keyword.cloud_notm}}
{: #ts_executable}
{: troubleshoot}

Potresti non riuscire ad eseguire i file eseguibili su {{site.data.keyword.cloud_notm}} se tali eseguibili sono stati sviluppati e creati in un ambiente diverso.

Non puoi eseguire gli eseguibili su {{site.data.keyword.cloud_notm}} se questi eseguibili sono stati sviluppati e creati in un ambiente diverso.
{: tsSymptoms}

Se il contenuto che desideri distribuire a {{site.data.keyword.cloud_notm}} è
già un eseguibile, il contenuto è stato creato precedentemente e non è necessario
crearlo in {{site.data.keyword.cloud_notm}}. In questo caso, non è richiesto alcun pacchetto di build per l'eseguibile da eseguire
su {{site.data.keyword.cloud_notm}}. Devi indicare esplicitamente a {{site.data.keyword.cloud_notm}} che non è richiesto alcun pacchetto di build.
{: tsCauses}

Quando distribuisci l'eseguibile a {{site.data.keyword.cloud_notm}},
devi specificare `null-buildpack`, che indica che
non è richiesto alcun pacchetto di build. Specifica `null-buildpack` utilizzando l'opzione **-b** con il comando `ibmcloud cf push`:
{: tsResolve}

```
ibmcloud cf push appname -p app_path -c <start_command> -b <null-buildpack>
```
{: codeblock}

Ad esempio:
```
ibmcloud cf push appname -p app_path -c ./RunMeNow -b https://github.com/ryandotsmith/null-buildpack
```
{: codeblock}

## Limite di memoria dell'organizzazione superato
{: #ts_outofmemory}
{: troubleshoot}

Se utilizzi un account utente Lite, potresti non riuscire a distribuire un'applicazione a {{site.data.keyword.cloud_notm}} se hai superato il limite di memoria della tua organizzazione. Puoi
ridurre la memoria utilizzata dalle tue applicazioni o aumentare la quota di memoria
del tuo account. La quota massima di memoria per un account Lite è 256 MB e può essere aumentata solo eseguendo l'upgrade a un account fatturabile.

Quando distribuisci un'applicazione a {{site.data.keyword.cloud_notm}}, viene visualizzato il seguente messaggio di errore:
{: tsSymptoms}

`FAILED Server error,
status code: 400, error code: 100005, message: You have exceeded your
organization's memory limit.`

Questo errore si verifica quando la quantità di memoria rimanente per la tua organizzazione è inferiore alla quantità di memoria richiesta dall'applicazione che desideri distribuire. La quota massima di memoria per un account Lite è 256 MB.
{: tsCauses}

Puoi aumentare la quota di memoria del tuo account o ridurre la memoria utilizzata dalle tue applicazioni.
{: tsResolve}

  * Per aumentare la quota di memoria del tuo account, esegui l'upgrade del tuo account Lite a un account fatturabile. Per ulteriori informazioni, vedi [Aggiornamento del tuo account](/docs/account/index.html#upgrade-to-paygo).
  * Per ridurre la memoria utilizzata dalle tue applicazioni, utilizza la console {{site.data.keyword.cloud_notm}} o l'interfaccia riga di comando Cloud Foundry. 

    Se utilizzi la console {{site.data.keyword.cloud_notm}}, completa la seguente procedura:

    1. Seleziona la tua applicazione dall'elenco risorse. Viene visualizzata la pagina dei dettagli dell'applicazione.
    2. Nel riquadro runtime, puoi ridurre il limite massimo di memoria o il numero di istanze dell'applicazione, o entrambi, per tua applicazione.

    Se utilizzi l'interfaccia riga di comando, completa la seguente procedura:

    1. Verifica la quantità di memoria utilizzata per le tue applicazioni:
  	  ```
	    ibmcloud cf list
	    ```
      {: codeblock}

	    Il comando `ibmcloud cf list` elenca tutte le applicazioni che hai distribuito nel tuo spazio corrente. Viene visualizzato anche lo stato di ciascuna applicazione.

    2. Per ridurre la quantità di memoria utilizzata dalla tua applicazione, riduci il numero di istanze dell'applicazione e/o il limite massimo di memoria.
	    ```
	    ibmcloud cf push appname -p app_path -i instance_number -m memory_limit
      ```
      {: codeblock}

    3. Riavvia la tua applicazione per rendere effettive le modifiche.

## Le applicazioni non si riavviano automaticamente
{: #ts_apps_not_auto_restarted}
{: troubleshoot}

Un'applicazione non si riavvia automaticamente se un servizio che associ mediante bind all'applicazione smette di funzionare.

Quando un servizio che associ mediante bind a un'applicazione viene arrestato in modo anomalo, nell'applicazione potrebbero verificarsi dei problemi come interruzioni, eccezioni ed errori di connessione. {{site.data.keyword.cloud_notm}} non riavvia automaticamente l'applicazione per eseguire un ripristino da tali problemi.
{: tsSymptoms}

Questo è il funzionamento progettato da Cloud Foundry.
{: tsCauses}

Puoi riavviare manualmente l'applicazione immettendo il seguente comando nell'interfaccia riga di comando:
{: tsResolve}

```
ibmcloud cf push appname -p app_path
```
{: codeblock}

Inoltre, puoi codificare l'applicazione per identificare e risolvere problemi come interruzioni, eccezioni ed errori di connessione.

<!-- begin STAGING ONLY -->

## Il debug di {{site.data.keyword.cloud_notm}} Live Sync non si avvia dalla riga di comando
{: #ts_no_debug}
{: troubleshoot}

Hai abilitato la funzione Debug di {{site.data.keyword.cloud_notm}} Live Sync per la tua applicazione utilizzando la riga di comando, ma non riesci ad accedere all'interfaccia Debug.

Hai abilitato la funzione Debug per la tua applicazione impostando la variabile di ambiente **BLUEMIX_APP_MGMT_ENABLE**. Tuttavia, non riesci ad accedere all'interfaccia utente Debug in `app_url/bluemix-debug/manage`.
{: tsSymptoms}

La funzione Debug non può essere abilitata nelle seguenti situazioni:
{: tsCauses}

  * Quando `manifest.yml` contiene l'attributo di comando
  * Quando utilizzi l'opzione **-c** per distribuire un'applicazione a {{site.data.keyword.cloud_notm}}

Per risolvere il problema utilizza una delle seguenti opzioni:
{: tsResolve}

  * La procedura consigliata è quella di utilizzare il pacchetto di build IBM Node.js per avviare l'applicazione. Per ulteriori informazioni, consulta la sezione del comando di avvio dell'argomento [Distribuzione di un'applicazione Node.js a {{site.data.keyword.cloud_notm}}](/docs/runtimes/nodejs/index.html#nodejs_runtime).
  * Disabilita il comando per la tua applicazione esistente riesaminando l'attributo di comando in `manifest.yml` per command: null o modificando il comando push per includere `-c null`.
  * Rimuovi l'attributo di **comando** da `manifest.yml`. Elimina quindi l'applicazione corrente da {{site.data.keyword.cloud_notm}} ed esegui nuovamente il push dell'applicazione.

<!-- end STAGING ONLY -->

## Impossibile trovare le organizzazioni in {{site.data.keyword.cloud_notm}}
{: #ts_orgs}
{: troubleshoot}

Potresti non riuscire a individuare la tua organizzazione in {{site.data.keyword.cloud_notm}} quando
lavori su una regione {{site.data.keyword.cloud_notm}}.

Puoi accedere correttamente alla console {{site.data.keyword.cloud_notm}} ma non puoi eseguire il push delle applicazioni utilizzando l'interfaccia riga di comando Cloud Foundry.
{: tsSymptoms}

Quando provi ad eseguire il push di un'applicazione a {{site.data.keyword.cloud_notm}} utilizzando l'interfaccia riga di comando Cloud Foundry, vedi uno dei seguenti messaggi di errore con il nome dell'organizzazione specificato nel messaggio.

`Error finding org`

`Organization not found`

Questo problema si verifica poiché l'endpoint API della regione che vuoi utilizzare non è specificato e l'organizzazione che stai cercando potrebbe trovarsi in una regione differente.
{: tsCauses}

Se stai eseguendo il push della tua applicazione a {{site.data.keyword.cloud_notm}} utilizzando l'interfaccia riga di comando Cloud Foundry, immetti il comando `cf api` e specifica l'endpoint API della regione. Ad esempio, immetti il seguente comando per stabilire una connessione alla regione {{site.data.keyword.cloud_notm}} Europa
Regno Unito:
{: tsResolve}

```
cf api https://api.eu-gb.cf.cloud.ibm.com
```
{: codeblock}


## Impossibile creare rotte di applicazione
{: #ts_hostistaken}
{: troubleshoot}

Quando distribuisci un'applicazione a {{site.data.keyword.cloud_notm}}, la rotta dell'applicazione non può essere creata se il nome host da te specificato è già in uso.

Quando distribuisci un'applicazione a {{site.data.keyword.cloud_notm}}, visualizzi il seguente messaggio di errore:
{: tsSymptoms}

`Creating route hostname.domainname ... FAILED Server error, status code: 400, error code: 210003, message: The host is taken: hostname`

Questo problema si verifica se il nome host da te specificato
è già in uso.
{: tsCauses}

Il nome host specificato deve essere univoco all'interno
del dominio che stai utilizzando. Per specificare un nome host differente, usa uno dei
seguenti metodi:
{: tsResolve}

  * Se distribuisci la tua applicazione utilizzando il file `manifest.yml`, specifica il nome host nell'opzione host.
    ```yaml
    host: host_name
	  ```

  * Se distribuisci la tua applicazione dal prompt dei comandi, utilizza il comando `ibmcloud cf push` con l'opzione **-n**.
    ```
    ibmcloud cf push appname -p app_path -n host_name
    ```
    {: codeblock}

## Non è possibile eseguire il push di applicazioni WAR utilizzando il comando ibmcloud cf push
{: #ts_cf_war}
{: troubleshoot}

Potresti non riuscire a utilizzare il comando `ibmcloud cf push` per distribuire un'applicazione web archiviata a {{site.data.keyword.cloud_notm}} se l'ubicazione dell'applicazione non è specificata correttamente.

Quando carichi un'applicazione WAR in {{site.data.keyword.cloud_notm}} utilizzando il comando `ibmcloud cf push`, vedi il seguente messaggio di errore:
{: tsSymptoms}
`Staging error: cannot get instances since staging failed.`

Questo problema potrebbe verificarsi se non si specifica il file WAR o il percorso del file WAR.
{: tsCauses}

Utilizza l'opzione **-p** per specificare
un file WAR o aggiungere il percorso del file WAR. Ad esempio:
{: tsResolve}

```
ibmcloud cf push MyUniqueAppName01 -p app.war
```
{: codeblock}

```
ibmcloud cf push MyUniqueAppName02 -p "./app.war"
```
{: codeblock}

Per ulteriori informazioni sul comando `ibmcloud cf push` , immetti `ibmcloud cf push -h`.

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

    * Utilizza il file [package.json ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.npmjs.com/package/jsonfile){: new_window}. Ad esempio:
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

Per ulteriori suggerimenti relativi alle applicazioni Node.js, vedi [Tips for Node.js Applications ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window}.

## Sono presenti degli errori di configurazione nel file `server.xml` dopo aver importato un'applicazione {{site.data.keyword.cloud_notm}} Liberty in Eclipse
{: #ts_eclipse}
{: troubleshoot}

Se vedi degli errori di configurazione nel file `server.xml` dopo aver importato un'applicazione {{site.data.keyword.cloud_notm}} Liberty in Eclipse, potresti dover rimuovere il file `server.xml` dal progetto.

Dopo aver importato un'applicazione {{site.data.keyword.cloud_notm}} Liberty in Eclipse, vedi degli errori di configurazione nel file `server.xml` dalla vista Problemi di Eclipse.
{: tsSymptoms}

Il pacchetto di build Liberty utilizza il file `server.xml` per configurare l'applicazione e genera un file `runtime-vars.xml` quando viene eseguito il push dell'applicazione Liberty a {{site.data.keyword.cloud_notm}}. Quando importi l'applicazione in Eclipse, il file `runtime-vars.xml` non esiste nel tuo ambiente locale.
{: tsCauses}

Puoi risolvere questo problema rimuovendo il file server.xml dal progetto. Il pacchetto di build crea il file `server.xml` dinamicamente quando
esegui il push dell'applicazione come un'applicazione WAR. Per ulteriori informazioni, vedi [Liberty for Java](/docs/runtimes/liberty/index.html).
{: tsResolve}

## Impossibile preparare l'applicazione utilizzando i pacchetti di build personalizzati
{: #ts_bp_compilation}
{: troubleshoot}

Potresti non riuscire a distribuire un'applicazione a {{site.data.keyword.cloud_notm}} con un pacchetto di build personalizzato se gli script in questo pacchetto non sono file eseguibili.

Quando distribuisci un'applicazione a {{site.data.keyword.cloud_notm}} con un pacchetto di build personalizzato, visualizzi il messaggio di errore `La preparazione dell'applicazione non è riuscita e, pertanto, non ci sono istanze da visualizzare.`
{: tsSymptoms}

Questo problema potrebbe verificarsi se gli script, ad esempio lo script di rilevamento, lo script di compilazione e lo script di rilascio, non sono eseguibili.
{: tsCauses}

Puoi utilizzare il comando [Git update ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://git-scm.com/docs/git-update-index){: new_window} per modificare l'autorizzazione di ciascuno script in eseguibile. Ad esempio, puoi immettere `git update --chmod=+x script.sh`.
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
dell'applicazione](/docs/manageapps/depapps.html#appmanifest).
 {: tsResolve}

## Impossibile distribuire le applicazioni Meteor
{: #ts_meteor}
{: troubleshoot}

Potresti non riuscire a distribuire un'applicazione Meteor a {{site.data.keyword.cloud_notm}} se il pacchetto di build non è specificato correttamente.

Quando distribuisci un'applicazione Meteor a {{site.data.keyword.cloud_notm}}, potresti visualizzare il messaggio di errore `La
preparazione dell'applicazione non è riuscita e, pertanto, non ci sono istanze da visualizzare.`
{: tsSymptoms}

Questo problema si verifica perché non viene fornito alcun pacchetto di build integrato per le applicazioni Meteor. Devi utilizzare un pacchetto di build personalizzato.
{: tsCauses}

Per utilizzare un pacchetto di build personalizzato per le applicazioni Meteor, usa uno dei seguenti metodi:
{: tsResolve}

  * Se distribuisci la tua applicazione utilizzando il file `manifest.yml`, specifica l'URL o il nome del pacchetto di build personalizzato usando l'opzione buildpack. Ad esempio:
  ```yaml
  buildpack: https://github.com/Sing-Li/bluemix-bp-meteor
  ```

  * Se distribuisci la tua applicazione dal prompt dei comandi, utilizza il comando `ibmcloud cf push` e specifica il tuo pacchetto di build personalizzato usando l'opzione **-b**. Ad esempio:
  ```
	ibmcloud cf push appname -p app_path -b https://github.com/Sing-Li/bluemix-bp-meteor
	```
  {: codeblock}

## Exceeded your storage quota
{: #exceed_quota}

Se i lavori di build o di distribuzione non riescono, e vedi il seguente messaggio, puoi eliminare le tue immagini con i seguenti comandi CLI. `Stato: non autorizzato: È stata superata la quota di archiviazione. Eliminare una o più immagini o rivedere la quota di archiviazione e il piano dei prezzi.`

* Installa la [CLI {{site.data.keyword.cloud_notm}}](/docs/cli/index.html), se non lo hai già fatto.
* Accedi a {{site.data.keyword.cloud_notm}} utilizzando `ibmcloud login` e indica come sua destinazione lo spazio in cui ti trovi.
* Elenca le tue immagini utilizzando `ibmcloud cr images`.
* Elimina le eventuali immagini inutilizzate servendoti di `ibmcloud cr image-rm <respository>:<tag>`.
* Esegui nuovamente il lavoro di build o di distribuzione che non era riuscito.

## Accessing Kubernetes logs
{: #access_kube_logs}

Se l'applicazione non è in esecuzione e non riesci ad accedere all'endpoint di integrità, prova a guardare i log nel cluster.
* Installa la [CLI {{site.data.keyword.cloud_notm}}](/docs/cli/index.html), se non lo hai già fatto.
* Accedi a {{site.data.keyword.cloud_notm}} utilizzando `ibmcloud login` e indica come sua destinazione lo spazio in cui ti trovi.
* Elenca i tuoi cluster utilizzando `ibmcloud cs clusters`,
* Indica come destinazione il tuo cluster corrispondente utilizzando `ibmcloud cs cluster-config <cluster-name>`.
* Esporta la variabile di ambiente che è elencata.
* Visualizza i tuoi pod utilizzando `kubectl get pods`. Se devi installare `kubectl`, vedi [Install and set up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).
* Puoi visualizzare i log nella tua applicazione utilizzando `kubectl logs <pod-name>.`


## Starting `docker` fails with "file not found" message
{: #docker_not_found}
{: troubleshoot}

Quando tenti di avviare Docker, viene visualizzato il seguente messaggio:
{: tsSymptoms}

```
An error exec: "docker": executable file not found in $PATH was encountered while building the Docker image.
```
{: screen}

Il client Docker non è installato oppure lo è ma non è stato avviato.
{: tsCauses}

Assicurati che [Docker](https://docs.docker.com/install/) sia installato e avvialo.
{: tsResolve}


## Building an app fails with Docker error
{: #build_error}
{: troubleshoot}

Quando tenti di creare un'applicazione con il comando `ibmcloud dev build`, il processo non riesce e ricevi un errore nome utente/password Docker.
{: tsSymptoms}

Stanno venendo utilizzate per l'autenticazione delle credenziali Docker Hub non corrette.
{: tsCauses}

Esci da Docker Hub nel client Docker.
{: tsResolve}


