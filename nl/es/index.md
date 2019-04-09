---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-04"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Guía de aprendizaje de iniciación
{: #tutorial-getting-started}

Puede crear aplicaciones web y móviles listas para la empresa en {{site.data.keyword.cloud}} y aprovechar las extensiones de nube contenidas en {{site.data.keyword.cloud_notm}}. Dispone de varias opciones para comenzar a trabajar. Puede crear una app con un kit de inicio que gestione el proceso en su nombre, o, si sabe exactamente lo que necesita, puede comenzar desde cero y crear su app con los recursos que necesite, o bien puede utilizar el repositorio existente y traer su propio código.
{: shortdesc}

## Antes de empezar
{: #prereqs-getting-started}

Puede crear su app mediante la consola de {{site.data.keyword.cloud_notm}} o mediante la interfaz de línea de mandatos (CLI). Si desea utilizar la CLI, consulte [Iniciación con la CLI de {{site.data.keyword.cloud_notm}}](/docs/cli/index.html#overview) para ver detalles sobre la instalación.

## Paso 1. Crear su app
{: #create-getting-started}

Para crear una app, seleccione uno de los siguientes puntos de partida:
* [Kit de inicio](/docs/apps/tutorials/tutorial_starter-kit.html#tutorial-starterkit): cree una app a partir de una selección de kits de inicio de servicio de app que gestionan el proceso automáticamente.
* [Personalizada](/docs/apps/tutorials/tutorial_scratch.html#tutorial-scratch): si sabe lo que quiere, cree una app personalizada desde cero con los recursos que necesite utilizando un kit de inicio en blanco.
* [Traiga su propio código](/docs/apps/tutorials/tutorial_byoc.html#tutorial-byoc): traiga su propio código estableciendo un enlace con su propio repositorio de contenido existente. La app y la imagen de Docker deben estar situadas en el mismo repositorio.
* [CLI](/docs/apps/create-deploy-cli.html#create-deploy-app-cli): cree y despliegue una app personalizada o de kit de inicio utilizando la CLI y las herramientas del desarrollador.
* [Patrones de código](/docs/apps/tutorials/tutorial_code-pattern.html#tutorial-codepattern): utilice un patrón de código de IBM Developer como base para crear su app.
* [Catálogo de {{site.data.keyword.cloud_notm}} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo")](https://cloud.ibm.com/catalog){: new_window}: puede examinar o buscar en el catálogo las apps y los servicios que puede crear y comenzar a utilizar hoy mismo.

## Paso 2. Añadir recursos
{: #resources-getting-started}

Si utiliza un kit de inicio para crear su app, los recursos se crean automáticamente. Puede asociar más recursos a su app pulsando **Añadir recurso** en la página de detalles de la app de la consola.

Para añadir recursos mediante la CLI, ejecute el mandato siguiente para añadir un servicio a la app. Puede seleccionar un servicio existente de uno ya habilitado en su cuenta, o añadir un nuevo servicio. 
```
ibmcloud dev edit
```
{: codeblock}

Para obtener más información, consulte [Adición de un servicio a la app](/docs/apps/reqnsi.html#add-resource).

## Paso 3. Desplegar la app
{: #deploy-getting-started}

Puede desplegar la app utilizando la consola o la línea de mandatos.

### Utilización de la consola
{: #console-getting-started}

Para desplegar la app mediante la consola, siga los pasos siguientes:

1. En la página **Detalles de la app**, pulse **Desplegar en la nube**.
2. Seleccione un método de despliegue y pulse **Crear**. {{site.data.keyword.cloud_notm}} crea de forma automática una cadena de herramientas abierta que se completa con un repositorio de Git y un conducto de entrega continua.
3. Abra la etapa del conducto de la nueva cadena de herramientas para ver el proceso de compilación y despliegue de forma que pueda visualizar en unos minutos su nueva app.

Para obtener más información, consulte la tabla de contenido para ver los diversos temas sobre despliegue en la sección "Despliegue e integración de apps".

### Utilización de la línea de mandatos
{: #cli-getting-started}

Para desplegar la app con la línea de mandatos, ejecute el mandato `ibmcloud dev deploy`. Consulte [Creación y despliegue de apps utilizando la CLI](/docs/apps/create-deploy-cli.html#create-deploy-app-cli) para obtener más información.

Ahora está preparado para el desarrollo iterativo y la entrega continua.
