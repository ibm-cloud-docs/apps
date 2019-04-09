---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-04"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Migration et hébergement d'applications
{: #hosting}

Si vous possédez déjà une application, vous pouvez l'héberger sur {{site.data.keyword.cloud}} avec tous les services d'infrastructure ou de plateforme dont vous avez besoin. Vous pouvez également faire migrer votre application vers {{site.data.keyword.cloud_notm}} de manière incrémentielle au lieu de déplacer toutes les parties de votre application en une seule fois vers l'environnement de cloud.

## Migration d'applications
{: #migrating}

Si votre application doit accéder à vos données ou à vos services sur site, vous pouvez utiliser [{{site.data.keyword.SecureGatewayfull}}](/docs/services/SecureGateway/index.html#getting-started-with-sg) pour établir un tunnel sécurisé entre une organisation {{site.data.keyword.cloud_notm}} et votre réseau de back end d'entreprise. Pour plus de détails, voir [Reaching enterprise backend with {{site.data.keyword.cloud_notm}} Secure Gateway via console ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}.

Des [services de migration {{site.data.keyword.cloud_notm}}![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/cloud/migration-services){: new_window} sont disponibles si vous avez besoin d'aide pour effectuer la migration.

## Hébergement d'applications
{: #ht_hostapp}

Dans {{site.data.keyword.cloud_notm}} [catalog![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/catalog/?taxonomyNavigation=apps){: new_window}, vous pouvez choisir un environnement géré, tel que Kubernetes ou Cloud Foundry, ou vous pouvez héberger votre application directement sur un serveur bare metal ou un serveur virtuel.

Sur un déploiement virtuel, la majeure partie des opérations de votre application est gérée par {{site.data.keyword.cloud_notm}}. Un déploiement [virtuel](/docs/vsi/vsi_about.html) est préférable si votre charge de travail est répartie sur plusieurs régions géographiques et que vous souhaitez utiliser un hyperviseur {{site.data.keyword.cloud_notm}} pour gérer vos déploiements. Un déploiement [bare metal](/docs/bare-metal/index.html#getting-started) est optimal si vous avez besoin d'un accès direct à un serveur physique dédié pour de meilleures performances.

Vous disposez également de nombreuses options pour :
* Sélectionner le type de [stockage![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} qui vous convient : stockage par blocs, stockage de fichiers ou stockage d'objets.
* Sélectionner le type de [réseau![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} dont vous avez besoin.
* Sélectionner un service de [conteneurisation![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=containers){: new_window} pour bénéficier de la technologie Kubernetes {{site.data.keyword.cloud_notm}}.
