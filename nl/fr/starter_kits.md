---

copyright:
  years: 2018
lastupdated: "2018-11-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Développement d'application
{: #intro}

{{site.data.keyword.cloud_notm}} Developer Console permet aux développeurs de créer des applications à partir de kits de démarrage, de mettre à disposition et de connecter des services optimisés par {{site.data.keyword.cloud_notm}} puis de télécharger rapidement un code fonctionnel ou d'effectuer la configuration pour la distribution continue. Vous pouvez créer, afficher, configurer et gérer votre application. Vous pouvez également télécharger le code de cette dernière. En utilisant les kits de démarrage, vous pouvez rapidement évaluer et tester les services {{site.data.keyword.cloud_notm}} avec une application exemple.
{:shortdesc}

## Qu'est-ce qu'un kit de démarrage ?
{: #starter_kits}

Les kits de démarrage constituent la solution idéale pour assembler de manière dynamique dans le langage de votre choix une application de production de squelette prête pour le déploiement en cloud. Chaque kit de démarrage comprend un langage, une infrastructure et un modèle pour un scénario d'utilisation adapté au monde réel spécifique. Vous pouvez réutiliser le code au lieu de le réinventer.

### Comparaison des exemples et des kits de démarrage

Les développeurs s'appuient souvent sur du code pré-écrit, tel que des fragments, des démonstrations et des exemples. Comment faire la différence entre des fragments, des démonstrations, des exemples et des kits de démarrage {{site.data.keyword.cloud_notm}} ?

* **Fragment** - Quelques lignes de code, souvent présentées dans une interface IDE. Les fragments aident un développeur à intégrer une syntaxe de langage de programmation ou une intégration de support à une API définie.

* **Démonstration** - Code généralement de très bonne qualité, d'une grande fidélité et utilisant une gamme de services et de points d'intégration. Elle requiert souvent un certain temps de réglage et est utilisée pour démontrer un problème ou illustrer un dispositif de plateforme. Les démonstrations peuvent évaluer des phases d'adoption du cloud. Parfois, son code est inclus dans le code de production.

* **Exemple** - Code constituant un petit exemple d'un dispositif, d'une fonction, d'un service ou d'une démarche utilisateur spécifique. Un exemple peut être réutilisé ou inclus dans une application en production. Vous pouvez utiliser des exemples pour afficher des fonctions techniques et des approches possibles pour la résolution des problèmes techniques.

* **Kit de démarrage {{site.data.keyword.cloud_notm}} ** - Les kits de démarrage sont des modèles prêts pour la production que vous pouvez intégrer à un ensemble de services pour générer un actif prêt pour la production. Vous pouvez ensuite les déployer directement dans un pipeline DevOps et un cluster Kubernetes. Un kit de démarrage contient des métadonnées descriptives qui vous fournissent suffisamment d'informations pour vous permettre de déterminer ce qu'il est et ce qu'il fait. Il contient également des instructions indiquant à {{site.data.keyword.cloud_notm}} ce qu'il doit produire. La sortie peut être améliorée. Le contenu du kit de démarrage n'est pas aussi complexe qu'une démonstration et pas aussi simple qu'un fragment ou un exemple. Il est créé dynamiquement selon vos exigences.

  Les kits de démarrage présentent une implémentation de modèle avec un environnement d'exécution (Swift et Kitura, par exemple). Ils peuvent inclure une expérience utilisateur simple ayant pour but de mettre en évidence l'intégration du service. Les kits de démarrage constituent des implémentations personnalisables d'un cas d'utilisation sophistiqué.

  Les kits de démarrage incluent des instructions qui permettent à {{site.data.keyword.cloud_notm}} de générer automatiquement des projets d'application structurés avec du code portable. Ils spécifient également des ressources à mettre à disposition automatiquement lorsque vous créez un projet.

## Ressources mises à disposition automatiquement
{: #auto_privisioned_resources}

Si un kit de démarrage spécifie les ressources requises, {{site.data.keyword.cloud_notm}} crée automatiquement les instances de ces ressources lorsque vous créez votre projet. Vous pouvez manuellement mettre à disposition des ressources existantes ou sélectionner des instances de ressource existantes à ajouter à votre projet après sa création. Une liste des instances de service associées à votre projet est visible dans la vue *Détails du projet* ainsi que les données d'identification dont vous pouvez avoir besoin.

## Génération de code portable
{: #portable_code}

Lorsque vous créez une application à partir d'un kit de démarrage, un code est automatiquement créé pour vous dans un format cohérent et indépendant de l'environnement d'exécution. Vous pouvez déployer le code dans l'environnement de votre choix, par exemple, Kubernetes ou Cloud Foundry, sans apporter de modifications.

Le projet inclut un fichier `README` contenant les détails techniques du projet et expliquant ce qui est nécessaire pour que votre application soit prête à s'exécuter.

Pour plus d'informations, voir la console de développeur [{{site.data.keyword.cloud_notm}} pour les ressources d'apprentissage Apple](https://cloud.ibm.com/developer/appledevelopment/learning-resources).
{: tip}

### Quel type de contenu d'application est généré ?
{: #content}

Le code généré par le kit de démarrage {{site.data.keyword.cloud_notm}} comprend quatre composants fondamentaux : la logique de cas d'utilisation, les composants de langage, l'activation de service et l'activation du cloud. La génération de ces composants vous fait économiser un temps précieux et garantit l'utilisation d'une architecture hors pair.

* La **logique de cas d'utilisation** est le code d'un cas d'utilisation particulier. Les exemples incluent le code pour un agent conversationnel Watson Conversation ou du code pour une application de reconnaissance vocale mobile.
* Les **composants de langage** sont des composants de code et des fichiers propres au langage que vous sélectionnez pour votre kit de démarrage. Par exemple, les programmeurs node.js ont besoin d'un fichier `package.json` pour la gestion des dépendances et ce fichier est automatiquement créé par l'expérience de développeur {{site.data.keyword.cloud_notm}}.
* L'**activation de service** est un code qui permet à votre application de connecter votre projet et d'utiliser les services que vous y avez ajoutés. La gestion des données d'identification, le code d'initialisation et les SDK propres aux services sont des exemples d'éléments d'activation de service.
* L'**activation du cloud** est un code qui permet à votre application de s'exécuter sur {{site.data.keyword.cloud_notm}}. Par exemple, les graphiques Helm qui permettent à votre application de s'exécuter sur un cluster Kubernetes {{site.data.keyword.cloud_notm}} font partie de la catégorie d'activation de cloud.

L'application générée par {{site.data.keyword.cloud_notm}} constitue la meilleure méthode en termes d'architecture pour le langage choisi pour votre projet. Pour voir plus de détails sur les fichiers et la structure d'un projet d'application, consultez les rubriques suivantes.

* [Fichiers d'application Java](/docs/apps/projects/java_project_contents.html)
* [Fichiers d'application Node.js](/docs/apps/projects/node_project_contents.html)
* [Fichiers d'application Python](/docs/apps/projects/python_project_contents.html)
* [Fichiers d'application Swift](/docs/apps/projects/swift_project_contents.html).
