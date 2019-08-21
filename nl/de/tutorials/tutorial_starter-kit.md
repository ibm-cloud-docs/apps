---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-17"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# App mit einem Starter-Kit erstellen
{: #tutorial-starterkit}

Mit einem Starter-Kit können Sie Ihre Anwendung schnell zum Einsatz bringen und auf zukünftige Entwicklungen vorbereiten. Wählen Sie ein Starter-Kit und eine Programmiersprache aus, erstellen Sie eine App und richten Sie dann eine DevOps-Toolchain ein, um Ihre App automatisch bereitzustellen.
{: shortdesc}

Sie können eine App aus einer Reihe von Starter-Kits erstellen, einschließlich eines leeren Starter-Kits, wenn Sie die Buildoptionen selbst anpassen möchten. In jedem Fall wird automatisch eine DevOps-Toolchain für die Bereitstellung Ihrer App erstellt. Sie können den Code auch für eine sofortige Überprüfung herunterladen.

{{site.data.keyword.cloud_notm}} verfügt über Entwicklerportale in verschiedenen Interessengebieten (wie Watson) oder einem digitalen Vertriebskanal (z. B. mobile oder Web-Apps). Über das Symbol **Menü** ![Menüsymbol](../../icons/icon_hamburger.svg) können Sie auf diese Portale zugreifen.

Jedes Entwicklerportal stellt Starter-Kits zur Verfügung, die für den Schwerpunktbereich des jeweiligen Portals relevant sind. Die Portale bieten konsistente, intuitive Workflows zur minutenschnellen Erstellung einer funktionierenden, produktionsbereiten App.

Starter-Kits sind in vielen Kategorien verfügbar, darunter die folgenden:
* [Watson ](https://{DomainName}/developer/watson/dashboard){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")
* [Apple ](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")
* [Mobile ](https://{DomainName}/developer/mobile/dashboard){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")
* [Web-App ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")

Weitere Informationen finden Sie in [Was sind Starter-Kits?](/docs/apps?topic=creating-apps-starter-kits)

## Schritt 1. Tools installieren
{: #prereqs-starterkit}

* Installieren Sie die [Entwicklertools](/docs/cli?topic=cloud-cli-getting-started).
* Docker wird als Teil der Entwicklertools installiert. Docker muss ausgeführt werden, damit die Buildbefehle funktionieren. Sie müssen ein Docker-Konto erstellen, die Docker-App ausführen und sich anmelden.
* Wenn Sie vorhaben, Ihre App in {{site.data.keyword.cfee_full}} bereitzustellen, müssen Sie [Ihr {{site.data.keyword.cloud_notm}}-Konto vorbereiten](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Schritt 2. App erstellen
{: #create-starterkit}

Starter-Kits sind in der {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}} in vielen Sprachen und Frameworks verfügbar. Zum Eingrenzen der Auswahl können Sie die Kategoriefilter wie Sprache und Typ verwenden.

1. Wählen Sie auf der Seite [Starter-Kits](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") in der {{site.data.keyword.dev_console}} ein Starter-Kit aus und klicken Sie auf **App erstellen**. 

    Um zu erfahren, was im Starter-Kit enthalten ist, wählen Sie die Kachel aus und lesen Sie die Details. Wenn Sie ein leeres Starter-Kit verwenden und Ihre App anschließend anpassen möchten, wählen Sie die Kachel **App erstellen** aus.
    {: tip}

2. Benennen Sie Ihre App und wählen Sie eine Ressourcengruppe aus.

3. Optional. Geben Sie Tags an, um Ihre App zu klassifizieren. Weitere Informationen finden Sie in [Mit Tags arbeiten](/docs/resources?topic=resources-tag).

4. Wählen Sie Ihre Sprache und Ihr Framework aus. Einige Starter-Kit sind möglicherweise nur ein einer Sprache verfügbar.

5. Klicken Sie auf **Erstellen**.

Großartiger Start! Sie haben soeben eine App erstellt!

Um Ihren Code zu überprüfen, bevor Sie Services hinzufügen oder Continuous Delivery hinzufügen, klicken Sie auf der Detailseite der App auf **Code herunterladen**. Prüfen Sie die Datei `README.md` in der heruntergeladenen komprimierten Datei, um herauszufinden, ob Sie weitere Aktionen ausführen müssen, um Ihre App betriebsbereit zu machen.
{: tip}

## Schritt 3. Services hinzufügen (optional)
{: #resources-starterkit}

Wenn für ein Starter-Kit bestimmte Services erforderlich sind, werden die automatisch bereitgestellten Serviceinstanzen automatisch erstellt und mit Ihrer App verbunden.

Sie können auch Services, die Ihre App mit der kognitiven Leistung von Watson funktional erweitern, mobile Services oder Sicherheitsservices hinzufügen. Im Rahmen dieses Lernprogramms fügen Sie eine Position für die Verwaltung Ihrer Daten hinzu.

1. Klicken Sie auf der Detailseite der App abhängig davon, ob Sie bereits über Services verfügen, die Sie mit dieser App verbinden möchten, auf **Service erstellen** oder auf **Vorhandene Services verbinden**.
2. Wählen Sie die Art des gewünschten Service aus und folgen Sie den Anweisungen, um entweder eine Serviceinstanz zu erstellen oder aber einen vorhandenen Service zu Ihrer App hinzuzufügen.

Nachdem Sie alle gewünschten Services hinzugefügt haben, werden diese auf der Detailseite der App angezeigt.

## Schritt 4. Bereitstellungsziel auswählen und Continuous Delivery konfigurieren
{: #target-starterkit}

Wenn Sie ein Bereitstellungsziel auswählen, wird automatisch eine DevOps-Toolchain für Ihre App erstellt. Die Toolchain enthält eine Delivery Pipeline, die den Bereitstellungsstatus Ihrer App anzeigt. Die neu generierte App wird in ein GitLab-Repository verschoben, das Teil der Toolchain ist.

Durch das Aktivieren einer DevOps-Toolchain wird eine teambasierte Entwicklungsumgebung für Ihre App erstellt. Wenn Sie eine Toolchain erstellen, erstellt der App-Service ein Git-Repository, in dem Sie Quellcode anzeigen, die App klonen und Problemmeldungen erstellen und verwalten können. Darüber hinaus verfügen Sie über Zugriff auf eine dedizierte GitLab-Umgebung  und eine Continuous-Delivery-Pipeline. Diese sind an das Bereitstellungsziel angepasst, das Sie auswählen, ob [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) oder [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Alle über ein {{site.data.keyword.cloud_notm}}-Entwicklerdashboard erstellten Toolchains sind für die automatische Bereitstellung konfiguriert.
{: note}

Führen Sie die folgenden Schritte aus, um Ihr Bereitstellungsziel auszuwählen und Continuous Delivery zu konfigurieren:

1. Klicken Sie auf der Detailseite der App auf **Continuous Delivery konfigurieren**.
2. Wählen Sie ein Bereitstellungsziel aus. Richten Sie Ihr Bereitstellungsziel entsprechend den Anweisungen für das ausgewählte Ziel ein:
  * **Führen Sie die Bereitstellung im [IBM Kubernetes Service](/docs/containers?topic=containers-app)** aus. Mit dieser Option wird ein Cluster mit Hosts erstellt, die als Workerknoten bezeichnet werden, um hoch verfügbare App-Container bereitzustellen und zu verwalten. Sie können einen Cluster erstellen oder die Bereitstellung in einem vorhandenen Cluster vornehmen.
  * **Führen Sie die Bereitstellung in Cloud Foundry aus**. Mit dieser Option wird Ihre cloudnative App bereitgestellt, ohne dass Sie die zugrundeliegende Infrastruktur verwalten müssen. Wenn Ihr Konto über Zugriff auf {{site.data.keyword.cfee_full_notm}} verfügt, können Sie entweder den Bereitstellertyp **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** oder den Bereitstellertyp **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)** auswählen, mit dem Sie isolierte Umgebungen für das Hosting von Cloud Foundry-Apps exklusiv für Ihr Unternehmen erstellen und verwalten können.
  * **Führen Sie die Bereitstellung in einer virtuellen Serverinstanz aus**. Diese Option stellt eine virtuelle Serverinstanz bereit, lädt ein Image, das Ihre App enthält, erstellt eine DevOps-Toolchain und initiiert den ersten Bereitstellungszyklus für Sie. Weitere Informationen finden Sie unter [Apps auf einem virtuellen Server bereitstellen](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server).

    Die VSI-Bereitstellung ist für einige Starter-Kits verfügbar. Wenn Sie diese Funktion verwenden möchten, rufen Sie das [{{site.data.keyword.cloud_notm}}-Dashboard](https://{DomainName}) auf und klicken Sie in der Kachel **Apps** auf **App erstellen**.
    {: note}

Nachdem Sie das Bereitstellungsziel ausgewählt und konfiguriert haben, wird auf der Detailseite der App angezeigt, dass Continuous Delivery konfiguriert ist. Wenn Sie das Repository anzeigen möchten, das den Quellcode für Ihre App enthält, klicken Sie auf **Repository anzeigen**.

## Schritt 5. App bereitstellen
{: #deploy-starterkit}

Die über das {{site.data.keyword.cloud_notm}}-Entwicklerdashboard erstellten DevOps-Toolchains sind für die automatische Bereitstellung konfiguriert.
{: note}

Nachdem Sie Ihr Bereitstellungsziel ausgewählt haben, öffnen Sie die Pipelinekomponente Ihrer neuen Toolchain, um den anfänglichen Erstellungs- und Bereitstellungsprozess zu starten, damit Sie Ihre neue App innerhalb weniger Minuten anzeigen können.

1. Klicken Sie auf der Detailseite der App auf **Toolchain anzeigen**.
2. Klicken Sie auf **Delivery Pipeline**. Hier können Sie Builds starten, die Bereitstellung verwalten sowie Protokolle und den Verlauf anzeigen.

Bei einer ordnungsgemäß konfigurierten Toolchain startet mit jedem Vorgang der Zusammenführung mit dem Masterzweig in Ihrem Repository ein Erstellungs-/Bereitstellungszyklus. Weitere Informationen finden Sie unter [Erstellen und bereitstellen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

Sie können Ihre App über die Befehlszeile bereitstellen, indem Sie den Befehl [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy) ausführen. Weitere Informationen finden Sie in [Apps über die CLI bereitstellen](/docs/apps?topic=creating-apps-deploying-apps#deploy-cli).

## Schritt 6. Ausführung der App verifizieren
{: #verify-starterkit}

Nach der Bereitstellung der App verweist Sie die Delivery Pipeline oder die Befehlszeile auf die URL für Ihre App.

1. Klicken Sie in der Toolchain von DevOps auf **Delivery Pipeline** und wählen Sie **Bereitstellungsstage** aus.
2. Klicken Sie auf **Protokolle und Verlauf anzeigen**.
3. Suchen Sie in der Protokolldatei nach der App-URL:

    Suchen Sie am Ende der Protokolldatei nach dem Wort `urls` oder `view` (bzw. 'ansehen'). Zum Beispiel wird in der Protokolldatei möglicherweise eine Zeile ähnlich der folgenden angezeigt: `urls: my-app-devhost.mybluemix.net` oder `Status der Anwendung ansehen unter: http://<ipaddress>:<port>/health`.

4. Rufen Sie die URL im Browser auf. Wenn die App ausgeführt wird, wird eine Nachricht angezeigt, die Folgendes enthält: `Congratulations` oder `{"status":"UP"}`.

Wenn Sie die Befehlszeile verwenden, führen Sie den Befehl [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) aus, um die URL der App anzuzeigen. Anschließend rufen Sie die URL in Ihrem Browser auf.
