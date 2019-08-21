---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-03"

keywords: apps, services, add service, application, service, instance, ibmcloud dev edit, vcap_services, credentials

subcollection: creating-apps

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{:note: .note}

# Service zur App hinzufügen
{: #add-resource}

Wenn Sie eine App mithilfe der {{site.data.keyword.cloud}}-{{site.data.keyword.dev_console}} erstellen, können Sie Services von der Seite mit den App-Details hinzufügen. Sie können die Ressourcen auch direkt aus dem {{site.data.keyword.cloud_notm}}-Katalog hinzufügen, außerhalb des Kontexts Ihrer App.
{: shortdesc}

Sie können eine Instanz des Service anfordern und unabhängig von Ihrer App verwenden oder Sie können die Serviceinstanz von der Seite mit den App-Details Ihrer App hinzufügen. Sie können einen bestimmten Servicetyp direkt aus dem {{site.data.keyword.cloud_notm}}-Katalog bereitstellen.

## Automatisch bereitgestellte Services
{: #auto-provision}

Wenn ein Starter-Kit erforderliche Services angibt, erstellt {{site.data.keyword.cloud_notm}} automatisch Instanzen dieser Services, wenn Sie Ihre App erstellen. Sie können Services auch manuell erstellen oder vorhandene Serviceinstanzen auswählen, die Sie Ihrer App nach ihrer Erstellung hinzufügen. Auf der Seite mit **App-Details** können Sie eine Liste mit Serviceinstanzen anzeigen, die Ihrer App zugeordnet sind. Außerdem sind dort die Berechtigungsnachweise aufgeführt, für den Fall, dass Sie sie später noch benötigen.

## Services erkennen
{: #discover-resources}

Sie haben die folgenden Möglichkeiten, alle in {{site.data.keyword.cloud_notm}} verfügbaren Services anzuzeigen:

* Über die {{site.data.keyword.cloud_notm}}-Konsole. Zeigen Sie den {{site.data.keyword.cloud_notm}}-Katalog an.
* Über die Befehlszeile. Verwenden Sie hier den Befehl `ibmcloud service offerings`.
* Über Ihre eigene Anwendung. Verwenden Sie die [Services-API GET /v2/services ](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").

Zum Entwickeln einer App wählen Sie den benötigten Service aus. Sobald Sie ihn ausgewählt haben, stellt {{site.data.keyword.cloud_notm}} den Service bereit. Dieser Bereitstellungsprozess kann für die verschiedenen Servicetypen unterschiedlich ablaufen. Ein Datenbankservice richtet beispielsweise eine Datenbank ein, während ein Push-Benachrichtigungsservice für mobile Apps Konfigurationsinformationen erstellt.

{{site.data.keyword.cloud_notm}} stellt Ihrer App mittels einer Serviceinstanz die Ressourcen eines Service zur Verfügung. Eine Serviceinstanz kann von mehreren Web-Apps gemeinsam genutzt werden.

Sie können auch Services verwenden, die in anderen Regionen gehostet werden, sofern diese Services in diesen Regionen verfügbar sind. Diese Services müssen im Internet
zugänglich gemacht werden und müssen über API-Endpunkte verfügen. Sie müssen Ihre App für die Verwendung dieser Services manuell codieren, wie Sie auch externe Apps oder Tools von anderen Anbietern zur Verwendung von {{site.data.keyword.cloud_notm}}-Services codieren. Weitere Informationen finden Sie unter [Services mit externen Apps verbinden](/docs/resources?topic=resources-externalapp).

## Neue Serviceinstanz anfordern
{: #request-instance}

Um eine neue Serviceinstanz anzufordern, müssen Sie die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle oder die {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle verwenden.

Bei der Angabe des Servicenamens sollten Sie nur alphabetische oder numerische Zeichen verwenden, da es sonst zu unvorhersehbaren Ergebnissen kommen kann.
{: note}

Wenn Sie zum Anfordern einer Serviceinstanz die {{site.data.keyword.cloud_notm}}-Benutzerschnittstelle verwenden, führen Sie die folgenden Schritte durch:

1. Klicken Sie im {{site.data.keyword.cloud_notm}}-Katalog auf die Kachel für den Service, den Sie hinzufügen möchten. Die Seite mit den Servicedetails wird geöffnet.

2. Geben Sie in das Feld **Servicename** einen Namen ein. Es wird ein Standardname bereitgestellt. Sie können den Namen
in dem Feld ändern oder ihn unverändert übernehmen.

3. Füllen Sie ggf. weitere Felder aus bzw. treffen Sie weitere Auswahlen und klicken Sie
anschließend auf **Erstellen**.

Wenn Sie zum Anfordern einer Serviceinstanz die {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle verwenden, dann laden Sie Ihre App lokal herunter, öffnen Sie die Befehlszeile und wechseln Sie ins App-Verzeichnis.

1. Führen Sie den folgenden Befehl aus, um einen Service zu Ihrer App hinzuzufügen. Sie können einen vorhandenen Service aus den Services auswählen, die bereits für Ihr Konto aktiviert sind, oder einen neuen Service hinzufügen.

  ```bash
  ibmcloud dev edit
  ```
  {: pre}

2. Folgen Sie der Bedienerführung, um eine Ressourcengruppe auszuwählen und einen neuen datenbezogenen Service (z. B. Cloudant) für Ihre App zu erstellen und ihn mit dieser Anwendung zu verbinden. Möglicherweise müssen Sie eine Region auswählen und die erforderliche Planung für den Service durchführen.
3. Bei der Erstellung des Service werden verschiedene Dateien (einschließlich der zugehörigen Berechtigungsnachweise) zu Ihrem App-Verzeichnis hinzugefügt, um die Integration des Service in die App zu vereinfachen. Sie können die Dateien manuell zusammenführen oder diesen Schritt zurückstellen und später ausführen.

Sie können eine Serviceinstanz nur an die App-Instanzen binden, die sich in demselben Bereich bzw. in derselben Organisation befinden. Sie können allerdings Serviceinstanzen aus anderen Bereichen oder Organisationen auf dieselbe Weise wie eine externe App verwenden. Anstatt eine Bindung zu erstellen, verwenden Sie die Berechtigungsnachweise, um Ihre App-Instanz direkt zu konfigurieren. Weitere Informationen dazu, wie externe Apps {{site.data.keyword.cloud_notm}}-Services verwenden, finden Sie unter [Externe Apps für die Verwendung von {{site.data.keyword.cloud_notm}}-Services aktivieren](/docs/resources?topic=resources-externalapp#externalapp).

## App konfigurieren
{: #configure-app}

Nachdem Sie eine Serviceinstanz an Ihre App gebunden haben, müssen Sie Ihre App für die Interaktion mit dem Service konfigurieren.

Für die Kommunikation mit Apps kann unter Umständen jeder Service einen anderen Mechanismus erfordern. Wenn Sie Apps entwickeln, werden diese Mechanismen zu Informationszwecken als Teil der Servicedefinition dokumentiert. Aus Konsistenzgründen sind diese Mechanismen für die Interaktion Ihrer App mit dem Service erforderlich.

* Um mit Datenbankservice zu interagieren, verwenden Sie die Informationen, die {{site.data.keyword.cloud_notm}} zur Verfügung stellt, z. B. die Benutzer-ID, das Kennwort und den Zugriffs-URI für die App.
* Um mit mobilen Back-End-Services zu interagieren, verwenden Sie die Informationen, die {{site.data.keyword.cloud_notm}} zur Verfügung stellt, z. B. die App-Kennung (App-ID), die clientspezifischen Sicherheitsinformationen und den Zugriffs-URI für die App. Die mobilen Services arbeiten üblicherweise in Kontexten miteinander, sodass Kontextinformationen wie der Name des App-Entwicklers oder des Benutzers, der die App verwendet, in der gesamten Servicegruppe genutzt werden können.
* Für die Interaktion mit Web-Apps oder serverseitigem Cloud-Code für mobile Apps verwenden Sie die Informationen, die {{site.data.keyword.cloud_notm}} bereitstellt, wie z. B. die Laufzeitberechtigungsnachweise in der Umgebungsvariablen *VCAP_SERVICES* der App. Der Wert für die Umgebungsvariable *VCAP_SERVICES* ist die Serialisierung eines JSON-Objekts. Die Variable enthält die erforderlichen Laufzeitdaten für die Interaktion mit den Services, an die die App gebunden ist. Das Format der Daten ist für die verschiedenen Services unterschiedlich. Um zu erfahren, was Sie zu erwarten haben und wie die einzelnen Informationen einzuordnen sind, sollte möglicherweise die Servicedokumentation zu Rate gezogen werden.

Wenn ein Service, den Sie an eine App binden, ausfällt, wird die Ausführung der App möglicherweise gestoppt oder die Anwendung weist Fehler auf. {{site.data.keyword.cloud_notm}} führt keinen automatischen Neustart für die App durch, um die Probleme zu beheben. Sie sollten in Erwägung ziehen, Ihre App zu codieren, damit eine Erkennung der Fehler möglich ist und der Systembetrieb nach einer Störung, nach Ausnahmebedingungen oder Verbindungsfehlern wiederhergestellt werden kann.

## Über {{site.data.keyword.cloud_notm}}-Bereitstellungsumgebungen hinweg auf Services zugreifen
{: #migrate_instance}

{{site.data.keyword.cloud_notm}} bietet viele Bereitstellungsoptionen und Sie können in einer Umgebung auf einen Service, der in einer anderen Umgebung ausgeführt wird, zugreifen. Falls Sie über einen Service verfügen, der in Cloud Foundry ausgeführt wird, können Sie auf diesen Service von einer App aus zugreifen, die in einem Kubernetes-Cluster ausgeführt wird.

### Beispiel: Über einen Kubernetes-Pod auf einen Cloud Foundry-Service zugreifen

Für den Zugriff auf einen Cloud Foundry-Service über einen Pod in einem Kubernetes-Cluster müssen Sie den Service an den Cluster binden, damit die Serviceberechtigungsnachweise in einem geheimen Kubernetes-Schlüssel gespeichert werden können. Dann können Sie diese Informationen für Ihre App verfügbar machen. 
{: shortdesc}

Serviceberechtigungsnachweise, die in einem geheimen Kubernetes-Schlüssel gespeichert werden, verfügen standardmäßig über eine Base64-Codierung und sind mit ETCD verschlüsselt. 

**Wichtig**: Die Serviceberechtigungsnachweise dürfen nicht direkt in der YAML-Datei der Bereitstellung referenziert oder zugänglich gemacht werden. YAML-Dateien für Bereitstellungen sind nicht dafür vorgesehen, sensible Daten zu enthalten, und bieten keine standardmäßige Verschlüsselung Ihrer Serviceberechtigungsnachweise. Für das korrekte Speichern dieser Informationen und den korrekten Zugriff darauf müssen Sie einen geheimen Kubernetes-Schlüssel verwenden. 

1. [Service an den Cluster binden](/docs/containers?topic=containers-service-binding#bind-services). 
2. Wählen Sie für den Zugriff auf Ihre Serviceberechtigungsnachweise über den App-Pod eine der folgenden Optionen aus. 
   - Geheimen Schlüssel als Datenträger an den Pod anhängen
   - Geheimen Schlüssel in Umgebungsvariablen referenzieren

## Vom Benutzer zur Verfügung gestellte Serviceinstanz erstellen
{: #user_provide_services}

Sie verfügen möglicherweise über Services, die außerhalb von {{site.data.keyword.cloud_notm}} verwaltet werden. Wenn Sie über Berechtigungsnachweise für den Zugriff auf solche externen Services über das Internet verfügen, können Sie vom Benutzer zur Verfügung gestellte {{site.data.keyword.cloud_notm}}-Serviceinstanzen erstellen, die Ihre externen Services darstellen und die Kommunikation mit diesen Services ermöglichen.

Führen Sie die folgenden Schritte aus, um eine vom Benutzer zur Verfügung gestellte Serviceinstanz zu erstellen und an eine App zu binden:

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

2. Binden Sie die Serviceinstanz mit dem Befehl `ibmcloud service bind` an Ihre App. Beispiel:

	```
	ibmcloud service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

Sie können Ihre App nun für die Verwendung der externen Services konfigurieren. Informationen zum Konfigurieren Ihrer App für die Interaktion mit einem Service finden Sie im Abschnitt [App konfigurieren](/docs/apps?topic=creating-apps-add-resource#configure-app).
