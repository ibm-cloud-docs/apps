---

copyright:
  years: 2015, 2018
lastupdated: "2018-10-05"

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Java app files
{: #java-project-files}

For Java apps, the following information is an inventory of what you typically find in {{site.data.keyword.Bluemix}}. When you create a starter kit, these files are created for you. If you're migrating an app to host in {{site.data.keyword.Bluemix_notm}}, you might want to review this information to avoid potential conflicts.
{:shortdesc}

## Spring
{: #spring-project-files}

The following table lists the directories and files that are included in a generated Java Spring app.

| `./` directory                                  | Description                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | The maven pom file |
| cli-config.yml | CLI configuration options |
| manifest.yml | Cloud Foundry deployment file |
| Dockerfile | Dockerfile for `ibmcloud dev run`, `ibmcloud dev deploy`, and `docker` commands |
| Dockerfile-tools | Dockerfile for `ibmcloud dev build` and `ibmcloud dev test` |
| LICENSE | License file |
| README.md | Description of app |
{: caption="Table 1. Contents of a generated Java Spring app root directory" caption-side="top"}

| `./src/main/java/` directory | Description                       |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/test/application/SBApplication.java` | The main Spring Application |
| `./src/main/test/application/HealthEndpointTest.java` | Tests |
| `./src/main/java/application/rest/HealthApplication.java` | Health endpoint |
| `./src/main/java/application/rest/v1/Example.java` | The example code |
| `./src/main/java/resources/application-local.properties` | Spring properties |
{: caption="Table 2. Contents of a generated Java Spring app /java/ directory" caption-side="top"}

| `./.bluemix/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Container build script |
| deploy.json | Deployment information |
| kube_deploy.sh | Kubernetes deployment script |
| pipeline.yml | IBM Cloud pipeline definition |
| toolchain.yml | IBM Cloud toolchain definition |
{: caption="Table 3. Contents of a generated Java Spring app ./.bluemix/ directory" caption-side="top"}

| `./chart/<projectname>/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm chart |
| `./chart/<projectname>/values.yaml` | Helm chart values |
| `./chart/<projectname>/templates/deployment.yaml` | Deployment template |
| `./chart/<projectname>/templates/hpa.yaml` | HPA template |
| `./chart/<projectname>/templates/service.yaml` | Service template |
{: caption="Table 4. Contents of a generated Java Spring app ./chart/<projectname>/templates/ directory" caption-side="top"}

| `./manifests/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Kubernetes Service & Deployment yaml |
{: caption="Table 5. Contents of a generated Java Spring app ./manifests/ directory" caption-side="top"}

## Liberty
{: #liberty-project-files}

The following table lists the directories and files that are included in a generated Java Liberty app.

| `./` directory                                  | Description                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | The maven pom file |
| cli-config.yml | CLI configuration options |
| manifest.yml | Cloud Foundry deployment file |
| Dockerfile | Dockerfile for `ibmcloud dev run`, `ibmcloud dev deploy`, and `docker` commands |
| `Dockerfile-tools` | Dockerfile for `ibmcloud dev build` and `ibmcloud dev test` commands |
| LICENSE | License file |
| README.md | Description of app |
{: caption="Table 6. Contents of a generated Java Liberty app root directory" caption-side="top"}

| `./src/main` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/java/application/rest/HealthApplication.java` | Health endpoint |
| `./src/main/java/application/rest/v1/Example.java` | The example code |
| `./src/main/liberty/config/jvm.options` | JVM options |
| `./src/main/liberty/config/jvmbx.options` | Java metrics agent config |
| `./src/main/liberty/config/server.env` | Environment variables |
| `./src/main/liberty/config/server.xml` | Server config |
| `./src/main/webapp/WEB-INF/beans.xml` | CDI bean config |
| `./src/main/webapp/WEB-INF/ibm-web-ext.xml` | IBM web app config |
| `./src/main/test/it/HealthEndpointTest.java` | Tests |
{: caption="Table 7. Contents of a generated Java Liberty app ./src/main/ directory" caption-side="top"}

| `./.bluemix/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Container build script |
| deploy.json | Deployment information |
| kube_deploy.sh | Kubernetes deployment script |
| pipeline.yml | IBM Cloud pipeline definition |
| toolchain.yml | IBM Cloud toolchain definition |
{: caption="Table 8. Contents of a generated Java Liberty app ./bluemix/ directory" caption-side="top"}

| `./chart/<projectname>/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Helm chart |
| `./chart/<projectname>/values.yaml` | Helm chart values |
| `./chart/<projectname>/templates/deployment.yaml` | Deployment template |
| `./chart/<projectname>/templates/hpa.yaml` | HPA template |
| `./chart/<projectname>/templates/service.yaml` | Service template |
{: caption="Table 9. Contents of a generated Java Liberty app ./chart/<projectname>/ directory" caption-side="top"}

| `./manifests/` directory | Description |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | Kubernetes Service & Deployment yaml |
{: caption="Table 10. Contents of a generated Java Liberty app ./manifests/ directory" caption-side="top"}
