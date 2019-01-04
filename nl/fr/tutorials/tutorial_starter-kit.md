---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Création d'une application à l'aide d'un kit de démarrage
{: #create_starterkit}

Vous pouvez utiliser un kit de démarrage pour que votre application démarre rapidement et pour la préparer à des développements futurs. Choisissez un kit de démarrage et un langage de programmation, créez une application, puis configurez une chaîne d'outils DevOps pour déployer automatiquement votre application. Vous pouvez également télécharger le code pour un examen immédiat.
{: shortdesc}

Vous pouvez créer une application en utilisant des kits de démarrage, notamment un kit vide si vous voulez personnaliser vous-même les options de génération. Quoi qu'il en soit, une chaîne d'outils est automatiquement créée pour le déploiement de votre application. Vous pouvez également télécharger le code pour un examen immédiat.

Les kits de démarrage sont disponibles dans de nombreuses catégories, telles que les suivantes :
* [Watson ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/watson/dashboard){:new_window}
* [Apple ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/appledevelopment/dashboard){:new_window}
* [Mobile ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/mobile/dashboard){:new_window}
* [Application Web ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/appservice/dashboard){:new_window}
* [Sécurité ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/security/dashboard){:new_window}
* [Finance ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/finance/dashboard){:new_window}

## Etape 1. Créer une application
{: #create-app}

1. A partir du tableau de bord [{{site.data.keyword.cloud}}](https://{DomainName}), cliquez sur l'icône **Menu** ![Icône Menu](../../icons/icon_hamburger.svg) > **Applications Web**.

2. Cliquez sur **Initiation** dans la section **Démarrer à partir du Web**.

3. Sélectionnez un kit de démarrage de votre choix, lisez les détails, puis cliquez sur **Créer**.
    
    Pour savoir ce qui est inclus dans le kit de démarrage, développez la vignette sur le tableau de bord des [kits de démarrage de service d'application ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/appservice/starter-kits){:new_window}. L'option de kit de démarrage "Créer une appli" peut être utilisée en tant qu'application Starter vide puis être personnalisée afin de répondre à vos besoins.
    {: tip}

4. Donnez un nom à votre application, sélectionnez votre langage, puis cliquez sur **Créer**.
    
    C'est un bon début ! Vous venez de créer une application.

Pour examiner votre code, cliquez sur **Télécharger le code** sur la page des détails d'application. Consultez le fichier `README.md` se trouvant dans le fichier compressé téléchargé pour savoir si vous devez exécuter d'autres actions pour rendre votre application de démarrage opérationnelle.
{: tip}

Pour plus d'informations, voir [Création d'une application Web basique avec un kit de démarrage](/docs/apps/tutorials/tutorial_web.html).

## Etape 2. Ajouter des ressources
{: #add-services}

Vous pouvez ajouter des ressources qui améliorent votre application avec la puissance cognitive de Watson, ajoutent des services mobiles ou des services de sécurité. Pour ce tutoriel, ajoutez un emplacement pour gérer vos données.

1. Dans la fenêtre de service d'application, cliquez sur **Ajouter une ressource**.
2. Sélectionnez le type de service souhaité. Par exemple, sélectionnez **Données** > **Suivant** > **Cloudant** > **Suivant**.
3. Sélectionnez votre plan de tarification. Il existe une option gratuite que vous pouvez utiliser pour ce tutoriel.
4. Cliquez sur **Créer**.

## Etape 3. Déployer dans {{site.data.keyword.cloud_notm}}
{: #deploy}

Cliquez sur **Déployer dans le cloud** sur la page Détails de l'application, sélectionnez une méthode de déploiement, par exemple, Cluster Kubernetes ou Application Cloud Foundry, puis cliquez sur **Créer**. {{site.data.keyword.cloud_notm}} crée automatiquement une chaîne d'outils ouverte complétée par un référentiel Git et un pipeline de distribution continue. Ouvrez le composant pipeline de votre nouvelle chaîne d'outils afin de commencer le processus de génération et de déploiement initial de sorte que vous puissiez voir votre application après quelques minutes.

Pour déployer votre application avec la ligne de commande, utilisez `ibmcloud dev deploy`. Pour plus d'informations, voir [Création et déploiement d'applications à l'aide de l'interface de ligne de commande](/docs/apps/create-deploy-cli.html).
