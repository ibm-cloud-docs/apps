---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-06"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Apps mit Mendix erstellen
{: #create-mendix}

Mendix ist eine Low-Code-Entwicklungsumgebung und ein Toolset, dass Ihnen dabei hilft, Anwendungen mit mehreren Geräten schneller und mit weniger Entwicklungsressourcen, die in {{site.data.keyword.cloud}} ausgeführt werden, zu liefern. Durch die Auswahl eines Mendix Low-Code-Starter-Kits werden Sie durch die Kontoeinrichtung auf eine Mendix-Plattform geführt, starten Ihr Projekt und wählen Ihre Entwicklungsumgebung entweder in der Cloud Foundry oder in Ihrem Kubernetes-Cluster aus.
{: shortdesc}

## Starter-Kit auswählen
{: #starterkit-mendix}

1. Klicken Sie im [{{site.data.keyword.cloud_notm}}-App-Service-Dashboard ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/appservice/dashboard){: new_window} auf **Einstieg**.
2. Wählen Sie ein Mendix-Low-Code-Starter-Kit aus einer der folgenden Kategorien aus:
  * [Mobile ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/appservice/starter-kits/mendix-mobile-app)
  * [Watson Web oder Mobile App ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson)
  * [Web-App ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}/developer/appservice/starter-kits/mendix-web-app)
3. Klicken Sie auf **Anwendung erstellen**.
4. Geben Sie auf der Seite **App-Details** den Namen Ihrer App und optional Tags an, um Ihre App zu klassifizieren. Weitere Informationen finden Sie in [Mit Tags arbeiten](/docs/resources/tagging_resources.html#tag).
5. Klicken Sie auf **Erstellen**.


## Autorisieren Sie IBM, um Ihr Projekt auf Mendix-und Linkkonten zu erstellen
{: #link-mendix-account}

Wenn Sie Mendix mit {{site.data.keyword.cloud_notm}} noch nicht verwenden, werden Sie zur Mendix-Plattform geführt, um sich bei {{site.data.keyword.cloud_notm}} anzumelden und zu autorisieren, um ein neues Projekt in Ihrem Namen auf der Mendix-Plattform zu erstellen. Dieses Projekt wird mit {{site.data.keyword.cloud_notm}} verknüpft, sodass Bereitstellungen automatisch an {{site.data.keyword.cloud_notm}} weitergeleitet werden.

1. Wenn Sie die folgende Nachricht sehen: "To complete app creation, a Mendix user account is required. Would you like to link your account now?" (Ein Mendix-Benutzer ist erforderlich, um die App-Erstellung abzuschließen. Möchten Sie Ihr Konto jetzt verknüpfen?), klicken Sie auf **Konto verknüpfen**.
2. Wählen Sie auf der Bestätigungsseite von Mendix **I agree to the Mendix Privacy Policy and Terms** (Ich stimme den Datenschutzrichtlinie und Bedingungen von Mendix zu) aus und klicken Sie auf **Bestätigen**.
3. Wenn Sie dazu aufgefordert werden, geben Sie Ihre E-Mail-Adresse, Ihr Kennwort und Ihr Land an und klicken auf **Erstellen**.
4. Klicken Sie auf der Seite, mit der Sie Benutzer für den **Zugriff auf Ihr Mendix-Konto berechtigen**, auf **Berechtigen**.

Nachdem die Autorisierung abgeschlossen ist, kehrt Ihr Browser zur Mendix-App zurück, die Sie erstellen. Die Seite für die **Auswahl einer Bereitstellungsumgebung** wird angezeigt.

## Bereitstellungsoption für Ihre Mendix-App auswählen
{: #select-deployment}

1. Wählen Sie auf der Seite **Bereitstellungsumgebung auswählen** die Option Cloud Foundry oder einen Ihrer Kubernetes-Cluster aus, die in {{site.data.keyword.cloud_notm}} ausgeführt werden. Wenn Ihr Konto über Zugriff auf {{site.data.keyword.cfee_full_notm}} verfügt, können Sie entweder den Cloud Foundry-Bereitstellertyp **[Public Cloud](/docs/cloud-foundry-public/about-cf.html#about-cf)** oder den Cloud Foundry-Bereitstellertyp **[Enterprise Environment](/docs/cloud-foundry-public/cfee.html#cfee)** auswählen, mit dem Sie isolierte Umgebungen für das Hosting von Cloud Foundry-Anwendungen exklusiv für Ihr Unternehmen erstellen und verwalten können.
2. Optional. Wenn Sie keinen Kubernetes-Cluster haben, können Sie jetzt einen erstellen.
3. Wählen Sie auf der Seite **Toolchain konfigurieren** Ihre Region und Ihre Ressourcengruppe aus und klicken Sie anschließend auf **Erstellen**.

Es wird eine DevOps-Toolchain erstellt. Die Toolchain integriert Ihr Mendix-Projekt auf der Mendix-Plattform in Ihre {{site.data.keyword.cloud_notm}}-Umgebung. Eine Standardanwendung wird in Ihrer Zielumgebung bereitgestellt, damit Sie überprüfen können, ob die Anwendung nach Ende der DevOps-Toolchain erfolgreich bereitgestellt wurde.

Die Mendix Cloud Foundry-Implementierungen benötigen den PostGRES-Datenbankservice, der kein Lite-Tier aufweist. Wenn Sie die Mendix-Starter-Kits mit einem Lite-Konto evaluieren möchten, können Sie einen Test-Kubernetes-Cluster als Ziel verwenden.
{: tip}

Wenn Sie für die Bereitstellung einen Kubernetes-Cluster ausgewählt haben, erfahren Sie im [Lernprogramm für Mendix-Kubernetes](/docs/apps/tutorials/tutorial_mendix_kubernetes.html#deploy-mendix-kube) mehr über die Konfiguration Ihres Clusters für den Produktionseinsatz.


## Mendix-Entwicklungs- und Bereitstellungslebenzyklus fortsetzen
{: #dev-lifecycle-mendix}

Mendix ist eine Low-Code-Authoring-Umgebung. Der Entwicklungszyklus erfordert, dass Sie Ihr Projekt in der Desktopanwendung Mendix Modeler öffnen.

1. Klicken Sie in Ihrer {{site.data.keyword.cloud_notm}}-Anwendung auf die Option zum **Bearbeiten in Mendix**.
2. Klicken Sie im Mendix-Webportal auf die Option zum **Bearbeiten in Desktop Modeler**.
  Die Mendix-Anwendung wird im Desktop-Modellierungsprogramm geöffnet.
3. Bearbeiten Sie Ihre Mendix-App und speichern Sie Ihre Änderungen.
4. Verwenden Sie das Menü **Ausführen** der Mendix-Anwendung Desktop Modeler und wählen Sie die Option **Ausführen** aus.
  Das Bereitstellungspaket wird erstellt und in Mendix hochgeladen. Nachdem das Bereitstellungspaket erstellt wurde, können Sie Ihre Anwendung in {{site.data.keyword.cloud_notm}} bereitstellen.
5. Um Ihre Mendix-Anwendung bereitzustellen, wechseln Sie wieder auf die Seite mit den **Anwendungsdetails** unter {{site.data.keyword.cloud_notm}} und klicken auf **Anwendung bereitstellen**.
  Mit dieser Aktion wird die DevOps-Toolchain gestartet, die die letzten Bereitstellungen von Mendix abruft und in Ihrer Zielumgebung bereitstellt. Nachdem die Bereitstellung abgeschlossen ist, wird die aktuellste Version Ihrer Anwendung automatisch gestartet und ist dann verfügbar.

Alle Mendix-Anwendungen sollen in {{site.data.keyword.cloud_notm}} durch Klicken auf **Anwendung bereitstellen** auf der Seite **Anwendungsdetails** unter {{site.data.keyword.cloud_notm}} bereitgestellt werden. Rufen Sie Mendix-Toolchains nicht manuell über die IBM DevOps-Schnittstelle auf. Das manuelle Starten von Toolchains über die DevOps-Schnittstelle führt zu fehlerhaften Bereitstellungen, da die erforderlichen Metadaten fehlen, die für Mendix-Bereitstellungen erforderlich sind. Abhängig vom Status Ihrer Anwendung kann entweder ein Fehler während des Starts der DevOps-Toolchain oder ein Fehler in der bereitgestellten Anwendung auftreten. Wenn Sie die Toolchain manuell starten und einen Fehler bemerken, können Sie Ihre Anwendungsbereitstellung durch Klicken auf **Anwendung implementieren** auf der Seite **Anwendungsdetails** unter {{site.data.keyword.cloud_notm}} wiederherstellen. Diese Aktion löst einen vollständigen DevOps-Ablauf für die Mendix-Anwendung aus, wobei die erforderlichen Metadaten enthalten sind.
{: tip}

## Nächste Schritte 
{: #next-steps-mendix}

Konfigurieren Sie Ihre App für die Bereitstellung in der Produktionsumgebung, um Ihre App in {{site.data.keyword.containerlong_notm}} bereitzustellen. Weitere Informationen enthält das [Lernprogramm für Mendix-Kubernetes](/docs/apps/tutorials/tutorial_mendix_kubernetes.html#deploy-mendix-kube). 
