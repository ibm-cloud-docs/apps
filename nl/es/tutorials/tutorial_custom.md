---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-22"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creación de una aplicación personalizada
{: #tutorial}

Puede crear una aplicación personalizada mediante servicios y un tiempo de ejecución. Decida la forma en la que instalar las herramientas que necesita, compile y ejecute la app localmente y despliéguelo en la nube.
{: shortdesc}

## Paso 1: Instalar las herramientas
{: #before-you-begin}

Instale las [herramientas del desarrollador ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.

## Paso 2: Crear una app
{: #create-devex}

Cree una app en {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}:

1. En la página [Kits de iniciación ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) en {{site.data.keyword.dev_console}}, seleccione **Crear** para crear una aplicación personalizada.

2. Especifique el nombre de la app. En esta guía de aprendizaje, utilice `CustomProject`.   

3. Especifique un nombre de host exclusivo como, por ejemplo, sus iniciales seguidas de `-devhost`. Por ejemplo:

	```
	abc-devhost
	```

	El nombre de host es la ruta de su app. Por ejemplo, `abc-devhost.mybluemix.net`.

4. Seleccione el lenguaje de la plataforma. En esta guía de aprendizaje, utilice `Node.js`.

5. (Opcional) Puede iniciar el andamiaje de su sistema de fondo desde un documento OpenAPI. Esto es útil para un desarrollador de sistemas de fondo que ya tiene definido en un documento Swagger su contrato de integración del sistema de fondo y del cliente. Se da soporte a los tipos de archivo **.yaml** y **.json**. Pulse **Añadir archivo** para subir su documento.

6. Pulse **Crear**.

## Opcional: Añadir recursos
{: #add-services}

1. En la vista **Detalles de la app**, seleccione **Añadir recurso**.

2. Seleccione el tipo de servicio que desee. Para esta guía de aprendizaje, seleccione **Datos** > **Siguiente** > **Cloudant NoSQL DB** > **Siguiente**.

3. Pulse **Crear**.

## Opcional: Crear una cadena de herramientas de DevOps
{: #add-toolchain}

La habilitación de una cadena de herramientas crea un entorno de desarrollo en equipo para la app. Cuando se crea una cadena de herramientas, el servicio de app suministrará un repositorio Git, donde visualizar el código fuente, clonar la app y crear y gestionar problemas. También es posible acceder a un entorno Gitlab dedicado y a un conducto de entrega personalizado para la plataforma de despliegue elegida como, por ejemplo, Kubernetes o Cloud Foundry.

La entrega continua está habilitada para algunas aplicaciones. Es posible que desee habilitar la entrega continua para automatizar compilaciones, pruebas y despliegues con Delivery Pipeline y GitHub.

1. Seleccione la app en la página **Apps**.

2. Pulse **Desplegar en la nube**.

3. Seleccione un método de despliegue. Puede optar entre:

	* Desplegar en un clúster Kubernetes. Aprovisione un clúster de hosts, denominados nodos de trabajador, para desplegar y gestionar contenedores de aplicación de alta disponibilidad. Puede crear un clúster o desplegar en un clúster existente.

	* Desplegar utilizando Cloud Foundry, donde no necesita gestionar la infraestructura subyacente.

## Paso 3: Generar el código de la app
{: #generate-code}

Si ha creado una cadena en el paso anterior, se ha creado un repositorio Git para la app donde encontrará el código. Siga estos pasos para acceder a su repositorio:

1. Seleccione la app en la página **Apps**.

2. Pulse **Ver cadena de herramientas**.

3. Pulse la tarjeta **Git** bajo la cabecera **CODE** para abrir el repositorio, donde podrá visualizar el código fuente y clonar la app.

Si una cadena de herramientas no está habilitada, puede acceder a su código descargando el código fuente directamente desde la vista Detalles de la app.

1. Seleccione la app en la página **Apps**.

2. Pulse **Descargar código** para descargar el archivador de la app.

## Paso 4: Empezar a trabajar con su app
{: #code}

Empiece a trabajar con la app descargada:

1. Expanda el archivo archivado.

2. Importe la app a su IDE.

3. Modifique el código.

4. Utilice {{site.data.keyword.dev_cli_notm}} para compilar y ejecutar el código de forma local.


## Paso 5: Compilar y ejecutar la app localmente
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

3. Abra su navegador en `http://localhost:3000` (el número de puerto puede ser diferente dependiendo del tiempo de ejecución elegido).


## Paso 6: Desplegar a la nube
{: #deploy}

### Desplegar utilizando una cadena de herramientas
Hay varias formas de desplegar una app en {{site.data.keyword.cloud_notm}}, sin embargo, utilizar una cadena de herramientas de DevOps es una de las mejores maneras posibles. Una cadena de herramientas de DevOps permite automatizar fácilmente despliegues en varios entornos y añadir rápidamente servicios de supervisión, registro y alertas para gestionar su app a medida que crece.

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
