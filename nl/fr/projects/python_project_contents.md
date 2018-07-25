---
copyright:
  years: 2015, 2018
lastupdated: "2018-07-05"
---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Fichiers d'application Python
{: #python-project-files}

Pour les applications Python, les informations ci-après répertorient ce que l'on trouve généralement dans {{site.data.keyword.Bluemix}}. Lorsque vous créez un kit de démarrage, ces fichiers sont créés pour vous. Si vous faites migrer une application vers un hôte dans {{site.data.keyword.Bluemix_notm}}, vous souhaiterez peut-être passer en revue ces informations pour éviter tout conflit.
{:shortdesc}

Le tableau suivant répertorie les répertoires et les fichiers couramment inclus dans une application Python générée :

| Répertoire racine                                     | Description                       |
|:------------------------------------------------|:------------------------------------------|
| requirements.txt | Packages Python requis |
| setup.py | Script d'installation de python |
| cli-config.yml | Options de configuration d'interface de ligne de commande |
| manifest.yml | Fichier de déploiement Cloud Foundry |
| Dockerfile | Fichier Dockerfile pour les commandes `ibmcloud dev run`, `ibmcloud dev deploy` et `docker` |
| Dockerfile-tools | Fichier Dockerfile pour `ibmcloud dev build` et `ibmcloud dev test` |
| LICENSE | Fichier de licence |
| README.md | Description d'application |
{: caption="Tableau 1. Contenu du répertoire racine généré dans une application Python" caption-side="top"}

| Répertoire  `./public/` | Description |
|:------------------------------------------------|:------------------------------------------|
| swagger.yml | Spécification Swagger pour la description d'API REST |
| index.html | Balisage de squelette pour des applications Web |
{: caption="Tableau 2. Contenu du répertoire public généré dans une application Python" caption-side="top"}

| Répertoire `./server/` | Description |
|:------------------------------------------------|:------------------------------------------|
| `__init__.py` | Marque les répertoires en tant que répertoires de packages Python |
{: caption="Tableau 3. Contenu du répertoire server généré dans une application Python" caption-side="top"}

| Répertoire `./tests/` | Description |
|:------------------------------------------------|:------------------------------------------|
| app_tests.py | Scénarios de test de serveur Python |
{: caption="Tableau 4. Contenu du répertoire tests généré dans une application Python" caption-side="top"}

| Répertoire  `./.bluemix/` | Description |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de construction du conteneur |
| deploy.json | Informations de déploiement |
| kube_deploy.sh | Script de déploiement Kubernetes |
| pipeline.yml | Définition de pipeline IBM Cloud |
| toolchain.yml | Définition de chaîne d'outils IBM Cloud |
{: caption="Tableau 5. Contenu du répertoire Bluemix généré dans une application Python" caption-side="top"}

| `./chart/<projectname>Répertoire /` | Description |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Graphique Helm |
| `./chart/<projectname>/values.yaml` | Valeurs du graphique Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Modèle de déploiement |
| `./chart/<projectname>/templates/service.yaml` | Modèle de service |
{: caption="Tableau 6. Contenu du répertoire chart généré dans une application Python" caption-side="top"}
