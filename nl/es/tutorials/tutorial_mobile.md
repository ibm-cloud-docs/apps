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

# Creación de una aplicación móvil con un kit de iniciación
{: #tutorial}

Puede crear un proyecto móvil a partir de un iniciador básico móvil. Aprenderá a instalar las herramientas que necesita y los pasos para ejecutar el proyecto en Xcode y Android Studio.
{: shortdesc}

## Instalación de las herramientas
{: #before-you-begin}

Instale las [herramientas de desarrollador](/docs/cli/idt/index.html#add-cli){: new_window}.


## Elija cómo desea crear su proyecto
{: #choose_how}

Puede crear un proyecto con uno de los siguientes métodos:
- [{{site.data.keyword.dev_console}}](#create-devex) basado en la web
- [{{site.data.keyword.dev_cli_notm}}](#create-cli) mediante mandatos locales


## Creación de un proyecto con {{site.data.keyword.dev_console}}
{: #create-devex}

1. Cree un proyecto de {{site.data.keyword.dev_console}} en {{site.data.keyword.Bluemix}}.

    1. En la página [Kits de iniciación ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) en {{site.data.keyword.dev_console}}, seleccione un kit de iniciación con base a las funcionalidades que desee. Por ejemplo, para una aplicación de Watson Language, vaya a **Watson Language** y pulse **Seleccionar kit de iniciación**.

    2. Especifique el nombre del proyecto. En esta guía de aprendizaje, utilice `WatsonProject`.   

    3. Seleccione el lenguaje de la plataforma. En esta guía de aprendizaje, utilizaremos `Swift`.

    4. Pulse **Crear proyecto**.

### Opcional: Añadir servicios
{: #add-services}

1. Seleccione su proyecto en la página **Proyectos**.

2. Pulse **Añadir servicio**.

3. Seleccione el tipo de servicio que desee. Para esta guía de aprendizaje, seleccione **Seguridad** > **Siguiente** > **App ID** > **Siguiente**.

4. Especifique el nombre del servicio y pulse **Crear**.

5. Para obtener más información sobre la configuración de la autenticación, consulte [Configuración de proveedores de identidad ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/appid/identity-providers.html){: new_window}.

6. Para obtener más información sobre la configuración de analíticas, consulte [Iniciación con {{site.data.keyword.mobileanalytics_short}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/mobileanalytics/index.html){: new_window}.

7. Para obtener más información sobre cómo configurar {{site.data.keyword.cloudant_short_notm}}, consulte [Iniciación a {{site.data.keyword.cloudant_short_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/Cloudant/index.html){: new_window}.

8. Para obtener más información sobre cómo configurar {{site.data.keyword.objectstorageshort}}, consulte [Iniciación a {{site.data.keyword.objectstorageshort}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](/docs/services/ObjectStorage/index.html){: new_window}.

9. Para obtener más información sobre cómo añadir notificaciones push, consulte la [documentación de notificaciones](/docs/services/mobilepush/c_overview_push.html#overview-push) Push.

### Generación del código de su proyecto
{: #generate-code}

1. Seleccione su proyecto en la página **Proyectos**.

2. Pulse **Descargar código** para descargar el archivador del proyecto.


### Cómo empezar a trabajar con su app
{: #code}

Empiece a trabajar con el proyecto descargado:

1. Expanda el archivo archivado.

2. Vaya al directorio del nuevo proyecto.

3. Utilice {{site.data.keyword.dev_cli_notm}} para continuar.


## Creación de un proyecto con {{site.data.keyword.dev_cli_notm}}
{: #create-cli}

1. Asegúrese de instalar [{{site.data.keyword.dev_cli_short}}](/docs/cli/idt/index.html).

2. En la solicitud de terminal, vaya al directorio local que prefiera y ejecute el siguiente mandato.

	```
	bx dev create
	```
	{: codeblock}

3. Proporcione los siguientes valores cuando se le solicite:

	* Seleccione un tipo de proyecto "Mobile Client", opción 2.
	* Seleccione un lenguaje de implementación para que sea "iOS Swift", opción 3.
	* Seleccione el kit de iniciación "Mobile App: Basic", opción 1.
	* Especifique el nombre de su proyecto: `MobileBasicProject`.

    Nota: Los números de selección concretos pueden variar dependiendo de las mejoras en las herramientas.

4. Si desea añadir servicios al proyecto, escriba `y` en la solicitud de preguntas y responda el resto de las preguntas.

5. Cuando `MobileBasicProject` se cree y guarde de forma satisfactoria, vaya a la carpeta `MobileBasicProject/MobileBasicProject-Swift`.

### Ejecución de su proyecto Swift en Xcode
{: #run_swift}

1. Abra el archivo `README.md` en un visor para archivos markdown para revisar los pasos para configurar el proyecto.

2. Abra el terminal, vaya a la carpeta del proyecto y, a continuación, ejecute los siguientes mandatos:
    1. Ejecute `pod setup` si tiene que configurar el repositorio de CocoaPods.
    2. Ejecute `pod update` si tiene que actualizar los pods existentes.
    3. Ejecute `pod install` para instalar los pods correspondientes al proyecto.

3. Abra su espacio de trabajo Xcode `<projectname>.xcworkspace`.

4. Ejecute la app.

### Ejecución del proyecto Cordova en Xcode
{: #run_cordova_xcode}

Si opta utilizar Cordova como su lenguaje de implementación, siga estas instrucciones.

1. Abra el archivo `README.md` en un visor Markdown para configurar el proyecto.

2. Abra su proyecto `platforms/ios` en Xcode.

3. Ejecute la app.


### Ejecución del proyecto Cordova en Android Studio
{: #run_cordova_studio}

Utilice esta sección si quiere utilizar Cordova como plataforma de su app móvil.

1. Extraiga el archivo `BasicProject-Cordova.zip`.

2. Abra el archivo `README.md` en un visor Markdown para configurar el proyecto.

3. Abra su proyecto `platforms/android` en Android Studio.

4. Ejecute la app.


### Ejecución del proyecto Android en Android Studio
{: #run_android}

Utilice esta sección si quiere utilizar Android como plataforma de su app móvil.

1. Abra el archivo `README.md` en un visor Markdown para configurar el proyecto.

2. Abra su proyecto `BasicProject-Android` en Android Studio.

3. Ejecute la app.
