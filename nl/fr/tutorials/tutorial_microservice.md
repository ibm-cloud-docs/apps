---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-07-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Création d'un microservice
{: #tutorial}

Vous pouvez créer une application à partir d'un kit de démarrage de base de microservice. Utilisez ces modules de démarrage pour générer un système de back end de microservice pour Node, Java ou Python avec un choix de structures Web. Vous verrez comment installer les outils dont vous avez besoin, comment générer et exécuter l'application localement et comment la déployer sur le cloud.
{: shortdesc}

## Etape 1 : Installer les outils
{: #install-tools}

Installez les [outils de développement ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.

Docker est installé en tant qu'outil de développement. Pour que les commandes de génération fonctionnent, Docker doit être en cours d'exécution. Vous devez créer un compte Docker, exécuter l'application Docker et vous connecter.

## Etape 2 : Créer une application
{: #create-devex}

Créez une application dans {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}} :

1. Sur la page [Kits de démarrage ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) dans {{site.data.keyword.dev_console}}, sélectionnez un kit de démarrage pour votre langage. Par exemple, pour une application Node.js, accédez à **Express.js Microservice** et cliquez sur **Sélectionner un kit de démarrage**.
2. Entrez le nom de votre application. Pour ce tutoriel, utilisez `MicroserviceProject`.
3. Entrez un nom d'hôte unique, par exemple, `abc-devhost`. Ce nom d'hôte correspond à la route de votre application, `abc-devhost.mybluemix.net`
4. Sélectionnez votre langage et votre infrastructure. Certains kits de démarrage peuvent être disponibles dans un seul langage.
5. Sélectionnez votre plan de tarification. Il existe une option gratuite que vous pouvez utiliser pour ce tutoriel.
6. Cliquez sur **Créer**.

## Etape 3 : Ajouter des ressources (facultatif)
{: #add-services}

Vous pouvez ajouter des ressources qui améliorent votre application avec la puissance cognitive de Watson, ajoutent des services mobiles ou des services de sécurité. Pour ce tutoriel, ajoutez un emplacement pour gérer vos données.

1. Dans la fenêtre de service d'application, cliquez sur **Ajouter une ressource**.
2. Sélectionnez le type de service souhaité. Par exemple, sélectionnez **Données** > **Suivant** > **Cloudant** > **Suivant**.
3. Sélectionnez votre plan de tarification. Il existe une option gratuite que vous pouvez utiliser pour ce tutoriel.
4. Cliquez sur **Créer**.

## Etape 4 : Créer une chaîne d'outils DevOps
{: #add-toolchain}

L'activation d'une chaîne d'outils permet de créer un environnement de développement basé sur une équipe pour votre application. Lorsque vous créez une chaîne d'outils, le service d'application crée un référentiel Git dans lequel vous pouvez afficher le code source, cloner votre application, créer et gérer des problèmes. Vous avez également accès à un environnement de lab dédié Git et à un pipeline de distribution continue. Ces éléments sont configurés pour la plateforme de déploiement choisie, Kubernetes ou Cloud Foundry.

La distribution continue est activée pour certaines applications. Vous pouvez activer la distribution continue pour automatiser les générations, les tests et les déploiements via Delivery Pipeline et GitHub.

1. Dans la fenêtre de service d'application, cliquez sur **Déployer dans le cloud**.
2. Sélectionnez une méthode de déploiement. Configurez votre méthode de déploiement en fonction des instructions s'appliquant à la méthode choisie.

    * Effectuer un déploiement sur un cluster Kubernetes. Créez un cluster d'hôtes, appelé noeuds d'employé, afin de déployer et de gérer des conteneurs d'application à haute disponibilité. Vous pouvez créer un cluster ou effectuer un déploiement sur un cluster existant.

    * Effectuer un déploiement à l'aide de Cloud Foundry. Dans ce cas, vous n'avez pas à vous préoccuper de gérer l'infrastructure sous-jacente.

## Etape 5 : Générer et exécuter l'application localement
{: #build-run}

Le déploiement de votre application dans le cloud effectué lors de la dernière étape a créé une chaîne d'outils. Cette dernière crée un référentiel Git pour votre application dans lequel vous pouvez trouver le code. Procédez comme suit pour accéder à votre référentiel. Vous pouvez générer l'application localement à des fins de test avant de la placer dans le cloud.

1. Dans la fenêtre de service d'application, cliquez sur **Télécharger le code** ou **Cloner votre référentiel** pour utiliser votre code localement.
2. Importez l'application dans votre environnement de développement intégré.
3. Modifiez le code.
4. Configurez l'[authentification Git](/docs/services/ContinuousDelivery/git_working.html#git_authentication) en ajoutant un jeton d'accès personnel.
5. Connectez-vous à l'interface de ligne de commande {{site.data.keyword.Bluemix}}. Si votre entreprise utilise des connexions fédérées, utilisez l'option `-sso`.

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Configurez vos cibles d'organisation et d'espace.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7.  Obtenez les données d'identification.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Assurez-vous que Docker est en cours d'exécution et générez votre application dans un conteneur de développement local à partir du répertoire.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Exécutez votre application dans un conteneur de développement local.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10.  Ouvrez votre navigateur dans `http://localhost:3000`. Votre numéro de port peut être différent en fonction de l'environnement d'exécution choisi.

## Etape 6 : Effectuer un déploiement sur le cloud
{: #deploy}

### Déploiement à l'aide d'une chaîne d'outils

Vous pouvez déployer votre application dans {{site.data.keyword.cloud_notm}} de différentes manières. Mais l'utilisation d'une chaîne d'outils DevOps reste le meilleur moyen de déployer des applications de production. A l'aide d'une chaîne d'outils DevOps, vous pouvez facilement automatiser un grand nombre de déploiements et ajouter rapidement des services de surveillance, de journalisation et d'alerte afin de gérer plus facilement votre application à mesure de sa croissance.

Avec une chaîne d'outils correctement configurée, un cycle de génération-déploiement démarre automatiquement avec chaque fusion vers la branche principale de votre référentiel. Toutes les chaînes d'outils créées à partir d'un tableau de bord de développeur {{site.data.keyword.cloud_notm}} sont configurées pour un déploiement automatique.

Vous pouvez également déployer manuellement votre application depuis votre chaîne d'outils DevOps :

1. Dans la fenêtre Détails de l'application, cliquez sur **Afficher la chaîne d'outils**.

2. Cliquez sur **Delivery pipeline**. Vous pouvez alors démarrer des générations, gérer le déploiement et afficher les journaux et l'historique.

### Déploiement en utilisant {{site.data.keyword.dev_cli_short}}

Pour déployer votre application sur Cloud Foundry, entrez la commande suivante :

```
ibmcloud dev deploy
```
{: pre}

Pour déployer votre application sur un cluster Kubernetes, entrez la commande suivante :

```
ibmcloud dev deploy --target <container>
```
{: pre}

## Etape 7 : Vérifier que votre application est en cours d'exécution
{: #verify}

Une fois votre application déployée, l'invite de commande ou le pipeline DevOps indique l'URL de votre application, par exemple `abc-devhost.mybluemix.net`. Accédez à cette URL à partir de votre navigateur.
