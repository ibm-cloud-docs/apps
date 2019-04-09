---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Creación de una app con un patrón de código
{: #tutorial-codepattern}

Puede utilizar un patrón de código para crear rápidamente una app y desplegarla en {{site.data.keyword.cloud}}. Puede ver el código en GitHub o crear y compilar una app en {{site.data.keyword.cloud_notm}}, donde puede utilizar una cadena de herramientas de DevOps para desplegar automáticamente la app.
{: shortdesc}

## Paso 1. Crear una app
{: #create-codepattern}

1. Vaya a [IBM Developer ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/patterns/){:new_window} y seleccione el patrón de código que desee. Por ejemplo, puede seleccionar el patrón de código [Crear una app web MEAN ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/patterns/build-a-mean-web-app/){:new_window}.

2. Lea la descripción del patrón de código y visualice el repositorio GitHub y el archivo `README.md`. Para ver el repositorio, pulse **Obtener el código**, lo que abre el repositorio GitHub correspondiente al patrón de código.

3. Comience a crear una app utilizando cualquiera de las siguientes opciones. Cualquiera de las opciones abre la página **Crear app** correspondiente al patrón de código.
    * En la página del patrón de código, pulse el enlace para crear una app en {{site.data.keyword.cloud_notm}}. 
    * En el archivo `README.md` en el repositorio GitHub, pulse el enlace para utilizar un kit de inicio para crear la app. 

4. En la página **Crear app**, asigne un nombre a la app, seleccione un grupo de recursos, si lo desea proporcione etiquetas y pulse **Crear**. Para obtener más información sobre las etiquetas, consulte [Cómo trabajar con etiquetas](/docs/resources/tagging_resources.html#tag).

  Para volver al patrón de código, pulse **Ver patrón de código**. Consulte el archivo `README.md` del repositorio para averiguar si es necesario realizar algo más para activar y ejecutar su app.
  {: tip}

## Paso 2. Añadir recursos
{: #resources-codepattern}

Puede añadir recursos para mejorar la app con la potencia cognitiva de Watson, para añadir servicios móviles o servicios de seguridad. El proceso crea una instancia de recurso, crea una clave de recurso (credenciales) y la enlaza a la app. Para esta guía de aprendizaje, añada un lugar para gestionar los datos.

1. En la página **Detalles de la app**, pulse **Añadir recurso**.
2. Seleccione el tipo de recurso que desee. 
3. Seleccione el plan de precios. Dispone de una opción lite.
4. Pulse **Crear**.

## Paso 3. Copiar las credenciales de servicio en el entorno

Después de añadir un recurso a la app, o si se necesita algún servicio para la app, tenga en cuenta que las credenciales para dicho servicio se muestran en el recuadro **Credenciales**. Debe copiar manualmente las credenciales en el entorno de despliegue.

Para obtener más información sobre cómo copiar credenciales en el entorno, consulte [Visión general de las credenciales](/docs/apps/creds_overview.html#credentials_overview).

## Paso 4. Desplegar en {{site.data.keyword.cloud_notm}}
{: #deploy-codepattern}

Puede desplegar la app en {{site.data.keyword.cloud_notm}} de varias formas, pero una cadena de herramientas de DevOps es la mejor forma de desplegar apps de producción. Con una cadena de herramientas de DevOps, puede automatizar fácilmente despliegues en muchos entornos y añadir rápidamente servicios de supervisión, de registro y de alertas para ayudar a gestionar su app a medida que crece.

La habilitación de una cadena de herramientas crea un entorno de desarrollo en equipo para la app. Cuando se crea una cadena de herramientas, el servicio de app crea un repositorio Git, donde puede ver el código fuente, clonar la app y crear y gestionar problemas. También es posible acceder a un entorno de laboratorio Git dedicado y a un conducto de entrega continua. Están personalizados para el entorno de desarrollo que elija, que puede ser [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) o [Servidor virtual (VSI)](/docs/vsi/vsi_index.html).}

1. En la página **Detalles de la app**, pulse **Desplegar en la nube**.
2. Seleccione un método de despliegue y pulse **Crear**. {{site.data.keyword.cloud_notm}} crea de forma automática una cadena de herramientas abierta que se completa con un repositorio de Git y un conducto de entrega continua.
3. Abra la etapa del conducto de la nueva cadena de herramientas para ver el proceso de compilación y despliegue de forma que pueda visualizar en unos minutos su nueva app.

Para obtener más información sobre los métodos de despliegue, compilaciones y conductos, consulte [Creación y despliegue](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy).
