---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-25"

keywords: apps, credentials, service, add service credentials, environment, deployment

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# Ajout de données d'identification de service à votre environnement de déploiement
{: #credentials_overview}

Découvrez comment ajouter manuellement des données d'identification de service à votre environnement de déploiement.
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

En général, vous souhaitez que votre logique d'application se procure les données d'identification de service sensibles, comme les clés ou les mots de passe d'API de base de données, à partir de l'environnement où s'exécute votre application. Ainsi, vous ne conservez pas les données d'identification dans votre référentiel de codes source. Les bases de données de vos environnements d'intégration continue, de pré-production et de production sont mises en quarantaine ou isolées les unes des autres.

Si vous créez une application en utilisant un modèle de kit de démarrage, l'environnement est préparé pour vous automatiquement. Votre cible de déploiement peut être de type suivant :
<!-- Add links to the new topics in the /docs/resources repo when available-->
  * Kubernetes
  * Cloud Foundry Public ou Cloud Foundry Enterprise Environment
  * Instance de serveur virtuel (également Docker local)
  
Cette procédure permet de configurer l'environnement. Les kits de démarrage génèrent du code qui utilise une bibliothèque dépendante afin de rendre le code portable pour qu'il s'exécute sur une des cibles de déploiement. Pour finir, aucune ramification n'est utilisée pour détecter dans quelle cible de déploiement l'application s'exécute.

L'administrateur ou l'ingénieur DevOps a la charge de préparer les environnements avec les configurations et les contrôles d'accès appropriés pour rendre disponibles les valeurs requises par votre application.

L'exécution de l'option "Configurer la distribution continue" est une étape unique qui effectue les tâches principales suivantes :
 * Prépare votre cible de déploiement avec des services, des ressources et des données d'identification.
 * Crée une chaîne d'outils DevOps pour générer et déployer votre application dans cet environnement, en utilisant le code qui référence correctement les données d'identification dans l'environnement.

Cependant, vous devez préparer la cible de déploiement dans l'un des scénarios suivants :
 * Lorsque vous utilisez votre propre code.
 * Lorsque vous utilisez un modèle de kit de démarrage vide.
 * Lorsque vous ajoutez un service à une application reposant sur un kit de démarrage après son déploiement.

La préparation d'environnement est toujours effectuée pour toutes les données d'identification de tous les services associés à une application et tous les `services` sont répertoriés dans le fichier `manifest.yml`, mais les références de données d'identification ne sont pas toutes placées dans le fichier `mappings.json`. Dans ce cas, vous devez vous-même placer ces références dans le fichier. Une fois que vous avez choisi un déploiement cible et que vous n'avez pas besoin de l'abstraction de la bibliothèque `IBMCloudEnv`, consultez la section "Votre code + (cible de déploiement)" correspondant à votre décision.
{: important}

Certains kits de démarrage n'incluent pas la référence à la dépendance `IBMCloudEnv`, au fichier `manifest.yml` ou au fichier `mappings.json`.
{: important}
