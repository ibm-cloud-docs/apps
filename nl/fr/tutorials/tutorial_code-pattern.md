---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

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

1. Accédez à [IBM Developer ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/patterns/){:new_window} et sélectionnez le modèle de code souhaité. Vous pouvez, par exemple, sélectionner le modèle de code [Build a MEAN Web App ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/patterns/build-a-mean-web-app/){:new_window}.

2. Lisez la description du modèle de code puis consultez le référentiel GitHub et le fichier `README.md`. Pour consulter le référentiel, cliquez sur **Obtenir le code**, qui ouvre le référentiel GitHub pour le modèle de code.

3. Commencez par créer une application en suivant une des procédures décrites ci-dessous. Une d'entre elles permet d'ouvrir la page **Créer une application** pour le modèle de code.
    * Sur la page du modèle de code, cliquez sur le lien pour la génération d'une application sur {{site.data.keyword.cloud_notm}}. 
    * Dans le fichier `README.md` du référentiel GitHub, cliquez sur le lien pour l'utilisation d'un kit de démarrage afin de créer l'application. 

4. Sur la page **Créer une application**, nommez votre application, sélectionnez un groupe de ressources et éventuellement créez des étiquettes puis cliquez sur **Créer**. Pour plus d'informations sur les étiquettes, voir [Utilisation d'étiquettes](/docs/resources/tagging_resources.html#tag).

  Pour revenir au modèle de code, cliquez sur l'option d'affichage du modèle de code****. Consultez le fichier `README.md` dans le référentiel pour savoir si vous devez exécuter d'autres actions pour rendre votre application opérationnelle.
  {: tip}

## Etape 2. Ajouter des ressources
{: #resources-codepattern}

Vous pouvez ajouter des ressources qui améliorent votre application avec la puissance cognitive de Watson, ajoutent des services mobiles ou des services de sécurité. Ce processus crée une instance de ressource, crée une clé de ressource (données d'identification) et l'associe à votre application. Pour ce tutoriel, ajoutez un emplacement pour gérer vos données.

1. Sur la page **Détails de l'application**, cliquez sur **Ajouter une ressource**.
2. Sélectionnez le type de ressource souhaité. 
3. Sélectionnez votre plan de tarification. Une option Lite est disponible.
4. Cliquez sur **Créer**.

## Etape 3. Copier des données d'identification de service dans votre environnement

Une fois que vous avez ajouté une ressource à votre application ou si des services sont requis pour votre application, notez que les données d'identification de ce service s'affichent dans la zone **Données d'identification**. Vous devez copier manuellement ces informations dans votre environnement de déploiement.

Pour plus d'informations sur la copie des données d'identification dans votre environnement, voir [Présentation des données d'identification](/docs/apps/creds_overview.html).

## Etape 4. Déployer dans {{site.data.keyword.cloud_notm}}
{: #deploy-codepattern}

Vous pouvez déployer votre application dans {{site.data.keyword.cloud_notm}} de différentes manières. Mais l'utilisation d'une chaîne d'outils DevOps reste le meilleur moyen de déployer des applications de production. A l'aide d'une chaîne d'outils DevOps, vous pouvez facilement automatiser un grand nombre de déploiements et ajouter rapidement des services de surveillance, de journalisation et d'alerte afin de gérer plus facilement votre application à mesure de sa croissance.

L'activation d'une chaîne d'outils permet de créer un environnement de développement basé sur une équipe pour votre application. Lorsque vous créez une chaîne d'outils, le service d'application crée un référentiel Git dans lequel vous pouvez afficher le code source, cloner votre application, créer et gérer des problèmes. Vous avez également accès à un environnement de lab dédié Git et à un pipeline de distribution continue. Ces éléments sont personnalisés en fonction de l'environnement de déploiement choisi, [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) ou [Virtual Server (VSI)](/docs/vsi/vsi_index.html).

1. Sur la page **Détails de l'application**, cliquez sur **Déployer dans le cloud**.
2. Sélectionnez une méthode de déploiement puis cliquez sur **Créer**. {{site.data.keyword.cloud_notm}} crée automatiquement une chaîne d'outils ouverte complétée par un référentiel Git et un pipeline de distribution continue.
3. Ouvrez l'étape de pipeline de votre nouvelle chaîne d'outils pour afficher le processus de génération et de déploiement de sorte que vous puissiez voir votre nouvelle application après quelques minutes.

Pour plus d'informations sur les méthodes de déploiement, les générations et les pipelines, voir [Génération et déploiement](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy).
