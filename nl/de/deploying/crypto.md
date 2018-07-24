---

copyright:
  years: 2018
lastupdated: "2018-07-23"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Schlüssel und Daten durch Verschlüsselungstechnologie schützen
{: #crypto}

{{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}} macht die IBM Z-Verschlüsselung in der Cloud verfügbar. {{site.data.keyword.cloud_notm}} bietet dieselbe Verschlüsselungstechnologie an, die auch für Bank- und Finanzservices eingesetzt wird.
{:shortdesc}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} schützt Ihre Schlüssel sowie Ihre ruhenden, in Gebrauch befindlichen und übertragenen Daten mit der höchsten Sicherheitsstufe der Branche - FIPS 140-2 Level 4. {{site.data.keyword.hscrypto}} ist der Keystore für den [{{site.data.keyword.keymanagementservicelong_notm}}](/docs/services/hs-crypto/index.html)-Service und schützt Ihre Schlüssel in einer Umgebung auf besonders hohem Sicherheitsniveau in IBM Z.

## ACSP-Client installieren und konfigurieren
{: ##crypto_config}

Erstellen Sie vor der Installation des ACSP-Clients (Advanced Cryptography Service Provider) eine Instanz von {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} über den [Katalog ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/catalog/services/hyper-protect-crypto-services){:new_window} und stellen Sie sie bereit. Anschließend müssen Sie den (ASCP-) Client in Ihrer Umgebung installieren und konfigurieren.

1. Laden Sie das Installationspaket aus dem [GitHub-Repository ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://github.com/ibm-developer/ibm-cloud-hyperprotectcrypto){:new_window} herunter. Wählen Sie im Ordner **Pakete** die Installationspaketdatei aus, die für das verwendete Betriebssystem und die verwendete CPU-Architektur geeignet ist. Wählen Sie beispielsweise für Ubuntu in x86 `acsp-pkcs11-client_1.5-3.5_amd64.deb` aus.
2. Installieren Sie das Paket für die Installation der ACSP-Clientbibliotheken mit dem Befehl `dpkg`. Beispiel: `dpkg -i acsp-pkcs11-client_1.5-3.5_amd64.deb`.
3. Wählen Sie in Ihrer Serviceinstanz von {{site.data.keyword.hscrypto}} in {{site.data.keyword.cloud_notm}} die Option **Verwalten** im Navigator aus.
4. Klicken Sie im Verwaltungsfenster auf **Konfiguration herunterladen**, um die Datei `acsp_client_credentials.uue` herunterzuladen.
5. Kopieren Sie die Datei `acsp_client_credentials.uue` in das Verzeichnis `/opt/ibm/acsp-pkcs11-client/config` in der lokalen Umgebung.
6. Decodieren Sie die Datei im Verzeichnis `/opt/ibm/acsp-pkcs11-client/config` mit dem folgenden Befehl:
   ```
   base64 --decode acsp_client_credentials.uue > acsp_client_credentials.tar
   ```
   {: codeblock}
7. Extrahieren Sie die Clientberechtigungsnachweisdatei mit dem folgenden Befehl:
   ```
   tar xf acsp_client_credentials.tar
   ```
   {: codeblock}
8. Verschieben Sie die `server-config`-Dateien mit dem folgenden Befehl an die Standardposition:
   ```
   mv server-config/* ./
   ```
   {: codeblock}
9. Benennen Sie die Clientberechtigungsnachweisdatei mit dem folgenden Befehl um:
   ```
   mv acsp.properties.client acsp.properties
   ```
   {: codeblock}
10. (Optional) Ändern Sie die Gruppen-ID der Dateien mit dem folgenden Befehl:
    ```
    chown root.pkcs11 *
    ```
    {: codeblock}
11. Ermöglichen Sie ACSP die Verwendung der entsprechenden Konfiguration für die Serviceinstanz in der Cloud:
    ```
    export ACSP_P11=/opt/ibm/acsp-pkcs11-client/config/acsp.properties
    ```
    {: codeblock}

Nun ist der ACSP-Client betriebsbereit und {{site.data.keyword.hscrypto}} kann verwendet werden.

## Nächste Schritte
{: ##next-steps}

Eine einfache Möglichkeit, {{site.data.keyword.cloud_notm}} {{site.data.keyword.hscrypto}} zu verwenden, ist der Einstieg mit {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}. Weitere Informationen zu {{site.data.keyword.hsplatform}} finden Sie in [Einführung in {{site.data.keyword.cloud_notm}} {{site.data.keyword.hsplatform}}](/docs/services/hypersecure-platform/index.html).
