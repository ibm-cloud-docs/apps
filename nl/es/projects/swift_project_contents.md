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

# Archivos de la app Swift
{: #swift-project-files}

Para las apps Swift, la siguiente información es un inventario de lo que normalmente se encuentra en {{site.data.keyword.Bluemix}}. Cuando se crea un kit de iniciación, estos archivos se crean en su nombre. Si está migrando una app para alojarla en {{site.data.keyword.Bluemix_notm}}, es posible que desee revisar esta información para evitar posibles conflictos. 
{:shortdesc}

En la siguiente tabla se muestra una lista de archivos y directorios comunes que se incluyen en una app Swift generada.

| Directorio Root                                     | Descripción |
|:------------------------------------------------|:------------------------------------------|
| Package.swift| Archivo de definición de dependencias de Swift |
| cli-config.yml | Opciones de configuración de CLI |
| manifest.yml | Archivo de despliegue de Cloud Foundry |
| Dockerfile | Archivo Dockerfile para mandatos `ibmcloud dev run`, `ibmcloud dev deploy` y `docker` |
| `Dockerfile-tools` | Dockerfile para `ibmcloud dev build` e `ibmcloud dev test` |
| LICENSE | Archivo de licencia |
| README.md | Descripción de la app |
{: caption="Tabla 1. Contenido de un directorio raíz de app Swift generado" caption-side="top"}

| Directorio `./Sources/Application/` | Descripción  |
|:------------------------------------------------|:------------------------------------------|
| `./Sources/Application/Application.swift` | Archivo application Swift |
| `./Sources/<projectname>/main.swift` | Archivo main Swift |
{: caption="Tabla 2. Contenido de un directorio /Sources/Application/ de app Swift generado" caption-side="top"}

| Directorio `./test/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
|test-server.js | Métodos de programa de utilidad para la realización de pruebas con Kitura |
{: caption="Tabla 3. Contenido de un directorio de prueba de app Swift generado" caption-side="top"}

| Directorio `./Tests/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| `./Tests/LinuxMain.swift` | Programa de utilidad para la realización de pruebas en Linux |
| `./Tests/ApplicationTests>/RouteTests.swift` | Archivo que incluye casos de prueba |
{: caption="Tabla 4. Contenido de un directorio de pruebas de app Swift generado" caption-side="top"}

| Directorio `./.bluemix/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de compilación del contenedor |
| deploy.json | Información de despliegue |
| kube_deploy.sh | Script de despliegue de Kubernetes |
| pipeline.yml | Definición de conducto de IBM Cloud |
| toolchain.yml | Definición de cadena de herramientas de IBM Cloud |
{: caption="Tabla 5. Contenido de un directorio bluemix de app Swift generado" caption-side="top"}

| Directorio `./chart/<projectname>/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Diagrama Helm |
| `./chart/<projectname>/values.yaml` | Valores de diagrama Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Plantilla de despliegue |
| `./chart/<projectname>/templates/service.yaml` | Plantilla de servicio |
{: caption="Tabla 6. Contenido de un directorio de gráfica de app Swift generado" caption-side="top"}

| Directorio `./manifests/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| kube.deploy.yml | yaml de despliegue y servicio de Kubernetes |
{: caption="Tabla 7. Contenido de un directorio de manifests generado" caption-side="top"}

