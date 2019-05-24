---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-10"

keywords: apps, credentials, service, add service credentials, environment, deployment

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# Adición manual de credenciales de servicio al entorno de despliegue
{: #credentials_overview}

Desea que la lógica de la aplicación adquiera credenciales de servicio confidenciales, como claves de API o contraseñas de base de datos, del entorno en el que se ejecuta la aplicación. De esta forma, no tiene que tiene que guardar las credenciales en el repositorio de código fuente.
{: shortdesc}

Si crea una app utilizando un kit de inicio, el entorno se prepara automáticamente. Cuando conecte un servicio al kit de inicio antes de desplegar la app, las credenciales del servicio se añadirán automáticamente al entorno.
{ :tip}

Debe añadir manualmente las credenciales de servicio al entorno de despliegue en los siguientes casos:

 * Trae su propio código.
 * Añade un servicio a una app basada en un kit de inicio después de que se despliegue la app.

El proceso de adición de credenciales de servicio depende del destino del despliegue y del lenguaje de programación. Para obtener más información sobre cómo configurar credenciales de servicio para el destino de despliegue, consulte la documentación específica del entorno de alojamiento:

  * [{{site.data.keyword.containershort}}](/docs/containers?topic=containers-service-binding#adding_app)
  * Cloud Foundry público o {{site.data.keyword.cfee_full}}
  * Instancia de servidor virtual (contenedor docker local)

Muchos lenguajes e infraestructuras proporcionan bibliotecas estándares para configuraciones específicas de la aplicación y específicas del entorno. Para obtener más información, consulte las siguientes guías de programación:

* [Java: Cómo trabajar con credenciales de servicio](/docs/java?topic=cloud-native-configuration)
* [Configuración del entorno Node.js](/docs/node?topic=nodejs-configure-nodejs)
* [Configuración del entorno Spring](/docs/java?topic=java-spring-configuration)
* [Configuración del entorno Swift](/docs/swift?topic=swift-configuration)
* [Configuración del entorno Go](/docs/go?topic=go-configure-go-env)
