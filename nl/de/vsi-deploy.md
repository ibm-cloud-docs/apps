---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, deploy, virtual server, App Service, vsi, virtual machine, delivery pipeline, virtual deployment

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:table: .aria-labeledby="caption"}

# Apps in einem virtuellen Server bereitstellen
{: #vsi-deploy}

Wenn Sie über ein nutzungsabhängiges Konto verfügen, können Sie den {{site.data.keyword.cloud}} [App-Service](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") verwenden, um Ihre Apps in zahlreichen Umgebungstypen, einschließlich virtueller Serverinstanzen, bereitzustellen. Eine virtuelle Serverinstanz emuliert eine Bare-Metal-Maschine und ist eine gängige Implementierungsoption, wenn lokale Workloads in die Cloud verschoben werden.
{: shortdesc}

Eine virtuelle Serverinstanz bietet im Vergleich zu anderen Konfigurationen mehr Transparenz, Vorhersagbarkeit und Automatisierungsmöglichkeiten für alle Workloadtypen. Kombinieren Sie die virtuelle Instanz mit einer Bare-Metal-Server-Instanz, um eindeutige Workloadkombinationen zu bilden. Sie können z. B. eine leistungsfähige Datenbanklogik oder effizientes maschinelles Lernen mit Bare-Metal- und GPU-Konfigurationen (GPU = Graphics Processing Unit, Grafik-Verarbeitungseinheit) erstellen, die unter einem auf Linux basierenden Debian-Betriebssystem ausgeführt werden.

Die Einrichtung einer virtuellen Serverinstanz und ihre Bereitstellung kann ein komplexer und zeitaufwändiger Prozess sein. Sie können jedoch schnell betriebsbereit sein, indem Sie den {{site.data.keyword.cloud_notm}}-App-Service verwenden.

Services werden nicht an die virtuelle Serverinstanz gebunden. Sie können Services nicht zu einer Anwendung in einem virtuellen Server hinzufügen.
{: important}

## Apps erstellen und implementieren
{: #create-deploy-vsi}

Der App-Service stellt eine virtuelle Serverinstanz für Sie bereit, lädt ein Image, das Ihre App enthält, erstellt eine DevOps-Toolchain und initiiert den ersten Bereitstellungszyklus für Sie.

1. [Erstellen Sie eine App](/docs/apps?topic=creating-apps-tutorial-scratch#tutorial-scratch). 
2. Klicken Sie auf der Seite **App-Details** auf **Continuous Delivery konfigurieren**.
3. Wählen Sie **Auf virtuellem Server bereitstellen** gemeinsam mit der Region aus, in der Ihr Server ausgeführt werden soll.

## Funktionsweise des Bereitstellungsprozesses

Der Bereitstellungsprozess für den virtuellen Server besteht aus mehreren Schlüsseltechnologien, die Terraform, Pipelineaktivierung, API-Schlüsselverwaltung (Git-Operationen) und das Verständnis des Toolchainprozesses umfassen. 

### Über Terraform bereitstellen

Alle App-Service-Starter-Kits können über [Terraform](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link"), ein Open-Source-IaC-Framework, in einer dynamisch erstellten virtuellen Instanz bereitgestellt werden. 

### Pipelinebereitstellung aktivieren

Wenn Sie ein Starter-Kit erstellen, das den {{site.data.keyword.cloud_notm}} [App-Service](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") verwendet, wird die virtuelle Serverinstanz aktiviert. Nach dem Erstellen der App können Sie auswählen, wo die App bereitgestellt werden soll. Die Starter-Kits sind für eine Bereitstellung über eine Continuous Delivery-Toolchain ausgelegt. Starter-Kits können für Kubernetes-Instanzen, Cloud Foundry-Instanzen und Virtual Server-Instanzen verwendet werden. Die Toolchain beinhaltet ein Quellcode-Repository und eine Bereitstellungspipeline.

Die Option für virtuelle Server schließt verschiedene Phasen ein. Zuerst wird der App-Code vorbereitet und in einem Git-Repository von GitLab gespeichert. Der Quellcode erstellt eine Toolchain mit einer Pipeline. Die Pipeline ist so definiert, dass der Code erstellt und in einem Debian-Paketmanagerformat paketiert wird. Danach wird eine virtuelle Instanz von Terraform bereitgestellt. Anschließend wird die App bereitgestellt, installiert und im aktiven virtuellen Image gestartet und der Zustand der App wird überprüft.

Die Pipeline verwendet eine Reihe von Benutzerkontoeigenschaften und ein neues SSH-Schlüsselpaar zur Bereitstellung der Infrastruktur. Diese Eigenschaften werden automatisch an die Toolchain übergeben, aus Sicherheitsgründen jedoch nicht im GIT-Quellcode gespeichert.

Führen Sie die folgenden Schritte aus, um diese Umgebungseigenschaften anzuzeigen. 

1. Klicken Sie auf der Seite "App-Details" auf **Toolchain anzeigen**.
2. Klicken Sie auf die Kachel **Delivery Pipeline**.
3. Klicken Sie auf das Symbol für die **Konfiguration der Stage** und dann für die Build-Stage auf **Stage konfigurieren**.
4. Klicken Sie auf die Registerkarte **Umgebungseigenschaften**, um die Eigenschaften anzuzeigen. Die folgende Tabelle enthält Informationen zu den verfügbaren Eigenschaften.

| Eigenschaft  | Beschreibung  |
|-----------|--------------|
| `TF_VAR_ibm_sl_api_key` | Der [Infrastruktur-API-Schlüssel](/docs/apps?topic=creating-apps-vsi-deploy#iaas-key) stammt aus der klassischen Infrastrukturkonsole. |
| `TF_VAR_ibm_sl_username` | Der [Infrastrukturbenutzername](/docs/apps?topic=creating-apps-vsi-deploy#user-key), der das klassische Infrastrukturkonto kennzeichnet. |
| `TF_VAR_ibm_cloud_api_key` | Der {{site.data.keyword.cloud_notm}} [API-Schlüssel](/docs/apps?topic=creating-apps-vsi-deploy#platform-key) wird zur Aktivierung der Serviceerstellung verwendet. |
| `PUBLIC_KEY` | Der für den Zugriff auf die virtuelle Serverinstanz definierte [öffentliche Schlüssel](/docs/apps?topic=creating-apps-vsi-deploy#public-key). |
| `PRIVATE_KEY` | Der für den Zugriff auf die virtuelle Serverinstanz definierte [private Schlüssel](/docs/apps?topic=creating-apps-vsi-deploy#public-key). Sie müssen für den Zeilenumbruch die Formatierung `\n` verwenden. |
| `VI_INSTANCE_NAME` | Der automatisch generierte Name für die virtuelle Serverinstanz. |
| `GIT_USER` | Wenn Sie den [Terraform-Status](/docs/apps?topic=creating-apps-vsi-deploy#tform-state) so festgelegt haben, dass der Status des Befehls zum Anwenden (apply) gespeichert wird, ist der GitLab-Benutzername erforderlich. |
| `GIT_PASSWORD` | Wenn Sie den [Terraform-Status](/docs/apps?topic=creating-apps-vsi-deploy#tform-state) so festgelegt haben, dass der Status des Befehls zum Anwenden (apply) gespeichert wird, ist das GitLab-Kennwort erforderlich. |
{: caption="Tabelle 1. Umgebungsvariablen, die für die Aktivierung geändert werden müssen" caption-side="top"}


#### API-Schlüssel für klassische Infrastruktur
{: #iaas-key}

Terraform erfordert einen API-Schlüssel für eine klassische Infrastruktur zum Erstellen von Infrastrukturressourcen. Der API-Schlüssel wird automatisch während der Bereitstellung abgerufen. Um einen Schlüssel manuell abzurufen, führen Sie die folgenden Schritte aus.

1. Rufen Sie die [Benutzerliste](https://{DomainName}/iam#/users){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") auf. Sie können auch auf **Verwalten** > **Zugriff (IAM)** klicken und **Benutzer** auswählen.
2. Klicken Sie auf einen Benutzernamen und dann auf **Benutzerdetails**.
3. Klicken Sie im Abschnitt zu den API-Schlüsseln auf **Schlüssel für klassische Infrastruktur hinzufügen**.
4. Kopieren Sie den API-Schlüssel ` TF_VAR_ibm_sl_api_key`, oder laden Sie ihn herunter, und speichern Sie ihn an einem sicheren Ort. Sie können die Details des API-Schlüssels später über die Option **Details anzeigen** im Menü **Aktionen** ![Symbol für Aktionsliste](../icons/action-menu-icon.svg) abrufen.
5. Fügen Sie den kopierten API-Schlüsselwert in die Toolchainkonfiguration ein, um `TF_VAR_ibm_sl_api_key` zu ersetzen.

Weitere Informationen finden Sie unter [API-Schlüssel für klassische Infrastruktur verwalten](/docs/iam?topic=iam-classic_keys#classic_keys) und [Berechtigungen für klassische Infrastruktur](/docs/iam?topic=iam-infrapermission#infrapermission).

#### Benutzername für klassische Infrastruktur
{: #user-key}

Der Benutzername für die klassische Infrastruktur wird ebenfalls automatisch abgerufen und während der Bereitstellung verwendet. Um den Benutzernamen manuell abzurufen, führen Sie die folgenden Schritte aus.

1. Rufen Sie die [Benutzerliste](https://{DomainName}/iam#/users){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") auf. Sie können auch auf **Verwalten** > **Zugriff (IAM)** klicken und **Benutzer** auswählen.
2. Klicken Sie auf einen Benutzernamen und dann auf **Benutzerdetails**.
3. Suchen Sie die Eigenschaft **VPN-Benutzername**.
4. Schneiden Sie den zugehörigen Wert aus und ersetzen Sie durch ihn den Wert der Toolchainkonfigurationseigenschaft `TF_VAR_ibm_sl_username`.

#### {{site.data.keyword.cloud_notm}}-API-Schlüssel
{: #platform-key}

Zur Erstellung von Services auf Plattformebene in Terraform, wie z. B. Datenbanken und Compose-Services, wird der {{site.data.keyword.cloud_notm}}-API-Schlüssel automatisch abgerufen und als Umgebungsvariable in Ihrer Pipeline gespeichert. Um einen {{site.data.keyword.cloud_notm}}-API-Schlüssel manuell abzurufen, führen Sie die folgenden Schritte aus.

1. Rufen Sie die [Benutzerliste](https://{DomainName}/iam#/users){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") auf. Sie können auch auf **Verwalten** > **Zugriff (IAM)** klicken und **Benutzer** auswählen.
2. Klicken Sie auf einen Benutzernamen und dann auf **Benutzerdetails**.
3. Suchen Sie den Abschnitt zu den API-Schlüsseln und klicken Sie auf **IBM Cloud-API-Schlüssel erstellen**.
4. Geben Sie einen Namen und eine Beschreibung ein und klicken Sie auf **Erstellen**.
5. Klicken Sie im angezeigten Fenster auf **Anzeigen**, um den Schlüssel zu überprüfen.
6. Kopieren Sie den Schlüssel und fügen Sie ihn in die Zwischenablage ein oder laden Sie den Schlüssel herunter.
7. Ersetzen Sie den Wert der Toolchainkonfigurationseigenschaft `TF_VAR_ibm_cloud_api_key` durch den generierten Wert.

#### Öffentliche und private Schlüssel
{: #public-key}

Damit die Toolchain die Debian-Paketierung in der virtuellen Serverinstanz installiert, generiert die Bereitstellungsinfrastruktur automatisch ein SSH-Schlüsselpaar mit privatem und öffentlichem Schlüssel, um den Git-Inhalt zur Instanz zu übertragen.

Gehen Sie wie folgt vor, um diese Schritte manuell auszuführen:
1. Erstellen Sie auf Ihrem Client wie im Folgenden beschrieben ein [Schlüsselpaar aus öffentlichem und privatem Schlüssel](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").
2. Rufen Sie die [Ansicht für die SSH-Schlüssel der Infrastruktur](https://{DomainName}/iam/#/users){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") auf. Sie können auch auf **Menü** > **Klassische Infrastruktur** > **Geräte** > **Verwalten** > **SSH-Schlüssel** klicken.
3. Klicken Sie auf **Hinzufügen**.
4. Kopieren Sie den Inhalt des zuvor erstellten öffentlichen Schlüssels und fügen Sie ihn in den Schlüsselinhalt ein.
5. Geben Sie dem Schlüssel einen Namen und klicken Sie auf **Hinzufügen**.

Der private Schlüssel muss in einer einzigen Zeile angegeben werden. Ersetzen Sie Zeilenumbrüche durch `\n`. Im Folgenden ist ein Beispiel dargestellt.
{: tip}

```
---------BEGIN RSA KEY----------\nasdfasdfeqwtqf13rf1eqwfwe\netq3efaewf23fa23f23f\n.....\n----------END RSA KEY-------------
```
{: screen}

#### Terraform-Status aktivieren
{: #tform-state}

Terraform unterstützt das Speichern des Status des Terraform-Befehls `apply`. Über diese Statusdatei wird der Befehl `apply` ein zweites Mal ausgeführt, um zu ermitteln, ob Terraform-Konfigurationsdateien geändert wurden. Der Status wird in dem Git-Repository gespeichert, in dem die App und die Konfiguration automatisch konfiguriert werden.

Zum Aktivieren des Statusspeichers werden `GIT_USER` und `GIT_PASSWORD` automatisch als Eigenschaften in den Umgebungsvariablen der Toolchain konfiguriert. Wenn Sie Zugriff auf diese Werte benötigen, führen Sie diese Schritte aus:

1. Greifen Sie in der Toolchain-Ansicht vom Code-Tool auf das Git-Repository zu.
2. Klicken Sie in GitLab auf das **Profilsymbol** und danach auf **Einstellungen**.
3. Klicken Sie auf **Konto**, kopieren Sie den Benutzernamen und ersetzen Sie den Wert für `GIT_USER` durch diesen Wert.
4. Klicken Sie auf **Zugriffstoken**.
5. Definieren Sie einen Namen für Ihr Token, wählen Sie einen Bereich aus und klicken Sie danach auf **Persönliches Zugriffstoken erstellen**.
6. Klicken Sie im Feld `Neues persönliches Zugriffstoken` auf **Kopieren** und ersetzen Sie den Wert für `GIT_PASSWORD` in den Toolchain-Eigenschaften.

Der Terraform-Status wird in einem Zweig namens `terraform` gespeichert und löst die Pipeline-Ausführung nicht aus, wenn eine Änderung ermittelt wurde.

### Git-Operationen aktivieren
{: #git-repo-vsi}

Wenn die App in {{site.data.keyword.cloud_notm}} bereitgestellt wird, wird ein GitLab-Repository erstellt, um den Code für die Quellcodeverwaltung zu hosten. Sie können Git-Operationen verwenden, um Teams zu ermöglichen, Änderungen an Ihrer App vorzunehmen und bereitzustellen. Im Folgenden wird der Inhalt der Ordner in diesem Repository beschrieben.

#### Debian-Ordner
{: #debian-folder}

Der `debian`-Ordner enthält die Konfiguration, die für das Paketieren der App in ein [Debian-Paket](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") erforderlich ist.

#### Terraform-Ordner
{: #terraform-folder}

Der Ordner `terraform` enthält die IaC-Konfiguration (IaC = Infrastructure as Code), die zum Bereitstellen von Infrastrukturressourcen verwendet werden kann. Die Hauptquelle beim Ändern der Optionen für Ihre Terraform-Konfiguration stellt die Datei `main.tf` dar.

```json
resource "ibm_compute_vm_instance" "vm1" {
    hostname = "${var.vi_instance_name}"
    domain = "example.com"
    os_reference_code = "DEBIAN_8_64"
    datacenter = "${var.datacenter}"
    network_speed = 100
    hourly_billing = true
    private_network_only = false
    cores = 1
    memory = 1024
    disks = [25]
    local_disk = false
    ssh_key_ids = [
        "${ibm_compute_ssh_key.ssh_key_gip.id}"
    ]
}
```

Sie können auch Bare-Metal-Server-Instanzen mit Terraform bereitstellen. Weitere Informationen hierzu finden Sie unter [IBM Terraform-Providerdokumentation](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") und [IBM Terraform-Provider-GIT-Repository](https://github.com/IBM-Cloud/terraform-provider-ibm){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").

Mithilfe der Datei `variables.tf` können Sie das Rechenzentrum ändern, das beim Erstellen der virtuellen Instanz als Ziel dienen soll. Die Liste der für die Plattform definierten Rechenzentren finden Sie unter [Rechenzentren](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link").

Standardmäßig ist die Terraform-Datei für Washington und `wdc04` konfiguriert.
```json
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### Toolchain-Stages verstehen
{: #toolchain-stages-vsi}

Die Toolchain stellt die Bereitstellung von Infrastruktur und Apps in einer einfachen Pipeline dar. Unterteilen Sie diese Pipeline in zwei Pipelines: eine Pipeline für den IaC-Bereich und eine Pipeline für die Bereitstellung der App.

Der Toolchain-Prozess verfügt über fünf Stages.

1. Der Stage 'Build' klont das Git-Repository und paketiert den Code in ein Debian-Paket.
2. In der Terraform-Planungsstage wird ein Terraform-Plan vorbereitet.
  ```console
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. In der Terraform-Anwendungsstage wird die Terraform-Konfiguration angewendet und gewartet, bis die IP-Adresse des virtuellen Servers verfügbar ist.

  ```console
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. In der Stage für Bereitstellen, Installieren und Starten wird das in der ersten Stage erstellte Debian-Paket in den aktiven virtuellen Server verschoben und dort installiert und anschließend gestartet.
5. In der Stage für die Statusprüfung (Health Check) wird überprüft, ob der Statusendpunkt in der App zur Verfügung steht. Anschließend wird die Pipeline ausgeführt.

Nach dem Start der App können Sie über die Protokolle der Stage für die Statusprüfung auf die App zugreifen. Klicken Sie auf die in den Protokollen aufgeführten URL-Links mit IP-Adresse und Port der App.
