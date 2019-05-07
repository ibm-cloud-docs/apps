---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-23"

keywords: getting started apps, create app tutorial, add services, deploy apps, create app, app tutorial

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Guía de aprendizaje de iniciación
{: #tutorial-getting-started}

Puede crear aplicaciones web y móviles listas para la empresa en {{site.data.keyword.cloud}} y aprovechar las extensiones de nube contenidas en {{site.data.keyword.cloud_notm}}. Dispone de varias opciones para comenzar a trabajar. Puede crear una app con un kit de inicio que gestione el proceso en su nombre, o, si sabe exactamente lo que necesita, puede comenzar desde cero y crear su app con los recursos que necesite, o bien puede utilizar el repositorio existente y traer su propio código.
{: shortdesc}

En el caso de que disponga de [código existente](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc) que desee modernizar y traer a la nube o de estar desarrollando una [nueva aplicación](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit), puede acceder al ecosistema de rápido crecimiento de los servicios e infraestructuras de tiempo de ejecución disponibles en {{site.data.keyword.cloud_notm}}.

¿Necesita ayuda para decidir dónde empezar? Consulte este diagrama para buscar ideas.

![Visión general de Experiencia del desarrollador](images/dev-journey.png "Visión general de Experiencia del desarrollador")

## Antes de empezar
{: #prereqs-getting-started}

Puede crear su app mediante la consola de {{site.data.keyword.cloud_notm}} o mediante la interfaz de línea de mandatos (CLI). Si desea utilizar la CLI, consulte los [pasos de instalación](/docs/cli?topic=cloud-cli-ibmcloud-cli).

## Paso 1. Crear su app
{: #create-getting-started}

Para crear una app, seleccione uno de los siguientes puntos de partida:

* Los [kits de inicio](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit) con apps específicas de casos de uso y preparadas para producción en diversos lenguajes de programación y patrones de arquitectura.
* Los [patrones de código de IBM Developer ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://developer.ibm.com/patterns/){:new_window} le ayuda a crear rápidamente la app y a desplegarla en {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte
[Patrones de código](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern).
* [Traiga su propio código](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc) estableciendo un enlace con su propio repositorio de contenido existente. La app y la imagen de Docker deben estar situadas en el mismo repositorio.
* Si sabe lo que quiere, cree una [app personalizada](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch) desde cero con los servicios que necesite utilizando un kit de inicio en blanco.
* Cree y despliegue una app personalizada o de kit de inicio utilizando la
[CLI y herramientas de desarrollador](/docs/apps?topic=creating-apps-create-deploy-app-cli).
* Examine o busque en el [catálogo de {{site.data.keyword.cloud_notm}}](https://{DomainName}/catalog){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") para ver si hay apps y servicios que puede crear y empezar a utilizar hoy.

## Paso 2. Añadir servicios
{: #resources-getting-started}

Si utiliza un kit de inicio para crear su app, los servicios obligatorios se crean automáticamente. Puede conectar más servicios a la app en la consola desde la página **Detalles de la app**, que se visualiza en cuanto como se crea la app.

Si desea añadir servicios después de crear la app, vaya al [panel de control de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}), localice la app y pulse el nombre de la app. Se muestra la página **Detalles de la app** y puede crear una instancia de servicio o conectar los servicios existentes.

O bien, puede ejecutar el mandato siguiente para añadir un servicio a la app utilizando la CLI. Puede seleccionar un servicio existente a partir de uno que ya esté habilitado en su cuenta, o añadir un servicio.
```
ibmcloud dev edit
```
{: codeblock}

Para obtener más información, consulte [Adición de un servicio a la app](/docs/apps?topic=creating-apps-add-resource).

## Paso 3. Desplegar la app
{: #deploy-getting-started}

Puede desplegar la app utilizando la consola o la CLI.

### Utilización de la consola
{: #console-getting-started}

Para desplegar la app mediante la consola, siga los pasos siguientes:

1. En la página **Detalles de la app**, pulse **Configurar entrega continua**.
2. Seleccione un destino de despliegue, seleccione los valores de la cadena de herramientas y pulse **Crear**. {{site.data.keyword.cloud_notm}} crea de forma automática una cadena de herramientas abierta que se completa con un repositorio de Git y un conducto de entrega continua.
3. Abra la etapa del conducto de la nueva cadena de herramientas para ver el proceso de compilación y despliegue de forma que pueda visualizar en unos minutos su nueva app.

Para obtener más información, consulte la tabla de contenido para ver los diversos temas sobre despliegue en la sección "Despliegue e integración de apps".

### Mediante la CLI
{: #cli-getting-started}

Para desplegar la app con la CLI, ejecute el mandato `ibmcloud dev deploy`. Consulte [Creación y despliegue de apps utilizando la CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli) para obtener más información.

Ahora está preparado para el desarrollo iterativo y la entrega continua.

## Información relacionada
{: #related-getting-started}

Las [guías de programación](https://{DomainName}/docs/home/build){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") están disponibles por idioma para ayudarle a empezar a trabajar. Existen muchas formas de alojar apps con la infraestructura de {{site.data.keyword.cloud_notm}} desde {{site.data.keyword.baremetal_short}} para que se ejecuten como una función sin servidor.
