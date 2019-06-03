---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-22"

keywords: supported architecture, supported languages cloud, web app, microservices, mobile, programming languages, app types, common architecture, cloud app

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# Arquitecturas comunes para apps en la nube
{: #patterns}

Los kits de inicio en {{site.data.keyword.cloud_notm}} ayudan a crear apps con una arquitectura probada. Las apps son todas diferentes, sin embargo, cuando las basa en un patrón arquitectónico conocido, es más fácil obtener resultados fiables con mayor rapidez. Cuando se crea una app a partir de un kit de inicio, está eligiendo uno de los distintos tipos de patrón junto con componentes, de forma similar a un tiempo de ejecución, para cumplimentar el patrón.
{:shortdesc}

## App web
{: #web}

El patrón de app web crea apps que sirven contenido web como, por ejemplo, HTML, JavaScript y hojas de estilo para el servidor web. {{site.data.keyword.cloud_notm}} ofrece varios kits de inicio a las apps web.

* Basic - sirve un archivo `index.html` estático, y un archivo JavaScript y de hoja de estilos vacíos.
* React - una infraestructura rica para crear interfaces de usuario. Los archivos de origen se encuentran en `src/client/app`, se compilan con WebPack y se sirven en el directorio público.

Encontrará los kits de inicio para el patrón de app web en el [panel de control del desarrollador de {{site.data.keyword.cloud_notm}} App
Service](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo").

## Microservicio
{: #microservice}

Las apps de los microservicios proporcionan la base para la creación de microservicios de fondo, incluidos los puntos finales de salud básicos y las API REST. Las apps generadas incluyen todas las dependencias necesarias, tanto para el propio microservicio como para los servicios de nube asociados.

Elija un kit de inicio de microservicio para los requisitos de idioma y de infraestructura. Encontrará los kits de inicio para el patrón Microservice en el [panel de control del desarrollador de {{site.data.keyword.cloud_notm}} App
Service](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo").

## Móvil
{: #mobile}

Las apps móviles son diferentes de los otros patrones porque tienen un componente del lado del cliente significativo. El patrón puede incluir conexiones directas a servicios móviles como notificaciones push, autenticación o analíticas de datos móviles. Los servicios móviles reciben el nombre de programa de fondo como servicio o patrón MBaaS. También pueden tener un programa de fondo para programa de usuario dedicado.

{{site.data.keyword.cloud_notm}} ofrece varios kits de inicio móvil para iOS Swift, Android y Cordova. Encontrará los kits de inicio para el patrón Mobile en el [panel de control del desarrollador de {{site.data.keyword.cloud_notm}} Mobile](https://{DomainName}/developer/mobile/dashboard){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo").

## Lenguajes
{: #languages}

Los kits de inicio que {{site.data.keyword.cloud_notm}} proporciona están disponibles en varias infraestructuras y lenguajes. Por ejemplo, los kits de inicio de microservicios ofrecen una opción Node.js, mientras que los kits de inicio más relacionados con el análisis de datos podrían incluir Python o Go. A continuación se trata sobre los lenguajes habituales que se utilizan en los kits de inicio de {{site.data.keyword.cloud_notm}}.

|Lenguaje de programación | Descripción | Infraestructuras de desarrollo |
|-----|-----|-----|
|Java | [Java](/docs/runtimes/liberty?topic=liberty-getting-started) constituye una excelente solución para crear aplicaciones empresariales. Pero las nuevas prestaciones de Java 8, combinadas con tiempos de ejecución más ligeros como Liberty e infraestructuras como Spring Boot, también convierten Java en la solución perfecta para crear microservicios. Java es un lenguaje de programación extendido para apps de Android. | Spring, Liberty, Android |
|Swift | [Swift](/docs/runtimes/swift?topic=Swift-getting-started) es un moderno lenguaje de programación creado en 2014, diseñado para sustituir Objective C y disponible como código abierto desde diciembre de 2015. Hoy en día, se utiliza para crear iOS, macOS, servicios web y software de sistema en sistemas operativos Linux y macos que utilicen una arquitectura x86, ARM o z. Escribe como un lenguaje de script pero se compila para obtener el alto rendimiento de C con un bajo uso de procesador. Resulta ideal para tiempos de ejecución de la nube. Utiliza un sistema de tipos estático y sólido que ve en Java, pero el estilo funcional y las rutinas asíncronas que ve en JavaScript. Ofrece un alto rendimiento y el origen se compila en código nativo utilizando la cadena de herramientas del compilador LLVM. Puede utilizar fácilmente bibliotecas del sistema de otros lenguajes escritos en C. Puesto que Swift se puede utilizar para codificar apps del lado del cliente como del lado del servidor, los desarrolladores utilizan Swift cuando necesitan migrar fácilmente las funciones del cliente al servidor y viceversa. | Kitura, iOS|
|Node.js | [Node.js](/docs/runtimes/nodejs?topicid=Nodejs-getting-started) es un tiempo de ejecución de JavaScript que utiliza un modelo de E/S sin bloqueo y dirigido por sucesos, que lo hace ligero y eficiente. Proporciona un alto nivel de rendimiento y escalabilidad para aplicaciones web, patrones de programa de fondo para programa de usuario y microservicios. El registro de paquetes de Node.js, npm, proporciona acceso a una gran colección de módulos de código abierto. Ofrece una amplia gama de características que le ayudan a acelerar el desarrollo de aplicaciones. | Express|
|JavaScript|JavaScript sirve para crear efectos interactivos en páginas web. JavaScript junto con HTML y CSS son la base de la mayoría de las páginas web. Cuando envuelve en un plugin de Cordova, el código JavaScript puede sacar partido de la funcionalidad de las funciones nativas del dispositivo. Los desarrolladores con conocimientos web pueden crear fácilmente apps móviles y, donde sea apropiado, el código web se puede reutilizar a través de entornos móviles y web.|Cordova|
|Python | [Python](/docs/runtimes/python?topic=Python-getting_started) es un lenguaje de programación interpretado de propósito general en el que se da importancia a la legibilidad. Python permite a los programadores implementar funciones utilizando menos líneas de código con relación a otros lenguajes. Las características del lenguaje permite escribir código imperativo, funcional y orientado a objetos. Python es utilizado habitualmente para procesar tareas de lenguaje natural. | Flask, Django|


