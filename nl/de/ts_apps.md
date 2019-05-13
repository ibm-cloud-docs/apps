---

copyright:
  years: 2015, 2019
lastupdated: "2019-05-08"

keywords: apps, application, troubleshooting, debug apps, known issues, debug, help, configuration, app, troubleshoot, error, errors, failure, failed, fail, issues, applications

subcollection: creating-apps

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Fehlerbehebung für die Erstellung von Apps
{: #managingapps}

Allgemeine Probleme im Zusammenhang mit der Erstellung von Apps können sein, dass Apps nicht aktualisiert werden können oder Doppelbytezeichen nicht angezeigt werden. In vielen Fällen können Sie diese Probleme durch Ausführen weniger einfacher Schritte beheben.
{:shortdesc}

## Eigene Apps werden in unterschiedlichen Domänen gehostet
{: #domains-ts}
{: troubleshoot}

Einige Apps werden in der Domäne `mybluemix.net` gehostet, andere jedoch in der Domäne `appdomain.cloud`.

Ihre eigenen vorhandenen Apps werden in der Domäne `mybluemix.net` gehostet, aber Ihre neueren Apps werden in der Domäne `appdomain.cloud` gehostet.
{: tsSymptoms}

Unter 'cloud.ibm.com' ist eine neue Option `*.appdomain.cloud` für den Hostnamen verfügbar.

Zuvor wurde die Domäne `mybluemix.net` für das Hosting von Apps in unterschiedlichen Bereitstellungszielen wie beispielsweise {{site.data.keyword.containerlong_notm}} oder Cloud Foundry verwendet. Bereits unter `mybluemix.net` gehostete Apps sind nicht betroffen.

Die Unterdomäne für Cloud Foundry-Apps heißt `cf.appdomain.cloud`. Die Unterdomäne für Apps, die Sie in {{site.data.keyword.containerlong_notm}} bereitstellen, heißt `containers.appdomain.cloud`.

Weitere Informationen enthält der Abschnitt [Eigene Domänen verwalten](/docs/apps?topic=creating-apps-update-domain).

## Es sind nicht gespeicherte Änderungen vorhanden
{: #ts_unsaved_changes}
{: troubleshoot}

Wenn Sie auf der Detailseite der App auf bestimmte Elemente klicken, können Sie möglicherweise keine Aktionen ausführen. Darüber hinaus werden Sie möglicherweise dazu aufgefordert, Änderungen zu speichern, bevor Sie den Vorgang fortsetzen können.

Wenn Sie versuchen, Ihre App oder Services auf der Detailseite der App zu prüfen, wird die folgende Fehlernachricht angezeigt:
{: tsSymptoms}

`Es sind nicht gespeicherte Änderungen vorhanden. Möchten Sie diese Seite tatsächlich verlassen?`

Wenn Sie Ihre Maus über das Feld **INSTANCES** (Instanzen) oder **MEMORY QUOTA** (Speicherkontingent) im Teilfenster für die Laufzeit bewegen, ändern sich die Werte. Hierbei handelt es sich um ein vorgesehenes Verhalten. Sie werden jedoch dazu aufgefordert, die Speicher- oder Instanzeinstellungen zu speichern, bevor Sie eine andere Seite aufrufen.
{: tsCauses}

Schließen Sie das Nachrichtenfenster und klicken Sie im Teilfenster für Ihre Laufzeitumgebung auf **ZURÜCKSETZEN**.
{: tsResolve}

## Automatische Funktionsübernahme zwischen {{site.data.keyword.cloud_notm}}-Regionen nicht verfügbar
{: #ts_failover}
{: troubleshoot}

Die automatische Funktionsübernahme zwischen {{site.data.keyword.cloud}}-Regionen kann nicht verwendet werden. Sie können allerdings einen DNS-Anbieter nutzen, der eine Funktionsübernahme zwischen mehreren IP-Adressen als Ausweichlösung unterstützt.

Wenn eine {{site.data.keyword.cloud_notm}}-Region nicht mehr verfügbar ist, sind auch die Apps, die in dieser Region ausgeführt werden, nicht mehr verfügbar, selbst dann nicht, wenn dieselben Apps in einer anderen {{site.data.keyword.cloud_notm}}-Region ausgeführt werden.
{: tsSymptoms}

{{site.data.keyword.cloud_notm}} bietet noch keine automatische Funktionsübernahme zwischen zwei Regionen an.
{: tsCauses}

Sie können einen DNS-Anbieter nutzen, der eine intelligente Funktionsübernahme zwischen einer Vielzahl von ID-Adressen unterstützt, und Ihre DNS-Einstellungen zur Aktivierung der automatischen Funktionsübernahme zwischen {{site.data.keyword.cloud_notm}}-Regionen manuell konfigurieren. DNS-Anbieter mit dieser Funktion sind z. B. NSONE, Akamai und Dyn.
{: tsResolve}

Wenn Sie Ihre DNS-Einstellungen konfigurieren, müssen Sie die öffentlichen IP-Adressen der {{site.data.keyword.cloud_notm}}-Regionen angeben, in denen Ihre Apps ausgeführt werden. Verwenden Sie zum Abrufen der öffentlichen IP-Adresse einer {{site.data.keyword.cloud_notm}}-Region den Befehl `nslookup`. Sie können in einem Befehlszeilenfenster beispielsweise den nachfolgenden Befehl eingeben.
```
nslookup cloud.ibm.com
```
{: codeblock}

## Auf {{site.data.keyword.cloud_notm}}-Services kann aufgrund von Berechtigungsfehlern nicht zugegriffen werden
{: #ts_vcap}
{: troubleshoot}

Berechtigungsfehler können auftreten, wenn Ihre App auf einen {{site.data.keyword.cloud_notm}}-Service zugreift und die Serviceberechtigungen in Ihrer App fest codiert sind.

Nachdem Sie Ihre App für die Kommunikation mit einem {{site.data.keyword.cloud_notm}}-Service konfiguriert haben, stellen Sie sie in {{site.data.keyword.cloud_notm}} bereit. Sie können die App jedoch nicht für den Zugriff auf den {{site.data.keyword.cloud_notm}}-Service verwenden und empfangen einen Berechtigungsfehler.
{: tsSymptoms}

Die fest codierten Berechtigungsnachweise in der App sind möglicherweise nicht korrekt. Jedes Mal, wenn der Service erneut erstellt wird, ändern sich die Berechtigungsnachweise für den Zugriff darauf.
{: tsCauses}

Statt die Berechtigungsnachweise in Ihrer App fest zu codieren, verwenden Sie Verbindungsparameter aus der Umgebungsvariablen VCAP_SERVICES. Die Methoden für die Verwendung von Verbindungsparametern aus der Umgebungsvariablen VCAP_SERVICES variieren abhängig von den Programmsprachen. Für Node.js-Apps können Sie beispielsweise den folgenden Befehl verwenden:
{: tsResolve}

```
process.env.VCAP_SERVICES
```

Weitere Informationen zu den Befehlen, die Sie in anderen Programmsprachen verwenden können, finden Sie in den Tipps für [Java ](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") und für [Ruby ](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").

## Fehler des Typs '502 Bad Gateway' empfangen
{: #ts_502_error}
{: troubleshoot}

Wenn Sie bei der Interaktion mit Apps unter {{site.data.keyword.cloud_notm}} Fehler vom Typ `502 Bad Gateway` erhalten, überprüfen Sie die Seite für die {{site.data.keyword.cloud_notm}}-Status und führen Sie anschließend die entsprechenden Aktionen durch.

Sie erhalten Fehlernachrichten, die mit '502 Bad Gateway' beginnen. So wird beispielsweise die Fehlernachricht `502 Bad Gateway: Verarbeitung der Anfrage durch registrierten Endpunkt fehlgeschlagen.` angezeigt.
{: tsSymptoms}

Zu einem Fehler des Typs 'Bad Gateway' kommt es in der Regel, wenn Sie eine Website besuchen, bei der zum Speichern und Vermitteln der Daten aus dem Hauptserver, der die Site hostet, ein Proxy-Server verwendet wird. Der Hauptserver und der Proxy-Server sind möglicherweise nicht ordnungsgemäß miteinander verbunden. In diesem Fall wird der HTTP-Statuscode 502 im Browserfenster angezeigt. Dieser Statuscode weist darauf hin, dass der Hauptserver der Site die HTTP-Implementierung, die vom Proxy-Server erwartet wird, nicht erhalten hat.
{: tsCauses}

Andere, weniger häufige Ursachen eines Fehlers vom Typ 'Bad Gateway' sind Ausfälle des Internet-Service-Providers, falsche Firewallkonfigurationen und Fehler des Browser-Cache.

Wenn Sie vermuten, dass ein {{site.data.keyword.cloud_notm}}-Service inaktiv ist, überprüfen Sie zunächst die Seite für den [{{site.data.keyword.cloud_notm}}-Status ](https://cloud.ibm.com/status){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link"). Als Ausweichlösung können Sie [den Service in einer anderen {{site.data.keyword.cloud_notm}}-Region verwenden](/docs/resources/connect_external_app?topic=resources-externalapp){: new_window}. Wenn der Status des Service als normal angegeben ist, versuchen Sie anhand der folgenden Schritte, das Problem zu beheben:
{: tsResolve}

  * Wiederholen Sie die Aktion.
    * Laden Sie die Seite neu, indem Sie auf der Tastatur die Taste F5 drücken oder auf die Schaltfläche zum **Aktualisieren** der Anzeige klicken. Wenn dieser Schritt nicht funktioniert, löschen Sie den Inhalt des Cachespeichers und die Cookies und laden Sie die Seite anschließend erneut.
    * Verwenden Sie einen anderen Browser.
    * Starten Sie Router, Modem und Computer erneut. Durch einen Warmstart dieser Geräte können verschiedene Fehler bereinigt werden, die zu dem Fehler 502 führen.
  * Warten Sie und wiederholen Sie den Vorgang zu einem späteren Zeitpunkt. In Bezug auf den Internet-Service-Provider oder die {{site.data.keyword.cloud_notm}}-Services kann es zu vorübergehenden Problemen kommen. Warten Sie, bis die vorübergehenden Probleme gelöst wurden.
  * Wenn das Problem dennoch bestehen bleibt, wenden Sie sich an den {{site.data.keyword.cloud_notm}}-Support. Weitere Informationen finden Sie unter [Kontaktaufnahme mit dem {{site.data.keyword.cloud_notm}}-Support ](/docs/get-support?topic=get-support-getting-customer-support){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").

## Android-Apps empfangen keine {{site.data.keyword.mobilepushshort}}
{: #ts_push}
{: troubleshoot}

In bestimmten Regionen, in denen nicht auf Google zugegriffen werden kann, empfangen Android-Apps keine Benachrichtigungen, die Sie über den IBM {{site.data.keyword.mobilepushshort}}-Service senden. In diesem Fall besteht die Ausweichlösung darin, Drittanbieterservices zu verwenden.

Sie können einen {{site.data.keyword.mobilepushshort}}-Service für Ihre {{site.data.keyword.cloud_notm}}-App verwenden und eine Nachricht an die registrierten Geräte senden. Jedoch können Apps, die für Android entwickelt wurden, Ihre Benachrichtigungen in bestimmten Regionen nicht empfangen.
{: tsSymptoms}

Der IBM {{site.data.keyword.mobilepushshort}}-Service nutzt den GCM-Service (Google Cloud Messaging), um Benachrichtigungen an mobile Apps zu versenden, die unter Android entwickelt wurden. Zur Aktivierung der Android-Apps für den Empfang von Benachrichtigungen muss der GCM-Service für die mobilen Apps zugänglich sein. In Regionen, in denen der GCM-Service nicht von den Android-Apps erreicht werden kann, können die Android-Apps keine {{site.data.keyword.mobilepushshort}} empfangen.
{: tsCauses}

Verwenden Sie als Ausweichlösung Services von Drittanbietern, die nicht vom GCM-Service abhängig sind, z. B. [Pushy ](https://pushy.me){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link"), [getui ](http://www.getui.com/){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") oder [jpush ](https://www.jpush.cn/){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").
{: tsResolve}

## Anzeigen von Doppelbytezeichen nach Push-Operation für Apps in {{site.data.keyword.cloud_notm}} nicht ordnungsgemäß
{: #ts_doublebytes}
{: troubleshoot}

Es kann vorkommen, dass Doppelbytezeichen nicht ordnungsgemäß angezeigt werden, wenn die Unicode-Unterstützung für das Servlet oder die JSP-Dateien nicht ordnungsgemäß konfiguriert wurde.

Wenn eine Anwendung per Push-Operation an {{site.data.keyword.cloud_notm}} übertragen wird, werden Doppelbytezeichen, die in der App angegeben sind, nicht ordnungsgemäß angezeigt.
{: tsSymptoms}

Das Problem kann auftreten, wenn die Unicode-Unterstützung für das Servlet oder die JSP-Dateien nicht ordnungsgemäß konfiguriert ist.
{: tsCauses}

Sie können den folgenden Code im Servlet oder der JSP-Datei verwenden:
{: tsResolve}

  * In der Servletquellendatei:
  ```java
	response.setContentType("text/html; charset=UTF-8");
	```
  {: codeblock}

  * In der JSP-Datei
  ```jsp
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```
  {: codeblock}

## Bereitstellung von Node.js-Apps nicht möglich
{: #ts_nodejs_deploy}
{: troubleshoot}

Bei der Aktualisierung einer Node.js-App oder bei der Bereitstellung einer Node.js-App in {{site.data.keyword.cloud_notm}} kann es zu Problemen kommen.

Bei der Aktualisierung einer Node.js-App oder bei der Bereitstellung einer Node.js-App in {{site.data.keyword.cloud_notm}} wird möglicherweise eine der folgenden Fehlernachrichten angezeigt:
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
     * Verwenden Sie die Befehlszeilenschnittstelle von Cloud Foundry. Beispiel:
      ```
		  ibmcloud cf push MyUniqueNodejs01 -p app_path -c "node app.js"
		  ```
      {: codeblock}

    * Mithilfe der Datei [package.json ](https://www.npmjs.com/package/jsonfile){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link"). Beispiel:
	    ```json
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
	```json
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

Weitere Tipps zu Node.js-Apps finden Sie unter [Tipps für Node.js-Anwendungen ](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").

## Konfigurationsfehler in Datei `server.xml` nach Import einer {{site.data.keyword.cloud_notm}} Liberty-App in Eclipse
{: #ts_eclipse}
{: troubleshoot}

Wenn in der Datei `server.xml` nach dem Import einer {{site.data.keyword.cloud_notm}} Liberty-App in Eclipse Konfigurationsfehler angezeigt werden, kann es erforderlich sein, die Datei `server.xml` aus dem Projekt zu entfernen.

Nach dem Import einer {{site.data.keyword.cloud_notm}} Liberty-App in Eclipse werden in der Eclipse-Ansicht 'Fehler' Konfigurationsfehler in der Datei `server.xml` angezeigt.
{: tsSymptoms}

Das Liberty-Buildpack verwendet die Datei `server.xml` zum Konfigurieren der App und generiert die Datei `runtime-vars.xml`, wenn die Liberty-App per Push-Operation an {{site.data.keyword.cloud_notm}} übertragen wird. Wenn Sie die App in Eclipse importieren, ist die Datei `runtime-vars.xml` in der lokalen Umgebung nicht vorhanden.
{: tsCauses}

Sie können dieses Problem durch Entfernen der Datei server.xml aus dem Projekt beheben. Vom Buildpack wird die Datei `server.xml` dynamisch erstellt, wenn Sie die App mit einer Push-Operation als WAR-App übertragen. Weitere Informationen finden Sie unter [Liberty for Java](/docs/runtimes/liberty?topic=liberty-liberty_runtime#liberty_runtime).
{: tsResolve}

## Staging für Apps mit angepassten Buildpacks nicht möglich
{: #ts_bp_compilation}
{: troubleshoot}

Es kann vorkommen, dass eine App unter {{site.data.keyword.cloud_notm}} nicht unter Verwendung eines angepassten Buildpacks bereitgestellt werden kann, wenn die Scripts im Buildpack keine ausführbaren Dateien sind.

Wenn Sie eine App unter {{site.data.keyword.cloud_notm}} unter Verwendung eines angepassten Buildpacks bereitstellen, kann es vorkommen, dass die Fehlernachricht `The application failed to stage, so there are no instances to display.` (Anzeigen der Instanzen nicht möglich, da Staging der Anwendung fehlgeschlagen ist) angezeigt wird.
{: tsSymptoms}

Dieses Problem kann auftreten, wenn Scripts, wie zum Beispiel die Scripts zum Identifizieren, Kompilieren und Freigeben, nicht ausgeführt werden können.
{: tsCauses}

Mit dem Befehl [Git update ](http://git-scm.com/docs/git-update-index){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") können Sie die Berechtigung für jedes einzelne Script in 'ausführbar' ändern. Sie können zum Beispiel `git update --chmod=+x script.sh` eingeben.
{: tsResolve}

## Bereitstellen einer App über die Delivery Pipeline in IBM {{site.data.keyword.cloud_notm}} Continuous Delivery nicht möglich
{: #ts_devops_to_bm}
{: troubleshoot}

 Es kann vorkommen, dass eine App nicht unter Verwendung der {{site.data.keyword.deliverypipeline}} in {{site.data.keyword.contdelivery_short}} bereitgestellt werden kann, wenn die Datei `manifest.yml` nicht in der App vorhanden ist.

 Wenn Sie eine App unter Verwendung der {{site.data.keyword.deliverypipeline}} in {{site.data.keyword.contdelivery_short}} bereitstellen, kann die Fehlernachricht `Unable to detect a supported application type` (Ermittlung eines unterstützten Anwendungstyps fehlgeschlagen) angezeigt werden.
 {: tsSymptoms}

 Dieses Problem kann auftreten, weil für die Pipeline die Datei `manifest.yml` zum Bereitstellen einer App in {{site.data.keyword.cloud_notm}} erforderlich ist.
 {: tsCauses}

 Zum Beheben dieses Problems müssen Sie die Datei `manifest.yml` erstellen. Weitere Informationen zum Erstellen der Datei `manifest.yml` finden Sie im [Abschnitt zum Anwendungsmanifest](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest).
 {: tsResolve}

## Speicherkontingent überschritten
{: #exceed_quota}

Wenn die Build- oder Bereitstellungsjobs fehlschlagen und die folgende Nachricht angezeigt wird, können Sie Ihre Images mit den folgenden Befehlszeilenschnittstellenbefehlen löschen. `Status: unauthorized: You have exceeded your storage quota. Delete one or more images, or review your storage quota and pricing plan.` (Status: unberechtigt: Sie haben das Speicherkontingent überschritten. Löschen Sie ein oder mehrere Images oder überprüfen Sie Ihr Speicherkontingent und den Preistarif.)

* Installieren Sie, falls nicht bereits geschehen, die [{{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle](/docs/cli?topic=cloud-cli-ibmcloud-cli).
* Melden Sie sich bei {{site.data.keyword.cloud_notm}} mit `ibmcloud login` an und verweisen Sie auf den Bereich, in dem Sie sich befinden.
* Listen Sie Ihre Images mit `ibmcloud cr images` auf.
* Löschen Sie alle nicht verwendeten Images mit dem Befehl `ibmcloud cr image-rm <respository>:<tag>`.
* Führen Sie den fehlgeschlagenen Build- oder Bereitstellungsjob erneut aus.

## Zugriff auf Kubernetes-Protokolle
{: #access_kube_logs}

Wenn die Anwendung nicht ausgeführt wird und Sie nicht auf den Statusendpunkt zugreifen können, versuchen Sie, die Protokolle im Cluster anzuschauen.
* Installieren Sie, falls nicht bereits geschehen, die [{{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle](/docs/cli?topic=cloud-cli-ibmcloud-cli).
* Melden Sie sich bei {{site.data.keyword.cloud_notm}} mit `ibmcloud login` an und verweisen Sie auf den Bereich, in dem Sie sich befinden.
* Listen Sie Ihre Cluster mit `ibmcloud cs clusters` auf.
* Zeigen Sie mit `ibmcloud cs cluster-config<cluster-name>` auf Ihren entsprechenden Cluster.
* Exportieren Sie die aufgelistete Umgebungsvariable.
* Zeigen Sie Ihre Pods mit `kubectl get pods` an. Wenn Sie `kubectl` installieren müssen, finden Sie weitere Informationen in [kubectl installieren und einrichten](https://kubernetes.io/docs/tasks/tools/install-kubectl/){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").
* Sie können die Protokolle in Ihrer App anzeigen, indem Sie `kubectl logs <pod-name> verwenden.`

## Starten von `Docker` schlägt mit der Nachricht "Datei nicht gefunden" fehl.
{: #docker_not_found}
{: troubleshoot}

Wenn Sie versuchen, Docker zu starten, wird die folgende Fehlernachricht angezeigt:
{: tsSymptoms}

```
Beim Erstellen des Docker-Images ist der Fehler 'Exec: Ausführbare Datei "docker" nicht in $PATH gefunden' aufgetreten.
```
{: screen}

Der Docker-Client ist nicht installiert oder er ist installiert, aber nicht gestartet.
{: tsCauses}

Stellen Sie sicher, dass [Docker](https://docs.docker.com/install/){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") installiert ist, und starten Sie Docker.
{: tsResolve}

## Erstellen einer App schlägt mit einem Docker-Fehler fehl.
{: #build_error}
{: troubleshoot}

Beim Erstellen einer App mit dem Befehl `ibmcloud dev build` schlägt dieser mit einem Docker-Fehler in Bezug auf den Benutzernamen/das Kennwort fehl. 
{: tsSymptoms}

Die für die Authentifizierung verwendeten Docker Hub-Berechtigungsnachweise sind nicht korrekt. 
{: tsCauses}

Melden Sie sich im Docker-Client von Docker Hub ab.
{: tsResolve}
