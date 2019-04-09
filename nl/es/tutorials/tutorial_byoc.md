---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

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

 * Instale la [interfaz de línea de mandatos (CLI) de {{site.data.keyword.dev_cli_long}}](/docs/cli/index.html#overview).
 * Consulte [¿Qué hace que una app sea buena?](/docs/apps/best-practice.html#best-practice) para ver las prácticas recomendadas para crear apps.
 * Debe tener un repositorio de código fuente Git de cualquiera de estos proveedores: GitHub, GitHub Enterprise, Git lab, BitBucket o Rational.
 * Si tiene intención de desplegar la app en [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about), debe [preparar la cuenta de {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry/prepare-account.html#prepare).

## Paso 1. Crear una app con un repositorio existente
{: #create-byoc}

Para crear una app y conectarla con el repositorio de origen, siga estos pasos:

1. En el [panel de control ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}){: new_window}, pulse **Crear una app** en el mosaico **Apps**.
2. Asigne un nombre a la app, seleccione un grupo de recursos y, si lo desea, proporcione etiquetas para clasificar la app. Para obtener más información, consulte [Cómo trabajar con etiquetas](/docs/resources/tagging_resources.html#tag).
3. Seleccione **Traiga su propio código** y proporcione el URL al repositorio Git. La app y la imagen de Docker deben estar situadas en el mismo repositorio.
4. Pulse **Crear**.

Se muestra la página **Detalles de la app**. Desde aquí puede:
* [Añadir recursos](/docs/apps/reqnsi.html#add-resource) (opcional).
* Si ha proporcionado etiquetas al crear la app, puede editarlas pulsando el icono **Editar** ![Icono Editar](../../icons/edit-tagging.svg) que hay junto a las etiquetas mostradas.
* Conectar la app a una cadena de herramientas de DevOps pulsando **Conectar a la cadena de herramientas de DevOps**. Si aún no tiene una cadena de herramientas, se abrirá la página **Conectar cadena de herramientas de DevOps**. Pulse **Crear cadena de herramientas de DevOps**. En este punto, se abre la página [Crear una cadena de herramientas](https://{DomainName}/devops/create) en el [panel de control de DevOps](https://{DomainName}/devops/) en un nuevo separador del navegador. Después de crear y configurar la cadena de herramientas en dicho separador, debe volver a la página **Conectar una cadena de herramientas** en la app y renovar la página.
* Para ver el repositorio, pulse **Ver repositorio.**
* Obtener más información sobre las cadenas de herramientas o sobre experiencias de creación de app pulsando cualquiera de los enlaces relacionados en la página **Detalles de la app**.

## Paso 2. Conectar la app a una cadena de herramientas de DevOps
{: #toolchain-byoc}

El establecimiento de un enlace entre la app, la cadena de herramientas y el repositorio es un paso encaminado a organizar los activos del producto. También ayuda a agregar una vista de su origen con el flujo de trabajo de DevOps, las instancias de la app en ejecución y los servicios dependientes en todos los destinos de despliegue. Para obtener más información, consulte [Creación de cadenas de herramientas](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

Puede conectar la app a una cadena de herramientas de DevOps mediante la consola de {{site.data.keyword.cloud_notm}} o la CLI.

### Utilización de la consola
{: #console-byoc-toolchain}

  1. Conecte la app a una cadena de herramientas de DevOps pulsando **Conectar a la cadena de herramientas de DevOps**. 
  
    Si no dispone de una cadena de herramientas existente, pulse **Crear cadena de herramientas de DevOps**. 
    
  2. Después de crear y configurar la cadena de herramientas, vuelva a la página Conectar una cadena de herramientas en la app y renueve la página. 

### Mediante la CLI

Puede utilizar el mandato `ibmcloud dev enable` para generar una plantilla de cadena de herramientas de DevOps que incorpora al repositorio como conjunto de instrucciones sobre lo que debe crear la cadena de herramientas de DevOps. 

  1. En la ventana de servicio de la app, pulse **Descargar código** o **Clonar el repositorio** para trabajar con el código localmente.
  2. Ejecute el mandato siguiente:
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

Consulte [Creación y despliegue de apps utilizando la CLI](/docs/apps/create-deploy-cli.html#create-deploy-app-cli) para obtener más información.

## Paso 3. Desplegar la app
{: #deploy-byoc}

Después de adjuntar una cadena de herramientas de DevOps a la app, siga los pasos siguientes para desplegarla en {{site.data.keyword.cloud_notm}}: 

1. En la página Detalles de la app, pulse **Desplegar en la nube**.
2. Seleccione un método de despliegue. Configure el método de despliegue de acuerdo con las instrucciones correspondientes al método que elija:
  * **Desplegar en [Kubernetes](/docs/apps/deploying/containers.html#containers)**. Esta opción crea un clúster de hosts, denominado nodos trabajadores, para desplegar y gestionar contenedores de aplicaciones de alta disponibilidad. Puede crear un clúster o desplegar en un clúster existente.
  * **Desplegar en Cloud Foundry**. Esta opción despliega la app nativa de la nube sin necesidad de gestionar la infraestructura subyacente. Si la cuenta tiene acceso a {{site.data.keyword.cfee_full_notm}}, puede seleccionar el tipo de desplegador de **[nube pública](/docs/cloud-foundry-public/about-cf.html#about-cf)** o de **[entorno de empresa](/docs/cloud-foundry-public/cfee.html#cfee)**, que puede utilizar para crear y gestionar entornos aislados para alojar aplicaciones de Cloud Foundry exclusivamente para su empresa.
  * **Desplegar en un [servidor virtual](/docs/apps/vsi-deploy.html#vsi-deploy)**. Esta opción proporciona una instancia de servidor virtual, carga una imagen que incluye la app, crea una cadena de herramientas DevOps e inicia automáticamente el primer ciclo de despliegue.


