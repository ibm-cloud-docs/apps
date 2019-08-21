---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-17"

keywords: apps, mobile, mobile app, starter kit, developer tools, devops toolchain, toolchain, create mobile app, mobile starter kit, android, ios, swift, xcode

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Creación de una app móvil
{: #tutorial-mobile}

{{site.data.keyword.cloud}} ofrece kits de inicio para apps móviles para ayudarle a crear una aplicación para móvil rápidamente. Seleccione un lenguaje, una infraestructura y herramientas de los kits de inicio para apps móviles para empezar a trabajar con una app preconfigurada. O bien, puede utilizar un kit de inicio básico para crear una app móvil personalizada.
{: shortdesc}

## Antes de empezar
{: #prereqs-mobile}

Instale la [interfaz de línea de mandatos (CLI) de {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-getting-started).

## Creación de una app móvil con un kit de inicio
{: #create-mobile}

Para crear una app móvil utilizando un kit de inicio, siga estos pasos:

1. En la página [Kits de inicio para apps móviles](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo") de la {{site.data.keyword.dev_console}}, seleccione un kit de inicio en base a las características que desee. Por ejemplo, seleccione **Watson Visual Recognition**.
2. Especifique el nombre de la app. En esta guía de aprendizaje, utilice `WatsonApp`.
3. Opcional. Proporcione etiquetas para clasificar la app. Para obtener más información, consulte [Cómo trabajar con etiquetas](/docs/resources?topic=resources-tag).
4. Seleccione su plataforma. Para esta guía de aprendizaje, seleccione **iOS Swift**. Es posible que algunos kits de inicio solo estén disponibles en un lenguaje.
5. Seleccione el plan de precios. Utilice la opción **Lite** para esta guía de aprendizaje. Si se requiere algún servicio, se definen automáticamente en el kit de inicio.
6. Pulse **Crear**.

## Creación de una app móvil personalizada
{: #create-mobile-basic}

Para crear una app móvil personalizada, siga estos pasos:

1. En la página [Kits de inicio para apps móviles](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo") de la {{site.data.keyword.dev_console}}, seleccione **Crear app**.
2. Especifique un nombre para su app. Para esta guía de aprendizaje, escriba `CustomMobile`.
3. Si lo desea, puede proporcionar etiquetas para clasificar la app. Para obtener más información, consulte [Cómo trabajar con etiquetas](/docs/resources?topic=resources-tag).
4. Seleccione **Crear una app nueva** como punto de partida.
5. Seleccione **Móvil** como tipo de app.
6. Seleccione el lenguaje y la infraestructura. Es posible que algunos kits de inicio solo estén disponibles en un lenguaje.
7. Seleccione el plan de precios. Puede utilizar la opción gratuita para esta guía de aprendizaje.
8. Pulse **Crear**.

## Creación de una app móvil con la CLI
{: #create-mobile-cli}

Para crear una app móvil con la [CLI de {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-getting-started), siga estos pasos:

1. Abra un terminal y vaya al directorio en el que desea crear la app.
2. Ejecute el mandato `ibmcloud dev create`.
3. Seleccione la opción **App móvil** en la lista de tipos de app.
4. Seleccione una plataforma móvil de la lista: Android o Swift.
5. Seleccione un kit de inicio.
6. Especifique un nombre para su app.
7. Si se añaden servicios, se le solicita que seleccione una región y un plan de precios para cada servicio.

La app se crea en el directorio de trabajo actual.

## Adición de servicios (opcional)
{: #resources-mobile}

En función del kit de inicio que haya seleccionado, es posible que algunos servicios ya estén conectados a la app. Puede añadir servicios para mejorar la app con la potencia cognitiva de Watson, para añadir servicios móviles o servicios de seguridad. Para esta guía de aprendizaje, añada un lugar para gestionar los datos.

Para añadir un servicio a la app, siga estos pasos:

1. En la página **Detalles de la app**, pulse **Crear servicio**.
2. Seleccione el tipo de servicio que desee. Por ejemplo, seleccione **Bases de datos** > **Siguiente** > **Cloudant** > **Siguiente**.
3. Seleccione el plan de precios. Utilice la opción **Lite** para esta guía de aprendizaje.
4. Pulse **Crear**.

## Descarga del código
{: #mobile-download-code}

Para descargar el código de app y trabajar con localmente con el mismo, siga estos pasos:

1. En la página **Detalles de la app**, pulse **Descargar código**.
2. Importe la app a su entorno de desarrollo integrado.
3. Modifique y guarde el código.

## Ejecución de la app móvil
{: #run-mobile-app}

### Ejecución de la app Swift en Xcode
{: #run_swift}

Si utiliza iOS Swift como lenguajes de implementación, siga estos pasos:

1. Abra el archivo `README.md` en un visor para archivos Markdown para revisar los pasos para configurar la app.
2. Abra el terminal, vaya a la carpeta de la app y, a continuación, ejecute los siguientes mandatos:
    1. Ejecute `pod setup` si tiene que configurar el repositorio de CocoaPods.
    2. Ejecute `pod update` si tiene que actualizar los pods existentes.
    3. Ejecute `pod install` para instalar los pods para la app.
3. Abra su espacio de trabajo Xcode `<appname>.xcworkspace`.
4. Ejecute la app.

### Ejecución de la app Android en Android Studio
{: #run_android}

Si utiliza Android como plataforma de la app móvil, siga estos pasos:

1. Abra el archivo `README.md` en un visor Markdown para configurar la app.
2. Abra la app `BasicProject-Android` en Android Studio.
3. Ejecute la app.

## Información relacionada
{: #related-mobile}

Puede obtener más información acerca de las apps móviles explorando estas guías de aprendizaje:

 * [Aplicación móvil iOS con notificaciones push](/docs/tutorials?topic=solution-tutorials-ios-mobile-push-analytics)
 * [Aplicación móvil nativa de Android con notificaciones push](/docs/tutorials?topic=solution-tutorials-android-mobile-push-analytics)
 * [Aplicación móvil con un programa de fondo sin servidor](/docs/tutorials?topic=solution-tutorials-serverless-mobile-backend)
