---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-15"

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
{:table: .aria-labeledby="caption"}

# Sucesos de {{site.data.keyword.dev_console}} {{site.data.keyword.cloudaccesstrailshort}}
{: #at_events}

Como responsable de seguridad, auditor o gestor, puede utilizar el servicio {{site.data.keyword.cloudaccesstrailfull}} para realizar el seguimiento de cómo interactúan los usuarios y las aplicaciones con la {{site.data.keyword.dev_console}} en {{site.data.keyword.cloud}}.
{: shortdesc}

El servicio {{site.data.keyword.cloudaccesstrailfull_notm}} registra actividades iniciadas por el usuario que cambian el estado de un servicio en {{site.data.keyword.cloud_notm}}. Para obtener más información, consulte [Acerca de {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov).

## Dónde ver los sucesos
{: #view-events-ui}

Los sucesos de {{site.data.keyword.cloudaccesstrailshort}} están disponibles en el dominio de la cuenta de {{site.data.keyword.cloudaccesstrailshort}} que está disponible en la región de {{site.data.keyword.cloud_notm}} donde se generan los sucesos de {{site.data.keyword.dev_console}}.

Para empezar a supervisar las acciones del usuario, consulte la [Guía de aprendizaje de iniciación](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started).

## Lista de sucesos
{: #events}

La tabla siguiente lista las acciones que generan un suceso:

<table>
  <caption>Acciones que generan sucesos</caption>
  <tr>
    <th>Acciones</th>
	  <th>Descripción</th>
  <tr>
  <tr>
    <td>bluemix-developer-experience.app.create</td>
	  <td>Un suceso se genera cuando un usuario crea una aplicación.</td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.read</td>
	  <td>Un suceso se genera cuando se produce cualquiera de las situaciones siguientes: </br><ul><li>Un usuario descarga el código de aplicación.</li> <li>Un usuario descarga el archivo de credenciales utilizando la CLI de {{site.data.keyword.dev_console}}.</li> <li>La infraestructura de la experiencia del desarrollador lee credenciales para recursos asociados con una aplicación.</li> <li>Un usuario ve la lista de aplicaciones, por ejemplo, cuando el usuario ve la lista de aplicaciones en la consola de {{site.data.keyword.dev_console}} o mediante la CLI de {{site.data.keyword.dev_cli_short}}.</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.update</td>
	  <td>Un suceso se genera cuando se produce cualquiera de las situaciones siguientes: </br><ul><li>Cambia algo de la aplicación, por ejemplo, cuando un usuario modifica el nombre de la aplicación. </li><li>Se crea y se añade un recurso nuevo a una aplicación.</li><li>Se añade un recurso existente a una aplicación.</li><li>Se elimina un servicio de una aplicación.</li><li>Se genera código para una aplicación.</li><li>Se añade una cadena de herramientas de DevOps mediante la experiencia del desarrollador, por ejemplo, seleccionando *Desplegar en la nube*.</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.delete</td>
	  <td>Se genera un suceso cuando un usuario suprime una aplicación.</td>
  </tr>
</table>
