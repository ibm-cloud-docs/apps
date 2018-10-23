---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-10-10"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creación de una aplicación móvil con un kit de inicio
{: #tutorial}

{{site.data.keyword.Bluemix}} ofrece kits de inicio móviles para ayudarle a crear una app para móvil rápidamente. Elija un idioma, una infraestructura y herramientas de kits de inicio de App Service para empezar a trabajar con una app personalizada preconfigurada. En esta guía de aprendizaje, puede aprender a instalar las herramientas que necesita, a crear y ejecutar la app localmente y a desplegarla en la nube.
{: shortdesc}

## Paso 1. Instalar las herramientas
{: #install-tools}

Instale las [herramientas del desarrollador](/docs/cli/index.html).

Docker se instala como parte de las herramientas de desarrollador. Docker debe estar en ejecución para que funcionen los mandatos de compilación. Debe crear una cuenta de Docker, ejecutar la app de Docker e iniciar la sesión.

## Paso 2. Crear una app utilizando la {{site.data.keyword.dev_console}}
{: #create-devex}

1. Cree una app de {{site.data.keyword.dev_console}} en {{site.data.keyword.Bluemix}}.
2. En la página [Kits de inicio ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) de la {{site.data.keyword.dev_console}}, seleccione un kit de inicio basado en las características que desee. Por ejemplo, para una aplicación de lenguaje Watson, seleccione **Swift Kitura**.
3. Especifique el nombre de la app. En esta guía de aprendizaje, utilice `WatsonApp`.
4. Seleccione el lenguaje de la plataforma. En esta guía de aprendizaje, utilizaremos `Swift`.
5. Seleccione el idioma y la infraestructura. Es posible que algunos kits de inicio solo estén disponibles en un idioma.
6. Seleccione el plan de precios. Hay una opción gratuita que puede utilizar para esta guía de aprendizaje.
7. Pulse **Crear**.

## Paso 3. Añadir recursos (opcional)
{: #add-services}

Puede añadir recursos para mejorar la app con la potencia cognitiva de Watson, para añadir servicios móviles o servicios de seguridad. Para esta guía de aprendizaje, añada un lugar para gestionar los datos.

1. En la ventana de servicio de la app, pulse **Añadir recurso**.
2. Seleccione el tipo de servicio que desee. Por ejemplo, seleccione **Datos** > **Siguiente** > **Cloudant** > **Siguiente**.
3. Seleccione el plan de precios. Hay una opción gratuita que puede utilizar para esta guía de aprendizaje.
4. Pulse **Crear**.

## Paso 4. Crear una cadena de herramientas de DevOps
{: #add-toolchain}

La habilitación de una cadena de herramientas crea un entorno de desarrollo en equipo para la app. Cuando se crea una cadena de herramientas, el servicio de app crea un repositorio Git, donde puede ver el código fuente, clonar la app y crear y gestionar problemas. También es posible acceder a un entorno de laboratorio Git dedicado y a un conducto de entrega continua. Se personalizan en la plataforma de despliegue que elija, ya sea Kubernetes o Cloud Foundry.

La entrega continua está habilitada para algunas aplicaciones. Puede habilitar la entrega continua para automatizar compilaciones, pruebas y despliegues a través de Delivery Pipeline y GitHub.

1. En la ventana de servicio de la app, pulse **Desplegar en la nube**.
2. Seleccione un método de despliegue. Configure el método de despliegue de acuerdo con las instrucciones para el método que elija.

    * Desplegar en un clúster Kubernetes. Cree un clúster de hosts, denominados nodos de trabajador, para desplegar y gestionar contenedores de aplicaciones de alta disponibilidad. Puede crear un clúster o desplegar en un clúster existente.

    * Desplegar con Cloud Foundry, donde no necesita gestionar la infraestructura subyacente.

## Paso 5. Crear y ejecutar la app localmente
{: #build-run}

El despliegue de la app en la nube en el último paso ha creado una cadena de herramientas. Una cadena de herramientas crea un repositorio Git para la app donde puede encontrar el código allí. Siga estos pasos para acceder a su repositorio. Puede compilar la app localmente para probarla antes de enviarla por push a la nube.

1. En la ventana de servicio de la app, pulse **Descargar código** o **Clonar el repositorio** para trabajar con el código localmente.
2. Importe la app a su entorno de desarrollo integrado.
3. Modifique el código.
4. Configure [Autenticación de Git](/docs/services/ContinuousDelivery/git_working.html#git_authentication) añadiendo una señal de acceso personal.
5. Inicie sesión en la interfaz de línea de mandatos de {{site.data.keyword.Bluemix}}. Si su organización utiliza inicios de sesión federados, utilice la opción `-sso`.

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Establezca los destinos de org y de espacio.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7.  Obtener las credenciales.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Asegúrese de que Docker se esté ejecutando y cree la app en un contenedor de desarrollo local desde el directorio.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Ejecute la app en un contenedor de desarrollo local.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10.  Abra el navegador en `http://localhost:3000`. Es posible que el número de puerto sea distinto en función del tiempo de ejecución elegido.

### Ejecución de la app Swift en Xcode
{: #run_swift}

1. Abra el archivo `README.md` en un visor para archivos markdown para revisar los pasos para configurar la app.
2. Abra el terminal, vaya a la carpeta de la app y, a continuación, ejecute los siguientes mandatos:
    1. Ejecute `pod setup` si tiene que configurar el repositorio de CocoaPods.
    2. Ejecute `pod update` si tiene que actualizar los pods existentes.
    3. Ejecute `pod install` para instalar los pods para la app.
3. Abra su espacio de trabajo Xcode `<appname>.xcworkspace`.
4. Ejecute la app.

### Ejecución de la app Cordova en Xcode
{: #run_cordova_xcode}

Si opta utilizar Cordova como su lenguaje de implementación, siga estas instrucciones.

1. Abra el archivo `README.md` en un visor Markdown para configurar la app.
2. Abra la app `platforms/ios` en Xcode.
3. Ejecute la app.

### Ejecución de la app Cordova en Android Studio
{: #run_cordova_studio}

Utilice esta sección si quiere utilizar Cordova como plataforma de su app móvil.

1. Extraiga el archivo `BasicProject-Cordova.zip`.
2. Abra el archivo `README.md` en un visor Markdown para configurar la app.
3. Abra la app `platforms/android` en Android Studio.
4. Ejecute la app.

### Ejecución de la app Android en Android Studio
{: #run_android}

Utilice esta sección si quiere utilizar Android como plataforma de su app móvil.

1. Abra el archivo `README.md` en un visor Markdown para configurar la app.
2. Abra la app `BasicProject-Android` en Android Studio.
3. Ejecute la app.

## Paso 6. Desplegar la app
{: #deploy}

### Desplegar utilizando una cadena de herramientas

Puede desplegar la app en {{site.data.keyword.cloud_notm}} de varias formas, pero una cadena de herramientas de DevOps es la mejor forma de desplegar apps de producción. Con una cadena de herramientas de DevOps, puede automatizar fácilmente despliegues en muchos entornos y añadir rápidamente servicios de supervisión, de registro y de alertas para ayudar a gestionar su app a medida que crece.

Con una cadena de herramientas correctamente configurada, un ciclo de despliegue de compilación empieza automáticamente después de cada fusión en la rama maestra en su repositorio. Todas las cadenas de herramientas creadas a partir de un panel de control de desarrollador de {{site.data.keyword.cloud_notm}} se configuran para un despliegue automático.

También puede desplegar manualmente su app desde su cadena de herramientas de DevOps:

1. En la ventana Detalles de la app, pulse **Ver cadena de herramientas**.

2. Pulse **Conducto de entrega** donde puede iniciar compilaciones, gestionar el despliegue y ver registros e historiales.

### Desplegar utilizando el {{site.data.keyword.dev_cli_short}}

Para desplegar la app en Cloud Foundry, especifique el mandato siguiente:

```
ibmcloud dev deploy
```
{: pre}

Para desplegar la app en un clúster de Kubernetes, especifique el mandato siguiente:

```
ibmcloud dev deploy --target <container>
```
{: pre}

## Paso 7. Verificar que la app se está ejecutando
{: #verify}

Después de desplegar la app, el conducto o la línea de mandatos de DevOps le apunta al URL para la app, por ejemplo `abc-devhost.mybluemix.net`. Vaya a ese URL en el navegador.
