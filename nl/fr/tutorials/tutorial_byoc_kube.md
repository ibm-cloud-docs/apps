---

copyright:
  years: 2018
lastupdated: "2018-11-29"

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

* Suivez la procédure de [création d'applications à partir de votre propre référentiel de codes](/docs/apps/tutorials/tutorial_byoc.html) pour créer une application.
* A partir du tableau de bord [{{site.data.keyword.cloud_notm}}![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}){: new_window}, cliquez sur l'icône **Menu**![Icône Menu](../../icons/icon_hamburger.svg) et sélectionnez **Conteneurs** pour [configurer un cluster Kubernetes](/docs/containers/container_index.html).
* Pour confirmer que votre application s'exécute dans Docker, exécutez les commandes suivantes :
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install  
  `
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* Ensuite, consultez votre URL, comme `http://localhost/springboothelloworld/sayhello`.   
Appuyez sur les touches `Ctrl+C` pour arrêter l'exécution de Docker.

## Ajout de ressources à votre application (Facultatif)
{: #add_resources}

Ajoutez une ressource de service à votre application, {{site.data.keyword.cloud_notm}} crée alors le service pour vous. Le processus de mise à disposition peut varier en fonction des types de service. Par exemple, un service de base de données crée une base de données, un service de notification push pour des applications mobiles génère des informations de configuration. {{site.data.keyword.cloud_notm}} fournit les ressources d'un service à votre application par le biais d'une
instance de service. Une instance de service peut être partagée entre plusieurs applications Web.

Ce processus met à disposition une instance de service, crée une clé de ressource (données d'identification) et l'associe à votre application. Pour plus d'informations, voir [Ajout d'un service à votre application](/docs/apps/reqnsi.html).

### Copie de données d'identification de service dans votre environnement

Une fois que vous avez ajouté une ressource de service à votre application, notez que les données d'identification de ce service s'affichent dans la zone **Données d'identification**. Vous devez copier les données d'identification dans votre environnement de déploiement.

Pour plus d'informations sur la copie des données d'identification dans votre environnement, voir [Ajout de données d'identification à votre environnement Kubernetes](/docs/apps/creds_kube.html).


## Préparation de votre application pour le déploiement en utilisant une chaîne d'outils DevOps
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

Les méthodes suivantes permettent de connecter votre application à une nouvelle chaîne d'outils :
* Si vous ne souhaitez pas créer de toute nouvelle chaîne d'outils DevOps, vous pouvez activer sur le cloud votre code existant en utilisant la commande [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable). La commande génère un modèle de chaîne d'outils DevOps que vous réservez dans votre référentiel. Vous devez alors utiliser ce modèle en tant que jeu d'instructions pour les éléments créés par la chaîne d'outils DevOps. Pour plus d'informations, voir la [documentation de l'interface CLI](/docs/apps/create-deploy-cli.html#byoc).
* Créez une toute nouvelle chaîne d'outils DevOps dans la console. Si vous souhaitez complètement contrôler la création de la chaîne d'outils DevOps sans que votre référentiel de code ne soit modifié, créez une toute nouvelle chaîne d'outils. Pour plus d'informations, voir [Création d'une toute nouvelle chaîne d'outils DevOps](#create_toolchain_scratch).

#### Création d'une toute nouvelle chaîne d'outils DevOps
{: #create_toolchain_scratch}

Si vous souhaitez créer une toute nouvelle chaîne d'outils et la connecter à votre application, procédez comme suit. Vous créez également toutes les intégrations pour générer votre application et la déployer dans le cluster Kubernetes. La fonction de chaîne d'outils DevOps inclut des modèles mais cette procédure permet de configurer une toute nouvelle chaîne d'outils DevOps.

Lorsque vous choisissez de créer une chaîne d'outils à partir de votre nouvelle application, la page [Créer une chaîne d'outils](https://{DomainName}/devops/create) du [tableau de bord DevOps](https://{DomainName}/devops/) s'affiche dans un nouvel onglet de votre navigateur. Une fois que vous avez créé et configuré votre chaîne d'outils dans cet onglet, vous devez revenir à la page **Connecter la chaîne d'outils** dans votre application et actualiser la page.
{:tip}

1. Sur la page **Créer une chaîne d'outils**, cliquez sur le modèle **Construisez votre propre chaîne d'outils**.
2. Sur la page **Construisez votre propre chaîne d'outils**, entrez un nom pour votre chaîne d'outils, sélectionnez une région et un groupe de ressources puis cliquez sur **Créer**.

Une chaîne d'outils vide sans intégration ou outil préconfiguré est créée. Configurez et testez votre nouvelle chaîne d'outils en effectuant les étapes suivantes.

## Ajout d'une intégration GitHub

Vous pouvez configurer la chaîne d'outils DevOps avec l'intégration GitHub en procédant comme suit :

1. Dans votre modèle de chaîne d'outils DevOps, cliquez sur **Ajouter un outil**.
2. Sélectionnez **GitHub** (si votre référentiel se trouve sur Public GitHub ou Enterprise GitHub).
3. Sur la page **Configurer l'intégration** pour GitHub, procédez comme suit :
  * Sélectionnez (ou entrez) l'URL de **GitHub Server**.
  * Si un message "Non autorisé sur GitHub" s'affiche, cliquez sur **Autoriser**. Puis sur la page **Autoriser IBM Cloud Toolchains**, cliquez sur **Autoriser IBM-Cloud**. Entrez ensuite votre mot de passe GitHub.
  * Sur la page **Configurer l'intégration**, sélectionnez **Existant** dans la zone **Type de référentiel** afin que la chaîne d'outils DevOps configure le référentiel avec un webhook et n'effectue _aucune_ déviation ou copie de votre référentiel.
  * Entrez votre **URL de référentiel**. (Par exemple, `https://github.com/yourrepo/spring-boot-hello-world`).
  * Attendez quelques instants. Une invite peut alors s'afficher vous demandant d'autoriser GitHub à accorder des droits à la chaîne d'outils DevOps afin d'utiliser l'API ReST GitHub pour configurer votre référentiel avec les webhooks nécessaires au déclenchement de la chaîne d'outils.
  * Cliquez sur **Créer une intégration**.

Vous avez configuré cette chaîne d'outils DevOps avec une intégration pour votre référentiel GitHub. Ainsi, vous permettez à la chaîne d'outils de définir un webhook dans votre référentiel afin que les demandes d'extraction et les envois de code par commandes push dans ce référentiel déclenchent un événement POST dans la chaîne d'outils. Vous pouvez consulter les paramètres de votre référentiel pour voir le nouveau webhook.

## Ajout d'un élément Delivery Pipeline pour générer, tester et déployer votre application

Les différentes actions ont lieu dans Delivery Pipeline.

1. Cliquez sur **Ajouter un outil**.
2. Sélectionnez **Delivery Pipeline**.
3. Sur la page **Configurer l'intégration** pour Delivery Pipeline, procédez comme suit :
 * Entrez "Intégration continue" comme nom de pipeline.
 * Cliquez sur **Créer une intégration**.

Vous avez créé un pipeline de distribution vide. Vous définissez ensuite des étapes de pipeline pour diriger votre entrée (contenu du référentiel GitHub) vers sa destination. Etant donné que ce tutoriel suppose que vous avez un référentiel GitHub qui génère une image Docker fonctionnelle et qui cible un cluster IBM Containers Kubernetes, vous créez des étapes de pipeline avec des entrées, des scripts shell et des sorties permettant d'atteindre cet objectif.

### Configuration de l'étape de pipeline de génération et de publication

1. Cliquez sur le pipeline de distribution que vous avez créé.
2. Sur la page Delivery Pipeline, cliquez sur **Ajouter une étape**.
3. Sur l'onglet **Entrée** de la page **Configuration de l'étape**, renseignez les zones de la manière suivante :
  * Pour le nom de l'étape, entrez **Générer & publier l'image Docker**.
  * **Type d'entrée** - Sélectionnez **Référentiel Git**.
  * **Référentiel Git** - Sélectionnez votre référentiel GitHub.
  * **Branche** - Sélectionnez la branche utilisée pour l'intégration continue.
4. Cliquez sur l'onglet **Travaux** puis renseignez les zones de la manière suivante :
  * Cliquez sur l'icône **Ajouter un travail '+'** et sélectionnez **Génération** pour le type de travail.
  * Entrez un nom, comme **Générer & publier**.
  * **Type de générateur** - Sélectionnez **Container Registry**.
  * **Région IBM Cloud** - Sélectionnez la région dans laquelle se trouve votre cluster Kubernetes.
  * **Clé d'API** - Sélectionnez **Entrer une clé d'API existante**. Si vous n'avez pas de clé ou ne connaissez pas votre clé d'API, vous pouvez [obtenir une clé d'API](https://{DomainName}/iam/#/apikeys) en ouvrant une autre fenêtre de navigateur et en accédant à **Gérer** > **Sécurité** > **Clés d'API de la plateforme**. Pensez à conserver cette clé à un emplacement sûr.
  * **Nom de compte** - Cette zone est renseignée automatiquement lorsque vous entrez une clé d'API.
  * **Espace de nom de Container Registry** - Entrez l'[espace de nom du registre de conteneur](https://{DomainName}/containers-kubernetes/registry/namespaces) (vous pouvez le trouver en cliquant sur l'icône **Menu**![Icône Menu](../../icons/icon_hamburger.svg) et en sélectionnant **Conteneurs** > **Registre** > **Espaces de nom**.)
  * **Nom d'image Docker** - Entrez **continu** car cette étape de génération de pipeline s'applique à la génération continue de la branche d'intégration continue de votre référentiel.
  * **Script de génération** - Notez le script shell. Les instructions de génération d'application sont manquantes pour _votre_ référentiel. Vous devez ajouter au moins une ligne après la première ligne `#!/bin/bash`. Par exemple, pour un référentiel généré en utilisant maven, vous pouvez ajouter quelques lignes similaires à l'exemple suivant :

    ```bash
    export JAVA_HOME=/opt/IBM/java8
    # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
    export MAVEN_OPTS="-Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
    mvn -B clean verify
    ```
    {: codeblock}
5. Cliquez sur **Sauvegarder**. Votre étape de pipeline de génération et de publication apparaît désormais dans votre chaîne d'outils.

### Test de votre étape de pipeline de génération et de publication

Cliquez sur l'icône **Ecouter** jusqu'à ce que la génération aboutisse. Vous savez que cette opération fonctionne lorsque l'étape devient verte et que la sortie du script confirme vos attentes. L'objectif de cette étape est de publier une image Docker dans votre registre d'images. Si le script ne s'affiche pas suffisamment, vous pouvez consulter le registre d'images pour confirmer la publication en cliquant sur l'icône **Menu** ![Icône Menu](../../icons/icon_hamburger.svg) puis en sélectionnant **Conteneurs** > **Registre** > **Référentiels privés**. Confirmez ensuite qu'un référentiel qui se termine par le nom `/continu` est répertorié. Nous vous rappelons qu'il s'agit du nom de l'image. 

### Configuration de l'étape de pipeline de déploiement sur un cluster

Jusqu'à présent, vous avez publié une image Docker dans votre registre d'images Docker privé. Maintenant, nous allons créer une étape qui déploie cette image dans votre cluster Kubernetes.

1. Sur la page Delivery Pipeline, cliquez sur **Ajouter une étape**.
2. Sur l'onglet **Entrée** de la page **Configuration de l'étape**, renseignez les zones de la manière suivante :
  * **Nom** - Entrez **Déployer**.
  * **type d'entrée** - Sélectionnez **Artefacts de génération**.
  * **Etape** - Sélectionnez **Générer & publier l'image Docker**.
  * **Travail** - Sélectionnez **Générer & publier**.
  * **Déclencheur d'étape** - Etant donné qu'il s'agit de votre pipeline d'intégration continue, sélectionnez l'option **Exécuter les travaux lorsque l'étape précédente est terminée** par défaut.
3. Cliquez sur l'onglet **Travaux** puis renseignez les zones de la manière suivante :
  * Cliquez sur l'icône **Ajouter un travail '+'** et sélectionnez **Déployer** comme type de travail.
  * Entrez un nom, comme **Déployer sur un cluster d'intégration continue**.
  * **Type de déployeur** - Sélectionnez **Kubernetes**.
  * **Région IBM Cloud** - Sélectionnez la région dans laquelle se trouve votre cluster Kubernetes.
  * **Clé d'API** - Sélectionnez **Entrer une clé d'API existante**. Si vous n'avez pas de clé ou ne connaissez pas votre clé d'API, vous pouvez [obtenir une clé d'API](https://{DomainName}/iam/#/apikeys) en ouvrant une autre fenêtre de navigateur et en accédant à **Gérer** > **Sécurité** > **Clés d'API de la plateforme**. Pensez à conserver cette clé à un emplacement sûr.
  * Acceptez les autres paramètres par défaut.
4. Cliquez sur **Sauvegarder**. Votre étape de pipeline de déploiement apparaît désormais dans votre chaîne d'outils.

### Test de votre étape de pipeline de déploiement sur un cluster

Cliquez sur l'icône **Ecouter** jusqu'à ce que la génération aboutisse. Vous savez que cette opération fonctionne lorsque l'étape devient verte et que la sortie du script confirme vos attentes. Vous pouvez afficher les journaux pour l'étape. Dans la dernière partie des journaux, recherchez un lien vers l'application en cours d'exécution. Toutefois, _vous_ seul connaissez le chemin et la racine du contexte de votre application. Ajoutez le chemin correct afin de confirmer que l'application s'exécute.
