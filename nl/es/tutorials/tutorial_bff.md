---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-06-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creación de una API de programa de fondo para programa de usuario (BFF)
{: #tutorial}

Puede crear una app a partir de un iniciador de programa de fondo para programa de usuario (BFF - Backend-For-Frontend). Utilice estos iniciadores para compilar API de programas de fondo para programas de usuario (BFF) en Node.js, Java o Swift utilizando distintas infraestructuras: Express.js, MicroProfile/Java EE, Kitura o Spring. Decida la forma en la que instalar las herramientas que necesita, compile y ejecute la app localmente y despliéguelo en la nube.
{: shortdesc}

## Paso 1: Instalar las herramientas
{: #before-you-begin}

Instale las [herramientas del desarrollador ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.

## Paso 2: Crear una app
{: #create-devex}

Cree una app en {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}.

1. En la página [Kits de iniciación ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) en {{site.data.keyword.dev_console}}, seleccione un kit de iniciación para su lenguaje. Por ejemplo, para una aplicación Node.js, vaya a **Express.js Backend** y pulse **Seleccionar kit de iniciación**.

2. Especifique el nombre de la app. En esta guía de aprendizaje, utilice `ExpressBackend`.

3. Especifique un nombre de host exclusivo como, por ejemplo, sus iniciales seguidas de `-devhost`. Por ejemplo:

   ```
   abc-devhost
   ```

   El nombre de host es la ruta de su app. Por ejemplo, `abc-devhost.mybluemix.net`.

4. Seleccione el lenguaje de la plataforma. En esta guía de aprendizaje, utilice `Node.js`.

5. Pulse **Crear**.

## Paso 3: Opcional - Añadir recursos
{: #add-services}

1. En la vista **Detalles de la app**, seleccione **Añadir recurso**.

2. Seleccione el tipo de servicio que desee. Para esta guía de aprendizaje, seleccione **Datos** > **Siguiente** > **Cloudant NoSQL DB** > **Siguiente**.

3. Pulse **Crear**.

## Paso 4: Opcional - Crear cadena de herramientas de DevOps
{: #add-toolchain}

La habilitación de una cadena de herramientas crea un entorno de desarrollo en equipo para la app. Cuando se crea una cadena de herramientas, el servicio de app suministrará un repositorio Git, donde visualizar el código fuente, clonar la app y crear y gestionar problemas. También es posible acceder a un entorno Gitlab dedicado y a un conducto de entrega personalizado para la plataforma de despliegue elegida como, por ejemplo, Kubernetes o Cloud Foundry.

La entrega continua está habilitada para algunas aplicaciones. Es posible que desee habilitar la entrega continua para automatizar compilaciones, pruebas y despliegues con Delivery Pipeline y GitHub.

1. Seleccione la app en la página **Apps**.

2. Pulse **Desplegar en la nube**.

3. Seleccione un método de despliegue. Puede optar entre:

	* Desplegar en un clúster Kubernetes. Aprovisione un clúster de hosts, denominados nodos de trabajador, para desplegar y gestionar contenedores de aplicación de alta disponibilidad. Puede crear un clúster o desplegar en un clúster existente.

	* Desplegar utilizando Cloud Foundry, donde no necesita gestionar la infraestructura subyacente.

## Paso 5: Generar el código de la app
{: #generate-code}

Si ha creado una cadena en el paso anterior, se ha creado un repositorio Git para la app donde encontrará el código. Siga estos pasos para acceder a su repositorio:

1. Seleccione la app en la página **Apps**.

2. Pulse **Ver cadena de herramientas**.

3. Pulse la tarjeta **Git** bajo la cabecera **CODE** para abrir el repositorio, donde podrá visualizar el código fuente y clonar la app.

Si una cadena de herramientas no está habilitada, puede acceder a su código descargando el código fuente directamente desde la vista Detalles de la app.

1. Seleccione la app en la página **Apps**.

2. Pulse **Descargar código** para descargar el archivador de la app.

## Paso 6: Empezar a trabajar con su app
{: #code}

Empiece a trabajar con la app descargada:

1. Expanda el archivo archivado.

2. Importe la app a su IDE.

3. Modifique el código.

4. Utilice {{site.data.keyword.dev_cli_notm}} para compilar y ejecutar el código de forma local.

## Paso 7: Construir y ejecutar la aplicación localmente
{: #build-run}

Añada su propio código, compile y ejecute la app. Puede ejecutar la aplicación localmente en su sistema host si instala las herramientas de compilación necesarias, o utilizando el soporte de contenedor disponible en {{site.data.keyword.dev_cli_notm}}.

### Utilización de {{site.data.keyword.dev_cli_short}}

1. Para crear la app en el directorio de proyecto actual, escriba el mandato siguiente:

   ```
   ibmcloud dev build
   ```
   {: codeblock}

2. Para ejecutar la app en el directorio actual, especifique el mandato siguiente:

   ```
   ibmcloud dev run
   ```
   {: codeblock}

3. Puede ejecutar curl en su servidor con:

   ```
   curl http://localhost:3000
   ```
   {: codeblock}

4. Visualice el documento de la API en su servidor en:

   ```
   http://localhost:3000/swagger/api
   ```
   {: codeblock}

5. Puede explorar la API en el servidor en:

   ```
   http://localhost:3000/explorer
   ```
   {: codeblock}

## Paso 8: Desplegar en la nube
{: #deploy}

### Desplegar utilizando una cadena de herramientas
Hay varias formas de desplegar una app en {{site.data.keyword.cloud_notm}}, sin embargo, utilizar una cadena de herramientas de DevOps es una de las mejores maneras posibles.  Una cadena de herramientas de DevOps permite automatizar fácilmente despliegues en varios entornos y añadir rápidamente servicios de supervisión, registro y alertas para gestionar su app a medida que crece.

Con una cadena de herramientas correctamente configurada, un ciclo de despliegue de compilación empieza automáticamente después de cada fusión en la rama maestra en su repositorio. Todas las cadenas de herramientas creadas a partir de un panel de control de desarrollador de {{site.data.keyword.cloud_notm}} se configuran para un despliegue automático.

También puede desplegar manualmente su app desde su cadena de herramientas de DevOps:

1. Seleccione la app en la página **Apps**.

2. Pulse **Ver cadena de herramientas**.

3. Visualice el conducto de entrega donde puede iniciar compilaciones, gestionar el despliegue y ver registros e historiales.

### Desplegar utilizando {{site.data.keyword.dev_cli_short}}
Si elige no utilizar una cadena de herramientas, también puede desplegar utilizando la {{site.data.keyword.dev_cli_short}}.

Para desplegar la app en Cloud Foundry, especifique el mandato siguiente:

```
ibmcloud dev deploy
```
{: codeblock}

Para desplegar la app en un clúster de Kubernetes, especifique el mandato siguiente:

```
ibmcloud dev deploy --target <container>
```
{: codeblock}

### Visualice su app en ejecución
Una vez desplegada la aplicación, verá un URL similar a `abc-devhost.mybluemix.net` en el conducto DevOps o en el terminal (si está utilizando una línea de mandatos). Visite dicho URL en su navegador.
