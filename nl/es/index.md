---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# Creación de apps en {{site.data.keyword.Bluemix_notm}}
{: #create}

En {{site.data.keyword.Bluemix}}, puede crear aplicaciones web y móviles a nivel de empresa y aprovechar las extensiones de nube alojadas por {{site.data.keyword.Bluemix_notm}}. Puede utilizar la consola de {{site.data.keyword.Bluemix}} y las herramientas de línea de mandatos para crear, ejecutar y desplegar las apps. Para empezar, puede seguir este caso de ejemplo completo de desarrollo.

## Paso 1: Registrarse para una cuenta de {{site.data.keyword.Bluemix_notm}}
{: #sign-up}

Vaya a [bluemix.net](bluemix.net). Escriba su correo electrónico, nombre, empresa, región, número de teléfono y ya habrá acabado. No necesita una tarjeta de crédito para registrarse para una cuenta gratuita. No dude en mirarlo todo.

## Paso 2: Buscar a través del catálogo
{: #catalog}

El catálogo de {{site.data.keyword.Bluemix_notm}} lista los recursos de infraestructura y de plataforma que ofrece. Puede empezar a crear su app seleccionando una máquina virtual, un contenedor, o Cloudant, una app de Cloud Foundry. Si necesita recursos de plataforma, {{site.data.keyword.Bluemix_notm}} también ofrece contenedores modelo, que proporcionan ejecución y otros servicios para ayudar a empezar la creación.

## Paso 3: Crear un recurso
{: #resource}

1. En el [panel de control](https://console.bluemix.net/dashboard/apps/), pulse **Crear recurso**.

2. Desde el catálogo, seleccione una app desde la sección Plataforma. A continuación, elija su ejecución. Por ejemplo, puede elegir un entorno de ejecución de IBM, como Liberty for Java, que están soportados por los paquetes de compilación de IBM. También puede elegir ejecuciones de Comunidad, como Tomcat, que se basan en paquetes de compilación de código abierto y de terceros.

  * [Iniciación a Containers](../containers/container_index.html)
  * [Iniciación a Openwhisk](../openwhisk/index.html)
  * [Creación de apps de Cloud Foundry](../cfapps/index.html#creating_cloud_foundry_apps)

3. Especifique el nombre de la app, el nombre de host y elija su plan de precios.

4. Seleccione el estilo de desarrollo. Puede editar la app en el editor de texto que prefiera y utilizar la línea de mandatos de {{site.data.keyword.Bluemix_notm}} para desplegarla en {{site.data.keyword.Bluemix_notm}}. También puede utilizar {{site.data.keyword.Bluemix_notm}} DevOps Services para desplegar la aplicación desde un navegador o utilizar Eclipse Tools for {{site.data.keyword.Bluemix_notm}} para trabajar en aplicaciones en el entorno de desarrollo integrado de Eclipse.

## Paso 4: Empezar añadiendo código
{: #code}

Cada app viene con una sección de iniciación que le ayuda a obtener todo el software y el contenido que necesita para empezar a trabajar.

En el panel de control, pulse la app y, a continuación, pulse **Iniciación**, que puede ayudarle a obtener el software que necesitará para desarrollar su app, apuntarle hacia el código fuente y ayudarle a desplegar la app por primera vez.

## Pasos siguientes
{: #next}

Una vez que se haya desarrollado su app, utilice nuestras guías [mejores prácticas](best-practice.html) y [disposición de nube](cloud-ready.html) para asegurarse de que la app está lista para {{site.data.keyword.Bluemix_notm}}. A continuación, [despliegue](../starters/install_cli.html) la app.
