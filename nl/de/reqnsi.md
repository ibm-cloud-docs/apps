---

copyright:
  years: 2015, 2018
lastupdated: "2018-09-07"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}

# Service zur App hinzufügen
{: #add_service}

Wenn Sie eine App mithilfe der {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.dev_console}} erstellen, können Sie Ressourcen von der App-Übersichtsseite hinzufügen. Sie können die Ressourcen jedoch auch direkt aus dem {{site.data.keyword.Bluemix_notm}}-Katalog hinzufügen, außerhalb des Kontexts Ihrer App.
{: shortdesc}

Sie können eine Instanz der Ressource anfordern und unabhängig von Ihrer App verwenden oder Sie können die Ressourceninstanz von der App-Übersichtseite zu Ihrer App hinzufügen. Sie können einen bestimmten Typ von Ressource (einen Service) direkt aus dem {{site.data.keyword.Bluemix_notm}}-Katalog bereitstellen.

## Services entdecken
{: #discover_services}

Sie haben die folgenden Möglichkeiten, alle in {{site.data.keyword.Bluemix_notm}} verfügbaren Services anzuzeigen:

* Über die {{site.data.keyword.Bluemix_notm}}-Konsole. Zeigen Sie den {{site.data.keyword.Bluemix_notm}}-Katalog an.
* Über die Befehlszeilenschnittstelle 'ibmcloud'. Verwenden Sie hier den Befehl `ibmcloud service offerings`.
* Über Ihre eigene Anwendung. Verwenden Sie die [Services-API GET /v2/services ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window}.

Zum Entwickeln einer Anwendung wählen Sie den benötigten Service aus. Sobald Sie ihn ausgewählt haben, stellt {{site.data.keyword.Bluemix_notm}} den Service bereit. Dieser Bereitstellungsprozess kann für die verschiedenen Servicetypen unterschiedlich ablaufen. Ein Datenbankservice richtet beispielsweise eine Datenbank ein, während ein Push-Benachrichtigungsservice für mobile Anwendungen Konfigurationsinformationen erstellt.

{{site.data.keyword.Bluemix_notm}} stellt Ihrer Anwendung mittels einer Serviceinstanz die Ressourcen eines Service zur Verfügung. Eine Serviceinstanz kann von mehreren Webanwendungen gemeinsam
genutzt werden.

Sie können auch Services verwenden, die in anderen Regionen gehostet werden, sofern diese Services in diesen Regionen verfügbar sind. Diese Services müssen im Internet
zugänglich gemacht werden und müssen über API-Endpunkte verfügen. Sie müssen Ihre Anwendung für die Verwendung dieser
Services manuell codieren, wie Sie auch externe Anwendungen oder Tools von anderen Anbietern
zur Verwendung von {{site.data.keyword.Bluemix_notm}}-Services codieren. Weitere Informationen finden Sie in [Externen Anwendungen und Tools von anderen Anbietern die Verwendung von {{site.data.keyword.Bluemix_notm}}-Services ermöglichen](#accser_external).

## Neue Serviceinstanz anfordern
{: #req_instance}

Um eine neue Serviceinstanz anzufordern, müssen Sie die {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle oder die {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle verwenden.

**Hinweis:** Bei der Angabe des Servicenamens sollten Sie nur alphabetische oder numerische Zeichen verwenden, da es sonst zu unvorhersehbaren Ergebnissen kommen kann.

Wenn Sie zum Anfordern einer Serviceinstanz die {{site.data.keyword.Bluemix_notm}}-Benutzerschnittstelle verwenden, führen Sie die folgenden Schritte durch:

1. Klicken Sie im {{site.data.keyword.Bluemix_notm}}-Katalog auf die Kachel für den Service, den Sie hinzufügen möchten. Die Seite mit den Servicedetails wird geöffnet.

2. Geben Sie in das Feld **Servicename** einen Namen ein. Es wird ein Standardname bereitgestellt. Sie können den Namen
in dem Feld ändern oder ihn unverändert übernehmen.

3. Füllen Sie ggf. weitere Felder aus bzw. treffen Sie weitere Auswahlen und klicken Sie
anschließend auf **Erstellen**.

Wenn Sie zum Anfordern einer Serviceinstanz die {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle verwenden, dann laden Sie Ihre App lokal herunter, öffnen Sie die Befehlszeile und wechseln Sie ins App-Verzeichnis.

1. Führen Sie den folgenden Befehl aus, um einen Service zu Ihrer App hinzuzufügen. Sie können einen vorhandenen Service aus den Services auswählen, die bereits für Ihr Konto aktiviert sind, oder einen neuen Service hinzufügen.

  ```bash
  ibmcloud dev edit
  ```
  {: pre}

2. Folgen Sie der Bedienerführung, um eine Ressourcengruppe auszuwählen und einen neuen datenbezogenen Service (z. B. Cloudant) für Ihre Anwendung zu erstellen und ihn mit dieser Anwendung zu verbinden. Möglicherweise müssen Sie eine Region auswählen und die erforderliche Planung für den Service durchführen.
3. Bei der Erstellung des Service werden verschiedene Dateien (einschließlich der zugehörigen Berechtigungsnachweise) zu Ihrem Anwendungsverzeichnis hinzugefügt, um die Integration des Service in die Anwendung zu vereinfachen. Sie können die Dateien manuell zusammenführen oder diesen Schritt zurückstellen und später ausführen.

Sie können eine Serviceinstanz nur an die App-Instanzen binden, die sich in demselben Bereich bzw. in derselben Organisation befinden. Sie können allerdings Serviceinstanzen aus anderen Bereichen oder Organisationen auf dieselbe Weise wie eine externe App verwenden. Anstatt eine Bindung zu erstellen, verwenden Sie die Berechtigungsnachweise, um Ihre App-Instanz direkt zu konfigurieren. Weitere Informationen dazu, wie externe Apps {{site.data.keyword.Bluemix_notm}}-Services verwenden, finden Sie unter [Externen Apps die Verwendung von {{site.data.keyword.Bluemix_notm}}-Services ermöglichen ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](#accser_external){: new_window}.

## Anwendung konfigurieren
{: #config}

Nachdem Sie eine Serviceinstanz an Ihre Anwendung gebunden haben, müssen Sie Ihre Anwendung für die Interaktion mit dem Service konfigurieren.

Für die Kommunikation mit Anwendungen kann unter Umständen jeder Service einen anderen Mechanismus erfordern. Wenn Sie Anwendungen entwickeln, werden diese Mechanismen zu Informationszwecken als Teil der Servicedefinition dokumentiert. Aus Konsistenzgründen sind diese Mechanismen für die Interaktion Ihrer Anwendung mit dem Service erforderlich.

* Um mit Datenbankservice zu interagieren, verwenden Sie die Informationen, die {{site.data.keyword.Bluemix_notm}} zur Verfügung stellt, z. B. die Benutzer-ID, das Kennwort und den Zugriffs-URI für die Anwendung.
* Um mit mobilen Back-End-Services zu interagieren, verwenden Sie die Informationen, die {{site.data.keyword.Bluemix_notm}} zur Verfügung stellt, z. B. die Anwendungskennung (app ID), die clientspezifischen Sicherheitsinformationen und den Zugriffs-URI für die Anwendung. Die mobilen Services arbeiten üblicherweise in Kontexten miteinander, sodass Kontextinformationen wie der Name des Anwendungsentwicklers oder des Benutzers, der die Anwendung verwendet, in der gesamten Servicegruppe genutzt werden können.
* Für die Interaktion mit Webanwendungen oder serverseitigem Cloud-Code für mobile Anwendungen verwenden Sie die Informationen, die {{site.data.keyword.Bluemix_notm}} bereitstellt, wie z. B. die Laufzeitberechtigungsnachweise in der Umgebungsvariablen *VCAP_SERVICES* der Anwendung. Der Wert für die Umgebungsvariable *VCAP_SERVICES* ist die Serialisierung eines JSON-Objekts. Die Variable enthält die erforderlichen Laufzeitdaten für die Interaktion mit den Services, an die die Anwendung gebunden ist. Das Format der Daten ist für die verschiedenen Services unterschiedlich. Um zu erfahren, was Sie zu erwarten haben und wie die einzelnen Informationen einzuordnen sind, sollte möglicherweise die Servicedokumentation zu Rate gezogen werden.

Wenn ein Service, den Sie an eine Anwendung binden, ausfällt, wird die Ausführung der Anwendung möglicherweise gestoppt oder die Anwendung weist Fehler auf. {{site.data.keyword.Bluemix_notm}} führt keinen automatischen Neustart für die Anwendung durch, um die Probleme zu beheben. Sie sollten in Erwägung ziehen, Ihre Anwendung zu codieren, damit eine Erkennung der Fehler möglich ist und der Systembetrieb nach einer Störung, nach Ausnahmebedingungen oder Verbindungsfehlern wiederhergestellt werden kann. Weitere Informationen finden Sie unter [Apps werden nicht automatisch erneut gestartet](/docs/troubleshoot/ts_apps.html#ts_apps_not_auto_restarted).

## Über {{site.data.keyword.Bluemix_notm}}-Bereitstellungsumgebungen hinweg auf Services zugreifen
{: #migrate_instance}

{{site.data.keyword.Bluemix_notm}} bietet viele Bereitstellungsoptionen und Sie können in einer Umgebung auf einen Service, der in einer anderen Umgebung ausgeführt wird, zugreifen. Falls Sie über einen Service verfügen, der in Cloud Foundry ausgeführt wird, können Sie auf diesen Service von einer Anwendung aus zugreifen, die in einem Kubernetes-Cluster ausgeführt wird.

### Beispiel: Über einen Kubernetes-Pod auf einen Cloud Foundry-Service zugreifen

Für den Zugriff auf einen Cloud Foundry-Service über einen Pod in einem Kubernetes-Cluster müssen Sie den Service an den Cluster binden, damit die Serviceberechtigungsnachweise in einem geheimen Kubernetes-Schlüssel gespeichert werden können. Dann können Sie diese Informationen für Ihre App verfügbar machen. 
{: shortdesc}

Serviceberechtigungsnachweise, die in einem geheimen Kubernetes-Schlüssel gespeichert werden, verfügen standardmäßig über eine Base64-Codierung und sind mit ETCD verschlüsselt. 

**Wichtig**: Die Serviceberechtigungsnachweise dürfen nicht direkt in der YAML-Datei der Bereitstellung referenziert oder zugänglich gemacht werden. YAML-Dateien für Bereitstellungen sind nicht dafür vorgesehen, sensible Daten zu enthalten, und bieten keine standardmäßige Verschlüsselung Ihrer Serviceberechtigungsnachweise. Für das korrekte Speichern dieser Informationen und den korrekten Zugriff darauf müssen Sie einen geheimen Kubernetes-Schlüssel verwenden. 

1. [Service an den Cluster binden](/docs/containers/cs_integrations.html#adding_cluster). 
2. Wählen Sie für den Zugriff auf Ihre Serviceberechtigungsnachweise über den App-Pod eine der folgenden Optionen aus. 
   - [Geheimen Schlüssel als Datenträger an den Pod anhängen](#mount_secret)
   - [Geheimen Schlüssel in Umgebungsvariablen referenzieren](#reference_secret)

## Externe Apps aktivieren
{: #accser_external}

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

Um einer externen App oder einem Tool eines anderen Anbieters die Verwendung eines {{site.data.keyword.Bluemix_notm}}-Service zu ermöglichen, führen Sie die folgenden Schritte durch:

1. Fordern Sie eine Instanz des Service an.
    1. Klicken Sie auf dem Dashboard in der Benutzerschnittstelle von {{site.data.keyword.Bluemix_notm}} auf **Ressource erstellen**. Daraufhin wird der Katalog angezeigt.
    2. Wählen Sie im Katalog den gewünschten Service aus, indem Sie auf die Kachel für den Service klicken. Die Seite mit den Servicedetails wird geöffnet.
    3. Lassen Sie im Servicefenster für die Liste **Verbindung herstellen zu:** den Standardwert **Nicht binden** ausgewählt. Diese Auswahl bedeutet, dass keine Verbindung zwischen dem Service und einer {{site.data.keyword.Bluemix_notm}}-App hergestellt wird.
    4. Wählen Sie die anderen Optionen je nach Bedarf entsprechend aus. Klicken Sie anschließend auf **Erstellen**. Es wird eine Serviceinstanz erstellt und das Service-Dashboard wird angezeigt.
2. Im Service-Dashboard können Sie die Option **Serviceberechtigungsnachweise** auswählen, um Berechtigungsnachweise im JSON-Format anzuzeigen oder hinzuzufügen. Wählen Sie eine Reihe von Berechtigungsnachweisen aus und klicken Sie in der Spalte 'Aktionen' auf **Berechtigungsnachweise anzeigen**. Verwenden Sie den angezeigten API-Schlüssel als Berechtigungsnachweise zur Herstellung einer Verbindung zu der Serviceinstanz.

Ihre Anwendung, die außerhalb von {{site.data.keyword.Bluemix_notm}} ausgeführt wird, kann nun auf den {{site.data.keyword.Bluemix_notm}}-Service zugreifen.

**Hinweis:** Wenn Sie Serviceinstanzen löschen oder die Rechnungsangaben überprüfen möchten, müssen Sie zu Ihrem Dashboard in der Benutzerschnittstelle zurückkehren, um die Serviceinstanzen zu verwalten.

## Vom Benutzer zur Verfügung gestellte Serviceinstanz erstellen
{: #user_provide_services}

Sie verfügen möglicherweise über Services, die außerhalb von {{site.data.keyword.Bluemix_notm}} verwaltet werden. Wenn Sie über Berechtigungsnachweise für den Zugriff auf solche externen Services über das Internet verfügen, können Sie vom Benutzer zur Verfügung gestellte {{site.data.keyword.Bluemix_notm}}-Serviceinstanzen erstellen, die Ihre externen Services darstellen und die Kommunikation mit diesen Services ermöglichen.

Führen Sie die folgenden Schritte aus, um eine vom Benutzer zur Verfügung gestellte Serviceinstanz zu erstellen und an eine Anwendung zu binden:

1. Erstellen Sie eine vom Benutzer zur Verfügung gestellte Serviceinstanz, indem Sie den Befehl `ibmcloud service user-provided-create` verwenden:
    * Verwenden Sie zum Erstellen einer allgemeinen, vom Benutzer zur Verfügung gestellten Serviceinstanz die Option **-p** und trennen Sie die Parameternamen durch Kommas. Die `ibmcloud`-Befehlszeilenschnittstelle fordert Sie dann nacheinander zum Angeben der einzelnen Parameter auf. Beispiel:
        ```
        ibmcloud service user-provided-create testups1 -p "host, port, dbname, username, password"
        host> pubsub01.example.com
        port> 1234
        dbname> sampledb01
        username> pubsubuser
        password> p@$$w0rd
        Creating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * Um eine Serviceinstanz zu erstellen, die Informationen an eine Protokoll-Management-Software eines anderen Anbieters weitergibt, verwenden Sie die Option `-l`. Geben Sie das Ziel an, das von der Protokollmanagementsoftware des anderen Anbieters bereitgestellt wird. Beispiel:

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example.com
        Creating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

    Wenn Sie einen oder mehrere Parameter der vom Benutzer zur Verfügung gestellten Serviceinstanz aktualisieren möchten, verwenden Sie den Befehl `ibmcloud service user-provided-update`.

    * Verwenden Sie zum Aktualisieren einer allgemeinen, vom Benutzer zur Verfügung gestellten Serviceinstanz die Option **-p** und geben Sie die Parameterschlüssel und -werte in einem JSON-Objekt an. Beispiel:

        ```
        ibmcloud service user-provided-update testups1 -p "{\"username\":\"pubsubuser2\",\"password\":\"p@$$w0rd2\"}"
        Updating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * Um eine Serviceinstanz zu erstellen, die Informationen an eine Protokoll-Management-Software eines anderen Anbieters weitergibt, verwenden Sie die Option `-l`. Beispiel:

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example2.com
        Updating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

2. Binden Sie die Serviceinstanz mit dem Befehl `ibmcloud service bind` an Ihre Anwendung. Beispiel:

	```
	ibmcloud service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

Sie können Ihre Anwendung nun für die Verwendung der externen Services konfigurieren. Informationen zum Konfigurieren Ihrer Anwendung für die Interaktion mit einem Service finden Sie unter [Anwendung für die Interaktion mit einem Service konfigurieren![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](#config){: new_window}.
