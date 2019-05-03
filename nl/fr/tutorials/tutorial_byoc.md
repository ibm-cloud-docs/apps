---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, byoc, code repository, continuous delivery, cli, deploy

subcollection: creating-apps

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

 * Installez l'interface de ligne de commande [{{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).
 * Voir [Qu'est-ce qui caractérise une bonne application ?](/docs/apps?topic=creating-apps-best-practice) pour connaître les meilleures pratiques en matière de création d'applications.
 * Vous devez avoir un référentiel de codes source Git d'un des fournisseurs suivants : GitHub, GitHub Enterprise, Git lab, BitBucket ou Rational.
 * Si vous envisagez de déployer votre application dans [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), vous devez [préparer votre compte {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Etape 1. Créer une application avec un référentiel existant
{: #create-byoc}

Pour créer une application et la connecter à votre référentiel source, procédez comme suit :

1. Depuis votre [tableau de bord](https://{DomainName}){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe"), cliquez sur **Créer une application** dans la vignette **Applications**.
2. Nommez votre application, sélectionnez un groupe de ressources et éventuellement créez des étiquettes pour classer votre application. Pour plus d'informations, voir [Utilisation d'étiquettes](/docs/resources?topic=resources-tag).
3. Sélectionnez **Utiliser votre propre code** et indiquez l'URL de votre référentiel Git. Votre application et votre image Docker doivent se trouver dans le même référentiel.
4. Cliquez sur **Créer**. La page **Détails de l'application** s'affiche. 
5. Facultatif. [Ajoutez des services](/docs/apps?topic=creating-apps-add-resource) à votre application.
6. Facultatif. Si vous avez créé des étiquettes lors de la création de l'application, vous pouvez les modifier en cliquant sur l'icône **Editer**![Icône Editer](../../icons/edit-tagging.svg) se trouvant en regard des étiquettes affichées.
7. Facultatif. Afficher votre référentiel en cliquant sur **Afficher le référentiel.**

## Etape 2. Déployer votre application
{: #toolchain-byoc}

L'établissement d'un lien entre votre application, la chaîne d'outils et le référentiel constitue une étape importante lors de l'organisation de vos actifs de produit. Cette opération vous permet également d'agréger une vue de votre référentiel source avec le flux de travaux DevOps, vos instances d'application en cours d'exécution et les services dépendants dans l'ensemble de vos cibles de déploiement. Pour plus d'informations, voir [Création de chaînes d'outils](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

Vous pouvez configurer la distribution continue pour votre application en utilisant la console {{site.data.keyword.cloud_notm}} ou l'interface de ligne de commande.

### Utilisation de la console
{: #console-byoc-toolchain}

  1. Sur la page **Détails de l'application**, connectez votre application à une chaîne d'outils DevOps en cliquant sur **Configurer la distribution continue**. La page **Déployer mon application** s'affiche.
  2. Si vous n'avez pas de chaîne d'outils existante, cliquez sur **Créer une chaîne d'outils**. Une fois la chaîne d'outils créée, utilisez les éléments de navigation pour revenir à la page **Détails de l'application**, qui indique que la distribution continue est configurée.
  3. Si vous disposez d'une chaîne d'outils existante, sélectionnez-la puis cliquez sur **Activer le déploiement**. La page **Détails de l'application** s'affiche, indiquant que la distribution continue est configurée.

### Utilisation de l'interface de ligne de commande (CLI)

Vous pouvez utiliser la commande `ibmcloud dev enable` pour générer un modèle de chaîne d'outils DevOps que vous enregistrez dans votre référentiel, en tant que jeu d'instructions pour les éléments créés par la chaîne d'outils DevOps. 

  1. Sur la page **Détails de l'application**, cliquez sur **Afficher le référentiel** pour utiliser votre code localement.
  2. Exécutez la commande suivante :
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

Pour plus d'informations, voir [Création et déploiement d'applications à l'aide de l'interface de ligne de commande](/docs/apps?topic=creating-apps-create-deploy-app-cli).

