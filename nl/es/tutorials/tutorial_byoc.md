---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, byoc, code repository, continuous delivery, cli, deploy

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Creación de apps desde su propio repositorio de código
{: #tutorial-byoc}

Puede crear una aplicación en {{site.data.keyword.cloud}} utilizando su repositorio de aplicaciones existente. Simplemente proporcione el enlace web a su repositorio durante la creación de la aplicación, continúe añadiendo recursos y, a continuación, conecte una cadena de herramientas de DevOps a la aplicación para su despliegue.
{: shortdesc}

## Antes de empezar
{: #prereqs-byoc}

Asegúrese de que cumple con los siguientes requisitos previos:

 * Instale la [interfaz de línea de mandatos (CLI) de {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).
 * Consulte [¿Qué hace que una app sea buena?](/docs/apps?topic=creating-apps-best-practice) para ver las prácticas recomendadas para crear apps.
 * Debe tener un repositorio de código fuente Git de cualquiera de estos proveedores: GitHub, GitHub Enterprise, Git lab, BitBucket o Rational.
 * Si tiene intención de desplegar la app en [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), debe [preparar la cuenta de {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Paso 1. Crear una app con un repositorio existente
{: #create-byoc}

Para crear una app y conectarla con el repositorio de origen, siga estos pasos:

1. En el [panel de control](https://{DomainName}){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo"), pulse **Crear una app** en el mosaico **Apps**.
2. Asigne un nombre a la app, seleccione un grupo de recursos y, si lo desea, proporcione etiquetas para clasificar la app. Para obtener más información, consulte [Cómo trabajar con etiquetas](/docs/resources?topic=resources-tag).
3. Seleccione **Traiga su propio código** y proporcione el URL al repositorio Git. La app y la imagen de Docker deben estar situadas en el mismo repositorio.
4. Pulse **Crear**. Se muestra la página **Detalles de la app**.
5. Opcional. [Añada servicios](/docs/apps?topic=creating-apps-add-resource) a la app.
6. Opcional. Si ha proporcionado etiquetas al crear la app, puede editarlas pulsando el icono **Editar** ![Icono Editar](../../icons/edit-tagging.svg) que hay junto a las etiquetas mostradas.
7. Opcional. Para ver el repositorio, pulse **Ver repositorio.**

## Paso 2. Desplegar la app
{: #toolchain-byoc}

El establecimiento de un enlace entre la app, la cadena de herramientas y el repositorio es un paso encaminado a organizar los activos del producto. También ayuda a agregar una vista de su origen con el flujo de trabajo de DevOps, las instancias de la app en ejecución y los servicios dependientes en todos los destinos de despliegue. Para obtener más información, consulte [Creación de cadenas de herramientas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

Puede configurar la entrega continua para la app utilizando la consola o la CLI de {{site.data.keyword.cloud_notm}}.

### Utilización de la consola
{: #console-byoc-toolchain}

  1. En la página **Detalles de la app**, conecte la app a una cadena de herramientas de DevOps pulsando **Configurar entrega continua**. Aparecerá la página **Desplegar mi app**.
  2. Si no dispone de una cadena de herramientas existente, pulse **Crear una cadena de herramientas**. Tras crear la cadena de herramientas, utilice el rastro de navegación para volver a la página **Detalles de la app**, que indica que se ha configurado la entrega continua.
  3. Si tiene una cadena de herramientas existente, selecciónela y, a continuación, pulse **Habilitar despliegue**. Aparecerá la página **Detalles de la app**, que indica que se ha configurado la entrega continua.

### Mediante la CLI

Puede utilizar el mandato `ibmcloud dev enable` para generar una plantilla de cadena de herramientas de DevOps que incorpora al repositorio como conjunto de instrucciones sobre lo que debe crear la cadena de herramientas de DevOps. 

  1. En la página **Detalles de la app**, pulse **Ver repositorio**.
  2. Ejecute el mandato siguiente:
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

Consulte [Creación y despliegue de apps utilizando la CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli) para obtener más información.

