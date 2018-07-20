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

# File applicazione Java
{: #java-project-files}

Per le applicazioni Java, le seguenti informazioni sono un inventario di quello che normalmente trovi in {{site.data.keyword.Bluemix}}. Quando crei un kit starter, questi file sono creati per te. Se stai migrando un'applicazione per essere ospitata in {{site.data.keyword.Bluemix_notm}}, potresti voler esaminare queste informazioni per evitare potenziali conflitti.
{:shortdesc}

## Spring
{: #spring-project-files}

La seguente tabella elenca le directory e i file che sono inclusi in un'applicazione Java Spring generata.

| Directory `./`                                  | Descrizione                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | Il file pom maven |
| cli-config.yml | Opzioni di configurazione della CLI |
| manifest.yml | File di distribuzione Cloud Foundry |
| Dockerfile | Dockerfile per i comandi `ibmcloud dev run`, `ibmcloud dev deploy` e `docker` |
| Dockerfile-tools | Dockerfile per `ibmcloud dev build` e `ibmcloud dev test` |
| LICENSE | File di licenza |
| README.md | Descrizione dell'applicazione |
{: caption="Tabella 1. Contenuto della directory root di un'applicazione Java Spring generata" caption-side="top"}

| Directory `./src/main/java/` | Descrizione                       |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/test/application/SBApplication.java` | L'applicazione Spring principale |
| `./src/main/test/application/HealthEndpointTest.java` | Test |
| `./src/main/java/application/rest/HealthApplication.java` | Endpoint integrità |
| `./src/main/java/application/rest/v1/Example.java` | Il codice di esempio |
| `./src/main/java/resources/application-local.properties` | Proprietà Spring |
{: caption="Tabella 2. Contenuto della directory /java/ di un'applicazione Java Spring generata" caption-side="top"}

| Directory `./.bluemix/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script di build del contenitore |
| deploy.json | Informazioni sulla distribuzione |
| kube_deploy.sh | Script di distribuzione Kubernetes |
| pipeline.yml | Definizione della pipeline IBM Cloud |
| toolchain.yml | Definizione della toolchain IBM Cloud toolchain |
{: caption="Tabella 3. Contenuto della directory ./.bluemix/ di un'applicazione Java Spring generata" caption-side="top"}

| `./chart/<projectname>/` directory | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Grafico Helm |
| `./chart/<projectname>/values.yaml` | Valori grafico Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Template distribuzione |
| `./chart/<projectname>/templates/hpa.yaml` | Template HPA |
| `./chart/<projectname>/templates/service.yaml` | Template del servizio |
{: caption="Tabella 4. Contenuto della directory ./chart/<projectname/templates/ di un'applicazione Java Spring generata" caption-side="top"}>

| Directory `./manifests/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Yaml di distribuzione e del servizio Kubernetes |
{: caption="Tabella 5. Contenuto della directory ./manifests/ di un'applicazione Java Spring generata" caption-side="top"}

## Liberty
{: #liberty-project-files}

La seguente tabella elenca le directory e i file che sono inclusi in un'applicazione Java Liberty generata.

| Directory `./`                                  | Descrizione                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | Il file pom maven |
| cli-config.yml | Opzioni di configurazione della CLI |
| manifest.yml | File di distribuzione Cloud Foundry |
| Dockerfile | Dockerfile per i comandi `ibmcloud dev run`, `ibmcloud dev deploy` e `docker` |
| Dockerfile-tools | Dockerfile per i comandi `ibmcloud dev build` e `ibmcloud dev test` |
| LICENSE | File di licenza |
| README.md | Descrizione dell'applicazione |
{: caption="Tabella 6. Contenuto della directory root di un'applicazione Java Liberty generata" caption-side="top"}

| Directory `./src/main` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/java/application/rest/HealthApplication.java` | Endpoint integrità |
| `./src/main/java/application/rest/v1/Example.java` | Il codice di esempio |
| `./src/main/liberty/config/jvm.options` | Opzioni JVM |
| `./src/main/liberty/config/jvmbx.options` | Configurazione agente metriche Java |
| `./src/main/liberty/config/server.env` | Variabili di ambiente |
| `./src/main/liberty/config/server.xml` | Configurazione server |
| `./src/main/webapp/WEB-INF/beans.xml` | Configurazione bean CDI |
| `./src/main/webapp/WEB-INF/ibm-web-ext.xml` | Configurazione applicazione web IBM |
| `./src/main/test/it/HealthEndpointTest.java` | Test |
{: caption="Tabella 7. Contenuto della directory ./src/main/ di un'applicazione Java Liberty generata" caption-side="top"}

| Directory `./.bluemix/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script di build del contenitore |
| deploy.json | Informazioni sulla distribuzione |
| kube_deploy.sh | Script di distribuzione Kubernetes |
| pipeline.yml | Definizione della pipeline IBM Cloud |
| toolchain.yml | Definizione della toolchain IBM Cloud toolchain |
{: caption="Tabella 8. Contenuto della directory ./bluemix/ di un'applicazione Java Liberty generata" caption-side="top"}

| `./chart/<projectname>/` directory | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Grafico Helm |
| `./chart/<projectname>/values.yaml` | Valori grafico Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Template distribuzione |
| `./chart/<projectname>/templates/hpa.yaml` | Template HPA |
| `./chart/<projectname>/templates/service.yaml` | Template del servizio |
{: caption="Tabella 9. Contenuto della directory ./chart/<projectname/ di un'applicazione Java Liberty generata" caption-side="top"}>

| Directory `./manifests/` | Descrizione |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Yaml di distribuzione e del servizio Kubernetes |
{: caption="Tabella 10. Contenuto della directory ./manifests/ di un'applicazione Java Liberty generata" caption-side="top"}
