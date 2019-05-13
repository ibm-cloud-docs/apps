---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-30"

keywords: getting started apps, create app tutorial, add services, deploy apps, create app, app tutorial

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Tutoriel d'initiation
{: #tutorial-getting-started}

Vous pouvez générer des applications mobiles et Web adaptées aux entreprises dans {{site.data.keyword.cloud}} et tirer parti des extensions cloud hébergées par {{site.data.keyword.cloud_notm}}. Vous pouvez commencer de différentes manières. Vous pouvez créer une application avec un kit de démarrage qui gère le processus pour vous, ou, si vous savez précisément ce que vous voulez, générer vous-même votre application avec les ressources dont vous avez besoin ou utiliser votre référentiel existant ainsi que votre propre code.
{: shortdesc}

Que vous disposiez d'un [code existant](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc) que vous souhaitez moderniser et placer sur le cloud ou que vous développiez une [toute nouvelle application](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit), vous pouvez bénéficier de l'écosystème à croissance rapide des services disponibles et des infrastructures d'exécution d'{{site.data.keyword.cloud_notm}}.

Avez-vous besoin d'aide pour déterminer où commencer ? Pour avoir des idées, consultez ce diagramme !

![Présentation de Developer Experience](images/dev-journey.png "Présentation de Developer Experience")

## Avant de commencer
{: #prereqs-getting-started}

Vous pouvez créer votre application en utilisant la console {{site.data.keyword.cloud_notm}} ou l'interface de ligne de commande. Si vous voulez utiliser cette dernière, voir les [étapes d'installation](/docs/cli?topic=cloud-cli-ibmcloud-cli).

## Etape 1. Créer votre application
{: #create-getting-started}

Créez une application en sélectionnant un des points d'entrée suivants :

* Les [kits de démarrage](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit) sont propres aux cas d'utilisation et génèrent des applications prêtes pour la production dans différents langages de programmation et modèles d'architecture.
* Les [modèles de code IBM Developer![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/patterns/){:new_window} permettent de créer rapidement votre application et de la déployer dans {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir [Modèles de code](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern).
* [Utilisez votre propre code](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc) en le liant à votre propre référentiel de contenu. Votre application et votre image Docker doivent se trouver dans le même référentiel.
* Si vous savez ce que vous voulez, générez une [application personnalisée](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch) avec les ressources dont vous avez besoin en utilisant un kit de démarrage vide.
* Créez et déployez une application personnalisée ou de kit de démarrage en utilisant l'[interface CLI et les outils de développement](/docs/apps?topic=creating-apps-create-deploy-app-cli).
* Parcourez le catalogue [{{site.data.keyword.cloud_notm}}](https://{DomainName}/catalog){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") afin d'y trouver les applications et les services que vous pouvez créer et commencer à utiliser dès aujourd'hui.

## Etape 2. Ajout de services
{: #resources-getting-started}

Lorsque vous utilisez un kit de démarrage pour créer votre application, les services obligatoires sont automatiquement créés pour vous. Vous pouvez connecter d'autres services à votre application dans la console à partir de la page **Détails de l'application**, qui s'affiche dès que vous créez l'application.

Si vous souhaitez ajouter des services une fois l'application créée, accédez au tableau de bord [{{site.data.keyword.cloud_notm}}![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}), localisez votre application, puis cliquez sur le nom de votre application. La page **Détails de l'application** s'affiche, et vous pouvez créer une instance de service ou connecter des services existants.

Vous pouvez aussi exécuter la commande suivante pour ajouter un service à votre application en utilisant l'interface de ligne de commande. Vous pouvez sélectionner un service existant parmi ceux déjà activés sur votre compte ou ajouter un service.
```
ibmcloud dev edit
```
{: codeblock}

Pour plus d'informations, voir [Ajout d'un service à votre application](/docs/apps?topic=creating-apps-add-resource).

## Etape 3. Déployer votre application
{: #deploy-getting-started}

Vous pouvez déployer votre application en utilisant la console ou l'interface de ligne de commande.

### Utilisation de la console
{: #console-getting-started}

Pour déployer votre application en utilisant la console, procédez comme suit :

1. Sur la page **Détails de l'application**, cliquez sur **Configurer la distribution continue**.
2. Sélectionnez une cible de déploiement, sélectionnez les paramètres de chaîne d'outils et cliquez sur **Créer**. {{site.data.keyword.cloud_notm}} crée automatiquement une chaîne d'outils ouverte complétée par un référentiel Git et un pipeline de distribution continue.
3. Ouvrez l'étape de pipeline de votre nouvelle chaîne d'outils pour afficher le processus de génération et de déploiement de sorte que vous puissiez voir votre nouvelle application après quelques minutes.

Pour plus d'informations, consultez la table des matières présentant les différentes rubriques de déploiement dans la section "Déploiement et intégration d'applications".

### Utilisation de l'interface de ligne de commande (CLI)
{: #cli-getting-started}

Pour déployer votre application en utilisant l'interface de ligne de commande, exécutez la commande `ibmcloud dev deploy`. Pour plus d'informations, voir [Création et déploiement d'applications à l'aide de l'interface de ligne de commande](/docs/apps?topic=creating-apps-create-deploy-app-cli).

Vous êtes maintenant prêt pour des tâches de développement itératif et de distribution continue.

Pour plus d'informations sur le déploiement de votre application, voir [Déploiement d'applications](/docs/apps?topic=creating-apps-deploying-apps).

## Informations connexes
{: #related-getting-started}

Des [guides de programmation](https://{DomainName}/docs/home/build){: new_window} ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe") sont disponibles pour chaque langage. Grâce à eux, vous pouvez commencer à effectuer les tâches souhaitées. Avec l'infrastructure {{site.data.keyword.cloud_notm}}, vous disposez de plusieurs options pour l'hébergement de vos applications, qu'il s'agisse de serveurs de type {{site.data.keyword.baremetal_short}} ou d'exécution en tant que fonction sans serveur.
