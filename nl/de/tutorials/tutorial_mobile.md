---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-03-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Mobile Anwendung mit einem Starter-Kit erstellen
{: #tutorial}

Sie können ein mobiles Projekt aus einem entsprechenden grundlegenden Starter erstellen. Darin erfahren Sie, wie die erforderlichen Tools installiert werden, und lernen die einzelnen Schritte zur Ausführung des Projekts in Xcode und Android Studio kennen.
{: shortdesc}

## Tools installieren
{: #before-you-begin}

Installieren Sie die [Entwicklertools](/docs/cli/idt/index.html#add-cli){: new_window}. 


## Vorgehensweise zur Erstellung Ihres Projekts auswählen
{: #choose_how}

Sie können ein Projekt mithilfe einer der folgenden Methoden erstellen: 
- Webbasierte [{{site.data.keyword.dev_console}}](#create-devex)
- Lokale befehlsgesteuerte [{{site.data.keyword.dev_cli_notm}}](#create-cli)


## Projekt mit der {{site.data.keyword.dev_console}} erstellen 
{: #create-devex}

1. Erstellen Sie ein {{site.data.keyword.dev_console}}-Projekt in {{site.data.keyword.Bluemix}}. 

    1. Wählen Sie auf der Seite [Starter-Kits ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) in der {{site.data.keyword.dev_console}} ein Starter-Kit auf der Grundlage der gewünschten Funktionalitäten aus. Wechseln Sie für eine Watson Language-Anwendung beispielsweise zu **Watson Language** und klicken Sie auf **Starter-Kit auswählen**. 

    2. Geben Sie Ihren Projektnamen ein. Verwenden Sie im Rahmen dieses Lernprogramms `WatsonProject`.    

    3. Wählen Sie Ihre Sprachplattform aus. Verwenden Sie im Rahmen dieses Lernprogramms `Swift`. 

    4. Klicken Sie auf **Projekt erstellen**. 

### Optional: Services hinzufügen
{: #add-services}

1. Wählen Sie Ihr Projekt auf der Seite **Projekte** aus. 

2. Klicken Sie auf **Service hinzufügen**. 

3. Wählen Sie den Typ des gewünschten Service aus. Wählen Sie im Rahmen dieses Lernprogramms **Sicherheit** > **Weiter** > **App-ID** > **Weiter** aus. 

4. Geben Sie Ihren Servicenamen ein und klicken Sie auf **Erstellen**. 

5. Weitere Informationen zum Konfigurieren der Authentifizierung finden Sie unter [Identitätsprovider konfigurieren ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/appid/identity-providers.html){: new_window}. 

6. Weitere Informationen zum Konfigurieren von Analysen finden Sie unter [Einführung in {{site.data.keyword.mobileanalytics_short}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/mobileanalytics/index.html){: new_window}. 

7. Weitere Informationen zum Konfigurieren von {{site.data.keyword.cloudant_short_notm}} finden Sie unter [Einführung in {{site.data.keyword.cloudant_short_notm}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/Cloudant/index.html){: new_window}. 

8. Weitere Informationen zum Konfigurieren von {{site.data.keyword.objectstorageshort}} finden Sie unter [Einführung in {{site.data.keyword.objectstorageshort}} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](/docs/services/ObjectStorage/index.html){: new_window}. 

9. Weitere Informationen zum Hinzufügen von Push-Benachrichtigungen finden Sie in der [Dokumentation zu Push-Benachrichtigungen](/docs/services/mobilepush/c_overview_push.html#overview-push). 

### Projektcode generieren
{: #generate-code}

1. Wählen Sie Ihr Projekt auf der Seite **Projekte** aus. 

2. Klicken Sie auf **Code herunterladen**, um Ihr Projektarchiv herunterzuladen. 


### Arbeit an Ihrer App beginnen
{: #code}

Beginnen Sie, mit Ihrem heruntergeladenen Projekt zu arbeiten: 

1. Erweitern Sie die archivierte Datei. 

2. Navigieren Sie zum neuen Projektverzeichnis. 

3. Fahren Sie in der {{site.data.keyword.dev_cli_notm}} fort. 


## Projekt mit der {{site.data.keyword.dev_cli_notm}} erstellen 
{: #create-cli}

1. Stellen Sie sicher, dass Sie die [{{site.data.keyword.dev_cli_short}}](/docs/cli/idt/index.html) installieren. 

2. Navigieren Sie in Ihrer Terminal-Eingabeaufforderung zu einem lokalen Verzeichnis Ihrer Wahl und führen Sie den folgenden Befehl aus. 

	```
	bx dev create
	```
	{: codeblock}

3. Geben Sie bei entsprechender Aufforderung die folgenden Werte an: 

	* Wählen Sie den Projekttyp 'Mobile Client', Option 2, aus.
	* Wählen Sie die Implementierungssprache 'iOS Swift', Option 3, aus. 
	* Wählen Sie das Starter-Kit 'Mobile App: Basic', Option 1, aus. 
	* Geben Sie einen Namen für Ihr Projekt ein: `MobileBasicProject`

    Hinweis: Die tatsächlichen Auswahlnummern können sich mit Toolerweiterungen ändern. 

4. Wenn Sie Services zu Ihrem Projekt hinzufügen möchten, geben Sie an der Eingabeaufforderung `y` ein und beantworten Sie die verbleibenden Fragen. 

5. Wenn Ihr `MobileBasicProject` erfolgreich erstellt und gespeichert wurde, navigieren Sie zum Ordner `MobileBasicProject/MobileBasicProject-Swift`. 

### Swift-Projekt in Xcode ausführen
{: #run_swift}

1. Öffnen Sie die Datei `README.md` in einem Markdown Viewer, um die Schritte zur Konfiguration Ihres Projekts zu überprüfen. 

2. Öffnen Sie Ihr Terminal, navigieren Sie zu Ihrem Projektordner und führen Sie die folgenden Befehle aus: 
    1. Führen Sie `pod setup` aus, wenn Sie Ihr CocoaPods-Repository einrichten müssen. 
    2. Führen Sie `pod update` aus, wenn Sie Ihre vorhandenen Pods aktualisieren müssen. 
    3. Führen Sie `pod install` aus, um die Pods für Ihr Projekt zu installieren. 

3. Öffnen Sie Ihren Xcode-Arbeitsbereich `<projectname>.xcworkspace`. 

4. Führen Sie Ihre App aus. 

### Cordova-Projekt in Xcode ausführen
{: #run_cordova_xcode}

Falls Sie ausgewählt haben, Cordova als Ihre Implementierungssprache zu verwenden, befolgen Sie diese Anweisungen. 

1. Öffnen Sie die Datei `README.md` in einem Markdown Viewer, um Ihr Projekt zu konfigurieren. 

2. Öffnen Sie Ihr Projekt `platforms/ios` in Xcode. 

3. Führen Sie Ihre App aus. 


### Cordova-Projekt in Android Studio ausführen
{: #run_cordova_studio}

Verwenden Sie diesen Abschnitt, wenn Sie Cordova als Plattform Ihrer mobilen App verwenden möchten. 

1. Extrahieren Sie die Datei `BasicProject-Cordova.zip`. 

2. Öffnen Sie die Datei `README.md` in einem Markdown Viewer, um Ihr Projekt zu konfigurieren. 

3. Öffnen Sie Ihr Projekt `platforms/android` in Android Studio. 

4. Führen Sie Ihre App aus. 


### Android-Projekt in Android Studio ausführen
{: #run_android}

Verwenden Sie diesen Abschnitt, wenn Sie Android als Plattform Ihrer mobilen App verwenden möchten. 

1. Öffnen Sie die Datei `README.md` in einem Markdown Viewer, um Ihr Projekt zu konfigurieren. 

2. Öffnen Sie Ihr Projekt `BasicProject-Android` in Android Studio. 

3. Führen Sie Ihre App aus. 
