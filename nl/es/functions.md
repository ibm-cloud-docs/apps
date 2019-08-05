---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-29"

keywords: apps, serverless, serverless app, functions, cli, api, sdk, create serverless app, serverless app tutorial

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creación de apps sin servidor
{: #serverless}

Para el desarrollo sin servidor, puede utilizar {{site.data.keyword.openwhisk}}, que es la oferta de funciones como servicio (FaaS) de IBM. Puede ejecutar la lógica de aplicación con {{site.data.keyword.openwhisk_short}} en respuesta a sucesos o invocaciones directas desde apps o web o móviles a través de HTTP sin suministro ni gestión de servidores. {{site.data.keyword.openwhisk_short}} realiza la administración del sistema, como escalado automático, la gestión de disponibilidad y el mantenimiento para que el usuario, como desarrollador, pueda centrarse en escribir la lógica de la app.
{:shortdesc}

Puede desarrollar sus apps sin servidor utilizando uno de los métodos siguientes:
* Interfaz de usuario (UI) de {{site.data.keyword.openwhisk_short}}.
* Interfaz de línea de mandatos (CLI) de {{site.data.keyword.openwhisk_short}}, que proporciona más control a su despliegue y a sus operaciones.
* Kit de inicio de {{site.data.keyword.openwhisk_short}}, donde puede configurar la entrega continua utilizando una cadena de herramientas DevOps y un conducto de entrega.

Para obtener más información sobre {{site.data.keyword.openwhisk_short}}, consulte la [documentación](/docs/openwhisk?topic=cloud-functions-getting_started).


## Desarrollo de la UI de {{site.data.keyword.openwhisk_short}}
{: #serverless-apps-ui}

Pruebe {{site.data.keyword.openwhisk_short}} en su [navegador](https://{DomainName}/functions/actions){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo"). Vaya a la página [Conceptos](https://{DomainName}/functions/learn){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") para realizar una visita rápida de la interfaz de usuario de {{site.data.keyword.openwhisk_short}}.

## Desarrollo con la CLI
{: #openwhisk_start_configure_cli}

Para obtener más información sobre la instalación y el desarrollo con la CLI de {{site.data.keyword.openwhisk_short}}, consulte [Configuración de la CLI de {{site.data.keyword.openwhisk_short}}](https://{DomainName}/functions/cli){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo").

## Exposición de API y conjuntos de datos como acciones web
{: #expose-actions}

De forma predeterminada, {{site.data.keyword.openwhisk_short}} define acciones que requieren una clave de autenticación. En entornos móviles de producción, es frecuentemente necesario autorizar a clientes móviles basados en flujos de OAuth para que expongan API y conjuntos de datos específicos.

{{site.data.keyword.openwhisk_short}} permite a los desarrolladores exponer sus funciones como acciones web, que se anotan, para crear rápidamente apps basadas en web. Puede programar la lógica de fondo con acciones anotadas a las que la app web puede acceder de forma anónima, sin necesidad de una clave de autenticación de {{site.data.keyword.openwhisk_short}}.

Para exponer una acción como una acción web, vaya al separador **Puntos finales** de la acción y seleccione **Habilitar como acción web**.

Ahora, los usuarios pueden llegar a la acción desde un navegador o una solicitud cURL, por ejemplo:
```
curl https://openwhisk.cloud.ibm.com/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

Salida:
```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} proporciona un [SDK móvil](/docs/openwhisk?topic=cloud-functions-pkg_mobile_sdk) para dispositivos iOS y watchOS que permite a las apps móviles enviar fácilmente desencadenantes remotos e invocar acciones remotas.

## Creación de apps sin servidor utilizando un kit de inicio
{: #serverless-starter}

Puede utilizar un kit de inicio para crear una app sin servidor como, por ejemplo, la app sin servidor de ejemplo de Python. Para localizar los kits de inicio, siga estos pasos:

1. Vaya a la página [Kits de inicio de App Service](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Icono de enlace externo](../icons/launch-glyph.svg "Icono de enlace externo") en la consola {{site.data.keyword.dev_console}}.
2. Escriba `serverless` en la barra de búsqueda para filtrar la lista de los kits de inicio.
3. Seleccione un kit de inicio sin servidor como, por ejemplo la app sin servidor de ejemplo de Python.
4. Asigne un nombre a la app y seleccione un grupo de recursos.
5. Opcional. Proporcione etiquetas para clasificar la app. Para obtener más información, consulte [Cómo trabajar con etiquetas](/docs/resources?topic=resources-tag).
6. Cree o seleccione una instancia de servicio Cloudant existente.
7. Opcional. Para inspeccionar el código antes de añadir más servicio o de desplegar la app, pulse **Ver código fuente**. Consulte el archivo `README.md` para averiguar si es necesario realizar algo más para activar y ejecutar su app.
8. Pulse **Crear**.

¡Buen comienzo! Acaba de crear una app.

## Adición de servicios (opcional)
{: #serverless-services}

Si un kit de inicio requiere servicios específicos, dispone servicios de suministro automático, de modo que se crean automáticamente instancias para dichos servicios cuando crea la app.

1. En la página Detalles de la app, pulse **Crear servicio** o **Conectar servicios existentes**, en función de si ya tiene servicios que desea conectar a esta app.
2. Seleccione el tipo de servicio que desee y siga las indicaciones para añadir un servicio existente a la app o para crear una instancia de servicio.

Después de añadir todos los servicios que desee, se muestran en la página Detalles de la app.

## Despliegue de la app
{: #serverless-deploy}

Para desplegar su app, siga estos pasos:

1. En la página Detalles de la app, pulse **Desplegar**.
2. Seleccione **Desplegar Cloud Functions** y pulse **Siguiente**.
3. En la página Configurar cadena de herramientas, escriba el nombre de una cadena de herramientas, seleccione una región y pulse **Crear**. Después de seleccionar y configurar el destino del despliegue, la página Detalles de la app indica que se ha configurado la entrega continua.
4. Opcional. Revise las acciones en la consola {{site.data.keyword.openwhisk_short}} pulsando el icono Acciones ![Icono Más acciones](../icons/action-menu-icon.svg) y seleccionando **Funciones de nube abierta**.
5. Opcional. Consulte el repositorio que contiene el código generado para su app y los servicios pulsando **Ver repositorio**.

## Verificación de que la app se ha desplegado
{: #serverless-verify}

Con una cadena de herramientas correctamente configurada, un ciclo de despliegue de compilación empieza automáticamente después de cada fusión en la rama maestra en su repositorio. Para obtener más información, consulte [Creación y despliegue](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

Para verificar que la app se ha desplegado correctamente, siga estos pasos:

1. En la página Detalles de la app, pulse **Ver cadena de herramientas**.
2. Pulse sobre **Conducto de entrega**, donde puede iniciar compilaciones, gestionar el despliegue y ver los registros y el historial.
3. Si el despliegue se ha realizado correctamente, cada etapa del conducto indica **Etapa pasada**.
4. Para ver la acción y la información de la API, pulse **Ver registros e historial** en el mosaico **Etapa de despliegue**.
