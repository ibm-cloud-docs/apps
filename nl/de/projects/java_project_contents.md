---

copyright:
  years: 2015, 2018
lastupdated: "2018-05-02"

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

| Verzeichnis und Datei                                     | Beschreibung                       |
|:------------------------------------------------|:------------------------------------------|
|**`./`**                                             |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pom.xml | Maven-POM-Datei |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;cli-config.yml | CLI-Konfigurationsoptionen |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;manifest.yml | Cloud Foundry-Bereitstellungsdatei |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Dockerfile | Dockerfile für Befehle `bx dev run`, `bx dev deploy` und `docker` |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Dockerfile-tools | Dockerfile für `bx dev build` und `bx dev test` |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;LICENSE |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;README.md | Beschreibung der App |
|**`./src/main/java/application/`** |  |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SBApplication.java | Spring-Hauptanwendung |
|**`./src/main/java/application/rest/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;HealthApplication.java | Statusendpunkt |
|**`./src/main/java/application/rest/v1/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Example.java | Beispielcode |
|**`./src/main/java/resources/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;application-local.properties | Spring-Eigenschaften |
|**`./src/main/test/application/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;HealthEndpointTest.java | Tests |
|**`./.bluemix/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;container_build.sh | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;deploy.json | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;kube_deploy.sh | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pipeline.yml | IBM Cloud-Pipelinedefinition |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;toolchain.yml | IBM Cloud-Toolchaindefinition |
|**`./chart/<projectname>/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Chart.yaml | Helm-Diagramm |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;values.yaml | Helm-Diagrammwerte |
|**`./chart/<projectname>/templates/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;deployment.yaml | Bereitstellungsvorlage |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;hpa.yaml | HPA-Vorlage |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;service.yaml | Servicevorlage |
|**`./manifests/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;kube.deploy.yml | Kubernetes-Service & Bereitstellungs-YAML |
{: caption="Tabelle 1. Inhalte einer generierten Java Spring-App" caption-side="top"}

## Liberty
{: #liberty-project-files}

In der folgenden Tabelle sind die Verzeichnisse und Dateien aufgelistet, die in einer generierten Java Liberty-App enthalten sind.

| Verzeichnis/Datei                                     | Beschreibung                       |
|:------------------------------------------------|:------------------------------------------|
|**`./`**                                             |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pom.xml | Maven-POM-Datei |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;cli-config.yml | CLI-Konfigurationsoptionen |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;manifest.yml | Cloud Foundry-Bereitstellungsdatei |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Dockerfile | Dockerfile für Befehle `bx dev run`, `bx dev deploy` und `docker` |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Dockerfile-tools | Dockerfile für Befehle `bx dev build` und `bx dev test` |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;LICENSE |  |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;README.md | Beschreibung der App |
|**`./src/main/java/application/rest/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;HealthApplication.java | Statusendpunkt |
|**`./src/main/java/application/rest/v1/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Example.java | Beispielcode |
|**`./src/main/liberty/config/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;jvm.options | JVM-Optionen |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;jvmbx.options | Konfiguration des Agenten für Java-Metriken |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;server.env | Umgebungsvariablen |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;server.xml | Serverkonfiguration |
|**`./src/main/webapp/WEB-INF/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;beans.xml | CDI-Bean-Konfiguration |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ibm-web-ext.xml | IBM Web-App-Konfiguration |
|**`./src/main/test/it/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;HealthEndpointTest.java | Tests |
|**`./.bluemix/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;container_build.sh | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;deploy.json | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;kube_deploy.sh | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pipeline.yml | IBM Cloud-Pipelinedefinition |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;toolchain.yml | IBM Cloud-Toolchaindefinition |
|**`./chart/<projectname>/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Chart.yaml | Helm-Diagramm |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;values.yaml | Helm-Diagrammwerte |
|**`./chart/<projectname>/templates/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;deployment.yaml | Bereitstellungsvorlage |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;hpa.yaml | HPA-Vorlage |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;service.yaml | Servicevorlage |
|**`./manifests/`** | |
|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;kube.deploy.yml | Kubernetes-Service & Bereitstellungs-YAML |
{: caption="Tabelle 2. Inhalte einer generierten Java Liberty-App" caption-side="top"}

