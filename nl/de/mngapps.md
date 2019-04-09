---

copyright:
  years: 2015, 2017, 2018
lastupdated: "2018-11-06"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Status der App prüfen
{: #manageapps}

Ihre Ressourcenliste in der {{site.data.keyword.Bluemix}}-Konsole stellt Übersichtsinformationen zu den von Ihnen erstellten Anwendungen bereit. Diese Übersichtsinformationen umfassen den Namen, das Symbol, die URL, die Laufzeit und den Ausführungsstatus sowie die Serviceinstanzen, die an die App gebunden sind.
{:shortdesc}

## Status der App verstehen
{: #status}

In Ihrer Ressourcenliste können Sie den Status jeder Anwendung anzeigen. In der Statusspalte jeder Anwendung können Sie sehen, ob die Instanzen der App ausgeführt werden.

<dl>
<dt>
<strong>
Gestoppt oder Unbekannt (grau)
</strong>
</dt>
<dd>
Ihre App wurde gestoppt oder der Status ist unbekannt. Das graue Symbol gibt an, dass die App gestoppt wurde oder dass der Status unbekannt ist.
</dd>
<dt>
<strong>
Aktiv (grün)
</strong>
</dt>
<dd>
Ihre App ist aktiv. Das grüne Symbol gibt an, dass die App gestartet wurde und alle Instanzen aktiv sind.
</dd>
<dt>
<strong>
_Anzahl_aktiv (gelb)
</strong>
</dt>
<dd>
Die App ist zwar gestartet, doch es sind nicht alle Instanzen aktiv. Das gelbe Symbol gibt an, dass weniger als 100 % der Instanzen aktiv sind. Die Anzahl der aktiven Instanzen und die Anzahl der fehlgeschlagenen Instanzen wird angezeigt.
</dd>
<dt>
<strong>
Nicht aktiv (rot)
</strong>
</dt>
<dd>
Ihre App wird nicht ausgeführt. Das rote Symbol gibt an, dass die App zwar gestartet wurde, aber keine Instanz aktiv ist.
</dd>
</dl>

## App-Details anzeigen
{: #viewingapps}

Sie können weitere Informationen zu einer App anzeigen, indem Sie auf den Namen der App in Ihrer Ressourcenliste klicken. Daraufhin wird die Seite 'Übersicht' der App angezeigt.

Nachdem eine App bereitgestellt wurde, können Sie sie über die Seite 'Übersicht' starten, stoppen oder erneut starten oder - im Falle von Webanwendungen - die Anzahl der Instanzen sowie die von der App verwendete Speichermenge ändern. {{site.data.keyword.Bluemix_notm}} führt für Webanwendungen keine automatische Skalierung der Apps auf Basis der jeweiligen Auslastung durch, weshalb Sie sie selbst verwalten müssen.

Nach einer Aktualisierung können Apps erneut bereitgestellt werden. Der Mechanismus zum Aktualisieren der App ist mit dem identisch, der für die ursprüngliche Bereitstellung verwendet wurde. {{site.data.keyword.Bluemix_notm}} stoppt alle aktiven Instanzen und ersetzt sie automatisch durch neue Instanzen.
