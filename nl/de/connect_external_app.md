---

copyright:
  years: 2015, 2018
lastupdated: "2018-11-05"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{: tip: .tip}

# Verbindung von Services zu externen Apps herstellen
{: #externalapp}

Möglicherweise verfügen Sie über Anwendungen, die außerhalb von {{site.data.keyword.Bluemix_notm}} erstellt und in Betrieb genommen wurden, oder Sie verwenden Tools von anderen Anbietern. Wenn ein {{site.data.keyword.Bluemix_notm}}-Service Serviceschlüssel zur Verfügung stellt, die über das Internet zugänglich sind, können Sie diese Services mit Ihren lokalen Apps oder mit Tools von anderen Anbietern verwenden.

Die folgenden Services stellen Serviceschlüssel bereit, die Sie extern verwenden können:

* {{site.data.keyword.alertnotificationshort}} <!--Alert Notification-->
* {{site.data.keyword.sparks}} <!--Analytics for Apache Spark-->
* {{site.data.keyword.blockchain}} <!--Blockchain-->
* {{site.data.keyword.cloudant}} <!--Cloudant&reg; NoSQL DB-->
* {{site.data.keyword.conversationshort}} <!--Conversation-->
* {{site.data.keyword.discoveryshort}} <!--Discovery-->
* {{site.data.keyword.geospatialshort_Geospatial}} <!--Geospatial Analytics-->
* {{site.data.keyword.GlobalizationPipeline_short}} <!--Globalization Pipeline-->
* {{site.data.keyword.appconserviceshort}} <!--IBM&reg; App Connect-->
* {{site.data.keyword.languagetranslatorshort}} <!--Language Translator-->
* {{site.data.keyword.dwl_short}} <!--Lift-->
* {{site.data.keyword.messagehub}} <!--Message Hub-->
* {{site.data.keyword.nlclassifiershort}} <!--Natural Language Classifier-->
* {{site.data.keyword.objectstorageshort}} <!--Object Storage-->
* {{site.data.keyword.personalityinsightsshort}} <!--Personality Insights-->
* {{site.data.keyword.mobilepush}} <!--Push-->
* {{site.data.keyword.speechtotextshort}} <!-- Speech to Text-->
* {{site.data.keyword.streaminganalyticsshort}} <!--Streaming Analytics-->
* {{site.data.keyword.texttospeechshort}} <!--Text to Speech-->
* {{site.data.keyword.toneanalyzershort}} <!--Tone Analyzer-->
* {{site.data.keyword.weather_short}} <!--Weather Company Data-->
* {{site.data.keyword.workloadscheduler}} <!--Workload Scheduler-->

Um einer externen App oder einem Tool eines anderen Anbieters die Verwendung eines {{site.data.keyword.Bluemix_notm}}-Service zu ermöglichen, führen Sie die folgenden Schritte aus:

1. Erstellen Sie eine Instanz des Service.
    1. Klicken Sie auf **Katalog**.
    2. Wählen Sie im Katalog den gewünschten Service aus, indem Sie auf die Kachel für den Service klicken. 
    3. Wählen Sie den Standort, die Organisation und den Bereich oder die Ressourcengruppe aus und klicken Sie dann auf **Erstellen**.
2. Wählen Sie auf der Seite mit den Servicedetails die Option **Serviceberechtigungsnachweise** aus, um Berechtigungsnachweise im JSON-Format anzuzeigen oder hinzuzufügen. 
    * Wenn Sie neue Berechtigungsnachweise erstellen wollen, wählen Sie **Neuer Berechtigungsnachweis** aus und fügen Sie optional manuell Berechtigungsnachweise hinzu oder importieren Sie eine Datei in JSON-Format und klicken Sie anschließend auf **Hinzufügen**. Wählen Sie **Berechtigungsnachweise anzeigen** aus, um die Berechtigungsnachweis für die Verbindungsherstellung zu Ihrer externen App zu speichern.
    * Wenn die Berechtigungsnachweise bereits vorhanden sind, wählen Sie eine Gruppe von Berechtigungsnachweisen aus und klicken Sie in der Spalte 'Aktionen' auf **Berechtigungsnachweise anzeigen**. 
3. Verwenden Sie den angezeigten API-Schlüssel als Berechtigungsnachweise zur Herstellung einer Verbindung zu der Serviceinstanz.

Ihre Anwendung, die außerhalb von {{site.data.keyword.Bluemix_notm}} ausgeführt wird, kann nun auf den {{site.data.keyword.Bluemix_notm}}-Service zugreifen.

Wenn Sie Serviceinstanzen löschen oder die Rechnungsangaben überprüfen möchten, müssen Sie zu Ihrem Dashboard in der Benutzerschnittstelle zurückkehren, um die Serviceinstanzen zu verwalten.
{: tip}
