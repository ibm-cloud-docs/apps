---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-03-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Création d'une application Web de base à l'aide d'un kit de démarrage
{: #tutorial}

Vous pouvez créer un projet à partir d'un kit de démarrage de base. Utilisez ces modules de démarrage dans le but de configurer un serveur Web simple pour Swift, Node, Java ou Python avec un choix de structures Web. Vous verrez comment installer les outils dont vous avez besoin, vous générerez et exécuterez le projet localement et vous le déploierez sur le cloud.
{: shortdesc}

## Etape 1 : Installer les outils
{: #before-you-begin}

Installez les [outils de développement ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.


## Etape 2 : Créer un projet
{: #create-devex}

Créez un projet dans la console {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}} :

1. Sur la page [Kits de démarrage ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) de la console {{site.data.keyword.dev_console}}, sélectionnez un kit de démarrage pour votre langage. Par exemple, pour une application Node.js, sélectionnez **Express.js Basic** et cliquez sur **Créer un projet**.

2. Entrez un nom de projet. Pour ce tutoriel, utilisez `WebBasicProject`.   

3. Entrez un nom d'hôte unique, par exemple, vos initiales plus `-devhost`. Par exemple :

	```
	abc-devhost
	```

	Ce nom d'hôte correspond à la route de votre projet. Par exemple, `abc-devhost.mybluemix.net`

4. Sélectionnez votre plateforme de langage. Pour ce tutoriel, utilisez `Node.js`.

5. Cliquez sur **Créer un projet**.

## Facultatif : Ajouter des resources
{: #add-services}

1. Dans la vue **Détails du projet**, sélectionnez **Ajouter une ressource**.

2. Sélectionnez le type de service souhaité. Pour ce tutoriel, sélectionnez **Données** > **Suivant** > **Cloudant NoSQL DB** > **Suivant**.

4. Cliquez sur **Créer**.

## Facultatif : Créer une chaîne d'outils DevOps
{: #add-toolchain}

l'activation d'une chaîne d'outils permet de créer un environnement de développement basé sur une équipe pour votre projet. Lorsque vous créez une chaîne d'outils, le service d'application met à disposition un référentiel git dans lequel vous pouvez afficher le code source, cloner votre projet et créer et gérer les problèmes. Vous avez également accès à un environnement Gitlab dédié et à un pipeline de distribution continue qui est personnalisé pour la plateforme de déploiement que vous avez choisie, telle que kubernetes ou Cloud Foundry.

La distribution continue est activée pour certaines applications. Vous souhaiterez peut-être activer la distribution continue pour automatiser les générations, les tests et les déploiements via le pipeline de distribution et GitHub.

1. Sélectionnez votre projet sur la page **Projets**. 

2. Cliquez sur **Déployer dans Cloud**.

3. Sélectionnez une méthode de déploiement. Les deux options suivantes s'offrent à vous :

	* Effectuer un déploiement sur un cluster Kubernetes. Mettez à disposition un cluster d'hôtes, appelé noeuds d'employé, afin de déployer et de gérer des conteneurs d'application à haute disponibilité. Vous pouvez créer un cluster ou effectuer un déploiement sur un cluster existant. 

	* Effectuer un déploiement à l'aide de Cloud Foundry, auquel cas, vous n'avez pas à vous préoccuper de gérer l'infrastructure sous-jacente.

## Etape 3 : Générer le code de votre projet
{: #generate-code}

Si vous avez créé une chaîne d'outils à l'étape précédente, un référentiel Git a été créé pour votre projet et vous y trouverez le code. Procédez comme suit pour accéder à votre référentiel :

1. Sélectionnez votre projet sur la page **Projets**. 

2. Cliquez sur **Afficher la chaîne d'outils**.

3. Cliquez sur la carte **Git** sous l'en-tête **CODE** afin d'ouvrir votre référentiel dans lequel vous pouvez visualiser le code source et cloner votre projet. 

Si une chaîne d'outils n'a pas été activée, vous pouvez accéder à votre code en téléchargeant la source directement à partir de la vue Détails du projet. 

1. Sélectionnez votre projet sur la page **Projets**. 

2. Cliquez sur **Télécharger le code** pour télécharger l'archive de votre projet. 

## Etape 4 : Commencer à utiliser votre application
{: #code}

Commencez à utiliser le projet que vous avez téléchargé :

1. Développez le fichier archivé.

2. Importez le projet dans votre interface IDE. 

3. Modifiez le code si nécessaire. 

4. Utilisez le {{site.data.keyword.dev_cli_notm}} pour générer et exécuter votre code localement. 


## Etape 5 : Générer et exécuter l'application localement
{: #build-run}

Ajoutez votre propre code, puis générez et exécutez le projet. Vous pouvez exécuter l'application localement sur votre système hôte si vous installez les outils de génération nécessaires, ou en utilisant le support de conteneur disponible dans le {{site.data.keyword.dev_cli_notm}}.

### Utilisation du plug-in {{site.data.keyword.dev_cli_short}}

1. Installez les dépendances de noeud :

  ```
  npm install
  ```
  {: codeblock}

2. Regroupez votre code de premier plan dans un module :

  ```
  gulp
  ```
  {: codeblock}

3. Pour générer le projet dans votre répertoire de projet en cours, entrez la commande suivante :

  ```
  bx dev build
  ```
  {: codeblock}

4. Pour exécuter le projet dans votre répertoire de projet en cours, entrez la commande suivante :

  ```
  bx dev run
  ```
  {: codeblock}

5. Ouvrez votre navigateur dans `http://localhost:3000` (votre numéro de port peut être différent selon l'environnement d'exécution choisi). 


## Etape 6 : Effectuer un déploiement sur le cloud
{: #deploy}

### Effectuer un déploiement à l'aide d'une chaîne d'outils
Il existe plusieurs moyens de déployer une application sur {{site.data.keyword.cloud_notm}}, mais l'utilisation d'une chaîne d'outils DevOps reste le meilleur moyen de déployer des applications de production. Une chaîne d'outils DevOps vous permet d'automatiser facilement des déploiements sur plusieurs environnements et d'ajouter rapidement des services de surveillance, de journalisation et d'alerte afin de vous aider à gérer votre application à mesure qu'elle grossit. 

Avec une chaîne d'outils correctement configurée, un cycle de génération-déploiement démarre automatiquement avec chaque fusion vers la branche principale de votre référentiel. Toutes les chaînes d'outils créées à partir d'un tableau de bord de développeur {{site.data.keyword.cloud_notm}} sont configurées pour un déploiement automatique.

Vous pouvez également déployer manuellement votre application depuis votre chaîne d'outils DevOps :

1. Sélectionnez votre projet sur la page **Projets**. 

2. Cliquez sur **Afficher la chaîne d'outils**.

3. Affichez votre pipeline de distribution où vous pouvez démarrer des générations, gérer le déploiement et visualiser les journaux et l'historique. 

### Effectuer un déploiement à l'aide du plug-in {{site.data.keyword.dev_cli_short}}
Si vous choisissez de ne pas utiliser une chaîne d'outils, vous pouvez également effectuer un déploiement à l'aide du plug-in {{site.data.keyword.dev_cli_short}}.

Pour déployer votre projet sur Cloud Foundry, entrez la commande suivante :

  ```
  bx dev deploy
  ```
  {: codeblock}

Pour déployer votre projet sur un cluster Kubernetes, entrez la commande suivante :

```
bx dev deploy --target <container>
```
{: codeblock}

### Vérifier que votre application est active
Une fois l'application déployée, vous verrez une URL semblable à `abc-devhost.mybluemix.net` dans le pipeline DevOps ou dans le terminal (si vous utilisez la ligne de commande). Visitez l'URL dans votre navigateur. 
