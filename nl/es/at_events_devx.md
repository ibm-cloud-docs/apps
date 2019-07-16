---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-04"

keywords: apps, applications, activity tracking events

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:deprecated: .deprecated}
{:table: .aria-labeledby="caption"}

# Sucesos de {{site.data.keyword.dev_console}} {{site.data.keyword.cloudaccesstrailshort}}
{: #at_events}

Como responsable de seguridad, auditor o gestor, puede utilizar el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar el seguimiento de cómo interactúan los usuarios y las aplicaciones con la {{site.data.keyword.dev_console}} en {{site.data.keyword.cloud}}.
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} está en desuso. A partir del 9 de mayo de 2019, no puede suministrar nuevas instancias de {{site.data.keyword.cloudaccesstrailshort}} y se eliminará el acceso a las instancias del plan *Lite*. Se da soporte a las instancias existentes del plan premium hasta el 30 de septiembre de 2019. Para seguir supervisando la actividad de la cuenta de {{site.data.keyword.cloud_notm}}, suministre una instancia de [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

El servicio {{site.data.keyword.cloudaccesstrailfull_notm}} registra actividades iniciadas por el usuario que cambian el estado de un servicio en {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Acerca de {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov).

## Dónde ver los sucesos
{: #view-events-ui}

Los sucesos de {{site.data.keyword.cloudaccesstrailshort}} están disponibles en el dominio de la cuenta de {{site.data.keyword.cloudaccesstrailshort}} que está disponible en la región de {{site.data.keyword.cloud_notm}} donde se generan los sucesos de {{site.data.keyword.dev_console}}.

Para empezar a supervisar las acciones del usuario, consulte la [Guía de aprendizaje de iniciación](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started).

## Lista de sucesos
{: #events}

La tabla siguiente lista las acciones que generan un suceso:

|Acciones	|Descripción	|
|-----|-------------|
|bluemix-developer-experience.app.create |Se genera un suceso cuando un usuario crea una app.|
|bluemix-developer-experience.app.read |Se genera un suceso cuando se produce cualquiera de las situaciones siguientes: <br><br>Un usuario descarga el código de app.<br><br>Un usuario descarga el archivo de credenciales utilizando la CLI de {{site.data.keyword.dev_console}}.<br><br>La infraestructura de {{site.data.keyword.cloud_notm}} lee credenciales correspondientes a servicios asociados a una app.<br><br>Un usuario visualiza la lista de apps. Por ejemplo, un usuario visualiza la lista de apps en la consola de {{site.data.keyword.dev_console}} o mediante la CLI de {{site.data.keyword.dev_cli_short}}.|
|bluemix-developer-experience.app.update |Se genera un suceso cuando se produce cualquiera de las situaciones siguientes: <br><br>Cambia algo referente a la app. Por ejemplo, un usuario modifica el nombre de la app.<br><br>Se crea un nuevo servicio y se añade a una app.<br><br>Se añade un servicio existente a una app.<br><br>Se elimina un servicio de una app.<br><br>Se genera código para una app.<br><br>Se añade una cadena de herramientas DevOps mediante la consola de {{site.data.keyword.cloud_notm}}. Por ejemplo, un usuario selecciona **Configurar entrega continua** en la página de Detalles de la app.|
|bluemix-developer-experience.app.delete |Se genera un suceso cuando un usuario suprime una app. |
{: caption="Tabla 1. Acciones que generan sucesos" caption-side="top"}
