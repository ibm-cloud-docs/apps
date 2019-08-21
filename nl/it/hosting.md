---

copyright:
  years: 2017, 2019
lastupdated: "2019-06-25"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Scelta del tuo ambiente host
{: #hosting}

Se disponi di un'applicazione esistente, puoi ospitarla su {{site.data.keyword.cloud}} con tutti i servizi di infrastruttura o piattaforma di cui hai bisogno.
{:shortdesc}

Con {{site.data.keyword.cloud_notm}}, non devi più affrontare grandi investimenti in hardware per testare o eseguire una nuova applicazione. Saremo invece noi a gestire il tutto e pagherai solo per ciò che usi. Il tuo ambiente server cloud è la base del tuo livello dell'infrastruttura. Puoi scegliere una sola opzione o una combinazione per ambienti più complessi. 

Hai diverse opzioni per ospitare le tue applicazioni, fornendoti maggiore controllo sull'infrastruttura quando vuoi o ne hai bisogno. Puoi eseguire la tua applicazione in uno dei seguenti modi:

  * Come un contenitore Docker su un cluster Kubernetes
  * Come un'applicazione Cloud Foundry
  * Come una funzione senza server
  * Come VMware
  * Come una macchina virtuale
  * Su {{site.data.keyword.baremetal_short}} ad elevate prestazioni 
  
<!--
{{site.data.keyword.baremetal_short}} are single-tenant, physical servers that are dedicated to a single customer. You control almost everything from the server host to the RAM and storage devices. These servers are used with workloads that require compute power over a sustained time, for example, several months.

Some example workloads include e-commerce, ERP, CRM, SCM, and financial services and regulatory applications.

{{site.data.keyword.BluVirtServers_short}} can be deployed as either as public or dedicated instances. With public instances, the resources of the server are shared with other customers, also known as a multi-tenant environment. Private instances dedicate the resources of the physical server to one customer who can have one or more virtual machines on the same server. These servers are ideal for workloads that run for a limited time, for example, a couple of weeks. Some workload examples are development and testing, backup and recovery, and disaster recovery. For more information about server options, see [Bare metal servers versus virtual servers: Choosing the best option for you](https://www.ibm.com/cloud/blog/bare-metal-virtual-servers-works){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").
-->

Consulta la seguente tabella per un riepilogo delle tue opzioni di calcolo.

| Opzione | Descrizione | 
|--------|---------------|
| [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started) | Combina i contenitori Docker e la tecnologia Kubernetes, un'esperienza utente intuitiva e la sicurezza e l'isolamento integrati per automatizzare la distribuzione, il funzionamento, il ridimensionamento e il monitoraggio di applicazioni caricate nei contenitori in un cluster di host di calcolo. |
| [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) | Istanzia più piattaforme Cloud Foundry isolate e di livello aziendale su richiesta. |
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-getting_started) | Una piattaforma di programmazione FaaS (Functions-as-a-Service) basata su Apache OpenWhisk. |
| [{{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started) | Integra o migra velocemente e facilmente i carichi di lavoro VMware in loco utilizzando l'infrastruttura ad elevate prestazioni, sicura e scalabile e la tecnologia di virtualizzazione ibrida VMware leader nel settore. |
| [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-public-virtual-servers) | Server virtuali scalabili acquistati con allocazioni di memoria e core dedicati. |
| [{{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-about-bm)  | Server a singolo tenant orari o mensili, a te dedicati e di cui nessuna loro parte, comprese le risorse server, è condivisa con altri clienti. |
{: caption="Tabella 1. Opzioni di calcolo" caption-side="top"}

