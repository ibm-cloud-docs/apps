---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-20"

keywords: apps, starter kit, kubernetes, cluster, kube, deploy, deployment

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Déploiement d'une application de kit de démarrage dans un cluster Kubernetes
{: #tutorial-starterkit-kube}

Découvrez comment créer une application dans {{site.data.keyword.cloud}} en utilisant un kit de démarrage de base et une chaîne d'outils Kubernetes et en mettant à disposition en continu l'application dans un conteneur sécurisé {{site.data.keyword.containerlong}}. Votre pipeline DevOps d'intégration continue peut être configuré afin que vos modifications de code soient automatiquement générées et propagées dans l'application se trouvant dans le cluster Kubernetes. Si vous disposez déjà d'un pipeline, vous pouvez le connecter à votre application.
{: shortdesc}

{{site.data.keyword.cloud_notm}} inclut des kits de démarrage vous permettant de générer les bases d'une application s'exécutant sur Kubernetes. Lorsque vous utilisez un kit de démarrage, il est facile de suivre un modèle de programmation natif de cloud qui utilise les meilleures pratiques {{site.data.keyword.cloud_notm}} pour le développement d'application. Les kits de démarrage génèrent des applications qui suivent le modèle de programmation natif de cloud. Ils incluent des scénarios de test, le diagnostic d'intégrité et des métriques dans chaque langage de programmation. Vous pouvez également mettre à disposition des services cloud qui sont ensuite initialisés dans votre application générée.

Ce tutoriel utilise la cible de déploiement {{site.data.keyword.containerlong}}. Dans ce tutoriel, vous allez créer une application à partir d'un kit de démarrage de base en utilisant Java + Spring, en y ajoutant une instance de service Cloudant et en la déployant dans {{site.data.keyword.containerlong}}. 

## Avant de commencer
{: #prereqs-starterkit-kube}

* Créez une application **Java + Spring** en utilisant un [kit de démarrage](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit).
* Installez l'[interface de ligne de commande {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-getting-started).
* Configurez [Docker ](https://www.docker.com/get-started){: new_window} ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe").

## Ajout de services à votre application
{: #resources-starterkit-kube}

Ajoutez un service {{site.data.keyword.cloud_notm}} à votre application. La procédure suivante met à disposition une instance Cloudant, crée une clé de ressource (données d'identification) et l'associe à votre application.

1. Sur la page **Détails de l'application**, cliquez sur **Ajouter un service**.
2. Sélectionnez **Données** puis cliquez sur **Suivant**..
3. Sélectionnez **Cloudant** puis cliquez sur **Suivant**.
4. Sur la page **Ajouter Cloudant**, sélectionnez la région (US-South), le groupe de ressources (valeur par défaut) et le plan de tarification (Lite - instance gratuite).
5. Cliquez sur **Créer**. La page **Détails de l'application** s'affiche et l'instance Cloudant est mise à disposition et liée à votre application. Notez que la clé de ressource Cloudant (données d'identification) est ajoutée à la zone **Données d'identification**.
6. Facultatif. Si vous souhaitez parcourir rapidement votre code d'application après l'ajout de services, cliquez sur **Télécharger le code**. Votre code est téléchargé en tant que fichier `.zip` contenant l'ensemble de la structure du code d'application. Vous pouvez facilement extraire le fichier et exécuter le code localement à l'aide du plug-in {{site.data.keyword.dev_cli_notm}} ou l'ajouter à votre référentiel de gestion de code.

## Déploiement de votre application à l'aide d'une chaîne d'outils DevOps
{: #deploy-starterkit-kube}

Connectez une chaîne d'outils DevOps à l'application et configurez-la de telle sorte qu'elle soit déployée dans un cluster Kubernetes hébergé dans le service {{site.data.keyword.cloud_notm}} Kubernetes.

1. Sur la page **Détails de l'application**, cliquez sur **Configurer la distribution continue**.
2. Sur la page **Sélectionner une cible de déploiement** page, sélectionnez **Déployer dans IBM Kubernetes Service**.
3. Sélectionnez une région et un cluster. Si vous n'avez pas de cluster Kubernetes, cliquez sur **Créer un cluster**.
  * Sur la page **Créer un nouveau cluster**, sélectionnez l'emplacement, le type de cluster (gratuit), entrez un nom de cluster puis cliquez sur **Créer un cluster**.
  * Si nécessaire, suivez les instructions à l'écran pour obtenir l'accès à votre cluster.
  * Attendez que le cluster indique **PRET** pour créer la chaîne d'outils. Avec la région **US-South**, vous pouvez mettre à disposition un cluster gratuit.
  * Retournez à la page **Sélectionner une cible de déploiement**.
4. Cliquez sur **Suivant**. La page **Configurer la chaîne d'outils** s'affiche.
5. Sur la page **Configurer la chaîne d'outils**, entrez un nom de chaîne d'outils, sélectionnez une région, sélectionnez un groupe de ressources puis cliquez sur **Créer**. La page **Détails de l'application** s'affiche avec les informations de déploiement concernant votre chaîne d'outils.

## Affichage de votre référentiel
{: #view-repo-starterkit-kube}

1. Sur la page **Détails de l'application**, cliquez sur **Afficher le référentiel**. Le référentiel Git généré par le kit de démarrage s'affiche.
2. Facultatif. Configurez SSH sur votre bureau en suivant les instructions à l'écran.
3. Facultatif. Créez un jeton d'accès personnel sur votre compte en suivant les instructions à l'écran.

## Affichage de l'historique, des journaux et des outils de chaîne d'outils
{: #view-logs-starterkit-kube}

1. Une fois l'étape de déploiement terminée, la page **Détails de l'application** s'affiche avec les informations de déploiement concernant votre chaîne d'outils.
2. Accédez à la chaîne d'outils en cliquant sur **Afficher la chaîne d'outils**. L'onglet **Vue d'ensemble** de la page de chaîne d'outils s'affiche. Il présente les outils inclus avec la chaîne d'outils. Cet exemple inclut les outils suivants présélectionnés dans le kit de démarrage lors de la création de la chaîne d'outils :
  * Un dispositif de suivi de travaux permettant d'effectuer le suivi des modifications et des mises à jour de projet.
  * Un référentiel Git qui contient le code source de votre application.
  * Une instance Eclipse Orion, qui est un environnement IDE Web permettant d'éditer votre application.
  * Un élément Delivery Pipeline composé d'une étape de génération et de déploiement pouvant être personnalisée.
	 * L'étape de génération conteneurise l'application, plus particulièrement elle :
	   * clone votre référentiel GitLab.
	   * génère l'application.
	   * génère l'application Docker.
	   * publie l'image dans votre registre de conteneur privé.
	 * L'étape de déploiement extrait l'image de conteneur de votre registre de conteneur puis la déploie dans votre cluster Kubernetes.
3. Cliquez sur **Delivery Pipeline**. Les étapes de pipeline s'affichent.
4. Dans la vignette **Etape de déploiement**, cliquez sur **Afficher les journaux et l'historique**.

## Vérification que votre application est en cours d'exécution
{: #verify-starterkit-kube}

Une fois votre application déployée, Delivery Pipeline ou la ligne de commande indique l'URL de votre application.

1. Dans votre chaîne d'outils DevOps, cliquez sur **Delivery Pipeline** puis sélectionnez **Etape de déploiement**.
2. Cliquez sur **Afficher les journaux et l'historique**.
3. Dans le fichier journal, recherchez l'URL de l'application :

    A la fin du fichier journal, recherchez `View the application health at: http://<ipaddress>:<port>/health`.

4. Accédez à l'URL dans votre navigateur. Si l'application est en cours d'exécution, un message qui inclut `Congratulations` ou `{"status":"UP"}` s'affiche.

Si vous utilisez la ligne de commande, exécutez la commande [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) pour afficher l'URL de votre application. Accédez ensuite à l'URL dans votre navigateur.

## Etapes suivantes
{: #next-steps-startkit-kube notoc}

* Si des erreurs surviennent lors du déploiement, consultez la rubrique de traitement des incidents concernant les problèmes connus, comme le [dépassement du quota de stockage](/docs/apps?topic=creating-apps-managingapps#exceed_quota) ou découvrez comment [accéder aux journaux Kubernetes](/docs/apps?topic=creating-apps-managingapps#access_kube_logs) pour rechercher des erreurs.

* Accédez à la configuration de service dans votre code :
	- Vous pouvez utiliser l'annotation _@Value_ ou utiliser la méthode _getProperty()_ de la classe d'environnement de structure Spring. Pour plus d'informations, voir [Accès aux données d'identification](/docs/java-spring?topic=java-spring-configuration#accessing-credentials).

* Ajoutez de nouvelles données d'identification de service à votre environnement Kubernetes :
	- Lorsque vous ajoutez un autre service à votre application une fois la chaîne d'outils DevOps créée, ces données d'identification de service ne sont pas automatiquement mises à jour dans votre application déployée et votre référentiel GitLab. Vous devez [ajouter manuellement les données d'identification à l'environnement de déploiement](/docs/apps?topic=creating-apps-credentials_overview).
