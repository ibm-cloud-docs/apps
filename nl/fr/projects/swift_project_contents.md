---
copyright:
  years: 2015, 2018
lastupdated: "2018-10-05"
---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Fichiers d'application Swift
{: #swift-project-files}

Pour les applications Swift, les informations ci-après répertorient ce que l'on trouve généralement dans {{site.data.keyword.Bluemix}}. Lorsque vous créez un kit de démarrage, ces fichiers sont créés pour vous. Si vous faites migrer une application vers un hôte dans {{site.data.keyword.Bluemix_notm}}, vous souhaiterez peut-être passer en revue ces informations pour éviter tout conflit. 
{:shortdesc}

Le tableau suivant répertorie les répertoires et les fichiers inclus dans une application Swift générée :

| Répertoire racine                                     | Description |
|:------------------------------------------------|:------------------------------------------|
| Package.swift| Fichier de définition de dépendance Swift |
| cli-config.yml | Options de configuration d'interface de ligne de commande |
| manifest.yml | Fichier de déploiement Cloud Foundry |
| Dockerfile | Fichier Dockerfile pour les commandes `ibmcloud dev run`, `ibmcloud dev deploy` et `docker` |
| `Dockerfile-tools` | Fichier Dockerfile pour `ibmcloud dev build` et `ibmcloud dev test` |
| LICENSE | Fichier de licence |
| README.md | Description d'application |
{: caption="Tableau 1. Contenu du répertoire racine généré dans une application Swift" caption-side="top"}

| Répertoire  `./Sources/Application/` | Description  |
|:------------------------------------------------|:------------------------------------------|
| `./Sources/Application/Application.swift` | Fichier d'application Swift |
| `./Sources/<projectname>/main.swift` | Principal fichier Swift |
{: caption="Tableau 2. Contenu du répertoire /Sources/Application/ généré dans une application Java" caption-side="top"}

| Répertoire  `./test/` | Description |
|:------------------------------------------------|:------------------------------------------|
|test-server.js | Méthodes utilitaires pour les tests avec Kitura |
{: caption="Tableau 3. Contenu du répertoire de test généré dans une application Swift" caption-side="top"}

| Répertoire  `./Tests/` | Description |
|:------------------------------------------------|:------------------------------------------|
| `./Tests/LinuxMain.swift` | Utilitaire pour les tests sous Linux |
| `./Tests/ApplicationTests>/RouteTests.swift` | Fichier incluant des scénarios de test |
{: caption="Tableau 4. Contenu du répertoire tests généré dans une application Swift" caption-side="top"}

| Répertoire  `./.bluemix/` | Description |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de construction du conteneur |
| deploy.json | Informations de déploiement |
| kube_deploy.sh | Script de déploiement Kubernetes |
| pipeline.yml | Définition de pipeline IBM Cloud |
| toolchain.yml | Définition de chaîne d'outils IBM Cloud |
{: caption="Tableau 5. Contenu du répertoire Bluemix généré dans une application Swift" caption-side="top"}

| `./chart/<projectname>Répertoire /` | Description |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Graphique Helm |
| `./chart/<projectname>/values.yaml` | Valeurs du graphique Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Modèle de déploiement |
| `./chart/<projectname>/templates/service.yaml` | Modèle de service |
{: caption="Tableau 6. Contenu du répertoire chart généré dans une application Swift" caption-side="top"}

| Répertoire `./manifests/` | Description |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Fichier yaml de service et de déploiement Kubernetes |
{: caption="Tableau 7. Contenu d'un répertoire manifests généré" caption-side="top"}

