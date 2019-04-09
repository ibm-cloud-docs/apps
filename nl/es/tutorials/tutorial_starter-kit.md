---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creación de una app con un kit de inicio
{: #create_starterkit}

Utilice un kit de inicio para empezar rápidamente su app y prepárela para el futuro desarrollo. Seleccione un kit de inicio y un lenguaje de programación, cree una app y configure una cadena de herramientas de DevOps para desplegar su app automáticamente. También puede descargar el código para una inspección inmediata.
{: shortdesc}

Puede crear una app desde una selección de kits de inicio, incluido uno en blanco si desea personalizar las opciones de compilación usted mismo. En cualquiera de los casos, se crea automáticamente una cadena de herramientas DevOps para desplegar la app. También puede descargar el código para una inspección inmediata.

Los kits de inicio están disponibles para muchas categoría, entre otras:
* [Watson ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/developer/watson/dashboard){:new_window}
* [Apple ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/developer/appledevelopment/dashboard){:new_window}
* [Móvil ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/developer/mobile/dashboard){:new_window}
* [App Web ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/developer/appservice/dashboard){:new_window}
* [Seguridad ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/developer/security/dashboard){:new_window}
* [Finanzas ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/developer/finance/dashboard){:new_window}

## Paso 1. Crear una app
{: #create-app}

1. En el [panel de control de {{site.data.keyword.cloud}}](https://{DomainName}), pulse el icono **Menú** ![Icono Menú](../../icons/icon_hamburger.svg) > **Apps web**.

2. Pulse **Iniciación** en la sección **Empezar desde web**.

3. Seleccione el kit de inicio que desee, lea los detalles y pulse **Crear**.
    
    Para ver lo que se incluye en el kit de inicio, expanda el mosaico del panel de control [Kits de inicio de servicio de app ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/developer/appservice/starter-kits){:new_window}. La opción del kit de inicio "Crear app" se puede utilizar como app de inicio en blanco y se puede personalizar para que se ajuste a sus necesidades.
    {: tip}

4. Proporcione un nombre para la app, seleccione el idioma y pulse **Crear**.
    
    Acaba de crear una app.

Para inspeccionar el código, pulse **Descargar código** en la página de detalles de la app. Consulte el archivo `README.md` del archivo comprimido descargado para averiguar si es necesario realizar algo más para ejecutar su app de inicio.
{: tip}

Para obtener más información, consulte [Creación de una app web básica con un kit de inicio](/docs/apps/tutorials/tutorial_web.html).

## Paso 2. Adición de recursos
{: #add-services}

Puede añadir recursos para mejorar la app con la potencia cognitiva de Watson, para añadir servicios móviles o servicios de seguridad. Para esta guía de aprendizaje, añada un lugar para gestionar los datos.

1. En la ventana de servicio de la app, pulse **Añadir recurso**.
2. Seleccione el tipo de servicio que desee. Por ejemplo, seleccione **Datos** > **Siguiente** > **Cloudant** > **Siguiente**.
3. Seleccione el plan de precios. Hay una opción gratuita que puede utilizar para esta guía de aprendizaje.
4. Pulse **Crear**.

## Paso 3. Desplegar en {{site.data.keyword.cloud_notm}}
{: #deploy}

Pulse **Desplegar en la nube** en la página de detalles de la app, seleccione un método de despliegue, como por ejemplo clúster de Kubernetes o app de Cloud Foundry, y pulse **Crear**. {{site.data.keyword.cloud_notm}} crea de forma automática una cadena de herramientas abierta que se completa con un repositorio de Git y un conducto de entrega continua. Abra el componente del conducto de la nueva cadena de herramientas para iniciar el proceso de compilación y despliegue inicial de forma que pueda visualizar en unos minutos su nueva app.

Para desplegar la app con la línea de mandatos, utilice `ibmcloud dev deploy`. Consulte [Creación y despliegue de apps utilizando la CLI](/docs/apps/create-deploy-cli.html) para obtener más información.
