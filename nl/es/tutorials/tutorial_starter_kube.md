---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, starter kit, Kubernetes, cluster

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Despliegue de una app de kit de inicio en un clúster de Kubernetes
{: #tutorial-starterkit-kube}

Aprenda a crear una aplicación en {{site.data.keyword.cloud}} utilizando un kit de inicio en blanco y una cadena de herramientas Kubernetes y a suministrar la app de forma continuada a un contenedor seguro en un clúster de Kubernetes. El conducto de DevOps de integración continua se puede configurar de modo que los cambios en el código se compilen automáticamente y se propaguen a la app que está en el clúster de Kube. Si ya tiene un conducto, puede conectarlo a la app.
{: shortdesc}

{{site.data.keyword.cloud_notm}} ofrece kits de inicio que le ayudan a crear la base de una app que se ejecuta en Kubernetes. Cuando se utiliza un kit de inicio, es fácil seguir un modelo de programación nativo de la nube que utiliza las prácticas recomendadas de {{site.data.keyword.cloud_notm}} para el desarrollo de apps. Los kits de inicio generan apps que siguen el modelo de programación nativo de la nube e incluyen casos de uso, comprobación de estado y métricas en cada uno de los lenguajes de programación. También puede suministrar servicios de nube que se inicialicen en la aplicación generada.

En esta guía de aprendizaje se utiliza el destino de despliegue de Kubernetes. En esta guía de aprendizaje, vamos a crear una aplicación a partir de un kit de inicio básico utilizando Java + Spring, a añadir a la misma una instancia de servicio Cloudant y a desplegarla en {{site.data.keyword.cloud_notm}} utilizando el servicio IBM Kubernetes.

En primer lugar, consulte el siguiente diagrama de flujo del kit de inicio y sus correspondientes pasos de visión general.

![Diagrama de flujo del kit de inicio](../images/starterkit-flow.png) 

## Antes de empezar
{: #prereqs-starterkit-kube}

* Cree una app **Java + Spring** utilizando un [kit de inicio](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit).
* Instale la [CLI de {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).
* Configure [Docker](https://www.docker.com/get-started){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo").

## Adición de servicios a la app
{: #resources-starterkit-kube}

Añada un servicio de {{site.data.keyword.cloud_notm}} a la aplicación. En los pasos siguientes se suministra una instancia de Cloudant, se crea una clave de recurso (credenciales) y se enlaza con la app.

1. En la página **Detalles de la app**, pulse **Añadir servicio**.
2. Seleccione **Datos** y pulse **Siguiente**.
3. Seleccione **Cloudant** y pulse **Siguiente**.
4. En la página **Añadir Cloudant**, seleccione la región (EE.UU. sur), el grupo de recursos (predeterminado) y el plan de precios (Lite - una instancia gratuita).
5. Pulse **Crear**. Se visualiza la página **Detalles de la app** y la instancia de Cloudant se suministra y se enlaza a la app. Observe que la clave de recurso de Cloudant (credenciales) se añade al campo **Credenciales**.
6. Opcional. Si desea echar un vistazo al código de la app después de añadir servicios, pulse **Descargar código**. El código se descarga como un archivo `.zip` que contiene toda la estructura del código de la app. Puede extraer fácilmente el archivo y ejecutar el código localmente utilizando {{site.data.keyword.dev_cli_notm}}, o añadirlo su repositorio de gestión de código.

## Despliegue la app utilizando la cadena de herramientas de DevOps
{: #deploy-starterkit-kube}

Adjunte una cadena de herramientas DevOps a la aplicación y configúrela para desplegarla en un clúster de Kubernetes alojado en el servicio de Kubernetes de {{site.data.keyword.cloud_notm}}.

1. En la página **Detalles de la app**, pulse **Configurar entrega continua**.
2. En la página **Seleccionar un destino de despliegue**, seleccione **Desplegar en el servicio IBM Kubernetes**.
3. Seleccione una región y un clúster. Si no tiene un clúster de Kubernetes, puede **Crear clúster**.
  * En la página **Crear clúster nuevo**, seleccione la ubicación, el tipo de clúster (gratuito), escriba un nombre de clúster y, a continuación, pulse **Crear clúster**.
  * Si es necesario, siga las instrucciones de la pantalla para obtener acceso a su clúster.
  * Espere hasta que el clúster indique **READY** para crear la cadena de herramientas. Con la región **EE.UU.sur**, puede suministrar un clúster gratuito.
  * Vuelva a la página **Seleccionar un destino de despliegue**.
4. Pulse **Siguiente**. Se muestra la página **Configurar cadena de herramientas**.
5. En la página **Configurar cadena de herramientas**, escriba un nombre de cadena de herramientas, seleccione una región, seleccione un grupo de recursos y luego pulse **Crear**. Se visualiza la página **Detalles de la app** junto con la información de despliegue sobre la cadena de herramientas.

## Visualización del repositorio
{: #view-repo-starterkit-kube}

1. En la página **Detalles de la app**, pulse **Ver repositorio**. Se muestra el repositorio Git que ha generado el kit de inicio.
2. Opcional. Configure SSH en el escritorio siguiendo las instrucciones de la pantalla.
3. Opcional. Cree una señal de acceso personal en la cuenta siguiendo las instrucciones de la pantalla.

## Visualización de las herramientas, los registros y el historial de la cadena de herramientas
{: #view-logs-starterkit-kube}

1. Cuando finaliza la etapa de despliegue, se visualiza la página **Detalles de la app** junto con la información de despliegue sobre la cadena de herramientas.
2. Acceda a la cadena de herramientas pulsando **Ver cadena de herramientas**. Se visualiza el separador **Visión general** de la página de la cadena de herramientas, que muestra las herramientas incluidas en la cadena de herramientas. Este ejemplo incluye las herramientas siguientes que se han preseleccionado en el kit de inicio cuando se ha creado la cadena de herramientas:
  * Un programa de seguimiento de problemas para realizar un seguimiento de las actualizaciones y los cambios del proyecto.
  * Un repositorio Git que contiene el código fuente de la aplicación.
  * Una instancia de Eclipse Orion, que es un IDE basado en web para editar la aplicación.
  * Un conducto de entrega que consta de una etapa de compilación y despliegue personalizable.
	 * La etapa de compilación (BUILD) conteneriza la app. En concreto, la etapa de compilación:
	   * Clona el repositorio GitLab.
	   * Crea la app.
	   * Crea la imagen de Docker.
	   * Publica la imagen en el registro de contenedor privado.
	 * La etapa de despliegue (DEPLOY) recupera la imagen del contenedor del registro del contenedor y la despliega en el clúster de Kubernetes.
3. Pulse **Delivery Pipeline**. Se muestran las etapas del conducto de entrega.
4. En el mosaico **Etapa de despliegue**, pulse **Ver registros e historial**.

## Verificación de que la app se está ejecutando
{: #verify-starterkit-kube}

Después de desplegar la app, el conducto de entrega o la línea de mandatos le apunta al URL para la app.

1. Desde la cadena de herramientas de DevOps, pulse **Delivery Pipeline** y luego seleccione **Etapa de despliegue**.
2. Pulse **Ver registros e historial**.
3. En el archivo de registro, busque el URL de la aplicación:

    Al final del archivo de registro, busque `Ver el estado de la aplicación en: http://<ipaddress>:<port>/health`.

4. Vaya al URL en el navegador. Si la app se está ejecutando, se muestra un mensaje que incluye `Enhorabuena` o `{"status":"UP"}`.

Si utiliza la línea de mandatos, ejecute el mandato [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para ver el URL de la app. Luego vaya al URL en el navegador.

## Pasos siguientes
{: #next-steps-startkit-kube notoc}

* Si recibe errores durante el despliegue, consulte el tema sobre resolución de problemas para ver problemas conocidos como [superación de la cuota de almacenamiento](/docs/apps?topic=creating-apps-managingapps#exceed_quota) o bien consulte cómo [acceder a los registros de Kubernetes](/docs/apps?topic=creating-apps-managingapps#access_kube_logs) para buscar errores.

* Acceda a la configuración del servicio en el código:
	- Puede utilizar la anotación _@Value_ o bien puede utilizar el método _getProperty()_ de la clase de entorno Spring. Para obtener más información, consulte [Acceso a credenciales](/docs/java-spring?topic=java-spring-configuration#accessing-credentials).

* Añada nuevas credenciales al entorno de Kubernetes:
	- Cuando se añade otro servicio a la aplicación después de que se cree la cadena de herramientas de DevOps, dichas credenciales de servicio no se actualizan automáticamente en la aplicación desplegada y en el repositorio GitLab. Debe [añadir manualmente las credenciales](/docs/apps?topic=creating-apps-add-credentials-kube) al entorno de despliegue.
