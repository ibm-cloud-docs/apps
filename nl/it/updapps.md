---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-02"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creazione e utilizzo di un dominio personalizzato
{: #updatingapps}

Per aggiornare le applicazioni in {{site.data.keyword.Bluemix_notm}}, puoi utilizzare la riga di comando o {{site.data.keyword.Bluemix}} Continuous Delivery. In molti casi, anche per i pacchetti di build come Node.js, devi fornire inoltre un parametro -c per specificare quale comando viene utilizzato per avviare la tua applicazione.
{:shortdesc}

I domini forniscono la rotta dell'URL assegnata alla tua organizzazione in {{site.data.keyword.Bluemix_notm}}. Per utilizzare un dominio personalizzato, devi registrare il dominio personalizzato su un server DNS pubblico, configurare tale dominio in {{site.data.keyword.Bluemix_notm}}. Quindi, associa il dominio personalizzato al dominio di sistema {{site.data.keyword.Bluemix_notm}} sul server DNS pubblico. Dopo aver
associato il tuo dominio personalizzato al dominio di sistema,
le richieste per il tuo dominio personalizzato vengono instradate alla tua applicazione in {{site.data.keyword.Bluemix_notm}}.

Puoi creare e utilizzare un dominio personalizzato utilizzando la console {{site.data.keyword.Bluemix_notm}} o l'interfaccia della riga di comando

## Utilizzo della console {{site.data.keyword.Bluemix_notm}}

Completa la seguente procedura per creare un dominio personalizzato per la tua organizzazione utilizzando la console:

1. Vai a **Gestisci** > **Account** > **Organizzazioni Cloud Foundry**.
2. Fai clic sul nome dell'organizzazione per cui stai creando un dominio personalizzato.
3. Fai clic sulla scheda **Domini**.
4. Fai clic su **Aggiungi un dominio** e immetti il tuo nome del dominio e seleziona la regione.
5. Conferma i tuoi aggiornamenti. Fai clic su **Aggiungi**.

Come esempio, puoi utilizzare `*.mycompany.com` per associare la rotta `www.mybluemix.com` alla tua applicazione. Puoi anche utilizzare `example.mycompany.com` per associare la rotta `www.example.mybluemix.com` all'applicazione.
{: tip}

Aggiungi la rotta con il dominio personalizzato a un'applicazione.

1. Fai clic sull'icona **Menu** ![Icona Menu](../icons/icon_hamburger.svg) > **Dashboard**, quindi fai clic sulla riga dell'applicazione a cui desideri aggiungere la rotta. Viene visualizzata la pagina **Panoramica**.
2. Dal menu **Rotte**, seleziona **Modifica rotte**.
3. Fai clic su **Aggiungi rotta** e specifica la rotta che vuoi utilizzare per l'applicazione.
4. Conferma i tuoi aggiornamenti facendo clic su **Salva**.

## Utilizzo della interfaccia riga di comando {{site.data.keyword.Bluemix_notm}}

1. Crea un dominio personalizzato per la tua organizzazione digitando il
seguente comando:

   ```
   ibmcloud app domain-create <your org name> mydomain
   ```

2. Aggiungi la rotta con il dominio personalizzato a un'applicazione. Per le applicazioni CF, immetti il seguente comando:

   ```
   ibmcloud app route-map myapp mydomain -n host_name

   ```

   Per i gruppi di contenitori, immetti il seguente comando:

   ```
   cf ic route map -n host_name -d mydomain mycontainergroup

   ```

Una volta configurato il dominio personalizzato in {{site.data.keyword.Bluemix_notm}}, associa il dominio personalizzato al dominio di sistema {{site.data.keyword.Bluemix_notm}} sul tuo server DNS registrato:

1. Imposta un record 'CNAME' per il nome dominio personalizzato sul tuo server DNS. La procedura per l'impostazione del record CNAME varia a seconda del tuo provider DNS. Ad esempio, se utilizzi GoDaddy, devi seguire le linee guida di [Domains Help ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} fornite da GoDaddy.
2. Associare il nome dominio personalizzato all'endpoint sicuro della regione {{site.data.keyword.Bluemix_notm}} in cui viene eseguita la tua applicazione. Utilizza i seguenti endpoint della regione per fornire la rotta dell'URL assegnata alla tua organizzazione in {{site.data.keyword.Bluemix_notm}}.

  * STATI UNITI SUD - `secure.us-south.bluemix.net`
  * STATI UNITI EST - `secure.us-east.bluemix.net`
  * EU-DE - `secure.eu-de.bluemix.net`
  * EUROPA REGNO UNITO - `secure.eu-gb.bluemix.net`
  * AU-SYD - `secure.au-syd.bluemix.net`

In un browser o nell'interfaccia riga di comando, immetti il seguente URL per accedere all'applicazione `myapp`:

```
http://nome_host.mio_dominio

```

Per rimuovere una rotta orfana, immetti il seguente comando:

```
ibmcloud app route-delete domain -n hostname -f

```
{: tip}

In tale esempio, `domain` è il nome del tuo dominio e `hostname` è il nome host della rotta per la tua applicazione. Per ulteriori informazioni sul comando `ibmcloud app route-delete`, immetti `ibmcloud app route-delete -h`. 
