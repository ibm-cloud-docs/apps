---

copyright:
  years: 2019
lastupdated: "2019-05-09"

keywords: developer tools, building apps, developer entry point, get started coding, starter kit

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Qu'est-ce qu'un kit de démarrage ?
{: #starter-kits}

Un kit de démarrage est un modèle prêt pour la production qui peut être intégré à un ensemble de services afin de générer un élément prêt pour la production pouvant être déployé directement dans un pipeline DevOps et un cluster Kubernetes. Les kits de démarrage constituent la solution idéale pour assembler de manière dynamique dans le langage de votre choix une application de production de squelette prête pour le déploiement en cloud. 
{:shortdesc}

Un kit de démarrage contient des métadonnées qui décrivent en quoi consiste le kit et ce qu'il fait. Il contient également des informations qui indiquent à {{site.data.keyword.cloud_notm}} ce qu'il doit produire. La sortie est prête à la production et peut être réutilisée pour d'autres améliorations conformes aux pratiques recommandées d'{{site.data.keyword.cloud_notm}}. Le contenu du kit de démarrage n'est pas aussi complexe qu'une démonstration et pas aussi simple qu'un fragment ou un exemple. Les applications sont créées dynamiquement selon les exigences du développeur.

Chaque kit de démarrage comprend un langage, une infrastructure et un modèle pour un scénario d'utilisation spécifique. Vous pouvez réutiliser le code au lieu de le réinventer. Si un kit de démarrage nécessite des services spécifiques, des services fournis automatiquement sont disponibles pour que des instances de ces services soient automatiquement créées lorsque vous créez votre application.

## Qu'est-ce qui distingue les kits de démarrage des exemples ?
{: #compare}

Les kits de démarrage sont prêts pour la production et ont pour principal objectif de présenter une implémentation de modèle de clé à l'aide d'un environnement d'exécution (par exemple, Node.js et Express). Dans certains cas, les kits de démarrage offrent une expérience utilisateur simple ayant pour but de mettre en évidence l'intégration du service. Dans d'autres cas, les kits de démarrage représentent une implémentation personnalisable d'un cas d'utilisation sophistiqué.

Un fragment correspond à quelques lignes de code, souvent présentées dans une interface IDE. Les fragments aident un développeur à intégrer une syntaxe de langage de programmation ou une intégration de support à une API définie. Une démonstration est généralement de très bonne qualité et d'une grande fidélité et utilise une gamme de services et de points d'intégration. Elle requiert souvent un certain temps de réglage et est utilisée pour démontrer un problème ou illustrer un dispositif de plateforme. Vous pouvez l'utiliser pour évaluer les phases d'adoption du cloud. Parfois, il s'agit de code inclus dans le code de production. Un exemple est un petit exemple d'un dispositif, d'une fonction, d'un service ou d'une démarche utilisateur spécifique. Vous pouvez réutiliser un exemple ou l'inclure dans une application de production. Il est généralement utilisé pour montrer des capacités techniques et une approche possible de résolution d'un problème technique.

## Code portable
{: #portable-code}

Lorsque vous créez une application à partir d'un kit de démarrage, un code est automatiquement créé pour vous à un format cohérent et ne dépendant pas de l'environnement d'exécution. Vous pouvez déployer le code dans la cible de votre choix (Kubernetes ou Cloud Foundry, par exemple) sans apporter de modifications.

Ce dernier contient du code d'activation de cloud pour plusieurs environnements de cloud. Vous pouvez produire un code qui suit les pratiques recommandées d'un langage spécifique et qui est spécifique à un cas d'utilisation. 

* Une logique de cas d'utilisation fournit des fonctions pour la fonction principale d'un cas d'utilisation donné. Par exemple, du code pour un agent conversationnel Watson Conversation ou du code pour une application de reconnaissance vocale mobile.
* Les composants de langage sont des composants de code et des fichiers propres au langage de programmation que vous sélectionnez pour votre kit de démarrage Par exemple, les programmeurs node.js ont besoin d'un fichier package.json pour la gestion des dépendances, et il se trouve que ce fichier est automatiquement créé pour vous.
* L'activation de service est un code qui permet à votre application de se connecter aux services que vous ajoutez et de les utiliser. La gestion des données d'identification, le code d'initialisation et les SDK propres aux services sont des exemples d'éléments d'activation de service.
* L'activation du cloud est un code qui permet à votre application de s'exécuter sur {{site.data.keyword.cloud_notm}}. Par exemple, les graphiques Helm qui permettent à votre application de s'exécuter sur un cluster Kubernetes {{site.data.keyword.cloud_notm}}.

Vous pouvez afficher votre code d'application en cliquant sur **Télécharger le code** sur la page Détails de l'application de votre application. Votre code est téléchargé en tant que fichier `.zip` contenant l'ensemble de la structure du code d'application. Vous pouvez extraire le fichier et exécuter le code localement à l'aide du plug-in {{site.data.keyword.dev_cli_notm}} ou l'ajouter à votre référentiel de gestion de code.

Chaque application inclut un fichier Readme contenant les détails techniques de l'application et expliquant ce qui est nécessaire pour que votre application soit active si elle n'est pas prête à l'emploi.
{: tip}
