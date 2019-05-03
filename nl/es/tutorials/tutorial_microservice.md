---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-04"

keywords: apps, microservice, developer tools, Node.js, Java, Python, DevOps toolchain, toolchain, cli, create microservice, microservice tutorial

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Creación de un microservicio
{: #tutorial-microservice}

Puede crear una aplicación a partir del iniciador básico de microservicios (Microservice Basic Starter). Utilice estos iniciadores para compilar un sistema de fondo de microservicio de fondo para Node, Java o Python con distintas infraestructuras. Decida la forma en la que instalar las herramientas que necesita, compile y ejecute la app localmente y despliéguela en la nube.
{: shortdesc}

## Paso 1. Instalar las herramientas
{: #prereqs-microservice}

* Instale las [herramientas del desarrollador](/docs/cli?topic=cloud-cli-ibmcloud-cli).
* Docker se instala como parte de las herramientas de desarrollador. Docker debe estar en ejecución para que funcionen los mandatos de compilación. Debe crear una cuenta de Docker, ejecutar la app de Docker e iniciar la sesión.
* Si tiene intención de desplegar la app en [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), debe [preparar la cuenta de {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Paso 2. Crear una app
{: #create-microservice}

Cree una app en {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}:

1. En la página [Kits de inicio](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo") de la {{site.data.keyword.dev_console}}, seleccione un kit de inicio para su lenguaje. Por ejemplo, para una aplicación Node.js, vaya a **Express.js Microservice** y pulse **Seleccionar kit de inicio**.
2. Especifique el nombre de la app. En esta guía de aprendizaje, utilice `MicroserviceProject`.
3. Especifique un nombre de host exclusivo, por ejemplo, `abc-devhost`. Este nombre de host es la ruta de la app, `abc-devhost.mybluemix.net`.
4. Opcional. Proporcione etiquetas para clasificar la app. Para obtener más información, consulte [Cómo trabajar con etiquetas](/docs/resources?topic=resources-tag).
5. Seleccione el idioma y la infraestructura. Es posible que algunos kits de inicio solo estén disponibles en un idioma.
6. Seleccione el plan de precios. Hay una opción gratuita que puede utilizar para esta guía de aprendizaje.
7. Pulse **Crear**.

El dominio compartido predeterminado es `mybluemix.net`, pero `appdomain.cloud` es otra opción de dominio que puede utilizar. Para obtener más información sobre cómo migrar a `appdomain.cloud`, consulte
[Actualización del dominio](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).
{: tip}

## Paso 3. Añadir servicios (opcional)
{: #resources-microservice}

Puede añadir servicios para mejorar la app con la potencia cognitiva de Watson, para añadir servicios móviles o servicios de seguridad. Para esta guía de aprendizaje, añada un lugar para gestionar los datos.

1. En la página **Detalles de la app**, pulse **Añadir servicio**.
2. Seleccione el tipo de servicio que desee. Por ejemplo, seleccione **Datos** > **Siguiente** > **Cloudant** > **Siguiente**.
3. Seleccione el plan de precios. Hay una opción gratuita que puede utilizar para esta guía de aprendizaje.
4. Pulse **Crear**.

## Paso 4. Crear una cadena de herramientas de DevOps
{: #toolchain-microservice}

La habilitación de una cadena de herramientas crea un entorno de desarrollo en equipo para la app. Cuando se crea una cadena de herramientas, el servicio de app crea un repositorio Git, donde puede ver el código fuente, clonar la app y crear y gestionar problemas. También es posible acceder a un entorno de laboratorio Git dedicado y a un conducto de entrega continua. Están personalizados para el destino de despliegue que elija, que puede ser [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) o [Servidor virtual (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers).

Todas las cadenas de herramientas creadas a partir de un panel de control de desarrollador de {{site.data.keyword.cloud_notm}} se configuran para un despliegue automático.
{: note}

1. En la página **Detalles de la app**, pulse **Configurar entrega continua**.
2. Seleccione un destino de despliegue. Configure el destino de despliegue de acuerdo con las instrucciones correspondientes al método que elija:
  * **Desplegar en el [servicio IBM Kubernetes](/docs/apps/deploying?topic=creating-apps-containers-kube)**. Esta opción crea un clúster de hosts, denominado nodos trabajadores, para desplegar y gestionar contenedores de aplicaciones de alta disponibilidad. Puede crear un clúster o desplegar en un clúster existente.
  * **Desplegar en Cloud Foundry**. Esta opción despliega la app nativa de la nube sin necesidad de gestionar la infraestructura subyacente. Si la cuenta tiene acceso a {{site.data.keyword.cfee_full_notm}}, puede seleccionar el tipo de desplegador de **[nube pública](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)** o de **[entorno de empresa](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**, que puede utilizar para crear y gestionar entornos aislados para alojar aplicaciones de Cloud Foundry exclusivamente para su empresa.
  * **Desplegar en un [servidor virtual](/docs/apps?topic=creating-apps-vsi-deploy)**. Esta opción proporciona una instancia de servidor virtual, carga una imagen que incluye la app, crea una cadena de herramientas DevOps e inicia automáticamente el primer ciclo de despliegue.

## Paso 5. Crear y ejecutar la app localmente
{: #build-run-microservice}

El despliegue de la app en la nube en el último paso ha creado una cadena de herramientas. Una cadena de herramientas crea un repositorio Git para la app donde puede encontrar el código allí. Siga estos pasos para acceder a su repositorio. Puede compilar la app localmente para probarla antes de enviarla por push a la nube.

1. En la página **Detalles de la app**, pulse **Descargar código** o **Clonar el repositorio** para trabajar con el código de manera local.
2. Importe la app a su entorno de desarrollo integrado.
3. Modifique el código.
4. Configure [Autenticación de Git](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) añadiendo una señal de acceso personal.
5. Inicie sesión en la interfaz de línea de mandatos de {{site.data.keyword.cloud_notm}}. Si su organización utiliza inicios de sesión federados, utilice la opción `-sso`.

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Establezca los destinos de org y de espacio.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7.  Obtener las credenciales.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Asegúrese de que Docker se esté ejecutando y cree la app en un contenedor de desarrollo local desde el directorio.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Ejecute la app en un contenedor de desarrollo local.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10.  Abra el navegador en `http://localhost:3000`. Es posible que el número de puerto sea distinto en función del tiempo de ejecución elegido.

## Paso 6. Desplegar la app
{: #deploy-microservice}

### Desplegar utilizando una cadena de herramientas
{: #deploy-microservice-toolchain}

Puede desplegar la app en {{site.data.keyword.cloud_notm}} de varias formas, pero una cadena de herramientas de DevOps es la mejor forma de desplegar apps de producción. Con una cadena de herramientas de DevOps, puede automatizar fácilmente despliegues en muchos entornos y añadir rápidamente servicios de supervisión, de registro y de alertas para ayudar a gestionar su app a medida que crece.

Con una cadena de herramientas correctamente configurada, un ciclo de despliegue de compilación empieza automáticamente después de cada fusión en la rama maestra en su repositorio. Todas las cadenas de herramientas creadas a partir de un panel de control de desarrollador de {{site.data.keyword.cloud_notm}} se configuran para un despliegue automático.

También puede desplegar manualmente su app desde su cadena de herramientas de DevOps:

1. En la página **Detalles de la app**, pulse **Ver cadena de herramientas**.

2. Pulse **Conducto de entrega** donde puede iniciar compilaciones, gestionar el despliegue y ver registros e historiales.

### Desplegar utilizando el {{site.data.keyword.dev_cli_short}}
{: #deploy-microservice-cli}

Para desplegar la app en Cloud Foundry, especifique el mandato siguiente:

```
ibmcloud dev deploy
```
{: pre}

Para desplegar la app en un clúster de Kubernetes, especifique el mandato siguiente:

```
ibmcloud dev deploy --target <container>
```
{: pre}

## Paso 7. Verificar que la app se está ejecutando
{: #verify-microservice}

Después de desplegar la app, el conducto de entrega o la línea de mandatos le apunta al URL para la app.

1. Desde la cadena de herramientas de DevOps, pulse **Delivery Pipeline** y luego seleccione **Etapa de despliegue**.
2. Pulse **Ver registros e historial**.
3. En el archivo de registro, busque el URL de la aplicación:

    Al final del archivo de registro, busque la palabra `urls` o `ver`. Por ejemplo, es posible que vea una línea en el archivo de registro parecida a `urls: my-app-devhost.mybluemix.net` o a `Ver el estado de la aplicación en: http://<ipaddress>:<port>/health`.

4. Vaya al URL en el navegador. Si la app se está ejecutando, se muestra un mensaje que incluye `Enhorabuena` o `{"status":"UP"}`.

Si utiliza la línea de mandatos, ejecute el mandato [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para ver el URL de la app. Luego vaya al URL en el navegador.
