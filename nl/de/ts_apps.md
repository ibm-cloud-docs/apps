---

copyright:

  years: 2015, 2018

lastupdated: "2018-07-02"

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}

# Fehlerbehebung für die Verwaltung von Apps
{: #managingapps}

Allgemeine Probleme im Zusammenhang mit der Verwaltung von Apps können sein, dass Apps nicht aktualisiert werden können oder Doppelbytezeichen nicht angezeigt werden. In vielen Fällen können Sie diese Probleme durch Ausführen weniger einfacher Schritte beheben.
{:shortdesc}

## Es sind nicht gespeicherte Änderungen vorhanden
{: #ts_unsaved_changes}

Wenn Sie zur Detailseite der App navigieren, können Sie möglicherweise keine Aktionen ausführen und werden aufgefordert, Änderungen zu speichern, bevor Sie fortfahren.

Wenn Sie versuchen, Ihre App oder Services auf der Detailseite der App zu prüfen, empfangen Sie immer wieder die folgende Fehlernachricht:
{: tsSymptoms}

`Es gibt nicht gespeicherte Änderungen auf Seite 'Name der App'. Speichern oder verwerfen Sie die Änderungen.`

Wenn Sie Ihre Maus über das Feld **INSTANCES** (Instanzen) oder **MEMORY QUOTA** (Speicherkontingent) im Teilfenster für die Laufzeit bewegen, ändern sich die Werte. Dieses Verhalten ist wie vorgesehen. Allerdings werden Sie von der Fehlernachricht aufgefordert, die Speicher- oder Instanzeinstellungen zu speichern, bevor Sie von der Seite wegnavigieren.
{: tsCauses}

Schließen Sie das Nachrichtenfenster und klicken Sie danach im Teilfenster für Ihre Laufzeitumgebung auf **ZURÜCKSETZEN**.
{: tsResolve}

## Automatische Funktionsübernahme zwischen {{site.data.keyword.Bluemix_notm}}-Regionen nicht verfügbar
{: #ts_failover}

Die automatische Funktionsübernahme zwischen {{site.data.keyword.Bluemix_notm}}-Regionen kann nicht verwendet werden. Sie können allerdings einen DNS-Anbieter nutzen, der eine Funktionsübernahme zwischen mehreren IP-Adressen als Ausweichlösung unterstützt.

Wenn eine {{site.data.keyword.Bluemix_notm}}-Region nicht mehr verfügbar ist, sind auch die Apps, die in dieser Region ausgeführt werden, nicht mehr verfügbar, selbst dann nicht, wenn dieselben Apps in einer anderen {{site.data.keyword.Bluemix_notm}}-Region ausgeführt werden.
{: tsSymptoms}

{{site.data.keyword.Bluemix_notm}} bietet noch keine automatische Funktionsübernahme zwischen zwei Regionen an.
{: tsCauses}

Sie können einen DNS-Anbieter nutzen, der eine intelligente Funktionsübernahme zwischen einer Vielzahl von ID-Adressen unterstützt, und Ihre DNS-Einstellungen zur Aktivierung der automatischen Funktionsübernahme zwischen {{site.data.keyword.Bluemix_notm}}-Regionen manuell konfigurieren. DNS-Anbieter mit dieser Funktion sind z. B. NSONE, Akamai, Dyn.
{: tsResolve}

Wenn Sie Ihre DNS-Einstellungen konfigurieren, müssen Sie die öffentlichen IP-Adressen der {{site.data.keyword.Bluemix_notm}}-Regionen angeben, in denen Ihre Apps ausgeführt werden. Verwenden Sie zum Abrufen der öffentlichen IP-Adresse einer {{site.data.keyword.Bluemix_notm}}-Region den Befehl `nslookup`. Sie können in einem Befehlszeilenfenster beispielsweise den nachfolgenden Befehl eingeben. 

```
nslookup stage1.mybluemix.net
```

## Apps können nicht in den Debugmodus versetzt werden
{: #ts_debug}

Möglicherweise können Sie den Debugmodus nicht aktivieren, wenn die JVM-Version (JVM = Java Virtual Machine) 8 oder eine frühere Version verwendet wird. 

Wenn Sie die Option zum Aktivieren des Anwendungsdebuggings (**Enable application debug**) auswählen, versuchen die Tools, die App in den Debugmodus zu versetzen. Daraufhin startet die Eclipse-Workbench eine Debugsitzung. Wenn die Tools den Debugmodus erfolgreich aktivieren können, wird als Status für die Webanwendung `Updating mode` (Aktualisierungsmodus), `Developing` (Entwicklung) und `Debugging` (Fehlerbehebung) angezeigt.
{: tsSymptoms}

Wenn die Tools den Debugmodus jedoch nicht aktivieren können, wird als Status für die Webanwendung lediglich `Updating mode` (Aktualisierungsmodus) und `Developing` (Entwicklung) ohne die Angabe `Debugging` (Fehlerbehebung) angezeigt. Außerdem zeigen die Tools möglicherweise die folgende Fehlernachricht in der Konsolenansicht an:

```
bluemixMgmgClient - ???? [pool-1-thread-1] .... ERROR --- ClientProxyImpl: Cannot create the websocket connections for MyWebProj
com.ibm.ws.cloudoe.management.client.exception.ApplicationManagementException: javax.websocket.DeploymentException: The HTTP request to initiate the  WebSocket connection failed
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl.onNewClientSocket(ClientProxyImpl.java:161)
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl$RunServerTask.run(ClientProxyImpl.java:267)
at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:522)
at java.util.concurrent.FutureTask.run(FutureTask.java:277)
at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1153)
at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
at java.lang.Thread.run(Thread.java:785)
Caused by: javax.websocket.DeploymentException: The HTTP request to initiate the WebSocket connection failed
at  org.apache.tomcat.websocket.WsWebSocketContainer.connectToServer(WsWebSocketContainer.java:315)
at  com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl.onNewClientSocket(ClientProxyImpl.java:158)
... 6 more
Caused by: java.util.concurrent.TimeoutException
at org.apache.tomcat.websocket.AsyncChannelWrapperSecure$WrapperFuture.get(AsyncChannelWrapperSecure.java:505)
at org.apache.tomcat.websocket.WsWebSocketContainer.processResponse(WsWebSocketContainer.java:542)
at org.apache.tomcat.websocket.WsWebSocketContainer.connectToServer(WsWebSocketContainer.java:296)
... 7 more
[2016-01-15 13:33:51.075] bluemixMgmgClient - ????  [pool-1-thread-1] .... ERROR --- ClientProxyImpl: Cannot create the  websocket connections for MyWebProj
com.ibm.ws.cloudoe.management.client.exception.ApplicationManagementException: javax.websocket.DeploymentException: The HTTP request to initiate the  WebSocket connection failed
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl.onNewClientSocket(ClientProxyImpl.java:161)
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl$RunServerTask.run(ClientProxyImpl.java:267)
at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:522)
at java.util.concurrent.FutureTask.run(FutureTask.java:277)
at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1153)
at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:628)
at java.lang.Thread.run(Thread.java:785)
Caused by: javax.websocket.DeploymentException: The HTTP request to initiate the WebSocket connection failed
at org.apache.tomcat.websocket.WsWebSocketContainer.connectToServer(WsWebSocketContainer.java:315)
at com.ibm.ws.cloudoe.management.client.impl.ClientProxyImpl.onNewClientSocket(ClientProxyImpl.java:158)
... 6 more
Caused by: java.util.concurrent.TimeoutException
at org.apache.tomcat.websocket.AsyncChannelWrapperSecure$WrapperFuture.get(AsyncChannelWrapperSecure.java:505)
at org.apache.tomcat.websocket.WsWebSocketContainer.processResponse(WsWebSocketContainer.java:542)
at org.apache.tomcat.websocket.WsWebSocketContainer.connectToServer(WsWebSocketContainer.java:296)
... 7 more
```

Die folgenden JVM-Versionen (JVM = Java Virtual Machine) können keine Debugsitzung erstellen: IBM JVM 7, IBM JVM 8 sowie frühere Versionen als Oracle JVM 8.
{: tsCauses}

Wenn Ihre Workbench eine dieser JVM-Versionen verwendet, treten möglicherweise Probleme beim Erstellen einer Debugsitzung auf. Ihre Workbench verwendet in der Regel dieselbe JVM-Version, die auf Ihrem lokalen Computer als System-JVM installiert ist. Ihre System-JVM ist nicht identisch mit der JVM Ihrer aktiven {{site.data.keyword.Bluemix_notm}}-Java&trade;-Anwendung. Die {{site.data.keyword.Bluemix_notm}}-Java-Anwendung wird fast immer unter IBM JVM und in manchen Fällen unter OpenJDK JVM ausgeführt.

Führen Sie die folgenden Schritte aus, um zu überprüfen, welche Java-Version von {{site.data.keyword.eclipsetoolsfull}} verwendet wird:
{: tsResolve}

  1. Wählen Sie in IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} **Hilfe** > **Informationen zu Eclipse** > **Installationsdetails** > **Konfiguration** aus.
  2. Suchen Sie in der Liste die Eigenschaft `eclipse.vm`. Die folgende Zeile enthält ein Beispiel für die Eigenschaft `eclipse.vm`:

	```
	eclipse.vm=C:\Programme\IBM\ibm-java-sdk-80-win-x86_64\bin\..\jre\bin\j9vm\jvm.dll
	```

  3. Geben Sie in der Befehlszeile `java -version` im Verzeichnis `bin` Ihrer Java-Installation ein. Die Informationen zu Ihrer IBM JVM-Version werden angezeigt.

Wenn Ihre Workbench IBM JVM 7 oder 8 verwendet bzw. eine frühere Version als Oracle JVM 8, führen Sie die folgenden Schritte aus, um zu Oracle JVM 8 zu wechseln:

  1. Laden Sie Oracle JVM 8 herunter und installieren Sie es (Details hierzu finden Sie unter [Java SE Downloads ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://www.oracle.com/technetwork/java/javase/downloads/index.html){: new_window}.
  2. Starten Sie Eclipse erneut.
  3. Überprüfen Sie, ob die Eigenschaft `eclipse.vm` auf Ihre neue Oracle JVM 8-Installation verweist.


## Wiederverwendung von Namen gelöschter Apps nicht möglich
{: #ts_reuse_appname}

Nach dem Löschen einer App kann der App-Name erst nach dem Löschen der App-Route wiederverwendet werden.

Bei der Wiederverwendung des App-Namens wird die folgende Nachricht angezeigt:
{: tsSymptoms}

`The name is already used by another app.` (Der Name wird bereits von einer anderen App verwendet.)

Beim Löschen einer App wird die zugehörige Route (URL für die App) nicht automatisch gelöscht. Deshalb kann sie nicht wiederverwendet werden. Sie müssen den Bereich aufrufen, in dem die App erstellt wurde, um die Route zu löschen.
{: tsCauses}

Führen Sie die folgenden Schritte aus, um die nicht verwendete Route zu löschen:
{: tsResolve}

  1. Stellen Sie fest, ob die Route zum aktuellen Bereich gehört. Geben Sie dazu den folgenden Befehl ein:

    ```
    cf routes
    ```

  2. Wenn die Route nicht zum aktuellen Bereich gehört, wechseln Sie in den betreffenden Bereich oder in die betreffende Organisation. Geben Sie dazu den folgenden Befehl ein:

    ```
    cf target -o org_name -s space_name
    ```

  3. Löschen Sie die App-Route, indem Sie den folgenden Befehl eingeben:

    ```
    cf delete-route domain_name -n host_name
    ```

  Beispiel:

  ```
  cf delete-route mybluemix.net -n app001
  ```

## Abrufen von Bereichen in Organisation nicht möglich
{: #ts_retrieve_space}

Sie können eine App oder einen Service nicht erstellen, wenn der derzeitigen Organisation kein Bereich zugeordnet ist.

Bei dem Versuch, in {{site.data.keyword.Bluemix_notm}} eine App zu erstellen, wird die folgende Fehlernachricht angezeigt:
{: tsSymptoms}

`BXNUI0515E: Die Bereiche in der Organisation wurden nicht abgerufen. Es ist entweder ein Netzverbindungsproblem aufgetreten oder Ihrer aktuellen Organisation ist kein Bereich zugeordnet.`

Dieser Fehler tritt oft auf, wenn Sie zum ersten Mal versuchen, im Katalog eine App oder einen Service zu erstellen, wenn noch kein Bereich erstellt wurde.
{: tsCauses}

Stellen Sie sicher, dass Sie in der derzeitigen Organisation einen Bereich erstellt haben. Verwenden Sie eine der folgenden Methoden, um einen Bereich zu erstellen:
{: tsResolve}

* Klicken Sie in der Menüleiste auf **Verwalten > Konto > Organisationen**. Wählen Sie die Organisation aus, in der der Bereich erstellt werden soll, und klicken Sie auf **Bereich erstellen**.
* Geben Sie in der Befehlszeilenschnittstelle `cf` Folgendes ein: `cf create-space <space_name> -o <organization_name>`.

Wiederholen Sie den Vorgang. Wenn diese Nachricht erneut angezeigt wird, rufen Sie die Seite für den [{{site.data.keyword.Bluemix_notm}}-Status ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://ibm.biz/bluemixstatus){: new_window} auf, um zu prüfen, ob ein Problem für einen Service oder eine Komponente vorliegt.

## Angeforderte Aktionen konnten nicht ausgeführt werden
{: #ts_authority}

Sie können Aktionen nur ausführen, wenn Sie über die entsprechende Zugriffsberechtigung verfügen. 

Wenn Sie versuchen, Aktionen für eine Serviceinstanz oder eine App-Instanz auszuführen, können Sie die angeforderten Aktionen nicht abschließen und es wird eine der folgenden Fehlernachrichten angezeigt:
{: tsSymptoms}

`BXNUI0514E: Sie sind kein Entwickler für die Bereiche in der Organisation <orgName>Organisationsname`.

`Serverfehler, Statuscode: 403, Fehlercode: 10003, Nachricht: Sie sind nicht berechtigt, die angeforderte Aktion auszuführen.`

Sie verfügen nicht über die entsprechende Berechtigungsebene zum Ausführen der Aktionen.
{: tsCauses}

Verwenden Sie zum Abrufen der erforderlichen Berechtigungsebene eine der nachfolgenden Methoden.
{: tsResolve}

* Wählen Sie eine andere Organisation und einen anderen Bereich aus, für die bzw. den Sie die Rolle des Entwicklers ausfüllen.
* Bitten Sie den Manager der Organisation, Ihre Rolle in die eines Entwicklers zu ändern oder einen Bereich zu erstellen und Ihnen dann eine Entwicklerrolle zuzuweisen. Informationen hierzu finden Sie unter [Organisationen und Bereiche verwalten](/docs/admin/orgs_spaces.html).

## Auf {{site.data.keyword.Bluemix_notm}}-Services kann aufgrund von Berechtigungsfehlern nicht zugegriffen werden
{: #ts_vcap}

Berechtigungsfehler können auftreten, wenn Ihre App auf einen {{site.data.keyword.Bluemix_notm}}-Service zugreift und die Serviceberechtigungen in Ihrer App fest codiert sind.

Nachdem Sie Ihre App für die Kommunikation mit einem {{site.data.keyword.Bluemix_notm}}-Service konfiguriert haben, stellen Sie sie in {{site.data.keyword.Bluemix_notm}} bereit. Sie können die App jedoch nicht für den Zugriff auf den {{site.data.keyword.Bluemix_notm}}-Service verwenden und empfangen einen Berechtigungsfehler.
{: tsSymptoms}

Die fest codierten Berechtigungsnachweise in der App sind möglicherweise nicht korrekt. Jedes Mal, wenn der Service erneut erstellt wird, ändern sich die Berechtigungsnachweise für den Zugriff darauf.
{: tsCauses}

Statt die Berechtigungsnachweise in Ihrer App fest zu codieren, verwenden Sie Verbindungsparameter aus der Umgebungsvariablen VCAP_SERVICES. Die Methoden für die Verwendung von Verbindungsparametern aus der Umgebungsvariablen VCAP_SERVICES variieren abhängig von den Programmsprachen. Für Node.js-Apps können Sie beispielsweise den folgenden Befehl verwenden:
{: tsResolve}

```
process.env.VCAP_SERVICES
```
Weitere Informationen zu den Befehlen, die Sie in anderen Programmsprachen verwenden können, finden Sie in den Tipps für [Java ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} und für [Ruby ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window}.


## Bereitstellung von Apps mit IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} nicht möglich
{: #ts_bm_tools_facet}

Wird eine nicht unterstützte Facette auf Ihr Eclipse-Projekt angewendet, können Sie Ihre Apps möglicherweise nicht mithilfe von IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} in {{site.data.keyword.Bluemix_notm}} bereitstellen.

Mit der Cloud Foundry-Befehlszeilenschnittstelle können Sie Ihre App erfolgreich in {{site.data.keyword.Bluemix_notm}} bereitstellen. Allerdings ist es nicht möglich, die App mit IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} in {{site.data.keyword.Bluemix_notm}} bereitzustellen, und es wird die folgende Fehlernachricht angezeigt: `Project facet <facet_name> is not supported.` (Projektfacette 'facettenname' wird nicht unterstützt.) Beispiel:
{: tsSymptoms}
`Project facet Cloud Foundry Standalone Application version 1.0 is not supported.` (Projektfacette Cloud Foundry Standalone Application Version 1 wird nicht unterstützt.)

IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} ordnet Projekte {{site.data.keyword.Bluemix_notm}}-Laufzeiten zu, und zwar durch Projektfacetten. Facetten definieren die Voraussetzungen für Java EE-Projekte in Eclipse und werden im Rahmen der Laufzeitkonfiguration genutzt, sodass unterschiedliche Laufzeiten unterschiedlichen Projekten zugeordnet werden. Wird die auf das Projekt angewendete Facette nicht von IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} unterstützt, können Sie Ihre App nicht mit IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} bereitstellen.
{: tsCauses}

Sie müssen die Facette aus dem Eclipse-Projekt entfernen, damit Sie Ihre App mit IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} bereitstellen können.
{: tsResolve}

Um die Facette zu entfernen, klicken Sie für das Projekt in IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} auf **Projekt > Eigenschaften > Projektfacetten**. Nehmen Sie anschließend die Markierung des Kontrollkästchens für die nicht unterstützte Facette zurück.

## Fehler des Typs '502 Bad Gateway' empfangen
{: #ts_502_error}

Wenn Sie bei der Interaktion mit Apps unter {{site.data.keyword.Bluemix_notm}} Fehler vom Typ '502 Bad Gateway' erhalten, überprüfen Sie die Seite für die {{site.data.keyword.Bluemix_notm}}-Status und führen Sie anschließend die entsprechenden Aktionen durch. 

Sie erhalten Fehlernachrichten, die mit '502 Bad Gateway' beginnen. So wird beispielsweise die Fehlernachricht `502 Bad Gateway: Registered endpoint failed to handle the request` (502 Bad Gateway: Verarbeitung der Anfrage durch registrierten Endpunkt fehlgeschlagen) angezeigt.
{: tsSymptoms}

Zu einem Fehler des Typs 'Bad Gateway' kommt es in der Regel, wenn Sie eine Website besuchen, bei der zum Speichern und Vermitteln der Daten aus dem Hauptserver, der die Site hostet, ein Proxy-Server verwendet wird. Der Hauptserver und der Proxy-Server sind möglicherweise nicht ordnungsgemäß miteinander verbunden. In diesem Fall wird der HTTP-Statuscode 502 im Browserfenster angezeigt. Dieser Statuscode weist darauf hin, dass der Hauptserver der Site die HTTP-Implementierung, die vom Proxy-Server erwartet wird, nicht erhalten hat.
{: tsCauses}

Andere, weniger häufige Ursachen eines Fehlers vom Typ 'Bad Gateway' sind Ausfälle des Internet-Service-Providers, falsche Firewallkonfigurationen und Fehler des Browser-Cache.

Wenn Sie vermuten, dass ein {{site.data.keyword.Bluemix_notm}}-Service inaktiv ist, überprüfen Sie zunächst die Seite für den [{{site.data.keyword.Bluemix_notm}}-Status ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://ibm.biz/bluemixstatus){: new_window}. Als Ausweichlösung können Sie den Service in einer anderen {{site.data.keyword.Bluemix_notm}}-Region verwenden. Ausführliche Informationen finden Sie in [Services in einer anderen Region verwenden ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/reqnsi.html#cross_region_service){: new_window}. Wenn der Status des Service als normal angegeben ist, versuchen Sie anhand der folgenden Schritte, das Problem zu beheben:
{: tsResolve}

  * Wiederholen Sie die Aktion.
    * Laden Sie die Seite neu, indem Sie auf der Tastatur die Taste F5 drücken oder auf die Schaltfläche zum Aktualisieren der Anzeige klicken. Wenn dieser Schritt nicht funktioniert, löschen Sie den Inhalt des Cachespeichers und die Cookies und laden Sie die Seite anschließend erneut.
    * Verwenden Sie einen anderen Browser.
    * Starten Sie Router, Modem und Computer erneut. Durch einen Warmstart dieser Geräte können verschiedene Fehler bereinigt werden, die zu dem Fehler 502 führen.
  * Warten Sie und wiederholen Sie den Vorgang zu einem späteren Zeitpunkt. Bei einigen Instanzen kann es in Verbindung mit Ihrem Internet-Service-Provider oder den {{site.data.keyword.Bluemix_notm}}-Services zu vorübergehenden Problemen kommen. Warten Sie, bis die vorübergehenden Probleme gelöst wurden.
  * Wenn das Problem dennoch bestehen bleibt, wenden Sie sich an den {{site.data.keyword.Bluemix_notm}}-Support. Weitere Informationen finden Sie unter [Kontaktaufnahme mit dem {{site.data.keyword.Bluemix_notm}}-Support ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](/docs/support/index.html#contacting-bluemix-support){: new_window}.

## Überschrittenes Plattenkontingent
{: #ts_disk_quota}

Wenn der Plattenspeicher knapp wird, können Sie das Plattenkontingent manuell so ändern, dass mehr Plattenspeicher zur Verfügung steht.

Wenn der Plattenspeicher knapp wird, wird möglicherweise eine Nachricht angezeigt, die besagt, dass das Plattenkontingent überschritten wurde. Zur Lösung des Problems haben Sie möglicherweise versucht, für Ihre App-Instanz ein Scale-up durchzuführen, um mehr Plattenspeicher zu erhalten. Sie haben beispielsweise versucht, ein Scale-up von 256 MB auf 1256 MB durchzuführen, und zwar durch Ändern des Speicherkontingents auf der Seite mit den App-Details. Da jedoch das Plattenkontingent dasselbe geblieben ist, haben Sie nicht mehr Plattenspeicher erhalten.
{: tsSymptoms}

Das Standardplattenkontingent, das für eine App zugeordnet wird, beträgt 1 GB. Wenn Sie mehr Plattenspeicher benötigen, müssen Sie das Plattenkontingent manuell angeben.
{: tsCauses}

Verwenden Sie eine der folgenden Methoden, um Ihr Plattenkontingent anzugeben. Sie können ein maximales Plattenkontingent von 2 GB angeben. Falls 2 GB dennoch nicht genug sein sollten, setzen Sie versuchsweise einen externen Service ein, z. B. [Object Store](/docs/services/ObjectStorage/index.html).
{: tsResolve}

  * Fügen Sie in der Datei 'manifest.yml' das folgende Element hinzu:
    ```
	disk_quota: <disk_quota>
	```
  * Verwenden Sie die Option **-k** in Kombination mit dem Befehl `cf push`, wenn Sie Ihre App mit einer Push-Operation an {{site.data.keyword.Bluemix_notm}} übertragen:
    ```
	cf push appname -p app_path -k <disk_quota>
	```


## Android-Apps empfangen keine {{site.data.keyword.mobilepushshort}}
{: #ts_push}

In bestimmten Regionen, in denen nicht auf Google zugegriffen werden kann, empfangen Android-Apps keine Benachrichtigungen, die Sie über den IBM {{site.data.keyword.mobilepushshort}}-Service senden. In diesem Fall besteht die Ausweichlösung darin, Drittanbieterservices zu verwenden.

Sie können einen {{site.data.keyword.mobilepushshort}}-Service für Ihre {{site.data.keyword.Bluemix_notm}}-App verwenden und eine Nachricht an die registrierten Geräte senden. Jedoch können Apps, die auf der Android-Plattform entwickelt wurden, Ihre Benachrichtigungen in bestimmten Regionen nicht empfangen.
{: tsSymptoms}

Der IBM {{site.data.keyword.mobilepushshort}}-Service nutzt den GCM-Service (Google Cloud Messaging), um Benachrichtigungen an mobile Apps zu versenden, die auf der Android-Plattform entwickelt wurden. Zur Aktivierung der Android-Apps für den Empfang von Benachrichtigungen muss der GCM-Service für die mobilen Apps zugänglich sein. In Regionen, in denen der GCM-Service nicht von den Android-Apps erreicht werden kann, können die Android-Apps keine {{site.data.keyword.mobilepushshort}} empfangen.
{: tsCauses}

Verwenden Sie als Ausweichlösung Services von Drittanbietern, die nicht vom GCM-Service abhängig sind, z. B. [Pushy ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://pushy.me){: new_window}, [getui ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://www.getui.com/){: new_window} oder [jpush ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://www.jpush.cn/){: new_window}.
{: tsResolve}

## Für Organisation geltender Grenzwert für Services wurde überschritten
{: #ts_servicelimit}

Wenn Sie Benutzer eines Testkontos sind, können Sie möglicherweise keine App in {{site.data.keyword.Bluemix_notm}} erstellen, wenn Sie den für Ihre Organisation geltenden Grenzwert für Services überschritten haben. 

Bei dem Versuch, in {{site.data.keyword.Bluemix_notm}} eine App zu erstellen, wird die folgende Fehlernachricht angezeigt:
{: tsSymptoms}

`BXNUI2032E: Die Ressource <service_instances> wurde nicht erstellt. Während der Kontaktaufnahme mit Cloud Foundry zum Erstellen der Ressource ist ein Fehler aufgetreten. Cloud Foundry-Nachricht: "You have exceeded your organization's services limit." ("Sie haben den für Ihre Organisation geltenden Grenzwert für Services überschritten.")`

Dieser Fehler tritt auf, wenn Sie den Grenzwert für die Anzahl der Serviceinstanzen, die für Ihr Konto bestehen können, überschritten haben. Die maximale Anzahl von Serviceinstanzen für ein Testkonto beträgt 10.
{: tsCauses}

Löschen Sie alle nicht benötigten Serviceinstanzen oder entfernen Sie den Grenzwert für die für Sie zulässige Anzahl von Serviceinstanzen.
{: tsResolve}

  * Zum Löschen einer Serviceinstanz können Sie die {{site.data.keyword.Bluemix_notm}}-Konsole oder die Befehlszeilenschnittstelle verwenden.

    Wenn Sie die {{site.data.keyword.Bluemix_notm}}-Konsole zum Löschen einer Serviceinstanz verwenden, führen Sie die folgenden Schritte aus:
	  1. Klicken Sie im Dashboard 'Services' für den Service, den Sie löschen wollen, auf das Menü **Aktionen**.
	  2. Klicken Sie auf **Service löschen**. Sie werden dazu aufgefordert, für die App, an die die Serviceinstanz gebunden war, ein erneutes Staging durchzuführen.

    Wenn Sie die Befehlszeilenschnittstelle zum Löschen einer Serviceinstanz verwenden, führen Sie folgende Schritte aus:
	  3. Heben Sie die Bindung zwischen der Serviceinstanz und der App mit dem folgenden Befehl auf: `cf unbind-service <appname> <service_instance_name>`.
	  4. Löschen Sie die Serviceinstanz durch Eingeben von `cf delete-service <service_instance_name>`.
	  5. Nach dem Löschen der Serviceinstanz ist es gegebenenfalls wünschenswert, für Ihre App, an die die Serviceinstanz gebunden war, ein erneutes Staging durchzuführen. Geben Sie hierzu folgenden Befehl ein: `cf restage <appname>`.

  * Wenn der Grenzwert für die Anzahl von Serviceinstanzen, über die Sie verfügen können, entfernt werden soll, müssen Sie Ihr Testkonto in ein zahlungspflichtiges Konto umwandeln. Informationen dazu, wie Ihr Testkonto in ein Zahlungskonto umgewandelt wird, finden Sie unter [Vorgehensweise zum Ändern des Plans](/docs/pricing/index.html#changing).

## Ausführbare Dateien können in {{site.data.keyword.Bluemix_notm}} nicht ausgeführt werden
{: #ts_executable}

Möglicherweise können Sie ausführbare Dateien in {{site.data.keyword.Bluemix_notm}} nicht ausführen, wenn diese ausführbaren Dateien in einer anderen Umgebung entwickelt wurden und der Build für sie auch dort erstellt wurde.

Sie können ausführbare Dateien nicht in {{site.data.keyword.Bluemix_notm}} ausführen, wenn diese ausführbaren Dateien in einer anderen Umgebung entwickelt und der Build für sie dort erstellt wurde.
{: tsSymptoms}

Wenn es sich bei dem Inhalt, den Sie per Push-Operation an {{site.data.keyword.Bluemix_notm}} übertragen wollen, bereits um eine ausführbare Datei handelt, wurde der Build für den Inhalt zuvor erstellt und ein erneuter Build in {{site.data.keyword.Bluemix_notm}} ist nicht erforderlich. In diesem Fall ist kein Buildpack erforderlich, damit die ausführbare Datei in {{site.data.keyword.Bluemix_notm}} ausgeführt werden kann. Sie müssen für {{site.data.keyword.Bluemix_notm}} explizit angeben, dass ein Buildpack nicht erforderlich ist.
{: tsCauses}

Wenn Sie die ausführbare Datei per Push-Operation an {{site.data.keyword.Bluemix_notm}} übertragen, müssen Sie durch einen `Null-Buildpack` angeben, dass kein Buildpack erforderlich ist. Sie geben einen `Null-Buildpack` an, indem Sie die Option **-b** in Verbindung mit dem Befehl `cf push` verwenden:
{: tsResolve}

```
cf push appname -p app_path -c <start_command> -b <null-buildpack>
```
Beispiel:
```
cf push appname -p app_path -c ./RunMeNow -b https://github.com/ryandotsmith/null-buildpack
```

## Für Organisation geltende Speicherbegrenzung wurde überschritten
{: #ts_outofmemory}

Wenn Sie Benutzer eines Testkontos sind, können Sie möglicherweise eine App nicht in {{site.data.keyword.Bluemix_notm}} bereitstellen, wenn Sie die für Ihre Organisation geltende Speicherbegrenzung überschritten haben. Sie können entweder den von Ihren Apps verwendeten Speicherplatz verringern oder das Speicherkontingent Ihres Konto erhöhen. Das Kontingent der maximalen Hauptspeicherkapazität für ein Testkonto beträgt 2 Gigabyte und kann nur durch den Wechsel zu einem gebührenpflichtigen Konto erhöht werden.

Wenn Sie eine App unter {{site.data.keyword.Bluemix_notm}} bereitstellen, wird die folgende Fehlernachricht angezeigt:
{: tsSymptoms}

`FAILED Server error, status code: 400, error code: 100005, message: You have exceeded your organization's memory limit.` (FEHLGESCHLAGEN Serverfehler, Statuscode: 400, Fehlercode: 100005, Nachricht: Sie haben die für Ihre Organisation geltende Speicherbegrenzung überschritten.)

Dieser Fehler tritt auf, wenn die für Ihre Organisation verbleibende Speichermenge niedriger ist, als die Speichermenge, die für die bereitzustellende App erforderlich ist. Das Kontingent der maximalen Hauptspeicherkapazität für ein Testkonto beträgt 2 Gigabyte.
{: tsCauses}

Sie können entweder das Speicherkontingent für Ihr Konto erhöhen oder den von Ihren Apps verwendeten Speicherplatz verringern.
{: tsResolve}

  * Zum Erhöhen des Speicherkontingents für Ihr Konto müssen Sie Ihr Testkonto in ein zahlungspflichtiges Konto umwandeln. Informationen dazu, wie Ihr Testkonto in ein Zahlungskonto umgewandelt wird, finden Sie unter [Zahlungskonten](/docs/pricing/index.html#pay-accounts).
  * Zum Verringern des Speicherplatzes, den Ihre Apps belegen, verwenden Sie entweder die {{site.data.keyword.Bluemix_notm}}-Konsole oder die Befehlszeilenschnittstelle `cf`. 

    Wenn Sie die {{site.data.keyword.Bluemix_notm}}-Konsole verwenden, führen Sie die folgenden Schritte aus:

    1. Wählen Sie im Dashboard 'Apps' Ihre App aus. Die Seite mit den Anwendungsdetails wird geöffnet.
    2. Im Teilfenster für die Laufzeit können Sie die maximale Hauptspeicherkapazität für Ihre App, die Anzahl der App-Instanzen oder beide Angaben reduzieren.

    Wenn Sie die Befehlszeilenschnittstelle `cf` verwenden, führen Sie die folgenden Schritte aus:

    1. Überprüfen Sie, wie viel Speicherplatz für Ihre Apps verwendet wird:

	  ```
	  cf apps
	  ```

	  Mit dem Befehl `cf apps` werden alle Apps aufgelistet, die Sie in Ihrem aktuellen Bereich bereitgestellt haben. Der Status der einzelnen Apps wird auch angezeigt.

    2. Zum Verringern der von Ihrer App verwendeten Speichermenge verringern Sie die Anzahl der App-Instanzen, die maximale Hauptspeicherkapazität oder beides:

	  ```
	  cf push appname -p app_path -i instance_number -m memory_limit
      ```

    3. Starten Sie Ihre App erneut, damit die Änderungen wirksam werden.

## Apps werden nicht automatisch erneut gestartet
{: #ts_apps_not_auto_restarted}

Eine App wird nicht automatisch erneut gestartet, wenn ein Service, den Sie an die App binden, nicht mehr ausgeführt wird.

Bei Absturz eines Service, den Sie an eine App binden, können in der App Probleme wie beispielsweise Ausfallzeiten, Ausnahmebedingungen und Verbindungsfehler auftreten. Die App wird von {{site.data.keyword.Bluemix_notm}} nicht automatisch neu gestartet, um diese Probleme zu beheben.
{: tsSymptoms}

Dieses Verhalten gehört zum Design von Cloud Foundry.
{: tsCauses}

Sie können die App manuell erneut starten, indem Sie den folgenden Befehl in die Befehlszeilenschnittstelle eingeben:
{: tsResolve}

```
cf push appname -p app_path
```

Darüber hinaus können Sie die App so codieren, dass Probleme wie Ausfallzeiten, Ausnahmebedingungen und Verbindungsfehler erkannt werden und eine Recovery durchgeführt wird.

## Verlust benutzerdefinierter Variablen bei Push-Operation für App
{: #ts_varsnotretained}

Wenn Sie eine App mit einer Push-Operation aus IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} an {{site.data.keyword.Bluemix_notm}} übertragen, werden die angegebenen Variablen zurückgesetzt, sofern die Variablen nicht in der Manifestdatei gespeichert werden.

Die angegebenen Variablen gehen verloren, nachdem Sie eine App mit einer Push-Operation von IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} an {{site.data.keyword.Bluemix_notm}} übertragen haben.
{: tsSymptoms}

Die angegebenen Variablen werden nur gespeichert, wenn Sie sie in der Manifestdatei speichern.
{: tsCauses}

Wenn Sie eine App aus IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}} mit einer Push-Operation an {{site.data.keyword.Bluemix_notm}} übertragen, wählen Sie das Kontrollkästchen **In Manifestdatei speichern** auf der Seite 'Anwendungsdetails' im Assistenten 'Anwendung' aus. Danach werden die Variablen, die Sie im Assistenten angeben, in der Manifestdatei für die Anwendung gespeichert. Beim nächsten Öffnen des Assistenten werden die Variablen automatisch angezeigt.
{: tsResolve}


## Organisationen werden in {{site.data.keyword.Bluemix_notm}} nicht gefunden
{: #ts_orgs}

Es kann vorkommen, dass Sie Ihre Organisation in {{site.data.keyword.Bluemix_notm}} nicht finden können, wenn Sie in einer {{site.data.keyword.Bluemix_notm}}-Region arbeiten.

Sie können sich zwar erfolgreich an der {{site.data.keyword.Bluemix_notm}}-Konsole anmelden, jedoch keine Apps mithilfe der Befehlszeilenschnittstelle `cf` oder des Eclipse-Plug-ins per Push-Operation übertragen.
{: tsSymptoms}

Wenn Sie versuchen, mithilfe der Befehlszeilenschnittstelle `cf` eine Anwendung per Push-Operation an {{site.data.keyword.Bluemix_notm}} zu übertragen, wird eine der folgenden Fehlernachrichten mit angegebenem Organisationsnamen angezeigt:

`Error finding org` (Fehler bei der Suche nach der Organisation)

`Organization not found` (Organisation nicht gefunden)

Wenn Sie versuchen, mithilfe des Eclipse-Plug-ins von Cloud Foundry eine Anwendung per Push-Operation an {{site.data.keyword.Bluemix_notm}} zu übertragen, wird die folgende Fehlernachricht angezeigt:

`Cloudspace not found` (Cloudbereich nicht gefunden)

Dieses Problem tritt auf, weil der API-Endpunkt der Region, mit der Sie arbeiten möchten, nicht angegeben ist und sich die gesuchte Organisation eventuell in einer anderen Region befindet.
{: tsCauses}

Wenn Sie eine Anwendung mithilfe der Befehlszeilenschnittstelle `cf` per Push-Operation an {{site.data.keyword.Bluemix_notm}} übertragen, geben Sie den Befehl `cf api` ein und geben Sie den API-Endpunkt der Region an. Geben Sie beispielsweise den folgenden Befehl ein, um eine Verbindung zu der {{site.data.keyword.Bluemix_notm}}-Region 'Europa - Vereintes Königreich' herzustellen:
{: tsResolve}

```
cf api https://api.eu-gb.bluemix.net
```

Wenn Sie eine Anwendung mithilfe von Eclipse Tools mit einer Push-Operation an {{site.data.keyword.Bluemix_notm}} übertragen, müssen Sie zuerst einen {{site.data.keyword.Bluemix_notm}}-Server erstellen und den API-Endpunkt der {{site.data.keyword.Bluemix_notm}}-Region angeben, in der die Organisation erstellt wurde. Weitere Informationen zur Verwendung der Eclipse-Tools finden Sie im Thema zur [Bereitstellung von Apps mit IBM Eclipse Tools for {{site.data.keyword.Bluemix_notm}}](/docs/manageapps/eclipsetools/eclipsetools.html).

## Erstellung von App-Routen nicht möglich
{: #ts_hostistaken}

Wenn Sie eine App unter {{site.data.keyword.Bluemix_notm}} bereitstellen, kann die Route der App nicht erstellt werden, wenn der angegebene Hostname bereits verwendet wird.

Wenn Sie eine App unter {{site.data.keyword.Bluemix_notm}} bereitstellen, wird die folgende Fehlernachricht angezeigt:
{: tsSymptoms}

`Creating route hostname.domainname ... FAILED Server error, status code: 400, error code: 210003, message: The host is taken: hostname` (Erstellen von Route 'hostname.domänenname' ... FEHLGESCHLAGEN Serverfehler, Statuscode: 400, Fehlercode: 210003, Nachricht: Der Hostname ist vergeben: 'hostname')

Dieses Problem tritt auf, wenn der angegebene Hostname bereits verwendet wird.
{: tsCauses}

Der angegebene Hostname muss innerhalb der verwendeten Domäne eindeutig sein. Verwenden Sie zum Angeben eines anderen Hostnamens eine der folgenden Methoden:
{: tsResolve}

  * Wenn Sie zum Implementieren der Anwendung die Datei `manifest.yml` verwenden, geben Sie den Hostnamen in der Option host an.
    ```
    host: host_name
	```
  * Wenn Sie die Anwendung über eine Eingabeaufforderung bereitstellen, verwenden Sie den Befehl `cf push` in Verbindung mit der Option **-n**.
    ```
    cf push appname -p app_path -n host_name
    ```


## Push-Operation für WAR-Anwendung mit Befehl cf push nicht möglich
{: #ts_cf_war}

Es kann vorkommen, dass Sie mit dem Befehl `cf push` eine archivierte Web-App unter {{site.data.keyword.Bluemix_notm}} nicht bereitstellen können, wenn die Position der App nicht ordnungsgemäß angegeben ist. 

Wenn Sie eine WAR-App in {{site.data.keyword.Bluemix_notm}} mit dem Befehl `cf push` hochladen, wird die folgende Fehlernachricht angezeigt:
{: tsSymptoms}
`Staging error: Cannot get instances since staging failed.` (Abrufen der Instanzen wegen fehlgeschlagenem Staging nicht möglich.)

Dieses Problem kann auftreten, wenn die WAR-Datei nicht angegeben ist oder wenn der Pfad zur WAR Datei nicht angegeben ist.
{: tsCauses}

Verwenden Sie die Option **-p** zum Angeben einer WAR-Datei oder fügen Sie den Pfad zur WAR-Datei hinzu. Beispiel:
{: tsResolve}

```
cf push MyUniqueAppName01 -p app.war
```

```
cf push MyUniqueAppName02 -p "./app.war"
```
Weitere Informationen zum Befehl `cf push` erhalten Sie, wenn Sie `cf push -h` eingeben.


## Anzeigen von Doppelbytezeichen nach Push-Operation für Apps in {{site.data.keyword.Bluemix_notm}} nicht ordnungsgemäß
{: #ts_doublebytes}

Es kann vorkommen, dass Doppelbytezeichen nicht ordnungsgemäß angezeigt werden, wenn die Unicode-Unterstützung für das Servlet oder die JSP-Dateien nicht ordnungsgemäß konfiguriert wurde.

Wenn eine Anwendung per Push-Operation an {{site.data.keyword.Bluemix_notm}} übertragen wird, werden Doppelbytezeichen, die in der App angegeben sind, nicht ordnungsgemäß angezeigt.
{: tsSymptoms}

Das Problem kann auftreten, wenn die Unicode-Unterstützung für das Servlet oder die JSP-Dateien nicht ordnungsgemäß konfiguriert ist.
{: tsCauses}

Sie können den folgenden Code im Servlet oder der JSP-Datei verwenden:
{: tsResolve}

  * In der Servletquellendatei:
    ```
	response.setContentType("text/html; charset=UTF-8");
	```
  * In der JSP-Datei:
    ```
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```


## Bereitstellung von Node.js-Apps nicht möglich
{: #ts_nodejs_deploy}

Bei der Aktualisierung einer Node.js-App oder bei der Bereitstellung einer Node.js-App in {{site.data.keyword.Bluemix_notm}} kann es zu Problemen kommen.

Bei der Aktualisierung einer Node.js-App oder bei der Bereitstellung einer Node.js-App in {{site.data.keyword.Bluemix_notm}} wird möglicherweise eine der folgenden Fehlernachrichten angezeigt:
{: tsSymptoms}

`An app was not successfully detected by any available buildpack.` (Eine App wurde von keinem verfügbaren Buildpack erfolgreich erkannt.)

`Instance (index 0) failed to start accepting connections.` (Bestätigen der Verbindungen durch Instanz (Index 0) fehlgeschlagen.)

`Cannot get instances since staging failed.` (Abrufen der Instanzen wegen fehlgeschlagenem Staging nicht möglich.)

Mögliche Ursachen:
{: tsCauses}

  * Der Startbefehl ist nicht angegeben.
  * In der App oder in einem anderen Ordner als dem Stammverzeichnis fehlen Dateien, die für die Bereitstellung einer Node.js-App erforderlich sind.

Verwenden Sie je nach Ursache des Problems eine der folgenden Methoden:
{: tsResolve}

  * Geben Sie unter Verwendung einer der folgenden Methoden den Startbefehl an:
     * Verwenden Sie die Befehlszeilenschnittstelle `cf`. Beispiel:
        ```
		cf push MyUniqueNodejs01 -p app_path -c "node app.js"
		```
    * Mithilfe der Datei [package.json ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://www.npmjs.com/package/jsonfile){: new_window}. Beispiel:
	    ```
		{
      ...
  	   "scripts": {
	 		 "start": "node app.js"
 	   }
	}
	    ```
    * Mithilfe der Datei `manifest.yml`. Beispiel:
	    ```
		applications:
  name: MyUniqueNodejs01
  ...
  command: node app.js
  ...
        ```

  * Stellen Sie sicher, dass in Ihrer Node.js-App eine Datei des Typs `package.json` existiert, damit das Node.js-Buildpack für die Erkennung der App aktiviert werden kann. Stellen Sie sicher, dass sich diese Datei im Stammverzeichnis Ihrer App befindet.
    Das folgende Beispiel zeigt eine einfache `package.json`-Datei:
	```
	{
        "name": "MyUniqueNodejs01",
        "version": "0.0.1",
        "description": "A sample package.json file",
        "dependencies": {
                "express": "3.4.x",
                "jade": "1.1.x"
        },
        "engines": {
                "node": "0.10.x"
        },
        "scripts": {
                  "start": "node app.js"
        }
 }
    ```

Weitere Tipps zu Node.js-Apps finden Sie unter [Tipps für Node.js-Anwendungen ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window}.


## Konfigurationsfehler in Datei `server.xml` nach Import einer {{site.data.keyword.Bluemix_notm}} Liberty-App in Eclipse
{: #ts_eclipse}

Wenn in der Datei `server.xml` nach dem Import einer {{site.data.keyword.Bluemix_notm}} Liberty-App in Eclipse Konfigurationsfehler angezeigt werden, kann es erforderlich sein, die Datei `server.xml` aus dem Projekt zu entfernen.

Nach dem Import einer {{site.data.keyword.Bluemix_notm}} Liberty-App in Eclipse werden in der Eclipse-Ansicht 'Fehler' Konfigurationsfehler in der Datei `server.xml` angezeigt.
{: tsSymptoms}

Das Liberty-Buildpack verwendet die Datei `server.xml` zum Konfigurieren der App und generiert die Datei `runtime-vars.xml`, wenn die Liberty-App per Push-Operation an {{site.data.keyword.Bluemix_notm}} übertragen wird. Wenn Sie die App in Eclipse importieren, ist die Datei `runtime-vars.xml` in der lokalen Umgebung nicht vorhanden.
{: tsCauses}

Sie können dieses Problem durch Entfernen der Datei server.xml aus dem Projekt beheben. Vom Buildpack wird die Datei `server.xml` dynamisch erstellt, wenn Sie die App mit einer Push-Operation als WAR-App übertragen. Weitere Informationen finden Sie unter [Liberty for Java](/docs/runtimes/liberty/index.html).
{: tsResolve}


## Staging für Apps mit angepassten Buildpacks nicht möglich
{: #ts_bp_compilation}

Es kann vorkommen, dass eine App unter {{site.data.keyword.Bluemix_notm}} nicht unter Verwendung eines angepassten Buildpacks bereitgestellt werden kann, wenn die Scripts im Buildpack nicht ausführbar sind.

Wenn Sie eine App unter {{site.data.keyword.Bluemix_notm}} unter Verwendung eines angepassten Buildpacks bereitstellen, kann es vorkommen, dass die Fehlernachricht `The application failed to stage, so there are no instances to display.` (Anzeigen der Instanzen nicht möglich, da Staging der Anwendung fehlgeschlagen ist) angezeigt wird.
{: tsSymptoms}

Dieses Problem kann auftreten, wenn Scripts, wie zum Beispiel die Scripts zum Identifizieren, Kompilieren und Freigeben, nicht ausgeführt werden können.
{: tsCauses}

Mit dem Befehl [git update ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](http://git-scm.com/docs/git-update-index){: new_window} können Sie die Berechtigung für jedes einzelne Script in 'ausführbar' ändern. Sie können zum Beispiel `git update --chmod=+x script.sh` eingeben.
{: tsResolve}

## Implementieren einer App über die Delivery Pipeline in IBM {{site.data.keyword.Bluemix_notm}} Continuous Delivery nicht möglich
 {: #ts_devops_to_bm}

 Es kann vorkommen, dass eine App nicht unter Verwendung der {{site.data.keyword.deliverypipeline}} in {{site.data.keyword.contdelivery_short}} implementiert werden kann, wenn die Datei `manifest.yml` nicht in der App vorhanden ist.

 Wenn Sie eine App unter Verwendung der {{site.data.keyword.deliverypipeline}} in {{site.data.keyword.contdelivery_short}} implementieren, kann die Fehlernachricht `Unable to detect a supported application type` (Ermittlung eines unterstützten Anwendungstyps fehlgeschlagen) angezeigt werden.
 {: tsSymptoms}

 Dieses Problem kann auftreten, weil für die Pipeline die Datei `manifest.yml` zum Implementieren einer App in {{site.data.keyword.Bluemix_notm}} erforderlich ist.
 {: tsCauses}

 Zum Beheben dieses Problems müssen Sie die Datei `manifest.yml` erstellen. Weitere Informationen zum Erstellen der Datei `manifest.yml` finden Sie im
[Abschnitt zum Anwendungsmanifest](/docs/manageapps/depapps.html#appmanifest).
 {: tsResolve}

## Push-Operation für Meteor-Anwendungen nicht möglich
{: #ts_meteor}

Es kann vorkommen, dass eine Meteor-Anwendung nicht per Push-Operation an {{site.data.keyword.Bluemix_notm}} übertragen werden kann, wenn der Buildpack nicht ordnungsgemäß angegeben ist.

Wenn Sie eine Meteor-App unter {{site.data.keyword.Bluemix_notm}} bereitstellen, kann die Fehlernachricht `The application failed to stage, so there are no instances to display.` (Anzeigen der Instanzen nicht möglich, da Staging der Anwendung fehlgeschlagen ist) angezeigt werden.
{: tsSymptoms}

Dieses Problem tritt auf, weil für Meteor-Apps kein integriertes Buildpack bereitgestellt wird. Sie müssen ein angepasstes Buildpack verwenden.
{: tsCauses}

Verwenden Sie eine der folgenden Methoden, um ein angepasstes Buildpack für Meteor-Apps zu verwenden:
{: tsResolve}

  * Wenn Sie zum Implementieren der App die Datei `manifest.yml` verwenden, geben Sie die URL oder den Namen des angepassten Buildpacks mithilfe der Option 'buildpack' an. Beispiel:
  ```
  buildpack: https://github.com/Sing-Li/bluemix-bp-meteor
  ```
  * Wenn Sie die Anwendung in einer Eingabeaufforderung bereitstellen, verwenden Sie den Befehl `cf push` und geben Sie das angepasste Buildpack mit der Option **-b** an. Beispiel:
    ```
	cf push appname -p app_path -b https://github.com/Sing-Li/bluemix-bp-meteor
	```
