---

copyright:
  years: 2018
lastupdated: "2018-03-16"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Empfohlene Phasen der Cloudentwicklung
{: #development_process}

Cloud-App-Entwickler durchlaufen vier grundlegende Phasen des Entwicklungsprozesses: Einstieg, Codierung, Bereitstellung und Verwaltung. Der Ablauf ist interaktiv und schnell. Das Ziel ist es, schnell eine mindestens funktionsfähige App zu erstellen und dann anhand des Feedbacks aus der Produktion den Code oder Bereitstellungszyklus immer wieder zu wiederholen, bis Ihre App bei den Benutzern ankommt.
{: shortdesc}

![Entwicklungsprozess](images/dev_flow_overview.png "Entwicklungsprozess") Abbildung 1. Phasen des Entwicklungsprozesses

In manchen Fällen wird die Ausführung als eine eigene Phase angesehen, aber im vorliegenden Fall kombinieren wir sie mit den Bereitstellungs- und Verwaltungsphasen.

Werfen wir einen genaueren Blick auf die beste Möglichkeit, {{site.data.keyword.cloud_notm}} in Ihrem Entwicklungsprozess zu verwenden.

##Einstieg
{: #get_started}

Beginnen Sie mit der Entwicklung Ihrer App in den {{site.data.keyword.cloud_notm}}-Entwicklerdashboards, in denen Sie ein Starter-Kit für Ihren Anwendungsfall und eine Programmiersprache auswählen können. {{site.data.keyword.cloud_notm}} verwendet Anweisungen aus dem Starter-Kit, um automatisch die erforderlichen Ressourcen bereitzustellen und ein sprachspezifisches, laufzeitunabhängiges App-Projekt zu erstellen, das als Grundlage für Produktions-App dient. Klicken Sie zum Abschluss der Einstiegsphase im Entwicklerdashboard auf **In Cloud bereitstellen**. Mit einem Klick wird eine vollständige DevOps-Toolchain mit einem Code-Repository, das mit Ihrem App-Quellcode gefüllt ist, und einer Bereitstellungspipeline erstellt.

![Einstieg](images/dev_get_started.png "Einstieg") Abbildung 2. Einstieg

Wenn Sie die Schaltfläche **In Cloud bereitstellen** verwenden, um Ihre DevOps-Toolchain einzurichten, wählen Sie Ihre Laufzeitplattform aus, z. B. Kubernetes oder Cloud Foundry. Die aus {{site.data.keyword.cloud_notm}} erzeugte Starter-App ist laufzeitunabhängig und muss nicht modifiziert werden.
{: tip}

##Lokal entwickeln
{: #develop_locally}

Nachdem Sie Ihr Starter-App-Projekt und Ihre Toolchain erstellt haben, starten Sie Ihre Entwicklung lokal. Klonen Sie den Code aus Ihrem Repository und importieren Sie ihn in Ihre IDE. Verwenden Sie {{site.data.keyword.dev_cli_notm}}, um Ihre Cloud-App auf Ihrer lokalen Maschine zu erstellen, auszuführen und zu testen. {{site.data.keyword.dev_cli_notm}} erstellt und verwaltet einen lokalen Container für Sie. Wenn Sie bereit sind, Ihre App in der Cloud auszuführen, führen Sie eine Push-Operation zu Ihrem Cloud-Repository durch und führen Sie Ihre Änderungen zusammen.

![Lokal entwickeln](images/dev_code_locally.png "Lokal entwickeln") Abbildung 3. Lokal entwickeln

Die grundlegenden Funktionen für {{site.data.keyword.dev_cli_notm}} sind `bx dev build` und `bx dev run`, aber die Befehlszeilenschnittstelle bietet noch viel mehr. Weitere Details finden Sie unter [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html).
{: tip}

##In {{site.data.keyword.cloud_notm}} bereitstellen und verwalten
{: #deliver_and_manage}

Das Zusammenführen von Änderungen in Ihrem Cloud-Repository startet einen Erstellen-Bereitstellen-Zyklus in der DevOps-Toolchain, die Sie zuvor erstellt haben. Ihre App wird nach wenigen Minuten in der Cloud ausgeführt.

Den Status Ihrer DevOps-Pipeline können Sie im Delivery Pipeline-Dashboard prüfen. Den allgemeinen Status Ihrer App finden Sie im {{site.data.keyword.cloud_notm}}-Dashboard für Ihr Konto.
{: tip}

Die Toolchain, die in Ihrer Einstiegsphase erzeugt wird, verfügt über die grundlegenden Komponenten, die für eine interaktive, teambasierte Continuous Delivery erforderlich sind. {{site.data.keyword.cloud_notm}} bietet jedoch zusätzlich eine breite Auswahl von DevOps-Services, die Sie in Ihrer Toolchain hinzufügen können, um die Bereitstellung, Überwachung, Protokollierung und Alertausgabe zu verbessern.

![Bereitstellen und verwalten](images/dev_deliver_and_manage.png "Bereitstellen und verwalten") Abbildung 4. Bereitstellen und verwalten

Weitere Informationen zur [kontinuierlichen Entwicklung unter {{site.data.keyword.cloud_notm}}](../services/ContinuousDelivery/index.html#cd_getting_started).

## Alles zusammenführen

![Prozessdetail](images/dev_process_detail.png "Prozessdetails") Abbildung 5. End-to-End-Entwicklungsprozess
