---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-18"

keywords: apps, deploy, deploying apps, toolchain, cli, cloud, devops, deployment, git, push

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Déploiement d'applications
{: #deploying-apps}

Vous pouvez déployer votre application dans {{site.data.keyword.cloud}} en utilisant une chaîne d'outils DevOps. Avec une telle chaîne, vous pouvez automatiser les déploiements dans un grand nombre d'environnements et ajouter rapidement des services de surveillance, de journalisation, d'analyse et d'alerte afin de gérer plus facilement votre application à mesure de sa croissance. Vous pouvez configurer la distribution continue et déployer votre application en utilisant l'interface de ligne de commande ou la console Web {{site.data.keyword.cloud_notm}}.
{: shortdesc}

Une chaîne d'outils DevOps inclut un environnement de développement basé sur une équipe pour votre application. Lorsque vous créez une chaîne d'outils, le service d'application crée un référentiel Git dans lequel vous pouvez afficher le code source, cloner votre application, créer et gérer des problèmes. Vous avez également accès à un environnement GitLab dédié et à un pipeline de distribution continue. Ces éléments sont personnalisés en fonction de la cible de déploiement choisie, [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) ou [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

## Utilisation de la console {{site.data.keyword.cloud_notm}}
{: deploy-console}

{{site.data.keyword.cloud_notm}} inclut une console Web dans laquelle vous pouvez configurer la distribution continue et déployer votre application en utilisant une chaîne d'outils DevOps.

### Avant de commencer
{: deploy-console-before}

Avant de commencer, utilisez le [tableau de bord {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") pour [créer votre application](/docs/apps?topic=creating-apps-getting-started) et [ajouter des services](/docs/apps?topic=creating-apps-getting-started#resources-getting-started).

### Déploiement automatique de votre application
{: deploy-console-auto}

Toutes les chaînes d'outils créées à partir du tableau de bord de développeur {{site.data.keyword.cloud_notm}} sont configurées pour un déploiement automatique.
{: note}

1. Sur la page **Détails de l'application**, cliquez sur **Configurer la distribution continue**.
2. Sélectionnez une cible de déploiement. Configurez votre cible de déploiement en fonction des instructions s'appliquant à la cible que vous sélectionnez :
  * **Déployer dans IBM Kubernetes Service**. Cette option crée un cluster d'hôtes, appelé noeuds worker, afin de déployer et de gérer des conteneurs d'application haute disponibilité. Vous pouvez créer un cluster ou effectuer un déploiement sur un cluster existant. Pour plus d'informations, voir [Déploiement d'applications dans des clusters Kubernetes](/docs/containers?topic=containers-app).
  * **Déployer dans Cloud Foundry**. Cette option déploie votre application cloud native sans qu'il soit nécessaire de gérer l'infrastructure sous-jacente. Si votre compte a accès à {{site.data.keyword.cfee_full_notm}}, vous pouvez sélectionner un déployeur de type **Public Cloud** ou **Enterprise Environment**, que vous pouvez utiliser pour créer et gérer des environnements isolés pour l'hébergement de vos applications Cloud Foundry exclusivement pour votre entreprise. Pour plus d'informations, voir [Déploiement d'applications dans Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps) et [Déploiement d'applications dans {{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps).
  * **Déployer sur un serveur virtuel**. Cette option met à disposition une instance de serveur virtuel, charge une image qui inclut votre application, crée une chaîne d'outils DevOps et initie pour vous le premier cycle de déploiement. Pour plus d'informations, voir [Déploiement d'applications dans un serveur virtuel](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server).

    Le déploiement de VSI est disponible pour certains kits de démarrage. Pour utiliser cette fonctionnalité, accédez au [tableau de bord {{site.data.keyword.cloud_notm}}](https://{DomainName}) et cliquez sur **Créer une application** dans la vignette **Applications**.
    {: note}

### Déploiement manuel de votre application
{: deploy-console-manual}

Avec une chaîne d'outils correctement configurée, un cycle de génération-déploiement démarre automatiquement lors de chaque fusion vers la branche principale de votre référentiel. 

Vous pouvez également déployer manuellement votre application depuis votre chaîne d'outils DevOps :

1. Sur la page **Détails de l'application**, cliquez sur **Afficher la chaîne d'outils**.
2. Cliquez sur **Delivery Pipeline**. Vous pouvez alors démarrer des générations, gérer le déploiement et afficher les journaux et l'historique.

La distribution continue est automatiquement activée pour certaines applications. Vous pouvez activer la distribution continue pour automatiser les générations, les tests et les déploiements via Delivery Pipeline et GitHub.

Pour plus d'informations, voir :
* [Génération et déploiement](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)
* [Création de chaînes d'outils](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)

## Utilisation de l'interface de ligne de commande {{site.data.keyword.dev_cli_short}}
{: #deploy-cli}

{{site.data.keyword.cloud_notm}} inclut une interface de ligne de commande robuste ainsi que des plug-in permettant de simplifier le flux de travaux du développeur. Vous pouvez déployer votre application {{site.data.keyword.cloud_notm}} en utilisant une des méthodes ci-dessous, en fonction de la manière dont votre application est configurée.

### Avant de commencer
{: #deploy-cli-before}

Avant de commencer, [ téléchargez et installez l'interface de ligne de commande {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-getting-started).

L'interface de ligne de commande n'est pas prise en charge par Cygwin. Utilisez l'outil dans une fenêtre autre que la fenêtre de ligne de commande Cygwin.
{: important}

  1. Téléchargez le code de votre application dans un nouveau répertoire afin de configurer votre environnement de développement.

  2. Placez-vous dans le répertoire dans lequel se trouve votre code.

  3.  Mettez à jour votre code d'application. Si vous utilisez une application exemple {{site.data.keyword.cloud_notm}} et qu'elle contient le fichier `src/main/webapp/index.html`, vous pouvez le modifier et éditer la ligne `"Thanks for creating ..."`. Vérifiez que l'application s'exécute localement avant de la déployer dans {{site.data.keyword.cloud_notm}}.

    Consultez le fichier `README.md`, qui contient des informations, telles que les instructions de génération.

    Si votre application est une application Liberty, vous devez la générer avant de la redéployer.
    {: note}

  4. Connectez-vous à l'interface de ligne de commande {{site.data.keyword.cloud_notm}} à l'aide de votre IBMid. Si vous avez plusieurs comptes, vous êtes invité à sélectionner le compte à utiliser. Si vous n'indiquez pas de région avec l'option `-r`, vous devez également sélectionner une région.
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    Si vos données d'identification sont rejetées, vous pouvez utiliser un ID fédéré. Pour vous connecter avec un ID fédéré, utilisez l'option `--sso`. Pour plus d'informations, voir [Connexion à l'aide d'un ID fédéré](/docs/iam/federated_id?topic=iam-federated_id#federated_id).
    {: tip}

### Déploiement automatique de votre application
{: #deploy-cli-auto}

Si vous n'avez pas créé de chaîne d'outils DevOps pour votre application et que cette dernière n'est pas encore dans un référentiel Git, vous pouvez exécuter la commande [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit). Suivez les invites pour configurer DevOps et pour effectuer le déploiement dans une nouvelle chaîne d'outils (et pour créer un nouveau référentiel GitLab).

Une fois que vous avez créé une chaîne d'outils DevOps pour votre application, déployer une nouvelle version revient tout simplement à valider et envoyer votre code vers le référentiel dans votre chaîne d'outils. 

1. Préparez les modifications à valider.
    ```
    git add .
    ```
2. Validez les modifications avec un bref message.
    ```
    git commit -m "made changes"
    ```
3. Transférez les validations de la branche principale vers le référentiel distant.
    ```
    git push origin master
    ```
4. Affichez la chaîne d'outils DevOps pour votre application à partir de la console {{site.data.keyword.cloud_notm}}. Vous pouvez afficher les détails de la chaîne d'outils à partir de l'écran **Détails de l'application** de la console {{site.data.keyword.cloud_notm}} en exécutant la commande [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) à partir du répertoire de l'application.
5. Affichez le pipeline au sein de la chaîne d'outils pour vérifier qu'une nouvelle version a démarré.

### Déploiement manuel de votre application
{: #deploy-cli-manual}

Vous pouvez déployer manuellement votre application dans {{site.data.keyword.cloud_notm}} en utilisant la commande [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).

  ```
  ibmcloud dev deploy
  ```
  {: codeblock}

### Informations connexes
{: #deploy-cli-related}

Pour plus d'informations sur le déploiement de votre application dans {{site.data.keyword.cloud_notm}} en utilisant l'interface de ligne de commande, voir :

* [Deploying to {{site.data.keyword.cloud_notm}} environments with {{site.data.keyword.dev_cli_short}} CLI](https://www.ibm.com/cloud/blog/deploying-to-ibm-cloud-environments-with-ibm-cloud-developer-tools-cli){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")
