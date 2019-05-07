---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-23"

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

Para el desarrollo sin servidor, puede utilizar la oferta de funciones como servicio (FaaS) de IBM, {{site.data.keyword.openwhisk}}. Puede ejecutar la lógica de aplicación con {{site.data.keyword.openwhisk_short}} en respuesta a sucesos o invocaciones directas desde apps web o móviles a través de HTTP sin suministro ni gestión de servidores.{{site.data.keyword.openwhisk_short}} realiza la administración del sistema como escalado automático, gestión de disponibilidad y mantenimiento para que, como desarrollador, pueda centrarse en escribir la lógica de aplicación.
{:shortdesc}

Puede utilizar la interfaz de usuario (IU) o la interfaz de línea de mandatos (CLI) de {{site.data.keyword.openwhisk_short}} para desarrollar las aplicaciones. Ambas tienen prestaciones similares para desarrollar aplicaciones. La CLI proporciona más control sobre el despliegue y las operaciones. Para obtener más información sobre {{site.data.keyword.openwhisk_short}}, consulte la [documentación](/docs/openwhisk?topic=cloud-functions-getting_started).

## Interfaz de usuario de {{site.data.keyword.openwhisk_short}}
{: #serverless-apps-ui}

Pruebe {{site.data.keyword.openwhisk_short}} en su [navegador](https://{DomainName}/openwhisk/actions){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo"). Vaya a la página [Conceptos](https://{DomainName}/openwhisk/learn){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo") para realizar una visita rápida de la interfaz de usuario de {{site.data.keyword.openwhisk_short}}.

## Desarrollo con la CLI
{: #openwhisk_start_configure_cli}

Para obtener más información sobre la instalación y el desarrollo con la CLI de {{site.data.keyword.openwhisk_short}}, consulte [Configuración de la CLI de {{site.data.keyword.openwhisk_short}}](https://{DomainName}/openwhisk/cli){: new_window} ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo").

## Exposición de API y conjuntos de datos como acciones web
{: #expose-actions}

De forma predeterminada, {{site.data.keyword.openwhisk_short}} define acciones que requieren una clave de autenticación. En entornos móviles de producción, es frecuentemente necesario autorizar a clientes móviles basados en flujos de OAuth para que expongan API y conjuntos de datos específicos.

{{site.data.keyword.openwhisk_short}} permite a los desarrolladores exponer sus funciones como acciones web, que se anotan, para crear rápidamente aplicaciones basadas en web. Puede programar la lógica de fondo con acciones anotadas a las que la aplicación web puede acceder de forma anónima, sin necesidad de una clave de autenticación de {{site.data.keyword.openwhisk_short}}.

Para exponer una acción como una acción web, vaya al separador **Puntos finales** de la acción y seleccione **Habilitar como acción web**.

Ahora, los usuarios pueden llegar a la acción desde un navegador o una solicitud cURL, por ejemplo:
```
curl https://openwhisk.cloud.ibm.com/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

**Salida:**
```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

{{site.data.keyword.openwhisk_short}} proporciona un [SDK móvil](/docs/openwhisk?topic=cloud-functions-openwhisk_mobile_sdk) para dispositivos iOS y watchOS que permite a las apps móviles enviar fácilmente desencadenantes remotos e invocar acciones remotas.
