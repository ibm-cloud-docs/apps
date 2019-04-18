---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, Mendix, starter kit, developer tools, Mendix app

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Creación de apps con Mendix
{: #create-mendix}

Mendix es un entorno de desarrollo con poco código y un conjunto de herramientas que le ayuda a entregar aplicaciones de varios dispositivos que se ejecutan en {{site.data.keyword.cloud}} con mayor rapidez y con menos recursos de desarrollo. Si selecciona un kit de inicio Mendix con poco código, se le guía para configurar su cuenta en Mendix Platform, iniciar el proyecto y seleccionar el destino de despliegue de Cloud Foundry o el clúster de Kubernetes.
{: shortdesc}

## Selección de un kit de inicio
{: #starterkit-mendix}

1. En el [panel de control de {{site.data.keyword.cloud_notm}} App Service](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo"), pulse **Iniciación**.
2. Seleccione un kit de inicio de Mendix con poco código de una de las siguientes categorías:
  * [Móvil](https://{DomainName}/developer/appservice/starter-kits/mendix-mobile-app){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
  * [Watson Web o Mobile App](https://{DomainName}/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
  * [App Web](https://{DomainName}/developer/appservice/starter-kits/mendix-web-app){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
3. Pulse **Crear app**.
4. En la página **Detalles de la app**, asigne un nombre a la app y, si lo desea, especifique etiquetas para clasificar la app. Para obtener más información, consulte [Cómo trabajar con etiquetas](/docs/resources?topic=resources-tag).
5. Pulse **Crear**.


## Autorización a IBM para crear su proyecto en Mendix y para enlazar cuentas
{: #link-mendix-account}

Si aún no está utilizado Mendix con {{site.data.keyword.cloud_notm}}, se le guiará por la plataforma Mendix para que registre y autorice a {{site.data.keyword.cloud_notm}} a crear un nuevo proyecto en la plataforma Mendix en su nombre. Este proyecto está enlazado a {{site.data.keyword.cloud_notm}}, por lo que los despliegues se dirigen automáticamente a {{site.data.keyword.cloud_notm}}.

1. Si ve un mensaje que indica que "Para completar la creación de la app se necesita una cuenta de usuario de Mendix. ¿Desea enlazar su cuenta ahora?", pulse **Enlazar cuenta**.
2. En la página de confirmación de Mendix, seleccione **Acepto la política de privacidad y las condiciones de Mendix** y pulse **Confirmar**.
3. Cuando se le solicite, especifique su dirección de correo electrónico, su contraseña y su país, y luego pulse **Crear**.
4. En la página **Autorizar acceso a la cuenta de Mendix**, pulse **Autorizar**.

Una vez que se haya completado la autorización, el navegador vuelve a la app Mendix que está creando. Se abrirá la página **Seleccionar un destino de despliegue**.

## Selección de un destino de despliegue para la app Mendix
{: #select-deployment}

1. En la página **Seleccionar un destino de despliegue**, seleccione Cloud Foundry o uno de los clústeres de Kubernetes que se ejecutan en {{site.data.keyword.cloud_notm}}. Si la cuenta tiene acceso a {{site.data.keyword.cfee_full_notm}}, puede seleccionar el tipo de desplegador de Cloud Foundry **[nube pública](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)** o **[entorno de empresa](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**, que puede utilizar para crear y gestionar entornos aislados para alojar aplicaciones de Cloud Foundry exclusivamente para su empresa.
2. Opcional. Si no tiene un clúster de Kubernetes, puede crear uno ahora.
3. En la página **Configurar cadena de herramientas**, seleccione su región y grupo de recursos y, a continuación, pulse **Crear**.

Se crea una cadena de herramientas DevOps. La cadena de herramientas integra el proyecto Mendix dentro de la plataforma Mendix en el entorno de {{site.data.keyword.cloud_notm}}. Se despliega una aplicación predeterminada en el destino de despliegue, de modo que pueda verificar que la aplicación se ha desplegado correctamente al finalizar la cadena de herramientas DevOps.

Los despliegues de Mendix Cloud Foundry requieren el servicio de base de datos PostGRES, que no tiene un nivel Lite. Si desea evaluar los kits de inicio de Mendix utilizando una cuenta Lite, puede elegir como destino un clúster de Kubernetes de prueba.
{: tip}

Si ha seleccionado un clúster de Kubernetes para el despliegue, consulte la [guía de aprendizaje de Mendix Kubernetes](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube) para aprender a configurar el clúster para su uso en producción.


## Continuación con el ciclo de vida de desarrollo y de despliegue de Mendix
{: #dev-lifecycle-mendix}

Mendix es un entorno de creación con poco código. El ciclo de vida de desarrollo requiere que abra el proyecto en la aplicación de escritorio Mendix Modeler.

1. Desde la aplicación {{site.data.keyword.cloud_notm}}, pulse **Editar en Mendix**.
2. En el portal web de Mendix, pulse **Editar en Desktop Modeler**.
  La aplicación Mendix se abre en el modelador de escritorio.
3. Edite la app Mendix y guarde los cambios.
4. Utilice el menú **Ejecutar** de la aplicación Mendix Desktop Modeler y seleccione la opción **Ejecutar**.
  El paquete de despliegue se crea y se carga en Mendix. Una vez que se haya creado el paquete de despliegue, puede desplegar la aplicación en {{site.data.keyword.cloud_notm}}.
5. Para desplegar la aplicación Mendix, vuelva a la página **Detalles de app** en {{site.data.keyword.cloud_notm}} y pulse **Desplegar**.
  Esta acción inicia la cadena de herramientas de DevOps de la aplicación, que obtiene el despliegue más reciente de Mendix y lo despliega en el entorno de destino. Una vez finalizado el despliegue, la versión más reciente de la aplicación se inicia automáticamente y pasa a estar disponible.

Todas las aplicaciones Mendix se despliegan en {{site.data.keyword.cloud_notm}} pulsando **Configurar entrega continua** en la página **Detalles de app** en {{site.data.keyword.cloud_notm}}. No invoque manualmente cadenas de herramientas de Mendix a través de la interfaz de IBM DevOps. Si se inician manualmente cadenas de herramientas a través de la interfaz de DevOps, es posible que el despliegue falle debido a una falta de los metadatos necesarios que resultan críticos para los despliegues de Mendix. En función del estado de la aplicación, es posible que se produzca un error durante el inicio de la cadena de herramientas de DevOps o un error en la aplicación desplegada. Si inicia manualmente una cadena de herramientas y se produce un error, puede restaurar la aplicación pulsando **Configurar entrega continua** en la página **Detalles de la app** en {{site.data.keyword.cloud_notm}}. Esta acción desencadena un flujo de DevOps completo para la aplicación Mendix, que incluye los metadatos necesarios.
{: tip}

## Pasos siguientes 
{: #next-steps-mendix}

Para desplegar la app en {{site.data.keyword.containerlong_notm}}, configure la app para el despliegue en producción. Para obtener más información, consulte la [guía de aprendizaje de Mendix Kubernetes](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube). 
