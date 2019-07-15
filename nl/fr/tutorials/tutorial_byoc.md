---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-20"

keywords: byoc, code repository, continuous delivery, cli, deploy, create app custom repo, custom repo, existing repo, custom code

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

Si vous avez une application dans un référentiel existant, vous pouvez utiliser un kit de démarrage de base pour créer un enregistrement d'application dans {{site.data.keyword.cloud_notm}} et connecter l'application à votre référentiel source et à votre chaîne d'outils DevOps.
{: shortdesc}

Vous pouvez commencer à partir du tableau de bord {{site.data.keyword.cloud_notm}} ou d'un kit de démarrage de base. Une fois que vous avez nommé votre application et que vous avez sélectionné un groupe de ressources, sélectionnez le point de démarrage **Utilisation de votre propre code**, indiquez l'URL du référentiel Git qui contient votre code puis cliquez sur **Créer**.

Vous pouvez connecter votre chaîne d'outils DevOps existante ou en créer une et fournir en continu votre application à la cible de déploiement de votre choix (Kubernetes ou Cloud Foundry, par exemple).

## Avant de commencer
{: #prereqs-byoc}

Assurez-vous que les éléments prérequis suivants sont disponibles et prêts à être utilisés :

 * Installez l'[interface de ligne de commande {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-getting-started).
 * Voir [Qu'est-ce qui caractérise une bonne application ?](/docs/apps?topic=creating-apps-best-practice) pour connaître les meilleures pratiques en matière de création d'applications.
 * Vous devez avoir un référentiel de codes source Git d'un des fournisseurs suivants : GitHub, GitHub Enterprise, Git lab, BitBucket ou Rational.
 * Si vous envisagez de déployer votre application dans [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), vous devez [préparer votre compte {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Création d'une application avec un référentiel existant
{: #create-byoc}

Pour créer une application et la connecter à votre référentiel source, procédez comme suit :

1. Dans la console [{{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe"), cliquez sur **Créer une application** dans la vignette **Applications**.
2. Nommez votre application, sélectionnez un groupe de ressources et éventuellement créez des étiquettes pour classer votre application. Pour plus d'informations, voir [Utilisation d'étiquettes](/docs/resources?topic=resources-tag).
3. Sélectionnez **Utiliser votre propre code** et indiquez l'URL de votre référentiel Git. Votre application et votre image Docker doivent se trouver dans le même référentiel.
4. Cliquez sur **Créer**. La page **Détails de l'application** s'affiche.
5. Facultatif. [Ajoutez des services](/docs/apps?topic=creating-apps-add-resource) à votre application.
6. Facultatif. Vous pouvez ajouter des étiquettes à cette application en cliquant sur **Ajouter des étiquettes**. Vous pouvez également modifier des étiquettes en cliquant sur l'icône **Editer** ![Icône Editer](../../icons/edit-tagging.svg) en regard des étiquettes affichées.
7. Facultatif. Afficher votre référentiel en cliquant sur **Afficher le référentiel.**

## Déploiement de votre application
{: #toolchain-byoc}

L'établissement d'un lien entre votre application, la chaîne d'outils et le référentiel constitue une étape importante lors de l'organisation de vos actifs de produit. Cette opération vous permet également d'agréger une vue de votre référentiel source avec le flux de travaux DevOps, vos instances d'application en cours d'exécution et les services dépendants dans l'ensemble de vos cibles de déploiement. Pour plus d'informations, voir [Création de chaînes d'outils](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

Vous pouvez configurer la distribution continue pour votre application en utilisant la console {{site.data.keyword.cloud_notm}} ou l'interface de ligne de commande.

### Utilisation de la console
{: #console-byoc-toolchain}

#### Si vous disposez déjà d'une chaîne d'outils DevOps que vous souhaitez connecter à votre application, procédez comme suit :

1. Sur la page **Détails de l'application**, cliquez sur **Configurer la distribution continue**. La page **Déployer mon application** s'affiche.
2. Sélectionnez la chaîne d'outils que vous souhaitez connecter à votre application puis cliquez sur **Activer le déploiement**. La page **Détails de l'application** s'affiche, indiquant que la distribution continue est configurée.

#### Si vous ne disposez pas de chaîne d'outils DevOps pour cette application, procédez comme suit :

1. Sur la page **Détails de l'application**, cliquez sur **Créer une chaîne d'outils DevOps**. La page **Créer une chaîne d'outils** s'affiche.
2. [Créez la chaîne d'outils](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).
3. Utilisez les éléments de navigation de la fenêtre de navigateur pour accéder à nouveau à la page **Détails de l'application**, qui indique que la distribution continue est configurée.

### Utilisation de l'interface de ligne de commande (CLI)
{: #cli-byoc-toolchain}

Vous pouvez utiliser la commande `ibmcloud dev enable` pour générer un modèle de chaîne d'outils DevOps que vous enregistrez dans votre référentiel, en tant que jeu d'instructions pour les éléments créés par la chaîne d'outils DevOps. 

  1. Sur la page **Détails de l'application**, cliquez sur **Afficher le référentiel** pour utiliser votre code localement.
  2. Exécutez la commande suivante :
    
    ```
    ibmcloud dev enable
    ```
   {: codeblock}

Pour plus d'informations sur le déploiement de votre application, voir [Déploiement d'applications](/docs/apps?topic=creating-apps-deploying-apps).

## Vérification que votre application est en cours d'exécution
{: #verify-byoc-app}

Delivery Pipeline ou la ligne de commande indique l'URL de votre application.

1. Dans votre chaîne d'outils DevOps, cliquez sur **Delivery Pipeline** puis sélectionnez **Etape de déploiement**.
2. Cliquez sur **Afficher les journaux et l'historique**.
3. Dans le fichier journal, recherchez l'URL de l'application. A la fin du fichier journal, recherchez le mot `urls` ou `view`. Par exemple, une ligne similaire à `urls: my-app-devhost.mybluemix.net` ou à `View the application health at: http://<ipaddress>:<port>/health` peut être incluse dans le fichier journal.
4. Accédez à l'URL dans votre navigateur. Si l'application est en cours d'exécution, un message qui inclut `Congratulations` ou `{"status":"UP"}` s'affiche.

Si vous utilisez la ligne de commande, exécutez la commande [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) pour ouvrir la page d'une application manuellement déployée dans votre navigateur par défaut.
