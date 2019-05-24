---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-30"

keywords: apps, code pattern, DevOps, toolchain, service credentials, create app code pattern, app pattern

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Création d'une application à l'aide d'un modèle de code
{: #tutorial-codepattern}

Vous pouvez utiliser un modèle de code pour créer rapidement votre application et la déployer dans {{site.data.keyword.cloud}}. Vous pouvez afficher le code dans GitHub ou créer et générer une application sur {{site.data.keyword.cloud_notm}}, où vous pouvez utiliser une chaîne d'outils DevOps pour déployer automatiquement votre application.
{: shortdesc}

## Etape 1. Créer une application
{: #create-codepattern}

1. Accédez à [IBM Developer ](https://developer.ibm.com/patterns/){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe") et sélectionnez le modèle de code souhaité. Vous pouvez, par exemple, sélectionner le modèle de code [Build a MEAN Web App ](https://developer.ibm.com/patterns/build-a-mean-web-app/){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe").

2. Lisez la description du modèle de code puis consultez le référentiel GitHub et le fichier `README.md`. Pour consulter le référentiel, cliquez sur **Obtenir le code**, qui ouvre le référentiel GitHub pour le modèle de code.

3. Commencez par créer une application en suivant une des procédures décrites ci-dessous. Une d'entre elles permet d'ouvrir la page **Créer une application** pour le modèle de code.
    * Sur la page du modèle de code, cliquez sur le lien pour la génération d'une application sur {{site.data.keyword.cloud_notm}}. 
    * Dans le fichier `README.md` du référentiel GitHub, cliquez sur le lien pour l'utilisation d'un kit de démarrage afin de créer l'application. 

4. Sur la page **Créer une application**, nommez votre application, sélectionnez un groupe de ressources et éventuellement créez des étiquettes puis cliquez sur **Créer**. Pour plus d'informations sur les étiquettes, voir [Utilisation d'étiquettes](/docs/resources?topic=resources-tag).

  Pour revenir au modèle de code, cliquez sur l'option d'affichage du modèle de code****. Consultez le fichier `README.md` dans le référentiel pour savoir si vous devez exécuter d'autres actions pour rendre votre application opérationnelle.
  {: tip}

## Etape 2. Ajouter des services
{: #resources-codepattern}

Vous pouvez ajouter des services qui améliorent votre application avec la puissance cognitive de Watson, ajoutent des services mobiles ou des services de sécurité. Ce processus crée une instance de service, crée une clé de ressource (données d'identification) et l'associe à votre application. Pour ce tutoriel, ajoutez un emplacement pour gérer vos données.

1. Sur la page **Détails de l'application**, cliquez sur **Ajouter un service**.
2. Sélectionnez le type de service voulu. 
3. Sélectionnez votre plan de tarification. Une option Lite est disponible.
4. Cliquez sur **Créer**.

## Etape 3. Copier des données d'identification de service dans votre environnement

Une fois que vous avez ajouté un service à votre application ou si des services sont requis pour votre application, notez que les données d'identification de ce service s'affichent dans la zone **Données d'identification**. Vous devez copier manuellement ces informations dans votre environnement de déploiement.

Pour plus d'informations sur la copie des données d'identification dans votre environnement, voir [Présentation des données d'identification](/docs/apps?topic=creating-apps-credentials_overview#credentials_overview).

## Etape 4. Déployer dans {{site.data.keyword.cloud_notm}}
{: #deploy-codepattern}

Lorsque vous sélectionnez une cible de déploiement, une chaîne d'outils DevOps est automatiquement créée pour votre application. La chaîne d'outils inclut un pipeline de distribution qui indique le statut de déploiement de votre application. La nouvelle application qui est générée est envoyée à un référentiel GitLab qui fait partie de la chaîne d'outils.

L'activation d'une chaîne d'outils DevOps crée un environnement de développement basé sur une équipe pour votre application. Lorsque vous créez une chaîne d'outils, le service d'application crée un référentiel Git dans lequel vous pouvez afficher le code source, cloner votre application, créer et gérer des problèmes. Vous avez également accès à un environnement GitLab dédié et à un pipeline de distribution continue. Ces éléments sont personnalisés en fonction de la cible de déploiement choisie, [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) ou [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Toutes les chaînes d'outils créées à partir d'un tableau de bord de développeur {{site.data.keyword.cloud_notm}} sont configurées pour un déploiement automatique.
{: note}

Pour sélectionner votre cible de déploiement et configurer la distribution continue, procédez comme suit :

1. Sur la page Détails de l'application, cliquez sur **Configurer la distribution continue**.
2. Sélectionnez une cible de déploiement. Configurez votre cible de déploiement en fonction des instructions s'appliquant à la cible que vous sélectionnez :
  * **Déployer dans [IBM Kubernetes Service](/docs/containers?topic=containers-app)**. Cette option crée un cluster d'hôtes, appelé noeuds worker, afin de déployer et de gérer des conteneurs d'application à haute disponibilité. Vous pouvez créer un cluster ou effectuer un déploiement sur un cluster existant.
  * **Déployer dans Cloud Foundry**. Cette option déploie votre application cloud native sans qu'il soit nécessaire de gérer l'infrastructure sous-jacente. Si votre compte a accès à {{site.data.keyword.cfee_full_notm}}, vous pouvez sélectionner un déployeur de type **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** ou **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**, que vous pouvez utiliser pour créer et gérer des environnements isolés pour l'hébergement de vos applications Cloud Foundry exclusivement pour votre entreprise.
  * **Déployer sur un serveur virtuel**. Cette option met à disposition une instance de serveur virtuel, charge une image qui inclut votre application, crée une chaîne d'outils DevOps et initie pour vous le premier cycle de déploiement.

Après avoir sélectionné et configuré la cible de déploiement, la page Détails de l'application indique que la distribution continue est configurée. Vous pouvez afficher le référentiel qui contient le code source de votre application en cliquant sur **Afficher le référentiel**.

Pour plus d'informations sur le déploiement de votre application, voir [Déploiement d'applications](/docs/apps?topic=creating-apps-deploying-apps).

Pour plus d'informations sur les cibles de déploiement, les générations et les pipelines, voir [Génération et déploiement](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).
