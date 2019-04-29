---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-02"

keywords: apps, deploy, deploying apps, toolchains, cli, cloud

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

Puede desplegar sus aplicaciones con una cadena de herramientas de DevOps o con una interfaz de línea de mandatos (CLI). Una cadena de herramientas de DevOps es un conjunto de integraciones de herramientas. La CLI constituye una forma simple de desplegar sus apps e instancias de servicio.
{: shortdesc}

## Despliegue de apps mediante cadenas de herramientas de DevOps
{: #toolchain-deploy-apps}

Las cadenas de herramientas abiertas están disponibles en los entornos Público y Dedicado en {{site.data.keyword.Bluemix}}. Con una cadena de herramientas correctamente configurada, el despliegue de una app resulta sencillo. Un ciclo de despliegue de compilación se inicia automáticamente después de cada fusión en la rama maestra en su repositorio.

Puede crear una cadena de herramientas de estas formas:
* Cree una cadena de herramientas a partir de una app. Para obtener más información, consulte
[Despliegue de la app](/docs/apps?topic=creating-apps-tutorial-scratch#deploy-scratch).
* Utilice una plantilla para crear una cadena de herramientas nueva. Para obtener más información, consulte [Creación de cadenas de herramientas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## Despliegue de apps mediante la CLI
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}} proporciona una CLI sólida así como plugins y extensiones de herramientas de desarrollador que se integran con la CLI.

Antes de empezar, [descargue e instale la CLI de {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).

La CLI no recibe soporte de Cygwin. Utilice la herramienta en una ventana que no sea la ventana de línea de mandatos de Cygwin.
{: important}

  1. Descargue el código de la app en un directorio nuevo para configurar su entorno de desarrollo.

  2. Cambie al directorio donde se encuentra el código.

  3.  Actualice el código de la app. Por ejemplo, si utiliza una aplicación de ejemplo de {{site.data.keyword.cloud_notm}} y la app contiene el archivo `src/main/webapp/index.html`, puede modificarla y editar la línea `Thanks for creating ...`. Asegúrese de que la app se ejecuta localmente
antes de volver a desplegarla en {{site.data.keyword.cloud_notm}}.

    Preste atención al archivo `manifest.yml`. Cuando despliegue su app en
{{site.data.keyword.cloud_notm}}, este archivo se utiliza para determinar el URL de la aplicación, la
asignación de memoria, el número de instancias y otros parámetros cruciales.

    Revise también el archivo `README.md`, que contiene detalles como las instrucciones de compilación.

    Si la aplicación es una app Liberty, debe compilarla antes de volverla a desplegar.
    {: note}

  4. Inicie sesión en la CLI de {{site.data.keyword.cloud_notm}} con su IBMid. Si tiene varias cuentas, se le solicitará que seleccione qué cuenta desea utilizar. Si no especifica una región con el distintivo `-r`, también deberá seleccionar una región.
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    Si se rechazan sus credenciales, puede que esté utilizando un ID federado. Para iniciar sesión con un ID federado, utilice el distintivo
`--sso`. Para obtener más información, consulte el apartado [Inicio de sesión con un ID federado](/docs/iam/federated_id?topic=iam-federated_id#federated_id).
    {: tip}

  5. Desde el nuevo directorio, despliegue la app en {{site.data.keyword.cloud_notm}} con el mandato [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).
    ```
    ibmcloud dev deploy <APP_NAME>
    ```
    {: codeblock}

  6. Acceda a la app ejecutando el mandato [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para ver el URL de la app. Luego vaya al URL en el navegador.
