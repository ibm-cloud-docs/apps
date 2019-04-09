---

copyright:
  years: 2018
lastupdated: "2018-12-17"

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
{: #deploy}

Puede desplegar sus apps con una cadena de herramientas o con una interfaz de línea de mandatos (CLI). Una cadena de herramientas es un conjunto de integraciones de herramientas. La CLI constituye una forma simple de desplegar sus apps e instancias de servicio.
{: shortdesc}

## Despliegue de apps mediante cadenas de herramientas
{: #toolchains_getting_started}

Las cadenas de herramientas abiertas están disponibles en los entornos Público y Dedicado en {{site.data.keyword.Bluemix}}. Con una cadena de herramientas correctamente configurada, el despliegue de una app resulta sencillo. Un ciclo de despliegue de compilación se inicia automáticamente después de cada fusión en la rama maestra en su repositorio. 

Puede crear una cadena de herramientas de estas dos maneras: utilizando una plantilla para crear la cadena de herramientas o creando una cadena de herramientas desde una app. Para obtener más información sobre las cadenas de herramientas, consulte [Creación de cadenas de herramientas](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

## Despliegue de apps mediante la CLI
{: #cli}

{{site.data.keyword.cloud_notm}} proporciona una CLI sólida así como plugins y extensiones de herramientas de desarrollador que se integran con la CLI.

Antes de empezar, [descargue e instale la CLI de {{site.data.keyword.cloud_notm}}](/docs/cli/index.html).

<p>
<a class="xref" href="https://cloud.ibm.com/docs/cli/index.html#overview" target="_blank" title="(Se abre en un nuevo separador o ventana)"><img class="image" src="images/btn_bx_commandline.svg" alt="Descargar IBM Cloud Developer Tools" /></a>
</p>

La CLI no recibe soporte de Cygwin. Utilice la herramienta en una ventana que no sea la ventana de línea de mandatos de Cygwin.
{: important}

  1. {: download} Descargue el código de la app en un directorio nuevo para configurar su entorno de desarrollo.

    <a class="xref" href="https://cloud.ibm.com" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="(Se abre en un nuevo separador o ventana)"></a>

  2. Cambie al directorio donde se encuentra el código.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">su_nuevo_directorio</var></code></pre>

  3.  Realice los cambios al código de su app. Por ejemplo, si utiliza una aplicación de ejemplo de {{site.data.keyword.cloud_notm}} y la app contiene el archivo `src/main/webapp/index.html`, puede modificarla y editar la línea `Thanks for creating ...`.  Asegúrese de que la app se ejecuta localmente
antes de volver a desplegarla en {{site.data.keyword.cloud_notm}}.

    Preste atención al archivo `manifest.yml`. Cuando despliegue su app nuevamente en
{{site.data.keyword.cloud_notm}}, este archivo se utiliza para determinar el URL de la aplicación, la
asignación de memoria, el número de instancias y otros parámetros cruciales.

    Revise también el archivo `README.md`, que contiene detalles como instrucciones de compilación, si procede.

  Si la aplicación es una app Liberty, debe compilarla antes de volverla a desplegar.{: note}

  4. Conecte e inicie una sesión en {{site.data.keyword.cloud_notm}}.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">NombreDominio</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">nombre_usuario</var> -o <var class="keyword varname" data-hd-keyref="org_name">nombre_organización</var> -s <var class="keyword varname" data-hd-keyref="space_name">nombre_espacio</var></code></pre>

  Si utiliza un ID federado, añada la opción `-sso`.

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">nombre_organización</var> -s <var class="keyword varname" data-hd-keyref="space_name">nombre_espacio</var> -sso</code></pre>

  Si el valor contiene un espacio, debe especificar `nombre_usuario`, `nombre_organización` y `nombre_espacio` entre comillas simples o dobles, por ejemplo `-o "my org"`.{: note}

  5. Desde el nuevo directorio, despliegue la app en {{site.data.keyword.cloud_notm}} con el mandato `ibmcloud dev deploy`. Para obtener más información, consulte [la documentación de CLI](/docs/cli/idt/commands.html#deploy).

  <pre class="pre"><code class="hljs">ibmcloud dev deploy <var class="keyword varname" data-hd-keyref="app_name">app_name</var></code></pre>

  6. Para acceder a su app, vaya a https://<var class="keyword varname" data-hd-keyref="app_url">url_app</var>.<span class="keyword" data-hd-keyref="APPDomain">NombreDominioApp</span>.
