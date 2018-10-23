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

# Archivos de la app Java
{: #java-project-files}

Para las apps Java, la siguiente información es un inventario de lo que normalmente se encuentra en {{site.data.keyword.Bluemix}}. Cuando se crea un kit de inicio, estos archivos se crean en su nombre. Si está migrando una app para alojarla en {{site.data.keyword.Bluemix_notm}}, es posible que desee revisar esta información para evitar posibles conflictos.
{:shortdesc}

## Spring
{: #spring-project-files}

En la siguiente tabla se muestra una lista de los directorios y archivos que se incluyen en una app Java Spring.

| Directorio `./`                                  | Descripción                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | Archivo pom de maven |
| cli-config.yml | Opciones de configuración de CLI |
| manifest.yml | Archivo de despliegue de Cloud Foundry |
| Dockerfile | Archivo Dockerfile para mandatos `ibmcloud dev run`, `ibmcloud dev deploy` y `docker` |
| Dockerfile-tools | Dockerfile para `ibmcloud dev build` e `ibmcloud dev test` |
| LICENSE | Archivo de licencia |
| README.md | Descripción de la app |
{: caption="Tabla 1. Contenido de un directorio raíz de app Java Spring generado" caption-side="top"}

| Directorio `./src/main/java/` | Descripción                       |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/test/application/SBApplication.java` | Aplicación principal Spring |
| `./src/main/test/application/HealthEndpointTest.java` | Pruebas |
| `./src/main/java/application/rest/HealthApplication.java` | Punto final de salud |
| `./src/main/java/application/rest/v1/Example.java` | Código de ejemplo |
| `./src/main/java/resources/application-local.properties` | Propiedades de Spring |
{: caption="Tabla 2. Contenido de un directorio /java/ de app Java Spring generado" caption-side="top"}

| Directorio `./.bluemix/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de compilación del contenedor |
| deploy.json | Información de despliegue |
| kube_deploy.sh | Script de despliegue de Kubernetes |
| pipeline.yml | Definición de conducto de IBM Cloud |
| toolchain.yml | Definición de cadena de herramientas de IBM Cloud |
{: caption="Tabla 3. Contenido de un directorio ./.bluemix/ de app Java Spring generado" caption-side="top"}

| Directorio `./chart/<projectname>/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Diagrama Helm |
| `./chart/<projectname>/values.yaml` | Valores de diagrama Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Plantilla de despliegue |
| `./chart/<projectname>/templates/hpa.yaml` | Plantilla HPA |
| `./chart/<projectname>/templates/service.yaml` | Plantilla de servicio |
{: caption="Tabla 4. Contenido de un directorio ./chart/<projectname/templates/ de app Java Spring generado" caption-side="top"}>

| Directorio `./manifests/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | yaml de despliegue y servicio de Kubernetes |
{: caption="Tabla 5. Contenido de un directorio ./manifests/ de app Java Spring generado" caption-side="top"}

## Liberty
{: #liberty-project-files}

La tabla siguiente lista los directorios y archivos incluidos en una app Java Liberty generada.

| Directorio `./`                                  | Descripción                       |
|:------------------------------------------------|:------------------------------------------|
| pom.xml | Archivo pom de maven |
| cli-config.yml | Opciones de configuración de CLI |
| manifest.yml | Archivo de despliegue de Cloud Foundry |
| Dockerfile | Archivo Dockerfile para mandatos `ibmcloud dev run`, `ibmcloud dev deploy` y `docker` |
| `Dockerfile-tools` | Dockerfile para mandatos `ibmcloud dev build` e `ibmcloud dev test` |
| LICENSE | Archivo de licencia |
| README.md | Descripción de la app |
{: caption="Tabla 6. Contenido de un directorio raíz de app Java Liberty generado" caption-side="top"}

| Directorio `./src/main` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| `./src/main/java/application/rest/HealthApplication.java` | Punto final de salud |
| `./src/main/java/application/rest/v1/Example.java` | Código de ejemplo |
| `./src/main/liberty/config/jvm.options` | Opciones de JVM |
| `./src/main/liberty/config/jvmbx.options` | Configuración del agente de métricas de Java |
| `./src/main/liberty/config/server.env` | Variables de entorno |
| `./src/main/liberty/config/server.xml` | Configuración de servidor |
| `./src/main/webapp/WEB-INF/beans.xml` | Configuración del bean de CDI |
| `./src/main/webapp/WEB-INF/ibm-web-ext.xml` | Configuración de app web de IBM |
| `./src/main/test/it/HealthEndpointTest.java` | Pruebas |
{: caption="Tabla 7. Contenido de un directorio ./src/main/ de app Java Liberty generado" caption-side="top"}

| Directorio `./.bluemix/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de compilación del contenedor |
| deploy.json | Información de despliegue |
| kube_deploy.sh | Script de despliegue de Kubernetes |
| pipeline.yml | Definición de conducto de IBM Cloud |
| toolchain.yml | Definición de cadena de herramientas de IBM Cloud |
{: caption="Tabla 8. Contenido de un directorio ./bluemix/ de app Java Liberty generado" caption-side="top"}

| Directorio `./chart/<projectname>/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Diagrama Helm |
| `./chart/<projectname>/values.yaml` | Valores de diagrama Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Plantilla de despliegue |
| `./chart/<projectname>/templates/hpa.yaml` | Plantilla HPA |
| `./chart/<projectname>/templates/service.yaml` | Plantilla de servicio |
{: caption="Tabla 9. Contenido de un directorio ./chart/<projectname/ de app Java Liberty generado" caption-side="top"}>

| Directorio `./manifests/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | yaml de despliegue y servicio de Kubernetes |
{: caption="Tabla 10. Contenido de un directorio ./manifests/ de app Java Liberty generado" caption-side="top"}
