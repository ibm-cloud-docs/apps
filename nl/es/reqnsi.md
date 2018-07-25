---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-26"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}

# Cómo añadir un servicio a la app
{: #add_service}

Cuando se crea una app con {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.dev_console}}, puede añadir recursos desde la página de visión general de la app. También puede suministrarlos directamente desde el catálogo de {{site.data.keyword.Bluemix_notm}}, fuera del contexto de su app.
{: shortdesc}

Puede solicitar una instancia del recurso y utilizarla independientemente de la app, o puede añadir la instancia de recurso a la app de la página de visión general de la app. Puede suministrar un determinado tipo de recurso (un servicio) directamente desde el catálogo de {{site.data.keyword.Bluemix_notm}}.

## Descubrimiento de servicios
{: #discover_services}

Puede ver todos los servicios disponibles en {{site.data.keyword.Bluemix_notm}} de las maneras siguientes:

* Desde la consola de {{site.data.keyword.Bluemix_notm}}. Visualice el catálogo de {{site.data.keyword.Bluemix_notm}}.
* Desde la interfaz de línea de mandatos ibmcloud. Utilice el mandato `ibmcloud service offerings`.
* Desde la propia aplicación. Utilice [GET /v2/services Services API ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window}.

Puede seleccionar el servicio que necesita cuando desarrolla aplicaciones. Cuando lo haya seleccionado, {{site.data.keyword.Bluemix_notm}} proporcionará el servicio. El proceso de suministro puede ser diferente para distintos tipos de servicios. Por ejemplo, un servicio de base de datos crea una base de datos y un servicio de notificación push para aplicaciones móviles genera información de configuración.

{{site.data.keyword.Bluemix_notm}} proporciona los recursos de un servicio a su aplicación mediante una instancia de servicio. Una instancia de servicio se puede compartir entre aplicaciones web.

También puede utilizar servicios que estén alojados en otras regiones si estos servicios están disponibles en dichas regiones. Estos servicios deben estar accesibles en Internet y tener puntos finales API. Debe codificar manualmente la aplicación para que utilice estos servicios de la misma forma que codifica aplicaciones externas o herramientas de terceros para que utilicen servicios {{site.data.keyword.Bluemix_notm}}. Para obtener más información, consulte [Habilitación de aplicaciones externas y de herramientas de terceros para utilizar servicios {{site.data.keyword.Bluemix_notm}}](#accser_external).

## Solicitud de una nueva instancia de servicio
{: #req_instance}

Para solicitar una nueva instancia de servicio, debe utilizar la interfaz de usuario de {{site.data.keyword.Bluemix_notm}} o la interfaz de la línea de mandatos de {{site.data.keyword.Bluemix_notm}}.

**Nota:** Cuando especifique el nombre de servicio, no utilice caracteres que no sean alfabéticos o caracteres numéricos, puesto que los resultados podrían ser imprevisibles.

Si utiliza la interfaz de usuario de {{site.data.keyword.Bluemix_notm}} para solicitar una instancia de servicio, siga los siguientes pasos:

1. En el catálogo de {{site.data.keyword.Bluemix_notm}}, pulse en el mosaico del servicio que desea añadir. Se abre la página de detalles del servicio.

2. Especifique un nombre en el campo **Nombre de servicio**. Se proporciona un nombre predeterminado. Puede modificar el nombre en el campo o dejarlo tal cual.

3. Cumplimente más campos o selecciones y, a continuación, pulse **CREAR**.

Si utiliza la interfaz de línea de mandatos {{site.data.keyword.Bluemix_notm}} para solicitar una instancia de servicio, siga los siguientes pasos:

1. Utilice el mandato `ibmcloud service offerings` para buscar el nombre y el plan del servicio que necesita.

2. Utilice el mandato siguiente para crear una instancia de servicio, done service_name es el nombre del servicio, service_plan es el plan del servicio y service_instance es el nombre que desea utilizar para esta instancia de servicio.

```
ibmcloud service create service_name service_plan service_instance
```

3. Utilice el siguiente mandato para enlazar una instancia de servicio a una aplicación, donde *appname* es el nombre de la aplicación y service_instance es el nombre de la instancia de servicio.

```
ibmcloud service bind appname service_instance
```

Se pueden enlazar una instancia de servicio únicamente a aquellas instancias de apps que se encuentran en el mismo espacio u organización. No obstante, puede utilizar instancias de servicio de otros espacios y organizaciones de la misma forma que lo hace una app externa. En lugar de crear
un enlace, utilice las credenciales para configurar directamente su instancia de app. Para obtener más información sobre cómo las apps externas utilizan los servicios de {{site.data.keyword.Bluemix_notm}}, consulte [Habilitación de apps externas para utilizar el servicio de {{site.data.keyword.Bluemix_notm}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](#accser_external){: new_window}.

## Configuración de la aplicación
{: #config}

Después de enlazar una instancia de servicio a una aplicación, debe configurar la aplicación para que interactúe con el servicio.

Cada servicio puede requerir un mecanismo diferente para comunicarse con las aplicaciones. Estos mecanismos están documentados como parte de la definición de servicio con fines informativos cuando desarrolle aplicaciones. Para una mayor coherencia, los mecanismos son necesarios para que la aplicación interactúe con el servicio.

* Para interactuar con servicios de base de datos, utilice la información que {{site.data.keyword.Bluemix_notm}} proporciona como, por ejemplo, el ID de usuario, la contraseña y el URI de acceso para la aplicación.
* Para interactuar con los servicios de dispositivos móviles de fondo, utilice la información que {{site.data.keyword.Bluemix_notm}} proporciona como la identidad de la aplicación (ID de app), la información de seguridad que es específica del cliente y el URI de acceso para la aplicación. Los servicios móviles suelen funcionar compartiendo el contexto entre sí, de forma que la información contextual como, por ejemplo, el nombre del desarrollador de la aplicación y el usuario que utilizan la aplicación, se pueden compartir entre el conjunto de servicios.
* Para interactuar con aplicaciones web o código en la nube del servidor para aplicaciones móviles, utilice la información que {{site.data.keyword.Bluemix_notm}} proporciona como las credenciales de tiempo de ejecución de la variable de entorno *VCAP_SERVICES* de la aplicación. El valor de la variable de entorno *VCAP_SERVICES* es la serialización del objeto JSON. La variable contiene los datos de tiempo de que son necesarios para interactuar con los servicios a los que la aplicación se enlaza. El formato de los datos es diferente para diferentes servicios. Es posible que necesite leer la documentación del servicio para saber lo que puede esperar y cómo interpretar cada información.

Si se bloquea un servicio enlazado con una aplicación, ésta podría dejar de funcionar o tener errores. {{site.data.keyword.Bluemix_notm}} no reinicia automáticamente la aplicación para solucionar los problemas. Escriba código en la aplicación para identificar y recuperarse de caídas, excepciones y fallos de conexión. Para obtener más información, consulte [Las apps no se reiniciarán automáticamente](/docs/troubleshoot/ts_apps.html#ts_apps_not_auto_restarted).

## Acceso a servicios en los entornos de despliegue de {{site.data.keyword.Bluemix_notm}}
{: #migrate_instance}

{{site.data.keyword.Bluemix_notm}} ofrece muchas opciones de despliegue y puede acceder a un servicio que se está ejecutando en un entorno desde un entorno diferente. Por ejemplo, si tiene un servicio que se está ejecutando en Cloud Foundry, puede acceder a dicho servicio desde una aplicación que se esté ejecutando en un clúster de Kubernetes.

### Ejemplo: Acceda a una instancia de servicio de Compose en Cloud Foundry desde un pod Kubernetes

Cualquier instancia de servicio, como {{site.data.keyword.composeForMongoDB}} o {{site.data.keyword.composeForRedis}}, son instancias de pago. Cuando se sienta cómodo utilizando la instancia de servicio de Compose, como {{site.data.keyword.composeForMongoDB}} en Kubernetes, puede importar las credenciales de la instancia que proporciona Compose en Cloud Foundry.

1. Vaya a **Credenciales** y recupere las credenciales de la instancia.

2. Abra el archivo `values.yml` del directorio de gráficos, por ejemplo, `chart/project/`.

3. Establezca los valores a los que se hace referencia en los entornos de servicio. Por ejemplo, en {{site.data.keyword.composeForMongoDB}}:

  ```
  services:
    mongo:
       url: {uri}
       dbName: {dbname}
       ca: {ca_certificate_base64}
       username: {username}
       password: {password}
       env: production

  ```

4. Abra el archivo `bindings.yml` del directorio de gráficos, por ejemplo, `chart/project/`.

5. Añada las referencias de valor de clave que se definen en el archivo `values.yml` al final donde se define el bloque `env`.

  ```
    env:
      - name: MONGO_URL
        value: {{ .Values.services.mongo.url }}
      - name: MONGO_DB_NAME
        value: {{ .Values.services.mongo.name }}
      - name: MONGO_USER
        value: {{ .Values.services.mongo.username }}
      - name: MONGO_PASS
        value: {{ .Values.services.mongo.password }}
      - name: MONGO_CA
        value: {{ .Values.services.mongo.ca }}
  ```

6. En la aplicación, utilice las variables de entorno para iniciar el servicio SDK que se proporciona para usted.

  ```javascript
    const serviceManger = require('./services/serivce-manage.js');
    const mongoURL = process.env.MONGO_URL || 'localhost';
    const mongoUser = process.env.MONGO_USER || '';
    const mongoPass = process.env.MONGO_PASS || '';
    const mongoDBName = process.env.MONGO_DB_NAME || 'comments';
    const mongoCA = [new Buffer(process.env.MONGO_CA || '', 'base64')]

    const options = {
        useMongoClient: true,
        ssl: true,
        sslValidate: true,
        sslCA: mongoCA,
        poolSize: 1,
        reconnectTries: 1
    };

    const mongoDBClient = serviceManger.get('mongodb');
  ```

### Secretos (Opcional)
{: #migrate_secrets_optional}

No exponga las credenciales en los archivos `deployment.yml` o `values.yml`. Puede utilizar una serie codificada en base64 o cifrar sus credenciales con una clave. Para obtener más información, consulte [Creación de un Secreto utilizando kubectl create secret ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://kubernetes.io/docs/concepts/configuration/secret/#creating-your-own-secrets) y [Cómo cifrar sus datos ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/)

## Habilitación de apps externas
{: #accser_external}

Es posible que tenga aplicaciones que se crearon y ejecutaron fuera de {{site.data.keyword.Bluemix_notm}},
o puede que utilice herramientas de terceros. Si los servicios de {{site.data.keyword.Bluemix_notm}} proporcionan claves que están accesibles en Internet, puede utilizarlas con las apps locales o herramientas de terceros.

Los siguientes servicios proporcionan claves de servicio que puede utilizar de forma externa:

* {{site.data.keyword.amashort_old}} <!--Advanced Mobile Access-->
* {{site.data.keyword.alchemyapishort}} <!--AlchemyAPI-->
* {{site.data.keyword.alertnotificationshort}} <!--Alert Notification-->
* {{site.data.keyword.sparks}} <!--Analytics for Apache Spark-->
* {{site.data.keyword.appseccloudshort}} <!--Application Security on Cloud-->
* {{site.data.keyword.blockchain}} <!--Blockchain-->
* {{site.data.keyword.cloudant}} <!--Cloudant&reg; NoSQL DB-->
* {{site.data.keyword.iotmapinsights_short}} <!--Context Mapping-->
* {{site.data.keyword.conversationshort}} <!--Conversation-->
* {{site.data.keyword.dashdbshort}} <!--dashDB-->
* {{site.data.keyword.discoveryshort}} <!--Discovery-->
* {{site.data.keyword.documentconversionshort}} <!--Document Conversion-->
* {{site.data.keyword.iotdriverinsights_short}} <!--Driver Behavior-->
* {{site.data.keyword.geospatialshort_Geospatial}} <!--Geospatial Analytics-->
* {{site.data.keyword.GlobalizationPipeline_short}} <!--Globalization Pipeline-->
* {{site.data.keyword.appconserviceshort}} <!--IBM&reg; App Connect-->
* {{site.data.keyword.dataworks_short}} <!--IBM&reg; Data Connect-->
* {{site.data.keyword.graphshort}} <!--IBM&reg; Graph-->
* {{site.data.keyword.iotelectronics_full}} <!--IBM&reg; IoT for Electronics-->
* {{site.data.keyword.twittershort}} <!--Insights for Twitter-->
* {{site.data.keyword.iot4auto_short}} <!--IoT for Automotive-->
* {{site.data.keyword.iotinsurance_short}} <!--IoT for Insurance-->
* {{site.data.keyword.languagetranslatorshort}} <!--Language Translator-->
* {{site.data.keyword.dwl_short}} <!--Lift-->
* {{site.data.keyword.messagehub}} <!--Message Hub-->
* {{site.data.keyword.mobileanalytics_short}} <!--Mobile Analytics-->
* {{site.data.keyword.nlclassifiershort}} <!--Natural Language Classifier-->
* {{site.data.keyword.objectstorageshort}} <!--Object Storage-->
* {{site.data.keyword.personalityinsightsshort}} <!--Personality Insights-->
* {{site.data.keyword.HybridConnect_short}} <!--Product Insights-->
* {{site.data.keyword.mobilepush}} <!--Push-->
* {{site.data.keyword.retrieveandrankshort}} <!--Retrieve and Rank-->
* {{site.data.keyword.speechtotextshort}} <!-- Speech to Text-->
* {{site.data.keyword.streaminganalyticsshort}} <!--Streaming Analytics-->
* {{site.data.keyword.texttospeechshort}} <!--Text to Speech-->
* {{site.data.keyword.toneanalyzershort}} <!--Tone Analyzer-->
* {{site.data.keyword.tradeoffanalyticsshort}} <!--Tradeoff Analytics-->
* {{site.data.keyword.weather_short}} <!--Weather Company Data-->
* {{site.data.keyword.workloadscheduler}} <!--Workload Scheduler-->

Para habilitar una app externa o una herramienta de terceros para que utilice un servicio {{site.data.keyword.Bluemix_notm}}, siga estos pasos:

1. Solicite una instancia del servicio.
    1. En el Panel de control de la interfaz de usuario de {{site.data.keyword.Bluemix_notm}}, pulse **Crear recurso**. Se visualiza el catálogo.
    2. En el catálogo, seleccione el servicio que desee pulsando el mosaico del servicio. Se abre la página de detalles del servicio.
    3. En la ventana de servicio, deje la selección de lista predeterminada **Conectar a:** como **Dejar sin enlazar**. Esta selección significa que el servicio no se conecta a una app de {{site.data.keyword.Bluemix_notm}}.
    4. Realice las selecciones que necesite. A continuación, pulse en **Crear**. Se creará una instancia de servicio y se mostrará el Panel de control del servicio.
2. En el Panel de control del servicio, puede seleccionar **Credenciales de servicio** para visualizar o añadir credenciales en formato JSON. Seleccione un conjunto de credenciales y pulse **Ver credenciales** en la columna de acciones. Utilice la clave API que se muestra como credenciales para conectarse a la instancia del servicio.

La aplicación que se ejecuta fuera de {{site.data.keyword.Bluemix_notm}} ahora puede acceder al servicio de {{site.data.keyword.Bluemix_notm}}.

**Nota:** Si desea suprimir instancias de servicio o comprobar la información de facturación, debe volver al Panel de control de la interfaz de usuario para gestionar las instancias de servicio.

## Creación de una instancia del servicio proporcionada por el usuario
{: #user_provide_services}

Es posible que tenga servicios gestionados fuera de {{site.data.keyword.Bluemix_notm}}. Si tiene credenciales para acceder a estos servicios externos desde Internet, puede crear instancias de servicio proporcionadas por el usuario de {{site.data.keyword.Bluemix_notm}} para representar y comunicarse con los servicios externos.

Para crear una instancia de servicio proporcionada por el usuario y enlazarla a una aplicación, siga los pasos siguientes:

1. Cree una instancia de servicio proporcionada por el usuario mediante el mandato `ibmcloud service user-provided-create`:
    * Para crear una instancia de servicio general proporcionada por el usuario, utilice la opción **-p** y separe los nombres de los parámetros por comas. La interfaz de línea de mandatos `ibmcloud` le solicitará de uno en uno cada parámetro. Por ejemplo:
        ```
        ibmcloud service user-provided-create testups1 -p "host, port, dbname, username, password"
        host> pubsub01.example.com
        port> 1234
        dbname> sampledb01
        username> pubsubuser
        password> p@$$w0rd
        Creating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * Para crear una instancia de servicio que proporcione información a software de gestión de registros de un otro proveedor, utilice la opción `-l`. Especifique el destino que proporciona el software de gestión de registros de terceros. Por ejemplo:

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example.com
        Creating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

    Si desea actualizar uno o varios parámetros de la instancia de servicio proporcionada por el usuario, utilice el mandato `ibmcloud service user-provided-update`.

    * Para actualizar una instancia de servicio general proporcionada por el usuario, utilice la opción **-p** y especifique las claves y valores de parámetros en un objeto JSON. Por ejemplo:

        ```
        ibmcloud service user-provided-update testups1 -p "{\"username\":\"pubsubuser2\",\"password\":\"p@$$w0rd2\"}"
        Updating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * Para crear una instancia de servicio que proporcione información a software de gestión de registros de un otro proveedor, utilice la opción `-l`. Por ejemplo:

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example2.com
        Updating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

2. Enlace la instancia de servicio a la aplicación con el mandato `ibmcloud service bind`. Por ejemplo:

	```
	ibmcloud service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

Ahora puede configurar la aplicación para que utilice servicios externos. Para obtener información sobre cómo configurar la aplicación para que interactúe con un servicio, consulte [Configuración de la aplicación para interactuar con un servicio ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](#config){: new_window}.

