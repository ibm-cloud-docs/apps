---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-30"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creación de una app con un kit de inicio
{: #tutorial-starterkit}

Utilice un kit de inicio para empezar rápidamente su aplicación y prepárela para el futuro desarrollo. Seleccione un kit de inicio y un lenguaje de programación, cree una app y configure una cadena de herramientas de DevOps para desplegar su app automáticamente. También puede descargar el código para una inspección inmediata.
{: shortdesc}

Puede crear una app desde una selección de kits de inicio, incluido uno en blanco si desea personalizar las opciones de compilación usted mismo. En cualquiera de los casos, se crea automáticamente una cadena de herramientas DevOps para desplegar la app. También puede descargar el código para una inspección inmediata.

{{site.data.keyword.cloud_notm}} tiene portales de desarrollador en distintas áreas de interés (por ejemplo, Watson, Seguridad o Finanzas) o para un canal digital (como por ejemplo, apps móviles o web). Puede acceder a estos portales desde el icono **Menú**
![Icono Menú](../../icons/icon_hamburger.svg).

Cada portal de desarrollador proporciona kits de inicio relevantes para el área de atención del portal. Los portales ofrecen flujos de trabajo coherentes e intuitivos para crear una app lista para producción en cuestión de minutos.

Los kits de inicio están disponibles para muchas categoría, entre otras:
* [Watson](https://{DomainName}/developer/watson/dashboard){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
* [Apple](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
* [Móvil](https://{DomainName}/developer/mobile/dashboard){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
* [App Web](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
* [Seguridad](https://{DomainName}/developer/security/dashboard){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
* [Finanzas](https://{DomainName}/developer/finance/dashboard){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")

[Más información](/docs/apps?topic=creating-apps-starter-kits) acerca de los kits de inicio.

## Paso 1. Crear una app
{: #create-starterkit}

1. En el [panel de control de {{site.data.keyword.cloud}}](https://{DomainName}){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo"), pulse el icono
**Menú** ![Icono Menú](../../icons/icon_hamburger.svg) > **Apps web**.

2. Pulse **Iniciación** en la sección **Empezar desde web**.

3. Seleccione el kit de inicio que desee, lea los detalles y pulse **Crear**.
    
    Para ver lo que se incluye en el kit de inicio, expanda el mosaico del panel de control [Kits de inicio de servicio de app](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo"). La opción del kit de inicio "Crear app" se puede utilizar como app de inicio en blanco y se puede personalizar para que se ajuste a sus necesidades.
    {: tip}

4. Proporcione un nombre para la app, seleccione un grupo de recursos, si lo desea proporcione etiquetas, seleccione el idioma y pulse **Crear**.
    
    Acaba de crear una app.

Para inspeccionar el código, pulse **Descargar código** en la página **Detalles de la app**. Consulte el archivo `README.md` del archivo comprimido descargado para averiguar si es necesario realizar algo más para ejecutar su app de inicio.
{: tip}

Para obtener más información, consulte los siguientes temas:
 * [Creación de una app web básica con un kit de inicio](/docs/apps/tutorials?topic=creating-apps-tutorial-webapp)
 * [Cómo trabajar con etiquetas](/docs/resources?topic=resources-tag)

## Paso 2. Añadir servicios
{: #resources-starterkit}

Puede añadir servicios para mejorar la app con la potencia cognitiva de Watson, para añadir servicios móviles o servicios de seguridad. Para esta guía de aprendizaje, añada un lugar para gestionar los datos.

1. En la página **Detalles de la app**, pulse **Añadir servicio**.
2. Seleccione el tipo de servicio que desee. Por ejemplo, seleccione **Datos** > **Siguiente** > **Cloudant** > **Siguiente**.
3. Seleccione el plan de precios. Hay una opción gratuita que puede utilizar para esta guía de aprendizaje.
4. Pulse **Crear**.

## Paso 3. Desplegar en {{site.data.keyword.cloud_notm}}
{: #deploy-starterkit}

Pulse **Configurar entrega continua** en la página **Detalles de la app**, seleccione un destino de
despliegue y pulse **Crear**. {{site.data.keyword.cloud_notm}} crea de forma automática una cadena de herramientas abierta que se completa con un repositorio de Git y un conducto de entrega continua.

La habilitación de una cadena de herramientas crea un entorno de desarrollo en equipo para la app. Cuando se crea una cadena de herramientas, el servicio de app crea un repositorio Git, donde puede ver el código fuente, clonar la app y crear y gestionar problemas. También es posible acceder a un entorno de laboratorio Git dedicado y a un conducto de entrega continua. Están personalizados para el destino de despliegue que seleccione, que puede ser [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) o [Servidor virtual (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers).

Después de seleccionar el destino de despliegue, abra el componente del conducto de la nueva cadena de herramientas para iniciar el proceso de compilación y despliegue inicial de forma que pueda visualizar en unos minutos su nueva app.

Todas las cadenas de herramientas creadas a partir de un panel de control de desarrollador de {{site.data.keyword.cloud_notm}} se configuran para un despliegue automático.
{: note}

Para desplegar la app con la línea de mandatos, utilice `ibmcloud dev deploy`. Consulte [Creación y despliegue de apps utilizando la CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli) para obtener más información.

Para obtener más información sobre cómo desplegar la app, consulte
[Despliegue de apps](/docs/apps?topic=creating-apps-deploying-apps).
