---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-05"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{: tip: .tip}

# Conexión de servicios a apps externas
{: #externalapp}

Es posible que tenga aplicaciones que se crearon y ejecutaron fuera de {{site.data.keyword.Bluemix_notm}},
o puede que utilice herramientas de terceros. Si los servicios de {{site.data.keyword.Bluemix_notm}} proporcionan claves que están accesibles en Internet, puede utilizarlas con las apps locales o herramientas de terceros.

Los siguientes servicios proporcionan claves de servicio que puede utilizar de forma externa:

* {{site.data.keyword.alertnotificationshort}} <!--Alert Notification-->
* {{site.data.keyword.sparks}} <!--Analytics for Apache Spark-->
* {{site.data.keyword.blockchain}} <!--Blockchain-->
* {{site.data.keyword.cloudant}} <!--Cloudant&reg; NoSQL DB-->
* {{site.data.keyword.conversationshort}} <!--Conversation-->
* {{site.data.keyword.discoveryshort}} <!--Discovery-->
* {{site.data.keyword.geospatialshort_Geospatial}} <!--Geospatial Analytics-->
* {{site.data.keyword.GlobalizationPipeline_short}} <!--Globalization Pipeline-->
* {{site.data.keyword.appconserviceshort}} <!--IBM&reg; App Connect-->
* {{site.data.keyword.languagetranslatorshort}} <!--Language Translator-->
* {{site.data.keyword.dwl_short}} <!--Lift-->
* {{site.data.keyword.messagehub}} <!--Message Hub-->
* {{site.data.keyword.nlclassifiershort}} <!--Natural Language Classifier-->
* {{site.data.keyword.objectstorageshort}} <!--Object Storage-->
* {{site.data.keyword.personalityinsightsshort}} <!--Personality Insights-->
* {{site.data.keyword.mobilepush}} <!--Push-->
* {{site.data.keyword.speechtotextshort}} <!-- Speech to Text-->
* {{site.data.keyword.streaminganalyticsshort}} <!--Streaming Analytics-->
* {{site.data.keyword.texttospeechshort}} <!--Text to Speech-->
* {{site.data.keyword.toneanalyzershort}} <!--Tone Analyzer-->
* {{site.data.keyword.weather_short}} <!--Weather Company Data-->
* {{site.data.keyword.workloadscheduler}} <!--Workload Scheduler-->

Para permitir que una app externa o una herramienta de terceros utilice un servicio {{site.data.keyword.Bluemix_notm}}, siga estos pasos:

1. Cree una instancia del servicio.
    1. Pulse **Catálogo**.
    2. En el catálogo, seleccione el servicio que desee pulsando el mosaico del servicio. 
    3. Seleccione la ubicación y la organización, el espacio o el grupo de recursos y luego pulse **Crear**.
2. En la página de detalles del servicio, seleccione **Credenciales de servicio** para visualizar o añadir credenciales en formato JSON.  
    * Para crear nuevas credenciales, seleccione **Nueva credencial** y, si lo desea, añada parámetros de configuración manualmente o importe un archivo en formato JSON y luego pulse **Añadir**. Seleccione **Ver credenciales** para guardar las credenciales para conectarse a la app externa.
    * Seleccione un conjunto de credenciales y pulse **Ver credenciales** en la columna Acciones si ya existen.  
3. Utilice la clave API que se muestra como credenciales para conectarse a la instancia del servicio.

La aplicación que se ejecuta fuera de {{site.data.keyword.Bluemix_notm}} ahora puede acceder al servicio de {{site.data.keyword.Bluemix_notm}}.

Si desea suprimir instancias de servicio o comprobar la información de facturación, debe volver al Panel de control de la interfaz de usuario para gestionar las instancias de servicio.
{: tip}
