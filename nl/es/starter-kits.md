---

copyright:
  years: 2019
lastupdated: "2019-04-15"

keywords: developer tools, building apps, developer entry point, get started coding, starter kit

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Kits de inicio
{: #starter-kits}

Los kits de inicio son la solución perfecta para ensamblar dinámicamente el esqueleto de una aplicación de producción en el lenguaje que elija que esté listo para el despliegue de la nube. Cada kit de inicio incluye un lenguaje, una infraestructura y un patrón para un caso de uso específico. Puede reutilizar código en lugar de reinventarlo.
{:shortdesc}

Si un kit de inicio requiere servicios específicos, no hay ningún problema. Con los servicios de suministro automático, {{site.data.keyword.cloud_notm}} crea automáticamente instancias para dichos servicios al crear la app. Puede acceder a los kits de inicio desde el panel de control de {{site.data.keyword.cloud_notm}} o la interfaz de línea de mandatos.

## ¿Qué es un kit de inicio?
{: #starter_kits}

Un kit de inicio es un patrón listo para el entorno de producción que se puede integrar con un conjunto de servicios para generar un activo listo para producción y que se puede desplegar directamente en un conducto de DevOps y en un clúster de Kubernetes. Un kit de inicio contiene metadatos descriptivos que proporcionan al usuario suficiente información para saber qué es y que hace el kit. También contiene instrucciones que indican a {{site.data.keyword.cloud_notm}} lo que debe producir. La salida está lista para producción desde un principio. Luego, de forma iterativa, puede añadir más mejoras con base a las prácticas recomendadas de {{site.data.keyword.cloud_notm}}. El contenido del kit de inicio no es tan complejo como una demostración ni tan trivial como un ejemplo o fragmento de código. Se crean de forma dinámica en función de los requisitos del desarrollador.

Consulte las instrucciones para la [creación de una app con un kit de inicio](/docs/apps?topic=creating-apps-tutorial-starterkit).

## ¿En qué se diferencian los kits de inicio de los ejemplos?
Los kits de inicio están listos para ser utilizados en producción y se centran en demostrar una implementación de un patrón clave utilizando un tiempo de ejecución (por ejemplo Node.js y Express). En algunos casos, los kits de inicio ofrecen una experiencia de usuario simple para resaltar la integración del servicio. En otros casos los kits de inicio representan una implementación personalizable de un caso de uso sofisticado.

* Un fragmento son unas pocas líneas de código que a menudo se presentan en un IDE. Los fragmentos ayudan a un desarrollador a integrar con una sintaxis de lenguaje de programación o dar soporte a la integración con una API definida.
* Una demostración normalmente ofrece una alta calidad y fidelidad y utiliza distintos servicios y puntos de integración. A menudo precisa de tiempo para configurarla y se utiliza para probar un problema empresarial o para demostrar una característica de una plataforma. Puede utilizarla para evaluar las etapas de la adopción en la nube. A veces, es código que se incluye en el código de producción.
* Un ejemplo es un pequeño ejemplo de una característica, función, servicio o recorrido de usuario específicos. Puede reutilizar un ejemplo o incluirlo en una aplicación de producción. Se suele utilizar para mostrar las posibilidades técnicas y un posible enfoque para resolver un problema técnico.

## Código portátil
{: #portable-code}

Cuando se crea una app a partir de kit de inicio, automáticamente se produce un código con un formato coherente y con que depende del tiempo de ejecución. Puede desplegarlo en el destino que desee como, por ejemplo, Kubernetes o Cloud Foundry, sin realizar cambios.

También puede revisar su código de app pulsando **Descargar código** en la página **Detalles de la app** de su app. El código se descarga como un archivo `.zip` que contiene toda la estructura del código de la app. Puede extraer fácilmente el archivo y ejecutar el código localmente utilizando {{site.data.keyword.dev_cli_notm}}, o añadirlo su repositorio de gestión de código.

### ¿Qué código se crea?
{: #what-code}

Cuando crea una app directamente o con ayuda de un kit de inicio, la app contiene código portátil. El código portátil contiene código de habilitación en la nube para varios entornos de nube. Después podrá crear código en cuatro áreas básicas:
* Código que sigue las prácticas recomendados de un idioma específico
* Código que permite que la app se ejecute en la nube
* Código que se ha inicializado para conectarse a servicios de nube
* Código que es específico de un caso de uso

La generación de estos componentes ahorra un tiempo valioso y asegura la utilización de la mejor arquitectura.

* La lógica de los casos de uso proporciona funciones para la función principal de un caso de uso concreto. Por ejemplo, el código para un chat bot de Watson Conversation o el código para una app móvil de reconocimiento visual.
* Los componentes de lenguaje son componentes de código y archivos específicos del lenguaje de programación que selecciona para el kit de inicio. Por ejemplo, los programadores de node.js necesitan un archivo package.json para la gestión de dependencias. Este archivo se crea en nombre del usuario de forma automática.
* La habilitación del servicio es el código que permite que su app se conecte y utilice los servicios que añade. La gestión de credenciales, el código de inicialización y SDK específicos de servicio son ejemplos de elementos de habilitación del servicio.
* La habilitación en la nube se corresponde con el código que permite ejecutar la app en {{site.data.keyword.cloud_notm}}. Por ejemplo, diagramas de Helm que permiten la ejecución de una app en un clúster Kubernetes de {{site.data.keyword.cloud_notm}}.

Cuando se crea una app an partir de un kit de inicio de {{site.data.keyword.cloud_notm}}, la app se inicia con la arquitectura probada que también refleja las mejores prácticas para el idioma seleccionado.

Cada app incluye un archivo readme que contiene detalles técnicos de la app y explica lo que se necesita para ejecutar la app si no se ejecuta desde un principio.
{: tip}
