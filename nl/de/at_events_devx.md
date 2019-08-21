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

|Aktionen	|Beschreibung	|
|-----|-------------|
|bluemix-developer-experience.app.create |Ein Ereignis wird generiert, wenn ein Benutzer eine App erstellt.|
|bluemix-developer-experience.app.read |Ein Ereignis wird generiert, wenn eine der folgenden Situationen eintritt:<br><br>Ein Benutzer lädt den App-Code herunter.<br><br>Ein Benutzer lädt die Berechtigungsnachweisdatei über die Befehlszeilenschnittstelle des {{site.data.keyword.dev_console}} herunter.<br><br>In der {{site.data.keyword.cloud_notm}}-Infrastruktur für Entwicklererfahrungen werden Berechtigungsnachweise für Services gelesen, die einer App zugeordnet sind.<br><br>Ein Benutzer zeigt die Liste der Apps an. Beispiel: Ein Benutzer zeigt die Liste der Apps in der {{site.data.keyword.dev_console}}-Konsole oder über die {{site.data.keyword.dev_cli_short}}-Benutzerschnittstelle an.|
|bluemix-developer-experience.app.update |Ein Ereignis wird generiert, wenn eine der folgenden Situationen eintritt:<br><br>In der App wird etwas geändert. Beispiel: Ein Benutzer ändert den Namen der App.<br><br>Ein neuer Service wird erstellt und zu einer App hinzugefügt.<br><br>Ein vorhandener Service wird zu einer App hinzugefügt.<br><br>Ein Service wird in einer App entfernt.<br><br>Für eine App wird Code generiert.<br><br>Eine DevOps-Toolkette wird über die {{site.data.keyword.cloud_notm}}-Konsole hinzugefügt. Beispiel: Ein Benutzer wählt die Option **Continuous Delivery konfigurieren** auf der Seite "App-Details" aus.|
|bluemix-developer-experience.app.delete |Ein Ereignis wird generiert, wenn ein Benutzer eine App löscht. |
{: caption="Tabelle 1. Aktionen, die Ereignisse generieren" caption-side="top"}
