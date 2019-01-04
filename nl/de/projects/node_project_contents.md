---
copyright:
  years: 2015, 2018
lastupdated: "2018-11-16"
---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Node.js-App-Dateien
{: #node-project-files}

Für Node.js-Apps stellen die folgenden Informationen einen Bestand der Komponenten dar, die Sie typischerweise in {{site.data.keyword.Bluemix}} finden. Wenn Sie ein Starter-Kit erstellen, werden diese Dateien für Sie erstellt. Wenn Sie eine App migrieren, um sie in {{site.data.keyword.Bluemix_notm}} zu hosten, sollten Sie diese Informationen durchlesen, um potenzielle Konflikte zu vermeiden. 
{:shortdesc}

In der folgenden Tabelle sind die gängigen Verzeichnisse und Dateien aufgelistet, die in einer generierten Node.js-App enthalten sind.

| Stammverzeichnis                                     | Beschreibung                       |
|:------------------------------------------------|:------------------------------------------|
|package.json | Metadateninformationen zu dem Paket, einschließlich Name, Version und Abhängigkeiten. |
|cli-config.yml | CLI-Konfigurationsoptionen |
|manifest.yml | Cloud Foundry-Bereitstellungsdatei |
|Dockerfile | Dockerfile für Befehle `ibmcloud dev run`, `ibmcloud dev deploy` und `docker` |
|Dockerfile-tools | Dockerfile für `ibmcloud dev build` und `ibmcloud dev test` |
|docker-compose.yml | App-Service-Konfiguration für Docker Compose |
|webpack.config.js | Web pack-Konfiguration für buildbezogene Informationen |
| LICENSE | Lizenzdatei |
|README.md | Beschreibung der App |
{: caption="Tabelle 1. Inhalt des Stammverzeichnisses einer generierten Node.js-App" caption-side="top"}

| Verzeichnis `./public/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| `./public/swagger.yml` | Swagger-Spezifikation zum Beschreiben von REST-APIs |
| `./public/index.html` | Gerüst-Markup für Webanwendungen |
|`./public/server/server.js` | Serverimplementierungsdatei |
{: caption="Tabelle 2. Inhalt des öffentlichen Verzeichnisses einer generierten Node.js-App" caption-side="top"}

| Verzeichnis `./test/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| test-server.js | Integrationstest für Express-Server |
{: caption="Tabelle 3. Inhalt des Testverzeichnisses einer generierten Node.js-App" caption-side="top"}

| Verzeichnis `./.bluemix/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Container-Build-Script |
| deploy.json | Bereitstellungsinformationen |
| kube_deploy.sh | Kubernetes-Bereitstellungsscript |
| pipeline.yml | IBM Cloud-Pipelinedefinition |
| toolchain.yml | IBM Cloud-Toolchaindefinition |
{: caption="Tabelle 4. Inhalt des Bluemix-Verzeichnisses einer generierten Node.js-App" caption-side="top"}

| `./chart/<projectname>Verzeichnis /` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm-Diagramm |
| `./chart/<projectname>/values.yaml` | Helm-Diagrammwerte |
| `./chart/<projectname>/templates/deployment.yaml` | Bereitstellungsvorlage |
| `./chart/<projectname>/templates/service.yaml` | Servicevorlage |
{: caption="Tabelle 5. Inhalt des Diagrammverzeichnisses einer generierten Node.js-App" caption-side="top"}
