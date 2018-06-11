---

copyright:
  years: 2015, 2018
lastupdated: "2018-05-22"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Fichiers d'application Java
{: #java-project-files}

Pour les applications Java, les informations ci-après répertorient ce que l'on trouve généralement dans {{site.data.keyword.Bluemix}}. Lorsque vous créez un kit de démarrage, ces fichiers sont créés pour vous. Si vous faites migrer une application vers un hôte dans {{site.data.keyword.Bluemix_notm}}, vous souhaiterez peut-être passer en revue ces informations pour éviter tout conflit. 
{:shortdesc}

## Spring
{: #spring-project-files}

Le tableau suivant répertorie les répertoires et les fichiers inclus dans une application Java Spring générée :

|Répertoire  `./`                                   | Description                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | Fichier Maven POM |
| cli-config.yml | Options de configuration d'interface de ligne de commande |
| manifest.yml | Fichier de déploiement Cloud Foundry |
| Dockerfile | Fichier Dockerfile pour les commandes `ibmcloud dev run`, `ibmcloud dev deploy` et `docker` |
| Dockerfile-tools | Fichier Dockerfile pour `ibmcloud dev build` et `ibmcloud dev test` |
| LICENSE |Fichier de licence |
| README.md | Description d'application |
{: caption="Tableau 1. Contenu du répertoire racine généré dans une application Java Spring" caption-side="top"}

|Répertoire  `./src/main/java/` | Description                       |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/test/application/SBApplication.java` | Principale application Spring |
| `./src/main/test/application/HealthEndpointTest.java` | Tests |
| `./src/main/java/application/rest/HealthApplication.java` | Noeud final de santé |
| `./src/main/java/application/rest/v1/Example.java` | Exemple de code |
| `./src/main/java/resources/application-local.properties` | Propriétés Spring |
{: caption="Tableau 2. Contenu du répertoire /java/ généré dans une application Java Spring" caption-side="top"}

|Répertoire  `./.bluemix/` | Description |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de construction du conteneur |
| deploy.json | Informations de déploiement |
| kube_deploy.sh | Script de déploiement Kubernetes |
| pipeline.yml | Définition de pipeline IBM Cloud |
| toolchain.yml | Définition de chaîne d'outils IBM Cloud |
{: caption="Tableau 3. Contenu du répertoire ./.bluemix/ généré dans une application Java Spring" caption-side="top"}

| Répertoire `./chart/<projectname>/`| Description |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Graphique Helm |
| `./chart/<projectname>/values.yaml` | Valeurs du graphique Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Modèle de déploiement |
| `./chart/<projectname>/templates/hpa.yaml` | Modèle HPA |
| `./chart/<projectname>/templates/service.yaml` | Modèle de service |
{: caption="Tableau 4. Contenu du répertoire ./chart/<projectname>/templates/ généré dans une application Java Spring" caption-side="top"}>

|Répertoire  `./manifests/`| Description |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Fichier yaml de service et de déploiement Kubernetes |
{: caption="Tableau 5. Contenu du répertoire ./manifests/ généré dans une application Java Spring " caption-side="top"}

## Liberty
{: #liberty-project-files}

Le tableau suivant répertorie les répertoires et les fichiers inclus dans une application Java Liberty générée :

|Répertoire  `./`                                   | Description                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | Fichier Maven POM |
| cli-config.yml | Options de configuration d'interface de ligne de commande |
| manifest.yml | Fichier de déploiement Cloud Foundry |
| Dockerfile | Fichier Dockerfile pour les commandes `ibmcloud dev run`, `ibmcloud dev deploy` et `docker` |
| Dockerfile-tools |Fichier Dockerfile pour les commandes `ibmcloud dev build` et `ibmcloud dev test` |
| LICENSE | Fichier de licence |
| README.md | Description d'application |
{: caption="Tableau 6. Contenu du répertoire racine généré dans une application Java Liberty" caption-side="top"}

|Répertoire  `./src/main` | Description |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/java/application/rest/HealthApplication.java` | Noeud final de santé |
| `./src/main/java/application/rest/v1/Example.java` | Exemple de code |
| `./src/main/liberty/config/jvm.options` | Options JVM |
| `./src/main/liberty/config/jvmbx.options` | Configuration d'agent de métriques Java |
| `./src/main/liberty/config/server.env` | Variables d'environnement |
| `./src/main/liberty/config/server.xml` | Configuration de serveur |
| `./src/main/webapp/WEB-INF/beans.xml` | Configuration de bean CDI |
| `./src/main/webapp/WEB-INF/ibm-web-ext.xml` | Configuration d'application Web IBM |
| `./src/main/test/it/HealthEndpointTest.java` | Tests |
{: caption="Tableau 7. Contenu du répertoire ./src/main/ généré dans une application Java Liberty " caption-side="top"}

| Répertoire `./.bluemix/`| Description |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de construction du conteneur |
| deploy.json | Informations de déploiement |
| kube_deploy.sh | Script de déploiement Kubernetes |
| pipeline.yml | Définition de pipeline IBM Cloud |
| toolchain.yml | Définition de chaîne d'outils IBM Cloud |
{: caption="Tableau 8. Contenu du répertoire ./bluemix/ généré dans une application Java Liberty " caption-side="top"}

|Répertoire `./chart/<projectname>/` | Description |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Graphique Helm |
| `./chart/<projectname>/values.yaml` | Valeurs du graphique Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Modèle de déploiement |
| `./chart/<projectname>/templates/hpa.yaml` | Modèle HPA |
| `./chart/<projectname>/templates/service.yaml` | Modèle de service |
{: caption="Tableau 9. Contenu du répertoire ./chart/<projectname>/ généré dans une application Java Spring" caption-side="top"}>

|Répertoire  `./manifests/`| Description |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Fichier yaml de service et de déploiement Kubernetes |
{: caption="Tableau 10. Tableau 5. Contenu du répertoire ./manifests/ généré dans une application Java Liberty " caption-side="top"}
