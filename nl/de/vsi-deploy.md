---
copyright:

  years: 2018

lastupdated: "2018-06-28"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Apps in einem virtuellen Server bereitstellen
{: #vsi-deploy}

Stellen Sie Apps von {{site.data.keyword.cloud}} [App Service ![Symbol für externen Link](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window} in virtuellen Serverinstanzen bereit, um ein Zusammenspiel der Plattform- und Infrastrukturaktivitäten zu ermöglichen und die Steuerungsmöglichkeiten und Flexibilität bei der Entwicklung von Apps zu erweitern.
{: shortdesc}

Eine virtuelle Serverinstanz bietet im Vergleich zu anderen Konfigurationen mehr Transparenz, Vorhersagbarkeit und Automatisierungsmöglichkeiten für alle Workloadtypen. Kombinieren Sie die virtuelle Instanz mit einem Bare-Metal-Server, um eindeutige Workloadkombinationen zu bilden. Sie können z. B. eine leistungsfähige Datenbanklogik oder effizientes maschinelles Lernen mit Bare-Metal- und GPU-Konfigurationen (GPU = Graphics Processing Unit, Grafik-Verarbeitungseinheit) erstellen, die auf einem auf Debian Linux basierenden Betriebssystem ausgeführt werden. 

## Vorbereitende Schritte
Für die Verwendung von virtuellen Instanzen muss Ihr {{site.data.keyword.cloud_notm}}-Konto für Infrastrukturservices aktiviert sein. Weitere Informationen finden Sie in [Upgrade auf den Infrastrukturservice![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link")](https://console.bluemix.net/dashboard/ibm-iaas-g1){: new_window}.

## Über Terraform bereitstellen
Alle Starter-Kits für App-Services können über [Terraform ![Symbol für externen Link](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window}, ein Open-Source-Framework für die Beschreibung von Infrastruktur mittels Code in einer dynamisch erstellten virtuellen Instanz bereitgestellt werden. Weitere Informationen finden Sie in der [Dokumentation zu Terraform![Symbol für externen Link](../icons/launch-glyph.svg)](https://www.terraform.io/docs/index.html){: new_window}. 

## Pipelinebereitstellung aktivieren

Wenn Sie ein Starter-Kit erstellen, bei dem der {{site.data.keyword.cloud_notm}}-[App-Service ![Symbol für externen Link](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window} verwendet wird, wird die virtuelle Serverinstanz aktiviert. Nach dem Erstellen der App können Sie auswählen, wo die App bereitgestellt werden soll. Die Starter-Kits sind für eine Bereitstellung über eine Continous Delivery-Toolchain ausgelegt. Starter-Kits können für Kubernetes-Instanzen, Cloud Foundry-Instanzen und virtuelle Server-Instanzen verwendet werden. Die Toolchain beinhaltet ein Quellcode-Repository und eine Bereitstellungspipeline. 

Die Option für virtuelle Server schließt verschiedene Phasen ein. Zunächst wird der App-Code aufbereitet und in einem GitLab-Repository gespeichert und es wird eine Toolchain mit Pipeline über den Quellcode erstellt. Die Pipeline ist so definiert, dass der Code erstellt und in einem Debian-Paketmanagerformat paketiert wird. Danach wird eine virtuelle Instanz von Terraform bereitgestellt. Anschließend wird die App bereitgestellt, installiert und im aktiven virtuellen Image gestartet und der Zustand der App wird überprüft. 

Die Pipeline schlägt bei der ersten Ausführung fehl, da zunächst eine Reihe von Benutzerkontoeigenschaften manuell konfiguriert werden müssen. Diese Eigenschaften können nicht in die Toolchain, bei der aus Sicherheitsgründen Git-Quellcode verwendet wird, übergeben werden. Sie müssen diese Werte manuell konfigurieren, damit die Toolchain ordnungsgemäß abgeschlossen werden kann. 

Gehen Sie wie im Folgenden beschrieben vor, um die Sicht mit den Umgebungseigenschaften aufzurufen und die Benutzerkontoeigenschaften für die Ausführung der Pipeline festzulegen. 

1. Klicken Sie auf der Seite mit den Anwendungsdetails auf **Toolchain anzeigen**. 
2. Klicken Sie auf die Kachel **Delivery Pipeline**. 
3. Klicken Sie bei der Build-Stage auf **Stage konfigurieren**. 
4. Klicken Sie auf die Registerkarte **Umgebungsvariablen**, um die Eigenschaften anzuzeigen. 
5. Ändern Sie die Eigenschaften auf der Registerkarte 'Umgebungsvariablen', um die ordnungsgemäße Ausführung der Toolchain zu ermöglichen. 

| Eigenschaft   | Beschreibung   |
|---|---|
| `TF_VAR_ibm_sl_api_key` | Der [Infrastruktur-API-Schlüssel](#iaas-key) aus der Infrastrukturkonsole. |
| `TF_VAR_ibm_sl_username` | Der [Infrastrukturbenutzername](#user-key) zur Kennzeichnung des Infrastrukturkontos. |
| `TF_VAR_ibm_cloud_api_key` | Der für die Serviceerstellung erforderliche {{site.data.keyword.cloud_notm}} [Plattform-API-Schlüssel](#platform-key). |
| `PUBLIC_KEY` | Der für den Zugriff auf die virtuelle Serverinstanz definierte [öffentliche Schlüssel](#public-key). |
| `PRIVATE_KEY` | Der für den Zugriff auf die virtuelle Serverinstanz definierte [private Schlüssel](#public-key). |
| `VI_INSTANCE_NAME` | Der automatisch generierte Name für die virtuelle Serverinstanz. |
| `GIT_USER` | Der GitLab-Benutzername. Dieser Name ist erforderlich, wenn Sie den [Terraform-Status](#tform-state) definieren, um den Status des Befehls 'Apply' zu speichern. |
| `GIT_PASSWORD` | Das GitLab-Kennwort. Dieses Kennwort ist erforderlich, wenn Sie den [Terraform-Status](#tform-state) definieren, um den Status des Befehls 'Apply' zu speichern. |
{: caption="Tabelle 1. Für die Aktivierung der Pipeline zu ändernde Umgebungsvariablen" caption-side="top"}

### Infrastruktur-API-Schlüssel abrufen
{: #iaas-key}

Terraform benötigt einen Infrastruktur-API-Schlüssel zum Erstellen von Infrastrukturressourcen. Rufen Sie wie im Folgenden beschrieben einen Infrastrukturschlüssel ab. 

1. Wechseln Sie zur infrastrukturbezogenen [Benutzerliste![Symbol für externen Link](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window}. Sie können auch auf **Menü** > **Infrastruktur** > **Konto** > **Benutzerliste** klicken. 
2. Suchen Sie nach den Details der Benutzer, die die Toolchain erstellen, und klicken Sie in der Spalte für den API-Schlüssel auf `Anzeigen` oder `Generieren`. In beiden Fällen wird der API-Schlüssel anschließend in einem Dialogfenster angezeigt. 
3. Kopieren Sie den API-Schlüssel und ersetzen Sie den Wert der Toolchain-Konfigurationseigenschaft `TF_VAR_ibm_sl_api_key` durch diesen Schlüssel. 

### Infrastrukturbenutzernamen abrufen
{: #user-key}

Rufen Sie wie im Folgenden beschrieben den Infrastrukturbenutzernamen. 

1. Wechseln Sie zur infrastrukturbezogenen [Benutzerliste![Symbol für externen Link](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window}. Sie können auch auf **Menü** > **Infrastruktur** > **Konto** > **Benutzerliste** klicken. 
2. Klicken Sie auf den Benutzer, von dem die Toolchain erstellt werden soll. 
3. Blättern Sie abwärts zur Eigenschaft **VPN-Benutzername**. 
4. Schneiden Sie den zugehörigen Wert aus und ersetzen Sie den Wert der Toolchainkonfigurationseigenschaft `TF_VAR_ibm_sl_username` durch diesen Wert. 

### Plattform-API-Schlüssel
{: #platform-key}

Der Plattform-API-Schlüssel wird von Terraform benötigt, um Services auf der Plattformebene wie Datenbank- und Compose-Services zu erstellen. Rufen Sie wie im Folgenden beschrieben einen Plattformschlüssel ab. 

1. Klicken Sie auf **Menü** > **Dashboard**, um sicherzustellen, dass der Benutzer im Plattform-Dashboard angezeigt wird. 
2. Klicken Sie auf **Verwalten** > **Sicherheit** > **Plattform-API-Schlüssel**. 
3. Klicken Sie auf **Erstellen**. 
4. Geben Sie einen Namen und eine Beschreibung ein und klicken Sie auf **Erstellen**. 
5. Klicken Sie im angezeigten Dialogfenster auf *Anzeigen*, um den Schlüssel zu überprüfen. 
6. Kopieren Sie den Schlüssel und fügen Sie ihn in die Zwischenablage ein oder laden Sie den Schlüssel herunter. 
7. Ersetzen Sie den Wert der Toolchainkonfigurationseigenschaft `TF_VAR_ibm_cloud_api_key` durch den generierten Wert. 

### Öffentlichen und privaten Schlüssel generieren
{: #public-key}

Gehen Sie wie im Folgenden beschrieben vor, um es der Toolchain zu ermöglichen, die Debian-Paketierung in der virtuellen Serverinstanz zu installieren. 

1. Erstellen Sie in der Client-Infrastruktur wie im Folgenden beschrieben ein [Schlüsselpaar aus öffentlichem und privatem Schlüssel![Symbol für externen Link](../icons/launch-glyph.svg)](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window}. 
2. Wechseln Sie zur [Ansicht mit den Infrastruktur-SSH-Schlüsseln![Symbol für externen Link](../icons/launch-glyph.svg)](https://control.bluemix.net/devices/sshkeys){: new_window} oder klicken Sie auf **Menü** > **Infrastruktur** > **Geräte** > **Verwalten** > **SSH-Schlüssel**. 
3. Klicken Sie auf **Hinzufügen**.
4. Kopieren Sie den Inhalt des zuvor erstellten privaten Schlüssels und fügen Sie ihn beim Schlüsselinhalt ein. 
5. Geben Sie dem Schlüssel einen Namen und klicken Sie auf **Hinzufügen**. 

### Terraform-Status aktivieren
{: #tform-state}

Terraform unterstützt das Speichern des Status des Terraform-Befehls `apply`. Über diese Statusdatei wird der Befehl `apply` ein zweites Mal ausgeführt, um zu ermitteln, ob Terraform-Konfigurationsdateien geändert wurden. Sie können den Status in dem Git-Repository speichern, das für die App und die Konfigurationsverwaltung verwendet wird. 

Aktivieren Sie die Statusspeicherung, indem Sie die Eigenschaften `GIT_USER` und `GIT_PASSWORD` in den Umgebungsvariablen der Toolchain konfigurieren. Rufen Sie die Werte wie folgt ab: 

1. Greifen Sie im Code-Tool über die Ansicht mit den Toolchains auf das Git-Repository zu. 
2. Klicken Sie in GitLab auf das **Profilsymbol** und danach auf **Einstellungen**. 
3. Klicken Sie auf **Konto**, kopieren Sie den Benutzernamen und ersetzen Sie den Wert für `GIT_USER` durch diesen Wert. 
4. Klicken Sie auf **Zugriffstoken**. 
5. Definieren Sie einen Namen für Ihr Token und klicken Sie danach auf **Persönliches Zugriffstoken erstellen**. 
6. Klicken Sie im Feld `Neues persönliches Zugriffstoken` auf das Kopiersymbol und ersetzen Sie den Wert für `GIT_PASSWORD` in den Toolchain-Eigenschaften durch diesen Wert. 

Der Terraform-Status wird in einem Zweig namens `terraform` gespeichert und löst die Pipeline-Ausführung nicht aus, wenn eine Änderung ermittelt wurde. 


### Git-Operationen ermöglichen
{: #git-repo}

Beim Bereitstellen der App in {{site.data.keyword.cloud_notm}} wird ein GitLab-Repository für den Code für die Quellcodeverwaltung erstellt. Mithilfe von Git-Operationen können Sie es Teams ermöglichen, mit Ihrer App zu arbeiten und Änderungen zu übergeben. Im Folgenden wird der Inhalt der Ordner in diesem Repository beschrieben. 

#### Debian-Ordner
{: #debian-folder}

Der Ordner `debian` enthält die Konfiguration, die zum Paketieren der App in ein [Debian-Paket![Symbol für externen Link](../icons/launch-glyph.svg)](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window} benötigt wird. 

#### Terraform-Ordner
{: #terraform-folder}

Der Ordner `terraform` enthält die IaC-Konfiguration (IaC = Infrastructure as Code), die zum Bereitstellen von Infrastrukturressourcen verwendet werden kann. Die Hauptquelle beim Ändern der Optionen für Ihre Terraform-Konfiguration stellt die Datei `main.tf` dar. 

```
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

Sie können auch Bare-Metal-Server mit Terraform bereitstellen. Weitere Informationen hierzu finden Sie in der [Providerdokumentation zu IBM Terraform![Symbol für externen Link](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} und im Abschnitt zum [Git-Repository für IBM Terraform-Provider![Symbol für externen Link](../icons/launch-glyph.svg)](https://github.com/IBM-Cloud/terraform-provider-ibm){: new_window}. 

Mithilfe der Datei `variables.tf` können Sie das Rechenzentrum ändern, das beim Erstellen der virtuellen Instanz als Ziel dienen soll. Ein Liste der bei der Plattform definierten Rechenzentren finden Sie im Abschnitt zu den [Rechenzentren![Symbol für externen Link](../icons/launch-glyph.svg)](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}. 

Standardmäßig ist die Terraform-Datei für Washington und `wdc04` konfiguriert. 

```
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### Toolchain-Stages verstehen
{: #toolchain-stages}

Die Toolchain stellt die Bereitstellung von Infrastruktur und Apps in einer einfachen Pipeline dar. Unterteilen Sie diese Pipeline in zwei Pipelines: eine Pipeline für den IaC-Bereich und eine Pipeline für die Bereitstellung der App. 

Die Toolchain wird in die folgenden Stages unterteilt: 

1. In der Build-Stage wird das Git-Repository geklont und in ein Debian-Paket paketiert. 
2. In der Terraform Planungsstage wird ein Terraform-Plan erstellt. 

  ```
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. In der Terraform-Anwendungsstage wird die Terraform-Konfiguration angewendet und gewartet, bis die IP-Adresse des virtuellen Servers verfügbar ist. 

  ```
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. In der Stage für Bereitstellen, Installieren und Starten wird das in der ersten Stage erstellte Debian-Paket in den aktiven virtuellen Server verschoben und dort installiert und anschließend gestartet. 
5. In der Stage für die Statusprüfung (Health Check) wird überprüft, ob der Statusendpunkt in der App zur Verfügung steht, und anschließend die Pipeline ausgeführt. 

Nach dem Start der App können Sie über die Protokolle der Stage für die Statusprüfung auf die App zugreifen. Klicken Sie auf die in den Protokollen aufgeführten URL-Links mit IP-Adresse und Port der App. 
