---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-15"

keywords: apps, custom domain, Kubernetes

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Aggiunta e utilizzo di un dominio personalizzato
{: #updatingapps}

I domini forniscono la rotta dell'URL assegnata alla tua organizzazione in {{site.data.keyword.cloud}}. I domini personalizzati indirizzano le richieste per le tue applicazioni a un URL che ti appartiene. Il dominio personalizzato può essere un dominio condiviso, un dominio secondario condiviso
o un dominio e un host condivisi. A meno che non venga specificato un dominio personalizzato, nell'instradamento alla tua applicazione, {{site.data.keyword.cloud_notm}} utilizza un dominio condiviso predefinito. Puoi creare e utilizzare un dominio personalizzato utilizzando la console {{site.data.keyword.cloud_notm}} o l'interfaccia della riga di comando
{:shortdesc}

Il dominio condiviso predefinito è `mybluemix.net`, ma `appdomain.cloud` è un'altra opzione di dominio che puoi utilizzare. Per ulteriori informazioni sulla migrazione a `appdomain.cloud`, vedi [Aggiornamento del tuo dominio](/docs/apps/tutorials?topic=creating-apps-update-domain).
{: tip}

Per utilizzare un dominio personalizzato, devi registrare il dominio personalizzato su un server DNS pubblico e poi configurare tale dominio in {{site.data.keyword.cloud_notm}}. Successivamente, devi associare il dominio personalizzato al dominio di sistema {{site.data.keyword.cloud_notm}} sul server DNS pubblico. Dopo aver
associato il tuo dominio personalizzato al dominio di sistema,
le richieste per il tuo dominio personalizzato vengono instradate alla tua applicazione in {{site.data.keyword.cloud_notm}}.

## Aggiunta di un dominio personalizzato dalla console {{site.data.keyword.cloud_notm}} 
{: #custom-domain-console}

Completa questa procedura per aggiornare un dominio personalizzato per la tua organizzazione utilizzando la console:

1. Vai a **Gestisci > Account** e seleziona **Organizzazioni Cloud Foundry**.
2. Fai clic sul nome dell'organizzazione per cui stai creando un dominio personalizzato.
3. Fai clic sulla scheda **Domini** per visualizzare un elenco di domini disponibili.
4. Fai clic su **Aggiungi dominio**, immetti il tuo nome del dominio e seleziona la regione.
5. Conferma i tuoi aggiornamenti e fai clic su **Aggiungi**.

## Aggiunta della rotta con il dominio personalizzato a un'applicazione

1. Dalla [console {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") fai clic sull'icona **Menu** ![icona Menu](../../icons/icon_hamburger.svg) e seleziona **Elenco risorse**.
2. Sulla pagina **Elenco risorse**, fai clic su **Applicazioni Cloud Foundry**.
3. Fai clic sull'applicazione alla quale desideri aggiungere la rotta. Viene visualizzata la pagina **Panoramica** dell'applicazione.
4. Seleziona il menu **Rotte** e seleziona **Modifica rotte**.
5. Fai clic su **Aggiungi rotta** e specifica la rotta che vuoi utilizzare per l'applicazione.
6. Conferma i tuoi aggiornamenti facendo clic su **Salva**.

Come esempio, puoi utilizzare `*.mycompany.com` per associare la rotta `www.mybluemix.net` alla tua applicazione. Puoi anche utilizzare `example.mycompany.com` per associare la rotta `www.example.bluemix.net` all'applicazione.
{: tip}

## Aggiunta di un dominio personalizzato dall'interfaccia riga di comando {{site.data.keyword.cloud_notm}} 
{: #custom-domain-cli}

1. Per le applicazioni Cloud Foundry, esegui la connessione al tuo endpoint API Cloud Foundry immettendo il seguente comando:
   ```
   ibmcloud target --cf-api <CF_ENDPOINT>
   ```
   
   **Endpoint API Cloud Foundry:**
   * STATI UNITI SUD - `api.us-south.cf.cloud.ibm.com`
   * STATI UNITI EST - `api.us-east.cf.cloud.ibm.com`
   * EU-DE - `api.eu-de.cf.cloud.ibm.com`
   * EU-GB - `api.eu-gb.cf.cloud.ibm.com`
   * AU-SYD - `api.au-syd.cf.cloud.ibm.com`
   
2. Crea un dominio personalizzato per la tua organizzazione digitando il
seguente comando:
   ```
   ibmcloud app domain-create <MY_ORGNAME> <MY_DOMAIN>
   ```

3. Aggiungi la rotta con il dominio personalizzato a un'applicazione.

   Per le applicazioni Cloud Foundry, immetti il seguente comando:
   ```
   ibmcloud app route-map <MY_APPNAME> <MY_DOMAIN> -n <MY_HOSTNAME>
   ```
   
## Associazione del dominio personalizzato al dominio di sistema.
{: #mapcustomdomain}

Una volta configurato il dominio personalizzato in {{site.data.keyword.cloud_notm}}, associa il dominio personalizzato al dominio di sistema {{site.data.keyword.cloud_notm}} sul tuo server DNS registrato:

1. Imposta un record 'CNAME' per il nome dominio personalizzato sul tuo server DNS. La procedura per l'impostazione del record CNAME varia a seconda del tuo provider DNS. Ad esempio, se utilizzi GoDaddy, devi seguire le linee guida di [Domains Help ](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") fornite da GoDaddy.
2. Associare il nome dominio personalizzato all'endpoint sicuro della regione {{site.data.keyword.cloud_notm}} in cui viene eseguita la tua applicazione. Utilizza i seguenti endpoint della regione per fornire la rotta dell'URL assegnata alla tua organizzazione in {{site.data.keyword.cloud_notm}}. Ad esempio, fai puntare il tuo CNAME su `<custom-domain>.us-east.cf.cloud.ibm.com.`

  **Endpoint Cloud Foundry:**
  * STATI UNITI SUD - `custom-domain.us-south.cf.cloud.ibm.com`
  * STATI UNITI EST - `custom-domain.us-east.cf.cloud.ibm.com`
  * EU-DE - `custom-domain.eu-de.cf.cloud.ibm.com`
  * EU-GB - `custom-domain.eu-gb.cf.cloud.ibm.com`
  * AU-SYD - `custom-domain.au-syd.cf.cloud.ibm.com`

## Accesso alla tua applicazione
{: #access-app}

In un browser, immetti il seguente URL per accedere alla tua applicazione, dove `hostname` è il tuo nome host e `mydomain` è il tuo nome di dominio:
```
http://hostname.mydomain
```

## Rimozione di una rotta orfana 
{: #remove-orphaned-route}

Per rimuovere una rotta orfana, immetti il seguente comando:
```
ibmcloud app route-delete <MY_DOMAIN> -n <MY_HOSTNAME> -f
```
{: tip}

In tale esempio, `domain` è il nome del tuo dominio e `hostname` è il nome host della rotta per la tua applicazione. Per ulteriori informazioni sul comando `ibmcloud app route-delete`, immetti `ibmcloud app route-delete -h`.

## Utilizzo di un dominio personalizzato per le applicazioni Kubernetes
{: #kube-custom-domain}

Il dominio secondario per i nomi host IBM Cloud Kubernetes Service è `containers.appdomain.cloud`. Il dominio secondario jolly Ingress fornito da IBM, `*.<cluster_name>.<region>.containers.mybluemix.net`, viene registrato per impostazione predefinita per il tuo cluster. Il certificato TLS fornito da IBM è un certificato jolly e può essere utilizzato per il dominio secondario jolly. Se vuoi utilizzare un dominio personalizzato, devi registrarlo come un dominio jolly come ad esempio `*.custom_domain.net`. Per utilizzare TLS, devi ottenere un certificato jolly.
Per ulteriori informazioni, vedi [Più domini all'interno di uno spazio dei nomi](/docs/containers?topic=containers-ingress#multi-domains).

Consulta [questa esercitazione](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes) che ti guida nella struttura di un'applicazione web, eseguendola in locale in un contenitore e poi distribuendola a un cluster Kubernetes creato con IBM Kubernetes Service. Inoltre, imparerai come associare un dominio personalizzato, monitorare l'integrità dell'ambiente e ridimensionare l'applicazione.
