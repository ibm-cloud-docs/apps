---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-02"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# Arquitecturas comunes para apps en la nube
{: #patterns}

Los kits de iniciación en {{site.data.keyword.cloud_notm}} ayudan a crear apps con una arquitectura probada. Las apps son todas diferentes, sin embargo, cuando las basa en un patrón arquitectónico conocido, es más fácil obtener resultados fiables con mayor rapidez. Cuando se crea una app a partir de un kit de iniciación, está eligiendo uno de los distintos tipos de patrón junto con componentes, de forma similar a un tiempo de ejecución, para cumplimentar el patrón.
{:shortdesc}

## App web
{: #web}

El patrón de App web crea apps que sirven contenido web como, por ejemplo, HTML, JavaScript y hojas de estilo para el servidor web. Existen varios kits de iniciación de App web.

* Basic - sirve un archivo `index.html` estático, y un archivo JavaScript y de hoja de estilos vacíos.
* React - una infraestructura rica para crear interfaces de usuario. Los archivos de origen se encuentran en `src/client/app`, se compilan con WebPack y se sirven en el directorio público.

Encontrará kits de iniciación para el patrón de App web en el [panel de control de desarrollador de {{site.data.keyword.cloud_notm}} App Service](https://console.bluemix.net/developer/appservice/dashboard).

## Programa de fondo para programa de usuario (BFF)
{: #bff}

El patrón de Programa de fondo para programa de usuario (BFF) ayuda a crear código de fondo que expone servicios y datos empresariales de una forma que satisfaga las necesidades de los usuarios para un canal de app específico como, por ejemplo, un canal móvil o web. Por ejemplo, los usuarios en un dispositivo móvil podrían utilizar el control de voz, mientras que los usuarios que consumiesen la app a través del navegador web podrían preferir utilizar el ratón. Puede compilar dos programas BFF, uno para móvil que incluye servicios como [{{site.data.keyword.conversationfull}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://www.ibm.com/watson/developercloud/conversation.html) y uno para web con una interfaz de usuario más sofisticada.

En {{site.data.keyword.cloud_notm}}, puede compilar un programa BFF con enfoque de programación para varios lenguajes. Puede utilizar Node.js, Swift, Java o Python y ejecutarlos en un patrón con servicios de contenedor o utilizando funciones sin servidor.

El programa BFF gestiona la persistencia de datos, la colocación en la caché y la integración con servicios de alto valor como, por ejemplo, [{{site.data.keyword.ibmwatson}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=watson), [{{site.data.keyword.iot_short_notm}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=iot), [{{site.data.keyword.weather_short}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/catalog/services/weather-company-data?taxonomyNavigation=apps) y [{{site.data.keyword.sparks}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/catalog/services/apache-spark?taxonomyNavigation=apps).

Los programas BFF habitualmente en la mayoría de las ocasiones exponen una API utilizando un patrón REST. No obstante, puede diseñar su programa BFF para que funcione desde una arquitectura de mensajería utilizando {{site.data.keyword.messagehub}}.

Hay varios kits de iniciación para BFF que puede elegir en función de sus requisitos de lenguaje e infraestructura.  Encontrará kits de iniciación para el patrón de BFF en el [panel de control de desarrollador de {{site.data.keyword.cloud_notm}} App Service](https://console.bluemix.net/developer/appservice/dashboard).

## Microservicio
{: #microservice}

Las apps de los microservicios proporcionan la base para la creación de microservicios de fondo, incluidos los puntos finales de salud básicos y las API REST. Las apps generadas contienen todas las dependencias necesarias, tanto para el propio microservicio, como para los servicios de nube asociados.

Hay varios kits de iniciación para microservicios que puede elegir en función de sus requisitos de lenguaje e infraestructura.  Encontrará kits de iniciación para el patrón de microservicios en el [panel de control de desarrollador de {{site.data.keyword.cloud_notm}} App Service](https://console.bluemix.net/developer/appservice/dashboard).

## Móvil
{: #mobile}

Las apps móviles son diferentes de los otros patrones porque tienen un componente del lado del cliente significativo. El patrón puede incluir conexiones directas a servicios móviles como notificaciones push, autenticación o analíticas web, conocidos como programa de fondo móvil como servicio (MBaaS (Mobile Backend as a Service)) o pueden tener un [Programa de fondo para programa de usuario (BFF)](#bff).  

{{site.data.keyword.cloud_notm}} ofrece varios kits de iniciación móvil para iOS Swift, Android y Cordova. Puede encontrar kits de iniciación para el patrón móvil en el [panel de control de desarrollador de {{site.data.keyword.cloud_notm}} Mobile](https://console.bluemix.net/developer/mobile/dashboard).

## Lenguajes
{: #languages}

Los kits de iniciación que {{site.data.keyword.cloud_notm}} proporciona están disponibles en varias infraestructuras y lenguajes. Por ejemplo, los kits de iniciación de microservicios ofrecen una opción Node.js, mientras que los kits de iniciación más relacionados con el análisis de datos podrían incluir Python o Go. A continuación se trata sobre los lenguajes habituales que se utilizan en los kits de iniciación de {{site.data.keyword.cloud_notm}}.


|Lenguaje de programación | Descripción | Infraestructuras de desarrollo |
|-----|-----|-----|
|Java | [Java](../runtimes/liberty/getting-started.html) cuenta con prestaciones demostradas para crear aplicaciones empresariales. Pero las nuevas prestaciones de Java 8, combinadas con tiempos de ejecución más ligeros como Liberty e infraestructuras como Spring Boot, hacen que Java sea perfecto también para crear microservicios.  Además, Java es un lenguaje de programación extendido para apps de Android. | Spring, Liberty, Android |
|Swift | [Swift](../runtimes/swift/getting-started.html) es un moderno lenguaje de programación creado por Apple en 2014 que se diseño para sustituir Objective C y que está disponible como código abierto desde diciembre de 2015. Hoy en día, se utiliza para crear iOS, macOS, servicios web y software de sistema en sistemas operativos Linux y macos que utilicen una arquitectura x86, ARM o z. Escribe como un lenguaje de script pero se compila para obtener el alto rendimiento de C con una sobrecarga baja, lo que la convierte en la opción ideal para tiempos de ejecución en la nube. Utiliza un sistema de tipos estático y sólido que ve en Java, pero el estilo funcional y las rutinas asíncronas que ve en JavaScript. Ofrece un alto rendimiento, y el origen se compila en código nativo utilizando la cadena de herramientas del compilador LLVM y puede utilizar bibliotecas de sistemas externos escritas en C fácilmente.  Puesto que Swift se puede utilizar para codificar apps del lado del cliente como del lado del servidor, los desarrolladores utilizan Swift cuando necesitan migrar fácilmente las funciones del cliente al servidor y viceversa. | Kitura, iOS|
|Node.js | [Node.js](../runtimes/nodejs/getting-started.html) es un tiempo de ejecución de JavaScript que utiliza un modelo de E/S sin bloqueo y dirigido por sucesos, que lo hace ligero y eficiente, proporcionando un gran rendimiento y escalabilidad para aplicaciones web, patrones de programa de fondo para programa de usuario y microservicios. El ecosistema de paquetes de Node.js', npm, proporciona acceso a una gran recopilación de módulos de código abierto, con una amplia variedad de prestaciones para acelerar el desarrollo de las aplicaciones. | Express|
|JavaScript|JavaScript sirve para crear efectos interactivos en páginas web. JavaScript junto con HTML y CSS son la base de la mayoría de las páginas web. Cuando envuelve en un plugin de Cordova, el código JavaScript puede sacar partido de la funcionalidad de las funciones nativas del dispositivo. Los desarrolladores con conocimientos web pueden crear fácilmente apps móviles y, donde sea apropiado, el código web se puede reutilizar a través de entornos móviles y web.|Cordova|
|Python | [Python](../runtimes/python/getting-started.html) es un lenguaje de programación interpretado de propósito general en el que se da mucha importancia a la legibilidad. Python permite a los programadores implementar funciones utilizando menos líneas de código con relación a otros lenguajes. Las características del lenguaje permite escribir código imperativo, funcional y orientado a objetos. Python es utilizado habitualmente para procesar tareas de lenguaje natural. | Flask, Django|


