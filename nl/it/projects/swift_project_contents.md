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

# File applicazione Swift
{: #swift-project-files}

Per le applicazioni Swift, le seguenti informazioni sono un inventario di quello che normalmente trovi in {{site.data.keyword.Bluemix}}. Quando crei un kit starter, questi file sono creati per te. Se stai migrando un'applicazione per essere ospitata in {{site.data.keyword.Bluemix_notm}}, potresti voler esaminare queste informazioni per evitare potenziali conflitti. 
{:shortdesc}

La seguente tabella elenca le directory e i file comuni che sono inclusi in un'applicazione Swift generata.

| Directory root                                     | Descrizione |
|:------------------------------------------------|:------------------------------------------|
|Package.swift| File di definizione dipendenza Swift |
|cli-config.yml | Opzioni di configurazione della CLI |
|manifest.yml | File di distribuzione Cloud Foundry |
|Dockerfile | Dockerfile per i comandi `ibmcloud dev run`, `ibmcloud dev deploy` e `docker` |
|Dockerfile-tools | Dockerfile per `ibmcloud dev build` e `ibmcloud dev test` |
| LICENSE | File di licenza |
|README.md | Descrizione dell'applicazione |
{: caption="Tabella 1. Contenuto della directory root di un'applicazione Swift generata" caption-side="top"}

| Directory `./Sources/Application/` | Descrizione  |
|:------------------------------------------------|:------------------------------------------|
| `./Sources/Application/Application.swift` | Il file dell'applicazione Swift |
| `./Sources/<projectname>/main.swift` | Il file principale Swift |
{: caption="Tabella 2. Contenuto della directory /Sources/Application/ di un'applicazione Swift generata" caption-side="top"}

| Directory `./test/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
|test-server.js | Metodi del programma di utilità per la verifica con Kitura |
{: caption="Tabella 3. Contenuto della directory di test di un'applicazione Swift generata" caption-side="top"}

| Directory `./Tests/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| `./Tests/LinuxMain.swift` | Programma di utilità per la verifica su Linux |
| `./Tests/ApplicationTests>/RouteTests.swift` | File contenente gli scenari di test |
{: caption="Tabella 4. Contenuto della directory di test di un'applicazione Swift generata" caption-side="top"}

| Directory `./.bluemix/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script di build del contenitore |
| deploy.json | Informazioni sulla distribuzione|
| kube_deploy.sh | Script di distribuzione Kubernetes |
| pipeline.yml | Definizione della pipeline IBM Cloud |
| toolchain.yml | Definizione della toolchain IBM Cloud toolchain |
{: caption="Tabella 5. Contenuto della directory bluemix di un'applicazione Swift generata" caption-side="top"}

| Directory `./chart/<projectname>/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Grafico Helm |
| `./chart/<projectname>/values.yaml` | Valori grafico Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Template distribuzione |
| `./chart/<projectname>/templates/service.yaml` | Template del servizio |
{: caption="Tabella 6. Contenuto della directory di grafici di un'applicazione Swift generata" caption-side="top"}

| Directory `./manifests/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Yaml di distribuzione e del servizio Kubernetes |
{: caption="Tabella 7. Contenuto della directory manifest di un'applicazione Swift generata" caption-side="top"}

