---

copyright:
  years: 2018
lastupdated: "2018-11-29"

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

* Siga los pasos para [crear apps a partir de su propio repositorio de código](/docs/apps/tutorials/tutorial_byoc.html) para crear una app.
* En el [panel de control de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://{DomainName}){: new_window}, pulse el icono **Menú** ![Icono Menú](../../icons/icon_hamburger.svg) y seleccione **Contenedores** para [configurar un clúster de Kubernetes](/docs/containers/container_index.html).
* Para confirmar que la app se ejecuta en Docker, ejecute los mandatos siguientes:
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install`
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* A continuación, visite el URL, como por ejemplo `http://localhost/springboothelloworld/sayhello`.   
Pulse `Control+C` para detener la ejecución de Docker.

## Opcional. Adición de recursos a la app
{: #add_resources}

Añada un recurso de servicio a la aplicación e {{site.data.keyword.cloud_notm}} crea el servicio automáticamente. El proceso de suministro puede ser diferente para distintos tipos de servicios. Por ejemplo, un servicio de base de datos crea una base de datos y un servicio de notificación push para aplicaciones móviles genera información de configuración. {{site.data.keyword.cloud_notm}} proporciona los recursos de un servicio a su aplicación mediante una instancia de servicio. Una instancia de servicio se puede compartir entre aplicaciones web.

El proceso suministra una instancia de servicio, crea una clave de recurso (credenciales) y la enlaza a la app. Para obtener más información, consulte [Adición de un servicio a la app](/docs/apps/reqnsi.html).

### Copia de las credenciales de servicio en el entorno

Después de añadir un recurso de servicio a la app, tenga en cuenta que las credenciales para dicho servicio se muestran en el recuadro **Credenciales**. Debe copiar las credenciales en el entorno de despliegue.

Para obtener más información sobre cómo copiar credenciales en el entorno, consulte [Adición de credenciales al entorno de Kubernetes](/docs/apps/creds_kube.html).


## Preparación de la app para el despliegue utilizando una cadena de herramientas DevOps
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

Si tiene una o varias cadenas de herramientas DevOps que están asociadas a la cuenta, pero que no están conectadas al repositorio Git que ha especificado durante la creación de la app, dichas cadenas de herramientas se muestran en la tabla con la etiqueta **sin su repositorio**. Puede seleccionar una de estas cadenas de herramientas y conectarla a la app, pero también debe añadir manualmente el repositorio a dicha cadena de herramientas.

Para obtener más información sobre cómo añadir el repositorio a la cadena de herramientas, consulte:

 * [Configuración de repositorio Git y seguimiento de problemas](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitbluemix)
 * [Configuración de GitHub](/docs/services/ContinuousDelivery/toolchains_integrations.html#github)
 * [Configuración de GitLab](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitlab)


### Conectar la app a una nueva cadena de herramientas
{: #create_toolchain}

Tiene estas opciones para conectar la app a una nueva cadena de herramientas:
* Si no desea crear una cadena de herramientas DevOps desde cero, puede habilitar para la nube su código existente utilizando el mandato [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable). El mandato genera una plantilla de cadena de herramientas DevOps que se incorpora al repositorio. A continuación, utilice dicha plantilla como conjunto de instrucciones para lo que crea la cadena de herramientas DevOps. Para obtener más información, consulte la
[documentación de CLI](/docs/apps/create-deploy-cli.html#byoc).
* Cree una cadena de herramientas DevOps desde cero en la consola. Si desea controlar por completo la creación de la cadena de herramientas DevOps sin cambios en el repositorio de código, cree la cadena de herramientas desde cero. Para obtener más información, consulte [Creación de una cadena de herramientas DevOps desde cero](#create_toolchain_scratch).

#### Creación de una cadena de herramientas DevOps desde cero
{: #create_toolchain_scratch}

Si desea crear una cadena de herramientas desde cero y conectarla a la app, siga estos pasos. También puede crear todas las integraciones para crear la app y desplegarla en el clúster de Kubernetes. La característica de cadena de herramientas DevOps ofrece plantillas, pero estos pasos le muestran cómo configurar una cadena de herramientas DevOps desde cero.

Cuando elija crear una cadena de herramientas a partir de su nueva app, se abre la página [Crear una cadena de herramientas](https://{DomainName}/devops/create) en el [panel de control de DevOps](https://{DomainName}/devops/) en un nuevo separador del navegador. Después de crear y configurar la cadena de herramientas en dicho separador, debe volver a la página **Conectar una cadena de herramientas** en la app y renovar la página.
{:tip}

1. En la página **Crear una cadena de herramientas**, pulse la plantilla **Crear su propia cadena de herramientas**.
2. En la página **Crear su propia cadena de herramientas**, escriba un nombre para la cadena de herramientas, seleccione una región y un grupo de recursos (predeterminado) y pulse **Crear**.

Se crea una cadena de herramientas vacía sin herramientas ni integraciones preconfiguradas. Continúe para configurar y probar la nueva cadena de herramientas completando los pasos restantes.

## Adición de una integración de GitHub

Puede configurar la cadena de herramientas DevOps con la integración de GitHub siguiendo los pasos siguientes:

1. En la plantilla de la cadena de herramientas DevOps, pulse **Añadir una herramienta**.
2. Seleccione **GitHub** (si el repositorio se encuentra en GitHub público o en Enterprise GitHub).
3. En la página **Configurar la integración** de GitHub, siga estos pasos:
  * Seleccione (o escriba) el URL del **Servidor GitHub**.
  * Si ve el mensaje "No autorizado en GitHub", pulse **Autorizar**. A continuación, en la página **Autorizar cadenas de herramientas de IBM Cloud**, pulse **Autorizar a IBM-Cloud**. Luego escriba su contraseña de GitHub.
  * En la página **Configurar la integración**, seleccione **Existente** para el **Tipo de repositorio** para que la cadena de herramientas DevOps configure el repositorio con un webhook y _no_ copie ni bifurque su repositorio.
  * Escriba el **URL de repositorio**. (Por ejemplo, `https://github.com/yourrepo/spring-boot-hello-world`).
  * Espere un momento; es posible que se le solicite autorizar a GitHub a que otorgue permiso a la cadena de herramientas DevOps para que utilice la API ReST de GitHub para configurar el repositorio con los webhooks necesarios para activar la cadena de herramientas.
  * Pulse **Crear integración**.

Ha configurado esta cadena de herramientas DevOps con una integración para el repositorio GitHub. Esto permite que la cadena de herramientas establezca un webhook en el repositorio, de modo que las solicitudes de extracción y los envíos de código en dicho repositorio desencadenen una solicitud POST destinada a la cadena de herramientas. Puede buscar en los valores de su repositorio para ver el nuevo webhook.

## Adición de un Delivery Pipeline para crear, probar y desplegar la app

Delivery Pipeline es donde tiene lugar el trabajo.

1. Pulse **Añadir una herramienta**.
2. Seleccione **Delivery Pipeline**.
3. En la página **Configurar la integración** de Delivery Pipeline, siga estos pasos:
 * Especifique "Integración continua" para el nombre del conducto.
 * Pulse **Crear integración**.

Ha creado un conducto de entrega vacío. A continuación, defina las etapas de conducto para dirigir la entrada (el contenido del repositorio GitHub) a su destino. Puesto que en esta guía de aprendizaje se presupone que tiene un repositorio GitHub que genera una imagen de Docker de trabajo y que está dirigido a un clúster de IBM Containers Kubernetes, creará etapas del conducto con entradas, scripts de shell y salidas destinadas a alcanzar este objetivo.

### Configuración de la etapa de conducto "Crear y publicar"

1. Pulse el conducto de entrega que ha creado.
2. En la página del conducto de entrega, pulse **Añadir una etapa**.
3. En el separador **Entrada** de la página **Configuración de etapa**, complete los campos tal como se indica a continuación:
  * Para el nombre de la etapa, escriba **Crear y publicar imagen de Docker**.
  * **Tipo de entrada**: seleccione **Repositorio Git**.
  * **Repositorio Git**: seleccione el repositorio GitHub.
  * **Rama**: seleccione la rama que utiliza para la integración continua.
4. Pulse el separador **Trabajos** y complete los campos tal como se indica a continuación:
  * Pulse el icono **Añadir trabajo '+'** y seleccione **Crear** para el tipo de trabajo.
  * Escriba un nombre, como por ejemplo **Crear y publicar**.
  * **Tipo de compilador**: seleccione **Registro de contenedor**.
  * **Región de IBM Cloud**: seleccione la región en la que se encuentra el clúster de Kubernetes.
  * **Clave de API**: seleccione **Especificar una clave de API existente**. Si no tiene una clave o no conoce la clave de la API, puede [obtener una clave de API](https://{DomainName}/iam/#/apikeys) abriendo otra ventana del navegador y navegando a **Gestionar** > **Seguridad** > **Claves de API de plataforma**. Asegúrese de guardar esta clave en un lugar seguro.
  * **Nombre de cuenta**: este campo se completa automáticamente cuando se especifica una clave de API.
  * **Espacio de nombres de registro de contenedor**: especifique el [espacio de nombres de registro de contenedor](https://{DomainName}/containers-kubernetes/registry/namespaces) (lo encontrará pulsando el icono **Menú** ![Icono Menú](../../icons/icon_hamburger.svg) y seleccionando **Contenedores** > **Registro** > **Espacios de nombres**.)
  * **Nombre de imagen de Docker**: especifique **continuo** porque esta etapa de compilación de conducto es para la compilación continua de la rama de integración continua del repositorio.
  * **Script de compilación**: observe el script de shell. Carece de las instrucciones de compilación de app de _su_ repositorio. Tiene que añadir una o varias líneas después de la primera línea `#!/bin/bash`. Por ejemplo, para un repo que se crea utilizando maven, puede añadir algunas líneas similares a las del ejemplo siguiente:

    ```bash
    export JAVA_HOME=/opt/IBM/java8
    # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
    export MAVEN_OPTS="-Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
    mvn -B clean verify
    ```
    {: codeblock}
5. Pulse **Guardar**. Ahora aparece en la cadena de caracteres la etapa de conducto "Crear y publicar".

### Prueba de la etapa de conducto "Crear y publicar"

Pulse el icono **Reproducir** hasta que la compilación se ejecute correctamente. Sabrá que funciona cuando la etapa se vuelva verde y la salida del script confirme sus expectativas. El objetivo en esta etapa es publicar una imagen de Docker en el registro de imágenes. Si el script no muestra lo suficiente para dejarle satisfecho, puede ver el registro de la imagen para confirmar la publicación pulsando el icono **Menú** ![Icono Menú](../../icons/icon_hamburger.svg) y luego seleccionando **Contenedores** > **Registro** > **Repositorios privados**. A continuación, confirme que aparece en la lista un repositorio que termina por el nombre `/continuo`. (Recuerde que ese era el nombre de la imagen.)

### Configuración de la etapa de conducto "Desplegar en clúster"

Hasta el momento, ha publicado una imagen de Docker en el registro privado de imágenes de Docker. Ahora, es el momento de crear una etapa que despliegue esa imagen en el clúster de Kubernetes.

1. En la página del conducto de entrega, pulse **Añadir una etapa**.
2. En el separador **Entrada** de la página **Configuración de etapa**, complete los campos tal como se indica a continuación:
  * **Nombre**: escriba **Desplegar**.
  * **Tipo de entrada**: seleccione **Crear artefactos**.
  * **Etapa**: seleccione **Compilar y publicar imagen de Docker**.
  * **Trabajo**: seleccione **Compilar y publicar**.
  * **Desencadenante de etapa**: puesto que este es el conducto de integración continua, seleccione el valor predeterminado **Ejecutar trabajos y luego se completará la etapa anterior**.
3. Pulse el separador **Trabajos** y complete los campos tal como se indica a continuación:
  * Pulse el icono **Añadir trabajo '+'** y seleccione **Desplegar** para el tipo de trabajo.
  * Escriba un nombre, como por ejemplo **Desplegar en clúster de integración continua**.
  * **Tipo de desplegador**: seleccione **Kubernetes**.
  * **Región de IBM Cloud**: seleccione la región en la que se encuentra el clúster de Kubernetes.
  * **Clave de API**: seleccione **Especificar una clave de API existente**. Si no tiene una clave o no conoce la clave de la API, puede [obtener una clave de API](https://{DomainName}/iam/#/apikeys) abriendo otra ventana del navegador y navegando a **Gestionar** > **Seguridad** > **Claves de API de plataforma**. Asegúrese de guardar esta clave en un lugar seguro.
  * Acepte el resto de valores predeterminados.
4. Pulse **Guardar**. Ahora aparece en la cadena de caracteres la etapa de conducto "Desplegar".

### Prueba de la etapa de conducto "Desplegar en clúster"

Pulse el icono **Reproducir** hasta que la compilación se ejecute correctamente. Sabrá que funciona cuando la etapa se vuelva verde y la salida del script confirme sus expectativas. Puede ver los registros correspondientes a la etapa. Casi al final de los registros, busque un enlace a la app en ejecución sobre el que puede pulsar. Sin embargo, solo _usted_ conoce la raíz de contexto de la app y la vía de acceso. Adjunte la vía de acceso correcta para confirmar que se ejecuta.
