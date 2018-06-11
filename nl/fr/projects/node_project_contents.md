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

# Fichiers d'application Node.js
{: #node-project-files}

Pour les applications Node.js, les informations ci-après répertorient ce que l'on trouve généralement dans {{site.data.keyword.Bluemix}}. Lorsque vous créez un kit de démarrage, ces fichiers sont créés pour vous. Si vous faites migrer une application vers un hôte dans {{site.data.keyword.Bluemix_notm}}, vous souhaiterez peut-être passer en revue ces informations pour éviter tout conflit. 
{:shortdesc}

Le tableau suivant répertorie les répertoires et les fichiers inclus dans une application Node.js générée :

| Répertoire racine                                     | Description                       |
|:------------------------------------------------|:------------------------------------------|
|package.json
| Fichier de métadonnées |
|cli-config.yml | Options de configuration d'interface de ligne de commande |
|manifest.yml | Fichier de déploiement Cloud Foundry |
| Dockerfile | Fichier Dockerfile pour les commandes `ibmcloud dev run`, `ibmcloud dev deploy` et `docker` |
| Dockerfile-tools | Fichier Dockerfile pour `ibmcloud dev build` et `ibmcloud dev test` |
|docker-compose.yml | Configuration de service d'application pour Docker Compose |
|webpack.config.js | Configuration Webpack pour les informations liées à la génération |
| LICENSE | Fichier de licence |
| README.md | Description d'application |
{: caption="Tableau 1. Contenu du répertoire racine généré dans une application Node.js " caption-side="top"}

|Répertoire  `./public/` | Description |
|:------------------------------------------------|:------------------------------------------|
| `./public/swagger.yml` | Spécification Swagger pour la description d'API REST |
| `./public/index.html` | Balisage de squelette pour des applications Web |
|`./public/server/server.js` | Fichier d'implémentation de serveur |
{: caption="Tableau 2. Contenu du répertoire public généré dans une application Node.js " caption-side="top"}

|Répertoire  `./test/` | Description |
|:------------------------------------------------|:------------------------------------------|
|test-server.js | Test d'intégration pour Express server |
{: caption="Tableau 3. Contenu du répertoire test généré dans une application Node.js " caption-side="top"}

|Répertoire  `./.bluemix/` | Description |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de construction du conteneur |
| deploy.json | Informations de déploiement |
| kube_deploy.sh | Script de déploiement Kubernetes |
| pipeline.yml | Définition de pipeline IBM Cloud |
| toolchain.yml | Définition de chaîne d'outils IBM Cloud |
{: caption="Tableau 4. Contenu du répertoire Bluemix généré dans une application Node.js" caption-side="top"}

|Répertoire `./chart/<projectname>/` | Description |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Graphique Helm |
| `./chart/<projectname>/values.yaml` | Valeurs du graphique Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Modèle de déploiement |
| `./chart/<projectname>/templates/service.yaml` | Modèle de service |
{: caption="Tableau 5. Contenu du répertoire chart généré dans une application Node.js " caption-side="top"}
