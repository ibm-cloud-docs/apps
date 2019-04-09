---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# Apps in {{site.data.keyword.Bluemix_notm}} erstellen
{: #create}

In {{site.data.keyword.Bluemix}} können Sie auf Unternehmen abgestimmte Mobil- und Webanwendungen erstellen und von {{site.data.keyword.Bluemix_notm}} gehostete Clouderweiterungen nutzen. Mit der {{site.data.keyword.Bluemix}}-Konsole und den Befehlszeilentools können Sie Ihre Apps erstellen, ausführen und bereitstellen. Zum Einstieg können Sie das in diesem Abschnitt vorgestellte durchgängige Entwicklungsszenario befolgen.

## Schritt 1: {{site.data.keyword.Bluemix_notm}}-Konto registrieren
{: #sign-up}

Rufen Sie die Seite [bluemix.net](bluemix.net) auf. Geben Sie dort einfach E-Mail-Adresse, Namen, Unternehmen, Region und Telefonnummer ein. Zur Registrierung für ein kostenloses Konto benötigen Sie keine Kreditkarte. Danach können Sie sich einfach einmal umsehen.

## Schritt 2: Katalog durchsuchen
{: #catalog}

Im {{site.data.keyword.Bluemix_notm}}-Katalog sind die verfügbaren Infrastruktur- und Plattformressourcen aufgeführt. Sie können die Erstellung Ihrer App damit beginnen, dass Sie eine virtuelle Maschine, einen Container oder aber Cloudant (also eine Cloud Foundry-App) auswählen. Falls Sie Plattformressourcen benötigen, bietet {{site.data.keyword.Bluemix_notm}} außerdem Boilerplates, die Laufzeiten und andere Service bereitstellen, mit denen Ihnen der Einstieg in die Entwicklung erleichtert wird.

## Schritt 3: Ressource erstellen
{: #resource}

1. Klicken Sie im [Dashboard](https://console.bluemix.net/dashboard/apps/) auf **Ressource erstellen**.

2. Wählen Sie im Abschnitt 'Plattform' des Katalogs eine App aus. Wählen Sie anschließend die Laufzeit aus. Sie können beispielsweise eine der IBM Laufzeitumgebungen wie 'Liberty for Java' auswählen, die durch IBM Buildpacks unterstützt werden. Sie können aber auch Community-Laufzeiten wie beispielsweise 'Tomcat' auswählen, die sich auf Open-Source- und Drittanbieter-Buildpacks stützen.

  * [Einführung in Container](../containers/container_index.html)
  * [Einführung in Openwhisk](../openwhisk/index.html)
  * [Cloud Foundry-Apps erstellen](../cfapps/index.html#creating_cloud_foundry_apps)

3. Geben Sie den Namen Ihrer App sowie den Hostnamen ein und wählen Sie Ihren Preistarif aus.

4. Wählen Sie Ihren Entwicklungsstil aus. Sie können die App im Texteditor Ihrer Wahl bearbeiten und sie über die {{site.data.keyword.Bluemix_notm}}-Befehlszeile in {{site.data.keyword.Bluemix_notm}} bereitstellen. Außerdem können Sie Ihre App mithilfe von {{site.data.keyword.Bluemix_notm}} DevOps Services über einen Browser bereitstellen oder die Eclipse-Tools für {{site.data.keyword.Bluemix_notm}} nutzen, um in der integrierten Eclipse-Entwicklungsumgebung an Apps zu arbeiten.

## Schritt 4: Code hinzufügen
{: #code}

Jede App enthält einen Einführungsabschnitt, in dem Sie erfahren, welche Software und Inhalte Sie benötigen, um mit der Arbeit beginnen zu können.

Klicken Sie im Dashboard auf Ihre App und dann auf **Einführung**. Anschließend erhalten Sie Hinweise auf die Software, die Sie für die Entwicklung Ihrer App benötigen, Verweise auf den Quellcode sowie Hilfe bei der erstmaligen Bereitstellung Ihrer App.

## Nächste Schritte
{: #next}

Nachdem Sie Ihre App entwickelt haben, können Sie mithilfe der Informationen in den Abschnitten über die [Best Practices](best-practice.html) und die [Vorbereitung für die Cloud](cloud-ready.html) feststellen, ob Ihre App für {{site.data.keyword.Bluemix_notm}} geeignet ist. Anschließend können Sie Ihre App [bereitstellen](../starters/install_cli.html).
