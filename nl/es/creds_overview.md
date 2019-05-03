---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, credentials

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# Visión general de las credenciales
{: #credentials_overview}

Aprenda a añadir manualmente credenciales de servicio al entorno de despliegue.
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

En general, desea que la lógica de la aplicación adquiera credenciales de servicio confidenciales, como claves de API o contraseñas de base de datos, del entorno en el que se ejecuta la aplicación. De esta forma, no tiene que guardar las credenciales en el repositorio de código fuente. Las bases de datos de los entornos de integración continua, preproducción y producción están en cuarentena entre sí.

Si crea una app utilizando una plantilla de kit de inicio, el entorno se prepara automáticamente. No importa si el destino de despliegue es:
  * [Kubernetes](/docs/apps?topic=creating-apps-add-credentials-kube)
  * [Cloud Foundry Public o Cloud Foundry Enterprise Environment](/docs/apps?topic=creating-apps-add-credentials-cf)
  * [Instancia de servidor virtual (también docker local)](/docs/apps?topic=creating-apps-add-credentials-vsi)
  
Se proporcionan pasos sobre cómo configurar el entorno. Los kits de inicio generan código que utiliza una biblioteca dependiente para hacer que el código sea portátil y se pueda ejecutar en cualquiera de los destinos de despliegue. Por último, no se utiliza ninguna lógica de rama para detectar el destino de despliegue en el que se ejecuta la aplicación.

El administrador o el ingeniero de DevOps es el responsable de preparar los entornos con los controles y las configuraciones de acceso adecuados para hacer que los valores que la aplicación necesite estén disponibles.

"Configurar entrega continua" es un paso único que realiza las tareas clave siguientes:
 * Prepara el destino de despliegue con servicios, recursos y credenciales.
 * Crea una cadena de herramientas DevOps para crear y desplegar la app en dicho entorno, utilizando código que hace referencia correctamente a las credenciales en el entorno.

No obstante, debe preparar el destino de despliegue en cualquiera de los casos siguientes:
 * Trae su propio código.
 * Comienza a partir de una plantilla de kit de inicio en blanco.
 * Añade un servicio a una app basada en un kit de inicio después de que se despliegue.

La preparación del entorno siempre se lleva a cabo para todas las credenciales de todos los servicios asociados a una app, y todos los servicios (`services`) se enumeran en `manifest.yml`, pero no todas las referencias de credenciales se incluyen en el archivo `mappings.json`. En estos casos, tiene que colocar usted mismo dichas referencias. Tras decidir un destino de despliegue, y si no necesita la abstracción de la biblioteca `IBMCloudEnv`, consulte la sección "Su código + (destino de despliegue)"
que se ajuste a su decisión.
{: important}

Algunos kits de inicio no incluyen la referencia a la dependencia `IBMCloudEnv` o a los archivos `manifest.yml` o `mappings.json`.
{: important}
