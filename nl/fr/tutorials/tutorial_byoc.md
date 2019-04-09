---

copyright:
  years: 2018
lastupdated: "2018-11-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Création d'applications à partir de votre propre référentiel de codes
{: #code-repo}

Vous pouvez créer une application dans {{site.data.keyword.cloud}} en utilisant votre référentiel d'applications existant. Il vous suffit d'indiquer le lien Web dans votre référentiel lors de la création d'application, de continuer d'ajouter des ressources puis de connecter une chaîne d'outils DevOps à votre application pour le déploiement.
{: shortdesc}

## Avant de commencer
{: #prereqs}

Assurez-vous que les éléments prérequis suivants sont disponibles et prêts à être utilisés :

 * Installez l'interface de ligne de commande (CLI) [{{site.data.keyword.dev_cli_long}}](/docs/cli/index.html).
 * Voir [Qu'est-ce qui caractérise une bonne application ?](/docs/apps/best-practice.html) pour connaître les meilleures pratiques en matière de création d'applications.
 * Vous devez avoir un référentiel de codes source Git d'un des fournisseurs suivants : GitHub, GitHub Enterprise, Git lab, BitBucket ou Rational.

## Etape 1. Créer une application avec un référentiel existant
{: #create}

Pour créer une application et la connecter à votre référentiel source, procédez comme suit :

1. A partir de votre tableau de bord [![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}){: new_window}, cliquez sur **Créer une application** dans la section **Applications**.
2. Nommez votre application et sélectionnez un groupe de ressources.
3. Sélectionnez **Utiliser votre propre code** et indiquez l'URL de votre référentiel Git. Votre application et votre image Docker doivent se trouver dans le même référentiel.
4. Cliquez sur **Créer**.

La page **Détails de l'application** s'affiche. Vous pouvez alors :
* [Ajouter des ressources](/docs/apps/reqnsi.html) (facultatif).
* Connecter votre application à une chaîne d'outils DevOps en cliquant sur **Se connecter à une chaîne d'outils DevOps**. Si vous ne disposez pas encore d'une chaîne d'outils, la page **Se connecter à une chaîne d'outils DevOps** s'affiche. Cliquez sur **Créer une chaîne d'outils DevOps**. A ce stade, la page [Créer une chaîne d'outils](https://{DomainName}/devops/create) du [tableau de bord DevOps](https://{DomainName}/devops/) s'ouvre dans un nouvel onglet de votre navigateur. Une fois que vous avez créé et configuré votre chaîne d'outils dans cet onglet, vous devez retourner à la page **Connecter la chaîne d'outils** de votre application et actualiser la page. Pour plus d'informations, voir [Connexion de votre application à une nouvelle chaîne d'outils](#create_toolchain).
* Afficher votre référentiel en cliquant sur **Afficher le référentiel.**
* Découvrir plus d'informations sur les chaînes d'outils ou sur la création d'application en cliquant sur un des liens connexes de la page **Détails de l'application**.

## Etape 2. Connecter votre application à une chaîne d'outils DevOps
{: #connect_toolchain}

L'établissement d'un lien entre votre application, la chaîne d'outils et le référentiel constitue une étape importante lors de l'organisation de vos actifs de produit. Cette opération vous permet également d'agréger une vue de votre référentiel source avec le flux de travaux DevOps, vos instances d'application en cours d'exécution et les services dépendants dans l'ensemble de vos cibles de déploiement. Pour plus d'informations, voir [Connexion de votre application à une nouvelle chaîne d'outils](/docs/services/ContinuousDelivery/toolchains_working.html).

Vous pouvez connecter votre application à une chaîne d'outils DevOps en utilisant l'interface CLI ou la console {{site.data.keyword.cloud_notm}}. 

### Utilisation de la console

  1. Connectez votre application à une chaîne d'outils DevOps en cliquant sur **Se connecter à une chaîne d'outils DevOps**. 
  
    Si vous n'avez pas de chaîne d'outils, cliquez sur **Créer une chaîne d'outils DevOps**. 
    
  2. Une fois que vous avez créé et configuré votre chaîne d'outils, vous devez retourner à la page Connecter la chaîne d'outils de votre application et actualiser la page. 

### Utilisation de l'interface de ligne de commande (CLI)

Vous pouvez utiliser la commande `ibmcloud dev enable` pour générer un modèle de chaîne d'outils Devops que vous enregistrez dans votre référentiel comme cela est demandé par les instructions de création de chaîne d'outils DevOps. 

  1. Dans la fenêtre Services d'appli, cliquez sur **Télécharger le code** ou **Cloner votre référentiel** pour utiliser votre code localement.
  2. Exécutez la commande suivante :
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

Pour plus d'informations, voir [Création et déploiement d'applications à l'aide de l'interface de ligne de commande](/docs/apps/create-deploy-cli.html#developing).

## Etape 3. Déployer votre application
{: #deploy_app}

Une fois que vous avez associé une chaîne d'outils DevOps à votre application, procédez comme suit pour la déployer dans {{site.data.keyword.cloud_notm}} : 

1. Sur la page Détails de l'application, cliquez sur **Déployer dans le cloud**.
2. Sélectionnez une méthode de déploiement. 

    * [Déployer dans un cluster Kubernetes](/docs/apps/tutorials/tutorial_byoc_kube.html). Créez un cluster d'hôtes, appelé noeuds d'employé, afin de déployer et de gérer des conteneurs d'application à haute disponibilité. Vous pouvez créer un cluster ou effectuer un déploiement sur un cluster existant.
    * Effectuer un déploiement à l'aide de Cloud Foundry. Dans ce cas, vous n'avez pas à vous préoccuper de gérer l'infrastructure sous-jacente.
    * Déployer dans une [instance de serveur virtuel](/docs/apps/vsi-deploy.html).


