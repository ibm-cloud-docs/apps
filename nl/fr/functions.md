---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-29"

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

Pour le développement sans serveur, vous pouvez utiliser {{site.data.keyword.openwhisk}}, l'offre Faas (Functions-as-a-Service) d'IBM. Vous pouvez exécuter la logique d'application avec {{site.data.keyword.openwhisk_short}} en réponse aux événements ou aux appels directs effectués par des applications Web ou mobiles via HTTP sans mise à disposition ou gestion des serveurs. {{site.data.keyword.openwhisk_short}} effectue l'administration système (telle que la mise à l'échelle automatique, la gestion de la disponibilité et la maintenance) afin que vous puissiez, en tant que développeur, vous concentrer sur la conception de la logique d'application.
{:shortdesc}

Vous pouvez développer vos applications sans serveur en utilisant l'une des méthodes suivantes :
* Interface utilisateur (IU) {{site.data.keyword.openwhisk_short}}.
* Interface de ligne de commande (CLI) {{site.data.keyword.openwhisk_short}}, qui permet de mieux contrôler votre développement et vos opérations.
* Kit de démarrage {{site.data.keyword.openwhisk_short}}, dans lequel vous pouvez configurer la distribution continue à l'aide d'une chaîne d'outils DevOps et d'une pipeline de livraison.

Pour obtenir des informations détaillées sur {{site.data.keyword.openwhisk_short}}, consultez la [documentation](/docs/openwhisk?topic=cloud-functions-getting_started).


## Développement avec l'interface utilisateur {{site.data.keyword.openwhisk_short}}
{: #serverless-apps-ui}

Utilisez {{site.data.keyword.openwhisk_short}} dans votre [navigateur](https://{DomainName}/functions/actions){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")}. Accédez à la page [Concepts ](https://{DomainName}/functions/learn){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") pour avoir un aperçu de l'interface utilisateur {{site.data.keyword.openwhisk_short}}.

## Développement avec l'interface CLI
{: #openwhisk_start_configure_cli}

Pour en savoir plus sur l'installation et le développement avec l'interface de ligne de commande {{site.data.keyword.openwhisk_short}}, voir [Configuration de l'interface de ligne de commande {{site.data.keyword.openwhisk_short}}](https://{DomainName}/functions/cli){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe").

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

Sortie :
```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} inclut un [kit SDK mobile](/docs/openwhisk?topic=cloud-functions-pkg_mobile_sdk) pour les appareils iOS et watchOS. Ainsi, les applications mobiles peuvent envoyer plus facilement des déclencheurs distants et appeler des actions distantes.

## Création d'applications sans serveur à l'aide d'un kit de démarrage
{: #serverless-starter}

Vous pouvez utiliser un kit de démarrage pour créer une application sans serveur, par exemple Python Example Serverless App. Pour localiser les kits de démarrage, procédez comme suit :

1. Accédez à la page [App Service Starter Kits](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") dans la console {{site.data.keyword.dev_console}}.
2. Entrez `serverless` dans la barre de recherche pour filtrer la liste des kits de démarrage.
3. Sélectionnez un kit de démarrage sans serveur, par exemple Python Example Serverless App.
4. Nommez votre application et sélectionnez un groupe de ressources.
5. Facultatif. Créez des étiquettes pour classer votre application. Pour plus d'informations, voir [Utilisation d'étiquettes](/docs/resources?topic=resources-tag).
6. Créez ou sélectionnez une instance de service Cloudant existante.
7. Facultatif. Pour inspecter votre code avant d'ajouter des services ou de déployer votre application, cliquez sur **Afficher le code source**. Vérifiez le fichier `README.md` pour savoir si vous devez effectuer d'autres actions pour faire fonctionner votre application.
8. Cliquez sur **Créer**.

C'est un bon début ! Vous venez de créer une application !

## Ajout de services (facultatif)
{: #serverless-services}

Si un kit de démarrage nécessite des services spécifiques, des services fournis automatiquement sont disponibles pour que des instances de ces services soient automatiquement créées lorsque vous créez votre application.

1. Sur la page Détails de l'application, cliquez sur **Créer un service**, ou sur **Connecter les services existants** si vous avez déjà des services que vous souhaitez connecter à cette application.
2. Sélectionnez le type de service que vous souhaitez et suivez les invites pour ajouter un service existant à votre application ou pour créer une instance de service.

Une fois que tous les services souhaités ont été ajoutés, ils s'affichent sur la page Détails de l'application.

## Déploiement de votre application
{: #serverless-deploy}

Pour déployer votre application, procédez comme suit :

1. Sur la page Détails de l'application, cliquez sur **Déployer**.
2. Sélectionnez **Déployer dans Cloud Functions**, puis cliquez sur **Suivant**.
3. Sur la page Configurer la chaîne d'outils, entrez un nom de chaîne d'outils, sélectionnez une région, puis cliquez sur **Créer**. Après avoir sélectionné et configuré la cible de déploiement, la page Détails de l'application indique que la distribution continue est configurée. 
4. Facultatif. Passez les actions en revue dans la console {{site.data.keyword.openwhisk_short}} en cliquant sur l'icône Actions ![Icône Plus d'actions](../icons/action-menu-icon.svg) et en sélectionnant **Open Cloud Functions**.
5. Facultatif. Affichez le référentiel contenant le code généré pour votre application et vos services en cliquant sur **Afficher le référentiel**.

## Vérification du déploiement de votre application
{: #serverless-verify}

Avec une chaîne d'outils correctement configurée, un cycle de génération-déploiement démarre automatiquement lors de chaque fusion vers la branche principale de votre référentiel. Pour plus d'informations, voir [Génération et déploiement](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

Pour vérifier que votre application est correctement déployée, procédez comme suit :

1. Sur la page Détails de l'application, cliquez sur **Afficher la chaîne d'outils**.
2. Cliquez sur **Delivery Pipeline**. Vous pouvez alors démarrer des générations, gérer le déploiement et afficher les journaux et l'historique.
3. Si le déploiement a abouti, chaque étape de pipeline indique **Réussite de l'étape**.
4. Pour afficher l'action et les informations relatives à l'API, cliquez sur **Afficher les journaux et l'historique** dans le pavé **Etape de déploiement**.
