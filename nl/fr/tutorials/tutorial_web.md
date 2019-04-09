---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Création d'une application Web basique avec un kit de démarrage
{: #tutorial-webapp}

{{site.data.keyword.cloud}} inclut plusieurs kits de démarrage vous permettant d'effectuer les opérations de codage rapidement. Choisissez un langage, une infrastructure et des outils dans les kits de démarrage de service d'application afin de commencer à utiliser une application personnalisée préconfigurée. Dans ce tutoriel, vous allez installer les outils dont vous avez besoin puis vous allez générer et exécuter l'application localement et la déployer dans le cloud.
{: shortdesc}

## Etape 1. Installer les outils
{: #prereqs-webapp}

Installez les [outils de développement](/docs/cli/index.html).

Docker est installé en tant qu'outil de développement. Pour que les commandes de génération fonctionnent, Docker doit être en cours d'exécution. Vous devez créer un compte Docker, exécuter l'application Docker et vous connecter.

## Etape 2. Sélectionner un kit de démarrage
{: #create-webapp}

Les kits de démarrage sont disponibles dans de nombreux langages et infrastructures de la console {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}. Sélectionnez le langage le plus adapté à votre projet pour commencer.

1. Sur la page des [kits de démarrage ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/appservice/starter-kits/) de la console {{site.data.keyword.dev_console}}, sélectionnez un kit de démarrage pour votre langage.
2. Entrez votre nom d'application et un nom d'hôte unique, par exemple, `abc-devhost`. Ce nom d'hôte correspond à la route de votre application, `abc-devhost.cloud.ibm.com`
3. Facultatif. Créez des étiquettes pour classer votre application. Pour plus d'informations, voir [Utilisation d'étiquettes](/docs/resources/tagging_resources.html#tag).
4. Sélectionnez votre langage et votre infrastructure. Certains kits de démarrage peuvent être disponibles dans un seul langage.
5. Sélectionnez votre plan de tarification. Il existe une option gratuite que vous pouvez utiliser pour ce tutoriel.
6. Cliquez sur **Créer**.

## Etape 3. Ajouter des ressources (facultatif)
{: #resources-webapp}

Vous pouvez ajouter des ressources qui améliorent votre application avec la puissance cognitive de Watson, ajoutent des services mobiles ou des services de sécurité. Pour ce tutoriel, ajoutez un emplacement pour gérer vos données.

1. Dans la fenêtre de service d'application, cliquez sur **Ajouter une ressource**.
2. Sélectionnez le type de service souhaité. Par exemple, sélectionnez **Données** > **Suivant** > **Cloudant** > **Suivant**.
3. Sélectionnez votre plan de tarification. Il existe une option gratuite que vous pouvez utiliser pour ce tutoriel.
4. Cliquez sur **Créer**.

## Etape 4. Créer une chaîne d'outils DevOps
{: #toolchain-webapp}

L'activation d'une chaîne d'outils permet de créer un environnement de développement basé sur une équipe pour votre application. Lorsque vous créez une chaîne d'outils, le service d'application crée un référentiel Git dans lequel vous pouvez afficher le code source, cloner votre application, créer et gérer des problèmes. Vous avez également accès à un environnement de lab dédié Git et à un pipeline de distribution continue. Ces éléments sont personnalisés en fonction de l'environnement de déploiement choisi, [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) ou [Virtual Server (VSI)](/docs/vsi/vsi_index.html).

La distribution continue est activée pour certaines applications. Vous pouvez activer la distribution continue pour automatiser les générations, les tests et les déploiements via Delivery Pipeline et GitHub.

Cliquez sur **Déployer dans le cloud** sur la page Détails de l'application, sélectionnez un environnement de déploiement puis cliquez sur **Créer**. {{site.data.keyword.cloud_notm}} crée automatiquement une chaîne d'outils ouverte complétée par un référentiel Git et un pipeline de distribution continue.

Une fois que vous avez sélectionné votre environnement de déploiement, ouvrez le composant Pipeline de votre nouvelle chaîne d'outils pour démarrer le processus de génération et de déploiement initial de sorte que vous puissiez voir votre application après quelques minutes.

Pour plus d'informations, voir [Création de chaînes d'outils](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

## Etape 5. Générer et exécuter l'application localement
{: #build-run-webapp}

Le déploiement de votre application dans le cloud effectué lors de la dernière étape a créé une chaîne d'outils. Cette dernière crée un référentiel Git pour votre application dans lequel vous pouvez trouver le code. Procédez comme suit pour accéder à votre référentiel. Vous pouvez générer l'application localement à des fins de test avant de la placer dans le cloud.

1. Dans la fenêtre de service d'application, cliquez sur **Télécharger le code** ou **Cloner votre référentiel** pour utiliser votre code localement.
2. Importez l'application dans votre environnement de développement intégré.
3. Modifiez le code.
4. Configurez l'[authentification Git](/docs/services/ContinuousDelivery/git_working.html#git_authentication) en ajoutant un jeton d'accès personnel.
5. Connectez-vous à l'interface de ligne de commande {{site.data.keyword.cloud_notm}}. Si votre entreprise utilise des connexions fédérées, utilisez l'option `-sso`.

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Configurez vos cibles d'organisation et d'espace.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. Obtenez les données d'identification.

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

10. Ouvrez votre navigateur dans `http://localhost:3000`. Votre numéro de port peut être différent en fonction de l'environnement d'exécution choisi.

## Etape 6. Déployer votre application
{: #deploy-webapp}

### Déploiement à l'aide d'une chaîne d'outils
{: #deploy-webapp-toolchain}

Vous pouvez déployer votre application dans {{site.data.keyword.cloud_notm}} de différentes manières. Mais l'utilisation d'une chaîne d'outils DevOps reste le meilleur moyen de déployer des applications de production. A l'aide d'une chaîne d'outils DevOps, vous pouvez facilement automatiser un grand nombre de déploiements et ajouter rapidement des services de surveillance, de journalisation et d'alerte afin de gérer plus facilement votre application à mesure de sa croissance.

Avec une chaîne d'outils correctement configurée, un cycle de génération-déploiement démarre automatiquement avec chaque fusion vers la branche principale de votre référentiel. Toutes les chaînes d'outils créées à partir d'un tableau de bord de développeur {{site.data.keyword.cloud_notm}} sont configurées pour un déploiement automatique.

Vous pouvez également déployer manuellement votre application depuis votre chaîne d'outils DevOps :

1. Dans la fenêtre Détails de l'application, cliquez sur **Afficher la chaîne d'outils**.
2. Cliquez sur **Delivery pipeline**. Vous pouvez alors démarrer des générations, gérer le déploiement et afficher les journaux et l'historique.

Pour plus d'informations, voir [Génération et déploiement](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy).

### Déploiement en utilisant {{site.data.keyword.dev_cli_short}}
{: #deploy-webapp-cli}

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

## Etape 7. Vérifier que votre application est en cours d'exécution
{: #verify-webapp}

Une fois votre application déployée, Delivery Pipeline ou la ligne de commande indique l'URL de votre application.

1. Dans votre chaîne d'outils DevOps, cliquez sur **Delivery Pipeline** puis sélectionnez **Etape de déploiement**.
2. Cliquez sur **Afficher les journaux et l'historique**.
3. Dans le fichier journal, recherchez l'URL de l'application :

    A la fin du fichier journal, recherchez le mot `urls` ou `view`. Par exemple, une ligne similaire à `urls: my-app-devhost.cloud.ibm.com` ou à `View the application health at: http://<ipaddress>:<port>/health` peut être incluse dans le fichier journal.

4. Accédez à l'URL dans votre navigateur. Si l'application est en cours d'exécution, un message qui inclut `Congratulations` ou `{"status":"UP"}` s'affiche.

Si vous utilisez la ligne de commande, exécutez la commande [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) pour afficher l'URL de votre application. Accédez ensuite à l'URL dans votre navigateur.
