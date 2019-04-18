---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-15"

keywords: apps, custom domain, Kubernetes

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Angepasste Domäne hinzufügen und verwenden
{: #updatingapps}

Mithilfe von Domänen wird die URL-Route angegeben, die Ihrer Organisation in {{site.data.keyword.cloud}} zugeordnet ist. Angepasste Domänen leiten Anforderungen für Ihre Anwendungen an eine Ihnen gehörende URL. Eine angepasste Domäne kann eine gemeinsame Domäne, eine gemeinsame Unterdomäne oder eine gemeinsame Domäne und ein gemeinsamer Host sein. Wenn keine angepasste Domäne angegeben ist, verwendet {{site.data.keyword.cloud_notm}} eine gemeinsam genutzte Standarddomäne in der Route für Ihre Anwendung. Sie können eine angepasste Domäne erstellen und verwenden, indem Sie entweder die {{site.data.keyword.cloud_notm}}-Konsole oder die -Befehlszeilenschnittstelle verwenden.
{:shortdesc}

Die gemeinsam genutzte Standarddomäne ist `mybluemix.net`, aber `appdomain.cloud` ist eine weitere Domänenoption, die Sie verwenden können. Weitere Informationen zur Migration auf `appdomain.cloud` finden Sie im Abschnitt zum [Aktualisieren Ihrer Domäne](/docs/apps/tutorials?topic=creating-apps-update-domain).
{: tip}

Um eine angepasste Domäne zu verwenden, müssen Sie die angepasste Domäne auf einem öffentlichen DNS-Server registrieren und dann die angepasste Domäne in {{site.data.keyword.cloud_notm}} konfigurieren. Dann müssen Sie die angepasste Domäne der {{site.data.keyword.cloud_notm}}-Systemdomäne auf dem öffentlichen DNS-Server zuordnen. Nachdem Ihre angepasste Domäne der Systemdomäne zugeordnet wurde, werden Anforderungen für Ihre angepasste Domäne an Ihre Anwendung in {{site.data.keyword.cloud_notm}} weitergeleitet.

## Angepasste Domäne über die {{site.data.keyword.cloud_notm}}-Konsole hinzufügen

{: #custom-domain-console}

Führen Sie diese Schritte aus, um mithilfe der Konsole eine angepasste Domäne für Ihre Organisation hinzuzufügen:

1. Wechseln Sie zu **Verwalten > Konto** und wählen Sie **Cloud Foundry-Organisationen** aus.
2. Klicken Sie auf den Namen der Organisation, für die Sie eine angepasste Domäne erstellen.
3. Klicken Sie auf die Registerkarte **Domänen**, um eine Liste der verfügbaren Domänen anzuzeigen.
4. Klicken Sie auf **Domäne hinzufügen**, geben Sie Ihren Domänennamen ein und wählen Sie die Region aus.
5. Bestätigen Sie Ihre Aktualisierungen und klicken Sie auf **Hinzufügen**.

## Route mit der angepassten Domäne einer Anwendung hinzufügen

1. Klicken Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") auf das Symbol **Menü** ![Menüsymbol](../../icons/icon_hamburger.svg) und wählen Sie **Ressourcenliste** aus.
2. Klicken Sie auf der Seite **Ressourcenliste** auf **Cloud Foundry-Apps**.
3. Klicken Sie auf die Anwendung, der Sie die Route hinzufügen möchten. Die Seite **Übersicht** der App wird angezeigt.
4. Wählen Sie das Menü **Routen** aus und wählen Sie **Routen bearbeiten** aus.
5. Klicken Sie auf **Route hinzufügen**. Geben Sie die Route an, die Sie für die Anwendung verwenden möchten.
6. Bestätigen Sie Ihre Aktualisierungen, indem Sie auf **Speichern** klicken.

Sie können beispielsweise `*.mycompany.com` verwenden, um die Route `www.mybluemix.net` Ihrer App zuzuordnen. Sie können auch `example.mycompany.com` verwenden, um die Route `www.example.bluemix.net` Ihrer App zuzuordnen.
{: tip}

## Angepasste Domäne über die {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle hinzufügen
{: #custom-domain-cli}

1. Stellen Sie für Cloud Foundry-Apps eine Verbindung zu Ihrem Ziel-Cloud Foundry-API-Endpunkt her, indem Sie den folgenden Befehl eingeben:
   ```
   ibmcloud target --cf-api <CF-ENDPUNKT>
   ```
   
   **Cloud Foundry-API-Endpunkte:**
   * US-SOUTH - `api.us-south.cf.cloud.ibm.com`
   * US-EAST - `api.us-east.cf.cloud.ibm.com`
   * EU-DE - `api.eu-de.cf.cloud.ibm.com`
   * EU-GB - `api.eu-gb.cf.cloud.ibm.com`
   * AU-SYD - `api.au-syd.cf.cloud.ibm.com`
   
2. Erstellen Sie eine angepasste Domäne für Ihre Organisation, indem Sie den folgenden Befehl eingeben:
   ```
   ibmcloud app domain-create <MEIN_ORGNAME> <MEINE_DOMÄNE>
   ```

3. Fügen Sie die Route mit der angepassten Domäne einer Anwendung hinzu.

   Geben Sie für Cloud Foundry-Apps den folgenden Befehl ein:
   ```
   ibmcloud app route-map <MEIN_APPNAME> <MEINE_DOMÄNE> -n <MEIN_HOSTNAME>
   ```
   
## Angepasste Domäne der Systemdomäne zuordnen
{: #mapcustomdomain}

Nach der Konfiguration der angepassten Domäne in {{site.data.keyword.cloud_notm}} ordnen Sie die angepasste Domäne der {{site.data.keyword.cloud_notm}}-Systemdomäne auf Ihrem registrierten DNS-Server zu:

1. Richten Sie einen Datensatz 'CNAME' für den Namen der angepassten Domäne auf Ihrem DNS-Server ein. Die Schritte zum Einrichten des CNAME-Datensatzes hängen von Ihrem DNS-Provider ab. Beispiel: Wenn Sie GoDaddy verwenden, folgen Sie den Anweisungen unter [Domains Help ](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") von GoDaddy.
2. Ordnen Sie den Namen der angepassten Domäne dem sicheren Endpunkt für die {{site.data.keyword.cloud_notm}}-Region zu, in der Ihre Anwendung ausgeführt wird. Geben Sie die URL-Route, die Ihrer Organisation in {{site.data.keyword.cloud_notm}} zugeordnet ist, mithilfe der nachfolgenden Regionsendpunkte an. Lassen Sie z. B. Ihren CNAME verweisen auf `<custom-domain>.us-east.cf.cloud.ibm.com.`

  **Cloud Foundry-Endpunkte:**
  * US-SOUTH - `custom-domain.us-south.cf.cloud.ibm.com`
  * US-EAST - `custom-domain.us-east.cf.cloud.ibm.com`
  * EU-DE - `custom-domain.eu-de.cf.cloud.ibm.com`
  * EU-GB - `custom-domain.eu-gb.cf.cloud.ibm.com`
  * AU-SYD - `custom-domain.au-syd.cf.cloud.ibm.com`

## Auf Ihre Anwendung zugreifen
{: #access-app}

Geben Sie in einem Browser die folgende URL ein, um auf Ihre Anwendung zuzugreifen. Dabei ist `hostname` Ihr Hostname und `mydomain` Ihr Domänenname:
```
http://hostname.mydomain
```

## Verwaiste Route entfernen
{: #remove-orphaned-route}

Führen Sie den folgenden Befehl aus, um eine verwaiste Route zu entfernen:
```
ibmcloud app route-delete <MEINE_DOMÄNE> -n <MEIN_HOSTNAME> -f
```
{: tip}

Bei diesem Beispiel steht `domain` für den Namen Ihrer Domäne und `hostname` für den Hostnamen der Route für Ihre Anwendung. Weitere Informationen zum Befehl `ibmcloud app route-delete` erhalten Sie, indem Sie den Befehl `ibmcloud app route-delete -h` eingeben.

## Angepasste Domäne für Kubernetes-Apps verwenden
{: #kube-custom-domain}

Die Unterdomäne für IBM Cloud Kubernetes Service-Hostnamen ist `containers.appdomain.cloud`. Der von IBM bereitgestellte Ingress-Unterdomänenplatzhalter `*.<cluster_name>.<region>.containers.mybluemix.net` ist standardmäßig für Ihren Cluster registriert. Das von IBM bereitgestellte TLS-Zertifikat ist ein Platzhalterzertifikat und kann für die Platzhalterunterdomäne verwendet werden. Wenn Sie eine angepasste Domäne verwenden möchten, müssen Sie die angepasste Domäne als Platzhalterdomäne registrieren, z. B. `*.custom_domain.net`. Um TLS verwenden zu können, müssen Sie ein Platzhalterzertifikat abrufen. Weitere Informationen finden Sie unter [Mehrere Domänen in einem Namensbereich](/docs/containers?topic=containers-ingress#multi-domains).

Beschäftigen Sie sich mit [diesem Lernprogramm](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes), das Sie begleitet beim Erstellen eines Gerüsts für eine Webanwendung, beim lokalen Ausführen der Anwendung in einem Container und beim anschließenden Bereitstellen in einem Kubernetes-Cluster, der mit IBM Kubernetes Service erstellt wurde. Darüber hinaus erfahren Sie, wie Sie eine angepasste Domäne binden, den Zustand der Umgebung überwachen und die Anwendung skalieren.
