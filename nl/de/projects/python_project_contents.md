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

# Python-App-Dateien
{: #python-project-files}

Für Python-Apps stellen die folgenden Informationen einen Bestand der Komponenten dar, die Sie typischerweise in {{site.data.keyword.Bluemix}} finden. Wenn Sie ein Starter-Kit erstellen, werden diese Dateien für Sie erstellt. Wenn Sie eine App migrieren, um sie in {{site.data.keyword.Bluemix_notm}} zu hosten, sollten Sie diese Informationen durchlesen, um potenzielle Konflikte zu vermeiden.
{:shortdesc}

In der folgenden Tabelle sind die gängigen Verzeichnisse und Dateien aufgelistet, die in einer generierten Python-App enthalten sind.

| Stammverzeichnis                                     | Beschreibung                       |
|:------------------------------------------------|:------------------------------------------|
| requirements.txt | Erforderliche Python-Pakete |
| setup.py | Python-Installationsscript |
| cli-config.yml | CLI-Konfigurationsoptionen |
| manifest.yml | Cloud Foundry-Bereitstellungsdatei |
| Dockerfile | Dockerfile für Befehle `ibmcloud dev run`, `ibmcloud dev deploy` und `docker` |
| Dockerfile-tools | Dockerfile für `ibmcloud dev build` und `ibmcloud dev test` |
| LICENSE | Lizenzdatei |
| README.md | Beschreibung der App |
{: caption="Tabelle 1. Inhalt des Stammverzeichnisses einer generierten Python-App" caption-side="top"}

| Verzeichnis `./public/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| swagger.yml | Swagger-Spezifikation zum Beschreiben von REST-APIs |
| index.html | Gerüst-Markup für Webanwendungen |
{: caption="Tabelle 2. Inhalt des öffentlichen Verzeichnisses einer generierten Python-App" caption-side="top"}

| Verzeichnis `./server/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| `__init__.py` | Markiert Verzeichnisse als Python-Paketverzeichnisse |
{: caption="Tabelle 3. Inhalt des Serververzeichnisses einer generierten Python-App" caption-side="top"}

| Verzeichnis `./tests/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| app_tests.py | Testfälle für Python-Server |
{: caption="Tabelle 4. Inhalt des Testverzeichnisses einer generierten Python-App" caption-side="top"}

| Verzeichnis `./.bluemix/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Container-Build-Script |
| deploy.json | Bereitstellungsinformationen |
| kube_deploy.sh | Kubernetes-Bereitstellungsscript |
| pipeline.yml | IBM Cloud-Pipelinedefinition |
| toolchain.yml | IBM Cloud-Toolchaindefinition |
{: caption="Tabelle 5. Inhalt des Bluemix-Verzeichnisses einer generierten Python-App" caption-side="top"}

| `./chart/<projectname>Verzeichnis /` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm-Diagramm |
| `./chart/<projectname>/values.yaml` | Helm-Diagrammwerte |
| `./chart/<projectname>/templates/deployment.yaml` | Bereitstellungsvorlage |
| `./chart/<projectname>/templates/service.yaml` | Servicevorlage |
{: caption="Tabelle 6. Inhalt des Diagrammverzeichnisses einer generierten Python-App" caption-side="top"}
