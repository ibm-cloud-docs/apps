---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, serverless, serverless app, functions, cli, api, sdk, create serverless app, serverless app tutorial

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Création d'applications sans serveur
{: #serverless}

Pour le développement sans serveur, vous pouvez utiliser les fonctions d'IBM en tant qu'offre de service (FaaS), {{site.data.keyword.openwhisk}}. Vous pouvez exécuter la logique d'application avec {{site.data.keyword.openwhisk_short}} en réponse aux événements ou aux appels directs effectués par des applications Web ou mobiles via HTTP sans mise à disposition ou gestion des serveurs. {{site.data.keyword.openwhisk_short}} effectue l'administration système (mise à l'échelle automatique, gestion de la disponibilité et maintenance, par exemple) afin que vous puissiez, en tant que développeur, vous concentrer sur la conception de la logique d'application.
{:shortdesc}

Vous pouvez utiliser l'interface utilisateur {{site.data.keyword.openwhisk_short}} ou l'interface de ligne de commande (CLI) pour développer vos applications. Les capacités en matière de développement d'applications de ces interfaces sont similaires. Cependant, l'interface CLI permet de mieux contrôler votre déploiement et vos opérations. Pour obtenir des informations détaillées sur {{site.data.keyword.openwhisk_short}}, consultez la [documentation](/docs/openwhisk?topic=cloud-functions-index).

## Interface utilisateur {{site.data.keyword.openwhisk_short}}
{: #serverless-apps-ui}

Utilisez {{site.data.keyword.openwhisk_short}} dans votre [navigateur](https://{DomainName}/openwhisk/actions){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")}. Accédez à la page [Concepts ](https://{DomainName}/openwhisk/learn){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe") pour avoir un aperçu de l'interface utilisateur {{site.data.keyword.openwhisk_short}}.

## Développement avec l'interface CLI
{: #openwhisk_start_configure_cli}

Pour en savoir plus sur l'installation et le développement avec l'interface de ligne de commande {{site.data.keyword.openwhisk_short}}, voir la page présentant la [configuration de l'interface de ligne de commande {{site.data.keyword.openwhisk_short}} ](https://{DomainName}/openwhisk/cli){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe").

## Exposition des API et des ensembles de données en tant qu'actions Web
{: #expose-actions}

Par défaut, {{site.data.keyword.openwhisk_short}} définit des actions pour lesquelles une clé d'authentification est requise. Dans des environnement mobiles de production, il est souvent nécessaire d'autoriser des clients mobiles à exposer des API et des ensembles de données spécifiques en fonction des flux OAuth.

{{site.data.keyword.openwhisk_short}} permet aux développeurs d'exposer leurs fonctions en tant qu'actions Web annotées afin de générer rapidement des applications Web. Vous pouvez programmer la logique de back end avec des actions annotées à laquelle votre application Web peut accéder de manière anonyme sans qu'aucune clé d'authentification {{site.data.keyword.openwhisk_short}} ne soit requise.

Pour exposer une action en tant qu'action Web, accédez à l'onglet **Noeuds finaux** de votre action et sélectionnez **Activer en tant qu'action Web**.

Désormais, les utilisateurs peuvent atteindre l'action à partir d'un navigateur ou d'une demande cURL, par exemple :
```
curl https://openwhisk.cloud.ibm.com/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

**Sortie :**
```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} inclut un [kit SDK mobile](/docs/openwhisk?topic=cloud-functions-openwhisk_mobile_sdk) pour les appareils iOS et watchOS. Ainsi, les applications mobiles peuvent envoyer plus facilement des déclencheurs distants et appeler des actions distantes. Un [kit SDK d'infrastructure sans serveur ](/docs/openwhisk?topic=cloud-functions-openwhisk_goserverless){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe") qui active les applications sans serveur est également disponible.

