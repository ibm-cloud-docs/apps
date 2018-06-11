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

# Java-App-Dateien
{: #java-project-files}

Für Java-Apps stellen die folgenden Informationen einen Bestand der Komponenten dar, die Sie typischerweise in {{site.data.keyword.Bluemix}} finden. Wenn Sie ein Starter-Kit erstellen, werden diese Dateien für Sie erstellt. Wenn Sie eine App migrieren, um sie in {{site.data.keyword.Bluemix_notm}} zu hosten, sollten Sie diese Informationen durchlesen, um potenzielle Konflikte zu vermeiden. 
{:shortdesc}

## Spring
{: #spring-project-files}

In der folgenden Tabelle sind die Verzeichnisse und Dateien aufgelistet, die in einer generierten Java Spring-App enthalten sind.

| Verzeichnis `./`                                  | Beschreibung                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | Maven-POM-Datei |
| cli-config.yml | CLI-Konfigurationsoptionen |
| manifest.yml | Cloud Foundry-Bereitstellungsdatei |
| Dockerfile |Dockerfile für Befehle `ibmcloud dev run`, `ibmcloud dev deploy` und `docker` |
| Dockerfile-tools | Dockerfile für `ibmcloud dev build` und `ibmcloud dev test` |
| LICENSE | Lizenzdatei |
| README.md | Beschreibung der App |
{: caption="Tabelle 1. Inhalt des Stammverzeichnisses einer generierten Java Spring-App" caption-side="top"}

| Verzeichnis `./src/main/java/` | Beschreibung                       |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/test/application/SBApplication.java` | Spring-Hauptanwendung |
| `./src/main/test/application/HealthEndpointTest.java` | Tests |
| `./src/main/java/application/rest/HealthApplication.java` | Statusendpunkt |
| `./src/main/java/application/rest/v1/Example.java` | Beispielcode |
| `./src/main/java/resources/application-local.properties` | Spring-Eigenschaften |
{: caption="Tabelle 2. Inhalt des Verzeichnisses /java/ einer generierten Java Spring-App" caption-side="top"}

| Verzeichnis `./.bluemix/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Container-Build-Script |
| deploy.json | Bereitstellungsinformationen |
| kube_deploy.sh | Kubernetes-Bereitstellungsscript |
| pipeline.yml | IBM Cloud-Pipelinedefinition |
| toolchain.yml | IBM Cloud-Toolchaindefinition |
{: caption="Tabelle 3. Inhalt des Verzeichnisses ./.bluemix/ einer generierten Java Spring-App" caption-side="top"}

| Verzeichnis `./chart/<projectname>/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm-Diagramm |
| `./chart/<projectname>/values.yaml` | Helm-Diagrammwerte |
| `./chart/<projectname>/templates/deployment.yaml` | Bereitstellungsvorlage |
| `./chart/<projectname>/templates/hpa.yaml` | HPA-Vorlage |
| `./chart/<projectname>/templates/service.yaml` | Servicevorlage |
{: caption="Tabelle 4. Inhalt des Verzeichnisses ./chart/<projectname/templates/ einer generierten Java Spring-App" caption-side="top"}>

| Verzeichnis `./manifests/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Kubernetes-Service & Bereitstellungs-YAML |
{: caption="Tabelle 5. Inhalt des Verzeichnisses ./manifests/ einer generierten Java Spring-App" caption-side="top"}

## Liberty
{: #liberty-project-files}

In der folgenden Tabelle sind die Verzeichnisse und Dateien aufgelistet, die in einer generierten Java Liberty-App enthalten sind.

| Verzeichnis `./`                                  | Beschreibung                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | Maven-POM-Datei |
| cli-config.yml | CLI-Konfigurationsoptionen |
| manifest.yml | Cloud Foundry-Bereitstellungsdatei |
| Dockerfile |Dockerfile für Befehle `ibmcloud dev run`, `ibmcloud dev deploy` und `docker` |
| Dockerfile-tools | Dockerfile für Befehle `ibmcloud dev build` und `ibmcloud dev test` |
| LICENSE | Lizenzdatei |
| README.md | Beschreibung der App |
{: caption="Tabelle 6. Inhalt des Stammverzeichnisses einer generierten Java Liberty-App" caption-side="top"}

| Verzeichnis `./src/main` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/java/application/rest/HealthApplication.java` | Statusendpunkt |
| `./src/main/java/application/rest/v1/Example.java` | Beispielcode |
| `./src/main/liberty/config/jvm.options` | JVM-Optionen |
| `./src/main/liberty/config/jvmbx.options` | Konfiguration des Agenten für Java-Metriken |
| `./src/main/liberty/config/server.env` | Umgebungsvariablen |
| `./src/main/liberty/config/server.xml` | Serverkonfiguration |
| `./src/main/webapp/WEB-INF/beans.xml` | CDI-Bean-Konfiguration |
| `./src/main/webapp/WEB-INF/ibm-web-ext.xml` | IBM Web-App-Konfiguration |
| `./src/main/test/it/HealthEndpointTest.java` | Tests |
{: caption="Tabelle 7. Inhalt des Verzeichnisses ./src/main/ einer generierten Java Liberty-App" caption-side="top"}

| Verzeichnis `./.bluemix/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Container-Build-Script |
| deploy.json | Bereitstellungsinformationen |
| kube_deploy.sh | Kubernetes-Bereitstellungsscript |
| pipeline.yml | IBM Cloud-Pipelinedefinition |
| toolchain.yml | IBM Cloud-Toolchaindefinition |
{: caption="Tabelle 8. Inhalt des Verzeichnisses ./bluemix/ einer generierten Java Liberty-App" caption-side="top"}

| Verzeichnis `./chart/<projectname>/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm-Diagramm |
| `./chart/<projectname>/values.yaml` | Helm-Diagrammwerte |
| `./chart/<projectname>/templates/deployment.yaml` | Bereitstellungsvorlage |
| `./chart/<projectname>/templates/hpa.yaml` | HPA-Vorlage |
| `./chart/<projectname>/templates/service.yaml` | Servicevorlage |
{: caption="Tabelle 9. Inhalt des Verzeichnisses ./chart/<projectname/ einer generierten Java Liberty-App" caption-side="top"}>

| Verzeichnis `./manifests/` | Beschreibung |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Kubernetes-Service & Bereitstellungs-YAML |
{: caption="Tabelle 10. Inhalt des Verzeichnisses ./manifests/ einer generierten Java Liberty-App" caption-side="top"}
