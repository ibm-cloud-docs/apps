---

copyright:
  years: 2017, 2018
lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creazione di un'applicazione personalizzata 
{: #build-your-own}

Se non stai utilizzando un kit starter e non sai di cosa hai bisogno, puoi creare la tua applicazione con le risorse che scegli.
{: shortdesc}

## Scelta del linguaggio 
{: #catalog}

Il catalogo {{site.data.keyword.Bluemix_notm}} elenca le risorse di infrastruttura e piattaforma disponibili per l'utilizzo. Puoi iniziare a creare la tua applicazione selezionando una macchina virtuale, un contenitore o un'applicazione Cloudant o Cloud Foundry. Se hai bisogno di risorse della piattaforma, {{site.data.keyword.Bluemix_notm}} offre anche dei [contenitori tipo](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=blueprints), che forniscono runtime e altri servizi per aiutarti a iniziare a costruire.

## Creazione di una risorsa
{: #resource}

1. Nel tuo [dashboard](https://console.bluemix.net/dashboard/apps/), fai clic su **Crea risorsa**.

2. Dal catalogo, seleziona un'applicazione dalla sezione Piattaforma. Quindi, seleziona il tuo runtime. Ad esempio, puoi scegliere un ambiente di runtime IBM, come Liberty for Java, che è supportato dai pacchetti di build IBM. Puoi anche scegliere runtime di community, come Tomcat, che si basano su pacchetti di build open source e di terze parti. 

  * [Introduzione ai contenitori](../containers/container_index.html)
  * [Introduzione a Openwhisk](../openwhisk/index.html)
  * [Creazione di applicazioni Cloud Foundry](../cfapps/index.html#creating_cloud_foundry_apps)

3. Inserisci il nome applicazione, il nome host e scegli il piano dei prezzi. 

4. Seleziona il tuo stile di sviluppo. Puoi modificare la tua applicazione nell'editor di testo preferito e utilizzare la riga di comando {{site.data.keyword.Bluemix_notm}} per distribuirla a {{site.data.keyword.Bluemix_notm}}. Puoi anche utilizzare i servizi {{site.data.keyword.Bluemix_notm}} DevOps per distribuire la tua applicazione da un browser o utilizzare Eclipse Tools for {{site.data.keyword.Bluemix_notm}} per lavorare sulle applicazioni nell'ambiente di sviluppo integrato di Eclipse.

## Aggiunta del codice 
{: #code}

Ogni applicazione viene fornita con una sezione introduttiva che ti aiuta a ottenere tutto il software e i contenuti necessari per iniziare a lavorare.

Nel dashboard, fai clic sulla tua applicazione e quindi su **Introduzione**, che può aiutarti a ottenere il software necessario per sviluppare la tua applicazione, indirizzarti al codice di origine e aiutarti a distribuire l'applicazione per la prima volta.

## Passi successivi
{: #next}

Continua a personalizzare la tua applicazione per adattarla alle tue esigenze. Controlla i seguenti suggerimenti per estendere la tua applicazione per raggiungere i risultati di business: 

* Rendi la tua applicazione più robusta aggiungendo [sicurezza](https://console.bluemix.net/catalog/?taxonomyNavigation=data&category=security){:new_window}, [monitoraggio](https://console.bluemix.net/catalog/?category=devops){:new_window} e i miglioramenti alla disponibilità descritti nella nostra guida di [procedure consigliate](best-practice.html).
* Rendi la tua applicazione più intelligente con [servizi cognitivi Watson](https://console.bluemix.net/catalog/?taxonomyNavigation=data&category=watson){:new_window} e [analisi avanzate e machine learning](https://console.bluemix.net/catalog/?taxonomyNavigation=data&category=data){:new_window}.
* Vai a [mobile](https://console.bluemix.net/catalog/?category=mobile){:new_window}.
* Prova [Internet of Things](https://console.bluemix.net/catalog/?category=iot){:new_window}.
* Utilizza i servizi come [API Connect](https://console.bluemix.net/catalog/?category=integration){:new_window} per integrare le [azioni senza server](https://console.bluemix.net/catalog/?category=whisk){:new_window}.

