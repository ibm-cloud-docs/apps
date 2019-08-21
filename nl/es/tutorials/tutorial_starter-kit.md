---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-17"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# Creación de una app con un kit de inicio
{: #tutorial-starterkit}

Utilice un kit de inicio para empezar rápidamente su aplicación y prepárela para el futuro desarrollo. Seleccione un kit de inicio y un lenguaje de programación, cree una app y configure una cadena de herramientas de DevOps para desplegar su app automáticamente.
{: shortdesc}

Puede crear una app desde una selección de kits de inicio, incluido uno básico si desea personalizar las opciones de compilación usted mismo. En cualquiera de los casos, se crea automáticamente una cadena de herramientas DevOps para desplegar la app. También puede descargar el código para una inspección inmediata.

{{site.data.keyword.cloud_notm}} tiene portales de desarrollador en distintas áreas de interés (por ejemplo, Watson) o para un canal digital (como por ejemplo, apps móviles o web). Puede acceder a estos portales desde el icono **Menú**
![Icono Menú](../../icons/icon_hamburger.svg).

Cada portal de desarrollador proporciona kits de inicio relevantes para el área de atención del portal. Los portales ofrecen flujos de trabajo coherentes e intuitivos para crear una app lista para producción en cuestión de minutos.

Los kits de inicio están disponibles para muchas categoría, entre otras:
* [Watson](https://{DomainName}/developer/watson/dashboard){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
* [Apple](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
* [Móvil](https://{DomainName}/developer/mobile/dashboard){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")
* [App Web](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")

Consulte [¿Qué los kits de inicio?](/docs/apps?topic=creating-apps-starter-kits) para obtener más información.

## Paso 1. Instalar las herramientas
{: #prereqs-starterkit}

* Instale las [herramientas del desarrollador](/docs/cli?topic=cloud-cli-getting-started).
* Docker se instala como parte de las herramientas de desarrollador. Docker debe estar en ejecución para que funcionen los mandatos de compilación. Debe crear una cuenta de Docker, ejecutar la app de Docker e iniciar la sesión.
* Si tiene intención de desplegar la app en {{site.data.keyword.cfee_full}}, debe [preparar la cuenta de {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Paso 2. Crear una app
{: #create-starterkit}

Los kits de inicio están disponibles en muchos lenguajes e infraestructuras en la {{site.data.keyword.dev_console}} de {{site.data.keyword.cloud_notm}}. Puede utilizar filtros de categorías, como lenguaje y tipo, para reducir la selección.

1. En la página [kits de inicio](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo") de la consola de {{site.data.keyword.dev_console}}, seleccione un kit de inicio y pulse **Crear app**. 

    Para ver lo que se incluye en el kit de inicio, seleccione el mosaico y lea los detalles. Si desea utilizar un kit de inicio básico y personalizar la app, seleccione el mosaico **Crear app**.
    {: tip}

2. Asigne un nombre a la app y seleccione un grupo de recursos.

3. Opcional. Proporcione etiquetas para clasificar la app. Para obtener más información, consulte [Cómo trabajar con etiquetas](/docs/resources?topic=resources-tag).

4. Seleccione el lenguaje y la infraestructura. Es posible que algunos kits de inicio solo estén disponibles en un lenguaje.

5. Pulse **Crear**.

¡Buen comienzo! Acaba de crear una app.

Para inspeccionar el código antes de añadir servicios o de configurar la entrega continua, pulse **Descargar código** en la página Detalles de la app. Consulte el archivo `README.md` del archivo comprimido descargado para averiguar si es necesario realizar algo más para ejecutar su app.
{: tip}

## Paso 3. Añadir servicios (opcional)
{: #resources-starterkit}

Si un kit de inicio requiere servicios específicos, las instancias de servicio suministradas automáticamente se crean automáticamente y se conectan a la app.

También puede añadir servicios para mejorar la app con la potencia cognitiva de Watson, para añadir servicios móviles o servicios de seguridad. Para esta guía de aprendizaje, añada un lugar para gestionar los datos.

1. En la página Detalles de la app, pulse **Crear servicio** o **Conectar servicios existentes**, en función de si ya tiene servicios que desea conectar a esta app.
2. Seleccione el tipo de servicio que desee y siga las indicaciones para añadir un servicio existente a la app o para crear una instancia de servicio.

Después de añadir todos los servicios que desee, se muestran en la página Detalles de la app.

## Paso 4. Seleccionar un destino del despliegue y configurar la entrega continua
{: #target-starterkit}

Cuando selecciona un destino de despliegue, se crea automáticamente una cadena de herramientas DevOps para la app. La cadena de herramientas incluye un conducto de entrega que indica el estado de despliegue de la app. La nueva app que se genera se envía a un repositorio GitLab que forma parte de la cadena de herramientas.

La habilitación de una cadena de herramientas DevOps crea un entorno de desarrollo en equipo para la app. Cuando se crea una cadena de herramientas, el servicio de app crea un repositorio Git, donde puede ver el código fuente, clonar la app y crear y gestionar problemas. También es posible acceder a un entorno de GitLab dedicado y a un conducto de entrega continua. Están personalizados para el destino de despliegue que seleccione, que puede ser [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) o [Servidor virtual (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Todas las cadenas de herramientas creadas a partir de un panel de control de desarrollador de {{site.data.keyword.cloud_notm}} se configuran para un despliegue automático.
{: note}

Para seleccionar el destino del despliegue y configurar la entrega continua, siga estos pasos:

1. En la página Detalles de la app, pulse **Configurar entrega continua**.
2. Seleccione un destino de despliegue. Configure el destino de despliegue de acuerdo con las instrucciones correspondientes al destino que seleccione:
  * **Desplegar en el [servicio IBM Kubernetes](/docs/containers?topic=containers-app)**. Esta opción crea un clúster de hosts, denominado nodos trabajadores, para desplegar y gestionar contenedores de apps de alta disponibilidad. Puede crear un clúster o desplegar en un clúster existente.
  * **Desplegar en Cloud Foundry**. Esta opción despliega la app nativa de la nube sin necesidad de gestionar la infraestructura subyacente. Si la cuenta tiene acceso a {{site.data.keyword.cfee_full_notm}}, puede seleccionar el tipo de desplegador de **[nube pública](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** o de **[entorno de empresa](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**, que puede utilizar para crear y gestionar entornos aislados para alojar apps de Cloud Foundry exclusivamente para su empresa.
  * **Desplegar en un servidor virtual**. Esta opción proporciona una instancia de servidor virtual, carga una imagen que incluye la app, crea una cadena de herramientas DevOps e inicia automáticamente el primer ciclo de despliegue. Para obtener más información, consulte
[Despliegue de apps en un servidor virtual](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server).

    El despliegue de VSI está disponible para algunos kits de inicio. Para utilizar esta característica, vaya al [panel de control de {{site.data.keyword.cloud_notm}}](https://{DomainName}) y pulse **Crear una app** en el mosaico **Apps**.
    {: note}

Después de seleccionar y configurar el destino del despliegue, la página Detalles de la app indica que se ha configurado la entrega continua. Para ver el repositorio que contiene el código fuente de la app, pulse **Ver repositorio**.

## Paso 5. Desplegar la app
{: #deploy-starterkit}

Las cadenas de herramientas de DevOps creadas en el panel de control de desarrollador de {{site.data.keyword.cloud_notm}} se configuran para un despliegue automático.
{: note}

Después de seleccionar el destino de despliegue, abra el componente del conducto de la nueva cadena de herramientas para iniciar el proceso de compilación y despliegue inicial de forma que pueda visualizar en unos minutos su nueva app.

1. En la página Detalles de la app, pulse **Ver cadena de herramientas**.
2. Pulse sobre **Conducto de entrega**, donde puede iniciar compilaciones, gestionar el despliegue y ver los registros y el historial.

Con una cadena de herramientas correctamente configurada, un ciclo de despliegue de compilación empieza automáticamente después de cada fusión en la rama maestra en su repositorio. Para obtener más información, consulte [Creación y despliegue](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

Puede desplegar la app desde la línea de mandatos con el mandato [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy). Para obtener más información, consulte [Despliegue de apps con la CLI](/docs/apps?topic=creating-apps-deploying-apps#deploy-cli).

## Paso 6. Verificar que la app se está ejecutando
{: #verify-starterkit}

Después de desplegar la app, el conducto de entrega o la línea de mandatos le apunta al URL para la app.

1. Desde la cadena de herramientas de DevOps, pulse **Delivery Pipeline** y luego seleccione **Etapa de despliegue**.
2. Pulse **Ver registros e historial**.
3. En el archivo de registro, busque el URL de la app:

    Al final del archivo de registro, busque la palabra `urls` o `ver`. Por ejemplo, es posible que vea una línea en el archivo de registro parecida a `urls: my-app-devhost.mybluemix.net` o a `Ver el estado de la aplicación en: http://<ipaddress>:<port>/health`.

4. Vaya al URL en el navegador. Si la app se está ejecutando, se muestra un mensaje que incluye `Enhorabuena` o `{"status":"UP"}`.

Si utiliza la línea de mandatos, ejecute el mandato [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para ver el URL de la app. Luego vaya al URL en el navegador.
