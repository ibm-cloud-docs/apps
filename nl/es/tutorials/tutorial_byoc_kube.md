---

copyright:
  years: 2018, 2019
lastupdated: "2019-01-03"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Despliegue de su propio código en un clúster de Kubernetes
{: #tutorial}

Obtenga información sobre cómo crear una app en {{site.data.keyword.cloud}} utilizando el repositorio de apps existente. Puede conectar su cadena de herramientas DevOps existente o crear una, y entregar de forma continua una app a un contenedor seguro en un clúster de Kubernetes. Esta guía de aprendizaje le ayuda a configurar un conducto de DevOps de integración continua de modo que el cambio se compile y se propague automáticamente a la app desplegada en el clúster de Kubernetes.
{: shortdesc}

Si ya tiene un repositorio de código fuente con un código base para una aplicación de fondo en funcionamiento, {{site.data.keyword.cloud_notm}} le ayuda a organizar este activo en una vista agregada de todos los activos que componen el producto completo. {{site.data.keyword.cloud_notm}} le ayuda a crear y ejecutar un flujo de trabajo DevOps escalable cuando utilice la característica de cadena de herramientas de DevOps. Esta guía de aprendizaje ayuda a que el desarrollador experimentado o el ingeniero de DevOps adquiera y configure un clúster de Kubernetes de {{site.data.keyword.cloud_notm}} de destino y configure y ejecute una cadena de herramientas DevOps, todo bajo la guía de las mejores prácticas de la nube.

Un _clúster_ es un conjunto de recursos, nodos, redes y dispositivos de almacenamiento que mantienen la alta disponibilidad de las apps. Después de crear el clúster, puede desplegar las apps en los contenedores.
{: tip}

## Antes de empezar
{: #prereqs}

* Cree una app. Consulte [Creación de apps a partir de su propio repositorio de código](/docs/apps/tutorials/tutorial_byoc.html) para obtener más información. 
* En la [consola de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}){: new_window}, pulse el icono **Menú** ![Icono Menú](../../icons/icon_hamburger.svg) y seleccione **Contenedores** para [configurar un clúster de Kubernetes](/docs/containers/container_index.html).
* Para confirmar que la app se ejecuta en Docker, ejecute los mandatos siguientes:
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install`
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* A continuación, vaya al URL, como por ejemplo `http://localhost/springboothelloworld/sayhello`. Pulse Control+C para detener la ejecución de Docker.

## Adición de recursos a la app (opcional)
{: #add_resources}

Añada un recurso de servicio a la aplicación e {{site.data.keyword.cloud_notm}} crea el servicio automáticamente. El proceso de suministro puede ser diferente para distintos tipos de servicios. Por ejemplo, un servicio de base de datos crea una base de datos y un servicio de notificación push para aplicaciones móviles genera información de configuración. {{site.data.keyword.cloud_notm}} proporciona los recursos de un servicio a su aplicación mediante una instancia de servicio. Una instancia de servicio se puede compartir entre aplicaciones web.

El proceso suministra una instancia de servicio, crea una clave de recurso (credenciales) y la enlaza a la app. Para obtener más información, consulte [Adición de un servicio a la app](/docs/apps/reqnsi.html).

Después de añadir un recurso de servicio a la app, debe copiar las credenciales del servicio en el entorno de despliegue. Para obtener más información, consulte [Adición de credenciales al entorno de Kubernetes](/docs/apps/creds_kube.html).

## Preparación de la app para el despliegue
{: #connect_toolchain}

En este paso, adjuntará una cadena de herramientas DevOps a la aplicación y la configurará para desplegarla en un clúster de Kubernetes alojado en el servicio de Kubernetes de {{site.data.keyword.cloud_notm}}.

La cadena de herramientas DevOps es lo suficientemente flexible como para permitir la ejecución gestionada de etapas arbitrarias de ejecución de un script de shell. Es decir, puede hacer casi cualquier cosa con una cadena de herramientas DevOps. Esta sección se centra en el despliegue de la app en un clúster de Kubernetes, y se tiene en cuenta la "preparación para el futuro" en relación al escalado de DevOps y a la aplicación de prácticas recomendadas.

El establecimiento de un enlace entre la app, la cadena de herramientas y el repositorio es un paso encaminado a organizar los activos del producto. También ayuda a agregar una vista de su repositorio de origen con el flujo de trabajo de DevOps, las instancias de la app en ejecución y los servicios dependientes en todos los destinos de despliegue.

En la página Conectar cadena de herramientas, dispone de algunas opciones:

* Conectar la app a una cadena de herramientas existente.
* Conectar la app a una cadena de herramientas existente que no contiene el repositorio. A continuación, conectar la cadena de herramientas a su repositorio más adelante.
* Conectar la app a una cadena de herramientas nueva.

### Conectar la app a una cadena de herramientas existente
{: #connect_toolchain_repo}

Si tiene una o varias cadenas de herramientas DevOps que ya están conectadas al repositorio Git que ha especificado durante la creación de la app, dichas cadenas de herramientas se muestran en la tabla **Con repositorio**. La cadena de herramientas debe estar configurada de modo que recupere el origen del mismo repositorio que ha definido en la app. Es muy probable que desee seleccionar una de esas cadenas de herramientas para conectarla a la app.

### Conectar la app a una cadena de herramientas existente que no contiene el repositorio
{: #connect_toolchain_notrepo}

Si tiene una o varias cadenas de herramientas DevOps que están asociadas a la cuenta, pero que no están conectadas al repositorio Git que ha especificado durante la creación de la app, dichas cadenas de herramientas se muestran en la tabla **Sin su repositorio**. Puede seleccionar una de estas cadenas de herramientas y conectarla a la app, pero también debe añadir manualmente el repositorio a dicha cadena de herramientas.

Para obtener más información sobre cómo añadir el repositorio a la cadena de herramientas, consulte:

 * [Configuración de repositorio Git y seguimiento de problemas](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitbluemix)
 * [Configuración de GitHub](/docs/services/ContinuousDelivery/toolchains_integrations.html#github)
 * [Configuración de GitLab](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitlab)


### Conectar la app a una nueva cadena de herramientas
{: #create_toolchain}

Si desea controlar por completo la creación de la cadena de herramientas DevOps sin cambios en el repositorio de código, cree la cadena de herramientas desde cero. También puede crear todas las integraciones para crear la app y desplegarla en el clúster de Kubernetes.  

1. En la página Crear una cadena de herramientas, pulse la plantilla **Crear su propia cadena de herramientas**.
2. Escriba un nombre para la cadena de herramientas, seleccione una región y un grupo de recursos (predeterminado) y pulse **Crear**.

Cuando elija crear una cadena de herramientas a partir de su nueva app, se abre la página [Crear una cadena de herramientas](https://{DomainName}/devops/create) en el panel de control de DevOps en un nuevo separador del navegador. Después de crear y configurar la cadena de herramientas en dicho separador, debe volver a la página Conectar una cadena de herramientas en la app y renovar la página. {:tip}

Si no desea crear una cadena de herramientas DevOps desde cero, puede habilitar para la nube su código existente utilizando el mandato [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable). El mandato genera una plantilla de cadena de herramientas DevOps que se incorpora al repositorio. A continuación, utilice dicha plantilla como conjunto de instrucciones para lo que crea la cadena de herramientas DevOps. Para obtener más información, consulte la
[documentación de CLI](/docs/apps/create-deploy-cli.html#byoc).

## Adición de una integración de GitHub

Configure la cadena de herramientas DevOpos con una integración para su GitHub para que la cadena de herramientas establezca un webhook en el repositorio, de modo que las solicitudes de extracción y los envíos de código en dicho repositorio envíen POST a la cadena de herramientas.  

1. En la plantilla de la cadena de herramientas DevOps, pulse **Añadir una herramienta**.
2. Seleccione **GitHub** si el repositorio se encuentra en GitHub público o en Enterprise GitHub.
3. Seleccione o escriba el URL del servidor GitHub. 
4. Es posible que aparezca el mensaje `No autorizado en GitHub`. Si es así, pulse **Autorizar**. A continuación, en la página Autorizar cadenas de herramientas de IBM Cloud, pulse **Autorizar a IBM Cloud** y escriba su contraseña de GitHub. 
5. En la página Configurar la integración, seleccione **Existente** para el Tipo de repositorio para que la cadena de herramientas DevOps configure el repositorio con un webhook y no copie ni bifurque su repositorio.
6. Escriba el URL de su repositorio, por ejemplo `https://github.com/yourrepo/spring-boot-hello-world`.
7. Transcurridos unos momentos, es posible que se le solicite que autorice a GitHub a que otorgue permiso a la cadena de herramientas DevOps para que utilice la API ReST de GitHub para configurar el repositorio con los webhooks necesarios para activar la cadena de herramientas.
8.  Pulse **Crear integración**.

Puede ver el nuevo webhook de los valores del repositorio.

## Adición de un conducto de entrega

1. Pulse **Añadir una herramienta**.
2. Seleccione **Delivery Pipeline**.
3. Especifique `Integración continua` como nombre del conducto y pulse **Crear integración**.

## Configuración de las etapas del conducto

Configure las etapas del conducto para dirigir la entrada (el contenido del repositorio GitHub) al destino correcto. Puesto que en esta guía de aprendizaje se presupone que tiene un repositorio GitHub que genera una imagen de Docker de trabajo y que está dirigido a un clúster de IBM Containers Kubernetes, creará etapas del conducto con entradas, scripts de shell y salidas destinadas a alcanzar este objetivo.

1. Configure la etapa de conducto `compilar y publicar`.
  1. Seleccione el conducto de entrega que ha creado y pulse **Añadir una etapa**.
  2. Pulse el separador **Entrada** y complete los campos tal como se indica a continuación:
    * Especifique `compilar y publicar imagen de Docker` como nombre de la etapa.
    * Seleccione **Repositorio Git** como tipo de entrada.
    * Seleccione su repositorio GitHub. 
    * Seleccione la rama que utiliza para la integración continua.
  3.  Pulse el separador **Trabajados**, pulse **Añadir trabajo '+'** y complete los campos del siguiente modo:
    * Seleccione **Compilar** como tipo de trabajo.
    * Especifique `compilar y publicar` como nombre. 
    * Seleccione **Registro de contenedor** como tipo de compilador.
    * Seleccione la región en la que se encuentra el clúster de Kubernetes.
    * Seleccione **Especificar una clave de API existente**. Si no tiene ninguna clave de API, consulte [Creación de una clave de API](/docs/iam/userid_keys.html#creating-an-api-key). 
    * Especifique el espacio de nombres del registro de contenedor, que encontrará pulsando el icono **Menú** ![Icono Menú](../../icons/icon_hamburger.svg) y seleccionando **Contenedores** > **Registro** > **Espacios de nombres**.
    * Para el nombre de la imagen de Docker, especifique `continuo` porque la etapa de compilación del conducto correspondiente a la compilación continua de la rama de integración continua del repositorio. 
    * Edite el script de compilación para añadir una o varias líneas después de la primera línea `#!/bin/bash`. Por ejemplo, para un repositorio que se crea utilizando maven, puede añadir algunas líneas similares a las del ejemplo siguiente:

      ```bash
      export JAVA_HOME=/opt/IBM/java8
      # Se recomienda el distintivo MAVEN_OPTS, -B y detener las etapas junto antes de 'install':
      export MAVEN_OPTS="-  
      Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
      mvn -B clean verify
      ```
      {: codeblock}
  4. Pulse **Guardar**. 
2. Para probar la etapa del conducto `compilar y publicar`, pulse el icono **Reproducir** hasta que la compilación sea correcta. Una etapa verde indica que la compilación ha resultado correcta.  
3. Configure la etapa del conducto `desplegar en clúster` para desplegar la imagen de Docker en el clúster Kubernetes.  
  1. En la página del conducto de entrega, pulse **Añadir una etapa**.
  2. Pulse el separador **Entrada** y complete los campos tal como se indica a continuación:
    * Especifique `desplegar en clúster` como nombre. 
    * Seleccione **Compilar artefactos** como tipo de tipo de entrada.
    * Seleccione **Compilar y publicar imagen de Docker** para la etapa.
    * Seleccione **Compilar y publicar** para el trabajo. 
    * Puesto que este es el conducto de integración continua, acepte la opción predeterminada para el desencadenante de la etapa. 
  3. Pulse el separador **Trabajados**, pulse **Añadir trabajo '+'** y complete los campos del siguiente modo:
    * Especifique `desplegar en clúster de integración continua` como nombre. 
    * Seleccione **Kubernetes** para el tipo de desplegador.
    * Seleccione la región en la que se encuentra el clúster de Kubernetes.
    * Especifique la clave de API existente. 
  4. Pulse **Guardar**.
4. Para probar la etapa del conducto `desplegar en clúster`, pulse el icono **Reproducir** hasta que la compilación sea correcta. Una etapa verde indica que la compilación ha resultado correcta. Puede ver los registros correspondientes a la etapa. Casi al final de los registros, busque un enlace a la app en ejecución sobre el que puede pulsar. Añada la vía de acceso correcta correspondiente a la app para confirmar que se ejecuta.
