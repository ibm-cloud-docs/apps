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

# Archivos de app de Python
{: #python-project-files}

Para las apps Python, la siguiente información es un inventario de lo que normalmente se encuentra en {{site.data.keyword.Bluemix}}. Cuando se crea un kit de iniciación, estos archivos se crean en su nombre. Si está migrando una app para alojarla en {{site.data.keyword.Bluemix_notm}}, es posible que desee revisar esta información para evitar posibles conflictos.
{:shortdesc}

En la siguiente tabla se muestra una lista de archivos y directorios comunes que se incluyen en una app Python generada.

| Directorio Root                                     | Descripción                       |
|:------------------------------------------------|:------------------------------------------|
| requirements.txt | Paquetes Python necesarios |
| setup.py | Script de instalador de Python |
| cli-config.yml | Opciones de configuración de CLI |
| manifest.yml | Archivo de despliegue de Cloud Foundry |
| Dockerfile | Archivo Dockerfile para mandatos `ibmcloud dev run`, `ibmcloud dev deploy` y `docker` |
| Dockerfile-tools | Dockerfile para `ibmcloud dev build` e `ibmcloud dev test` |
| LICENSE | Archivo de licencia |
| README.md | Descripción de la app |
{: caption="Tabla 1. Contenido de un directorio raíz de app Python generado" caption-side="top"}

| Directorio `./public/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| swagger.yml | Especificación swagger para describir las API REST |
| index.html | Esquema para aplicaciones web |
{: caption="Tabla 2. Contenido de un directorio público de app Python generado" caption-side="top"}

| Directorio `./server/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| `__init__.py` | Marca directorios como directorios de paquetes de Python |
{: caption="Tabla 3. Contenido de un directorio de servidor de app Python generado" caption-side="top"}

| Directorio `./tests/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| app_tests.py | Casos de prueba de servidor de Python |
{: caption="Tabla 4. Contenido de un directorio de pruebas de app Python generado" caption-side="top"}

| Directorio `./.bluemix/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| container_build.sh | Script de compilación del contenedor |
| deploy.json | Información de despliegue |
| kube_deploy.sh | Script de despliegue de Kubernetes |
| pipeline.yml | Definición de conducto de IBM Cloud |
| toolchain.yml | Definición de cadena de herramientas de IBM Cloud |
{: caption="Tabla 5. Contenido de un directorio bluemix de app Python generado" caption-side="top"}

| Directorio `./chart/<projectname>/` | Descripción |
|:------------------------------------------------|:------------------------------------------|
| `./chart/<projectname>/Chart.yaml` | Diagrama Helm |
| `./chart/<projectname>/values.yaml` | Valores de diagrama Helm |
| `./chart/<projectname>/templates/deployment.yaml` | Plantilla de despliegue |
| `./chart/<projectname>/templates/service.yaml` | Plantilla de servicio |
{: caption="Tabla 6. Contenido de un directorio de gráfica de app Python generado" caption-side="top"}
