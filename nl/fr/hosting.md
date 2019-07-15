---

copyright:
  years: 2017, 2019
lastupdated: "2019-06-25"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Choix de votre environnement d'hébergement
{: #hosting}

Si vous possédez déjà une application, vous pouvez l'héberger sur {{site.data.keyword.cloud}} avec tous les services d'infrastructure ou de plateforme dont vous avez besoin.
{:shortdesc}

Avec {{site.data.keyword.cloud_notm}}, il n'est plus nécessaire d'effectuer d'investissements importants en termes de matériel pour tester ou exécuter une nouvelle application. A la place, nous gérons tout pour vous et ne vous facturons que ce que vous utilisez. Votre environnement de serveur Cloud constitue la base de votre couche d'infrastructure. Vous pouvez choisir une seule option ou un ensemble d'options pour plusieurs environnements complexes. 

Vous disposez de plusieurs options pour l'hébergement de vos applications, ce qui vous permet d'avoir le niveau de contrôle souhaité ou requis sur l'infrastructure. Vous pouvez exécuter votre application de l'une des façons suivantes :

  * En tant que conteneur Docker sur un cluster Kubernetes
  * En tant qu'application Cloud Foundry
  * En tant que fonction sans serveur
  * En tant que VMware
  * En tant que machine virtuelle
  * Sur {{site.data.keyword.baremetal_short}} à hautes performances 
<!--
{{site.data.keyword.baremetal_short}} are single-tenant, physical servers that are dedicated to a single customer. You control almost everything from the server host to the RAM and storage devices. These servers are used with workloads that require compute power over a sustained time, for example, several months.

Some example workloads include e-commerce, ERP, CRM, SCM, and financial services and regulatory applications.

{{site.data.keyword.BluVirtServers_short}} can be deployed as either as public or dedicated instances. With public instances, the resources of the server are shared with other customers, also known as a multi-tenant environment. Private instances dedicate the resources of the physical server to one customer who can have one or more virtual machines on the same server. These servers are ideal for workloads that run for a limited time, for example, a couple of weeks. Some workload examples are development and testing, backup and recovery, and disaster recovery. For more information about server options, see [Bare metal servers versus virtual servers: Choosing the best option for you](https://www.ibm.com/cloud/blog/bare-metal-virtual-servers-works){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").
-->

Consultez le tableau suivant pour obtenir un récapitulatif de vos options de calcul.

| Option | Description | 
|--------|---------------|
| [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started) | Associe les conteneurs Docker, la technologie Kubernetes, une expérience utilisateur intuitive ainsi que l'isolement et la sécurité intégrés permettant d'automatiser le déploiement, le fonctionnement, la mise à l'échelle et la surveillance des applications conteneurisées dans un cluster d'hôtes de calcul. |
| [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) | Instancie à la demande plusieurs plateformes Cloud Foundry d'entreprise isolées. |
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-getting_started) | Plateforme de programmation FaaS (Functions-as-a-Service) basée sur Apache OpenWhisk. |
| [{{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started) | Intègre ou migre rapidement et en toute transparence des charges de travail VMware locales en utilisant une infrastructure évolutive, sécurisée et à hautes performances ainsi que la technologie de virtualisation hybride VMware de pointe. |
| [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-public-virtual-servers) | Serveurs virtuels évolutifs achetés avec des coeurs dédiés et des allocations de mémoire. |
| [{{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-about-bm)  | Serveurs à service exclusif horaires ou mensuels qui vous sont dédiés et qui ne sont pas partagés (notamment les ressources de serveur) avec d'autres clients. |
{: caption="Tableau 1. Options de calcul" caption-side="top"}

