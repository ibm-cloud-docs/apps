---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-01"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{:note: .note}

# Cómo añadir un recurso a la app
{: #add-resource}

Cuando se crea una app con {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}, puede añadir recursos desde la página de detalles de la app. También puede suministrarlos directamente desde el catálogo de {{site.data.keyword.cloud_notm}}, fuera del contexto de su app.
{: shortdesc}

Puede solicitar una instancia del recurso y utilizarla independientemente de la app, o puede añadir la instancia de recurso a la app desde la página Detalles de la app. Puede suministrar un determinado tipo de recurso directamente desde el catálogo de {{site.data.keyword.cloud_notm}}.

## Descubrimiento de recursos
{: #discover-resources}

Puede ver todos los servicios disponibles en {{site.data.keyword.cloud_notm}} de las maneras siguientes:

* Desde la consola de {{site.data.keyword.cloud_notm}}. Visualice el catálogo de {{site.data.keyword.cloud_notm}}.
* Desde la línea de mandatos. Utilice el mandato `ibmcloud service offerings`.
* Desde la propia aplicación. Utilice [GET /v2/services Services API ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window}.

Puede seleccionar el servicio que necesita cuando desarrolla aplicaciones. Cuando lo haya seleccionado, {{site.data.keyword.cloud_notm}} proporcionará el servicio. El proceso de suministro puede ser diferente para distintos tipos de servicios. Por ejemplo, un servicio de base de datos crea una base de datos y un servicio de notificación push para aplicaciones móviles genera información de configuración.

{{site.data.keyword.cloud_notm}} proporciona los recursos de un servicio a su aplicación mediante una instancia de servicio. Una instancia de servicio se puede compartir entre aplicaciones web.

También puede utilizar servicios que estén alojados en otras regiones si estos servicios están disponibles en dichas regiones. Estos servicios deben estar accesibles en Internet y tener puntos finales API. Debe codificar manualmente la aplicación para que utilice estos servicios de la misma forma que codifica aplicaciones externas o herramientas de terceros para que utilicen servicios {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Permitir que aplicaciones externas y herramientas de terceros utilicen servicios de {{site.data.keyword.cloud_notm}}](/docs/resources/connect_external_app#externalapp).

## Solicitud de una nueva instancia de servicio
{: #request-instance}

Para solicitar una nueva instancia de servicio, debe utilizar la interfaz de usuario de {{site.data.keyword.cloud_notm}} o la interfaz de la línea de mandatos de {{site.data.keyword.cloud_notm}}.

Cuando especifique el nombre de servicio, no utilice caracteres que no sean alfabéticos o caracteres numéricos, puesto que los resultados podrían ser imprevisibles.
{: note}

Si utiliza la interfaz de usuario de {{site.data.keyword.cloud_notm}} para solicitar una instancia de servicio, siga los siguientes pasos:

1. En el catálogo de {{site.data.keyword.cloud_notm}}, pulse en el mosaico del servicio que desea añadir. Se abre la página de detalles del servicio.

2. Especifique un nombre en el campo **Nombre de servicio**. Se proporciona un nombre predeterminado. Puede modificar el nombre en el campo o dejarlo tal cual.

3. Cumplimente más campos o selecciones y, a continuación, pulse **CREAR**.

Si utiliza la interfaz de línea de mandatos {{site.data.keyword.cloud_notm}} para solicitar una instancia de servicio, descargue la app de forma local, abra la línea de mandatos y cambie al directorio de la app.

1. Ejecute el mandato siguiente para añadir un servicio a la app. Puede seleccionar un servicio existente de uno ya habilitado en su cuenta, o añadir un nuevo servicio.

  ```bash
  ibmcloud dev edit
  ```
  {: pre}

2. Siga las indicaciones para seleccionar un grupo de recursos y para crear y conectar un nuevo servicio relacionado con datos a la aplicación, como por ejemplo Cloudant. Es posible que tenga que seleccionar una región y un plan para el servicio.
3. Cuando se crea el servicio, se añaden varios archivos al directorio de la aplicación, incluidas las credenciales, para ayudarle a integrar el servicio en la aplicación. Puede fusionar manualmente los archivos o saltarse este paso por ahora.

Se pueden enlazar una instancia de servicio únicamente a aquellas instancias de apps que se encuentran en el mismo espacio u organización. No obstante, puede utilizar instancias de servicio de otros espacios y organizaciones de la misma forma que lo hace una app externa. En lugar de crear
un enlace, utilice las credenciales para configurar directamente su instancia de app. Para obtener más información sobre cómo utilizan las apps externas los servicios de {{site.data.keyword.cloud_notm}}, consulte [Permitir que apps externas utilicen servicios de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](/docs/resources/connect_external_app#externalapp){: new_window}.

## Configuración de la aplicación
{: #configure-app}

Después de enlazar una instancia de servicio a una aplicación, debe configurar la aplicación para que interactúe con el servicio.

Cada servicio puede requerir un mecanismo diferente para comunicarse con las aplicaciones. Estos mecanismos están documentados como parte de la definición de servicio con fines informativos cuando desarrolle aplicaciones. Para una mayor coherencia, los mecanismos son necesarios para que la aplicación interactúe con el servicio.

* Para interactuar con servicios de base de datos, utilice la información que {{site.data.keyword.cloud_notm}} proporciona como, por ejemplo, el ID de usuario, la contraseña y el URI de acceso para la aplicación.
* Para interactuar con los servicios de dispositivos móviles de fondo, utilice la información que {{site.data.keyword.cloud_notm}} proporciona como la identidad de la aplicación (ID de app), la información de seguridad que es específica del cliente y el URI de acceso para la aplicación. Los servicios móviles suelen funcionar compartiendo el contexto entre sí, de forma que la información contextual como, por ejemplo, el nombre del desarrollador de la aplicación y el usuario que utilizan la aplicación, se pueden compartir entre el conjunto de servicios.
* Para interactuar con aplicaciones web o código en la nube del servidor para aplicaciones móviles, utilice la información que {{site.data.keyword.cloud_notm}} proporciona como las credenciales de tiempo de ejecución de la variable de entorno *VCAP_SERVICES* de la aplicación. El valor de la variable de entorno *VCAP_SERVICES* es la serialización del objeto JSON. La variable contiene los datos de tiempo de que son necesarios para interactuar con los servicios a los que la aplicación se enlaza. El formato de los datos es diferente para diferentes servicios. Es posible que necesite leer la documentación del servicio para saber lo que puede esperar y cómo interpretar cada información.

Si se bloquea un servicio enlazado con una aplicación, ésta podría dejar de funcionar o tener errores. {{site.data.keyword.cloud_notm}} no reinicia automáticamente la aplicación para solucionar los problemas. Escriba código en la aplicación para identificar y recuperarse de caídas, excepciones y fallos de conexión. Para obtener más información, consulte [Las apps no se reiniciarán automáticamente](/docs/troubleshoot/ts_apps.html#ts_apps_not_auto_restarted).

## Acceso a servicios en los entornos de despliegue de {{site.data.keyword.cloud_notm}}
{: #migrate_instance}

{{site.data.keyword.cloud_notm}} ofrece muchas opciones de despliegue y puede acceder a un servicio que se está ejecutando en un entorno desde un entorno diferente. Por ejemplo, si tiene un servicio que se está ejecutando en Cloud Foundry, puede acceder a dicho servicio desde una aplicación que se esté ejecutando en un clúster de Kubernetes.

### Ejemplo: Acceda a un servicio de Cloud Foundry desde un pod de Kubernetes

Para acceder a un servicio de Cloud Foundry desde un pod de un clúster de Kubernetes, debe enlazar el servicio al clúster para almacenar las credenciales del servicio en un secreto de Kubernetes. A continuación, puede poner esta información a disposición de la app. 
{: shortdesc}

Las credenciales de servicio que se almacenan en un secreto de Kubernetes están codificadas con base64 y cifradas en etcd de forma predeterminada. 

**Importante**: No haga referencia ni exponga las credenciales de servicio directamente en el archivo YAML de despliegue. Los archivos YAML de despliegue no están diseñados para contener datos confidenciales y no cifran las credenciales de servicio de forma predeterminada. Para almacenar correctamente esta información y acceder a ella, debe utilizar un secreto de Kubernetes. 

1. [Enlace el servicio al clúster](/docs/containers/cs_integrations.html#adding_cluster). 
2. Para acceder a las credenciales de servicio desde su pod de app, elija una de las siguientes opciones. 
   - [Monte el secreto como un volumen en el pod](#mount_secret)
   - [Haga referencia al secreto en variables de entorno](#reference_secret)

## Creación de una instancia del servicio proporcionada por el usuario
{: #user_provide_services}

Es posible que tenga servicios gestionados fuera de {{site.data.keyword.cloud_notm}}. Si tiene credenciales para acceder a estos servicios externos desde Internet, puede crear instancias de servicio proporcionadas por el usuario de {{site.data.keyword.cloud_notm}} para representar y comunicarse con los servicios externos.

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

Ahora puede configurar la aplicación para que utilice servicios externos. Para obtener información sobre cómo configurar la aplicación para que interactúe con un servicio, consulte [Configuración de la aplicación para que interactúe con un servicio](/docs/apps/reqnsi.html#configure-app).
