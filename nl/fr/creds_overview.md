---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-10"

keywords: apps, credentials, service, add service credentials, environment, deployment

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# Ajout manuel des informations d'identification de service à votre environnement de déploiement
{: #credentials_overview}

Vous voulez que votre logique applicative acquière des données d'identification de service sensibles, telles que des clés d'API de base de données ou des mots de passe, dans l'environnement dans lequel votre application s'exécute. De cette façon, vous n'avez pas besoin de conserver vos données d'identification dans votre référentiel de code source.
{: shortdesc}

Si vous créez une application en utilisant un kit de démarrage, l'environnement est automatiquement préparé pour vous. Lorsque vous connectez un service à votre kit de démarrage avant de déployer votre application, les données d'identification du service sont automatiquement ajoutées à votre environnement.
{ :tip}

Vous devez ajouter manuellement les données d'identification de service à votre environnement de déploiement dans les deux scénarios suivants :

 * Lorsque vous utilisez votre propre code.
 * Lorsque vous ajoutez un service à une application basée sur un kit de démarrage après le déploiement de l'application.

Le processus d'ajout des données d'identification de service dépend de votre cible de déploiement et de votre langage de programmation. Pour plus d'informations sur la configuration des données d'identification de service pour votre cible de déploiement, consultez la documentation spécifique à votre environnement d'hébergement :

  * [{{site.data.keyword.containershort}}](/docs/containers?topic=containers-service-binding#adding_app)
  * Cloud Foundry Public ou {{site.data.keyword.cfee_full}}
  * Instance de serveur virtuel (conteneur Docker local)

Un grand nombre de langages et d'infrastructures fournissent des bibliothèques standard pour les configurations spécifiques aux applications et à l'environnement. Pour plus d'informations, voir les guides de programmation suivants :

* [Java: Working with service credentials](/docs/java?topic=cloud-native-configuration)
* [Configuration de l'environnement Node.js](/docs/node?topic=nodejs-configure-nodejs)
* [Configuration de l'environnement Spring](/docs/java?topic=java-spring-configuration)
* [Configuration de l'environnement Swift](/docs/swift?topic=swift-configuration)
* [Configuration de l'environnement Go](/docs/go?topic=go-configure-go-env)
