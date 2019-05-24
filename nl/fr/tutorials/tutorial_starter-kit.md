---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-10"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{: note .note}

# Création d'une application à l'aide d'un kit de démarrage
{: #tutorial-starterkit}

Vous pouvez utiliser un kit de démarrage pour que votre application démarre rapidement et pour la préparer à des développements futurs. Sélectionnez un kit de démarrage et un langage de programmation, créez une application, puis configurez une chaîne d'outils DevOps pour déployer automatiquement votre application. Vous pouvez également télécharger le code pour un examen immédiat.
{: shortdesc}

Vous pouvez créer une application en utilisant des kits de démarrage, notamment un kit vide si vous voulez personnaliser vous-même les options de génération. Quoi qu'il en soit, une chaîne d'outils est automatiquement créée pour le déploiement de votre application. Vous pouvez également télécharger le code pour un examen immédiat.

{{site.data.keyword.cloud_notm}} propose des portails de développeur s'appliquant à différents domaines d'intérêt (par exemple, Watson, la sécurité ou la finance) ou un canal de vente numérique (par exemple, les applications mobiles ou Web). Vous pouvez accéder à ces portails à partir de l'icône **Menu** ![Icône Menu](../../icons/icon_hamburger.svg).

Chaque portail de développeur fournit des kits de démarrage adaptés au domaine d'intérêt du portail. Les portails incluent des flux de travaux cohérents et intuitifs pour la création d'une application fonctionnelle prête pour la production en quelques minutes.

Les kits de démarrage sont disponibles dans de nombreuses catégories, telles que les suivantes :
* [Watson ](https://{DomainName}/developer/watson/dashboard){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")
* [Apple ](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")
* [Mobile ](https://{DomainName}/developer/mobile/dashboard){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")
* [Application Web ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")
* [Sécurité ](https://{DomainName}/developer/security/dashboard){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")
* [Finance ](https://{DomainName}/developer/finance/dashboard){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")

Pour plus d'informations, voir [Qu'est-ce qu'un kit de démarrage ?](/docs/apps?topic=creating-apps-starter-kits) .

## Etape 1. Installer les outils
{: #prereqs-starterkit}

* Installez les [outils de développement](/docs/cli?topic=cloud-cli-ibmcloud-cli).
* Docker est installé en tant qu'outil de développement. Pour que les commandes de génération fonctionnent, Docker doit être en cours d'exécution. Vous devez créer un compte Docker, exécuter l'application Docker et vous connecter.
* Si vous envisagez de déployer votre application dans {{site.data.keyword.cfee_full}}, vous devez [préparer votre compte {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Etape 2. Créer une application
{: #create-starterkit}

Les kits de démarrage sont disponibles dans de nombreux langages et infrastructures de la console {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}. Vous pouvez utiliser les filtres de catégorie, comme le langage ou le type, pour restreindre la sélection.

1. Sur la page des [kits de démarrage](https://{DomainName}/developer/appservice/starter-kits/){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe") de la console {{site.data.keyword.dev_console}}, sélectionnez un kit de démarrage et cliquez sur **Créer une application**. 

    Pour voir ce qui est inclus dans le kit de démarrage, sélectionnez la vignette et lisez les détails. Si vous souhaitez utiliser un kit de démarrage vide et le personnaliser, sélectionnez la vignette **Créer une application**.
    {: tip}

2. Nommez votre application et sélectionnez un groupe de ressources.

3. Facultatif. Créez des étiquettes pour classer votre application. Pour plus d'informations, voir [Utilisation d'étiquettes](/docs/resources?topic=resources-tag).

4. Sélectionnez votre langage et votre infrastructure. Certains kits de démarrage peuvent être disponibles dans un seul langage.

5. Cliquez sur **Créer**.

C'est un bon début ! Vous venez de créer une application !

Pour inspecter votre code avant d'ajouter des services ou de configurer la distribution continue, cliquez sur **Télécharger le code** sur la page Détails de l'application. Vérifiez le fichier `README.md` dans le fichier compressé téléchargé pour savoir si vous devez effectuer d'autres actions pour faire fonctionner votre application.
{: tip}

## Etape 3. Ajouter des services (facultatif)
{: #resources-starterkit}

Si un kit de démarrage nécessite des services spécifiques, des services fournis automatiquement sont disponibles pour que des instances de ces services soient automatiquement créées lorsque vous créez votre application.

Vous pouvez également ajouter des services qui améliorent votre application avec la puissance cognitive de Watson, ajoutent des services mobiles ou des services de sécurité. Pour ce tutoriel, ajoutez un emplacement pour gérer vos données.

1. Sur la page Détails de l'application, cliquez sur **Créer un service**, ou sur **Connecter les services existants** si vous avez déjà des services que vous souhaitez connecter à cette application.
2. Sélectionnez le type de service que vous souhaitez et suivez les invites pour ajouter un service existant à votre application ou pour créer une instance de service.

Une fois que tous les services souhaités ont été ajoutés, ils s'affichent sur la page Détails de l'application.

## Etape 4. Sélectionner une cible de déploiement et configurer la distribution continue
{: #target-starterkit}

Lorsque vous sélectionnez une cible de déploiement, une chaîne d'outils DevOps est automatiquement créée pour votre application. La chaîne d'outils inclut un pipeline de distribution qui indique le statut de déploiement de votre application. La nouvelle application qui est générée est envoyée à un référentiel GitLab qui fait partie de la chaîne d'outils.

L'activation d'une chaîne d'outils DevOps crée un environnement de développement basé sur une équipe pour votre application. Lorsque vous créez une chaîne d'outils, le service d'application crée un référentiel Git dans lequel vous pouvez afficher le code source, cloner votre application, créer et gérer des problèmes. Vous avez également accès à un environnement GitLab dédié et à un pipeline de distribution continue. Ces éléments sont personnalisés en fonction de la cible de déploiement choisie, [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) ou [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Toutes les chaînes d'outils créées à partir d'un tableau de bord de développeur {{site.data.keyword.cloud_notm}} sont configurées pour un déploiement automatique.
{: note}

Pour sélectionner votre cible de déploiement et configurer la distribution continue, procédez comme suit :

1. Sur la page Détails de l'application, cliquez sur **Configurer la distribution continue**.
2. Sélectionnez une cible de déploiement. Configurez votre cible de déploiement en fonction des instructions s'appliquant à la cible que vous sélectionnez :
  * **Déployer dans [IBM Kubernetes Service](/docs/containers?topic=containers-app)**. Cette option crée un cluster d'hôtes, appelé noeuds worker, afin de déployer et de gérer des conteneurs d'application à haute disponibilité. Vous pouvez créer un cluster ou effectuer un déploiement sur un cluster existant.
  * **Déployer dans Cloud Foundry**. Cette option déploie votre application cloud native sans qu'il soit nécessaire de gérer l'infrastructure sous-jacente. Si votre compte a accès à {{site.data.keyword.cfee_full_notm}}, vous pouvez sélectionner un déployeur de type **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** ou **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**, que vous pouvez utiliser pour créer et gérer des environnements isolés pour l'hébergement de vos applications Cloud Foundry exclusivement pour votre entreprise.
  * **Déployer sur un serveur virtuel**. Cette option met à disposition une instance de serveur virtuel, charge une image qui inclut votre application, crée une chaîne d'outils DevOps et initie pour vous le premier cycle de déploiement.

Après avoir sélectionné et configuré la cible de déploiement, la page Détails de l'application indique que la distribution continue est configurée. Vous pouvez afficher le référentiel qui contient le code source de votre application en cliquant sur **Afficher le référentiel**.

## Etape 5. Déployer votre application
{: #deploy-starterkit}

Les chaînes d'outils DevOps qui sont créées dans le tableau de bord de développement d'{{site.data.keyword.cloud_notm}} sont configurées pour le déploiement automatique.
{: note}

Une fois que vous avez sélectionné votre cible de déploiement, ouvrez le composant Pipeline de votre nouvelle chaîne d'outils pour démarrer le processus de génération et de déploiement initial afin que vous puissiez voir votre application après quelques minutes.

1. Sur la page Détails de l'application, cliquez sur **Afficher la chaîne d'outils**.
2. Cliquez sur **Delivery Pipeline**. Vous pouvez alors démarrer des générations, gérer le déploiement et afficher les journaux et l'historique.

Avec une chaîne d'outils correctement configurée, un cycle de génération-déploiement démarre automatiquement lors de chaque fusion vers la branche principale de votre référentiel. Pour plus d'informations, voir [Génération et déploiement](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

Vous pouvez déployer votre application à partir de la ligne de commande en exécutant la commande [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy). Pour plus d'informations, voir [Déploiement d'applications avec l'interface CLI](/docs/apps?topic=creating-apps-deploying-apps#deploy-cli).

## Etape 6. Vérifier que votre application s'exécute
{: #verify-starterkit}

Une fois votre application déployée, Delivery Pipeline ou la ligne de commande indique l'URL de votre application.

1. Dans votre chaîne d'outils DevOps, cliquez sur **Delivery Pipeline** puis sélectionnez **Etape de déploiement**.
2. Cliquez sur **Afficher les journaux et l'historique**.
3. Dans le fichier journal, recherchez l'URL de l'application :

    A la fin du fichier journal, recherchez le mot `urls` ou `view`. Par exemple, une ligne similaire à `urls: my-app-devhost.mybluemix.net` ou à `View the application health at: http://<ipaddress>:<port>/health` peut être incluse dans le fichier journal.

4. Accédez à l'URL dans votre navigateur. Si l'application est en cours d'exécution, un message qui inclut `Congratulations` ou `{"status":"UP"}` s'affiche.

Si vous utilisez la ligne de commande, exécutez la commande [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) pour afficher l'URL de votre application. Accédez ensuite à l'URL dans votre navigateur.
