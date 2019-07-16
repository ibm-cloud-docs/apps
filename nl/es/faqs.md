---

copyright:

  years: 2019

lastupdated: "2019-06-03"

keywords: apps FAQs, apps frequently asked questions, applications FAQs, applications frequently asked questions

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}


# Preguntas más frecuentes
{: #apps-faq}

## ¿Qué ha ocurrido con mybluemix.net?
{: #domain-change-faq}
{: faq}

Hay una nueva opción de nombre de host `*.appdomain.cloud` disponible en cloud.ibm.com.

Anteriormente, se utilizaba el dominio `mybluemix.net` para alojar aplicaciones en diversos destinos de despliegue, como {{site.data.keyword.containerlong_notm}} o Cloud Foundry. Las apps que tenga alojadas en `mybluemix.net` no se verán afectadas.

El subdominio para las apps de Cloud Foundry es `cf.appdomain.cloud`. El subdominio para las apps que despliegue en {{site.data.keyword.containerlong_notm}} es `containers.appdomain.cloud`.

Para obtener más información, consulte [Gestión de los dominios](/docs/apps?topic=creating-apps-update-domain).

## ¿Dónde puedo encontrar una lista de mis apps?
{: #cf-app}
{: faq}

Su lista de recursos en la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") proporciona información de resumen de las apps que ha creado. En la lista de recursos, la sección **Apps** contiene todas las apps que ha creado pero que *no* se han desplegado en Cloud Foundry. La sección **Apps de Cloud Foundry** contiene todas las apps que ha creado y desplegado en Cloud Foundry.

## ¿Por qué no puedo seleccionar un espacio de Cloud Foundry cuando intento desplegar mi app?
{: #cf-space}
{: faq}

Es muy probable que necesite crear un espacio de Cloud Foundry en primer lugar. Si utiliza la interfaz de línea de mandatos de Cloud Foundry, escriba `cf create-space <space_name> -o <organization_name>`. De lo contrario, realice estos pasos desde la consola:

1. En la barra de menús de la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo"), seleccione
**Gestionar** > **Cuenta**.
2. Seleccione **Organizaciones de Cloud Foundry**.
3. Pulse sobre el nombre de la organización en la que desee crear el espacio y pulse **Añadir un espacio**.

## ¿Cómo suprimo apps?
{: #delete-apps}
{: faq}

Para suprimir una app que haya creado, siga estos pasos:

1. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo"), pulse el icono **Menú** ![Icono Menú](../icons/icon_hamburger.svg) y seleccione **Lista de recursos**.
2. Pulse el icono **Acciones** ![Icono Acciones](../icons/action-menu-icon.svg) de la app que desee suprimir y pulse **Suprimir**.

## ¿Cómo puedo detener una app de Cloud Foundry en mi cuenta?
{: #app-stop}
{: faq}

Si desea detener una app de Cloud Foundry, siga los siguientes pasos:


1. En el panel de control, pulse **Ver recursos** dentro de la sección de resumen de recursos.
1. En la Lista de recursos, amplíe las secciones y busque la instancia de servicio que desee detener.
1. Seleccione el menú **Acciones** ![Icono Lista de acciones](../icons/action-menu-icon.svg) y pulse **Detener**.

## ¿Qué son las cadenas de herramientas y qué relación tienen con mi app?
{: #toolchains}
{: faq}

Una cadena de herramientas es un conjunto de integraciones de herramientas que dan soporte a tareas de desarrollo, despliegue, y operaciones. Puede crear una cadena de herramientas desde su app. La cadena de herramientas puede soportar tareas continuas de desarrollo, despliegue, supervisión, etc. y está asociada con su app. Cada app se puede asociar con una cadena de herramientas. Se puede configurar una cadena de herramientas de manera que los cambios realizados en la cadena de herramientas creen y desplieguen la app automáticamente. Para obtener más información sobre las cadenas de herramientas, consulte [Creación de cadenas de herramientas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## ¿Cómo cambio el dominio para mis apps de Cloud Foundry?
{: #cf-domains-faq}
{: faq}

Para apps de Cloud Foundry, puede cambiar el dominio de `mybluemix.net` a `appdomain.cloud` utilizando la interfaz de línea de mandatos o la consola de
{{site.data.keyword.cloud_notm}}. Para obtener más información sobre cómo cambiar el dominio a `appdomain.cloud`, consulte
[Actualización del dominio](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).

Al crear nuevas apps, el dominio compartido predeterminado es `mybluemix.net`, pero `appdomain.cloud` es otra opción de dominio que puede utilizar.
