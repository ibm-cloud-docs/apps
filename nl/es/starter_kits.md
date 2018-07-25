---

copyright:
  years: 2018
lastupdated: "2018-07-05"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Desarrollo de apps
{: #intro}

La consola del desarrollador de {{site.data.keyword.cloud_notm}} ayuda a los desarrolladores a crear apps a partir de kits de iniciación, a suministrar y conectar servicios clave optimizados para {{site.data.keyword.cloud_notm}} y a descargar rápidamente código de trabajo o a realizar la configuración para un suministro continuo. Puede crear, ver, configurar y gestionar la app y descargar el código de la misma. El uso de kits de iniciación le ayuda a evaluar y probar con rapidez los servicios de {{site.data.keyword.cloud_notm}} con una sencilla app.
{:shortdesc}

## ¿Qué es un kit de iniciación?
{: #starter_kits}

Los kits de iniciación son la solución perfecta para ensamblar dinámicamente el esqueleto de una app de producción en el lenguaje que elija que esté listo para el despliegue de la nube. Cada kit de iniciación incluye un lenguaje, una infraestructura y un patrón para un caso de uso específico en el mundo real. Puede reutilizar código en lugar de reinventarlo.

### Comparación entre muestras y kits de iniciación

Los desarrolladores a menudo utilizan código escrito previamente, como fragmentos de código, demostraciones y muestras. ¿Sabe qué diferencia hay entre fragmentos de código, demostraciones y muestras y los kits de iniciación de {{site.data.keyword.cloud_notm}}?

* **Fragmento de código** - Unas pocas líneas de código que se suelen presentar en un IDE. Los fragmentos ayudan a un desarrollador a integrar con una sintaxis de lenguaje de programación o dar soporte a la integración con una API definida.

* **Demostración** - Código que normalmente ofrece una alta calidad y fidelidad y que utiliza distintos servicios y puntos de integración. Suele precisar configuración y se utiliza para probar un problema empresarial o para demostrar una característica de una plataforma. Las demostraciones pueden evaluar las etapas de una adopción en la nube. A veces su código se incluye en el código de producción.

* **Muestra** - Código que constituye un pequeño ejemplo de una característica, función, servicio o recorrido del usuario específico. Es posible reutilizar o incluir los ejemplos en una aplicación de producción. Puede utilizar muestras para mostrar las capacidades técnicas y los enfoques posibles para resolver problemas técnicos.

* **Kit de iniciación de {{site.data.keyword.cloud_notm}}** - Los kits de iniciación son patrones listos para producción que puede integrar con un conjunto de servicios para generar un activo listo para producción. Luego puede desplegarlos directamente en un conducto de DevOps y en un clúster Kubernetes. Un kit de iniciación contiene metadatos descriptivos que proporcionan al usuario suficiente información para saber qué es y qué hace el kit. También contiene instrucciones que indican a {{site.data.keyword.cloud_notm}} lo que debe producir. El resultado se puede mejorar aún más. El contenido del kit de iniciación no es tan complejo como una demostración ni tan trivial como un ejemplo o fragmento de código. Los kits de iniciación se crean de forma dinámica en función de sus requisitos.

  Los kits de inicio muestran una implementación de patrón clave con un tiempo de ejecución, por ejemplo Swift y Kitura. Pueden incluir una experiencia de usuario simple para resaltar la integración del servicio. Los kits de iniciación son implementaciones personalizables de un caso de uso sofisticado.

  Los kits de iniciación incluyen instrucciones que permite a {{site.data.keyword.cloud_notm}} producir de forma automática proyectos de apps estructurales con un código portátil. También especifican los recursos que se deben suministrar automáticamente al crear un proyecto.

## Recursos de suministro automático
{: #auto_privisioned_resources}

Si un kit de iniciación especifica recursos que son necesarios, {{site.data.keyword.cloud_notm}} crea automáticamente las instancias de estos recursos cuando el usuario crea el proyecto. Puede suministrar los recursos manualmente o seleccionar instancias de recursos existentes para añadirlos a su proyecto después de haberlo creado. Encontrará una lista de las instancias de servicio asociadas al proyecto en la vista *Detalles del proyecto*, junto con las credenciales, en el caso de que las necesite.

## Generación de código portátil
{: #portable_code}

Cuando se crea una app a partir de kit de iniciación, automáticamente se crea un código con un formato coherente y con un tiempo de ejecución independiente. Puede desplegar el código en el entorno que desee, por ejemplo, Kubernetes o Cloud Foundry, sin realizar cambios.

El proyecto incluye un archivo `README` con los detalles técnicos del proyecto y en el que se explica lo que necesita para que la app esté lista para ejecutarse.

Para obtener más información, consulte la [consola del desarrollador de {{site.data.keyword.cloud_notm}} para recursos de aprendizaje de Apple](https://console.bluemix.net/developer/appledevelopment/learning-resources).
{: tip}

### ¿Qué contenido de la app se genera?
{: #content}

El código que genera el kit de iniciación de {{site.data.keyword.cloud_notm}} tiene cuatro componentes fundamentales: lógica del caso de uso, componentes del lenguaje, habilitación del servicio y habilitación en la nube. La generación de estos componentes ahorra un tiempo valioso y asegura la utilización de la mejor arquitectura.

* La **lógica de caso de uso** es el código correspondiente a un caso de uso concreto. Por ejemplo, el código para un chat bot de Watson Conversation o el código para una app móvil de reconocimiento visual.
* Los **componentes del lenguaje** son componentes del código y archivos específicos del lenguaje que seleccione para el kit de iniciación. Por ejemplo, los programadores de node.js necesitan un archivo `package.json` para la gestión de dependencias, y este archivo lo crea automáticamente la experiencia de desarrollador de {{site.data.keyword.cloud_notm}}.
* **Habilitación del servicio** es el código que permite que su app se conecte al proyecto y utilice los servicios que añada. La gestión de credenciales, el código de inicialización y los SDK específicos de servicio son ejemplos de elementos de habilitación del servicio.
* La **habilitación en la nube** se corresponde con el código que permite ejecutar la app en {{site.data.keyword.cloud_notm}}. Por ejemplo, los diagramas de Helm permiten que la app que se ejecuta en un clúster de Kubernetes de {{site.data.keyword.cloud_notm}} entren en la categoría de habilitación de la nube.

La app que genera {{site.data.keyword.cloud_notm}} produce es arquitectónicamente correcta y utiliza las prácticas recomendadas correspondientes al lenguaje que elija para el proyecto. Para ver detalles sobre los archivos y la estructura de un proyecto de app, consulte los temas siguientes.

* [Archivos de la app Java](/docs/apps/projects/java_project_contents.html)
* [Archivos de la app Node.js](/docs/apps/projects/node_project_contents.html)
* [Archivos de la app Python](/docs/apps/projects/python_project_contents.html)
* [Archivos de la app Swift](/docs/apps/projects/swift_project_contents.html).
