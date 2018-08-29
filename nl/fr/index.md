---

copyright:
  years: 2017, 2018
lastupdated: "2018-08-21"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Tutoriel d'initiation
{: #create}

Dans {{site.data.keyword.Bluemix}}, vous pouvez générer des applications mobiles et Web au niveau de l'entreprise, et tirer parti des extensions cloud hébergées par {{site.data.keyword.Bluemix_notm}}. Vous pouvez utiliser les outils de ligne de commande et la console {{site.data.keyword.Bluemix}} pour générer, exécuter et déployer vos applications. Démarrez de deux façons : en créant une application avec un kit de démarrage qui gère le processus pour vous, ou, si vous savez précisément ce que vous voulez, en générant votre application avec les ressources dont vous avez besoin.
{:shortdesc}

Vous pouvez utiliser un kit de démarrage pour que votre application démarre rapidement et pour la préparer à des développements futurs. Choisissez un kit de démarrage et un langage de programmation, créez une application, puis configurez une chaîne d'outils DevOps pour déployer automatiquement votre application. Vous pouvez également télécharger le code pour un examen immédiat.

Les kits de démarrage sont disponibles dans de nombreuses catégories, telles que les suivantes :

* [Watson ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/developer/watson/dashboard){:new_window}
* [Apple ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/developer/appledevelopment/dashboard){:new_window}
* [Mobile ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/developer/mobile/dashboard){:new_window}
* [Application Web ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/developer/appservice/dashboard){:new_window}
* [Sécurité ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/developer/security/dashboard){:new_window}
<!--* [Watson Data Platform developer console](https://console.bluemix.net/developer/dataplatform)-->
* [Finance ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/developer/finance/dashboard){:new_window}

## Avant de commencer

[Inscrivez-vous ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net){: new_window} pour obtenir un compte {{site.data.keyword.cloud_notm}}. Indiquez votre adresse électronique, votre nom, le nom de votre société, votre région et votre numéro de téléphone.

Vous n'avez pas besoin de carte de crédit pour obtenir un compte gratuit. Cependant, si vous entrez un numéro de carte de crédit, vous pourrez accéder à davantage de ressources et pourrez plus facilement vous procurer toutes les offres {{site.data.keyword.cloud_notm}}.

## Etape 1. Créer une application
{: #project}

1. Cliquez sur l'icône **Menu** ![Icône Menu](../icons/icon_hamburger.svg) > **Applications Web**.

2. Cliquez sur **Initiation** dans la section **Démarrer à partir du Web**.

3. Sélectionnez un kit de démarrage de votre choix, lisez les détails, puis cliquez sur **Créer**.

   Pour voir ce qui est inclus dans le kit de démarrage, développez la vignette sur le tableau de bord des kits de démarrage de service d'application.
   {: tip}

4. Donnez un nom à votre application, sélectionnez votre langage, puis cliquez sur **Créer**.

   C'est un bon début ! Vous venez de créer une application.

   Pour examiner votre code, cliquez sur **Télécharger le code** sur la page des détails d'application. Consultez le fichier `README.md` se trouvant dans le fichier compressé téléchargé pour savoir si vous devez exécuter d'autres actions pour rendre votre application de démarrage opérationnelle.
   {: tip}

## Etape 2. Ajouter des ressources
{: #addResources}

La majeure partie des kits de démarrage demande à {{site.data.keyword.cloud_notm}} de mettre automatiquement des ressources à votre disposition. Vous pouvez également associer davantage de ressources à votre application en cliquant sur **Ajouter une ressource** sur la page des détails d'application.

Pour développer et exécuter votre application localement utilisez le [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html)
{: tip}

## Etape 3. Déployer votre application
{: #deploy}

Cliquez sur **Déployer dans Cloud** sur la page des détails d'application, sélectionnez une méthode de déploiement, par exemple, Cluster Kubernetes ou Application Cloud Foundry, puis cliquez sur **Créer**. {{site.data.keyword.cloud_notm}} crée automatiquement une chaîne d'outils ouverte complétée par un référentiel Git et un pipeline de distribution continue. Ouvrez le composant pipeline de votre nouvelle chaîne d'outils afin de commencer le processus de génération et de déploiement initial de sorte que vous puissiez voir votre application après quelques minutes.

Vous êtes maintenant prêt pour des tâches de développement itératif et de distribution continue.
