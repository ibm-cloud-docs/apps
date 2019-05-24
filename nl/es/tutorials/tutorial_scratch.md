---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-10"

keywords: scratch, developer tools, custom app, app tutorial, verify app running, run app local

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Creación de una app desde cero
{: #tutorial-scratch}

Puede crear una aplicación personalizada desde cero mediante servicios y un tiempo de ejecución. 
{: shortdesc}

## Antes de empezar
{: #prereqs-scratch}

* Instale la [{{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli), que incluye Docker. 
* Cree una cuenta de Docker, ejecute la app de Docker e inicie una sesión. Docker debe estar en ejecución para que funcionen los mandatos de compilación.
* Si tiene intención de desplegar la app en {{site.data.keyword.cfee_full}}, debe [preparar la cuenta de {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Creación de la app
{: #create-scratch}

1. En el [panel de control de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}), pulse **Crear una app** en el widget Apps.

  También puede crear una app personalizada en la página [Kits de inicio ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}/developer/appservice/starter-kits/) en {{site.data.keyword.dev_console}}.
  {: tip}

2. Especifique un nombre para su app. En esta guía de aprendizaje, escriba `CustomProject`.
3. Si lo desea, puede proporcionar etiquetas para clasificar la app. Para obtener más información, consulte [Cómo trabajar con etiquetas](/docs/resources?topic=resources-tag).
4. Seleccione el idioma y la infraestructura. Es posible que algunos kits de inicio solo estén disponibles en un idioma.
5. Seleccione el plan de precios. Puede utilizar la opción gratuita para esta guía de aprendizaje.
6. Pulse **Crear**.

## Adición de servicios (opcional)
{: #resources-scratch}

Puede añadir servicios para mejorar la app con la potencia cognitiva de Watson, para añadir servicios móviles o servicios de seguridad. Para esta guía de aprendizaje, puede añadir un lugar para gestionar los datos.

1. En la página **Detalles de la app**, pulse **Añadir servicio**.
2. Seleccione el tipo de servicio que desee. Por ejemplo, seleccione **Datos** > **Siguiente** > **Cloudant** > **Siguiente**.
3. Seleccione el plan de precios. Puede utilizar la opción gratuita para esta guía de aprendizaje.
4. Pulse **Crear**.

## Creación y ejecución de la app localmente
{: #build-run-scratch}

También puede compilar la app localmente para probarla antes de desplegarla en la nube.

1. En la página **Detalles de la app**, pulse **Descargar código** o **Clonar el repositorio** para trabajar con el código de manera local.
2. Importe la app a su entorno de desarrollo integrado.
3. Modifique el código.
4. Configure [Autenticación de Git](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) añadiendo una señal de acceso personal.
5. Inicie sesión en la interfaz de línea de mandatos (CLI) de {{site.data.keyword.cloud_notm}}. Si su organización utiliza inicios de sesión federados, utilice la opción `-sso`; por ejemplo:

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Ejecute el mandato siguiente para definir los destinos de la organización y del espacio.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. Ejecute el siguiente mandato para recuperar las credenciales.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Asegúrese de que Docker se esté ejecutando y ejecute el siguiente mandato para crear la app en un contenedor de desarrollo local desde el directorio.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Ejecute el siguiente mandato para ejecutar la app en un contenedor de desarrollo local.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. Vaya a `http://localhost:3000` en el navegador. Es posible que el número de puerto sea distinto en función del tiempo de ejecución elegido.

## Despliegue de la app
{: #deploy-scratch}

Cuando selecciona un destino de despliegue, se crea automáticamente una cadena de herramientas DevOps para la app. La cadena de herramientas incluye un conducto de entrega que indica el estado de despliegue de la app. La nueva app que se genera se envía a un repositorio GitLab que forma parte de la cadena de herramientas.

La habilitación de una cadena de herramientas DevOps crea un entorno de desarrollo en equipo para la app. Cuando se crea una cadena de herramientas, el servicio de app crea un repositorio Git, donde puede ver el código fuente, clonar la app y crear y gestionar problemas. También es posible acceder a un entorno de GitLab dedicado y a un conducto de entrega continua. Están personalizados para el destino de despliegue que seleccione, que puede ser [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) o [Servidor virtual (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Todas las cadenas de herramientas creadas a partir de un panel de control de desarrollador de {{site.data.keyword.cloud_notm}} se configuran para un despliegue automático.
{: note}

Para seleccionar el destino del despliegue y configurar la entrega continua, siga estos pasos:

1. En la página Detalles de la app, pulse **Configurar entrega continua**.
2. Seleccione un destino de despliegue. Configure el destino de despliegue de acuerdo con las instrucciones correspondientes al destino que seleccione:
  * **Desplegar en el [servicio IBM Kubernetes](/docs/containers?topic=containers-app)**. Esta opción crea un clúster de hosts, denominado nodos trabajadores, para desplegar y gestionar contenedores de aplicaciones de alta disponibilidad. Puede crear un clúster o desplegar en un clúster existente.
  * **Desplegar en Cloud Foundry**. Esta opción despliega la app nativa de la nube sin necesidad de gestionar la infraestructura subyacente. Si la cuenta tiene acceso a {{site.data.keyword.cfee_full_notm}}, puede seleccionar el tipo de desplegador de **[nube pública](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** o de **[entorno de empresa](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**, que puede utilizar para crear y gestionar entornos aislados para alojar aplicaciones de Cloud Foundry exclusivamente para su empresa.
  * **Desplegar en un servidor virtual**. Esta opción proporciona una instancia de servidor virtual, carga una imagen que incluye la app, crea una cadena de herramientas DevOps e inicia automáticamente el primer ciclo de despliegue.

Después de seleccionar y configurar el destino del despliegue, la página Detalles de la app indica que se ha configurado la entrega continua. Para ver el repositorio que contiene el código fuente de la app, pulse **Ver repositorio**.

Para desplegar la app con la línea de mandatos, utilice `ibmcloud dev deploy`. Consulte [Creación y despliegue de apps utilizando la CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli) para obtener más información.

Para obtener más información sobre cómo desplegar la app, consulte
[Despliegue de apps](/docs/apps?topic=creating-apps-deploying-apps).

## Verificación de que la app se está ejecutando
{: #verify-scratch}

Después de desplegar la app, el conducto de entrega o la línea de mandatos le apunta al URL para la app.

1. Desde la cadena de herramientas de DevOps, pulse **Delivery Pipeline** y luego seleccione **Etapa de despliegue**.
2. Pulse **Ver registros e historial**.
3. En el archivo de registro, busque el URL de la aplicación:

   Al final del archivo de registro, busque la palabra `urls` o `ver`. Por ejemplo, es posible que vea una línea en el archivo de registro parecida a `urls: my-app-devhost.mybluemix.net` o a `Ver el estado de la aplicación en: http://<ipaddress>:<port>/health`.

4. Vaya al URL en el navegador. Si la app se está ejecutando, se muestra un mensaje que incluye `Enhorabuena` o `{"status":"UP"}`.

Si utiliza la línea de mandatos, ejecute el mandato [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para ver el URL de la app. Luego vaya al URL en el navegador.

