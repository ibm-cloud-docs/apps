---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-02"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Création d'une API BFF (backend-for-frontend)
{: #tutorial}

Vous pouvez créer une application à partir d'un kit de démarrage BFF (backend-for-frontend). Utilisez ces kits de démarrage pour générer des API BFF (backend-for-frontend) en Node.js, Java ou Swift à l'aide d'une grande variété d'infrastructures : Express.js, MicroProfile/Java EE, Kitura ou Spring. Vous verrez comment installer les outils dont vous avez besoin, comment générer et exécuter l'application localement et comment la déployer sur le cloud.
{: shortdesc}

## Etape 1 : Installer les outils
{: #before-you-begin}

Installez les [outils de développement ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.

## Etape 2 : Créer une application
{: #create-devex}

Créez une application dans {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}.

1. Sur la page [Kits de démarrage ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) dans {{site.data.keyword.dev_console}}, sélectionnez un kit de démarrage pour votre langage. Par exemple, pour une application Node.js, accédez à **Express.js Backend** et cliquez sur **Sélectionner un kit de démarrage**.

2. Entrez le nom de votre application. Pour ce tutoriel, utilisez `ExpressBackend`.

3. Entrez un nom d'hôte unique, par exemple, vos initiales plus `-devhost`. Par exemple :

	```
	abc-devhost
	```

	Ce nom d'hôte correspond à la route de votre application. Par exemple, `abc-devhost.mybluemix.net`

4. Sélectionnez votre plateforme de langage. Pour ce tutoriel, utilisez `Node.js`.

5. Cliquez sur **Créer**.

## Facultatif : Ajouter des resources
{: #add-services}

1. Dans la vue **Détails de l'application**, sélectionnez **Ajouter une ressource**.

2. Sélectionnez le type de service souhaité. Pour ce tutoriel, sélectionnez **Données** > **Suivant** > **Cloudant NoSQL DB** > **Suivant**.

3. Cliquez sur **Créer**.

## Facultatif : Créer une chaîne d'outils DevOps
{: #add-toolchain}

L'activation d'une chaîne d'outils permet de créer un environnement de développement basé sur une équipe pour votre application. Lorsque vous créez une chaîne d'outils, le service d'application met à disposition un référentiel git dans lequel vous pouvez afficher le code source, cloner votre application et créer et gérer les problèmes. Vous avez également accès à un environnement Gitlab dédié et à un pipeline de distribution continue qui est personnalisé pour la plateforme de déploiement que vous avez choisie, telle que kubernetes ou Cloud Foundry.

La distribution continue est activée pour certaines applications. Vous souhaiterez peut-être activer la distribution continue pour automatiser les générations, les tests et les déploiements via le pipeline de distribution et GitHub.

1. Sélectionnez votre application sur la page **Applications**.

2. Cliquez sur **Déployer dans Cloud**.

3. Sélectionnez une méthode de déploiement. Les deux options suivantes s'offrent à vous :

	* Effectuer un déploiement sur un cluster Kubernetes. Mettez à disposition un cluster d'hôtes, appelé noeuds d'employé, afin de déployer et de gérer des conteneurs d'application à haute disponibilité. Vous pouvez créer un cluster ou effectuer un déploiement sur un cluster existant.

	* Effectuer un déploiement à l'aide de Cloud Foundry, auquel cas, vous n'avez pas à vous préoccuper de gérer l'infrastructure sous-jacente.

## Etape 3 : Générer le code de votre application
{: #generate-code}

Si vous avez créé une chaîne d'outils à l'étape précédente, un référentiel Git a été créé pour votre application et vous y trouverez le code. Procédez comme suit pour accéder à votre référentiel :

1. Sélectionnez votre application sur la page **Applications**.

2. Cliquez sur **Afficher la chaîne d'outils**.

3. Cliquez sur la carte **Git** sous l'en-tête **CODE** afin d'ouvrir votre référentiel dans lequel vous pouvez visualiser le code source et cloner votre application. 

Si une chaîne d'outils n'est pas activée, vous pouvez accéder à votre code en téléchargeant la source directement à partir de la vue Détails de l'application. 

1. Sélectionnez votre application sur la page **Applications**.

2. Cliquez sur **Télécharger le code** pour télécharger l'archive de votre application. 

## Etape 4 : Commencer à utiliser votre application
{: #code}

Commencez à utiliser l'application que vous avez téléchargée :

1. Développez le fichier archivé.

2. Importez l'application dans votre interface IDE.

3. Modifiez le code.

4. Utilisez le {{site.data.keyword.dev_cli_notm}} pour générer et exécuter votre code localement.

## Etape 5 : Générer et exécuter l'application localement
{: #build-run}

Ajoutez votre propre code, puis générez et exécutez l'application. Vous pouvez exécuter l'application localement sur votre système hôte si vous installez les outils de génération nécessaires, ou en utilisant le support de conteneur disponible dans le {{site.data.keyword.dev_cli_notm}}.

### Utilisation du plug-in {{site.data.keyword.dev_cli_short}}

1. Pour générer l'application dans votre répertoire d'application en cours, entrez la commande suivante :

  ```
  bx dev build
  ```
  {: codeblock}

2. Pour exécuter l'application dans votre répertoire d'application en cours, entrez la commande suivante :

  ```
  bx dev run
  ```
  {: codeblock}

3. Vous pouvez exécuter la commande curl sur votre serveur, via :

   ```
   curl http://localhost:3000
   ```
   {: codeblock}

4. Vous pouvez afficher le document d'API sur votre serveur à l'adresse suivante :

   ```
   http://localhost:3000/swagger/api
   ```
   {: codeblock}

5. Vous pouvez explorer l'API sur votre serveur à l'adresse suivante :

   ```
   http://localhost:3000/explorer
   ```
   {: codeblock}

## Etape 6 : Effectuer un déploiement sur le cloud
{: #deploy}

### Effectuer un déploiement à l'aide d'une chaîne d'outils
Il existe plusieurs moyens de déployer une application sur {{site.data.keyword.cloud_notm}}, mais l'utilisation d'une chaîne d'outils DevOps reste le meilleur moyen de déployer des applications de production.  Une chaîne d'outils DevOps vous permet d'automatiser facilement des déploiements sur plusieurs environnements et d'ajouter rapidement des services de surveillance, de journalisation et d'alerte afin de vous aider à gérer votre application à mesure qu'elle grossit.

Avec une chaîne d'outils correctement configurée, un cycle de génération-déploiement démarre automatiquement avec chaque fusion vers la branche principale de votre référentiel. Toutes les chaînes d'outils créées à partir d'un tableau de bord de développeur {{site.data.keyword.cloud_notm}} sont configurées pour un déploiement automatique.

Vous pouvez également déployer manuellement votre application depuis votre chaîne d'outils DevOps :

1. Sélectionnez votre application sur la page **Applications**.

2. Cliquez sur **Afficher la chaîne d'outils**.

3. Affichez votre pipeline de distribution où vous pouvez démarrer des générations, gérer le déploiement et visualiser les journaux et l'historique.

### Effectuer un déploiement à l'aide du plug-in {{site.data.keyword.dev_cli_short}}
Si vous choisissez de ne pas utiliser une chaîne d'outils, vous pouvez également effectuer un déploiement à l'aide du plug-in {{site.data.keyword.dev_cli_short}}.

Pour déployer votre application sur Cloud Foundry, entrez la commande suivante :

  ```
  bx dev deploy
  ```
  {: codeblock}

Pour déployer votre application sur un cluster Kubernetes, entrez la commande suivante :

```
bx dev deploy --target <container>
```
{: codeblock}

### Vérifier que votre application est active
Une fois l'application déployée, vous verrez une URL semblable à `abc-devhost.mybluemix.net` dans le pipeline DevOps ou dans le terminal (si vous utilisez la ligne de commande). Visitez l'URL dans votre navigateur.
