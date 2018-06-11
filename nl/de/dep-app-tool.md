---
copyright:

  years: 2018

lastupdated: "2018-05-22"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Apps bereitstellen
{: #deploy}

Sie können Ihre Apps mit einer Toolchain oder über eine Befehlszeilenschnittstelle bereitstellen. Eine Toolchain ist ein Satz von Toolintegrationen. Die Befehlszeilenschnittstelle ist eine einfache Möglichkeit, Ihre Apps und Serviceinstanzen bereitzustellen.
{: shortdesc}

## Apps mit Toolchains bereitstellen
{: #toolchains_getting_started}

Offene Toolchains sind in den Public- und Dedicated-Umgebungen unter {{site.data.keyword.Bluemix}} verfügbar. Sie können eine Toolchain auf zwei Arten erstellen: Erstellen Sie die Toolchain aus einer Vorlage oder aus einer App. Weitere Informationen zu Toolchains finden Sie unter [Toolchains erstellen](../services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

Mit einer ordnungsgemäß konfigurierten Toolchain ist das Bereitstellen ihrer App trivial: Bei jedem Vorgang der Zusammenführung mit dem Masterzweig in Ihrem Repository wird automatisch ein Erstellen-Bereitstellen-Zyklus ausgelöst.

Alle über ein {{site.data.keyword.Bluemix}}-Entwicklerdashboard erstellten Toolchains sind für die automatische Bereitstellung konfiguriert.
{: tip}

## Apps mit der Befehlszeilenschnittstelle bereitstellen
{: #cli}

IBM Cloud bietet eine leistungsfähige Befehlszeilenschnittstelle (Command Line Interface, CLI) sowie Plug-ins und Entwicklertoolerweiterungen, die in die CLI integriert werden.

Zur Bereitstellung Ihrer Apps und Serviceinstanzen können Sie die {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle verwenden.
{:shortdesc}

Laden Sie zunächst die {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle herunter und installieren Sie sie.

<p>
<a class="xref" href="https://clis.ng.bluemix.net" target="_blank" title="(Wird in einer neuen Registerkarte oder in einem neuen Fenster geöffnet)"><img class="image" src="images/btn_bx_commandline.svg" alt="Bluemix-Befehlszeilenschnittstelle herunterladen" /></a>
</p>

**Einschränkung:** Das Befehlszeilentool wird von Cygwin nicht unterstützt. Verwenden Sie das Tool in einem anderen Befehlszeilenfenster als dem Cygwin-Befehlszeilenfenster.
{:prereq}

Nach der Installation der Befehlszeilenschnittstelle können Sie beginnen:

  1. {: download} Laden Sie den Code für Ihre App in ein neues Verzeichnis herunter, um Ihre Entwicklungsumgebung einzurichten.

    <a class="xref" href="http://bluemix.net" target="_blank" img class=“image” src=“images/btn_starter-code.svg” alt=“Download application code” title="(Wird in einer neuen Registerkarte oder in einem neuen Fenster geöffnet)"></a>

  2. Wechseln Sie in das Verzeichnis, in dem sich Ihr Code befindet.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">neues_Verzeichnis</var></code></pre>

  3.  Nehmen Sie Änderungen an Ihrem App-Code vor. Beispiel: Wenn Sie eine {{site.data.keyword.Bluemix_notm}}-Beispielanwendung verwenden und Ihre App die Datei `src/main/webapp/index.html` enthält, können Sie sie ändern und den Dankestext für die Erstellung in einen anderen Text ändern. Stellen Sie sicher, dass sich die App lokal ausführen lässt, bevor sie wieder in {{site.data.keyword.Bluemix_notm}} bereitgestellt wird.

    Beachten Sie die Datei `manifest.yml`. Wenn Ihre App wieder in {{site.data.keyword.Bluemix_notm}} bereitgestellt wird, dient diese Datei zum Ermitteln der URL, der Speicherzuordnung, der Anzahl von Instanzen und anderer wichtiger Parameter für Ihre Anwendung.

    Beachten Sie auch die Datei `README.md`, die gegebenenfalls Informationen wie Erstellungsanweisungen enthält.

    Hinweis: Wenn es sich bei Ihrer Anwendung um eine Liberty-App handelt, müssen Sie sie vor der erneuten Bereitstellung erstellen.

  4. Stellen Sie eine Verbindung zu {{site.data.keyword.Bluemix_notm}} her und melden Sie sich an.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">Domänenname</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">Benutzername</var> -o <var class="keyword varname" data-hd-keyref="org_name">Organisationsname</var> -s <var class="keyword varname" data-hd-keyref="space_name">Bereichsname</var></code></pre>

  Wenn Sie eine eingebundene ID nutzen, fügen Sie die Option `-sso` hinzu.

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">Organisationsname</var> -s <var class="keyword varname" data-hd-keyref="space_name">Bereichsname</var> -sso</code></pre>

  **Hinweis**: Wenn der Wert ein Leerzeichen enthält, müssen `username`, `org_name` und `space_name` in einfache oder doppelte Anführungszeichen eingeschlossen werden. Beispiel: `-o "my org"`.

  5. Führen Sie unter <var class="keyword varname">neues_Verzeichnis</var> mit dem Befehl `ibmcloud app push` ein erneutes Staging Ihrer App in {{site.data.keyword.Bluemix_notm}} durch. Weitere Informationen zum Befehl `ibmcloud app push` finden Sie unter [Anwendung hochladen](/docs/starters/upload_app.html).

  <pre class="pre"><code class="hljs">ibmcloud app push <var class="keyword varname" data-hd-keyref="app_name">App-Name</var></code></pre>

  6. Greifen Sie auf Ihre App zu, indem Sie zu https://<var class="keyword varname" data-hd-keyref="app_url">App-URL</var>.<span class="keyword" data-hd-keyref="APPDomain">App-Domänenname</span> navigieren.
