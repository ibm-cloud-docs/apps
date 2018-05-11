---
copyright:
  years: 2015, 2018
lastupdated: "2018-03-16"
---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Node.js-Projektdateien
{: #node-project-files}

Für Node.js-Projekte stellen die folgenden Informationen einen Bestand der Komponenten dar, die Sie typischerweise in {{site.data.keyword.Bluemix}} finden. Wenn Sie ein Starter-Kit erstellen, werden diese Dateien für Sie erstellt. Wenn Sie eine App migrieren, um sie in {{site.data.keyword.Bluemix_notm}} zu hosten, sollten Sie diese Informationen durchlesen, um potenzielle Konflikte zu vermeiden.
{:shortdesc}

In der folgenden Tabelle sind die gängigen Verzeichnisse und Dateien aufgelistet, die in einem generierten Node.js-Projekt enthalten sind.

| Verzeichnis und Datei                                     | Beschreibung                       |
|:------------------------------------------------|:------------------------------------------|
|<b>`./`</b>                                             |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;package.json | Metadatendatei |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;cli-config.yml | CLI-Konfigurationsoptionen |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;manifest.yml | Cloud Foundry-Bereitstellungsdatei |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Dockerfile | Dockerfile für Befehle `bx dev run`, `bx dev deploy` und `docker` |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Dockerfile-tools | Dockerfile für `bx dev build` und `bx dev test` |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;docker-compose.yml | App-Service-Konfiguration für Docker Compose |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;webpack.config.js | Webpack-Konfiguration für buildbezogene Informationen |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;LICENSE |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;README.md | Beschreibung des Projekts |
|<b>`./public/`</b> |  |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;swagger.yml | Swagger-Spezifikation zum Beschreiben von REST-APIs |
|<b>`./public/index.html`</b> |  |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;index.html | Gerüst-Markup für Webanwendungen |
|<b>`./public/server/`</b> | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;server.js | Serverimplementierungsdatei |
|<b>`./test/`</b> | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;test-server.js | Integrationstest für Express-Server |
|<b>`./.bluemix/`</b> | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;container_build.sh | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;deploy.json | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;kube_deploy.sh | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pipeline.yml | IBM Cloud-Pipelinedefinition |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;toolchain.yml | IBM Cloud-Toolchaindefinition |
|<b>`./chart/<projectname>/`</b> | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Chart.yaml | Helm-Diagramm |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;values.yaml | Helm-Diagrammwerte |
|<b>`./chart/<projectname>/templates/`</b> | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;deployment.yaml | Bereitstellungsvorlage |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;service.yaml | Servicevorlage |
{: caption="Tabelle 1. Inhalte eines generierten Node.js-Projekts" caption-side="top"}

