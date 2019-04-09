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

# Adición de credenciales al entorno de Cloud Foundry
{: #add-credentials-cf}

Aprenda a añadir credenciales de servicio al entorno de despliegue de Cloud Foundry. Estas instrucciones se aplican tanto a [Cloud Foundry Public](/docs/cloud-foundry-public/about-cf.html#about-cf) como a [Cloud Foundry Enterprise Environment](/docs/cloud-foundry-public/cfee.html#cfee).
{: shortdesc}

## Su código + Cloud Foundry
{: #credentials-byoc-cf}

En el espacio de Cloud Foundry en el que reside la aplicación, puede definir qué servicio de Cloud Foundry llama a un servicio proporcionado por el usuario. Un servicio proporcionado por el usuario es un JSON binario almacenado como si fuera un servicio que se puede enlazar en el espacio de Cloud Foundry. Después de iniciar la sesión y de conectarse a la organización y al espacio de Cloud Foundry, siga los pasos siguientes para crear y enlazar un servicio.

1. Cree un servicio proporcionado por el usuario con el mandato siguiente:
  ```console
  cf cups customcreds -p '{"username":"Leeroy","password":"Jenkins"}'
  ```
  {: codeblock}

2. Configure la aplicación de Cloud Foundry para enlazarla con el servicio proporcionado por el usuario añadiendo a la sección de servicios:
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - customcreds
  ```

3. Codifique la aplicación de modo que lea el entorno para una variable de entorno `VCAP_SERVICES`, analícela en JSON y busque las credenciales que necesita (pseudocódigo de tipo node.js):
  ```
  // get the 'password' from "customcreds" user-provided service
  vcapServices = getEnvironment('VCAP_SERVICES');
  vcapServicesAsJSON = JSON.parse(vcapServices);
  upsArray = vcapServicesAsJSON['user-provided'];
  if (upsArray) {
      for (var i = 0, len = upsArray.length; i < len; i++) {
          if (upsArray[i].name === 'customcreds') {
              return upsArray[i].credentials.password
          }
      }
  }
  ```
{: codeblock}


## App de kit de inicio + Cloud Foundry
{: #credentials-starterkit-cf}

### Cómo se prepara el espacio de Cloud Foundry

Utilice la característica **Desplegar en la nube** para desplegar la app en su espacio de Cloud Foundry.

Si la instancia de recurso basada en Cloud Foundry está en el mismo espacio de Cloud Foundry que la aplicación de Cloud Foundry desplegada, consulte la [siguiente sección](/docs/apps/creds_cf.html#cf_resource_same).

Si la instancia de recurso basada en Cloud Foundry está en un espacio distinto del espacio de destino para la aplicación de Cloud Foundry, consulte la [sección siguiente](/docs/apps/creds_cf.html#cf_resource_different).

Si el recurso que ha asociado con la aplicación está basado en Controlador de recursos, consulte [Controlador de recursos](/docs/apps/creds_cf.html#cf_resource_controller).

#### El recurso basado en Cloud Foundry está en el mismo espacio que la app desplegada
{: #cf_resource_same}

Si el recurso que ha asociado con la aplicación está basado en Cloud Foundry, el recurso es "enlazable" en Cloud Foundry. Puede ver el servicio en el espacio de Cloud Foundry conectando la línea de mandatos `cf` con la región, la organización y el espacio correctos. Puede saber si el recurso está basado en Cloud Foundry en el momento de la creación del recurso, si se le ha solicitado en qué organización y espacio de Cloud desea crear el recurso.

Puede ver las aplicaciones enlazadas ejecutando el mandato siguiente:
```console
cf services
```
{: codeblock}

Resultado de ejemplo:
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg3-alertnotificati-1538417831070   alertnotification   authorizedusers                create succeeded
```
{: screen}

#### El recurso basado en Cloud Foundry se encuentra en un espacio diferente de la app desplegada
{: #cf_resource_different}

Cloud Foundry no da soporte al "enlace" de una aplicación de Cloud Foundry con un servicio de Cloud Foundry cuando la aplicación y el servicio no están en el mismo espacio de Cloud Foundry. El espacio de Cloud Foundry debe estar preparado con servicios "proporcionados por el usuario", y se aplica la siguiente sección.

#### El recurso basado en Controlador de recursos está asociado a la app
{: #cf_resource_controller}

Si el recurso que ha asociado con la aplicación está basado en Controlador de recursos (puede saber que se basa en `Controlador de recursos` si en el momento de la creación del recurso se le preguntó en qué grupo de recursos deseaba crear el recurso), el recurso _no_ es "enlazable" a Cloud Foundry. El espacio de Cloud Foundry debe estar preparado con las credenciales del recurso para que la aplicación pueda hacer referencia a las mismas en el código. La preparación se realiza automáticamente, y puede observar los resultados de la preparación del espacio conectando la línea de mandatos `cf` al espacio con el mandato siguiente:
```console
cf services
```
{: codeblock}

Resultado de ejemplo:
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg-cloudant-1538408663553           user-provided
```
{: screen}

Cloud Foundry no permite la visibilidad del valor de las credenciales de servicio, codificadas o no, en la línea de mandatos `cf service` o `cf services`. Funcionalmente, un servicio proporcionado por el usuario es un JSON binario que se define como una "instancia de servicio" con nombre en el espacio de Cloud Foundry. Para ver los valores, primero debe enlazar una aplicación al servicio de Cloud Foundry indicando el nombre de la instancia de servicio en el archivo `manifest.yml` de la app bajo la cabecera `services`. A continuación, ejecute la app en el espacio de Cloud Foundry y obtenga el entorno de dicha aplicación con el mandato `cf env $APP_NAME`.

Afortunadamente, el código generado a partir de un kit de inicio se llena automáticamente con los enlaces correctos para recuperar y utilizar los valores del entorno que se han definido para el mismo en el espacio de Cloud Foundry en el que se ejecuta la aplicación.

### El código generado por el kit de inicio
{: #starterkit-generated-code-cf}

Antes de continuar, consulte [App de kit de inicio + kube](/docs/apps/creds_kube.html#credentials-starterkit-kube-gencode). A continuación, aplique el cambio siguiente:

* Aunque el código generado proporciona el archivo `deployment.yml`, no se puede aplicar para una aplicación que se despliegue en Cloud Foundry. En su lugar _se_ aplica el archivo `manifest.yml` y su contenido se muestra en _bind_ para los dos servicios que se crean en el espacio de Cloud Foundry:
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - blarg3-alertnotificati-1538417831070
      - blarg-cloudant-1538408663553
  ```
  {: codeblock}

Se vuelve a aplicar el resto de la documentación correspondiente a la subsección anterior. La biblioteca `IBMCloudEnv` abstrae la recuperación de los valores desde el entorno en el que se ejecuta la aplicación.

La biblioteca abstrae cierta complejidad en la recuperación de valores de entorno de Cloud Foundry. En Cloud Foundry, se proporciona una aplicación en ejecución con una variable de entorno denominada `VCAP_SERVICES` cuyo valor es un JSON binario y que contiene los valores de las credenciales de servicio enlazadas, independientemente de si el servicio es una instancia de servicio que está _en_ el espacio de Cloud Foundry o un valor de servicio definido por el usuario. Las claves de nivel superior de la variable de entorno JSON de `VCAP_SERVICES` son
la `etiqueta` de Cloud Foundry asociada a los servicios basados en Cloud Foundry y la clave `proporcionada por el usuario`
cuyo valor contiene una matriz de credenciales para todos los servicios "proporcionados por el usuario".

**Atención**: de forma similar al aviso de atención de la sección a la que se hace referencia, la preparación del entorno  _siempre_ se realiza para todas las credenciales de todos los recursos asociados con una app, y todos los `servicios`
se listan en el archivo `manifest.yml`, pero _no todas las referencias de credenciales_ se colocan en el archivo `mappings.json`. En estos casos, tiene que colocar usted mismo dichas referencias. Cuando decida el despliegue de destino y no necesite la abstracción de la biblioteca de `IBMCloudEnv`, consulte la sección "Su código + (despliegue de destino)" que se ajuste a su decisión.

**Doble atención**: algunos kits de inicio no incluyen la referencia a la dependencia `IBMCloudEnv` o a los archivos `manifest.yml` o `mappings.json`.
