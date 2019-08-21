---

copyright:
  years: 2019
lastupdated: "2019-06-03"

keywords: apps, custom, domain, kubernetes, cloud foundry, add, subdomain, custom domain, dns, domainname, domain name, endpoint, update, migrate

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Gestione dei tuoi domini
{: #update-domain}

I domini forniscono la rotta dell'URL assegnata alla tua organizzazione in {{site.data.keyword.cloud}}. I domini personalizzati indirizzano le richieste per le tue applicazioni a un URL che ti appartiene. Il dominio personalizzato può essere un dominio condiviso, un dominio secondario condiviso
o un dominio e un host condivisi. A meno che non venga specificato un dominio personalizzato, nell'instradamento alla tua applicazione, {{site.data.keyword.cloud_notm}} utilizza un dominio condiviso predefinito. Il processo per la gestione dei domini dipende dalla tua destinazione di distribuzione, come ad esempio {{site.data.keyword.containershort}}, Cloud Foundry e altri.
{:shortdesc}

Per utilizzare un dominio personalizzato, devi registrare il dominio personalizzato su un server DNS pubblico e poi configurare tale dominio in {{site.data.keyword.cloud_notm}}. Successivamente, devi associare il dominio personalizzato al dominio di sistema {{site.data.keyword.cloud_notm}} sul server DNS pubblico. Dopo aver associato il tuo dominio personalizzato al dominio di sistema, le richieste per il tuo dominio personalizzato vengono instradate alla tua applicazione in {{site.data.keyword.cloud_notm}}.

## Modifica del tuo dominio per le applicazioni Kubernetes
{: #update-domain-kube}

Il dominio secondario per i nomi host {{site.data.keyword.containershort_notm}} è `containers.appdomain.cloud`. Il dominio secondario jolly Ingress fornito da IBM, `*.<cluster_name>.<region>.containers.appdomain.cloud`, viene registrato per impostazione predefinita per il tuo cluster. Il certificato TLS fornito da IBM è un certificato jolly e può essere utilizzato per il dominio secondario jolly. Per ulteriori informazioni, vedi [Più domini all'interno di uno spazio dei nomi](/docs/containers?topic=containers-ingress#multi-domains).

## Utilizzo di un dominio personalizzato per le applicazioni Kubernetes
{: #custom-domain-kube}

Se vuoi utilizzare un dominio personalizzato, devi registrarlo come un dominio jolly, ad esempio `*.custom_domain.net`. Per utilizzare TLS, devi ottenere un certificato jolly. Per ulteriori informazioni, vedi [Più domini all'interno di uno spazio dei nomi](/docs/containers?topic=containers-ingress#multi-domains).

Consulta [questa esercitazione](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes) che ti guida nella struttura di un'applicazione web, eseguendola in locale in un contenitore e poi distribuendola a un cluster Kubernetes creato con IBM Kubernetes Service. Inoltre, l'esercitazione ti mostra come eseguire il bind di un dominio personalizzato, monitorare l'integrità dell'ambiente e ridimensionare l'applicazione.

## Modifica del tuo dominio per le applicazioni Cloud Foundry
{: #update-domain-cf}

Per le applicazioni Cloud Foundry, puoi modificare il tuo dominio da `mybluemix.net` a `appdomain.cloud` utilizzando la console o la CLI (command-line interface) {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni su come modificare il tuo dominio in `appdomain.cloud`, vedi [Aggiornamento del tuo dominio](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).

Il dominio condiviso predefinito è `mybluemix.net`, ma `appdomain.cloud` è un'altra opzione di dominio che puoi utilizzare.
{: tip}

## Utilizzo di un dominio personalizzato per le applicazioni Cloud Foundry
{: #custom-domain-cf}

Per le applicazioni Cloud Foundry, puoi creare e utilizzare un dominio personalizzato mediante la console o la CLI (command-line interface) {{site.data.keyword.cloud_notm}}. Per ulteriori informazioni, vedi [Aggiunta e utilizzo di un dominio personalizzato](/docs/cloud-foundry-public?topic=cloud-foundry-public-custom-domains).
