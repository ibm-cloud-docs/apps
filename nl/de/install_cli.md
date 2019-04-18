---

copyright:

  years: 2015，2017, 2018

lastupdated: "2018-11-29"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:prereq: .prereq}
{:download: .download}
{:pre: .pre}
{:app_name: data-hd-keyref="app_name"}
{:app_key: data-hd-keyref="app_key"}
{:app_secret: data-hd-keyref="app_secret"}
{:app_url: data-hd-keyref="app_url"}
{:host: data-hd-keyref="host"}
{:org_name: data-hd-keyref="org_name"}
{:route: data-hd-keyref="route"}
{:space_name: data-hd-keyref="space_name"}
{:service_name: data-hd-keyref="service_name"}
{:service_instance_name: data-hd-keyref="service_instance_name"}
{:user_ID: data-hd-keyref="user_ID"}
{:note: .note}

# Apps mit der Befehlszeilenschnittstelle bereitstellen

Zur Bereitstellung Ihrer Apps und Serviceinstanzen können Sie die {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle verwenden.
{:shortdesc}

Laden Sie zunächst die {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle herunter und installieren Sie sie.

<p>
<a class="xref" href="https://clis.ng.bluemix.net" target="_blank" title="(Wird in einer neuen Registerkarte oder in einem neuen Fenster geöffnet)"><img class="image" src="images/btn_bx_commandline.svg" alt="IBM Cloud-Befehlszeilenschnittstelle herunterladen" /> </a>
</p>

**Einschränkung:** Das Befehlszeilentool wird von Cygwin nicht unterstützt. Verwenden Sie das Tool in einem anderen Befehlszeilenfenster als dem Cygwin-Befehlszeilenfenster.
{:prereq}

Nach der Installation der Befehlszeilenschnittstelle können Sie beginnen:

  1. {: download} Laden Sie den Code für Ihre App in ein neues Verzeichnis herunter, um Ihre Entwicklungsumgebung einzurichten.

    <a class="xref" href="http://bluemix.net" target="_blank" title="(Wird in einer neuen Registerkarte oder in einem neuen Fenster geöffnet)"><img class="image" src="images/btn_starter-code.svg" alt="Anwendungscode herunterladen" /> </a>

  2. Wechseln Sie in das Verzeichnis, in dem sich Ihr Code befindet.

  <pre class="pre"><code class="hljs">cd <var class="keyword varname">neues_Verzeichnis</var></code></pre>

  3.  Nehmen Sie Änderungen an Ihrem App-Code vor. Beispiel: Wenn Sie eine {{site.data.keyword.Bluemix}}-Beispielanwendung verwenden und Ihre App die Datei `src/main/webapp/index.html` enthält, können Sie sie ändern und den Dankestext für die Erstellung in einen anderen Text ändern. Stellen Sie sicher, dass sich die App lokal ausführen lässt, bevor sie wieder in {{site.data.keyword.Bluemix_notm}} bereitgestellt wird.

    Beachten Sie die Datei `manifest.yml`. Wenn Ihre App wieder in {{site.data.keyword.Bluemix_notm}} bereitgestellt wird, dient diese Datei zum Ermitteln der URL, der Speicherzuordnung, der Anzahl von Instanzen und anderer wichtiger Parameter für Ihre Anwendung.

    Beachten Sie auch die Datei `README.md`, die gegebenenfalls Informationen wie Erstellungsanweisungen enthält.

    Wenn es sich bei Ihrer Anwendung um eine Liberty-App handelt, müssen Sie sie vor der erneuten Bereitstellung erstellen.
    {: note}

  4. Stellen Sie eine Verbindung zu {{site.data.keyword.Bluemix_notm}} her und melden Sie sich an.

  <pre class="pre"><code class="hljs">ibmcloud api https://api.<span class="keyword" data-hd-keyref="DomainName">Domänenname</span></code></pre>

  <pre class="pre"><code class="hljs">ibmcloud login -u <var class="keyword varname" data-hd-keyref="user_ID">Benutzername</var> -o <var class="keyword varname" data-hd-keyref="org_name">Organisationsname</var> -s <var class="keyword varname" data-hd-keyref="space_name">Bereichsname</var></code></pre>

  Wenn Sie eine föderierte ID nutzen, fügen Sie die Option `-sso` hinzu.

  <pre class="pre"><code class="hljs">ibmcloud login  -o <var class="keyword varname" data-hd-keyref="org_name">Organisationsname</var> -s <var class="keyword varname" data-hd-keyref="space_name">Bereichsname</var> -sso</code></pre>

  Wenn der betreffende Wert ein Leerzeichen enthält, müssen `Benutzername`, `Organisationsname` und `Bereichsname` in Hochkommas oder Anführungszeichen eingeschlossen werden. Beispiel: `-o "my org"`.
  {: note}

  5. Führen Sie unter <var class="keyword varname">neues_Verzeichnis</var> mit dem Befehl `ibmcloud app push` ein erneutes Staging Ihrer App in {{site.data.keyword.Bluemix_notm}} durch. Weitere Informationen zum Befehl `ibmcloud app push` finden Sie unter [Anwendung hochladen](/docs/starters/upload_app.html).

  <pre class="pre"><code class="hljs">ibmcloud app push <var class="keyword varname" data-hd-keyref="app_name">App-Name</var></code></pre>

  6. Greifen Sie auf Ihre App zu, indem Sie zu https://<var class="keyword varname" data-hd-keyref="app_url">App-URL</var>.<span class="keyword" data-hd-keyref="APPDomain">App-Domänenname</span> navigieren.
