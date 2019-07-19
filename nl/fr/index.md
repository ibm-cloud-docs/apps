---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, create apps, add resources, deploy apps

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Tutoriel d'initiation
{: #tutorial-getting-started}

Vous pouvez générer des applications mobiles et Web adaptées aux entreprises dans {{site.data.keyword.cloud}} et tirer parti des extensions cloud hébergées par {{site.data.keyword.cloud_notm}}. Vous pouvez commencer de différentes manières. Vous pouvez créer une application avec un kit de démarrage qui gère le processus pour vous, ou, si vous savez précisément ce que vous voulez, générer vous-même votre application avec les ressources dont vous avez besoin ou utiliser votre référentiel existant ainsi que votre propre code.
{: shortdesc}

## Avant de commencer
{: #prereqs-getting-started}

Vous pouvez créer votre application en utilisant la console {{site.data.keyword.cloud_notm}} ou l'interface de ligne de commande. Si vous voulez utiliser cette dernière, voir les [étapes d'installation](/docs/cli?topic=cloud-cli-ibmcloud-cli).

## Etape 1. Créer votre application
{: #create-getting-started}

Créez une application en sélectionnant un des points d'entrée suivants :
* [Kit de démarrage](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit) - Créez une application à partir d'une sélection de kits de démarrage de service d'application qui gèrent le processus pour vous.
* [Personnalisé](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch) - Si vous savez ce que vous voulez, générez une application personnalisée avec les ressources dont vous avez besoin en utilisant un kit de démarrage vide.
* [Utilisation de votre propre code](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc) - Utilisez votre propre code en le liant à votre propre référentiel de contenu. Votre application et votre image Docker doivent se trouver dans le même référentiel.
* [Interface CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli) - Créez et déployez une application personnalisée ou de kit de démarrage en utilisant l'interface CLI et les outils Developer.
* [Modèles de code](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern) - Utilisez un modèle de code IBM Developer comme base pour la création de votre application.
* [Catalogue {{site.data.keyword.cloud_notm}} ](https://cloud.ibm.com/catalog){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") : vous pouvez parcourir le catalogue ou rechercher dans ce dernier des applications et des services que vous pouvez créer et commencer à utiliser dès à présent.

## Etape 2. Ajouter des ressources
{: #resources-getting-started}

Quand vous utilisez un kit de démarrage pour créer votre application, vos services sont automatiquement créés pour vous. Vous pouvez associer des services supplémentaires à votre application en cliquant sur **Ajouter un service** sur la page **Détails de l'application** de la console.

Pour ajouter des services à votre application en utilisant l'interface de ligne de commande, exécutez la commande suivante. Vous pouvez sélectionner un service existant parmi ceux qui sont déjà activés sur votre compte ou ajouter un nouveau service. 
```
ibmcloud dev edit
```
{: codeblock}

Pour plus d'informations, voir [Ajout d'un service à votre application](/docs/apps?topic=creating-apps-add-resource).

## Etape 3. Déployer votre application
{: #deploy-getting-started}

Vous pouvez déployer votre application en utilisant la console ou la ligne de commande.

### Utilisation de la console
{: #console-getting-started}

Pour déployer votre application en utilisant la console, procédez comme suit :

1. Sur la page **Détails de l'application**, cliquez sur **Configurer la distribution continue**.
2. Sélectionnez une cible de déploiement, sélectionnez les paramètres de chaîne d'outils et cliquez sur **Créer**. {{site.data.keyword.cloud_notm}} crée automatiquement une chaîne d'outils ouverte complétée par un référentiel Git et un pipeline de distribution continue.
3. Ouvrez l'étape de pipeline de votre nouvelle chaîne d'outils pour afficher le processus de génération et de déploiement de sorte que vous puissiez voir votre nouvelle application après quelques minutes.

Pour plus d'informations, consultez la table des matières présentant les différentes rubriques de déploiement dans la section "Déploiement et intégration d'applications".

### Utilisation de la ligne de commande
{: #cli-getting-started}

Pour déployer votre application en utilisant la ligne de commande, exécutez la commande `ibmcloud dev deploy`. Pour plus d'informations, voir [Création et déploiement d'applications à l'aide de l'interface de ligne de commande](/docs/apps?topic=creating-apps-create-deploy-app-cli).

Vous êtes maintenant prêt pour des tâches de développement itératif et de distribution continue.
