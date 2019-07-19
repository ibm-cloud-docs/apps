---

copyright:
  years: 2019
lastupdated: "2019-03-15"

keywords: apps, domain, Kubernetes, Cloud Foundry, cli

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Aggiornamento del tuo dominio
{: #update-domain}

I domini forniscono la rotta dell'URL assegnata alla tua organizzazione in {{site.data.keyword.cloud}}. Per le applicazioni Cloud Foundry, puoi migrare il tuo dominio da `mybluemix.net` a `appdomain.cloud` utilizzando la console {{site.data.keyword.cloud_notm}} o l'interfaccia riga di comando.
{:shortdesc}

## Aggiornamento dei domini dalla console {{site.data.keyword.cloud_notm}} 
{: #update-domain-console}

Il dominio condiviso predefinito è `mybluemix.net`, ma `appdomain.cloud` è un'altra opzione di dominio che puoi utilizzare.
{: tip}

Completa questa procedura per aggiornare il dominio per la tua organizzazione Cloud Foundry utilizzando la console:

1. Dalla [console {{site.data.keyword.cloud_notm}} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}){: new_window}, fai clic sull'icona **Menu** ![icona Menu](../icons/icon_hamburger.svg) e seleziona **Elenco risorse**.
2. Sulla pagina **Elenco risorse**, fai clic su **Applicazioni Cloud Foundry**.
3. Fai clic sull'applicazione di cui vuoi modificare il dominio. Viene visualizzata la pagina **Panoramica** dell'applicazione.
4. Seleziona il menu **Rotte**, prendi nota del dominio corrente, ad esempio `<myapp.mybluemix.net>` e fai clic su **Modifica rotte**.
5. Seleziona l'elenco di domini e poi fai clic sul dominio che vuoi utilizzare, ad esempio `us-south.cf.appdomain.cloud`.
6. Conferma i tuoi aggiornamenti facendo clic su **Salva**.
7. Conferma di voler sostituire il vecchio dominio e fai clic su **Rimuovi**.
8. Per verificare che la nuova rotta stia funzionando, fai clic su **Visita URL applicazione**.

## Aggiornamento dei domini dall'interfaccia riga di comando {{site.data.keyword.cloud_notm}} 
{: #update-domain-cli}

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

2. Aggiungi la rotta con il nuovo dominio a un'applicazione digitando il seguente comando:
   ```
   ibmcloud app route-map APP_NAME DOMAIN -n HOSTNAME
   ```

## Aggiornamento del tuo dominio per le applicazioni Kubernetes
{: #update-domain-kube}

Il dominio secondario per i nomi host {{site.data.keyword.containerlong}} è `containers.appdomain.cloud`. Il dominio secondario jolly Ingress fornito da IBM, `*.<cluster_name>.<region>.containers.appdomain.cloud`, viene registrato per impostazione predefinita per il tuo cluster. Il certificato TLS fornito da IBM è un certificato jolly e può essere utilizzato per il dominio secondario jolly. Per ulteriori informazioni, vedi [Più domini all'interno di uno spazio dei nomi](/docs/containers?topic=containers-ingress#multi-domains).
