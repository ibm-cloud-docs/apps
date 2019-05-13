---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-30"

keywords: byoc, code repository, continuous delivery, cli, deploy, create app custom repo, custom repo, existing repo, custom code

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

Si dispone de una aplicación en un repositorio existente, puede utilizar un kit de inicio vacío para crear un registro de app en {{site.data.keyword.cloud_notm}} y conectarlo al repositorio de origen y una cadena de herramientas de DevOps.
{: shortdesc}

Puede empezar desde el panel de control de {{site.data.keyword.cloud_notm}} o desde cualquier kit de inicio vacío. Después de dar un nombre a la app y seleccionar un grupo de recursos, seleccione el punto de inicio **Traiga su propio código**, proporcione el URL de repositorio Git que contiene el código y pulse en **Crear**.

Puede volver a conectar su cadena de herramientas DevOps existente o crear una y entregar de forma continua la app al destino de despliegue que elija, como Kubernetes o Cloud Foundry.

## Antes de empezar
{: #prereqs-byoc}

Asegúrese de que cumple con los siguientes requisitos previos:

 * Instale la [interfaz de línea de mandatos (CLI) de {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).
 * Consulte [¿Qué hace que una app sea buena?](/docs/apps?topic=creating-apps-best-practice) para ver las prácticas recomendadas para crear apps.
 * Debe tener un repositorio de código fuente Git de cualquiera de estos proveedores: GitHub, GitHub Enterprise, Git lab, BitBucket o Rational.
 * Si tiene intención de desplegar la app en [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), debe [preparar la cuenta de {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Creación de una app con un repositorio existente
{: #create-byoc}

Para crear una app y conectarla con el repositorio de origen, siga estos pasos:

1. En la [consola de {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo"), pulse **Crear una app** en el mosaico **Apps**.
2. Asigne un nombre a la app, seleccione un grupo de recursos y, si lo desea, proporcione etiquetas para clasificar la app. Para obtener más información, consulte [Cómo trabajar con etiquetas](/docs/resources?topic=resources-tag).
3. Seleccione **Traiga su propio código** y proporcione el URL al repositorio Git. La app y la imagen de Docker deben estar situadas en el mismo repositorio.
4. Pulse **Crear**. Se muestra la página **Detalles de la app**.
5. Opcional. [Añada servicios](/docs/apps?topic=creating-apps-add-resource) a la app.
6. Opcional. Puede añadir etiquetas a esta app pulsando **Añadir etiquetas**, o puede editar etiquetas pulsando el icono
**Editar** ![Icono Editar](../../icons/edit-tagging.svg) situado junto a las etiquetas mostradas.
7. Opcional. Para ver el repositorio, pulse **Ver repositorio.**

## Despliegue de la app
{: #toolchain-byoc}

El establecimiento de un enlace entre la app, la cadena de herramientas y el repositorio es un paso encaminado a organizar los activos del producto. También ayuda a agregar una vista de su origen con el flujo de trabajo de DevOps, las instancias de la app en ejecución y los servicios dependientes en todos los destinos de despliegue. Para obtener más información, consulte [Creación de cadenas de herramientas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

Puede configurar la entrega continua para la app utilizando la consola o la CLI de {{site.data.keyword.cloud_notm}}.

### Utilización de la consola
{: #console-byoc-toolchain}

#### Si ya tiene una cadena de herramientas de DevOps que desee conectar a la app, siga estos pasos:

1. En la página **Detalles de la app**, pulse **Configurar entrega continua**. Aparecerá la página **Desplegar mi app**.
2. Seleccione la cadena de herramientas que desee conectar a la app y pulse **Habilitar despliegue**. Aparecerá la página **Detalles de la app**, que indica que se ha configurado la entrega continua.

#### Si no tiene una cadena de herramientas de DevOps para esta app, siga estos pasos:

1. En la página **Detalles de la app**, pulse **Crear cadena de herramientas de DevOps**. Se abrirá la página **Crear una cadena de herramientas**.
2. [Cree la cadena de herramientas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).
3. Utilice el rastro de navegación de la ventana de navegador para volver a la página **Detalles de la app**, que indica que la entrega continua está configurada.

### Mediante la CLI
{: #cli-byoc-toolchain}

Puede utilizar el mandato `ibmcloud dev enable` para generar una plantilla de cadena de herramientas de DevOps que incorpora al repositorio como conjunto de instrucciones sobre lo que debe crear la cadena de herramientas de DevOps. 

  1. En la página **Detalles de la app**, pulse **Ver repositorio**.
  2. Ejecute el mandato siguiente:
    
    ```
    ibmcloud dev enable
    ```
   {: codeblock}

Para obtener más información sobre cómo desplegar la app, consulte
[Despliegue de apps](/docs/apps?topic=creating-apps-deploying-apps).

## Verificación de que la app se está ejecutando
{: #verify-byoc-app}

Delivery Pipeline o la línea de mandatos le señalará el URL de la app.

1. Desde la cadena de herramientas de DevOps, pulse **Delivery Pipeline** y luego seleccione **Etapa de despliegue**.
2. Pulse **Ver registros e historial**.
3. En el archivo de registro, busque el URL de la aplicación. Al final del archivo de registro, busque la palabra `urls` o `ver`. Por ejemplo, es posible que vea una línea en el archivo de registro parecida a `urls: my-app-devhost.mybluemix.net` o a `Ver el estado de la aplicación en: http://<ipaddress>:<port>/health`.
4. Vaya al URL en el navegador. Si la app se está ejecutando, se muestra un mensaje que incluye `Enhorabuena` o `{"status":"UP"}`.

Si utiliza la línea de mandatos, ejecute el mandato [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para abrir la página de una app desplegada de forma manual en el navegador predeterminado.
