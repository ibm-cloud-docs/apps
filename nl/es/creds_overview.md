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

# Visión general de las credenciales
{: #credentials_overview}

Aprenda a añadir manualmente credenciales de servicio al entorno de despliegue.
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

En general, desea que la lógica de la aplicación adquiera credenciales de servicio confidenciales, como claves de API o contraseñas de base de datos, del entorno en el que se ejecuta la aplicación. De esta forma, no tiene que guardar las credenciales en el repositorio de código fuente. Las bases de datos de los entornos de integración continua, preproducción y producción están en cuarentena entre sí.

Si crea una app utilizando una plantilla de kit de inicio, el entorno se prepara automáticamente. No importa si el destino de despliegue es:
  * [Kubernetes](/docs/apps/creds_kube.html#add-credentials-kube)
  * [Cloud Foundry Public o Cloud Foundry Enterprise Environment](/docs/apps/creds_cf.html#add-credentials-cf)
  * [Instancia de servidor virtual (también docker local)](/docs/apps/creds_vsi.html#add-credentials-vsi)
  
Se proporcionan pasos sobre cómo configurar el entorno. Los kits de inicio generan código que utiliza una biblioteca dependiente para hacer que el código sea portátil y se pueda ejecutar en cualquiera de los destinos de despliegue. Por último, no se utiliza ninguna lógica de rama para detectar el destino de despliegue en el que se ejecuta la aplicación.

El administrador o el ingeniero de DevOps es el responsable de preparar los entornos con los controles y las configuraciones de acceso adecuados para hacer que los valores que la aplicación necesite estén disponibles.

El proceso "Desplegar en la nube" es un paso único que realiza las siguientes tareas clave:
 * Preparar el entorno de despliegue de destino con servicios, recursos y credenciales.
 * Crea una cadena de herramientas DevOps para crear y desplegar la app en dicho entorno, utilizando código que hace referencia correctamente a las credenciales en el entorno.

Sin embargo, debe preparar el entorno de despliegue de destino en los siguientes casos:
 * Trae su propio código.
 * Comienza a partir de una plantilla de kit de inicio en blanco.
 * Añade un servicio a una app basada en un kit de inicio _después_ de que se despliegue.




