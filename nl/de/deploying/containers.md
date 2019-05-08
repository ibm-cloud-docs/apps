---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-23"

keywords: apps, deploying apps, containers, kubernetes, docker, clusters, devops toolchain, deployment, kube

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Container mit Kubernetes verwenden
{: #containers-kube}

Als Einstieg in {{site.data.keyword.containershort}} können Sie hoch verfügbare Apps in Docker-Containern bereitstellen, die in Kubernetes-Clustern ausgeführt werden. Verwalten Sie die Anwendungsentwicklung im Team mithilfe von Git und verwenden Sie dann die DevOps-Toolchain, um die Bereitstellung der App in Kubernetes zu verwalten.
{: shortdesc}

Bei Containern handelt es sich um eine Standardmethode zum Packen von Apps und allen zugehörigen Abhängigkeiten, die ein nahtloses Verschieben der Apps zwischen Umgebungen ermöglicht. Im Gegensatz zu virtuellen Maschinen wird bei Containern das Betriebssystem nicht in das Paket einbezogen. In Containern werden nur der App-Code, die Laufzeit, die Systemtools, die Bibliotheken und die Einstellungen gepackt. Container sind einfacher, portierbarer und effizienter als virtuelle Maschinen.

[Einführung in {{site.data.keyword.containershort_notm}}](/docs/containers?topic=containers-getting-started) enthält weitere Informationen zum Service.

## Bereitstellungen konfigurieren
{: #config-deploy}

Wenn Sie Back-End- oder Web-Serving-Apps erstellen, können Sie sie im {{site.data.keyword.containershort_notm}}-Service bereitstellen, der die Kubernetes-Umgebung verwendet.

1. Stellen Sie die App in der Cloud bereit, indem Sie eine automatisiert Cloud-Pipeline einrichten.
2. Klicken Sie auf **Continuous Delivery konfigurieren**.
3. Wählen Sie **IBM Kubernetes-Service** als Ziel aus. Sie müssen [einen Cluster erstellen ](https://{DomainName}/kubernetes/catalog/cluster/create){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link"), falls noch kein Cluster vorhanden ist.
4. Rufen Sie nach dem Abschluss der Bereitstellung Ihre Live-App in der Cloud auf, indem Sie die URL aus den Protokollen der Bereitstellungstage in der Delivery Pipeline verwenden. Die letzte IP-Adresse mit einem Port ist die neue Startseite Ihrer App, z. B. 169.60.133.124:32355.

## Services binden
{: #bind-services}

Beim Erstellen der Toolchain werden die Services, die Sie Ihrer App zugeordnet haben, an den Kubernetes-Cluster gebunden, indem geheime Kubernetes-Schlüssel verwendet werden. Geheime Schlüssel dienen zur Verwaltung der Serviceberechtigungsnachweise außerhalb der aktiven App. Die App liest die geheimen Schlüssel und ruft dann die Werte ab, die zum Starten der Ausführung benötigt werden. Das Binden von Services ermöglicht die Bereitstellung der App in einer anderen Kubernetes-Umgebung, die möglicherweise {{site.data.keyword.cloud}}-Serviceinstanzen auf Produktionsniveau verwendet.

Wenn Sie den Service oder die geheimen Schlüssel löschen, müssen Sie sie manuell erneut binden oder Sie müssen die Toolchain löschen und erneut erstellen.
{: tip}

Weitere Informationen finden Sie in [Geheime Schlüssel ](https://kubernetes.io/docs/concepts/configuration/secret/){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link").

## Entwicklung starten
{: #dev}

1. Rufen Sie das neue Online-Git-Repository über die Toolchain auf und beginnen Sie mit der Bearbeitung des Codes. Zum Anzeigen der Toolchain klicken Sie auf **Toolchain anzeigen**.
2. Greifen Sie auf das Git-Repository, in dem der Code erstellt wurde, zu, indem Sie das Repository in der lokalen Umgebung klonen.
3. Öffnen Sie das Projekt mit der bevorzugten IDE.

## Build und Bereitstellung: Toolchain verwenden
{: #bulid-deploy-tc}

Die Toolchain enthält die Build-Stage und die Bereitstellungsstage.

### Build-Stage
{: #build-stage}
Die Build-Stage wird ausgelöst, wenn der Befehl `git push` für das Git-Repository ausgeführt wird. Die Stage in der Pipeline löst den Build eines Docker-Image aus und stellt das Image in die Container-Registry.

Weitere Informationen finden Sie in [Einführung in IBM Cloud Container Registry](/docs/services/Registry?topic=registry-getting-started).

### Bereitstellungsstage
{: #deploy-stage}

Die Bereitstellungsstage ruft das neueste Image aus {{site.data.keyword.registryshort_notm}} ab und stellt es dann mithilfe eines Helm-Diagramms im Kubernetes-Cluster bereit. Das Helm-Diagramm wurde bei der Bereitstellung in der Cloud zur App hinzugefügt. Helm-Diagramme vereinfachen die Verwaltung der Bereitstellungsschritte des gepackten Container-Image.

Weitere Informationen finden Sie in [Diagramme ](https://docs.helm.sh/developing_charts/){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link").

{{site.data.keyword.cloud_notm}} unterstützt eine Reihe von [vorkonfigurierten Helm-Diagrammen ](https://{DomainName}/kubernetes/solutions/helm-charts){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link").

## App-Sicherheit überprüfen
{: #sec}

{{site.data.keyword.containershort_notm}} unterstützt das Scannen der gepackten Container-Images zur Überprüfung auf Sicherheitslücken. Das Scannen zu Sicherheitszwecken ist für die Unterstützung von auf Unternehmen abgestimmten Anwendungen unverzichtbar.

Rufen Sie das [Image-Repository ](https://{DomainName}/kubernetes/registry/main/private){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") für die Container auf, um eine Überprüfung auf potenzielle Sicherheitslücken durchzuführen.
