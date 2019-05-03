---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-05"

keywords: byoc, code repository, continuous delivery, cli, deploy, create app custom repo, custom repo, existing repo, custom code

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Apps aus Ihrem eigenen Code-Repository erstellen
{: #tutorial-byoc}

Wenn Sie über eine Anwendung in einem vorhandenen Repository verfügen, können Sie mithilfe eines leeren Starter-Kits einen App-Datensatz in {{site.data.keyword.cloud_notm}} erstellen und die App mit Ihrem Quellenrepository und Ihrer DevOps-Toolchain verbinden.
{: shortdesc}

Sie können über das {{site.data.keyword.cloud_notm}}-Dashboard oder ein beliebiges leeres Starter-Kit starten. Nachdem Sie Ihre App benannt und eine Ressourcengruppe ausgewählt haben, wählen Sie den Ausgangspunkt **Eigenen Code integrieren** aus, geben Sie die URL des Git-Repositorys an, das Ihren Code enthält, und klicken Sie auf **Erstellen**.

Sie können Ihre vorhandene DevOps-Toolchain verbinden oder eine erstellen und eine App kontinuierlich für das Bereitstellungsziel Ihrer Wahl, wie z. B. Kubernetes oder Cloud Foundry, bereitstellen.

## Vorbereitende Schritte
{: #prereqs-byoc}

Stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

 * Installieren Sie die [{{site.data.keyword.dev_cli_long}}-Befehlszeilenschnittstelle](/docs/cli?topic=cloud-cli-ibmcloud-cli).
 * Lesen Sie [Bewährte Verfahren (Best Practices) für die Erstellung guter Apps](/docs/apps?topic=creating-apps-best-practice), um bewährte Verfahren zum Erstellen von Apps kennenzulernen.
 * Sie müssen über ein Git-Quellcode-Repository von einem der folgenden Anbieter verfügen: GitHub, GitHub Enterprise, GitLab, BitBucket oder Rational.
 * Wenn Sie vorhaben, Ihre App in [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about) bereitzustellen, müssen Sie [Ihr {{site.data.keyword.cloud_notm}}-Konto vorbereiten](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## App mit einem vorhandenen Repository erstellen
{: #create-byoc}

Führen Sie die folgenden Schritte aus, um eine App zu erstellen und sie mit Ihrem Quellenrepository zu verbinden:

1. Klicken Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}){: new_window} ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link") in der Kachel **Apps** auf **App erstellen**.
2. Benennen Sie Ihre App, wählen Sie eine Ressourcengruppe aus und geben Sie optional Tags an, um Ihre App zu klassifizieren. Weitere Informationen finden Sie in [Mit Tags arbeiten](/docs/resources?topic=resources-tag).
3. Wählen Sie **Eigenen Code integrieren** aus und geben Sie die URL für Ihr Git-Repository an. Ihre App und das Docker-Image müssen sich im selben Repository befinden.
4. Klicken Sie auf **Erstellen**. Die Seite **App-Details** wird angezeigt.
5. Optional. Sie können Ihrer App [Services hinzufügen](/docs/apps?topic=creating-apps-add-resource).
6. Optional. Sie können dieser App Tags hinzufügen, indem Sie auf **Tags hinzufügen**klicken, oder Tags bearbeiten, indem Sie auf das Symbol **Bearbeiten** ![Bearbeitungssymbol](../../icons/edit-tagging.svg) neben den angezeigten Tags klicken.
7. Optional. Klicken Sie auf **Repository anzeigen**, um das Repository anzuzeigen.

## App bereitstellen
{: #toolchain-byoc}

Die Erstellung einer Verknüpfung zwischen App, Toolchain und Repository ist ein Schritt zur Organisation Ihrer Produktassets. Außerdem hilft sie bei der Zusammenstellung einer Ansicht Ihres Quellenrepositorys mit Ihrem DevOps-Workflow, Ihren aktiven App-Instanzen und abhängigen Services über alle Ihre Bereitstellungsziele hinweg. Weitere Informationen finden Sie unter [Toolchains erstellen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

Sie können Continuous Delivery für Ihre App konfigurieren, indem Sie entweder die {{site.data.keyword.cloud_notm}}-Konsole oder die Befehlszeilenschnittstelle verwenden.

### Verwendung der Konsole
{: #console-byoc-toolchain}

#### Wenn Sie bereits über eine DevOps-Toolchain verfügen, die Sie mit Ihrer App verbinden möchten, führen Sie die folgenden Schritte aus:

1. Klicken Sie auf der Seite **App-Details** auf **Continuous Delivery konfigurieren**. Die Seite **App bereitstellen** wird angezeigt.
2. Wählen Sie die Toolchain aus, die an Ihre App angeschlossen werden soll, und klicken Sie auf **Bereitstellung aktivieren**. Die Seite **App-Details** wird angezeigt und zeigt an, dass Continuous Delivery konfiguriert ist.

#### Wenn Sie für diese App noch keine DevOps-Toolchain haben, führen Sie die folgenden Schritte aus:

1. Klicken Sie auf der Seite **App-Details** auf **DevOps-Toolchain erstellen**. Die Seite **Toolchain erstellen** wird angezeigt.
2. [Erstellen Sie die Toolchain](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).
3. Verwenden Sie den Breadcrumb-Pfad im Browserfenster, um zur Seite **App-Details** zurückzukehren. Dort wird angezeigt, dass Continuous Delivery konfiguriert wurde.

### Verwendung der Befehlszeilenschnittstelle
{: #cli-byoc-toolchain}

Sie können den Befehl `ibmcloud dev enable` verwenden, um eine DevOps-Toolchain-Vorlage zu generieren, die Sie in Ihrem Repository einchecken als Instruktionssatz für das, was die DevOps-Toolchain erstellen soll. 

  1. Klicken Sie auf der Seite **App-Details** auf **Repository anzeigen**, um lokal mit Ihrem Code zu arbeiten.
  2. Führen Sie den folgenden Befehl aus:
    
    ```
    ibmcloud dev enable
    ```
   {: codeblock}

Weitere Informationen finden Sie in [Apps über die Befehlszeilenschnittstelle erstellen und bereitstellen](/docs/apps?topic=creating-apps-create-deploy-app-cli).

## Ausführung der App verifizieren
{: #verify-byoc-app}

Die Delivery Pipeline oder Befehlszeile verweist auf die URL für Ihre App.

1. Klicken Sie in der Toolchain von DevOps auf **Delivery Pipeline** und wählen Sie **Bereitstellungsstage** aus.
2. Klicken Sie auf **Protokolle und Verlauf anzeigen**.
3. Suchen Sie in der Protokolldatei nach der Anwendungs-URL. Suchen Sie am Ende der Protokolldatei nach dem Wort `urls` oder `view` (bzw. 'ansehen'). Zum Beispiel wird in der Protokolldatei möglicherweise eine Zeile ähnlich der folgenden angezeigt: `urls: my-app-devhost.mybluemix.net` oder `Status der Anwendung ansehen unter: http://<ipaddress>:<port>/health`.
4. Rufen Sie die URL im Browser auf. Wenn die App ausgeführt wird, wird eine Nachricht anzeigt, die Folgendes enthält: `Congratulations` oder `{"status":"UP"}`.

Wenn Sie die Befehlszeile verwenden, führen Sie den Befehl [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) aus, um die Seite einer manuell bereitgestellten App in Ihrem Standardbrowser anzuzeigen.
