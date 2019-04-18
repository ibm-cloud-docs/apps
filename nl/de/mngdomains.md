---

copyright:
  years: 2019
lastupdated: "2019-03-15"

keywords: apps, domain, Kubernetes, Cloud Foundry, cli

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Domäne aktualisieren
{: #update-domain}

Mithilfe von Domänen wird die URL-Route angegeben, die Ihrer Organisation in {{site.data.keyword.cloud}} zugeordnet ist. Bei Cloud Foundry-Apps können Sie Ihre Domäne von `mybluemix.net` nach `appdomain.cloud` migrieren, indem Sie entweder die {{site.data.keyword.cloud_notm}}-Konsole oder die Befehlszeilenschnittstelle verwenden.{:shortdesc}

## Domänen über die {{site.data.keyword.cloud_notm}}-Konsole aktualisieren
{: #update-domain-console}

Die gemeinsam genutzte Standarddomäne ist `mybluemix.net`, aber `appdomain.cloud` ist eine weitere Domänenoption, die Sie verwenden können.
{: tip}

Führen Sie die folgenden Schritte aus, um die Domäne für Ihre Cloud Foundry-Organisation über die Konsole zu aktualisieren:

1. Klicken Sie in der [{{site.data.keyword.cloud_notm}}-Konsole ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://{DomainName}){: new_window} auf das Symbol **Menü** ![Menüsymbol](../icons/icon_hamburger.svg) und wählen Sie **Ressourcenliste** aus.
2. Klicken Sie auf der Seite **Ressourcenliste** auf **Cloud Foundry-Apps**.
3. Klicken Sie auf die Anwendung, für die Sie die Domäne ändern möchten. Die Seite **Übersicht** der App wird angezeigt.
4. Wählen Sie das Menü **Routen** aus, suchen Sie die aktuelle Domäne, z. B. `.<myapp.mybluemix.net>`, und klicken Sie auf **Routen bearbeiten**.
5. Wählen Sie die Liste der Domänen aus und klicken Sie anschließend auf die Domäne, die Sie verwenden möchten, z. B. `us-south.cf.appdomain.cloud`.
6. Bestätigen Sie Ihre Aktualisierungen, indem Sie auf **Speichern** klicken.
7. Bestätigen Sie, dass Sie die alte Domäne ersetzen möchten, und klicken Sie auf **Entfernen**.
8. Klicken Sie auf **App-URL aufrufen**, um zu prüfen, ob die neue Route funktioniert.

## Domänen über die {{site.data.keyword.cloud_notm}}-Befehlszeilenschnittstelle aktualisieren
{: #update-domain-cli}

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

2. Fügen Sie die Route mit der neuen Domäne einer Anwendung hinzu, indem Sie den folgenden Befehl eingeben:
   ```
   ibmcloud app route-map APP-NAME DOMÄNE -n HOSTNAME
   ```

## Domäne für Kubernetes-Apps aktualisieren
{: #update-domain-kube}

Die Unterdomäne für {{site.data.keyword.containerlong}}-Hostnamen ist `containers.appdomain.cloud`. Der von IBM bereitgestellte Ingress-Unterdomänenplatzhalter `*.<cluster_name>.<region>.containers.appdomain.cloud` ist standardmäßig für Ihren Cluster registriert. Das von IBM bereitgestellte TLS-Zertifikat ist ein Platzhalterzertifikat und kann für die Platzhalterunterdomäne verwendet werden. Weitere Informationen finden Sie unter [Mehrere Domänen in einem Namensbereich](/docs/containers?topic=containers-ingress#multi-domains).
