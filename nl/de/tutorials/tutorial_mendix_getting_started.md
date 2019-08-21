---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-03"

keywords: apps, Mendix, starter kit, developer tools, Mendix app, create mendix app

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note .note}

# Apps mit Mendix erstellen
{: #create-mendix}

Mendix ist eine Low-Code-Entwicklungsumgebung und ein Toolset, dass Ihnen dabei hilft, Anwendungen mit mehreren Geräten schneller und mit weniger Entwicklungsressourcen, die in {{site.data.keyword.cloud}} ausgeführt werden, zu liefern. Durch die Auswahl eines Mendix-Low-Code-Starter-Kits werden Sie durch die Kontoeinrichtung auf der Mendix-Plattform, das Starten Ihres Projekts und das Auswählen Ihres Bereitstellungsziels (Cloud Foundry oder Ihr Kubernetes-Cluster) geführt.
{: shortdesc}

## Starter-Kit auswählen
{: #starterkit-mendix}

1. Klicken Sie im [{{site.data.keyword.cloud_notm}}-App-Service-Dashboard ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") auf **Einstieg**.
2. Wählen Sie ein Mendix-Low-Code-Starter-Kit aus einer der folgenden Kategorien aus:
  * [Mobile](https://{DomainName}/developer/appservice/starter-kits/mendix-mobile-app){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")
  * [Watson Web oder Mobile App ](https://{DomainName}/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")
  * [Web-App ](https://{DomainName}/developer/appservice/starter-kits/mendix-web-app){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")
3. Klicken Sie auf **Anwendung erstellen**.
4. Geben Sie auf der Seite **App-Details** den Namen Ihrer App und optional Tags an, um Ihre App zu klassifizieren. Weitere Informationen finden Sie in [Mit Tags arbeiten](/docs/resources?topic=resources-tag).
5. Klicken Sie auf **Erstellen**.

## Autorisieren Sie IBM, um Ihr Projekt auf Mendix-und Linkkonten zu erstellen
{: #link-mendix-account}

Wenn Sie Mendix mit {{site.data.keyword.cloud_notm}} noch nicht verwenden, werden Sie zur Mendix-Plattform geführt, um sich bei {{site.data.keyword.cloud_notm}} anzumelden und zu autorisieren, um ein neues Projekt in Ihrem Namen auf der Mendix-Plattform zu erstellen. Dieses Projekt wird mit {{site.data.keyword.cloud_notm}} verknüpft, sodass Bereitstellungen automatisch an {{site.data.keyword.cloud_notm}} weitergeleitet werden.

1. Wenn diese Nachricht angezeigt wird, klicken Sie auf **Konto verknüpfen**.
  ```
  "To complete app creation, a Mendix user account is required. Would you like to link your account now?" (Ein Mendix-Benutzer ist erforderlich, um die App-Erstellung abzuschließen. Möchten Sie Ihr Konto jetzt verknüpfen?)
  ```
  {: screen}

2. Wählen Sie auf der Bestätigungsseite von Mendix **I agree to the Mendix Privacy Policy and Terms** (Ich stimme den Datenschutzrichtlinie und Bedingungen von Mendix zu) aus und klicken Sie auf **Bestätigen**.
3. Wenn Sie dazu aufgefordert werden, geben Sie Ihre E-Mail-Adresse, Ihr Kennwort und Ihr Land an und klicken auf **Erstellen**.
4. Klicken Sie auf der Seite, mit der Sie Benutzer für den **Zugriff auf Ihr Mendix-Konto berechtigen**, auf **Berechtigen**.

Nachdem die Autorisierung abgeschlossen ist, kehrt Ihr Browser zur Mendix-App zurück, die Sie erstellen. Die Seite **Bereitstellungsziel auswählen** wird angezeigt.

## Bereitstellungsziel für Ihre Mendix-App auswählen
{: #select-deployment}

1. Wählen Sie auf der Seite **Bereitstellungsziel auswählen** Cloud Foundry oder einen Ihrer Kubernetes-Cluster aus, die in {{site.data.keyword.cloud_notm}} ausgeführt werden. Wenn Ihr Konto über Zugriff auf {{site.data.keyword.cfee_full_notm}} verfügt, können Sie entweder den Cloud Foundry-Bereitstellertyp **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)** oder den Cloud Foundry-Bereitstellertyp **[Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)** auswählen, mit dem Sie isolierte Umgebungen für das Hosting von Cloud Foundry-Apps exklusiv für Ihr Unternehmen erstellen und verwalten können.
2. Optional. Wenn Sie keinen Kubernetes-Cluster haben, können Sie jetzt einen erstellen.
3. Wählen Sie auf der Seite **Toolchain konfigurieren** Ihre Region und Ihre Ressourcengruppe aus und klicken Sie anschließend auf **Erstellen**.

Es wird eine DevOps-Toolchain erstellt. Die Toolchain integriert Ihr Mendix-Projekt auf der Mendix-Plattform in Ihre {{site.data.keyword.cloud_notm}}-Umgebung. Eine Standard-App wird in Ihrem Bereitstellungsziel bereitgestellt, damit Sie überprüfen können, ob die App nach Ende der DevOps-Toolchain erfolgreich bereitgestellt wurde.

Die Mendix Cloud Foundry-Bereitstellungen benötigen den PostGRES-Datenbankservice, der kein Lite-Tier aufweist. Wenn Sie die Mendix-Starter-Kits mit einem Lite-Konto evaluieren möchten, können Sie einen Test-Kubernetes-Cluster als Ziel verwenden.
{: tip}

Wenn Sie für die Bereitstellung einen Kubernetes-Cluster ausgewählt haben, erfahren Sie im [Lernprogramm für Mendix-Kubernetes](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube) mehr über die Konfiguration Ihres Clusters für den Produktionseinsatz.

## Mendix-Entwicklungs- und Bereitstellungslebenzyklus fortsetzen
{: #dev-lifecycle-mendix}

Mendix ist eine Low-Code-Authoring-Umgebung. Der Entwicklungszyklus erfordert, dass Sie Ihr Projekt in der Desktop-App Mendix Modeler öffnen.

1. Klicken Sie in Ihrer {{site.data.keyword.cloud_notm}}-App auf die Option zum **Bearbeiten in Mendix**.
2. Klicken Sie im Mendix-Webportal auf die Option zum **Bearbeiten in Desktop Modeler**.
  Die Mendix-App wird im Desktop-Modellierungsprogramm geöffnet.
3. Bearbeiten Sie Ihre Mendix-App und speichern Sie Ihre Änderungen.
4. Verwenden Sie das Menü **Ausführen** der Mendix-App Desktop Modeler und wählen Sie die Option **Ausführen** aus.
  Das Bereitstellungspaket wird erstellt und in Mendix hochgeladen. Nachdem das Bereitstellungspaket erstellt wurde, können Sie Ihre App in {{site.data.keyword.cloud_notm}} bereitstellen.
5. Um Ihre Mendix-App bereitzustellen, wechseln Sie wieder auf Ihre Seite **App-Details** unter {{site.data.keyword.cloud_notm}} und klicken auf **Bereitstellen**.
  Mit dieser Aktion wird die DevOps-Toolchain Ihrer App gestartet, die die letzten Bereitstellungen von Mendix abruft und in Ihrer Zielumgebung bereitstellt. Nachdem die Bereitstellung abgeschlossen ist, wird die aktuellste Version Ihrer App automatisch gestartet und ist dann verfügbar.

Alle Mendix-Apps müssen in {{site.data.keyword.cloud_notm}} durch Klicken auf **Continuous Delivery konfigurieren** auf der Seite **App-Details** unter {{site.data.keyword.cloud_notm}} bereitgestellt werden. Rufen Sie Mendix-Toolchains nicht manuell über die IBM DevOps-Schnittstelle auf. Das manuelle Starten von Toolchains über die DevOps-Schnittstelle führt zu fehlerhaften Bereitstellungen, da die erforderlichen Metadaten fehlen, die für Mendix-Bereitstellungen erforderlich sind. Abhängig vom Status Ihrer App kann entweder ein Fehler während des Starts der DevOps-Toolchain oder ein Fehler in der bereitgestellten App auftreten.

Wenn Sie eine Toolchain manuell starten und einen Fehler bemerken, können Sie Ihre App-Bereitstellung durch Klicken auf **Continuous Delivery konfigurieren** auf der Seite **App-Details** unter {{site.data.keyword.cloud_notm}} wiederherstellen. Diese Aktion löst einen vollständigen DevOps-Ablauf für die Mendix-App aus, wobei die erforderlichen Metadaten enthalten sind.
{: tip}

## Optional: {{site.data.keyword.cos_full_notm}} konfigurieren 
{: #mendix-cos}

Für manche Benutzer kann es sinnvoll sein, ihre bereitgestellte Mendix-App so zu konfigurieren, dass {{site.data.keyword.cos_full}} für den persistenten Speicher und Dateiuploads verwendet wird. {{site.data.keyword.cos_full_notm}} ist ein mit S3 kompatibler Objektspeicherservice. Um den mit S3 kompatiblen Dateispeicher nutzen zu können, müssen Mendix-Apps die folgenden Umgebungsvariablen definieren, damit ein Zugriff auf eine {{site.data.keyword.cos_full_notm}}-Instanz erfolgen kann, nachdem Continuous Delivery konfiguriert wurde:

* `S3_ACCESS_KEY_ID` - Der S3-Schlüssel, der Bestandteil der {{site.data.keyword.cos_full_notm}}-Berechtigungsnachweise ist.
* `S3_SECRET_ACCESS_KEY` - Der geheime S3-Schlüssel, der Bestandteil der {{site.data.keyword.cos_full_notm}}-Berechtigungsnachweise ist.
* `S3_BUCKET_NAME` - Das S3-Speicherbucket.
* `S3_ENDPOINT` - Der S3-Speicherendpunkt.
* `S3_USE_V2_AUTH` - Der Wert ist `true`

Weitere Informationen zu {{site.data.keyword.cos_full_notm}}-Buckets und -Schlüsseln finden Sie in der [API-Dokumentation von {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-gs-dev). Zusätzliche Angaben über regionale und regionsübergreifende Endpunktwerte enthalten die [{{site.data.keyword.cos_full_notm}}-Docs](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints). Mehr über die Mendix-Unterstützung für mit S3 kompatiblen Speicher erfahren Sie in der [Dokumentation für das Mendix-Buildpack](https://github.com/mendix/cf-mendix-buildpack#s3-settings){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link").

### {{site.data.keyword.cos_full_notm}}-Einstellungen für Cloud Foundry-Apps
{: cos-cfapps}

Führen Sie für Cloud Foundry-Bereitstellungen die folgenden Schritte aus:

1. Legen Sie mit dem Befehl `cf set-env` die folgenden Umgebungsvariablen für Cloud Foundry fest:

  ```
    ibmcloud cf set-env <IHRE_APP> S3_ACCESS_KEY_ID <IHR_SCHLÜSSEL>
    ibmcloud cf set-env <IHRE_APP> S3_SECRET_ACCESS_KEY <IHR_GEHEIMER_SCHLÜSSEL>
    ibmcloud cf set-env <IHRE_APP> S3_BUCKET_NAME <IHR_BUCKET>
    ibmcloud cf set-env <IHRE_APP> S3_ENDPOINT s3.us-south.cloud-object-storage.appdomain.cloud
    ibmcloud cf set-env <IHRE_APP> S3_USE_V2_AUTH true
  ```

2. Nachdem Sie alle diese Werte angegeben haben, führen Sie für Ihre Cloud Foundry-App ein erneutes Staging durch, damit die neuen Werte angewendet werden.

  ```
    ibmcloud cf restage <IHRE_APP>
  ```

### {{site.data.keyword.cos_full_notm}}-Einstellungen für Kubernetes-Apps
{: #cos-kubeapps}

Führen Sie für Kubernetes-Bereitstellungen die folgenden Schritte aus:

1. Legen Sie die Umgebungsvariablen `S3_ACCESS_KEY_ID` und `S3_SECRET_ACCESS_KEY` als Werte für den geheimen Kubernetes-Schlüssel im Cluster fest. Weitere Informationen zum Erstellen von geheimen Kubernetes-Schlüsseln enthält die [{{site.data.keyword.containershort_notm}}-Dokumentation](/docs/containers?topic=containers-service-binding#adding_app).

2. Geben Sie neben allen vorhandenen Werten die Umgebungsvariablen als zusätzliche Umgebungsvariablen in der Datei `mendix-app.yaml` an, die sich im Ordner `chart/<appname>/templates` des Git-Repositorys befindet. Die Namen der geheimen Schlüssel müssen mit den Namen übereinstimmen, die Sie im vorherigen Schritt erstellt haben.

  ```
    env:
      - name: S3_ACCESS_KEY_ID
        valueFrom:
          secretKeyRef:
            name: "mendix-s3-key"
            key: db-endpoint
      - name: S3_SECRET_ACCESS_KEY
        valueFrom:
          secretKeyRef:
            name: "mendix-s3-secret-key"
            key: db-endpoint
      - name: S3_ENDPOINT
        value: "s3.us-south.cloud-object-storage.appdomain.cloud"
      - name: S3_USE_V2_AUTH
        value: "true"
  ```

3. Nachdem die Kubernetes-Änderungen angewendet wurden, stellen Sie Ihre App erneut bereit, indem Sie zur Seite **App-Details** navigieren und auf **Bereitstellen** klicken. 

## Nächste Schritte 
{: #next-steps-mendix}

Konfigurieren Sie Ihre App für die Bereitstellung in der Produktionsumgebung, um Ihre App in {{site.data.keyword.containerlong_notm}} bereitzustellen. Weitere Informationen enthält das [Lernprogramm für Mendix-Kubernetes](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube). 
