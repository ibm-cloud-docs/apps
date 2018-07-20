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

# File applicazione Python
{: #python-project-files}

Per le applicazioni Python, le seguenti informazioni sono un inventario di quello che normalmente trovi in {{site.data.keyword.Bluemix}}. Quando crei un kit starter, questi file sono creati per te. Se stai migrando un'applicazione per essere ospitata in {{site.data.keyword.Bluemix_notm}}, potresti voler esaminare queste informazioni per evitare potenziali conflitti.
{:shortdesc}

La seguente tabella elenca le directory e i file comuni che sono inclusi in un'applicazione Python generata.

| Directory root                                     | Descrizione                       |
|:------------------------------------------------|:------------------------------------------|
| requirements.txt | Pacchetti Python richiesti |
| setup.py | Script di installazione Python |
| cli-config.yml | Opzioni di configurazione della CLI |
| manifest.yml | File di distribuzione Cloud Foundry |
| Dockerfile | Dockerfile per i comandi `ibmcloud dev run`, `ibmcloud dev deploy` e `docker` |
| Dockerfile-tools | Dockerfile per `ibmcloud dev build` e `ibmcloud dev test` |
| LICENSE | File di licenza |
| README.md | Descrizione dell'applicazione |
{: caption="Tabella 1. Contenuto della directory root di un'applicazione Python generata" caption-side="top"}

| Directory `./public/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| swagger.yml | Specifica Swagger per descrivere l'API REST |
| index.html | Markup Skeleton per le applicazioni web |
{: caption="Tabella 2. Contenuto della directory pubblica di un'applicazione Python generata" caption-side="top"}

| Directory `./server/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| `__init__.py` | Contrassegna le directory come directory del pacchetto Python |
{: caption="Tabella 3. Contenuto della directory server di un'applicazione Python generata" caption-side="top"}

| Directory `./tests/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| app_tests.py | Scenari di test del server Python |
{: caption="Tabella 4. Contenuto della directory di test di un'applicazione Python generata" caption-side="top"}

| Directory `./.bluemix/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script di build del contenitore |
| deploy.json | Informazioni sulla distribuzione |
| kube_deploy.sh | Script di distribuzione Kubernetes |
| pipeline.yml | Definizione della pipeline IBM Cloud |
| toolchain.yml | Definizione della toolchain IBM Cloud toolchain |
{: caption="Tabella 5. Contenuto della directory bluemix di un'applicazione Python generata" caption-side="top"}

| `./chart/<projectname>/` directory | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Grafico Helm |
| `./chart/<projectname>/values.yaml` | Valori grafico Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Template distribuzione |
| `./chart/<projectname>/templates/service.yaml` | Template del servizio |
{: caption="Tabella 6. Contenuto della directory di grafici di un'applicazione Python generata" caption-side="top"}
