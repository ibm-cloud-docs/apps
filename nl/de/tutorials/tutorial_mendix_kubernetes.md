---

copyright:
  years: 2018
lastupdated: "2018-11-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Ihre Mendix-App auf {{site.data.keyword.containerlong_notm}} bereitstellen
{: #getting-started}

Standardmäßig werden Mendix-Anwendungen, die Zielbereitstellungen für {{site.data.keyword.containerlong}} sind, in einem Auswertungsmodus konfiguriert. Dieser Modus ermöglicht Ihnen, in kurzer Zeit mit der Anwendungserstellung zu beginnen und diese Anwendung in der Cloud bereitzustellen. Es werden jedoch weder Datenpersistenz noch erweiterte Kubernetes-Konfigurationen konfiguriert. Dieses Lernprogramm führt Sie durch die Konfiguration einer Produktionsumgebung, indem Sie mit dem {{site.data.keyword.cos_full_notm}}-Service eine persistente Speichermenge in Kubernetes definieren.
{: shortdesc}

## Vorbereitende Schritte
{: #prerequisites}

- Ihre Mendix-App erstellen. Weitere Informationen finden Sie unter [Mendix-Apps erstellen](/docs/apps/tutorials/tutorial_mendix_getting_started.html).
- Installieren Sie die [{{site.data.keyword.dev_cli_notm}}-CLI (Command-Line Interface)](/docs/cli/index.html), die die {{site.data.keyword.containershort_notm}}-CLI umfasst.
- Melden Sie sich bei der `ibmcloud`-CLI an und konfigurieren Sie `kubectl` für den [Zugriff auf die Kubernetes-Cluster](/docs/containers/cs_tutorials.html#cs_cluster_tutorial_lesson3).

## Cloud Object Storage-Serviceinstanz erstellen
{: #cloud-object-storage}

Führen Sie beginnend von der Detailseite Ihrer Anwendung die folgenden Schritte aus:
1. Klicken Sie auf **Ressource hinzufügen**.
2. Wählen Sie **Speicher** aus und klicken Sie auf **Weiter**.
3. Wählen Sie anschließend die Option **Cloudobjektspeicher** aus und klicken Sie auf **Weiter**.
4. Ihnen werden die Preistarife für Ihre {{site.data.keyword.cos_full_notm}}-Instanz angezeigt. Wählen Sie den Preistarif aus, der Ihren Anforderungen am besten entspricht, und klicken Sie dann auf **Erstellen**, um eine Instanz des {{site.data.keyword.cos_full_notm}}-Service zur Verwendung mit Ihrer Mendix-Anwendung zu erstellen.

  Wenn Sie lieber eine vorhandene Instanz des {{site.data.keyword.cos_full_notm}}-Service verwenden, klicken Sie auf **Ressource hinzufügen** und wählen eine vorhandene Instanz für Ihre Anwendung aus.
  {: tip}

## Speicherbucket erstellen
{: #storage-bucket}

Sobald eine Instanz des {{site.data.keyword.cos_full_notm}}-Service Ihrer Mendix-Anwendung zugeordnet ist, müssen Sie einen Speicherbucket erstellen, in dem Daten gespeichert werden können. Um einen Bucket zu erstellen, klicken Sie für die {{site.data.keyword.cos_full_notm}}-Instanz auf **...** und wählen **Dashboard öffnen** aus.  

Das {{site.data.keyword.cos_full_notm}}-Service-Dashboard wird in einem neuen Fenster auf der Registerkarte **Buckets** angezeigt. Klicken Sie auf **Bucket erstellen** und befolgen Sie die Schritte zum Erstellen eines Buckets unter Verwendung eines eindeutigen Namens. Erstellen Sie im Rahmen dieses Lernprogramms einen Bucket mit dem Namen `my-mendix-bucket`.

## Persistenten Speicher konfigurieren
{: #kubernetes-storage}

Folgen Sie den Anweisungen in der Dokumentation zum [Speichern von Daten in {{site.data.keyword.cos_full_notm}}](/docs/containers/cs_storage_cos.html). Innerhalb Ihres Kubernetes-Clusters werden ein `PersistentVolumeClaim` und ein `PersistentVolume` erstellt und können von der PostGres-Datenbankinstanz, die in Ihrem Cluster ausgeführt wird, als Teil der Mendix-Anwendung verwendet werden. Stellen Sie sicher, dass Sie die `PersistentVolumeClaim` mithilfe des Buckets `my-mendix-bucket` wie im vorherigen Schritt beschrieben erstellen und überprüfen Sie den Namen `PersistentVolumeClaim` für die Verwendung im nächsten Schritt.

## Datei `postgres-deployment.yaml` bearbeiten
{: #postgres-deployment}

Sobald ein persistenter Datenträger für Ihren Kubernetes-Cluster konfiguriert ist, besteht der nächste Schritt darin, die PostGres-Datenbankbereitstellung, die in Ihrem Cluster ausgeführt wird, zu ändern. Zuerst müssen Sie die Dateien im Git-Repository bearbeiten, die als Teil der IBM DevOps-Toolchain-Integration erstellt wurden. Um das Git-Repository zu finden, rufen Sie die Detailseite der Anwendung auf und klicken in der Kachel mit den **Bereitstellungsdetails** auf den Git-URL-Link.  

Sie können das Git-Repository entweder auf Ihre lokale Maschine klonen oder die folgenden Änderungen im Online-Editor vornehmen. Öffnen Sie die Datei `chart/{app name}/templates/postgres-deployment.yaml` und ersetzen Sie `{app name}` durch den Namen Ihrer Mendix-Anwendung. Die Datei verfügt standardmäßig nicht über die Einträge `volumeMount` oder `volumes`, sodass alle Daten speicherintern innerhalb des aktiven Bereitstellungspods gespeichert werden. Sie müssen beide Einträge, `volumeMount` und `volumes`, zur Kubernetes-Datei `deployment.yaml` hinzufügen, damit Daten im {{site.data.keyword.cos_full_notm}}-Bucket gespeichert werden und beim Neustart des Pods nicht verloren gehen. 

Das folgende Beispiel `postgres-deployment.yaml` enthält die Einträge `volumeMount` und `volumes`.  
```yaml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: "{appname}-postgres"
spec:
  replicas: 1
  template:
    metadata:
      labels:
        service: "{appname}-postgres"
    spec:
      containers:
        - name: "{appname}-postgres"
          image: postgres:10.1
          ports:
            - containerPort: 5432
          env:
            - name: POSTGRES_DB
              value: db0
            - name: POSTGRES_USER
              value: mendix
            - name: POSTGRES_PASSWORD
              value: mendix
          volumeMounts:
            - mountPath: "/var/lib/postgresql/data"
              name: "mendix-data"
      volumes:
        - name: mendix-data
          persistentVolumeClaim:
            claimName: {pvc-name}
```

Stellen Sie sicher, dass `{pvc-name}` durch den Namen Ihres `PersistentVolumeClaim` aus dem vorherigen Schritt ersetzt wird und achten Sie darauf, dass Sie den Namen Ihrer App, die bereits in der Datei innerhalb Ihres Git-Repositorys festgelegt ist, nicht überschreiben. Übertragen Sie anschließend Ihre Änderungen zurück in das Git-Repository.

## Erneute Bereitstellung
{: #redeploy}

Sobald die Änderungen an der Datei `postgres-deployment.yaml` wieder im Repository festgeschrieben sind, wird eine neue Ausführung der DevOps-Pipeline automatisch ausgelöst. Dabei wird jedoch erneut die Standardanwendung bereitgestellt. Sie müssen die neueste Version der Mendix-Anwendung erneut bereitstellen, damit die neueste Version Ihrer Anwendung mit den neuesten persistenten Änderungen am Datenträger bereitgestellt wird.

Um die erneute Bereitstellung auszuführen, wechseln Sie auf die Seite mit den Anwendungsdetails und klicken auf **Anwendung bereitstellen** in der Kachel mit den **Bereitstellungsdetails**. Wenn die Bereitstellung innerhalb der DevOps-Toolchain mit einer Nachricht fehlschlägt, die besagt, dass die Datei `.mda` der Anwendung nicht gefunden werden konnte, dann müssen Sie diese Datei erneut aus Mendix exportieren. Sie können die Datei aus der Desktopanwendung Mendix Modeler exportieren oder durch Klicken auf die Option zum **Bearbeiten in Mendix**. Wechseln Sie dann innerhalb der Mendix-Webschnittstelle zum Abschnitt **Umgebungen** und befolgen Sie die Schritte, nachdem Sie auf die Option **Paket vom Teamserver erstellen** geklickt haben. Sobald Ihre Anwendung aus Mendix exportiert wurde, wechseln Sie auf die Detailseite der Anwendung und klicken erneut auf **Anwendung bereitstellen**. Die zuletzt exportierte Anwendung wird in Ihrem Kubernetes-Cluster mithilfe der DevOps-Toolchain von {{site.data.keyword.cloud_notm}} bereitgestellt. Sobald die Bereitstellung erfolgreich abgeschlossen wurde, kann Ihre Anwendung produktiv genutzt werden.

## Zusätzliche Informationen
{: #additional-information}

Weitere Details zur Architektur bei der Ausführung von Mendix-Anwendungen in Kubernetes-Umgebungen finden Sie im Abschnitt über das Ausführen von Mendix auf Kubernetes [Run Mendix on Kubernetes](https://docs.mendix.com/developerportal/deploy/run-mendix-on-kubernetes) in der Benutzerdokumentation von Mendix.
