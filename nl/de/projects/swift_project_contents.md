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

# Swift-App-Dateien
{: #swift-project-files}

Für Swift-Apps stellen die folgenden Informationen einen Bestand der Komponenten dar, die Sie typischerweise in {{site.data.keyword.Bluemix}} finden. Wenn Sie ein Starter-Kit erstellen, werden diese Dateien für Sie erstellt. Wenn Sie eine App migrieren, um sie in {{site.data.keyword.Bluemix_notm}} zu hosten, sollten Sie diese Informationen durchlesen, um potenzielle Konflikte zu vermeiden. 
{:shortdesc}

In der folgenden Tabelle sind die gängigen Verzeichnisse und Dateien aufgelistet, die in einer generierten Swift-App enthalten sind.

| Stammverzeichnis                                     | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
|Package.swift| Swift-Abhängigkeitsdefinitionsdatei |
|cli-config.yml | CLI-Konfigurationsoptionen |
|manifest.yml | Cloud Foundry-Bereitstellungsdatei |
|Dockerfile |Dockerfile für Befehle `ibmcloud dev run`, `ibmcloud dev deploy` und `docker` |
|Dockerfile-tools | Dockerfile für `ibmcloud dev build` und `ibmcloud dev test` |
| LICENSE | Lizenzdatei |
|README.md | Beschreibung der App |
{: caption="Tabelle 1. Inhalt des Stammverzeichnisses einer generierten Swift-App" caption-side="top"}

| Verzeichnis `./Sources/Application/` | Beschreibung  |
|:------------------------------------------------|:------------------------------------------|
| `./Sources/Application/Application.swift` | Swift-Anwendungsdatei |
| `./Sources/<projectname>/main.swift` | Swift-Hauptdatei |
{: caption="Tabelle 2. Inhalt des Verzeichnisses /Sources/Application/ einer generierten Swift-App" caption-side="top"}

| Verzeichnis `./test/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
|test-server.js | Dienstprogrammmethoden für das Testen mit Kitura |
{: caption="Tabelle 3. Inhalt des Testverzeichnisses einer generierten Swift-App" caption-side="top"}

| Verzeichnis `./Tests/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| `./Tests/LinuxMain.swift` | Dienstprogramm für das Testen unter Linux |
| `./Tests/ApplicationTests>/RouteTests.swift` | Datei mit Testfällen |
{: caption="Tabelle 4. Inhalt des Testverzeichnisses einer generierten Swift-App" caption-side="top"}

| Verzeichnis `./.bluemix/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Container-Build-Script |
| deploy.json | Bereitstellungsinformationen |
| kube_deploy.sh | Kubernetes-Bereitstellungsscript |
| pipeline.yml | IBM Cloud-Pipelinedefinition |
| toolchain.yml | IBM Cloud-Toolchaindefinition |
{: caption="Tabelle 5. Inhalt des Bluemix-Verzeichnisses einer generierten Swift-App" caption-side="top"}

| Verzeichnis `./chart/<projectname>/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm-Diagramm |
| `./chart/<projectname>/values.yaml` | Helm-Diagrammwerte |
| `./chart/<projectname>/templates/deployment.yaml` | Bereitstellungsvorlage |
| `./chart/<projectname>/templates/service.yaml` | Servicevorlage |
{: caption="Tabelle 6. Inhalt des Diagrammverzeichnisses einer generierten Swift-App" caption-side="top"}

| Verzeichnis `./manifests/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Kubernetes-Service & Bereitstellungs-YAML |
{: caption="Tabelle 7. Inhalt des Manifestverzeichnisses einer generierten Swift-App" caption-side="top"}

