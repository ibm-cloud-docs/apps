---

copyright:
  years: 2015, 2018
lastupdated: "2018-02-15"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Aggiornamento di applicazioni
{: #updatingapps}

Per aggiornare le applicazioni in {{site.data.keyword.Bluemix_notm}}, puoi utilizzare la riga di comando o {{site.data.keyword.Bluemix}} Continous Delivery. In molti casi, anche per i pacchetti di build integrati quali Node.js, devi inoltre fornire un parametro -c per specificare il comando utilizzato per avviare la tua applicazione.
{:shortdesc}

## Creazione e utilizzo di un dominio personalizzato
{: #domain}

Per le applicazioni Cloud Foundry e i gruppi di contenitori, puoi utilizzare un dominio personalizzato nell'URL della tua applicazione anziché il dominio di sistema {{site.data.keyword.Bluemix_notm}} predefinito che è mybluemix.net.

I domini forniscono la rotta dell'URL assegnata alla tua organizzazione in {{site.data.keyword.Bluemix_notm}}. Per utilizzare un dominio personalizzato, devi registrare il dominio personalizzato su un server DNS pubblico, configurare tale dominio in {{site.data.keyword.Bluemix_notm}} e quindi associarlo al dominio di sistema {{site.data.keyword.Bluemix_notm}} sul server DNS pubblico. Dopo aver
associato il tuo dominio personalizzato al dominio di sistema {{site.data.keyword.Bluemix_notm}},
le richieste per il tuo dominio personalizzato vengono instradate alla tua applicazione in {{site.data.keyword.Bluemix_notm}}.

Puoi creare e utilizzare un dominio personalizzato in {{site.data.keyword.Bluemix_notm}} utilizzando l'interfaccia utente di {{site.data.keyword.Bluemix_notm}} o l'interfaccia della riga di comando bluemix.

### Utilizzo della console {{site.data.keyword.Bluemix_notm}}

  1. Crea un dominio personalizzato per la tua organizzazione.

	1. Vai a **Gestisci** &gt; **Account** &gt; **Organizzazioni Cloud Foundry** &gt; **Visualizza dettagli** per la tua organizzazione. Quindi, fai clic su **Modifica organizzazione Cloud Foundry** &gt; **Domini**.

	2. Nella scheda **DOMINI**, fai clic su **AGGIUNGI DOMINIO**, immetti il nome del tuo dominio personalizzato e fai clic su **SALVA**.

	**Nota**: puoi utilizzare, ad esempio, `mycompany.com` per associare la rotta `www.mycompany.com` alla tua applicazione. Puoi anche utilizzare `example.mycompany.com` per associare la rotta `www.example.mycompany.com` all'applicazione.

  2. Aggiungi la rotta con il dominio personalizzato a un'applicazione.

    1. Fai clic sull'icona **Menu** ![Icona Menu](../icons/icon_hamburger.svg) &gt; **Dashboard**, quindi fai clic sulla riga dell'applicazione a cui desideri aggiungere la rotta. Viene visualizzata la pagina **Panoramica**.

	2. Dal menu **Rotte**, seleziona **Modifica rotte**.

	3. Fai clic su **Aggiungi rotta** e specifica la rotta che vuoi utilizzare per l'applicazione.
	4. Fai clic su **Salva**.

### Utilizzo dell'interfaccia riga di comando bluemix

  1. Crea un dominio personalizzato per la tua organizzazione digitando il
seguente comando:

    ```
    bluemix app domain-create <your org name> mydomain
    ```

    *organization_name*: il nome della tua organizzazione.

    *mydomain*: il nome del dominio personalizzato che desideri utilizzare.

  2. Aggiungi la rotta con il dominio personalizzato a un'applicazione. Per le applicazioni CF, immetti il seguente comando:

    ```
    bluemix app route-map myapp mydomain -n host_name
    ```

    Per i gruppi di contenitori, immetti il seguente comando:
     ```
     cf ic route map -n host_name -d mydomain mycontainergroup
     ```

    *myapp*: per le applicazioni CF, il nome della tua applicazione.

    *mydomain*: il nome del tuo dominio personalizzato, ad esempio `www.mydomain.mybluemix.net`.

    *host_name*: il nome host nella rotta che desideri utilizzare per la tua applicazione.

    *mycontainergroup*: per i gruppi di contenitori, il nome del gruppo di contenitori.

Una volta configurato il dominio personalizzato in {{site.data.keyword.Bluemix_notm}}, devi associarlo al dominio personalizzato del dominio di sistema {{site.data.keyword.Bluemix_notm}} sul tuo server DNS registrato:

  1. Imposta un record 'CNAME' per il nome dominio personalizzato sul tuo server DNS. La procedura per l'impostazione del record CNAME varia a seconda del tuo provider DNS. Ad esempio, se utilizzi GoDaddy, devi seguire le linee guida di [Domains Help ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} fornite da GoDaddy.
  2. Associare il nome dominio personalizzato all'endpoint sicuro della regione {{site.data.keyword.Bluemix_notm}} in cui viene eseguita la tua applicazione. Utilizza i seguenti endpoint della regione per fornire la rotta dell'URL assegnata alla tua organizzazione in {{site.data.keyword.Bluemix_notm}}:

    * STATI UNITI SUD: `secure.us-south.bluemix.net`
    * STATI UNITI EST: `secure.us-east.bluemix.net`
    * EU-DE: `secure.eu-de.bluemix.net`
    * EUROPA REGNO UNITO: `secure.eu-gb.bluemix.net`
    * AU-SYD: `secure.au-syd.bluemix.net`

In un browser o nell'interfaccia riga di comando, immetti il seguente URL per accedere all'applicazione myapp:

```
http://nome_host.mio_dominio
```

**Nota:** per rimuovere una rotta orfana, utilizza il seguente comando:

```
bluemix app route-delete domain -n hostname -f
```

*domain* è il nome del tuo dominio e *hostname* è il nome host della rotta per la tua applicazione. Per ulteriori informazioni sul comando **bluemix app route-delete**, digita `bluemix app route-delete -h`.

##Distribuzioni blue-green
{: #blue_green}

{{site.data.keyword.Bluemix_notm}} supporta
la tecnica di distribuzione Blue-Green che consente la fornitura continua e la riduzione degli eventi di inattività.

La *distribuzione Blue-Green* è una tecnica di distribuzione
con zero tempo di inattività che consiste in due ambienti di produzione quasi identici,
denominati Blue e Green. La differenza sta nelle risorse utente
che lo sviluppatore ha modificato intenzionalmente, solitamente
nella versione dell'applicazione. In ogni momento, almeno uno degli ambienti
è attivo. L'utilizzo della tecnica di distribuzione Blue-Green ti offre i
seguenti vantaggi:

* Portare il software rapidamente dall'ultima fase di test alla produzione
live.
* Distribuire una nuova versione di un'applicazione senza interrompere il traffico
verso quell'applicazione.
* Eseguire un rapido rollback. Se ci sono problemi in uno dei due ambienti,
puoi passare rapidamente all'altro.

Se hai già distribuito un'applicazione in {{site.data.keyword.Bluemix_notm}} e
desideri aggiornare l'applicazione a una nuova versione, puoi utilizzare uno dei
seguenti due approcci per garantire la distribuzione Blue-Green.

###Esempio: utilizzo del comando bluemix app rename

In questo esempio, il nome dell'applicazione è Blue. L'esempio mostra come aggiornare la versione di *Blue* utilizzando il comando **bluemix app rename** senza interrompere il traffico verso l'applicazione. In via facoltativa, la versione precedente di *Blue* può
essere eliminata quando è in funzione la nuova.

1. Esegui il push dell'applicazione *Blue* a {{site.data.keyword.Bluemix_notm}}.

  ```
  bluemix app push Blue
  ```

  Risultato: l'applicazione *Blue* è in esecuzione e sta rispondendo all'URL `Blue.mybluemix.net`.

2. Utilizza il comando **bluemix app rename** per ridenominare l'applicazione *Blue* in *Green*:

  ```
  bluemix app rename Blue Green
  ```

  Elenca le applicazioni nello spazio corrente utilizzando il comando **bluemix app list**:

  ```
  ...
  name             requested state   instances   memory   disk   urls
  Green            started           1/1         1G       1G	 Blue.mybluemix.net
  ...
  ```

  Risultato: l'applicazione *Green* è in esecuzione e sta rispondendo all'URL `Blue.mybluemix.net`.

3. Apporta le modifiche necessarie e prepara la versione
*Blue*. Esegui il push dell'applicazione *Blue* aggiornata a {{site.data.keyword.Bluemix_notm}}:

  ```
  bluemix app push Blue
  ```

  Elenca le applicazioni nello spazio corrente utilizzando il comando **bluemix app list**:

  ```
  ...
  name             requested state   instances   memory   disk   urls
  Green            started           1/1         1G       1G	 Blue.mybluemix.net
  Blue             started           1/1         1G       1G	 Blue.mybluemix.net
  ...
  ```

  Risultati:
    * Vengono distribuite due istanze dell'applicazione, *Blue* e *Green*.
	* L'applicazione *Green* è in esecuzione e sta rispondendo all'URL `Blue.mybluemix.net`.

4. Facoltativo: se vuoi eliminare la versione precedente (*Green*) dell'applicazione, utilizza il comando **bluemix app delete**.

  ```
  bluemix app delete Green -f
  ```

  Elenca le rotte nel tuo spazio utilizzando il comando **bluemix app route-map**:

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Blue
  ...
  ```

  Risultato: l'applicazione *Blue* sta rispondendo all'URL `Blue.mybluemix.net`.

###Esempio: utilizzo del comando bluemix app route-map

In questo esempio, *Blue* è l'applicazione
distribuita in precedenza e *Green* è la versione aggiornata. Questo esempio mostra come aggiornare la versione di *Blue* utilizzando il comando **bluemix app route-map** senza interrompere il traffico verso l'applicazione. In via facoltativa, la versione precedente di *Blue* può
essere eliminata quando è in funzione la nuova.

1. Esegui il push dell'applicazione *Blue* a {{site.data.keyword.Bluemix_notm}}.

  ```
  bluemix app push Blue
  ```

  Risultato: l'applicazione *Blue* è in esecuzione e sta rispondendo all'URL `Blue.mybluemix.net`.

2. Apportare le modifiche necessarie e preparare la versione
*Green*. Esegui il push dell'applicazione *Green* a {{site.data.keyword.Bluemix_notm}}:

  ```
  bluemix app push Green
  ```

  Elenca le applicazioni nello spazio corrente utilizzando il comando **bluemix app route-map**:

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Blue
  Green            mybluemix.net    Green
  ...
  ```

  Risultati:

    * Vengono distribuite due istanze dell'applicazione, *Blue* e *Green*.
	* L'applicazione *Blue* sta rispondendo all'URL `Blue.mybluemix.net` e l'applicazione *Green* sta rispondendo all'URL `Green.mybluemix.net`.

3. Associa l'applicazione *Blue* all'applicazione *Green* in modo che tutto il traffico a `Blue.mybluemix.net` venga instradato sia all'applicazione *Blue* che all'applicazione *Green*.

  ```
  bluemix app route-map Green mybluemix.net -n Blue
  ```

  Elenca le rotte nel tuo spazio utilizzando il comando bluemix app route-map:

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Blue, Green
  Green            mybluemix.net    Green
  ...
  ```

  Risultato:

    * Il router CF ora invia il traffico per Blue.mybluemix.net sia all'applicazione Blue che all'applicazione Green.
	* Il router CF continua a inviare il traffico per Green.mybluemix.net all'applicazione Green.

4. Quando verifichi che *Green* sia in esecuzione nel modo previsto, rimuovi la rotta `Blue.mybluemix.net` dall'applicazione *Blue*:

  ```
  bluemix app route-unmap Blue mybluemix.net -n Blue
  ```

  Elenca le rotte nel tuo spazio utilizzando il comando bluemix app route-map:

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Green
  Green            mybluemix.net    Green
  ...
  ```

  Risultato: il router CF smette di inviare traffico all'applicazione *Blue*. L'applicazione *Green* risponde a entrambi gli URL: `Green.mybluemix.net` e `Blue.mybluemix.net`.

5. Rimuovi la rotta `Green.mybluemix.net` all'applicazione *Green*.

  ```
  bluemix app route-unmap Green mybluemix.net -n Green
  ```

  Risultato: il router CF smette di inviare traffico all'applicazione *Blue*. L'applicazione *Green* sta rispondendo all'URL `Blue.mybluemix.net`.

6. Facoltativo: se vuoi eliminare la versione precedente (*Blue*) dell'applicazione, utilizza il comando `bluemix app delete`.

  ```
  bluemix app delete Blue -f
  ```

  Elenca le rotte nel tuo spazio utilizzando il comando bluemix app route-map:

  ```
  ...
  host             domain           apps
  Blue             mybluemix.net    Green
  ...
  ```

  Risultato: l'applicazione *Green* sta rispondendo all'URL `Blue.mybluemix.net`.


# Link correlati
{: #rellinks notoc}

## Link correlati
{: #general}

[Distribuzioni Blue-green ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](http://martinfowler.com/bliki/BlueGreenDeployment.html){:new_window}
