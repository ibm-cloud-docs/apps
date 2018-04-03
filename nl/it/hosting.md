---

copyright:
  years: 2017, 2018
lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Migrazione e hosting delle applicazioni
{: #hosting}

Se disponi di un'applicazione esistente, puoi ospitarla su {{site.data.keyword.Bluemix}} con tutti i servizi di infrastruttura o piattaforma di cui hai bisogno. Puoi anche migrare la tua applicazione a {{site.data.keyword.Bluemix_notm}} in modo incrementale invece di spostarla all'ambiente cloud in una singola operazione. 

## Migrazione di applicazioni
{: #migrating}

Se hai bisogno della tua applicazione per accedere ai tuoi servizi o dati in loco, puoi utilizzare [{{site.data.keyword.SecureGatewayfull}}](../services/SecureGateway/secure_gateway.html) per stabilire un tunnel protetto tra un'organizzazione {{site.data.keyword.Bluemix_notm}} e la rete di backend aziendale. Per i dettagli, vedi [Reaching enterprise backend with {{site.data.keyword.Bluemix_notm}} Secure Gateway via console ](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} ![Icona link esterno](../icons/launch-glyph.svg).

Se hai bisogno di aiuto con la tua migrazione, [IBM Cloud Migration Services](https://www.ibm.com/cloud/migration-services){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") sono disponibili.

## Host delle applicazioni
{: #ht_hostapp}

Nel {{site.data.keyword.Bluemix_notm}} [catalogo](https://console.bluemix.net/catalog/?taxonomyNavigation=apps){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno"), puoi scegliere un ambiente gestito come Kubernetes o Cloud Foundry o puoi ospitare la tua applicazione direttamente su un server bare metal o virtuale.

In una distribuzione virtuale, la maggior parte delle operazioni della tua applicazione sono gestite da {{site.data.keyword.Bluemix_notm}}. Una distribuzione [virtuale](../vsi/vsi_about.html) è la soluzione migliore se il carico di lavoro è distribuito su aree geografiche e desideri utilizzare un hypervisor {{site.data.keyword.Bluemix_notm}} per gestire le tue distribuzioni. Un distribuzione [bare metal](../bare-metal/index.html) è la soluzione migliore se hai bisogno dell'accesso diretto a un server fisico dedicato per prestazioni più elevate. 

Hai anche molte opzioni per: 
* Selezionare il tipo di [archiviazione](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") più adattato a te tra archiviazione a blocchi, archiviazione file o archiviazione oggetti.
* Selezionare il tipo di [rete](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") di cui hai bisogno.
* Selezionare un servizio di [containerizzazione](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") per sfruttare la tecnologia di {{site.data.keyword.Bluemix_notm}} Kubernetes.
