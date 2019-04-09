---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Création d'applications à partir de votre propre référentiel de codes
{: #tutorial-byoc}

Vous pouvez créer une application dans {{site.data.keyword.cloud}} en utilisant votre référentiel d'applications existant. Il vous suffit d'indiquer le lien Web dans votre référentiel lors de la création d'application, de continuer d'ajouter des ressources puis de connecter une chaîne d'outils DevOps à votre application pour le déploiement.
{: shortdesc}

## Avant de commencer
{: #prereqs-byoc}

Assurez-vous que les éléments prérequis suivants sont disponibles et prêts à être utilisés :

 * Installez l'interface de ligne de commande (CLI) [{{site.data.keyword.dev_cli_long}}](/docs/cli/index.html#overview).
 * Voir [Qu'est-ce qui caractérise une bonne application ?](/docs/apps/best-practice.html#best-practice) pour connaître les meilleures pratiques en matière de création d'applications.
 * Vous devez avoir un référentiel de codes source Git d'un des fournisseurs suivants : GitHub, GitHub Enterprise, Git lab, BitBucket ou Rational.
 * Si vous envisagez de déployer votre application dans [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about), vous devez [préparer votre compte {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry/prepare-account.html#prepare).

## Etape 1. Créer une application avec un référentiel existant
{: #create-byoc}

Pour créer une application et la connecter à votre référentiel source, procédez comme suit :

1. A partir de votre tableau de bord [![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}){: new_window}, cliquez sur **Créer une application** dans la section **Applications**.
2. Nommez votre application, sélectionnez un groupe de ressources et éventuellement créez des étiquettes pour classer votre application. Pour plus d'informations, voir [Utilisation d'étiquettes](/docs/resources/tagging_resources.html#tag).
3. Sélectionnez **Utiliser votre propre code** et indiquez l'URL de votre référentiel Git. Votre application et votre image Docker doivent se trouver dans le même référentiel.
4. Cliquez sur **Créer**.

La page **Détails de l'application** s'affiche. Vous pouvez alors :
* [Ajouter des ressources](/docs/apps/reqnsi.html#add-resource) (facultatif).
* Si vous avez créé des étiquettes lors de la création de l'application, vous pouvez les modifier en cliquant sur l'icône **Editer**![Icône Editer](../../icons/edit-tagging.svg) se trouvant en regard des étiquettes affichées.
* Connecter votre application à une chaîne d'outils DevOps en cliquant sur **Se connecter à une chaîne d'outils DevOps**. Si vous ne disposez pas encore d'une chaîne d'outils, la page **Se connecter à une chaîne d'outils DevOps** s'affiche. Cliquez sur **Créer une chaîne d'outils DevOps**. A ce stade, la page [Créer une chaîne d'outils](https://{DomainName}/devops/create) du [tableau de bord DevOps](https://{DomainName}/devops/) s'ouvre dans un nouvel onglet de votre navigateur. Une fois que vous avez créé et configuré votre chaîne d'outils dans cet onglet, vous devez revenir à la page **Connecter la chaîne d'outils** dans votre application et actualiser la page.
* Afficher votre référentiel en cliquant sur **Afficher le référentiel.**
* Découvrir plus d'informations sur les chaînes d'outils ou sur la création d'application en cliquant sur un des liens connexes de la page **Détails de l'application**.

## Etape 2. Connecter votre application à une chaîne d'outils DevOps
{: #toolchain-byoc}

L'établissement d'un lien entre votre application, la chaîne d'outils et le référentiel constitue une étape importante lors de l'organisation de vos actifs de produit. Cette opération vous permet également d'agréger une vue de votre référentiel source avec le flux de travaux DevOps, vos instances d'application en cours d'exécution et les services dépendants dans l'ensemble de vos cibles de déploiement. Pour plus d'informations, voir [Création de chaînes d'outils](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

Vous pouvez connecter votre application à une chaîne d'outils DevOps en utilisant l'interface CLI ou la console {{site.data.keyword.cloud_notm}}.

### Utilisation de la console
{: #console-byoc-toolchain}

  1. Connectez votre application à une chaîne d'outils DevOps en cliquant sur **Se connecter à une chaîne d'outils DevOps**. 
  
    Si vous n'avez pas de chaîne d'outils, cliquez sur **Créer une chaîne d'outils DevOps**. 
    
  2. Une fois que vous avez créé et configuré votre chaîne d'outils, vous devez retourner à la page Connecter la chaîne d'outils de votre application et actualiser la page. 

### Utilisation de l'interface de ligne de commande (CLI)

Vous pouvez utiliser la commande `ibmcloud dev enable` pour générer un modèle de chaîne d'outils DevOps que vous enregistrez dans votre référentiel comme cela est demandé par les instructions de création de chaîne d'outils DevOps. 

  1. Dans la fenêtre Services d'appli, cliquez sur **Télécharger le code** ou **Cloner votre référentiel** pour utiliser votre code localement.
  2. Exécutez la commande suivante :
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

Pour plus d'informations, voir [Création et déploiement d'applications à l'aide de l'interface de ligne de commande](/docs/apps/create-deploy-cli.html#create-deploy-app-cli).

## Etape 3. Déployer votre application
{: #deploy-byoc}

Une fois que vous avez associé une chaîne d'outils DevOps à votre application, procédez comme suit pour la déployer dans {{site.data.keyword.cloud_notm}} : 

1. Sur la page Détails de l'application, cliquez sur **Déployer dans le cloud**.
2. Sélectionnez une méthode de déploiement. Configurez votre méthode de déploiement en fonction des instructions s'appliquant à la méthode choisie.
  * **Déployer dans [Kubernetes](/docs/apps/deploying/containers.html#containers)**. Cette option crée un cluster d'hôtes, appelé noeuds worker, afin de déployer et de gérer des conteneurs d'application à haute disponibilité. Vous pouvez créer un cluster ou effectuer un déploiement sur un cluster existant.
  * **Déployer dans Cloud Foundry**. Cette option déploie votre application cloud native sans qu'il soit nécessaire de gérer l'infrastructure sous-jacente. Si votre compte a accès à {{site.data.keyword.cfee_full_notm}}, vous pouvez sélectionnez un déployeur de type **[Public Cloud](/docs/cloud-foundry-public/about-cf.html#about-cf)** ou **[Enterprise Environment](/docs/cloud-foundry-public/cfee.html#cfee)**, que vous pouvez utiliser pour créer et gérer des environnements isolés pour l'hébergement de vos applications Cloud Foundry exclusivement pour votre entreprise.
  * **Déployer sur un [serveur virtuel](/docs/apps/vsi-deploy.html#vsi-deploy)**. Cette option met à disposition une instance de serveur virtuel, charge une image qui inclut votre application, crée une chaîne d'outils DevOps et initie pour vous le premier cycle de déploiement.


