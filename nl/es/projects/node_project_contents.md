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

# Archivos de la app Node.js
{: #node-project-files}

Para las apps Node.js, la siguiente información es un inventario de lo que normalmente se encuentra en {{site.data.keyword.Bluemix}}. Cuando se crea un kit de inicio, estos archivos se crean en su nombre. Si está migrando una app para alojarla en {{site.data.keyword.Bluemix_notm}}, es posible que desee revisar esta información para evitar posibles conflictos. 
{:shortdesc}

En la siguiente tabla se muestra una lista de archivos y directorios comunes que se incluyen en una app Node.js generada.

| Directorio Root                                     | Descripción                       |
|:------------------------------------------------|:------------------------------------------|
|package.json | Información de metadatos sobre el paquete que incluye el nombre, la versión y las dependencias. |
|cli-config.yml | Opciones de configuración de CLI |
|manifest.yml | Archivo de despliegue de Cloud Foundry |
|Dockerfile | Archivo Dockerfile para mandatos `ibmcloud dev run`, `ibmcloud dev deploy` y `docker` |
|Dockerfile-tools | Dockerfile para `ibmcloud dev build` e `ibmcloud dev test` |
|docker-compose.yml | Configuración de servicio app para Docker Compose |
|webpack.config.js | Configuración de webpack para información relacionada con la compilación |
| LICENSE | Archivo de licencia |
|README.md | Descripción de la app |
{: caption="Tabla 1. Contenido de un directorio raíz de app Node.js generado" caption-side="top"}

| Directorio `./public/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| `./public/swagger.yml` | Especificación swagger para describir las API REST |
| `./public/index.html` | Esquema para aplicaciones web |
|`./public/server/server.js` | Archivo de implementación de servidor |
{: caption="Tabla 2. Contenido de un directorio público de app Node.js generado" caption-side="top"}

| Directorio `./test/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| test-server.js | Prueba de integración para servidor Express |
{: caption="Tabla 3. Contenido de un directorio de prueba de app Node.js generado" caption-side="top"}

| Directorio `./.bluemix/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de compilación del contenedor |
| deploy.json | Información de despliegue |
| kube_deploy.sh | Script de despliegue de Kubernetes |
| pipeline.yml | Definición de conducto de IBM Cloud |
| toolchain.yml | Definición de cadena de herramientas de IBM Cloud |
{: caption="Tabla 4. Contenido de un directorio bluemix de app Node.js generado" caption-side="top"}

| Directorio `./chart/<projectname>/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Diagrama Helm |
| `./chart/<projectname>/values.yaml` | Valores de diagrama Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Plantilla de despliegue |
| `./chart/<projectname>/templates/service.yaml` | Plantilla de servicio |
{: caption="Tabla 5. Contenido de un directorio de gráfica de app Node.js generado" caption-side="top"}
