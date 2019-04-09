---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-25"

---

# Best Practices für die App-Erstellung

Wenn Sie eine App in {{site.data.keyword.Bluemix_notm}} erstellen, müssen Sie hierbei möglicherweise anders vorgehen, als Sie dies von anderen Umgebungen gewöhnt sind. Die in diesem Abschnitt vorgestellten Best Practices unterstützen Sie dabei, optimale Apps für die Cloudplattform zu erstellen.

## Architektur mit mehreren Regionen
{: #multiregion}

Die Ausführung von mehreren Instanzen empfiehlt sich in einer einzelnen Region, um Ausfallzeiten zu vermeiden. Zur Bereitstellung einer noch stabileren Anwendung kann es jedoch sinnvoll sein, eine Architektur mit mehreren Regionen zu nutzen.

## Überwachungsoptionen
{: #monitoring}

{{site.data.keyword.Bluemix_notm}} vereinfacht die Überwachung Ihrer Anwendungen durch Services wie [Monitoring and Analytics](/docs/services/monana/index.html) und [New Relic ![Symbol für externen Link](../icons/launch-glyph.svg)](http://newrelic.com/){: new_window}. Weitere Informationen zu diesem Thema finden Sie unter [Überwachung und Protokollierung](../monitor_log/logging.html#monitoring_logging_bluemix_apps).

## Unterstützungsoptionen
{: #support}

Die gebührenpflichtigen {{site.data.keyword.Bluemix_notm}}-Preisstrukturpläne bieten eine Reihe unterschiedlicher Kontotypen mit *optionalem* gebührenpflichtigen Support. Eine Registrierung dieser Option sollten Sie ungeachtet Ihres Kontotyps auf jeden Fall in Erwägung ziehen, wenn Sie Ihre Anwendung in einer {{site.data.keyword.Bluemix_notm}}-Produktionsumgebung nutzen wollen.

Im Abschnitt zum Anfordern von [Unterstützung](../get-support/howtogetsupport.html) ist beschrieben, wie Sie - ob mit oder ohne gebührenpflichtigem Support - Unterstützung anfordern, die Sie bei unvorhergesehenen Problemen schützt.

## Für die Cloud geeignete Apps entwickeln
{: #cloud-ready-apps}

Wenn alle nachfolgenden Prinzipien in einer App beachtet werden, ist die App für die Cloud geeignet und kann nach {{site.data.keyword.Bluemix_notm}} migriert werden. Wenn in der App gegen ein Prinzip verstoßen wird, können Sie die App in der Regel so ändern, dass sie den Prinzipien entspricht.
{:shortdesc}

### App entsprechend erstellen, dass sie unabhängig von der Topologie ist

In einer Umgebung ohne Cloud kann von der App eine bestimmte Bereitstellungstopologie verwendet werden. Die Apptopologie kann sich in Cloud-Apps jedoch ändern, weil für die Cloud geeignete Apps und Services sofortige Änderungen der Skalierbarkeit zulassen. Die Änderungen der Skalierbarkeit umfassen dynamisches Skalieren und eine manuelle Größenänderung der Instanzenanzahl einer App.

Erstellen Sie Ihre App so generisch und statusunabhängig wie möglich, um zu verhindern, dass die App durch Änderungen der Skalierbarkeit beeinträchtigt wird.

### Annehmen, dass das lokale Dateisystem ein nicht permanentes System ist

Eine App-Instanz kann in der Cloud jederzeit verschoben, gelöscht oder kopiert werden; verlassen Sie sich deswegen nicht auf die Dateien, die in das Dateisystem geschrieben werden. Wenn eine App das lokale Dateisystem als Cache für häufig verwendete Informationen (einschließlich von App-Protokollen) verwendet, gehen diese Informationen verloren, wenn die Instanz beendet wird und an einer anderen Position oder auf einer anderen virtuellen Maschine erneut gestartet wird.

Sie können Informationen anstatt im lokalen Dateisystem in einem Service speichern, z. B. in einer SQL- oder NoSQL-Datenbank. In einer dynamischen Cloudumgebung ist es darüber hinaus wichtig, dass die Protokolle durch einen Service bereitgestellt werden, der länger verfügbar ist als die App-Instanzen, für die die Protokolle erstellt werden.

### Sitzungsstatus außerhalb der App speichern

Der Status Ihres Systems wird durch die Datenbanken und den gemeinsam genutzter Speicher definiert und nicht durch jede einzelne aktive App-Instanz. Statusangaben jeder Art schränken die Skalierbarkeit einer App ein. Versuchen Sie, die Auswirkung des Sitzungsstatus dadurch zu minimieren, dass er an einer zentralen Position auf dem Server gespeichert wird.

Wenn Sie den Sitzungsstatus nicht vollständig ignorieren können, verlagern Sie ihn in einen Speicher mit hoher Verfügbarkeit, der sich außerhalb Ihres App-Servers befindet. Solche Speicher sind zum Beispiel IBM WebSphere Extreme Scale, Redis, Memcached oder eine externe Datenbank.

### Externe Service-Registry zum Auflösen von Serviceendpunkten verwenden

Hierbei handelt es sich um ein generelles Prinzip, das sich mehrfach auswirkt. Gehen Sie zum Beispiel nicht davon aus, dass den Services, die von der App verwendet werden, bestimmte Hostnamen oder IP-Adressen zugeordnet sind. Die Services in der Cloudumgebung können verlagert oder neu generiert worden sein und auch die Hostnamen und IP-Adressen können sich ändern.

Das Extrahieren von umgebungsspezifischen Abhängigkeiten in eine Reihe von Eigenschaftendateien ist zwar eine Verbesserung, aber trotzdem unzulänglich. Ein bewährtes Verfahren ist das Verwenden einer externen Service-Registry zum Auflösen von Serviceendpunkten oder das Delegieren der gesamten Routingfunktion an einen Service-Bus oder eine Lastausgleichsfunktion mit einem virtuellen Namen.

### Infrastruktur-APIs in der App vermeiden

Wenn Sie in Ihrer App eine bestimmte Infrastruktur-API benötigen, ist eine Änderung der Infrastruktur eine Herausforderung, weil von einer Infrastruktur-API auf viele verschiedene Schichten im Software-Stack verwiesen werden kann.

Sie können stattdessen auf vorhandene Open Source-Produkte oder kostenpflichtige Produkte zurückgreifen und PaaS-Lösungen (PaaS - Platform as a Service) in der PaaS-Schicht belassen, damit sie nicht zu einem Bestandteil Ihres App-Codes werden.

### Standardprotokolle verwenden

Verwenden Sie nicht eingeschränkt lesbare Protokolle, für die eine zusätzliche Konfiguration erforderlich ist, damit sie dauerhaft verfügbar sind.

Apps, die auf Standardprotokollen basieren, sind ausfallsicherer, wenn die Konfigurationselemente an die Plattform delegiert werden. Zu den Standardprotokollen gehören HTTP, SSL, Standarddatenbanken, Warteschlangensteuerung und Web-Service-Verbindungen.

### Kompatibilitätsbibliotheken statt betriebssystemspezifischer Features verwenden

Wenn Sie bereits betriebssystemspezifische Funktionen verwendet haben, können Sie dieses Problem mithilfe von Kompatibilitätsbibliotheken, z. B. Cygwin oder Mono, beheben. Cygwin ist eine Kompatibilitätsbibliothek, von der eine Reihe von Linux-Tools in einer Windows-Umgebung bereitgestellt werden. Mono ist eine Kompatibilitätsbibliothek, von der Windows .NET-Funktionen in Linux bereitgestellt werden.

Vermeiden Sie betriebssystemspezifische Abhängigkeiten; verwenden Sie stattdessen Services, die von der Middlewareinfrastruktur oder von Service-Providern bereitgestellt werden.

### Installationsprozess mit Scripts steuern

Es kann vorkommen, dass die App in der dynamischen Cloudumgebung häufig bedarfsgesteuert installiert wird. Der Installationsprozess muss scriptgesteuert und zuverlässig sein, die Konfigurationsdaten müssen aus den Scripts externalisiert werden.

Erfassen Sie die App-Installation als einheitlichen Satz aus Scripts, die vom Betriebssystem unabhängig sind. Halten Sie die App-Installation klein und portierbar, damit sie an abweichende Automatisierungsverfahren angepasst werden kann. Minimieren Sie auch die Abhängigkeiten, die für die App-Installation erforderlich sind.

Weitere Informationen zu für die Cloud geeigneten Apps finden Sie in dem Abschnitt zu [12-Faktor-Apps![Symbol für externen Link](../icons/launch-glyph.svg)](http://12factor.net/){: new_window}.

