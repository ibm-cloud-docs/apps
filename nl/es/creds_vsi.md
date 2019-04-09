---

copyright:
  years: 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Adición de credenciales a la instancia virtual o al entorno de docker local
{: #add_credentials}

Aprenda a añadir credenciales de servicio a la instancia de servidor virtual o al entorno de despliegue de docker local.
{: shortdesc}

## Su código + Instancia de servidor virtual o docker local
{: #byoc_vsi}

Bajo VSI o docker local, el entorno es totalmente suyo. Por ejemplo, puede escribir su código como el del siguiente ejemplo y proporcionar el valor de entorno de credencial a la aplicación cuando la ejecute. 
```
password = getEnvironment('password');
```
{: codeblock}

En Bash, puede escribir su código como el del siguiente ejemplo: 
```bash
export password="someThingSensitive"
# run app locally.  If node, something like:
npm run start
```
{: codeblock}

En Docker, puede escribir su código como el del siguiente ejemplo: 
```
docker run -p 80:8080 -e password="someThingSensitive"
```
{: codeblock}

## Kit de inicio + VSI (o Docker local)
{: #sk_vsi}

### Cómo se prepara la instancia de servidor virtual

El entorno está totalmente bajo su control, como si ejecutara la aplicación desde su portátil. Es decir, Docker local. Puesto que VSI es realmente nativo desde la perspectiva de la aplicación en ejecución, no existe ningún _secreto_ (como en Kubernetes) ni _servicio_
(como en Cloud Foundry).

### El código generado por el kit de inicio

El código que se genera a partir de un kit de inicio tiene la biblioteca `IBMCloudEnv` nativa, que sintetiza la recuperación de valores de entorno de modo que el código de la aplicación sea portátil y se pueda ejecutar en varios despliegues de destino. Con Docker virtual o local, este entorno debe estar preparado con valores que satisfagan la biblioteca de `IBMCloudEnv` que _no necesariamente_ procede de las variables de entorno reales.

Para su comodidad, las instrucciones de `mappings.json` que se incluyen con la salida generada por el kit de inicio tienen referencias a un archivo local desde el que la biblioteca de `IBMCloudEnv` toma los valores que puede utilizar la aplicación. 

Por ejemplo, observe la última línea de la sección siguiente del archivo `mappings.json`:
```json
"cloudant_apikey": {
  "searchPatterns": [
    "user-provided:blarg-cloudant-1538408663553:apikey",
    "cloudfoundry:$['cloudant'][0].credentials.apikey",
    "env:service_cloudant:$.apikey",
    "env:cloudant_apikey",
    "file:/server/localdev-config.json:$.cloudant_apikey"
  ]
},
```
{: codeblock}

Si utiliza la característica "Desplegar en la nube" cuando crea una app, el archivo `/server/localdev-config.json` se elimina del repositorio de GitLab. Por motivos de seguridad, no desea colocar sus credenciales en un repositorio de código fuente.

Si utiliza `git clone` en el repositorio de GitLab creado para iniciar el desarrollo activo, observe que el archivo `.gitignore` ignora específicamente `server/localdev-config.json` para ayudar a evitar la incorporación accidental de un archivo que tenga credenciales confidenciales. Sin embargo, VSI _sí_ necesita ese archivo, al igual que el desarrollador que trabaja en un portátil. 

Puede recuperar el archivo `server/localdev-config.json` siguiendo estos pasos:

1. Utilice `git clone` en el repositorio de Git lab que se ha creado automáticamente cuando ha utilizado la característica "Desplegar en la nube".
2. Instale la [CLI de {{site.data.keyword.cloud_notm}}](/docs/cli/index.html), que incluye el plugin `dev`.
3. Utilice la línea de mandatos `ibmcloud` para iniciar una sesión en {{site.data.keyword.cloud_notm}}.
4. Ejecute `ibmcloud dev get-credentials`, que hace referencia al archivo `cli-config.yml`. El archivo `cli-config.yml` incluye información sobre la aplicación y el trabajo de generación que tiene las credenciales. 

Si se elimina algún recurso de la aplicación entre el uso de la característica "Desplegar en la nube" e `ibmcloud dev get-credentials`, el archivo descargado `/server/localdev-config.json` no tiene todas las credenciales que puede necesitar el código base `git clone`.
{: tip}

Si está ejecutando la aplicación en un contenedor Docker, puede optar por eliminar el archivo `/server/localdev-config.json` por completo y pasar las variables de entorno en la línea de mandatos de Docker.

Continuando con la sección "cloudant_apikey" del archivo `mappings.json`, observe la sentencia `env:cloudant_apikey` que hay antes de la línea `file...`. Esto significa que una variable de entorno llamada `cloudant_apikey` tiene prioridad sobre el contenido del archivo. Por lo tanto, incluso si el archivo se encuentra en la imagen de Docker que ha creado (lo que no es necesario), puede sobrescribir valores pasándolos en la línea de mandatos de Docker.

Por ejemplo:
```console
docker run -p 80:8080 -e cloudant_apikey="someKeyValue"
```
{: codeblock}
