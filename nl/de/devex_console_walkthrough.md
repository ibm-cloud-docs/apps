---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-11-29"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Walkthrough der {{site.data.keyword.cloud_notm}}-Entwicklerkonsole
{: #intro}

<!--I can't see how a customer needs to be walked through the experience without performing a specific task.-->


{{site.data.keyword.cloud}} Developer Experience ermöglicht einem Entwickler von für die Cloud nativen Anwendungen, eine App aus einer Vielzahl von Starter-Kits zu erstellen, wichtige für {{site.data.keyword.Bluemix_notm}} optimierte Services zu erstellen und zu verbinden und dann Arbeitscode rasch herunterzuladen oder für Continuous Delivery entsprechend einzurichten. Developer Experience stellt eine Reihe von Entwicklerkonsolen in {{site.data.keyword.Bluemix_notm}} bereit, mit denen Sie Ihre App erstellen, anzeigen, konfigurieren und verwalten sowie in einer Devops-Pipeline bereitstellen oder zur lokalen Entwicklung herunterladen können.

Durch die Erstellung einer App über eine {{site.data.keyword.cloud_notm}}-Entwicklerkonsole werden alle erforderlichen Komponenten Ihrer App unter Ihrem Konto auf dem {{site.data.keyword.cloud_notm}}-Server gepflegt. Daher können Sie zwischen der GUI der Entwicklerkonsole und [{{site.data.keyword.dev_cli_notm}}](/docs/cli/idt/index.html) nach Wunsch und Bedarf hin- und herwechseln.

{{site.data.keyword.cloud_notm}}-Entwicklerkonsolen bieten Ihnen einen nahtlosen Weg zum Erstellen einer einsatzbereiten Starter-App für den von Ihnen ausgewählten Anwendungsfall. Lassen Sie uns einen Blick auf die Schritte werfen, die Sie auf Ihrer Reise machen könnten.

<!-- Ready to jump in?  Visit the [{{site.data.keyword.cloud_notm}} Web App developer console](https://{DomainName}/developer/appservice) to get started.
{: tip} -->

##Anzeige 'Übersicht'
{: #overview_screen}

Die Anzeige 'Übersicht' stellt Inhalte dar, die auf den Themenschwerpunkt oder Kanalfokus der Entwicklerkonsole zugeschnitten ist, in der Sie arbeiten. Von der Anzeige 'Übersicht' aus können Sie Dokumentation einsehen, auf Lernressourcen zugreifen, Services durchsuchen, vorgestellte Starterkits anzeigen oder sich mit einer umfangreicheren Sammlung von Starter-Kits verbinden. Um  in die Ansicht 'Starter-Kits' zu gelangen, klicken Sie in der Navigation auf `Starter-Kits`.

![Anzeige 'Übersicht' in der Entwicklerkonsole](images/overview_screen.png "Anzeige 'Übersicht") <br> *Anzeige 'Übersicht' in der Entwicklerkonsole*

##Ansicht 'Starter-Kit'
{: #starter_kits_view}

In der Ansicht 'Starter-Kits' wird die Sammlung der Starter-Kits angezeigt, die für einen Bereich eines Anwendungsfalls spezifisch sind. Sie können auf der Karte eines Starter-Kits auf verschiedene Links klicken, um Demonstrationen und weitere Informationen anzuzeigen. Wählen Sie ein Starter-Kit aus, um in die Ansicht 'Neue App erstellen' zu gelangen.

In manchen Fällen führt die Auswahl eines Starter-Kits dazu, dass weitere Details zu dem Starter-Kit angezeigt werden. In diesem Fall klicken Sie einfach auf die Schaltfläche `Erstellen`, um in die Ansicht 'Neue App erstellen' zu wechseln.{: tip}

![Ansicht 'Starter-Kits' in der Entwicklerkonsole](images/starter_kits_view.png "Ansicht 'Starter-Kits'") <br> *Ansicht 'Starter-Kits' in der Entwicklerkonsole*

##Ansicht 'Neue App erstellen'
{: #create_new_project_view}

In der Ansicht 'Neue App erstellen' geben Sie Ihrer App einen Namen, stellen Bereitstellungs- und Routing-Informationen bereit und wählen eine Sprache aus. Beachten Sie, dass im Bereich rechts auch die Services angezeigt werden, die bei der Erstellung Ihrer App automatisch bereitgestellt werden, wenn Sie Ihre App erstellen, sowie die Preisstrukturpläne für den jeweiligen Service und die gültigen Bedingungen. Durch Klicken auf `Erstellen` gelangen Sie zur Ansicht 'App-Details'. Sofern Sie nicht bereits bei {{site.data.keyword.cloud_notm}} angemeldet sind, müssen Sie die Anmeldung jetzt durchführen.

![Ansicht 'Neue App erstellen' in der Entwicklerkonsole](images/create_new_project_view.png "Ansicht 'Neue App erstellen'") <br> *Ansicht 'Neue App erstellen' in der Entwicklerkonsole*

## Ansicht 'App-Details'
{: #project_details_view}

In der Ansicht 'App-Details' wird eine Liste der Services angezeigt, die für Ihre App konfiguriert sind. Für jedes Element in der Liste werden der Servicename, Links zu anderen Informationen und eine Aktionsschaltfläche mit drei vertikal angeordneten Punkten (...) angezeigt. Die Optionen der Aktionsschaltfläche ermöglichen das Entfernen des Service aus der App, das Öffnen des Dashboards für den Service und das Löschen des Service. Beachten Sie, dass durch das Entfernen einer Serviceinstanz lediglich die Zuordnung zu dieser App entfernt, nicht aber die Serviceinstanz an sich gelöscht wird. Beachten Sie auch, dass die Serviceberechtigungsnachweise in dieser Ansicht konsolidiert sind, damit Sie nicht jede Ansicht der Serviceinstanz einzeln aufrufen müssen, um sie zu erhalten.


![Ansicht 'App-Details' in der Entwicklerkonsole](images/project_details_view.png "Ansicht 'App-Details'") <br> *Ansicht 'App-Details' in der Entwicklerkonsole*

Die Ansicht 'App-Details' ermöglicht Ihnen auch das Hinzufügen neuer oder bereits vorhandener Services zu Ihrer App, die nicht Teil des ursprünglichen Starter-Kits waren. Klicken Sie dazu im Listenfeld der Services auf den Link `Ressource hinzufügen`. Welche Services verfügbar sind, hängt von der Art der App und den Services ab, die in einer Region verfügbar sind. Das bedeutet, dass nicht alle Service zum Zuordnen zu allen Apps verfügbar sind.

![Dialog 'Ressourcen hinzufügen' in der Entwicklerkonsole](images/add_resource_dialog.png "Dialog 'Ressourcen hinzufügen'") <br> *Dialog 'Ressourcen hinzufügen' in der Entwicklerkonsole*

In der Ansicht 'App-Details' haben Sie auf zwei Arten Zugriff auf Ihren Code:

*  [Empfohlen] Klicken Sie auf die Schaltfläche `In Cloud bereitstellen`, um Ihren Code mit einer Push-Operation in ein Repository zu übertragen und Ihre App in {{site.data.keyword.cloud_notm}} bereitzustellen. Weitere Informationen zu der DevOps-Toolchain von {{site.data.keyword.cloud_notm}} erhalten Sie, wenn Sie [hier](/docs/services/ContinuousDelivery/toolchains_about.html#toolchains_about) klicken.
*  Wenn Sie einen kurzen Blick auf Ihren App-Code werden wollen, wählen Sie `Code herunterladen` aus, um den Code für Ihre App zu generieren und herunterzuladen.

##Ansicht 'App-Liste'
{: #project_list_view}

In der Ansicht 'App-Liste' wird eine Liste aller Apps angezeigt, die Sie erstellt haben. Von hier aus können Sie Ihre Apps umbenennen oder löschen. Klicken Sie auf eine Zeile mit dem Namen einer App, um zur Ansicht 'App-Details' zurückzugelangen.

![Ansicht 'App-Liste' in der Entwicklerkonsole](images/project_list_view.png "Ansicht 'App-Liste'") <br> *Ansicht 'App-Liste' in der Entwicklerkonsole*
