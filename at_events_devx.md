---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-03"

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

# {{site.data.keyword.dev_console}} {{site.data.keyword.cloudaccesstrailshort}} events
{: #at_events}

As a security officer, auditor, or manager, you can use the {{site.data.keyword.cloudaccesstrailfull}} service to track how users and applications interact with the {{site.data.keyword.dev_console}} in the {{site.data.keyword.cloud}}.
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} is deprecated. As of 9 May 2019, you cannot provision new {{site.data.keyword.cloudaccesstrailshort}} instances, and access to *Lite* plan instances will be removed. Existing premium plan instances are supported until 30 September 2019. To continue monitoring the activity of your {{site.data.keyword.cloud_notm}} account, provision an instance of the [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

The {{site.data.keyword.cloudaccesstrailfull_notm}} service records user-started activities that change the state of a service in {{site.data.keyword.cloud_notm}}. For more information, see [About {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov).

## Where to view the events
{: #view-events-ui}

{{site.data.keyword.cloudaccesstrailshort}} events are available in the {{site.data.keyword.cloudaccesstrailshort}} account domain that is available in the {{site.data.keyword.cloud_notm}} region where {{site.data.keyword.dev_console}} events are generated.

To start monitoring your user's actions, see the [Getting started tutorial](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started).

## List of events
{: #events}

The following table lists the actions that generate an event:

<table>
  <caption>Actions that generate events</caption>
  <tr>
    <th>Actions</th>
	  <th>Description</th>
  <tr>
  <tr>
    <td>bluemix-developer-experience.app.create</td>
	  <td>An event is generated when a user creates an app.</td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.read</td>
	  <td>An event is generated when any of the following situations happen: </br><ul><li>A user downloads the app code.</li> <li>A user downloads the credentials file by using the {{site.data.keyword.dev_console}} CLI.</li> <li>The {{site.data.keyword.cloud_notm}} infrastructure reads credentials for services that are associated with an app.</li> <li>A user views the list of app, for example, when the user views the list of apps in the {{site.data.keyword.dev_console}} developer console or through the {{site.data.keyword.dev_cli_short}} CLI.</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.update</td>
	  <td>An event is generated when any of the following situations happen: </br><ul><li>Something about the app changes, for example, when a user modifies the name of the app. </li><li>A new service is created and added to an app.</li><li>An existing service is added to an app.</li><li>A service is removed from an app.</li><li>Code is generated for an app.</li><li>A DevOps toolchain is added through the {{site.data.keyword.cloud_notm}} console, for example, by selecting **Configure continuous delivery**.</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.delete</td>
	  <td>An event is generated when a user deletes an app.</td>
  </tr>
</table>
