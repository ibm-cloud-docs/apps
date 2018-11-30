---

copyright:
  years: 2018
lastupdated: "2018-11-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Creación de apps con Mendix
{: #getting-started}

Mendix es un entorno de desarrollo con poco código y un conjunto de herramientas que le ayuda a entregar aplicaciones de varios dispositivos que se ejecutan en {{site.data.keyword.cloud}} con mayor rapidez y con menos recursos de desarrollo. Si selecciona un kit de inicio Mendix con poco código, se le guía para configurar su cuenta en Mendix Platform, iniciar el proyecto y seleccionar el entorno de despliegue en Cloud Foundry o en el clúster de Kubernetes.
{: shortdesc}

## Selección de un kit de inicio
{: #select-a-starter-kit}

2. En el [panel de control de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/dashboard/apps){: new_window}, pulse el icono **Menú** ![Icono Menú](../../icons/icon_hamburger.svg).
3. Seleccione un kit de inicio de Mendix con poco código de una de las siguientes categorías:
  * [Móvil ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/developer/appservice/starter-kits/mendix-mobile-app)
  * [Watson Web o Mobile App ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson)
  * [App Web ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://console.bluemix.net/developer/appservice/starter-kits/mendix-web-app)
4. Pulse **Crear app**.
5. Asigne un nombre a la app. 
6. Pulse **Crear**.

## Autorización a IBM para crear su proyecto en Mendix y para enlazar cuentas
{: #link-mendix-account}

Si aún no está utilizado Mendix con {{site.data.keyword.cloud_notm}}, se le guiará por la plataforma Mendix para que registre y autorice a {{site.data.keyword.cloud_notm}} a crear un nuevo proyecto en la plataforma Mendix en su nombre. Este proyecto está enlazado a {{site.data.keyword.cloud_notm}}, por lo que los despliegues se dirigen automáticamente a {{site.data.keyword.cloud_notm}}.

1. Si ve un mensaje que indica que "Para completar la creación de la app se necesita una cuenta de usuario de Mendix. ¿Desea enlazar su cuenta ahora?", pulse **Enlazar cuenta**.
2. En la página de confirmación de Mendix, seleccione **Acepto la política de privacidad y las condiciones de Mendix** y pulse **Confirmar**.
3. Cuando se le solicite, especifique su dirección de correo electrónico, su contraseña y su país, y luego pulse **Crear**.
4. En la página **Autorizar acceso a la cuenta de Mendix**, pulse **Autorizar**.

Una vez que se haya completado la autorización, el navegador vuelve a la app Mendix que está creando. Se visualiza la página **Elegir un entorno de despliegue**.

## Selección de una opción de despliegue para la app Mendix
{: #select-deployment}

1. En la página **Elegir un entorno de despliegue**, seleccione Cloud Foundry o uno de los clústeres de Kubernetes que se ejecutan en {{site.data.keyword.cloud_notm}}.
2. Opcional. Si no tiene un clúster de Kubernetes, puede crear uno ahora.
3. En la página **Configurar cadena de herramientas**, seleccione su región y grupo de recursos y, a continuación, pulse **Crear**.

Se crea una cadena de herramientas DevOps. La cadena de herramientas integra el proyecto Mendix dentro de la plataforma Mendix en el entorno de {{site.data.keyword.cloud_notm}}. Se despliega una aplicación predeterminada en el despliegue de destino de modo que pueda verificar que la aplicación se ha desplegado correctamente al finalizar la cadena de herramientas DevOps.

Los despliegues de Mendix Cloud Foundry requieren el servicio de base de datos PostGRES, que no tiene un nivel Lite.   Si desea evaluar los kits de inicio de Mendix utilizando una cuenta Lite, puede elegir como destino un clúster de Kubernetes de prueba.
{: tip}

Si ha seleccionado un clúster de Kubernetes para el despliegue, consulte la [guía de aprendizaje de Mendix Kubernetes](/docs/apps/tutorials/tutorial_mendix_kubernetes.html) para aprender a configurar el clúster para su uso en producción.


## Continuación con el ciclo de vida de desarrollo y de despliegue de Mendix
{: #development-lifecycle}

Mendix es un entorno de creación con poco código. El ciclo de vida de desarrollo requiere que abra el proyecto en la aplicación de escritorio Mendix Modeler.

1. Desde la aplicación {{site.data.keyword.cloud_notm}}, pulse **Editar en Mendix**.
2. En el portal web de Mendix, pulse **Editar en Desktop Modeler**.
  La aplicación Mendix se abre en el modelador de escritorio.
3. Edite el app Mendix y guarde los cambios.
4. Utilice el menú **Ejecutar** de la aplicación Mendix Desktop Modeler y seleccione la opción **Ejecutar**.
  El paquete de despliegue se crea y se carga en Mendix. Una vez que se haya creado el paquete de despliegue, puede desplegar la aplicación en {{site.data.keyword.cloud_notm}}.
5. Para desplegar la aplicación Mendix, vuelva a la página **Detalles de app** en {{site.data.keyword.cloud_notm}} y pulse **Desplegar aplicación**.
  Esta acción inicia la cadena de herramientas de DevOps de la aplicación, que obtiene el despliegue más reciente de Mendix y lo despliega en el entorno de destino. Una vez finalizado el despliegue, la versión más reciente de la aplicación se inicia automáticamente y pasa a estar disponible.

Todas las aplicaciones Mendix se despliegan en {{site.data.keyword.cloud_notm}} pulsando **Desplegar aplicación** en la página **Detalles de app** en {{site.data.keyword.cloud_notm}}. No invoque manualmente cadenas de herramientas de Mendix a través de la interfaz de IBM DevOps. Si se inician manualmente cadenas de herramientas a través de la interfaz de DevOps, es posible que el despliegue falle debido a una falta de los metadatos necesarios que resultan críticos para los despliegues de Mendix. En función del estado de la aplicación, es posible que se produzca un error durante el inicio de la cadena de herramientas de DevOps o un error en la aplicación desplegada. Si inicia manualmente una cadena de herramientas y se produce un error, puede restaurar la aplicación pulsando **Desplegar aplicación** en la página **Detalles de app** en {{site.data.keyword.cloud_notm}}. Esta acción desencadena un flujo de DevOps completo para la aplicación Mendix, que incluye los metadatos necesarios.
{: tip}

## Pasos siguientes 
{: #next steps}

Para desplegar la app en {{site.data.keyword.containerlong_notm}}, configure la app para el despliegue en producción. Para obtener más información, consulte [Guía de aprendizaje de Mendix Kubernetes](/docs/apps/tutorials/tutorial_mendix_kubernetes.html). 
