---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, deploy, deploying apps, toolchains, cli

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Apps bereitstellen
{: #deploying-apps}

Sie können Ihre Apps mit einer Toolchain oder über eine Befehlszeilenschnittstelle (CLI) bereitstellen. Eine Toolchain ist ein Satz von Toolintegrationen. Die Befehlszeilenschnittstelle ist eine einfache Möglichkeit, Ihre Apps und Serviceinstanzen bereitzustellen.
{: shortdesc}

## Apps mithilfe von Toolchains bereitstellen
{: #toolchain-deploy-apps}

Offene Toolchains sind in den Public- und Dedicated-Umgebungen unter {{site.data.keyword.Bluemix}} verfügbar. Mit einer ordnungsgemäß konfigurierten Toolchain ist das Bereitstellen Ihrer App einfach. Bei einer ordnungsgemäß konfigurierten Toolchain startet mit jedem Vorgang der Zusammenführung mit dem Masterzweig in Ihrem Repository ein Erstellungs-/Bereitstellungszyklus.

Sie können auf folgenden Wegen eine Toolchain erstellen:
* Sie können eine Toolchain mithilfe einer Vorlage erstellen.
* Sie können eine Toolchain aus einer App heraus erstellen.

Weitere Informationen zu Toolchains finden Sie unter [Toolchains erstellen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## Apps über die Befehlszeilenschnittstelle (CLI) bereitstellen
{: #cli-deploy-apps}

{{site.data.keyword.cloud_notm}} bietet eine leistungsfähige Befehlszeilenschnittstelle (Command Line Interface, CLI) sowie Plug-ins und Entwicklertoolerweiterungen, die in die CLI integriert werden.

Bevor Sie beginnen, müssen Sie die {{site.data.keyword.cloud_notm}}-CLI [herunterladen und installieren](/docs/cli?topic=cloud-cli-ibmcloud-cli).

Die Befehlszeilenschnittstelle wird von Cygwin nicht unterstützt. Verwenden Sie das Tool in einem anderen Fenster als dem Cygwin-Befehlszeilenfenster.
{: important}

  1. {: download} Laden Sie den Code für Ihre App in ein neues Verzeichnis herunter, um Ihre Entwicklungsumgebung einzurichten.

    <a class="xref" href="https://{DomainName}" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="(Wird in einer neuen Registerkarte oder in einem neuen Fenster geöffnet)"></a>

  2. Wechseln Sie in das Verzeichnis, in dem sich Ihr Code befindet.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">neues_Verzeichnis</var></code></pre>

  3.  Nehmen Sie Änderungen an Ihrem App-Code vor. Beispiel: Wenn Sie eine {{site.data.keyword.cloud_notm}}-Beispielanwendung verwenden und Ihre App die Datei `src/main/webapp/index.html` enthält, können Sie sie ändern und den Dankestext für die Erstellung bearbeiten. Stellen Sie sicher, dass sich die App lokal ausführen lässt, bevor sie wieder in {{site.data.keyword.cloud_notm}} bereitgestellt wird.

    Beachten Sie die Datei `manifest.yml`. Wenn Ihre App wieder in {{site.data.keyword.cloud_notm}} bereitgestellt wird, dient diese Datei zum Ermitteln der URL, der Speicherzuordnung, der Anzahl von Instanzen und anderer wichtiger Parameter für Ihre Anwendung.

    Prüfen Sie auch den Inhalt der Datei `README.md`, die gegebenenfalls Informationen wie Erstellungsanweisungen enthält.

  Wenn es sich bei Ihrer Anwendung um eine Liberty-App handelt, müssen Sie sie erstellen, bevor Sie sie erneut bereitstellen.
  {: note}

  4. Stellen Sie eine Verbindung zu {{site.data.keyword.cloud_notm}} her und melden Sie sich an.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">Domänenname</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">Benutzername</var> -o <var class="keyword varname" data-hd-keyref="org_name">Organisationsname</var> -s <var class="keyword varname" data-hd-keyref="space_name">Bereichsname</var></code></pre>

  Wenn Sie eine föderierte ID nutzen, fügen Sie die Option `-sso` hinzu.

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">Organisationsname</var> -s <var class="keyword varname" data-hd-keyref="space_name">Bereichsname</var> -sso</code></pre>

  Wenn der Wert ein Leerzeichen enthält, müssen `username`, `org_name` und `space_name` in einfache oder doppelte Anführungszeichen eingeschlossen werden. Beispiel: `-o "my org"`.
  {: note}

  5. Führen Sie in Ihrem neuen Verzeichnis mit dem Befehl `ibmcloud dev deploy` die Bereitstellung Ihrer App in {{site.data.keyword.cloud_notm}} durch. Weitere Informationen finden Sie in der [Dokumentation zur Befehlszeilenschnittstelle](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).

  <pre class="pre"><code class="hljs">ibmcloud dev deploy <var class="keyword varname" data-hd-keyref="app_name">App-Name</var></code></pre>

  6. Greifen Sie auf Ihre App zu, indem Sie zu https://<var class="keyword varname" data-hd-keyref="app_url">App-URL</var>.<span class="keyword" data-hd-keyref="APPDomain">App-Domänenname</span> navigieren.
