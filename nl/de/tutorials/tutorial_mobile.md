---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-17"

keywords: apps, mobile, mobile app, starter kit, developer tools, devops toolchain, toolchain, create mobile app, mobile starter kit, android, ios, swift, xcode

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Mobile App erstellen
{: #tutorial-mobile}

{{site.data.keyword.cloud}} stellt Starter-Kits für Mobilgeräte bereit, die Sie bei der schnellen Erstellung einer mobilen Anwendung unterstützen. Wählen Sie aus den mobilen Starter-Kits eine Sprache, ein Framework und Tools aus, um mit der Arbeit mit einer vorkonfigurierten App zu beginnen. Sie können auch ein Basis-Starter-Kit verwenden, um eine benutzerdefinierte mobile App zu erstellen.
{: shortdesc}

## Vorbereitende Schritte
{: #prereqs-mobile}

Installieren Sie die [{{site.data.keyword.dev_cli_long}}-Befehlszeilenschnittstelle](/docs/cli?topic=cloud-cli-getting-started).

## Mobile App mit einem Starter-Kit erstellen
{: #create-mobile}

Führen Sie die folgenden Schritte aus, um eine mobile App unter Verwendung eines Starter-Kits zu erstellen:

1. Wählen Sie auf der Seite [Mobile Starter-Kits ](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") in der {{site.data.keyword.dev_console}} ein Starter-Kit auf der Basis der gewünschten Features aus. Beispiel: Wählen Sie **Watson Visual Recognition** aus.
2. Geben Sie Ihren App-Namen ein. Verwenden Sie im Rahmen dieses Lernprogramms `WatsonApp`.
3. Optional. Geben Sie Tags an, um Ihre App zu klassifizieren. Weitere Informationen finden Sie in [Mit Tags arbeiten](/docs/resources?topic=resources-tag).
4. Wählen Sie Ihre Plattform aus. Wählen Sie für dieses Lernprogramm **iOS Swift**aus. Einige Starter-Kits sind möglicherweise in nur einer Sprache verfügbar.
5. Wählen Sie Ihren Preisstrukturplan aus. Verwenden Sie für dieses Lernprogramm die Option **Lite**. Wenn Services erforderlich sind, werden sie automatisch im Starter-Kit definiert.
6. Klicken Sie auf **Erstellen**.

## Angepasste mobile App erstellen
{: #create-mobile-basic}

Führen Sie die folgenden Schritte aus, um eine angepasste mobile App zu erstellen:

1. Wählen Sie auf der Seite [Mobile Starter-Kits](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") in {{site.data.keyword.dev_console}} die Kachel **App erstellen** aus.
2. Geben Sie einen Namen für Ihre App ein. Geben Sie für dieses Lernprogramm `CustomMobile` ein.
3. Optional können Sie Tags angeben, um Ihre App zu klassifizieren. Weitere Informationen finden Sie in [Mit Tags arbeiten](/docs/resources?topic=resources-tag).
4. Wählen Sie **Neue App erstellen** als Ausgangspunkt aus.
5. Wählen Sie **Mobile** als App-Typ aus.
6. Wählen Sie Ihre Sprache und Ihr Framework aus. Einige Starter-Kits sind möglicherweise in nur einer Sprache verfügbar.
7. Wählen Sie Ihren Preisstrukturplan aus. Sie können für dieses Lernprogramm die kostenfreie Option verwenden.
8. Klicken Sie auf **Erstellen**.

## Mobile App mit der Befehlszeilenschnittstelle erstellen
{: #create-mobile-cli}

Führen Sie die folgenden Schritte aus, um eine mobile App mit der [{{site.data.keyword.dev_cli_long}}-Befehlszeilenschnittstelle (CLI)](/docs/cli?topic=cloud-cli-getting-started) zu erstellen:

1. Öffnen Sie ein Terminal und navigieren Sie zu einem Verzeichnis, in dem Sie Ihre App erstellen möchten.
2. Führen Sie den Befehl `ibmcloud dev create` aus.
3. Wählen Sie die Option **Mobile App** aus der Liste der App-Typen aus.
4. Wählen Sie eine mobile Plattform aus der Liste: Android oder Swift.
5. Wählen Sie ein Starter-Kit aus.
6. Geben Sie einen Namen für Ihre App ein.
7. Wenn Services hinzugefügt werden, werden Sie aufgefordert, für jeden Service eine Region und einen Preisplan auszuwählen.

Die App wird in Ihrem aktuellen Arbeitsverzeichnis erstellt.

## Services hinzufügen (optional)
{: #resources-mobile}

Je nachdem, welches Starter-Kit Sie ausgewählt haben, sind einige Services möglicherweise bereits mit Ihrer App verbunden. Sie können Services, die Ihre App mit der kognitiven Leistung von Watson funktional erweitern, mobile Services oder Sicherheitsservices hinzufügen. Im Rahmen dieses Lernprogramms fügen Sie eine Position für die Verwaltung Ihrer Daten hinzu.

Führen Sie die folgenden Schritte aus, um einen Service zu Ihrer App hinzuzufügen:

1. Klicken Sie auf der Seite **App-Details** auf **Service erstellen**.
2. Wählen Sie den Typ des gewünschten Service aus. Wählen Sie beispielsweise **Datenbanken** > **Weiter** > **Cloudant** > **Weiter** aus.
3. Wählen Sie Ihren Preisstrukturplan aus. Verwenden Sie für dieses Lernprogramm die Option **Lite**.
4. Klicken Sie auf **Erstellen**.

## Code herunterladen
{: #mobile-download-code}

Führen Sie die folgenden Schritte aus, um Ihren App-Code herunterzuladen und mit ihm lokal zu arbeiten:

1. Klicken Sie auf der Seite **App-Details** auf **Code herunterladen**.
2. Importieren Sie die App in die integrierte Entwicklungsumgebung.
3. Ändern Sie den Code und speichern Sie ihn.

## Mobile App ausführen
{: #run-mobile-app}

### Swift-App in Xcode ausführen
{: #run_swift}

Wenn Sie iOS Swift als Ihre Implementierungssprache verwenden, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die Datei `README.md` in einem Markdown Viewer, um die Schritte zur Konfiguration Ihrer App zu überprüfen.
2. Öffnen Sie Ihr Terminal, navigieren Sie zu Ihrem App-Ordner und führen Sie die folgenden Befehle aus:
    1. Führen Sie `pod setup` aus, wenn Sie Ihr CocoaPods-Repository einrichten müssen.
    2. Führen Sie `pod update` aus, wenn Sie Ihre vorhandenen Pods aktualisieren müssen.
    3. Führen Sie `pod install` aus, um die Pods für Ihre App zu installieren.
3. Öffnen Sie Ihren `<appname>.xcworkspace` Xcode-Arbeitsbereich.
4. Führen Sie Ihre App aus.

### Android-App in Android Studio ausführen
{: #run_android}

Wenn Sie Android als Plattform für Ihre mobile App verwenden, führen Sie die folgenden Schritte aus:

1. Öffnen Sie die Datei `README.md` in einem Markdown Viewer, um Ihre App zu konfigurieren.
2. Öffnen Sie Ihre App `BasicProject-Android` in Android Studio.
3. Führen Sie Ihre App aus.

## Zugehörige Informationen
{: #related-mobile}

Erkunden Sie diese Lernprogramme, um mehr über mobile Apps zu erfahren:

 * [Mobile iOS-App mit Push-Benachrichtigungen](/docs/tutorials?topic=solution-tutorials-ios-mobile-push-analytics)
 * [Mobile Android-App mit Push-Benachrichtigungen](/docs/tutorials?topic=solution-tutorials-android-mobile-push-analytics)
 * [Mobile App mit einem serverlosen Back-End](/docs/tutorials?topic=solution-tutorials-serverless-mobile-backend)
