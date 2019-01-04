---

copyright:
  years: 2017, 2018
lastupdated: "2018-11-29"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Bewährte Verfahren (Best Practices) für die Erstellung guter Apps
{: #best-practice}

Erstellen Sie Ihre App in {{site.data.keyword.cloud}}, um alle Vorteile auszuschöpfen, die eine Cloud bietet. Die in diesem Abschnitt vorgestellten bewährten Verfahren (Best Practices) helfen Ihnen dabei, Ihre Apps für die Cloud vorzubereiten.
{: shortdesc}

## App topologieunabhängig konzipieren

In einer Umgebung ohne Cloud verwendet Ihre App möglicherweise eine bestimmte Bereitstellungstopologie. Die App-Topologie kann sich in Cloud-Apps jedoch ändern, weil für die Cloud geeignete Apps und Services sofortige Änderungen der Skalierbarkeit zulassen. Diese Änderungen umfassen dynamisches Skalieren und eine manuelle Änderung der Anzahl von Instanzen einer App.

Erstellen Sie Ihre App so generisch und statusunabhängig wie möglich, um zu verhindern, dass die App durch Änderungen in der Skalierbarkeit beeinträchtigt wird.

## Davon ausgehen, dass es sich beim lokalen Dateisystem nicht um ein permanentes System handelt

Verlassen Sie sich nicht auf die Dateien, die in das Dateisystem geschrieben werden, da eine App-Instanz in der Cloud verschoben, gelöscht oder dupliziert werden kann. Wenn eine App das lokale Dateisystem als Cache für häufig verwendete Informationen (einschließlich App-Protokolle) verwendet, gehen diese Informationen verloren, wenn die Instanz beendet wird und an einem anderen Standort oder auf einer anderen virtuellen Maschine erneut gestartet wird.

Sie können Informationen anstatt im lokalen Dateisystem in einem Service speichern, z. B. in einer SQL- oder NoSQL-Datenbank. In einer dynamischen Cloudumgebung ist es darüber hinaus wichtig, dass die Protokolle durch einen Service bereitgestellt werden, der länger verfügbar ist als die App-Instanzen, für die die Protokolle erstellt werden.

## Sitzungsstatus aus Ihrer App ausschließen

Der Status Ihres Systems wird durch die Datenbanken und den gemeinsam genutzter Speicher definiert und nicht durch jede einzelne aktive App-Instanz. Statusangaben jeder Art schränken die Erweiterbarkeit einer App ein. Versuchen Sie, die Auswirkung des Sitzungsstatus dadurch zu minimieren, dass er an einer zentralen Position auf dem Server gespeichert wird.

Wenn Sie den Sitzungsstatus nicht vollständig ignorieren können, verlagern Sie ihn in einen Speicher mit hoher Verfügbarkeit, der sich außerhalb Ihres App-Servers befindet. Solche Speicher sind zum Beispiel IBM WebSphere eXtreme Scale, Redis, Memcached oder eine externe Datenbank.

## Externe Service-Registry zum Auflösen von Serviceendpunkten verwenden

Gehen Sie nicht davon aus, dass den Services, die von der App verwendet werden, bestimmte Hostnamen oder IP-Adressen zugeordnet sind. Die Services in der Cloudumgebung können verlagert oder neu generiert worden sein und auch die Hostnamen und IP-Adressen können sich ändern.

Das Extrahieren von umgebungsspezifischen Abhängigkeiten in eine Reihe von Eigenschaftendateien ist zwar eine Verbesserung, aber trotzdem unzulänglich. Ein bewährtes Verfahren ist das Verwenden einer externen Service-Registry zum Auflösen von Serviceendpunkten oder das Delegieren der gesamten Routingfunktion an einen Service-Bus oder eine Lastausgleichsfunktion mit einem virtuellen Namen.

## App unter Verwendung einer Architektur mit mehreren Regionen erstellen
{: #multiregion}

Sie können mehr als eine Instanz ausführen, um Ausfallzeiten in einer einzelnen Region zu vermeiden. Zur Bereitstellung einer noch stabileren Anwendung kann es sinnvoll sein, eine Architektur mit mehreren Regionen zu nutzen.

## Überwachung Ihrer Apps sicherstellen
{: #monitoring}

{{site.data.keyword.Bluemix_notm}} vereinfacht die Überwachung Ihrer Anwendungen durch Services wie [New Relic ![Symbol für externen Link](../icons/launch-glyph.svg)](http://newrelic.com/){: new_window}.

## Vorteile von Supportoptionen nutzen
{: #support}

Die gebührenpflichtigen {{site.data.keyword.Bluemix_notm}}-Preisstrukturpläne bieten eine Reihe unterschiedlicher Kontotypen mit optionalem gebührenpflichtigen Support. Eine Registrierung dieser Option sollten Sie ungeachtet Ihres Kontotyps auf jeden Fall in Erwägung ziehen, wenn Sie Ihre Anwendung in einer {{site.data.keyword.Bluemix_notm}}-Produktionsumgebung nutzen wollen.

Im Abschnitt zum Anfordern von [Unterstützung](/docs/get-support/howtogetsupport.html) ist beschrieben, wie Sie - ob mit oder ohne gebührenpflichtigem Support - Unterstützung anfordern, die Sie bei unvorhergesehenen Problemen schützt.

## Infrastruktur-APIs in der App vermeiden

Wenn Sie in Ihrer App eine bestimmte Infrastruktur-API benötigen, ist eine Änderung der Infrastruktur eine Herausforderung, weil von einer Infrastruktur-API auf viele verschiedene Schichten im Software-Stack verwiesen werden kann.

Sie können stattdessen auf vorhandene Open Source-Produkte oder kostenpflichtige Produkte zurückgreifen und PaaS-Lösungen (PaaS - Platform as a Service) in der PaaS-Schicht belassen, damit sie nicht zu einem Bestandteil Ihres App-Codes werden.

## Standardprotokolle verwenden

Verwenden Sie nicht eingeschränkt lesbare Protokolle, für die eine zusätzliche Konfiguration erforderlich ist, damit sie dauerhaft verfügbar sind.

Apps, die auf Standardprotokollen basieren, sind ausfallsicherer, wenn die Konfigurationselemente an die Plattform delegiert werden. Zu den Standardprotokollen gehören HTTP, SSL, Standarddatenbanken, Warteschlangensteuerung und Web-Service-Verbindungen.

## Kompatibilitätsbibliotheken statt betriebssystemspezifischer Features verwenden

Wenn Sie bereits betriebssystemspezifische Funktionen verwendet haben, können Sie dieses Problem mithilfe von Kompatibilitätsbibliotheken, z. B. Cygwin oder Mono, beheben. Cygwin ist eine Kompatibilitätsbibliothek, von der eine Reihe von Linux-Tools in einer Windows-Umgebung bereitgestellt werden. Mono ist eine Kompatibilitätsbibliothek, die Windows .NET-Tools in Linux bereitstellt.

Vermeiden Sie betriebssystemspezifische Abhängigkeiten; verwenden Sie stattdessen Services, die von der Middlewareinfrastruktur oder von Service-Providern bereitgestellt werden.

## Installationsprozess mit Scripts steuern

Es kann vorkommen, dass die App in der dynamischen Cloudumgebung häufig bedarfsgesteuert installiert wird. Der Installationsprozess muss scriptgesteuert und zuverlässig sein, die Konfigurationsdaten müssen aus den Scripts externalisiert werden.

Erfassen Sie die App-Installation als einheitlichen Satz aus Scripts, der vom Betriebssystem unabhängig ist. Halten Sie die App-Installation klein und portierbar, damit sie an abweichende Automatisierungsverfahren angepasst werden kann. Minimieren Sie auch die Abhängigkeiten, die für die App-Installation erforderlich sind.

Weitere Informationen zu für die Cloud geeigneten Apps finden Sie in dem Abschnitt zu [12-Faktor-Apps![Symbol für externen Link](../icons/launch-glyph.svg)](http://12factor.net/){: new_window}.


