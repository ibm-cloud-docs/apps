---

copyright:
  years: 2016, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:table: .aria-labeledby="caption"}

# Evénements {{site.data.keyword.dev_console}} {{site.data.keyword.cloudaccesstrailshort}}
{: #at_events}

En tant que responsable de la sécurité, auditeur ou gestionnaire, vous pouvez utiliser le service {{site.data.keyword.cloudaccesstrailfull}} pour suivre comment les utilisateurs et les applications interagissent avec {{site.data.keyword.dev_console}} dans {{site.data.keyword.cloud}}.
{: shortdesc}

Le service {{site.data.keyword.cloudaccesstrailfull_notm}} enregistre les activités démarrées par l'utilisateur qui changent l'état d'un service dans {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir [About {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker/activity_tracker_ov.html#activity_tracker_ov).

## Emplacement des événements
{: #view-events-ui}

Les événements {{site.data.keyword.cloudaccesstrailshort}} sont disponibles dans le domaine de compte {{site.data.keyword.cloudaccesstrailshort}}, lui même disponible dans la région {{site.data.keyword.cloud_notm}} où les événements {{site.data.keyword.dev_console}} sont générés.

Pour commencer à surveiller les actions utilisateur, consultez le [tutoriel d'initiation](/docs/services/cloud-activity-tracker/index.html#getting-started-with-cla).

## Liste des événements
{: #events}

Le tableau suivant répertorie les actions qui génèrent un événement :

<table>
  <caption>Actions qui génèrent des événements</caption>
  <tr>
    <th>Actions</th>
	  <th>Description</th>
  <tr>
  <tr>
    <td>bluemix-developer-experience.app.create</td>
	  <td>Un événement est généré lorsqu'un utilisateur crée une application.</td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.read</td>
	  <td>Un événement est généré lorsqu'une des situations suivantes a lieu : </br><ul><li>Un utilisateur télécharge le code de l'application.</li> <li>Un utilisateur télécharge le fichier de données d'identification à l'aide de l'interface de ligne de commande {{site.data.keyword.dev_console}}.</li> <li>L'infrastructure d'expérience des développeurs lit les données d'identification pour les ressources associées à une application.</li> <li>Un utilisateur consulte la liste des applications dans la console {{site.data.keyword.dev_console}} ou via l'interface de ligne de commande {{site.data.keyword.dev_cli_short}}.</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.update</td>
	  <td>Un événement est généré lorsqu'une des situations suivantes a lieu : </br><ul><li>L'application a été modifiée (un utilisateur a modifié le nom de l'application, par exemple). </li><li>Une nouvelle ressource est créée et ajoutée à une application.</li><li>Une ressource existante est ajoutée à une application.</li><li>Un service est retiré d'une application.</li><li>Du code est généré pour une application.</li><li>Une chaîne d'outils DevOps est ajoutée via l'expérience des développeurs, par exemple, lors de la sélection de l'option *Déployer dans le cloud*.</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.delete</td>
	  <td>Un événement est généré lorsqu'un utilisateur supprime une application.</td>
  </tr>
</table>
