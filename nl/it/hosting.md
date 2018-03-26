---

copyright:
  years: 2017, 2018
lastupdated: "2017-01-26"

---

{:shortdesc: .shortdesc}

# Host delle applicazioni
{: #hosting}

Se disponi di un'applicazione esistente, puoi ospitarla su IBM Cloud con tutti i servizi di infrastruttura o piattaforma di cui hai bisogno. Per le applicazioni esistenti, puoi avvalerti dell'infrastruttura {{site.data.keyword.Bluemix_notm}} per ospitare le applicazioni che hai sviluppato appositamente per {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Migrazione di applicazioni
{: #ht_hostapp}

Per le applicazioni esistenti, puoi migrare le tue applicazioni in {{site.data.keyword.Bluemix_notm}} in modo incrementale, invece di spostare completamente l'applicazione nell'ambiente cloud. Puoi migrare prima una parte della tua applicazione e connetterla al system of record o ai dati esistenti attraverso il servizio Cloud Integration.

Per le tue applicazioni {{site.data.keyword.Bluemix_notm}}, potresti dover accedere ai dati o ai servizi di back-end, ad esempio un system of record. In {{site.data.keyword.Bluemix_notm}}, puoi utilizzare il servizio Secure Gateway per stabilire un tunnel protetto tra un'organizzazione {{site.data.keyword.Bluemix_notm}} e la rete di backend aziendale. Il servizio consente alle applicazioni su {{site.data.keyword.Bluemix_notm}} di accedere ai dati e ai servizi della rete di back-end. Per i dettagli, vedi [Reaching enterprise backend with Bluemix Secure Gateway via console ![Icona link esterno](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}.

{{site.data.keyword.Bluemix_notm}} può ospitare la tua applicazione esistente e fornire tutta l'infrastruttura di cui hai bisogno. Nel [catalogo](https://console.bluemix.net/catalog/?taxonomyNavigation=apps), puoi scegliere se ospitare la tua applicazione su un server bare metal o su un server virtuale. Un distribuzione [bare metal](../bare-metal/index.html#about-bare-metal-servers) è la soluzione migliore se hai bisogno di un server fisico dedicato per prestazioni più elevate. Una distribuzione [virtuale](/vsi/vsi_index.html#provisioning-a-virtual-server) è la soluzione migliore se il carico di lavoro è distribuito su aree geografiche e desideri utilizzare un hypervisor {{site.data.keyword.Bluemix_notm}} per gestire le tue distribuzioni.

Puoi migrare parti dell'applicazione in {{site.data.keyword.Bluemix_notm}} in una sola volta o componente per componente. Dai un'occhiata ad alcuni dei servizi che offriamo per la migrazione della tua applicazione.

* Seleziona il tipo di [archiviazione](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage) più adattato a te tra archiviazione a blocchi, archiviazione file o archiviazione oggetti.
* Seleziona il tipo di [rete](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork) di cui hai bisogno.
* Seleziona un servizio di [containerizzazione](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers) per sfruttare la tecnologia di {{site.data.keyword.Bluemix_notm}} Kubernetes.

## Passi successivi
{: #next-steps}

Se il tuo servizio può essere ospitato in più di una regione, puoi selezionare dove è ospitata la tua applicazione. Per farlo, registra e aggiungi le informazioni personalizzate sull'URL nella tua applicazione in {{site.data.keyword.Bluemix_notm}}. Quindi, seleziona le regioni in cui è ospitata la tua applicazione. Vedi [Aggiornamento di applicazioni](updapps.html) per ulteriori informazioni su come distribuire la tua applicazione.
