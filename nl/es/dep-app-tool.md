---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-18"

keywords: apps, deploy, deploying apps, toolchain, cli, cloud, devops, deployment, git, push

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Despliegue de apps
{: #deploying-apps}

Puede desplegar la aplicación en {{site.data.keyword.cloud}} utilizando la cadena de herramientas de DevOps. Con una cadena de herramientas de DevOps, puede automatizar los despliegues en muchos entornos y añadir rápidamente servicios de supervisión, registro, información y alertas que le ayuden a gestionar la app a medida que crece. Puede configurar la entrega continua y desplegar la app utilizando la consola web o la interfaz de línea de mandatos (CLI) de {{site.data.keyword.cloud_notm}}.
{: shortdesc}

Una cadena de herramientas de DevOps proporciona un entorno de desarrollo basado en equipos para la app. Cuando se crea una cadena de herramientas, el servicio de app crea un repositorio Git, donde puede ver el código fuente, clonar la app y crear y gestionar problemas. También es posible acceder a un entorno de GitLab dedicado y a un conducto de entrega continua. Están personalizados para el destino de despliegue que seleccione, que puede ser [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) o [Servidor virtual (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

## Utilización de la consola {{site.data.keyword.cloud_notm}}
{: deploy-console}

{{site.data.keyword.cloud_notm}} proporciona una consola web donde puede configurar la entrega continua y desplegar la app utilizando una cadena de herramientas de DevOps.

### Antes de empezar
{: deploy-console-before}

Antes de comenzar, utilice el [panel de control de {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") para [crear su app](/docs/apps?topic=creating-apps-getting-started) y [añadir servicios](/docs/apps?topic=creating-apps-getting-started#resources-getting-started).

### Despliegue automático de la app
{: deploy-console-auto}

Todas las cadenas de herramientas creadas en el panel de control de desarrollador de {{site.data.keyword.cloud_notm}} se configuran para un despliegue automático.
{: note}

1. En la página **Detalles de la app**, pulse **Configurar entrega continua**.
2. Seleccione un destino de despliegue. Configure el destino de despliegue de acuerdo con las instrucciones correspondientes al destino que seleccione:
  * **Desplegar en el servicio IBM Kubernetes**. Esta opción crea un clúster de hosts, denominado nodos trabajadores, para desplegar y gestionar contenedores de apps de alta disponibilidad. Puede crear un clúster o desplegar en un clúster existente. Para obtener más información, consulte [Despliegue de apps en clústeres de Kubernetes](/docs/containers?topic=containers-app).
  * **Desplegar en Cloud Foundry**. Esta opción despliega la app nativa de la nube sin necesidad de gestionar la infraestructura subyacente. Si la cuenta tiene acceso a {{site.data.keyword.cfee_full_notm}}, puede seleccionar el tipo de desplegador de **nube pública** o de **entorno de empresa**, que puede utilizar para crear y gestionar entornos aislados para alojar apps de Cloud Foundry exclusivamente para su empresa. Para obtener más información, consulte
[Despliegue de apps en Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps) y
[Despliegue de apps en {{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps).
  * **Desplegar en un servidor virtual**. Esta opción proporciona una instancia de servidor virtual, carga una imagen que incluye la app, crea una cadena de herramientas DevOps e inicia automáticamente el primer ciclo de despliegue. Para obtener más información, consulte
[Despliegue de apps en un servidor virtual](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server).

    El despliegue de VSI está disponible para algunos kits de inicio. Para utilizar esta característica, vaya al [panel de control de {{site.data.keyword.cloud_notm}}](https://{DomainName}) y pulse **Crear una app** en el mosaico **Apps**.
    {: note}

### Despliegue manual de su app
{: deploy-console-manual}

Con una cadena de herramientas correctamente configurada, un ciclo de despliegue de compilación empieza automáticamente después de cada fusión en la rama maestra en su repositorio. 

También puede desplegar manualmente su app desde su cadena de herramientas de DevOps:

1. En la página **Detalles de la app**, pulse **Ver cadena de herramientas**.
2. Pulse sobre **Conducto de entrega**, donde puede iniciar compilaciones, gestionar el despliegue y ver los registros y el historial.

La entrega continua está habilitada de forma automática para algunas apps. Puede habilitar la entrega continua para automatizar compilaciones, pruebas y despliegues a través de Delivery Pipeline y GitHub.

Para obtener más información, consulte:
* [Compilación y despliegue](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)
* [Creación de cadenas de herramientas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)

## Uso de la CLI de {{site.data.keyword.dev_cli_short}}
{: #deploy-cli}

{{site.data.keyword.cloud_notm}} proporciona una CLI sólida y plugins para ayudarle a simplificar el flujo de trabajo del desarrollador. Puede desplegar su app {{site.data.keyword.cloud_notm}} de una de estas dos maneras, en función de cómo haya configurado su app.

### Antes de empezar
{: #deploy-cli-before}

Antes de empezar, [descargue e instale la CLI de {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-getting-started).

La CLI no recibe soporte de Cygwin. Utilice la herramienta en una ventana que no sea la ventana de línea de mandatos de Cygwin.
{: important}

  1. Descargue el código de la app en un directorio nuevo para configurar su entorno de desarrollo.

  2. Cambie al directorio donde se encuentra el código.

  3.  Actualice el código de la app. Por ejemplo, si utiliza una app de ejemplo de {{site.data.keyword.cloud_notm}} y la app contiene el archivo `src/main/webapp/index.html`, puede modificarla y editar la línea `Thanks for creating ...`. Asegúrese de que la app se ejecuta localmente
antes de volver a desplegarla en {{site.data.keyword.cloud_notm}}.

    Revise el archivo `README.md`, que contiene detalles como las instrucciones de compilación.

    Si la app es una app Liberty, debe compilarla antes de volverla a desplegar.
    {: note}

  4. Inicie sesión en la CLI de {{site.data.keyword.cloud_notm}} con su IBMid. Si tiene varias cuentas, se le solicitará que seleccione qué cuenta desea utilizar. Si no especifica una región con el distintivo `-r`, también deberá seleccionar una región.
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    Si se rechazan sus credenciales, puede que esté utilizando un ID federado. Para iniciar sesión con un ID federado, utilice el distintivo
`--sso`. Para obtener más información, consulte el apartado [Inicio de sesión con un ID federado](/docs/iam/federated_id?topic=iam-federated_id#federated_id).
    {: tip}

### Despliegue automático de la app
{: #deploy-cli-auto}

Si no ha creado una cadena de herramientas de DevOps para la app y la app aún no está en un repositorio Git, puede ejecutar el mandato [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit). Siga las indicaciones para "Configurar DevOps" y despliegue en una nueva cadena de herramientas (y cree un nuevo repositorio GitLab).

Después de crear una cadena de herramientas de DevOps para su app, el despliegue de una nueva compilación será tan simple como confirmar y enviar su código al repositorio de la cadena de herramientas. 

1. Prepare los cambios que se deben confirmar.
    ```
    git add .
    ```
2. Confirme los cambios con un mensaje breve.
    ```
    git commit -m "made changes"
    ```
3. Envíe las confirmaciones en la rama maestra al repositorio remoto.
    ```
    git push origin master
    ```
4. Vea la cadena de herramientas de DevOps para su app desde la consola de {{site.data.keyword.cloud_notm}}. Puede ver detalles de la cadena de herramientas desde la página **Detalles de la app** en la consola de {{site.data.keyword.cloud_notm}} ejecutando el mandato [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) desde el directorio de la app.
5. Ver el conducto dentro de la cadena de herramientas para verificar que se ha iniciado la nueva compilación.

### Despliegue manual de su app
{: #deploy-cli-manual}

Puede desplegar manualmente la app en {{site.data.keyword.cloud_notm}} utilizando el mandato
[`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).

  ```
  ibmcloud dev deploy
  ```
  {: codeblock}

### Información relacionada
{: #deploy-cli-related}

Para obtener más información sobre cómo desplegar la app en {{site.data.keyword.cloud_notm}} utilizando la CLI, consulte:

* [Despliegue en entornos de {{site.data.keyword.cloud_notm}} con la CLI de {{site.data.keyword.dev_cli_short}}](https://www.ibm.com/cloud/blog/deploying-to-ibm-cloud-environments-with-ibm-cloud-developer-tools-cli){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")
