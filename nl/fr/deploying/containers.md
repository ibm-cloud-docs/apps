---

copyright:
  years: 2018
lastupdated: "2018-07-23"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Utilisation de conteneurs avec Kubernetes
{: #containers}

Commencez à utiliser {{site.data.keyword.containershort}} en déployant des applications hautement disponibles dans des conteneurs Docker s'exécutant dans des clusters Kubernetes. Gérez votre développement coopératif avec Git puis utilisez la chaîne d'outils DevOps pour gérer le déploiement de votre application dans Kubernetes.
{: shortdesc}

Les conteneurs constituent un moyen standard de conditionner des applications et toutes leurs dépendances. Ainsi, vous pouvez déplacer en toute transparence des applications entre divers environnements. Contrairement aux machines virtuelles, les conteneurs ne sont pas intégrés au système d'exploitation. Seuls le code d'application, l'environnement d'exécution, les outils système, les bibliothèques et les paramètres sont inclus dans les conteneurs. Les conteneurs sont plus légers, plus portables et plus efficaces que les machines virtuelles.

Pour plus d'informations sur le service, voir [Initiation à {{site.data.keyword.containershort_notm}}](/docs/containers/container_index.html#container_index).

## Configuration de déploiements
{: #config-deploy}

Lorsque vous créez des applications de back end ou de service Web, vous pouvez les déployer dans le service {{site.data.keyword.containershort_notm}}, qui utilise l'environnement Kubernetes.

1. Déployez votre application dans le cloud en configurant un pipeline de cloud automatisé.
2. Cliquez sur **Déployer dans Cloud**.
3. Sélectionnez Kubernetes en tant que cible. Vous devez [créer un cluster ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/containers-kubernetes/catalog/cluster/create){:new_window} si vous n'en avez pas encore.
4. Une fois votre déploiement terminé, accédez à votre application active dans le cloud en vous procurant l'URL dans les journaux lors déploiement du pipeline de distribution. La dernière adresse IP avec un port constitue la nouvelle page d'accueil de votre application, par exemple 169.60.133.124:32355.

## Liaison de services
{: #bind-services}

Lorsque la chaîne d'outils est créée, les services associés à votre application sont liés au cluster Kubernetes en utilisant des valeurs confidentielles Kubernetes. Ces dernières permettent de gérer les données d'identification de service en dehors de votre application en cours d'exécution. L'application lit les valeurs confidentielles puis extrait les valeurs requises pour le démarrage de l'exécution. La liaison des services vous permet de déployer l'application dans un autre environnement Kubernetes pouvant utiliser des instances de service {{site.data.keyword.cloud_notm}} de niveau de production.

Si vous supprimez le service ou les valeurs confidentielles, vous devez les lier manuellement à nouveau ou supprimer et recréer la chaîne d'outils.
{: tip}

Pour plus d'informations, voir [Secrets ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://kubernetes.io/docs/concepts/configuration/secret/){:new_window}.

## Démarrage du développement
{: #dev}

1. A partir de la chaîne d'outils, accédez à votre nouveau référentiel Git en ligne et commencez à utiliser votre code. Pour voir la chaîne d'outils, cliquez sur **Afficher la chaîne d'outils**.
2. Accédez au référentiel Git dans lequel le code a été créé en clonant le référentiel dans votre environnement local.
3. Ouvrez le projet avec votre environnement IDE favori.

## Génération et déploiement avec une chaîne d'outils
{: #bulid-deploy-tc}

La chaîne d'outils contient l'étape de génération et l'étape de déploiement.

### Etape de génération
{: #build-stage}
L'étape de génération se déclenche lorsqu'une commande `git push` s'exécute dans votre référentiel Git. L'étape du pipeline déclenche une génération d'image de docker et place cette dernière dans le registre de conteneurs.

Pour plus d'informations, voir [Initiation à IBM Cloud Container Registry](/docs/services/Registry/index.html#index).

### Etape de déploiement
{: #deploy-stage}

L'étape de déploiement extrait la dernière image d'{{site.data.keyword.registryshort_notm}} puis la déploie dans votre cluster Kubernetes en utilisant un graphique Helm. Le graphique Helm a été ajouté à votre application lors du déploiement dans le cloud. L'utilisation de ces graphiques facilite la gestion des étapes de déploiement de l'image du conteneur intégré.

Pour plus d'informations, voir [Charts ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://docs.helm.sh/developing_charts/){:new_window}.

{{site.data.keyword.cloud_notm}} prend en charge plusieurs [graphiques Helm préconfigurés ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/containers-kubernetes/solutions/helm-charts){:new_window}.

## Vérification de la sécurité des applications
{: #sec}

{{site.data.keyword.containershort_notm}} prend en charge l'analyse des images de conteneur pour détecter s'il existe des vulnérabilités de sécurité. L'analyse de sécurité est essentielle pour les applications destinées aux entreprises.

Consultez le [référentiel d'images des conteneurs ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/containers-kubernetes/registry/private){:new_window} pour vérifier s'il existe des vulnérabilités de sécurité potentielles.
