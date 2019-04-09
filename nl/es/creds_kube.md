---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# Adición de credenciales al entorno de Kubernetes
{: #add-credentials-kube}

Aprenda a añadir credenciales de servicio al entorno de despliegue de Kubernetes.
{: shortdesc}

Debe añadir manualmente las credenciales de servicio al entorno de despliegue en estos casos de ejemplo:
 * Trae su propio código.
 * Comienza a partir de una plantilla de kit de inicio en blanco.
 * Añade un servicio a una app basada en un kit de inicio _después_ de que se despliegue.

## Su código + Kubernetes
{: #credentials-byoc-kube}

<!-- (Refer to the ["Code it Right"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#code-it-right) and ["Prepare the Environment"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#prepare-the-environment) sections.  But translate a bit so we're only mentioning editing a `deployment.yml` file, not the "deployment.yml section of the script in the Deploy pipeline stage configuration".) -->

### Codificación correcta

Como medida de precaución, puede codificar la aplicación para confirmar que su entorno está completo en la base principal de la aplicación. No desea que el despliegue de una aplicación en un clúster cuyo entorno no está completo suponga una interrupción para el producto. Es posible que aplicación no se inicie y la configuración de Kubernetes puede impedir de forma automática tales interrupciones.

Supongamos que tiene las dos variables de entorno siguientes:
* `SECRET`
* `NOT_SECRET`

Para una base de datos, las variables pueden ser `APIKEY` y `DB_URL`, donde la primera es confidencial y la segunda no lo es.

En Java, podría escribir algo parecido a lo siguiente en la base principal de la aplicación:
```java
if (System.getenv("SECRET") == null) {
    throw new RuntimeException("Environment variable 'SECRET' is not set!");
}
// and many more checks...
```
{: codeblock}

En el nodo, consulte un ejemplo similar:
```js
if (!process.env.SECRET) {
    console.error('ENVIRONMENT variable "SECRET" is not set!');
    process.exit(1);
}
// and many more checks...
```
{: codeblock}

### Prepare el entorno

En el archivo `deployment.yml` de Kubernetes, se pueden definir las variables de entorno o una _referencia a un secreto en el clúster_.

#### Establezca el despliegue para obtener las credenciales del entorno

En la sección con `kind: Deployment`, añada el código de ejemplo siguiente a un nivel de sangrado después de `spec.template.spec.containers`:
```yaml
env:
  - name: SECRET
    valueFrom:
      secretKeyRef:
          name: name-secret
          key: KEY_SECRET
  - name: NOT_SECRET
    value: "I'm not a secret"
```
{: codeblock}

* Pulse **Guardar**.

Configure el clúster de modo que _secretKeyRef_ con el nombre `name-secret` y la
clave `KEY_SECRET` se resuelvan en un valor.

#### Instalación de las herramientas necesarias

Utilice un terminal de la estación de trabajo para instalar las siguientes herramientas:

1. Instale la [CLI de {{site.data.keyword.dev_cli_long}}](/docs/cli/index.html).
2. Inicie una sesión con el mandato `ibmcloud login`.
3. Conéctese a su clúster con el mandato `ibmcloud cs cluster-config {your_cluster_name}`.
4. Copie y pegue el mandato `export` para ejecutarlo desde un terminal.

#### Defina el secreto en el clúster

La {{site.data.keyword.dev_cli_notm}} proporciona `kubectl`, que puede ejecutar porque está conectado al clúster de Kubernetes.

Para definir el secreto que se puede resolver, utilice estos mandatos `kubectl`:
```console
echo -n 'This is the secret.  Shhhhh!' > ./KEY_SECRET
```
{: codeblock}

```console
kubectl create secret generic name-secret --from-file=./KEY_SECRET
```
{: codeblock}

Ahora que el clúster de Kubernetes está preparado con un secreto que se puede resolver, puede actualizar la aplicación para que utilice las variables de entorno definidas en el archivo `deployment.yml`.

## App de kit de inicio + Kubernetes
{: #credentials-starterkit-kube}

1. Vaya a la página **Detalles de la app** de la app.
2. Para crear una instancia de Cloud Object Storage, seleccione **Añadir recurso** > **Almacenamiento** > **Cloud Object Storage** > **Plan Lite (gratuito)** > **Crear**.
3. Pulse `Descargar código` para volver a generar el proyecto con los fragmentos de código inyectados.
4. Para acceder a las credenciales localmente, copie y sustituya los archivos siguientes del archivo `.zip` recién generado en el clon local de Git para acceder a las credenciales. Todavía tiene que crear un secreto de Kubernetes en el clúster para alojar las credenciales.

	- `chart/{appName}/bindings.yaml` - Genera una variable de entorno en el clúster de Kubernetes que apunta al secreto.
	- `src/main/resources/localdev-config.json` - Acceso a las credenciales mientras la app se ejecuta localmente.
  - `src/main/resources/mappings.json` - Una correlación para proporcionar acceso al método [`env.getProperty()`](/docs/java-spring/configuration.html#accessing-credentials) para acceder a las variables de entorno desde el código.
  - `manifest.yml` - Este archivo enlaza el servicio a la aplicación Cloud Foundry.

Si más adelante decide desplegar en una aplicación Cloud Foundry con un recurso de Controlador de recursos (ubicado en un grupo de recursos en lugar de en una organización o espacio), debe copiar un archivo más.
{: note}

5. [Visualice](https://cloud.ibm.com/containers-kubernetes/clusters) el clúster de Kubernetes con la región correspondiente (EE.UU. sur si es uno gratuito).
6. Pulse en el clúster y seleccione **Panel de control de Kubernetes** en la parte superior derecha para ver el panel de control del clúster.
7. Desplácese hacia abajo hasta que vea una sección con la etiqueta **Secrets**. Puede ver un secreto correspondiente a su instancia de servicio de {{site.data.keyword.cloudant_short_notm}} que utiliza el siguiente convenio `binding-{appName}-{serviceName}-{timestamp}`. En el archivo `chart/{appName}/bindings.yaml`, encontrará el secreto de {{site.data.keyword.cloudant_short_notm}} correspondiente.
8. Ahora puede crear uno correspondiente para la instancia de Cloud Object Storage con el nombre de secreto que ya se ha generado en `chart/{appName}/bindings.yaml` y que tiene un aspecto parecido a `binding-create-app-ktibr-cloudobjectstor-1538170732311`.
9. Vaya a la página **Detalles de la app** en el panel de control y copie las credenciales correspondientes a la instancia de Cloud Object Storage. Consulte la siguiente salida de credenciales de ejemplo:
```yaml
{
  "apikey": "hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg",
  "endpoints": "https://cos-service.bluemix.net/endpoints",
  "resource_instance_id": "crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"
}    
```
{: codeblock}

10. Asegúrese de que el clúster se haya configurado utilizando `ibmcloud cs cluster-config {your_cluster_name}` y exportando el mandato en las instrucciones siguientes.
11. Utilice el mandato `echo` para colocar las credenciales en el archivo `binding`.
  ```console
  echo -n '{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://cos-service.bluemix.net/endpoints","resource_instance_id":"crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}' > ./binding

  ```
  {: codeblock}

12. Cree el secreto con `kubectl create secret generic binding-create-app-ktibr-cloudobjectstor-15381707323113 --from-file=./binding`. Si vuelve al panel de control del clúster de Kubernetes, podrá ver el secreto que ha creado.

Si está realizando el despliegue en una aplicación de Cloud Foundry, tiene que crear un servicio proporcionado por el usuario si utiliza una instancia de Controlador de recursos (si el recurso reside en un grupo de recursos en lugar de en una organización o espacio). 
{: note}
  
  ```console
  ibmcloud cf create-user-provided-service create-app-ktibr-cloudobjectstor-1538170732311 -p `{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://cos-service.bluemix.net/endpoints","resource_instance_id":"crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}`
  ```
  {: codeblock}

  El nombre del servicio proporcionado por el usuario se encuentra en el archivo `manifest.yml` con el nombre de instancia correspondiente.

13. Ahora puede acceder al secreto a través de las variables de entorno con el método `env.getProperty` cuando la aplicación se ejecute en el clúster de Kubernetes.

### Cómo se prepara el clúster de Kubernetes

Utilice la característica **Desplegar en la nube** para desplegar la app en su clúster de Kubernetes de IBM Containers. La característica prepara el clúster de Kubernetes con secretos para las credenciales de los recursos que están asociados a la app. Para ver los resultados de la preparación del clúster, siga estos pasos:

1. Ejecute este mandato para ver los resultados: `kubectl get secrets`:
  ```
  NAME                                   TYPE                                  DATA      AGE
  binding-blarg-cloudant-1538408663553   Opaque                                1         13m
  bluemix-default-secret                 kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-international   kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-regional        kubernetes.io/dockerconfigjson        1         17d
  default-token-xfd5n                    kubernetes.io/service-account-token   3         17d
  ```
  {: screen}

  Puede consultar [más documentación sobre secretos](https://kubernetes.io/docs/concepts/configuration/secret/).
  {: tip}

2. Observe que el nombre del secreto es el nombre del recurso.
3. Visualice la información detallada sobre el secreto mediante `kubectl get secret binding-blarg-cloudant-1538408663553 -o=yaml`:

  ```
  apiVersion: v1
  data:
    binding: eyJhcGlrZXkiOiI4RFprT3VMVnduVkExWW1HODFnazNQMjZOeThlNWFWbjVhaFpZLVVEOHQ1NCIsImhvc3QiOiI1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJpYW1fYXBpa2V5X2Rlc2NyaXB0aW9uIjoiQXV0byBnZW5lcmF0ZWQgYXBpa2V5IGR1cmluZyByZXNvdXJjZS1rZXkgb3BlcmF0aW9uIGZvciBJbnN0YW5jZSAtIGNybjp2MTpibHVlbWl4OnB1YmxpYzpjbG91ZGFudG5vc3FsZGI6dXMtc291dGg6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzpiZmEzNDJkZC00YjZmLTRkZmUtYTM1YS05MTA4ZmIwZWM1NzE6OiIsImlhbV9hcGlrZXlfbmFtZSI6ImF1dG8tZ2VuZXJhdGVkLWFwaWtleS01MzI3ZWMxZC0wOWE1LTQyMzctOTczNS03ZTAxZmU3NDFiYzciLCJpYW1fcm9sZV9jcm4iOiJjcm46djE6Ymx1ZW1peDpwdWJsaWM6aWFtOjo6OnNlcnZpY2VSb2xlOldyaXRlciIsImlhbV9zZXJ2aWNlaWRfY3JuIjoiY3JuOnYxOmJsdWVtaXg6cHVibGljOmlhbS1pZGVudGl0eTo6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzo6c2VydmljZWlkOlNlcnZpY2VJZC1mNWRhMjMwYy1kNDE0LTQ4NTQtYjE1Yi00MmJmZmRhYWVmNWIiLCJwYXNzd29yZCI6ImY4MjU2ZDJhODYyMjI5NzViZDI3Mjc1MjEzMTY4YTQyNzBhNDZmMmEyOGQ5NDkyMjRhYzFjOTc3NjMwMWNlZTYiLCJwb3J0Ijo0NDMsInVybCI6Imh0dHBzOi8vNTlhYTdiMWEtNWFhYi00ZjJkLTlhNzMtOGMzYjI5NDA4Zjk2LWJsdWVtaXg6ZjgyNTZkMmE4NjIyMjk3NWJkMjcyNzUyMTMxNjhhNDI3MGE0NmYyYTI4ZDk0OTIyNGFjMWM5Nzc2MzAxY2VlNkA1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJ1c2VybmFtZSI6IjU5YWE3YjFhLTVhYWItNGYyZC05YTczLThjM2IyOTQwOGY5Ni1ibHVlbWl4In0=
  kind: Secret
  metadata:
    annotations:
      service-instance-id: 'crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::'
      service-key-id: 5327ec1d-09a5-4237-9735-7e01fe741bc7
    creationTimestamp: 2018-10-01T15:45:02Z
    name: binding-blarg-cloudant-1538408663553
    namespace: default
    resourceVersion: "155591"
    selfLink: /api/v1/namespaces/default/secrets/binding-blarg-cloudant-1538408663553
    uid: f5e7885c-c590-11e8-ad83-8e37f3f3216f
  type: Opaque
  ```
  {: screen}

  El `binding` es el valor codificado en base64 del secreto. Si se decodifica, muestra el JSON sin formato de las `credenciales` de la instancia del recurso, más algunos valores `iam_...` :
  ```
  {
    "apikey": "8DZkOuLVwnVA1YmG81gk3P26Ny8e5aVn5ahZY-UD8t54",
    "host": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "iam_apikey_description": "Auto generated apikey during resource-key operation for Instance - crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::",
    "iam_apikey_name": "auto-generated-apikey-5327ec1d-09a5-4237-9735-7e01fe741bc7",
    "iam_role_crn": "crn:v1:bluemix:public:iam::::serviceRole:Writer",
    "iam_serviceid_crn": "crn:v1:bluemix:public:iam-identity::a/480fd1ec14ac540c5bc37da799a63437::serviceid:ServiceId-f5da230c-d414-4854-b15b-42bffdaaef5b",
    "password": "f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6",
    "port": 443,
    "url": "https://59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix:f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6@59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "username": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix"
  }
  ```
  {: screen}

El código de la aplicación no puede recuperar el secreto de Kubernetes a no ser que el archivo `deployment.yml` declare un valor `env` que haga referencia al secreto. Si utiliza un kit de inicio, este código se genera automáticamente.

### El código generado por el kit de inicio
{: #credentials-starterkit-kube-gencode}

En este caso, ha creado esta aplicación a partir de un kit de inicio. El código que se genera a partir de un kit de inicio se crea de forma que sea portátil para que se pueda ejecutar localmente, en Cloud Foundry o en Kubernetes. Se utiliza la biblioteca, `IBMCloudEnv`, para proporcionar una capa de abstracción entre el código de la aplicación y la recuperación de las variables de entorno que contienen las credenciales correspondientes a los recursos (instancias de servicio).

El código que se crea a partir del kit de inicio tiene una dependencia para la biblioteca `IBMCloudEnv` y genera la siguiente salida:

* Un archivo `bindings.yml`, que se incluye en línea en el archivo `deployment.yml`, con este contenido:
  ```yaml
   - name: service_cloudant
     valueFrom:
     secretKeyRef:
        name: binding-blarg-cloudant-1538408663553
        key: binding
        optional: true
  ```
  {: codeblock}

  El `secretKeyRef.name` expone el secreto de Kubernetes definido de modo que lo pueda recuperar la aplicación como una variable de entorno sencilla en el código de aplicación.

* Las instrucciones para la biblioteca `IBMCloudEnv` se encapsulan en un archivo `mappings.json`, que se encuentra en el código base generado por el kit de inicio. El archivo `mappings.json` contiene definiciones individuales para cada credencial:
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

  El archivo `mappings.json` utiliza la sintaxis de `jsonpath` y el orden de la matriz `searchPatterns`
para guiar la lógica de `IBMCloudEnv`.

* Utilice el código siguiente para recuperar la clave de la API de Cloudant (pseudocódigo):
  ```java
  cloudantApiKey = IBMCloudEnv.getValue('cloudant_apikey');
  ```
  {: codeblock}

La biblioteca `IBMCloudEnv` detecta automáticamente si la aplicación se está ejecutando en Kubernetes, Cloud Foundry o una instancia de servidor virtual (se trata como un docker local), y aplica el `searchPattern` correcto para encontrar el valor que se devuelve.

Por lo tanto, el archivo `mappings.json` se debe considerar como _la lista definitiva_ de los valores preconfigurados e inmediatamente disponibles que proceden del entorno en el que se va a ejecutar la app. Los valores se rellenan en el entorno correspondiente al clúster que ha seleccionado como destino al utilizar la característica **Desplegar en la nube**.

**Atención**: en el momento de escribir esta documentación, la preparación del entorno _siempre_ se realiza para todas las credenciales correspondientes a todos los recursos asociados a una app, pero _no todas las referencias `env`_ se encuentran en el archivo `bindings.yml` o en el archivo `mappings.json`. En estos casos, debe colocar dichas referencias usted mismo. Si ya ha decidido un despliegue de destino y no necesita la abstracción de la biblioteca de `IBMCloudEnv`, consulte la sección "Su código + (despliegue de destino)" que se ajuste a su decisión.

Algunos kits de inicio no incluyen la referencia a la dependencia `IBMCloudEnv` o a los archivos `manifest.yml` o `mappings.json`.
{: note}
