---

copyright:
  years: 2017, 2019
lastupdated: "2019-03-15"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Migration et hébergement d'applications
{: #hosting}

Si vous possédez déjà une application, vous pouvez l'héberger sur {{site.data.keyword.cloud}} avec tous les services d'infrastructure ou de plateforme dont vous avez besoin. Vous pouvez également faire migrer votre application vers {{site.data.keyword.cloud_notm}} de manière incrémentielle au lieu de déplacer toutes les parties de votre application en une seule fois vers l'environnement de cloud.

## Migration d'applications
{: #migrating}

Si votre application doit accéder à vos données ou à vos services sur site, vous pouvez utiliser [{{site.data.keyword.SecureGatewayfull}}](/docs/services/SecureGateway?topic=securegateway-getting-started-with-sg#getting-started-with-sg) pour établir un tunnel sécurisé entre une organisation {{site.data.keyword.cloud_notm}} et votre réseau de back end d'entreprise. Pour plus de détails, voir [Reaching enterprise backend with {{site.data.keyword.cloud_notm}} Secure Gateway via console ](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").

Des [services de migration {{site.data.keyword.cloud_notm}} ](https://www.ibm.com/cloud/migration-services){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") sont disponibles si vous avez besoin d'aide pour effectuer la migration.

## Hébergement d'applications
{: #ht_hostapp}

Dans {{site.data.keyword.cloud_notm}} [catalog](https://{DomainName}/catalog/?taxonomyNavigation=apps){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe"), vous pouvez choisir un environnement géré, tel que Kubernetes ou Cloud Foundry, ou vous pouvez héberger votre application directement sur un serveur bare metal ou un serveur virtuel.

Sur un déploiement virtuel, la majeure partie des opérations de votre application est gérée par {{site.data.keyword.cloud_notm}}. Un déploiement [virtuel](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers) est préférable si votre charge de travail est répartie sur plusieurs régions géographiques et que vous souhaitez utiliser un hyperviseur {{site.data.keyword.cloud_notm}} pour gérer vos déploiements. Un déploiement [bare metal](/docs/bare-metal?topic=bare-metal-bm-getting-started#getting-started) est optimal si vous avez besoin d'un accès direct à un serveur physique dédié pour de meilleures performances.

Vous disposez également de nombreuses options pour :
* Sélectionner le type de [stockage](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") qui vous convient : stockage par blocs, stockage de fichiers ou stockage d'objets.
* Sélectionner le type de [réseau](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")} dont vous avez besoin.
* Sélectionner un service de [conteneurisation](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=containers){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") pour bénéficier de la technologie Kubernetes {{site.data.keyword.cloud_notm}}.
