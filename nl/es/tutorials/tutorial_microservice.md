---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-03-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creación de un microservicio
{: #tutorial}

Puede crear un proyecto a partir del iniciador básico de microservicios (Microservice Basic Starter). Utilice estos iniciadores para compilar un sistema de fondo de microservicio de fondo para Node, Java o Python con distintas infraestructuras. Decida la forma en la que instalar las herramientas que necesita, compile y ejecute el proyecto localmente y despliéguelo en la nube.
{: shortdesc}

## Paso 1: Instalar las herramientas
{: #before-you-begin}

Instale las [herramientas del desarrollador ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.

## Paso 2: Crear un proyecto
{: #create-devex}

Cree un proyecto en {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}:

1. En la página [Kits de iniciación ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) en {{site.data.keyword.dev_console}}, seleccione un kit de iniciación para su lenguaje. Por ejemplo, para una aplicación Node.js, vaya a **Express.js Microservice** y pulse **Seleccionar Starter Kit**.

2. Especifique el nombre del proyecto. En esta guía de aprendizaje, utilice `MicroserviceProject`.   

3. Especifique un nombre de host exclusivo como, por ejemplo, sus iniciales seguidas de `-devhost`. Por ejemplo:

	```
	abc-devhost
	```

	Este nombre de host es la ruta de su proyecto. Por ejemplo, `abc-devhost.mybluemix.net`.

4. Seleccione el lenguaje de la plataforma. En esta guía de aprendizaje, utilice `Node.js`.

5. Pulse **Crear proyecto**.

## Opcional: Añadir recursos
{: #add-services}

1. En la vista **Detalles del proyecto**, seleccione **Añadir recurso**.

2. Seleccione el tipo de servicio que desee. Para esta guía de aprendizaje, seleccione **Datos** > **Siguiente** > **Cloudant NoSQL DB** > **Siguiente**.

4. Pulse **Crear**.

## Opcional: Crear una cadena de herramientas de DevOps
{: #add-toolchain}

La habilitación de una cadena de herramientas crea un entorno de desarrollo en equipo para su proyecto. Cuando se crea una cadena de herramientas, el servicio de app suministrará un repositorio Git, donde visualizar el código fuente, clonar el proyecto y crear y gestionar problemas. También es posible acceder a un entorno Gitlab dedicado y a un conducto de entrega personalizado para la plataforma de despliegue elegida como, por ejemplo, Kubernetes o Cloud Foundry.

La entrega continua está habilitada para algunas aplicaciones. Es posible que desee habilitar la entrega continua para automatizar compilaciones, pruebas y despliegues con Delivery Pipeline y GitHub.

1. Seleccione su proyecto en la página **Proyectos**.

2. Pulse **Desplegar en la nube**.

3. Seleccione un método de despliegue. Puede optar entre:

	* Desplegar en un clúster Kubernetes. Aprovisione un clúster de hosts, denominados nodos de trabajador, para desplegar y gestionar contenedores de aplicación de alta disponibilidad. Puede crear un clúster o desplegar en un clúster existente.

	* Desplegar utilizando Cloud Foundry, donde no necesita gestionar la infraestructura subyacente.

## Paso 3: Generar su código de proyecto
{: #generate-code}

Si ha creado una cadena de herramientas en el paso anterior, se ha creado un repositorio Git para el proyecto donde podrá encontrar el código. Siga estos pasos para acceder a su repositorio:

1. Seleccione su proyecto en la página **Proyectos**.

2. Pulse **Ver cadena de herramientas**.

3. Pulse la tarjeta **Git** bajo la cabecera **CODE** para abrir el repositorio, donde podrá visualizar el código fuente y clonar el proyecto.

Si una cadena de herramientas no está habilitada, puede acceder a su código descargando el código fuente directamente desde la vista Detalles del proyecto.

1. Seleccione su proyecto en la página **Proyectos**.

2. Pulse **Descargar código** para descargar el archivador del proyecto.

## Paso 4: Empezar a trabajar con su app
{: #code}

Empiece a trabajar con el proyecto descargado:

1. Expanda el archivo archivado.

2. Importe el proyecto en su IDE.

3. Modifique el código.

4. Utilice {{site.data.keyword.dev_cli_notm}} para compilar y ejecutar el código de forma local.


## Paso 5: Compilar y ejecutar la app localmente
{: #build-run}

Añada su propio código, compile y ejecute el proyecto. Puede ejecutar la aplicación localmente en su sistema host si instala las herramientas de compilación necesarias, o utilizando el soporte de contenedor disponible en {{site.data.keyword.dev_cli_notm}}.

### Utilización de {{site.data.keyword.dev_cli_short}}

1. Para crear el proyecto en el directorio de proyecto actual, escriba el siguiente mandato:

  ```
  bx dev build
  ```
  {: codeblock}

2. Para ejecutar el proyecto en el directorio de proyecto actual, escriba el siguiente mandato:

  ```
  bx dev run
  ```
  {: codeblock}

3. Puede acceder a la aplicación utilizando `curl` en el servidor:

	```
	curl http://localhost:9080
	```
	{: codeblock}


## Paso 6: Desplegar a la nube
{: #deploy}

### Desplegar utilizando una cadena de herramientas
Hay varias formas de desplegar una app en {{site.data.keyword.cloud_notm}}, sin embargo, utilizar una cadena de herramientas de DevOps es una de las mejores maneras posibles.  Una cadena de herramientas de DevOps permite automatizar fácilmente despliegues en varios entornos y añadir rápidamente servicios de supervisión, registro y alertas para gestionar su app a medida que crece.

Con una cadena de herramientas correctamente configurada, un ciclo de despliegue de compilación empieza automáticamente después de cada fusión en la rama maestra en su repositorio. Todas las cadenas de herramientas creadas a partir de un panel de control de desarrollador de {{site.data.keyword.cloud_notm}} se configuran para un despliegue automático.

También puede desplegar manualmente su app desde su cadena de herramientas de DevOps:

1. Seleccione su proyecto en la página **Proyectos**.

2. Pulse **Ver cadena de herramientas**.

3. Visualice el conducto de entrega donde puede iniciar compilaciones, gestionar el despliegue y ver registros e historiales.

### Desplegar utilizando {{site.data.keyword.dev_cli_short}}
Si elige no utilizar una cadena de herramientas, también puede desplegar utilizando la {{site.data.keyword.dev_cli_short}}.

Especifique el siguiente mandato para desplegar su proyecto en Cloud Foundry:

  ```
  bx dev deploy
  ```
  {: codeblock}

Especifique el siguiente mandato para desplegar su proyecto en un clúster Kubernetes:

```
bx dev deploy --target <container>
```
{: codeblock}

### Visualice su app en ejecución
Una vez desplegada la aplicación, verá un URL similar a `abc-devhost.mybluemix.net` en el conducto DevOps o en el terminal (si está utilizando una línea de mandatos). Visite dicho URL en su navegador.

