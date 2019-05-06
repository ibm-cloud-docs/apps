---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-23"

keywords: cloud development, develop apps, build apps, continuous delivery, toolchain, development stages, development phases

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Phases recommandées pour le développement de cloud
{: #development_process}

Les développeurs d'application en cloud passent par quatre phases fondamentales lors du processus de développement : mise en route, codage, distribution et gestion. L'objectif est de produire rapidement une application fonctionnelle, puis d'utiliser les commentaires en retour de l'application de production pour itérer en continu le code ou le cycle de distribution jusqu'à ce que votre application trouve un écho auprès des utilisateurs.
{: shortdesc}

![Flux de développement](images/dev_flow_overview.png "Flux de développement") Figure 1. Phases du processus de développement

Dans certains cas, la phase d'exécution (`run`) est distincte, mais ici, nous l'avons combinée avec les phases de distribution et de gestion.

Examinons de plus près le meilleur moyen d'utiliser {{site.data.keyword.cloud}} dans votre flux de développement.

## Mise en route
{: #get_started}

Générez votre application à partir des tableaux de bord {{site.data.keyword.cloud_notm}} Developer dans lesquels vous pouvez sélectionner un kit de démarrage lié à votre scénario d'utilisation et choisir un langage de programmation. {{site.data.keyword.cloud_notm}} utilise les instructions du kit de démarrage pour créer automatiquement les ressources dont vous avez besoin et pour créer une application indépendante de l'environnement d'exécution et propre au langage qui constitue la base de votre application de production. Pour exécuter la phase de mise en route, cliquez sur **Configurer la distribution continue** à partir de **Détails de l'application**. Un clic permet de créer une chaîne d'outils DevOps complète avec un référentiel de code alimenté avec votre code source d'application et votre pipeline de déploiement.

![Mise en route](images/dev_get_started.png "Mise en route") Figure 2. Flux de mise en route

Lorsque vous utilisez le bouton **Configurer la distribution continue** pour configurer votre chaîne d'outils DevOps, sélectionnez votre plateforme d'exécution, par exemple, Kubernetes ou Cloud Foundry. L'application de kit de démarrage générée à partir d'{{site.data.keyword.cloud_notm}} est indépendante de l'environnement d'exécution et n'a pas besoin d'être modifiée.
{: tip}

## Développement en local
{: #develop_locally}

Après avoir créé votre application de kit de démarrage et votre chaîne d'outils, vous commencez votre développement en local. Clonez le code à partir de votre référentiel sur un poste de travail local et importez-le dans votre interface IDE. Utilisez le plug-in {{site.data.keyword.dev_cli_long}} pour générer, exécuter et tester votre application en cloud sur votre machine locale. {{site.data.keyword.dev_cli_notm}} crée et gère des conteneurs locaux pour vous. Lorsque vous êtes prêt à voir que votre application s'exécute sur le cloud, envoyez le contenu à votre référentiel cloud et fusionnez vos modifications.

![Développement en local](images/dev_code_locally.png "Développement en local") Figure 3. Flux de développement en local

Les fonctions de base pour {{site.data.keyword.dev_cli_notm}} sont `ibmcloud dev build` et `ibmcloud dev run`, mais l'interface de ligne de commande offre bien d'autres fonctions. Pour plus d'informations, voir [{{site.data.keyword.dev_cli_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).
{: tip}

## Distribution et gestion dans {{site.data.keyword.cloud_notm}}
{: #deliver_and_manage}

La fusion des modifications apportées à votre référentiel cloud entraîne le démarrage d'un cycle de génération et de déploiement dans la chaîne d'outils DevOps que vous avez créée précédemment. Votre application s'exécute dans le cloud au bout de quelques minutes.

Pour vérifier le statut de votre pipeline DevOps, utilisez votre tableau de bord de pipeline de distribution. Pour vérifier le statut général de votre application, consultez le tableau de bord {{site.data.keyword.cloud_notm}} pour votre compte.
{: tip}

La chaîne d'outils produite par votre démarche de mise en route comporte les composants de base dont vous avez besoin pour une distribution continue collaborative qui repose sur une équipe. Cependant, {{site.data.keyword.cloud_notm}} offre un ensemble étendu de services DevOps que vous pouvez ajouter à votre chaîne d'outils afin d'améliorer la distribution, la surveillance, la journalisation et les alertes.

![Distribution et gestion](images/dev_deliver_and_manage.png "Distribution et gestion") Figure 4. Flux de distribution et de gestion

En savoir plus sur le [développement continu sur {{site.data.keyword.cloud_notm}}](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-getting-started).

## Vue d'ensemble de toutes les phases

![Détails du processus](images/dev_process_detail.png "Détails du processus") Figure 5. Processus de développement de bout en bout
