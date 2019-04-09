---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Création d'une toute nouvelle application
{: #tutorial-scratch}

Vous pouvez créer une toute nouvelle application personnalisée en utilisant des services et un environnement d'exécution. 
{: shortdesc}

## Avant de commencer
{: #prereqs-scratch}

* Installez [{{site.data.keyword.dev_cli_long}}](/docs/cli/index.html), qui inclut Docker. 
* Créez un compte Docker, exécutez l'application Docker puis connectez-vous. Pour que les commandes de génération fonctionnent, Docker doit être en cours d'exécution.
* Si vous envisagez de déployer votre application dans [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about), vous devez [préparer votre compte {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry/prepare-account.html#prepare).

## Création de votre application
{: #create-scratch}

1. A partir de votre tableau de bord [{{site.data.keyword.cloud_notm}}![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://cloud.ibm.com), cliquez sur **Créer une application** dans le widget Applications.

  Vous pouvez également créer une application personnalisée à partir de la page [Kits de démarrage ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/appservice/starter-kits/) dans {{site.data.keyword.dev_console}}.
  {: tip}

2. Entrez un nom pour votre application. Pour ce tutoriel, entrez `CustomProject`.
3. Entrez un nom d'hôte unique, par exemple, `abc-devhost`. Ce nom d'hôte correspond à la route de votre application, par exemple `abc-devhost.cloud.ibm.com`
4. Vous pouvez éventuellement créer des étiquettes pour classer votre application. Pour plus d'informations, voir [Utilisation d'étiquettes](/docs/resources/tagging_resources.html#tag).
5. Sélectionnez votre langage et votre infrastructure. Certains kits de démarrage peuvent être disponibles dans un seul langage.
6. Sélectionnez votre plan de tarification. Vous pouvez utiliser l'option gratuite pour ce tutoriel.
7. Cliquez sur **Créer**.

## Ajout de ressources (facultatif)
{: #resources-scratch}

Vous pouvez ajouter des ressources qui améliorent votre application avec la puissance cognitive de Watson, ajoutent des services mobiles ou des services de sécurité. Pour ce tutoriel, vous pouvez ajouter un emplacement pour gérer vos données.

1. Dans la fenêtre Services d'appli, cliquez sur **Ajouter une ressource**.
2. Sélectionnez le type de service souhaité. Par exemple, sélectionnez **Données** > **Suivant** > **Cloudant** > **Suivant**.
3. Sélectionnez votre plan de tarification. Vous pouvez utiliser l'option gratuite pour ce tutoriel.
4. Cliquez sur **Créer**.

## Génération et exécution de l'application localement
{: #build-run-scratch}

Vous pouvez également générer l'application localement à des fins de test avant de pouvoir la déployer dans le cloud.

1. Dans la fenêtre Services d'appli, cliquez sur **Télécharger le code** ou **Cloner votre référentiel** pour utiliser votre code localement.
2. Importez l'application dans votre environnement de développement intégré.
3. Modifiez le code.
4. Configurez l'[authentification Git](/docs/services/ContinuousDelivery/git_working.html#git_authentication) en ajoutant un jeton d'accès personnel.
5. Connectez-vous à l'interface de ligne de commande {{site.data.keyword.cloud_notm}}. Si votre organisation utilise des connexions fédérées, utilisez l'option `-sso`, par exemple :

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Exécutez la commande suivante pour définir vos cibles d'organisation et d'espace.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. Exécutez la commande suivante pour extraire les données d'identification.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Assurez-vous que Docker est en cours d'exécution et exécutez la commande suivante pour générer votre application dans un conteneur de développement local à partir du répertoire.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Exécutez la commande suivante pour exécuter votre application dans un conteneur de développement local.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. Indiquez `http://localhost:3000` dans votre navigateur. Votre numéro de port peut être différent en fonction de l'environnement d'exécution choisi.

## Déploiement de votre application
{: #deploy-scratch}

Vous pouvez déployer votre application dans {{site.data.keyword.cloud_notm}} de différentes manières. Mais l'utilisation d'une chaîne d'outils DevOps reste le meilleur moyen de déployer des applications de production. A l'aide d'une chaîne d'outils DevOps, vous pouvez facilement automatiser un grand nombre de déploiements et ajouter rapidement des services de surveillance, de journalisation et d'alerte afin de gérer plus facilement votre application à mesure de sa croissance.

L'activation d'une chaîne d'outils permet de créer un environnement de développement basé sur une équipe pour votre application. Lorsque vous créez une chaîne d'outils, le service d'application crée un référentiel Git dans lequel vous pouvez afficher le code source, cloner votre application, créer et gérer des problèmes. Vous avez également accès à un environnement de lab dédié Git et à un pipeline de distribution continue. Ces éléments sont personnalisés en fonction de l'environnement de déploiement choisi, [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) ou [Virtual Server (VSI)](/docs/vsi/vsi_index.html).

Toutes les chaînes d'outils créées à partir d'un tableau de bord de développeur {{site.data.keyword.cloud_notm}} sont configurées pour un déploiement automatique.
{: note}

### Déploiement manuel avec une chaîne d'outils DevOps

Avec une chaîne d'outils correctement configurée, un cycle de génération-déploiement démarre automatiquement avec chaque fusion vers la branche principale de votre référentiel. 

Vous pouvez également déployer manuellement votre application depuis votre chaîne d'outils DevOps :

1. Dans la fenêtre Détails de l'application, cliquez sur **Afficher la chaîne d'outils**.
2. Cliquez sur **Delivery pipeline**. Vous pouvez alors démarrer des générations, gérer le déploiement et afficher les journaux et l'historique.

La distribution continue est activée pour certaines applications. Vous pouvez activer la distribution continue pour automatiser les générations, les tests et les déploiements via Delivery Pipeline et GitHub.

Pour plus d'informations, voir :
* [Génération et déploiement](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy) avec Continuous Delivery.
* [Création de chaînes d'outils](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started) à partir d'un modèle.

### Déploiement automatique avec une chaîne d'outils DevOps

1. Sur la page Détails de l'application, cliquez sur **Déployer dans le cloud**.
2. Sélectionnez une méthode de déploiement. Configurez votre méthode de déploiement en fonction des instructions s'appliquant à la méthode choisie.
  * **Déployer dans [Kubernetes](/docs/apps/deploying/containers.html#containers)**. Cette option crée un cluster d'hôtes, appelé noeuds worker, afin de déployer et de gérer des conteneurs d'application à haute disponibilité. Vous pouvez créer un cluster ou effectuer un déploiement sur un cluster existant.
  * **Déployer dans Cloud Foundry**. Cette option déploie votre application cloud native sans qu'il soit nécessaire de gérer l'infrastructure sous-jacente. Si votre compte a accès à {{site.data.keyword.cfee_full_notm}}, vous pouvez sélectionnez un déployeur de type **[Public Cloud](/docs/cloud-foundry-public/about-cf.html#about-cf)** ou **[Enterprise Environment](/docs/cloud-foundry-public/cfee.html#cfee)**, que vous pouvez utiliser pour créer et gérer des environnements isolés pour l'hébergement de vos applications Cloud Foundry exclusivement pour votre entreprise.
  * **Déployer sur un [serveur virtuel](/docs/apps/vsi-deploy.html#vsi-deploy)**. Cette option met à disposition une instance de serveur virtuel qui inclut votre application, créer une chaîne d'outils DevOps et initie pour vous le premier cycle de déploiement.

Le déploiement de votre application dans le cloud lors de la dernière étape crée automatiquement une chaîne d'outils. La chaîne d'outils crée un référentiel Git pour votre application dans lequel vous pouvez trouver le code. 

### Déploiement en utilisant {{site.data.keyword.dev_cli_short}}
{: #deploy-scratch-cli}

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

## Vérification que votre application est en cours d'exécution
{: #verify-scratch}

Une fois votre application déployée, Delivery Pipeline ou la ligne de commande indique l'URL de votre application.

1. Dans votre chaîne d'outils DevOps, cliquez sur **Delivery Pipeline** puis sélectionnez **Etape de déploiement**.
2. Cliquez sur **Afficher les journaux et l'historique**.
3. Dans le fichier journal, recherchez l'URL de l'application :

    A la fin du fichier journal, recherchez le mot `urls` ou `view`. Par exemple, une ligne similaire à `urls: my-app-devhost.cloud.ibm.com` ou à `View the application health at: http://<ipaddress>:<port>/health` peut être incluse dans le fichier journal.

4. Accédez à l'URL dans votre navigateur. Si l'application est en cours d'exécution, un message qui inclut `Congratulations` ou `{"status":"UP"}` s'affiche.

Si vous utilisez la ligne de commande, exécutez la commande [`ibmcloud dev view`](/docs/cli/idt/commands.html#view) pour afficher l'URL de votre application. Accédez ensuite à l'URL dans votre navigateur.
