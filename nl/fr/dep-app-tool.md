---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-02"

keywords: apps, deploy, deploying apps, toolchains, cli, cloud

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

Vous pouvez déployer vos applications avec une chaîne d'outils DevOps ou l'interface de ligne de commande (CLI). Une chaîne d'outils DevOps est un ensemble d'intégrations d'outils. L'interface de ligne de commande constitue un moyen simple de déployer vos applications et vos instances de service.
{: shortdesc}

## Déploiement d'applications en utilisant des chaînes d'outils DevOps
{: #toolchain-deploy-apps}

Des chaînes d'outils ouvertes sont disponibles dans les environnements {{site.data.keyword.Bluemix}} Public et Dédié. Avec une chaîne d'outils correctement configurée, le déploiement de votre application devient un jeu d'enfants. Un cycle de génération-déploiement démarre automatiquement avec chaque fusion vers la branche principale de votre référentiel.

Vous pouvez créer une chaîne d'outils d'une des manières suivantes :
* En créant une chaîne d'outils à partir d'une application. Pour plus d'informations, voir [Déploiement de votre application](/docs/apps?topic=creating-apps-tutorial-scratch#deploy-scratch).
* En utilisant un modèle pour créer une chaîne d'outils. Pour plus d'informations, voir [Création de chaînes d'outils](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## Déploiement d'applications en utilisant l'interface de ligne de commande
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}} fournit une interface de ligne de commande robuste, ainsi que des plug-in et des extensions d'outil de développement qui s'intègrent à l'interface de ligne de commande.

Avant de commencer, [ téléchargez et installez l'interface de ligne de commande {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).

L'interface de ligne de commande n'est pas prise en charge par Cygwin. Utilisez l'outil dans une fenêtre autre que la fenêtre de ligne de commande Cygwin.
{: important}

  1. Téléchargez le code de votre application dans un nouveau répertoire afin de configurer votre environnement de développement.

  2. Placez-vous dans le répertoire dans lequel se trouve votre code.

  3.  Mettez à jour votre code d'application. Si vous utilisez une application exemple {{site.data.keyword.cloud_notm}} et qu'elle contient le fichier `src/main/webapp/index.html`, vous pouvez le modifier et éditer la ligne `"Thanks for creating ..."`. Vérifiez que l'application s'exécute localement avant de la déployer dans {{site.data.keyword.cloud_notm}}.

    Tenez compte du fichier `manifest.yml`. Lorsque vous déployez votre application dans {{site.data.keyword.cloud_notm}}, il est utilisé pour déterminer l'adresse URL de votre application, l'allocation de mémoire, le nombre d'instances et d'autres paramètres essentiels.

    Consultez également le fichier `README.md`, qui contient des informations, telles que les instructions de génération.

    Si votre application est une application Liberty, vous devez la générer avant de la redéployer.
    {: note}

  4. Connectez-vous à l'interface de ligne de commande {{site.data.keyword.cloud_notm}} à l'aide de votre IBMid. Si vous avez plusieurs comptes, vous êtes invité à sélectionner le compte à utiliser. Si vous n'indiquez pas de région avec l'option `-r`, vous devez également choisir une région.
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    Si vos données d'identification sont rejetées, vous pouvez utiliser un ID fédéré. Pour vous connecter avec un ID fédéré, utilisez l'option `--sso`. Pour plus d'informations, voir [Connexion à l'aide d'un ID fédéré](/docs/iam/federated_id?topic=iam-federated_id#federated_id).
    {: tip}

  5. A partir du nouveau répertoire, déployez votre application dans {{site.data.keyword.cloud_notm}} en utilisant la commande [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).
    ```
    ibmcloud dev deploy <APP_NAME>
    ```
    {: codeblock}

  6. Accédez à votre application en exécutant la commande [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) pour afficher l'URL de votre application. Accédez ensuite à l'URL dans votre navigateur.
