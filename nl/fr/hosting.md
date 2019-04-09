---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# Hébergement d'applications
{: #hosting}

Si vous possédez déjà une application, vous pouvez l'héberger sur IBM Cloud avec tous les services d'infrastructure ou de plateforme dont vous avez besoin. Vous pouvez également profiter de l'infrastructure {{site.data.keyword.Bluemix_notm}} pour héberger des applications que vous avez développées de façon spécifique pour {{site.data.keyword.Bluemix_notm}}.
{:shortdesc}

## Migration d'applications
{: #ht_hostapp}

Vous pouvez migrer vos applications dans {{site.data.keyword.Bluemix_notm}} de façon incrémentielle au lieu de les envoyer intégralement dans l'environnement de cloud. Vous pouvez d'abord migrer une partie de votre application puis vous connecter aux
données ou au système d'enregistrement qui existent en utilisant le service Cloud Integration.

Pour vos applications {{site.data.keyword.Bluemix_notm}}, vous pouvez avoir besoin d'accéder aux données de back end ou à des services comme un système d'enregistrement. Dans {{site.data.keyword.Bluemix_notm}}, vous pouvez utiliser le service Secure Gateway afin d'établir un tunnel sécurisé entre une organisation {{site.data.keyword.Bluemix_notm}} et le réseau de back end de l'entreprise. Le service permet aux applications dans {{site.data.keyword.Bluemix_notm}} d'accéder aux données et aux services du réseau de back end. Pour plus de détails, voir [Reaching enterprise backend with Bluemix Secure Gateway via console ![Icône de lien externe](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}.

{{site.data.keyword.Bluemix_notm}} peut héberger votre application existante et fournir toute l'infrastructure de {{site.data.keyword.Bluemix_notm}}. Dans le [catalogue](https://console.bluemix.net/catalog/?taxonomyNavigation=apps), vous pouvez choisir si vous hébergez votre application dans le cloud sur un serveur bare metal ou sur un serveur virtuel. 

Vous pouvez migrer des parties de l'application vers {{site.data.keyword.Bluemix_notm}} en une seule fois ou bien composant par composant. Vous pouvez consulter quelques-uns des services que nous offrons lors de la migration de votre application.

* Sélectionnez le type de [stockage](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage) qui vous convient : stockage par blocs, stockage de fichiers, ou stockage d'objets.
* Sélectionnez le type de [réseau](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork) dont vous avez besoin.
* Sélectionnez un service de [conteneurisation](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers) afin de bénéficier de la technologie Kubernetes de {{site.data.keyword.Bluemix_notm}}.

## Etapes suivantes
{: #next-steps}

Si votre service peut être hébergé sur plusieurs régions, vous pouvez sélectionner la région de votre choix. Dans [Mise à jour d'applications](updapps.html), vous pouvez sélectionner les régions où votre application est hébergée et éditer votre URL personnalisée.
