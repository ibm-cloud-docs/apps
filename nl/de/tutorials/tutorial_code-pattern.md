---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-30"

keywords: apps, code pattern, DevOps, toolchain, service credentials, create app code pattern, app pattern

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# App mit einem Codemuster erstellen
{: #tutorial-codepattern}

Sie können ein Codemuster verwenden, um Ihre Anwendung rasch zu erstellen und in {{site.data.keyword.cloud}} bereitzustellen. Sie können den Code entweder in GitHub anzeigen oder eine App auf {{site.data.keyword.cloud_notm}} erstellen und dort ihren Build erstellen. Außerdem können Sie dort Ihre App mithilfe einer DevOps-Toolchain automatisch bereitstellen.
{: shortdesc}

## Schritt 1. App erstellen
{: #create-codepattern}

1. Rufen Sie [IBM Developer ](https://developer.ibm.com/patterns/){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") auf und wählen Sie das gewünschte Codemuster aus. Sie können z. B. das Codemuster [MEAN-Web-App erstellen](https://developer.ibm.com/patterns/build-a-mean-web-app/){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link").

2. Lesen Sie die Beschreibung des Codemusters und zeigen Sie das GitHub-Repository und die Datei `README.md` an. Klicken Sie zum Anzeigen des Repositorys auf **Code abrufen**, sodass das GitHub-Repository für das Codemuster geöffnet wird.

3. Starten Sie die Erstellung einer App, indem Sie eine der folgenden Optionen verwenden. Mit beiden Optionen wird die Seite **App erstellen** für das Codemuster geöffnet.
    * Klicken Sie auf der Codemusterseite auf den Link zum Erstellen einer App in {{site.data.keyword.cloud_notm}}. 
    * Klicken Sie in der Datei `README.md` im GitHub-Repository auf den Link für die Verwendung eines Starter-Kits zum Erstellen der App. 

4. Benennen Sie auf der Seite **App erstellen** Ihre App, wählen Sie eine Ressourcengruppe aus, geben Sie optional Tags an und klicken Sie auf **Erstellen**. Weitere Informationen zu Tags finden Sie im Abschnitt [Mit Tags arbeiten](/docs/resources?topic=resources-tag).

  Wenn Sie zum Codemuster zurückkehren möchten, klicken Sie auf **Codemuster anzeigen**. Prüfen Sie die Datei `README.md` im Repository, um herauszufinden, ob weitere Aktionen durchgeführt werden müssen, um die App betriebsbereit zu machen.
  {: tip}

## Schritt 2. Services hinzufügen
{: #resources-codepattern}

Sie können Services, die Ihre App mit der kognitiven Leistung von Watson funktional erweitern, mobile Services oder Sicherheitsservices hinzufügen. Dieser Prozess erstellt eine Serviceinstanz, erstellt einen Ressourcenschlüssel (Berechtigungsnachweise) und stellt die Bindung an Ihre App her. Im Rahmen dieses Lernprogramms fügen Sie eine Position für die Verwaltung Ihrer Daten hinzu.

1. Klicken Sie auf der Seite **App-Details** auf **Service hinzufügen**.
2. Wählen Sie den Typ des gewünschten Service aus. 
3. Wählen Sie Ihren Preisstrukturplan aus. Eine Lite-Option ist verfügbar.
4. Klicken Sie auf **Erstellen**.

## Schritt 3. Serviceberechtigungsnachweise in Ihre Umgebung kopieren

Nachdem Sie Ihrer App einen Service hinzugefügt haben, oder wenn für Ihre App Services erforderlich sind, beachten Sie, dass die Berechtigungsnachweise für diesen Service im Feld **Berechtigungsnachweise** angezeigt werden. Sie müssen die Berechtigungsnachweise manuell in Ihre Bereitstellungsumgebung kopieren.

Weitere Informationen zum Kopieren von Berechtigungsnachweisen in Ihre Umgebung finden Sie unter [Übersicht über Berechtigungsnachweise](/docs/apps?topic=creating-apps-credentials_overview#credentials_overview).

## Schritt 4. In {{site.data.keyword.cloud_notm}} bereitstellen
{: #deploy-codepattern}

Wenn Sie ein Bereitstellungsziel auswählen, wird automatisch eine DevOps-Toolchain für Ihre App erstellt. Die Toolchain enthält eine Delivery Pipeline, die den Bereitstellungsstatus Ihrer App anzeigt. Die neu generierte App wird in ein GitLab-Repository verschoben, das Teil der Toolchain ist.

Durch das Aktivieren einer DevOps-Toolchain wird eine teambasierte Entwicklungsumgebung für Ihre App erstellt. Wenn Sie eine Toolchain erstellen, erstellt der App-Service ein Git-Repository, in dem Sie Quellcode anzeigen, die App klonen und Problemmeldungen erstellen und verwalten können. Darüber hinaus verfügen Sie über Zugriff auf eine dedizierte GitLab-Umgebung  und eine Continuous-Delivery-Pipeline. Diese sind an das Bereitstellungsziel angepasst, das Sie auswählen, ob [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) oder [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Alle über ein {{site.data.keyword.cloud_notm}}-Entwicklerdashboard erstellten Toolchains sind für die automatische Bereitstellung konfiguriert.
{: note}

Führen Sie die folgenden Schritte aus, um Ihr Bereitstellungsziel auszuwählen und Continuous Delivery zu konfigurieren:

1. Klicken Sie auf der Detailseite der App auf **Continuous Delivery konfigurieren**.
2. Wählen Sie ein Bereitstellungsziel aus. Richten Sie Ihr Bereitstellungsziel entsprechend den Anweisungen für das ausgewählte Ziel ein:
  * **Führen Sie die Bereitstellung im [IBM Kubernetes Service](/docs/containers?topic=containers-app)** aus. Mit dieser Option wird ein Cluster mit Hosts erstellt, die als Workerknoten bezeichnet werden, um hoch verfügbare Anwendungscontainer bereitzustellen und zu verwalten. Sie können einen Cluster erstellen oder die Bereitstellung in einem vorhandenen Cluster vornehmen.
  * **Führen Sie die Bereitstellung in Cloud Foundry aus**. Mit dieser Option wird Ihre Cloud-native App bereitgestellt, ohne dass Sie die zugrundeliegende Infrastruktur verwalten müssen. Wenn Ihr Konto über Zugriff auf {{site.data.keyword.cfee_full_notm}} verfügt, können Sie entweder den Bereitstellertyp **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** oder den Bereitstellertyp **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)** auswählen, mit dem Sie isolierte Umgebungen für das Hosting von Cloud Foundry-Anwendungen exklusiv für Ihr Unternehmen erstellen und verwalten können.
  * **Führen Sie die Bereitstellung in einer virtuellen Serverinstanz aus**. Diese Option stellt eine virtuelle Serverinstanz bereit, lädt ein Image, das Ihre App enthält, erstellt eine DevOps-Toolchain und initiiert den ersten Bereitstellungszyklus für Sie.

Nachdem Sie das Bereitstellungsziel ausgewählt und konfiguriert haben, wird auf der Detailseite der App angezeigt, dass Continuous Delivery konfiguriert ist. Wenn Sie das Repository anzeigen möchten, das den Quellcode für Ihre App enthält, klicken Sie auf **Repository anzeigen**.

Weitere Informationen zum Bereitstellen Ihrer App finden Sie unter [Apps bereitstellen](/docs/apps?topic=creating-apps-deploying-apps).

Weitere Informationen zu Bereitstellungszielen, Builds und Pipelines finden Sie unter [Build und Bereitstellung](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).
