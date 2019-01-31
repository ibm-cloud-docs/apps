---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-03"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Déploiement de votre propre code dans un cluster Kubernetes
{: #tutorial}

Découvrez comment créer une application dans {{site.data.keyword.cloud}} en utilisant votre référentiel d'applications. Vous pouvez connecter votre chaîne d'outils DevOps existante ou en créer une et fournir en continu une application à un conteneur sécurisé dans un cluster Kubernetes. Ce tutoriel présente comment configurer un pipeline DevOps d'intégration en continu afin que la modification soit automatiquement générée et propagée à votre application déployée dans le cluster Kubernetes.
{: shortdesc}

Lorsque vous avez déjà un référentiel de codes source avec un codebase pour une application d'arrière-plan opérationnelle, {{site.data.keyword.cloud_notm}} vous permet d'organiser cet actif dans une vue agrégée de tous les actifs constituant l'ensemble du produit. {{site.data.keyword.cloud_notm}} vous permet d'utiliser un flux de travaux DevOps évolutif lorsque vous avez recours à la fonction de chaîne d'outils DevOps. Ce tutoriel permet à l'ingénieur DevOps ou au développeur expérimenté d'acquérir et de configurer un cluster {{site.data.keyword.cloud_notm}} Kubernetes cible et de configurer et d'exécuter une chaîne d'outils DevOps, en suivant les meilleures pratiques en matière de cloud.

Un _cluster_ est un ensemble de ressources, de noeuds d'agent, de réseaux et de périphériques de stockage permettant d'assurer une haute disponibilité des applications. Une fois que vous avez créé votre cluster, vous pouvez déployer vos applications dans des conteneurs.
{: tip}

## Avant de commencer
{: #prereqs}

* Créez une application. Pour plus d'informations, voir [Création d'applications à partir de votre propre référentiel de codes](/docs/apps/tutorials/tutorial_byoc.html).
* Dans la console [{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}){: new_window}, cliquez sur l'icône **Menu** ![Icône Menu](../../icons/icon_hamburger.svg) puis sélectionnez **Conteneurs** pour [configurer un cluster Kubernetes](/docs/containers/container_index.html).
* Pour confirmer que votre application s'exécute dans Docker, exécutez les commandes suivantes :
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install  
  `
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* Ensuite, accédez à votre URL (`http://localhost/springboothelloworld/sayhello` par exemple). Appuyez sur les touches Ctrl+C pour arrêter l'exécution de Docker.

## Ajout de ressources à votre application (facultatif)
{: #add_resources}

Ajoutez une ressource de service à votre application, {{site.data.keyword.cloud_notm}} crée alors le service pour vous. Le processus de mise à disposition peut varier en fonction des types de service. Par exemple, un service de base de données crée une base de données, un service de notification push pour des applications mobiles génère des informations de configuration. {{site.data.keyword.cloud_notm}} fournit les ressources d'un service à votre application par le biais d'une
instance de service. Une instance de service peut être partagée entre plusieurs applications Web.

Ce processus met à disposition une instance de service, crée une clé de ressource (données d'identification) et l'associe à votre application. Pour plus d'informations, voir [Ajout d'un service à votre application](/docs/apps/reqnsi.html).

Une fois que vous avez ajouté une ressource de service à votre application, vous devez copier les données d'identification du service dans votre environnement de déploiement. Pour plus d'informations, voir [Ajout de données d'identification à votre environnement Kubernetes](/docs/apps/creds_kube.html).

## Préparation de votre application pour le déploiement
{: #connect_toolchain}

Dans cette étape, vous allez associer une chaîne d'outils DevOps à l'application et allez la configurer afin qu'elle soit déployée dans un cluster Kubernetes hébergé dans le service {{site.data.keyword.cloud_notm}} Kubernetes.

La chaîne d'outils DevOps est suffisamment flexible pour permettre l'exécution gérée d'étapes arbitraires d'exécution de script shell. Autrement dit, vous pouvez effectuer quasiment toutes les actions avec une chaîne d'outils DevOps. La portée de cette section cible le déploiement de votre application sur un cluster Kubernetes, tout en gardant à l'esprit une vérification future de DevOps mis à l'échelle et des meilleures pratiques en matière de cloud.

L'établissement d'une liaison entre votre application, la chaîne d'outils et le référentiel constitue une étape dans l'organisation de vos actifs de produit. Cette opération vous permet également d'agréger une vue de votre référentiel source avec le flux de travaux DevOps, vos instances d'application en cours d'exécution et les services dépendants dans l'ensemble de vos cibles de déploiement.

Sur la page Connecter la chaîne d'outils, vous disposez de plusieurs options :

* Connexion de votre page à une chaîne d'outils existante.
* Connexion de votre application à une chaîne d'outils existante ne contenant pas votre référentiel. Connectez ensuite la chaîne d'outils à votre référentiel ultérieurement.
* Connexion de votre application à une nouvelle chaîne d'outils.

### Connexion de votre application à une chaîne d'outils existante
{: #connect_toolchain_repo}

Si vous avez une ou plusieurs chaînes d'outils DevOps déjà connectées au référentiel Git spécifié lors de la création de votre application, ces chaînes d'outils s'affichent dans le tableau présentant les chaînes d'outils avec votre référentiel. La chaîne d'outils doit être configurée pour extraire la source à partir du référentiel défini dans l'application. Il est fort probable que vous souhaitiez sélectionner une de ces chaînes d'outils à connecter à votre application.

### Connexion de votre application à une chaîne d'outils existante qui ne contient pas votre référentiel
{: #connect_toolchain_notrepo}

Si vous avez une ou plusieurs chaînes d'outils DevOps associées à votre compte mais que vous n'êtes pas connecté au référentiel Git spécifié lors de la création de votre application, ces chaînes d'outils s'affichent dans le tableau présentant les chaînes d'outils sans votre référentiel. Vous pouvez sélectionner une de ces chaînes d'outils et la connecter à votre application mais vous devez également ajouter manuellement votre référentiel à cette chaîne d'outils.

Pour plus d'informations sur l'ajout de votre référentiel à votre chaîne d'outils, voir :

 * [Configuration de Git Repos and Issue Tracking](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitbluemix)
 * [Configuration de GitHub](/docs/services/ContinuousDelivery/toolchains_integrations.html#github)
 * [Configuration de GitLab](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitlab)


### Connexion de votre application à une nouvelle chaîne d'outils
{: #create_toolchain}

Si vous souhaitez complètement contrôler la création de la chaîne d'outils DevOps sans que votre référentiel de code ne soit modifié, créez une toute nouvelle chaîne d'outils. Vous créez également toutes les intégrations pour générer votre application et la déployer dans le cluster Kubernetes. 

1. Sur la page Créer une chaîne d'outils, cliquez sur le modèle **Construisez votre propre chaîne d'outils**.
2. Entrez un nom pour votre chaîne d'outils, sélectionnez une région et un groupe de ressources puis cliquez sur **Créer**.

Lorsque vous choisissez de créer une chaîne d'outils à partir de votre nouvelle application, la page [Créer une chaîne d'outils](https://{DomainName}/devops/create) du tableau de bord DevOps s'affiche dans un nouvel onglet de votre navigateur. Une fois que vous avez créé et configuré votre chaîne d'outils dans cet onglet, vous devez revenir à la page Connecter la chaîne d'outils dans votre application et actualiser la page.
{:tip}

Si vous ne souhaitez pas créer de toute nouvelle chaîne d'outils DevOps, vous pouvez activer sur le cloud votre code existant en utilisant la commande [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable). La commande génère un modèle de chaîne d'outils DevOps que vous réservez dans votre référentiel. Vous devez alors utiliser ce modèle en tant que jeu d'instructions pour les éléments créés par la chaîne d'outils DevOps. Pour plus d'informations, voir la [documentation de l'interface CLI](/docs/apps/create-deploy-cli.html#byoc).

## Ajout d'une intégration GitHub

Configurez la chaîne d'outils DevOps avec une intégration de votre référentiel GitHub pour que la chaîne d'outils définisse un webhook dans votre référentiel afin que les demandes d'extraction et les transmissions de code dans ce référentiel envoient un événement POST à la chaîne d'outils. 

1. Dans votre modèle de chaîne d'outils DevOps, cliquez sur **Ajouter un outil**.
2. Sélectionnez **GitHub** si votre référentiel se trouve sur Public GitHub ou Enterprise GitHub.
3. Sélectionnez ou entrez l'URL du serveur GitHub.
4. Un message `Unauthorized on GitHub` peut être affiché. Le cas échéant, cliquez sur **Autoriser**. Puis sur la page Autoriser IBM Cloud Toolchains, cliquez sur Autoriser IBM-Cloud et entrez votre mot de passe GitHub.
5. Sur la page Configurer l'intégration, sélectionnez **Existant** pour le type de référentiel afin que la chaîne d'outils DevOps configure le référentiel avec un webhook et n'effectue aucune déviation ou copie de votre référentiel.
6. Entrez votre URL de référentiel, par exemple `https://github.com/yourrepo/spring-boot-hello-world`.
7. Attendez quelques instants. Une invite peut alors s'afficher vous demandant d'autoriser GitHub à accorder des droits à la chaîne d'outils DevOps afin d'utiliser l'API ReST GitHub pour configurer votre référentiel avec les webhooks nécessaires au déclenchement de la chaîne d'outils.
8.  Cliquez sur **Créer une intégration**.

Vous pouvez afficher le nouveau webhook à partir de vos paramètres de référentiel.

## Ajout d'un composant Delivery Pipeline

1. Cliquez sur **Ajouter un outil**.
2. Sélectionnez **Delivery Pipeline**.
3. Entrez `Intégration continue` comme nom de pipeline puis cliquez sur **Créer une intégration**.

## Configuration de vos étapes de pipeline

Configurez les étapes de pipeline pour diriger votre entrée (contenu du référentiel GitHub) vers la destination appropriée. Etant donné que ce tutoriel suppose que vous avez un référentiel GitHub qui génère une image Docker fonctionnelle et qui cible un cluster IBM Containers Kubernetes, vous créez des étapes de pipeline avec des entrées, des scripts shell et des sorties permettant d'atteindre cet objectif.

1. Configurez votre étape de pipeline de `génération et de publication`.
  1. Sélectionnez le pipeline de distribution que vous avez créé puis cliquez sur **Ajouter une étape**.
  2. Cliquez sur l'onglet **Entrée** puis renseignez les zones de la manière suivante :
    * Entrez `générer et publier votre image Docker` comme nom d'étape.
    * Sélectionnez **Référentiel Git** comme type d'entrée.
    * Sélectionnez votre référentiel GitHub.
    * Sélectionnez la branche utilisée pour l'intégration continue.
  3.  Cliquez sur l'onglet **Travaux**, sur **Ajouter un travail '+'** puis renseignez les zones de la manière suivante :
    * Sélectionnez l'option de génération**** pour le type de travail.
    * Entrez `générer et publier` comme nom.
    * Sélectionnez **Container Registry** comme type de générateur.
    * Sélectionnez la région dans laquelle se trouve votre cluster Kubernetes.
    * Sélectionnez **Entrer une clé d'API existante**. Si vous n'avez pas de clé d'API, voir [Création d'une clé d'API](/docs/iam/userid_keys.html#creating-an-api-key). 
    * Entrez l'espace de nom du registre de conteneur que vous pouvez trouver en cliquant sur l'icône **Menu** ![Icône Menu](../../icons/icon_hamburger.svg) et en sélectionnant **Conteneurs** > **Registre** > **Espaces de nom**.
    * Pour le nom de l'image Docker, entrez `continu` car cette étape de génération de pipeline s'applique à la génération continue de la branche d'intégration en continu de votre référentiel.
    * Editez le script de génération en ajoutant une ou plusieurs lignes après la première ligne `#!/bin/bash`. Par exemple, pour un référentiel généré en utilisant maven, vous pouvez ajouter quelques lignes similaires à l'exemple suivant :

      ```bash
      export JAVA_HOME=/opt/IBM/java8
      # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
      export MAVEN_OPTS="-  
      Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
      mvn -B clean verify
      ```
      {: codeblock}
  4. Cliquez sur **Enregistrer**. 
2. Testez votre étape de pipeline de `génération et de publication` en cliquant sur l'icône **Exécuter** jusqu'à ce que la génération aboutisse. L'étape Vert indique que la génération a abouti. 
3. Configurez votre étape de pipeline de `déploiement dans le cluster` afin de déployer l'image Docker dans votre cluster Kubernetes. 
  1. Sur la page Delivery Pipeline, cliquez sur **Ajouter une étape**.
  2. Cliquez sur l'onglet **Entrée** puis renseignez les zones de la manière suivante :
    * Entrez `Déploiement dans le cluster` comme nom.
    * Sélectionnez **Artefacts de génération** pour le type d'entrée.
    * Sélectionnez l'option de génération et de publication d'image Docker**** pour l'étape.
    * Sélectionnez l'option de génération et de publication**** pour le travail.
    * Etant donné qu'il s'agit de votre pipeline d'intégration continue, acceptez l'option par défaut pour le déclencheur d'étape.
  3. Cliquez sur l'onglet **Travaux**, sur **Ajouter un travail '+'** puis renseignez les zones de la manière suivante :
    * Entrez `Déploiement dans le cluster d'intégration continue` comme nom.
    * Sélectionnez **Kubernetes** comme type de déployeur.
    * Sélectionnez la région dans laquelle se trouve votre cluster Kubernetes.
    * Entrez votre clé d'API existante. 
  4. Cliquez sur **Enregistrer**.
4. Testez votre étape de pipeline de déploiement sur le cluster`` en cliquant sur l'icône **Exécuter** jusqu'à ce que la génération aboutisse. L'étape Vert indique que la génération a abouti. Vous pouvez afficher les journaux pour l'étape. Dans la dernière partie des journaux, recherchez un lien vers l'application en cours d'exécution. Ajoutez le chemin correct de votre application afin de confirmer que cette dernière s'exécute.
