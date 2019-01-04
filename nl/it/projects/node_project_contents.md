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

# File applicazione Node.js
{: #node-project-files}

Per le applicazioni Node.js, le seguenti informazioni sono un inventario di quello che normalmente trovi in {{site.data.keyword.Bluemix}}. Quando crei un kit starter, questi file sono creati per te. Se stai migrando un'applicazione per essere ospitata in {{site.data.keyword.Bluemix_notm}}, potresti voler esaminare queste informazioni per evitare potenziali conflitti. 
{:shortdesc}

La seguente tabella elenca le directory e i file comuni che sono inclusi in un'applicazione Node.js generata.

| Directory root                                     | Descrizione                       |
|:------------------------------------------------|:------------------------------------------|
|package.json | Informazioni sui metadati relative al pacchetto, compresi il nome, la versione e le dipendenze. |
|cli-config.yml | Opzioni di configurazione della CLI |
|manifest.yml | File di distribuzione Cloud Foundry |
|Dockerfile | Dockerfile per i comandi `ibmcloud dev run`, `ibmcloud dev deploy` e `docker` |
|Dockerfile-tools | Dockerfile per `ibmcloud dev build` e `ibmcloud dev test` |
|docker-compose.yml | Configurazione del servizio dell'applicazione per Docker Compose |
|webpack.config.js | Configurazione del pacchetto web per le informazioni correlate alla build |
| LICENSE | File di licenza |
|README.md | Descrizione dell'applicazione |
{: caption="Tabella 1. Contenuto della directory root di un'applicazione Node.js generata" caption-side="top"}

| Directory `./public/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| `./public/swagger.yml` | Specifica Swagger per descrivere l'API REST |
| `./public/index.html` | Markup Skeleton per le applicazioni web |
|`./public/server/server.js` | File di implementazione del server |
{: caption="Tabella 2. Contenuto della directory pubblica di un'applicazione Node.js generata" caption-side="top"}

| Directory `./test/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| test-server.js | Test di integrazione per il server Express |
{: caption="Tabella 3. Contenuto della directory di test di un'applicazione Node.js generata" caption-side="top"}

| Directory `./.bluemix/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script di build del contenitore |
| deploy.json | Informazioni sulla distribuzione |
| kube_deploy.sh | Script di distribuzione Kubernetes |
| pipeline.yml | Definizione della pipeline IBM Cloud |
| toolchain.yml | Definizione della toolchain IBM Cloud toolchain |
{: caption="Tabella 4. Contenuto della directory bluemix di un'applicazione Node.js generata" caption-side="top"}

| `./chart/<projectname>/` directory | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Grafico Helm |
| `./chart/<projectname>/values.yaml` | Valori grafico Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Template distribuzione |
| `./chart/<projectname>/templates/service.yaml` | Template del servizio |
{: caption="Tabella 5. Contenuto della directory di grafici di un'applicazione Node.js generata" caption-side="top"}
