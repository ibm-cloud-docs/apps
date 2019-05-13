---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-30"

keywords: scratch, developer tools, custom app, app tutorial, verify app running, run app local

subcollection: creating-apps

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

* Installez [{{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli), qui inclut Docker. 
* Créez un compte Docker, exécutez l'application Docker puis connectez-vous. Pour que les commandes de génération fonctionnent, Docker doit être en cours d'exécution.
* Si vous envisagez de déployer votre application dans {{site.data.keyword.cfee_full}}, vous devez [préparer votre compte {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Création de votre application
{: #create-scratch}

1. Depuis votre [tableau de bord{{site.data.keyword.cloud_notm}} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}), cliquez sur **Créer une application** dans le widget Applications.

  Vous pouvez également créer une application personnalisée à partir de la page [Kits de démarrage ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/developer/appservice/starter-kits/) dans {{site.data.keyword.dev_console}}.
  {: tip}

2. Entrez un nom pour votre application. Pour ce tutoriel, entrez `CustomProject`.
3. Vous pouvez éventuellement créer des étiquettes pour classer votre application. Pour plus d'informations, voir [Utilisation d'étiquettes](/docs/resources?topic=resources-tag).
4. Sélectionnez votre langage et votre infrastructure. Certains kits de démarrage peuvent être disponibles dans un seul langage.
5. Sélectionnez votre plan de tarification. Vous pouvez utiliser l'option gratuite pour ce tutoriel.
6. Cliquez sur **Créer**.

## Ajout de services (facultatif)
{: #resources-scratch}

Vous pouvez ajouter des services qui améliorent votre application avec la puissance cognitive de Watson, ajoutent des services mobiles ou des services de sécurité. Pour ce tutoriel, vous pouvez ajouter un emplacement pour gérer vos données.

1. Sur la page **Détails de l'application**, cliquez sur **Ajouter un service**.
2. Sélectionnez le type de service souhaité. Par exemple, sélectionnez **Données** > **Suivant** > **Cloudant** > **Suivant**.
3. Sélectionnez votre plan de tarification. Vous pouvez utiliser l'option gratuite pour ce tutoriel.
4. Cliquez sur **Créer**.

## Génération et exécution de l'application localement
{: #build-run-scratch}

Vous pouvez également générer l'application localement à des fins de test avant de pouvoir la déployer dans le cloud.

1. Sur la page **Détails de l'application**, cliquez sur **Télécharger le code** ou **Cloner votre référentiel** pour utiliser votre code localement.
2. Importez l'application dans votre environnement de développement intégré.
3. Modifiez le code.
4. Configurez l'[authentification Git](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) en ajoutant un jeton d'accès personnel.
5. Connectez-vous à l'interface de ligne de commande {{site.data.keyword.cloud_notm}}. Si votre entreprise utilise des connexions fédérées, utilisez l'option `-sso`, par exemple :

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

Cliquez sur **Configurer la distribution continue** sur la page **Détails de l'application**, sélectionnez une cible de déploiement et cliquez sur **Créer**. {{site.data.keyword.cloud_notm}} crée automatiquement une chaîne d'outils ouverte complétée par un référentiel Git et un pipeline de distribution continue.

L'activation d'une chaîne d'outils permet de créer un environnement de développement basé sur une équipe pour votre application. Lorsque vous créez une chaîne d'outils, le service d'application crée un référentiel Git dans lequel vous pouvez afficher le code source, cloner votre application, créer et gérer des problèmes. Vous avez également accès à un environnement de lab dédié Git et à un pipeline de distribution continue. Ces éléments sont personnalisés en fonction de la cible de déploiement choisie, [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) ou [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers).

Une fois que vous avez sélectionné votre cible de déploiement, ouvrez le composant Pipeline de votre nouvelle chaîne d'outils pour démarrer le processus de génération et de déploiement initial afin que vous puissiez voir votre application après quelques minutes.

Toutes les chaînes d'outils créées à partir d'un tableau de bord de développeur {{site.data.keyword.cloud_notm}} sont configurées pour un déploiement automatique.
{: note}

Pour déployer votre application avec la ligne de commande, utilisez `ibmcloud dev deploy`. Pour plus d'informations, voir [Création et déploiement d'applications à l'aide de l'interface de ligne de commande](/docs/apps?topic=creating-apps-create-deploy-app-cli).

Pour plus d'informations sur le déploiement de votre application, voir [Déploiement d'applications](/docs/apps?topic=creating-apps-deploying-apps).

## Vérification que votre application est en cours d'exécution
{: #verify-scratch}

Une fois votre application déployée, Delivery Pipeline ou la ligne de commande indique l'URL de votre application.

1. Dans votre chaîne d'outils DevOps, cliquez sur **Delivery Pipeline** puis sélectionnez **Etape de déploiement**.
2. Cliquez sur **Afficher les journaux et l'historique**.
3. Dans le fichier journal, recherchez l'URL de l'application :

   A la fin du fichier journal, recherchez le mot `urls` ou `view`. Par exemple, une ligne similaire à `urls: my-app-devhost.mybluemix.net` ou à `View the application health at: http://<ipaddress>:<port>/health` peut être incluse dans le fichier journal.

4. Accédez à l'URL dans votre navigateur. Si l'application est en cours d'exécution, un message qui inclut `Congratulations` ou `{"status":"UP"}` s'affiche.

Si vous utilisez la ligne de commande, exécutez la commande [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) pour afficher l'URL de votre application. Accédez ensuite à l'URL dans votre navigateur.

