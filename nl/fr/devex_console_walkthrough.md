---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-11-29"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Parcours guidé dans la console {{site.data.keyword.cloud_notm}} Developer Console
{: #intro}

<!--I can't see how a customer needs to be walked through the experience without performing a specific task.-->


{{site.data.keyword.cloud}} Developer Experience permet aux développeurs d'applications en cloud natives de créer une application à partir de plusieurs kits de démarrage, de créer et de connecter des services optimisés par {{site.data.keyword.Bluemix_notm}} puis de télécharger rapidement un code fonctionnel ou d'effectuer la configuration pour la distribution continue. Developer Experience inclut un ensemble de consoles de développeur dans {{site.data.keyword.Bluemix_notm}} qui permettent de créer, d'afficher, de configurer et de gérer votre application ainsi que de la déployer dans un pipeline devops ou de la télécharger pour le développement local.

Lorsque vous créez une application en utilisant une console {{site.data.keyword.cloud_notm}} Developer Console, tous les composants requis de votre application sont gérés dans votre compte sur le serveur {{site.data.keyword.cloud_notm}}. Ainsi, vous pouvez si vous le souhaitez passer facilement de l'interface Developer Console à [{{site.data.keyword.dev_cli_notm}}](/docs/cli/idt/index.html) et inversement.

La console {{site.data.keyword.cloud_notm}} Developer Console vous permet de générer en toute transparence une application Starter prête pour la production dans le cadre du cas d'utilisation sélectionné. Examinons les différentes étapes que vous pouvez suivre au cours de ce processus.

<!-- Ready to jump in?  Visit the [{{site.data.keyword.cloud_notm}} Web App developer console](https://{DomainName}/developer/appservice) to get started.
{: tip} -->

##Ecran Vue d'ensemble
{: #overview_screen}

L'écran Vue d'ensemble inclut le contenu adapté aux élément sur lesquels vous travaillez dans la console de développeur. A partir de cet écran, vous pouvez voir la documentation, accéder aux ressources d'apprentissage, parcourir les services, voir les kits de démarrage proposés ou accéder à des liens vers d'autres kits de démarrage. Cliquez sur `Kits de démarrage` dans la navigation pour accéder à la vue correspondante.

![Ecran Vue d'ensemble de Developer Console](images/overview_screen.png "Ecran Vue d'ensemble") <br> *Ecran Vue d'ensemble de Developer Console*

##Vue Kits de démarrage
{: #starter_kits_view}

La vue Kits de démarrage affiche l'ensemble de kits de démarrage spécifiques à une zone de cas d'utilisation. Vous pouvez cliquer sur différents liens dans une carte de kit de démarrage pour voir des démonstrations ainsi que d'autres informations. Sélectionnez un kit de démarrage pour accéder à la vue Créer une application.

Dans certains cas, lorsque vous sélectionnez un kit de démarrage, des informations sur ce dernier s'affichent. Le cas échéant, il vous suffit de cliquer sur le bouton `Créer` pour accéder à la vue Créer une application.{: tip}

![Vue Kits de démarrage de Developer Console](images/starter_kits_view.png "Vue Kits de démarrage") <br> *Vue Kits de démarrage de Developer Console*

##Vue Créer une application
{: #create_new_project_view}

Dans la vue Créer une application, vous pouvez nommer votre application, indiquer des informations de déploiement et de routage et sélectionner un langage. Sur la droite, vous pouvez également voir les services automatiquement mis à disposition lors de la création de votre application ainsi que les différentes conditions de tarification. Cliquez sur `Créer` pour accéder à la vue Détails de l'application. Si vous n'êtes pas encore connecté à {{site.data.keyword.cloud_notm}}, vous devez le faire maintenant.

![Vue Créer une application de Developer Console](images/create_new_project_view.png "Vue Créer une application") <br> *Vue Créer une application de Developer Console*

## Vue Détails de l'application
{: #project_details_view}

La vue Détails de l'application affiche la liste des services configurés pour votre application. Pour chaque élément de la liste, vous avez accès au nom du service, à des liens vers d'autres informations ainsi qu'à un bouton d'*actions* avec trois points alignés verticalement. Les options de ce bouton** permettent de retirer un service de l'application, d'ouvrir le tableau de bord pour le service et de supprimer le service. Le fait de retirer une instance de service retire uniquement l'association à cette application mais ne supprime pas l'instance de service. Notez également que les données d'identification du service sont consolidées dans cette vue. Il n'est donc pas nécessaire d'accéder à chaque vue d'instance de service individuelle pour les obtenir.

![Vue Détails de l'application de Developer Console](images/project_details_view.png "Vue Détails de l'application") <br> *Vue Détails de l'application de Developer Console*

La vue Détails de l'application vous permet également d'ajouter à votre application des services, qu'ils soient nouveaux ou existants, qui ne faisaient pas partie du kit de démarrage d'origine. Pour cela, cliquez sur le lien `Ajouter une ressource` dans la zone de liste des services. Les services disponibles dépendent du type d'application et des services d'une région. Tous les services ne peuvent donc pas être associés à toutes les applications.

![Boîte de dialogue Ajouter une ressource de Developer Console](images/add_resource_dialog.png "Boîte de dialogue Ajouter une ressource") <br> *Boîte de dialogue Ajouter une ressource de Developer Console*

Dans la vue Détails de l'application, vous pouvez accéder à votre code de deux manières différentes :

*  [Méthode recommandée] Cliquez sur le bouton `Déployer dans le cloud` pour transférer votre code à un référentiel et déployer l'application dans {{site.data.keyword.cloud_notm}}. Pour plus d'informations sur la chaîne d'outils {{site.data.keyword.cloud_notm}} DevOps, cliquez [ici](/docs/services/ContinuousDelivery/toolchains_about.html#toolchains_about).
*  Pour avoir un aperçu de votre code d'application, sélectionnez `Télécharger le code` afin de générer et de télécharger le code pour votre application.

##Vue Liste des applications
{: #project_list_view}

Dans la vue Liste des applications, vous pouvez voir la liste de toutes les applications que vous avez créées. Vous pouvez également renommer ou supprimer vos applications. Cliquez sur une ligne de nom d'application pour accéder à nouveau à la vue Détails de l'application.

![Vue Liste des applications de Developer Console](images/project_list_view.png "Vue Liste des applications") <br> *Vue Liste des applications de Developer Console*
