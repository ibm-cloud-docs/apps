---

copyright:
  years: 2015, 2018
lastupdated: "2018-03-16"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Angepasste Domäne erstellen und verwenden
{: #updatingapps}

Sie können die Befehlszeile oder {{site.data.keyword.Bluemix}} Continuous Delivery verwenden, um die Anwendungen in {{site.data.keyword.Bluemix_notm}} zu aktualisieren. In vielen Fällen müssen Sie (selbst für die integrierten Buildpacks wie beispielsweise 'Node.js') auch den Parameter '-c' verwenden, um anzugeben, welcher Befehl zum Starten Ihrer Anwendung verwendet wird.
{:shortdesc}

Mithilfe von Domänen wird die URL-Route angegeben, die Ihrer Organisation in {{site.data.keyword.Bluemix_notm}} zugeordnet ist. Um eine angepasste Domäne zu verwenden, müssen Sie die angepasste Domäne auf einem öffentlichen DNS-Server registrieren, die angepasste Domäne in {{site.data.keyword.Bluemix_notm}} konfigurieren und die angepasste Domäne der {{site.data.keyword.Bluemix_notm}}-Systemdomäne auf dem öffentlichen DNS-Server zuordnen. Nachdem Ihre angepasste Domäne der Systemdomäne zugeordnet wurde, werden Anforderungen für Ihre angepasste Domäne an Ihre Anwendung in {{site.data.keyword.Bluemix_notm}} weitergeleitet.

Sie können eine angepasste Domäne erstellen und verwenden, indem Sie entweder die {{site.data.keyword.Bluemix_notm}}-Konsole oder die -Befehlszeilenschnittstelle verwenden.

## {{site.data.keyword.Bluemix_notm}}-Konsole verwenden

Führen Sie die folgenden Schritte aus, um mithilfe der Konsole eine angepasste Domäne für Ihre Organisation zu erstellen:

1. Wechseln Sie zu **Verwalten** &gt; **Konto** &gt; **Cloud Foundry-Organisationen**.
2. Klicken Sie auf den Namen der Organisation, für die Sie eine angepasste Domäne erstellen.
3. Klicken Sie auf die Registerkarte **Domänen**.
4. Klicken Sie auf **Domäne hinzufügen**, geben Sie Ihren Domänennamen ein und wählen Sie die Region aus.
5. Bestätigen Sie Ihre Aktualisierungen. Klicken Sie auf **Hinzufügen**. 

Sie können beispielsweise `*.mycompany.com` verwenden, um die Route `www.mybluemix.com` Ihrer App zuzuordnen. Sie können auch `example.mycompany.com` verwenden, um die Route `www.example.mybluemix.com` Ihrer App hinzuzufügen.
{: tip}

Fügen Sie die Route mit der angepassten Domäne einer Anwendung hinzu.

1. Klicken Sie auf das Symbol **Menü** ![Menüsymbol](../icons/icon_hamburger.svg) &gt; **Dashboard**. Klicken Sie dann auf die Zeile für die Anwendung, der Sie die Route hinzufügen möchten. Die Seite **Übersicht** wird angezeigt.
2. Wählen Sie im Menü **Routen** die Option **Routen bearbeiten** aus.
3. Klicken Sie auf **Route hinzufügen**. Geben Sie die Route an, die Sie für die Anwendung verwenden möchten.
4. Bestätigen Sie Ihre Aktualisierungen, indem Sie auf **Speichern** klicken.

## {{site.data.keyword.Bluemix_notm}}-Befehlszeilenschnittstelle verwenden

1. Erstellen Sie eine angepasste Domäne für Ihre Organisation, indem Sie den folgenden Befehl eingeben:

   ```
   bluemix app domain-create <Organisationsname> mydomain
   ```

2. Fügen Sie die Route mit der angepassten Domäne zu einer Anwendung hinzu. Geben Sie für CF-Apps den folgenden Befehl ein:

   ```
   bluemix app route-map myapp mydomain -n host_name

   ```

   Geben Sie für Containergruppen den folgenden Befehl ein:

   ```
   cf ic route map -n host_name -d mydomain mycontainergroup

   ```

Nach der Konfiguration der angepassten Domäne in {{site.data.keyword.Bluemix_notm}} ordnen Sie die angepasste Domäne der {{site.data.keyword.Bluemix_notm}}-Systemdomäne auf Ihrem registrierten DNS-Server zu:

1. Richten Sie einen Datensatz 'CNAME' für den Namen der angepassten Domäne auf Ihrem DNS-Server ein. Die Schritte zum Einrichten des CNAME-Datensatzes hängen von Ihrem DNS-Provider ab. Beispiel: Wenn Sie GoDaddy verwenden, befolgen Sie die Anleitung [Domains Help ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} von GoDaddy.
2. Ordnen Sie den Namen der angepassten Domäne dem sicheren Endpunkt für die {{site.data.keyword.Bluemix_notm}}-Region zu, in der Ihre Anwendung ausgeführt wird. Verwenden Sie die folgenden Regionsendpunkte, um die URL-Route anzugeben, die Ihrer Organisation in {{site.data.keyword.Bluemix_notm}} zugeordnet ist:

  * US-SOUTH: `secure.us-south.bluemix.net`
  * US-EAST: `secure.us-east.bluemix.net`
  * EU-DE: `secure.eu-de.bluemix.net`
  * EU-GB: `secure.eu-gb.bluemix.net`
  * AU-SYD: `secure.au-syd.bluemix.net`

Geben Sie die folgende URL in einen Browser oder eine Befehlszeilenschnittstelle ein, um auf die Anwendung 'myapp' zuzugreifen:

```
http://host_name.mydomain

```

Führen Sie den folgenden Befehl aus, um eine verwaiste Route zu entfernen:

```
bluemix app route-delete domain -n hostname -f

```
{: tip}

`domain` ist der Name Ihrer Domäne und `hostname` ist der Hostname der Route für Ihre Anwendung. Weitere Informationen zum Befehl **bluemix app route-delete** erhalten Sie, wenn Sie Folgendes eingeben: `bluemix app route-delete -h`.

