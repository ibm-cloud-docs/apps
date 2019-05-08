---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-25"

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

# {{site.data.keyword.dev_console}} {{site.data.keyword.cloudaccesstrailshort}}events
{: #at_events}

Als Sicherheitsbeauftragter, Prüfer oder Manager eines bestimmten Bereichs können Sie mit dem Service {{site.data.keyword.cloudaccesstrailfull}} die Interaktion von Benutzern und Anwendungen mit dem {{site.data.keyword.dev_console}} in {{site.data.keyword.cloud}} verfolgen.
{: shortdesc}

{{site.data.keyword.cloudaccesstrailfull}} ist veraltet. Ab dem 9. Mai 2019 können Sie keine neuen Instanzen von {{site.data.keyword.cloudaccesstrailshort}} bereitstellen und der Zugriff auf die *Lite*-Planinstanzen wird entfernt. Bestehende Prämiumplaninstanzen werden bis zum 30. September 2019 unterstützt. Wenn Sie mit der Überwachung des {{site.data.keyword.cloud_notm}}-Kontos fortfahren möchten, stellen Sie eine Instanz von [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started) bereit.
{: deprecated}

Der Service {{site.data.keyword.cloudaccesstrailfull_notm}} zeichnet die von Benutzern gestarteten Aktivitäten auf, durch die sich der Status eines Service in {{site.data.keyword.cloud_notm}} ändert. Weitere Informationen hierzu finden Sie im Abschnitt mit [Informationen zu {{site.data.keyword.cloudaccesstrailshort}}](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov).

## Wo werden Ereignisse angezeigt?
{: #view-events-ui}

{{site.data.keyword.cloudaccesstrailshort}}-Ereignisse sind in der {{site.data.keyword.cloudaccesstrailshort}}-Kontodomäne verfügbar, die zu der {{site.data.keyword.cloud_notm}}-Region gehört, in der {{site.data.keyword.dev_console}}-Ereignisse generiert werden.

Weitere Informationen zum Einstieg in die Überwachung der Benutzeraktionen finden Sie im [Lernprogramm 'Einführung'](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started).

## Ereignisliste
{: #events}

In der folgenden Tabelle werden die Aktionen aufgeführt, die das Generieren von Ereignissen auslösen:

<table>
  <caption>Aktionen, die Ereignisse generieren</caption>
  <tr>
    <th>Aktionen</th>
	  <th>Beschreibung</th>
  <tr>
  <tr>
    <td>bluemix-developer-experience.app.create</td>
	  <td>Ein Ereignis wird generiert, wenn ein Benutzer eine Anwendung erstellt.</td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.read</td>
	  <td>Ein Ereignis wird generiert, wenn eine der folgenden Situationen eintritt: </br><ul><li>Ein Benutzer lädt den Anwendungscode herunter.</li> <li>Ein Benutzer lädt die Berechtigungsnachweisdatei über die Befehlszeilenschnittstelle des {{site.data.keyword.dev_console}} herunter.</li> <li>In der Infrastruktur für Entwicklererfahrungen werden Berechtigungsnachweise für Services gelesen, die einer Anwendung zugeordnet sind.</li> <li>Die Anwendungsliste wird von einem Benutzer angezeigt, z. B. wenn der Benutzer die Liste der Anwendungen in der {{site.data.keyword.dev_console}}-Konsole oder über die {{site.data.keyword.dev_cli_short}}-Befehlszeilenschnittstelle anzeigt.</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.update</td>
	  <td>Ein Ereignis wird generiert, wenn eine der folgenden Situationen eintritt: </br><ul><li>Bei der Anwendung tritt eine Änderung auf, z. B. dadurch, dass der Name der Anwendung von einem Benutzer geändert wird. </li><li>Ein neuer Service wird erstellt und zu einer Anwendung hinzugefügt.</li><li>Ein vorhandener Service wird zu einer Anwendung hinzugefügt.</li><li>Ein Service wird in einer Anwendung entfernt.</li><li>Für eine Anwendung wird Code generiert.</li><li>Eine DevOps-Toolchain wird über die Umgebung für Entwicklererfahrungen hinzugefügt, indem z. B. die Option *Continuous Delivery konfigurieren* ausgewählt wird.</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.delete</td>
	  <td>Ein Ereignis wird generiert, wenn ein Benutzer eine Anwendung löscht.</td>
  </tr>
</table>
