---
copyright:

  years: 2018

lastupdated: "2018-10-08"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Distribuzione a un server virtuale
{: #vsi-deploy}

Distribuisci le applicazioni {{site.data.keyword.cloud}} [App Service ![Icona link esterno](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window} nelle istanze del server virtuale per consentire alle attività di sviluppo dell'infrastruttura e della piattaforma di collaborare e aumentare la flessibilità e il controllo dell'applicazione.
{: shortdesc}

Un'istanza del server virtuale offre trasparenza, prevedibilità e automazione migliori per tutti i tipi di carico di lavoro quando confrontata con altre configurazioni. Combinala con un server bare metal per creare combinazioni di carico di lavoro uniche. Ad esempio, puoi creare la logica di database ad alte prestazioni o machine learning con configurazioni bare metal e GPU che eseguono un sistema operativo basato su Linux Debian.

## Prima di iniziare
Per utilizzare le istanze virtuali, il tuo account {{site.data.keyword.cloud_notm}} deve essere abilitato per l'infrastruttura. Per ulteriori informazioni, consulta [Esegui l'aggiornamento all'infrastruttura ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/dashboard/ibm-iaas-g1){: new_window}.

**Importante**: non viene eseguito il bind dei servizi all'istanza del server virtuale. Non puoi aggiungere servizi a un'applicazione in un server virtuale.

## Distribuzione tramite Terraform
Tutti i kit starter del servizio dell'applicazione possono essere distribuiti in un'istanza virtuale creata dinamicamente tramite [Terraform ![Icona link esterno](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window}, un'infrastruttura open source come framework del codice. Per ulteriori informazioni, consulta [Terraform Documentation ![Icona link esterno](../icons/launch-glyph.svg)](https://www.terraform.io/docs/index.html){: new_window}.

## Abilitazione della tua distribuzione della pipeline

Quando crei un kit starter che utilizza {{site.data.keyword.cloud_notm}} [App Service ![Icona link esterno](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window}, viene abilitata l'istanza del server virtuale. Dopo aver creato l'applicazione, puoi scegliere dove vuoi distribuirla. I kit starter sono abilitati per supportare la distribuzione utilizzando una toolchain di Continuous Delivery. I kit starter possono avere come destinazione istanze di Virtual Server, Kubernetes e Cloud Foundry. La toolchain include un repository del codice di origine e una pipeline di distribuzione.

L'opzione del server virtuale funziona a fasi. Per prima cosa, il codice dell'applicazione viene preparato e memorizzato in un repository GITLab Git e il codice di origine crea una toolchain con una pipeline. La pipeline viene definita per creare il codice e impacchettarlo in un formato del gestore pacchetti Debian. Quindi, Terraform fornisce un'istanza virtuale. Infine, l'applicazione viene distribuita, installata e avviata all'interno dell'immagine virtuale in esecuzione e il relativo stato di integrità viene convalidato.

La pipeline utilizza una serie di proprietà account utente e una nuova coppia di chiavi SSH per la distribuzione all'infrastruttura. Queste proprietà vengono automaticamente passate nella toolchain, ma non memorizzate nel codice di origine GIT per motivi di sicurezza.

Per visualizzare queste proprietà di ambiente, completa questa procedura. Consulta la tabella per acquisire informazioni sulle proprietà disponibili.

1. Dalla pagina dei dettagli dell'applicazione, fai clic su **View Toolchain**.
2. Fai clic sul tile **Delivery Pipeline**.
3. Fai clic sull'icona **Stage Configure** e quindi su **Configure Stage** nella fase di build.
4. Fai clic sulla scheda **Environment Properties** per visualizzare le proprietà.

| Proprietà   | Descrizione   |
|---|---|
| `TF_VAR_ibm_sl_api_key` | La [chiave API dell'infrastruttura](#iaas-key) viene dalla console dell'infrastruttura. |
| `TF_VAR_ibm_sl_username` | Il [nome utente dell'infrastruttura](#user-key) che identifica l'account dell'infrastruttura. |
| `TF_VAR_ibm_cloud_api_key` | La [chiave API della piattaforma](#platform-key) {{site.data.keyword.cloud_notm}} viene utilizzata per abilitare la creazione del servizio. |
| `PUBLIC_KEY` | La [chiave pubblica](#public-key) definita per abilitare l'accesso all'istanza del server virtuale. |
| `PRIVATE_KEY` | La [chiave privata](#public-key) definita per abilitare l'accesso all'istanza del server virtuale. **Nota**: devi utilizzare la formattazione di stile nuova riga `\n`. |
| `VI_INSTANCE_NAME` | Il nome generato automaticamente per l'istanza del server virtuale. |
| `GIT_USER` | Se imposti lo [stato Terraform](#tform-state) per memorizzare lo stato del comando applicato, è obbligatorio il nome utente GITLab. |
| `GIT_PASSWORD` | Se imposti lo [stato Terraform](#tform-state) per memorizzare lo stato del comando applicato, è obbligatoria la password GITLab. |
{: caption="Tabella 1. Variabili di ambiente da modificare per l'abilitazione" caption-side="top"}

#### Chiave API dell'infrastruttura
{: #iaas-key}

Terraform richiede una chiave API dell'infrastruttura per creare le risorse dell'infrastruttura. Questa viene ottenuta automaticamente durante la distribuzione. Segui questa procedura per richiamare una chiave manualmente. 

1. Vai all'[elenco utenti ![Icona link esterno](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window} dell'infrastruttura. Puoi anche fare clic su **Menu** > **Infrastruttura** > **Account** > **Elenco utenti**.
2. Trova i dettagli dell'utente che sta creando la toolchain e fai clic su `View` nella colonna delle chiavi API o fai clic su `Generate`; entrambi i passi visualizzano la chiave API in una finestra.
3. Copia la chiave API e sostituisci il valore nella configurazione della toolchain `TF_VAR_ibm_sl_api_key`.

#### Nome utente dell'infrastruttura
{: #user-key}

Il nome utente dell'infrastruttura viene anche ottenuto automaticamente e utilizzato durante la distribuzione. Segui questa procedura per richiamare una chiave manualmente. 

1. Vai all'[elenco utenti ![Icona link esterno](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window} dell'infrastruttura. Puoi anche fare clic su **Menu** > **Infrastruttura** > **Account** > **Elenco utenti**.
2. Fai clic sull'utente per cui vuoi creare la toolchain.
3. Scorri verso il basso fino alla proprietà **Nome utente VPN**.
4. Taglia e incolla questo valore e sostituisci la configurazione della toolchain `TF_VAR_ibm_sl_username`.

#### Chiave API della piattaforma
{: #platform-key}

Per creare servizi a livello di piattaforma in Terraform, come database e servizi di composizione, la chiave API della piattaforma viene automaticamente ottenuta ed archiviata come variabile di ambiente nella tua pipeline. Segui questa procedura per richiamare una chiave della piattaforma manualmente. 

1. Dalla pagina [Chiavi API ![Icona link esterno](../icons/launch-glyph.svg)](https://console.bluemix.net/iam/#/apikeys), fai clic su **Gestisci** > **Sicurezza** > **Chiavi API della piattaforma**.
2. Fai clic su **Crea**.
3. Immetti un nome e una descrizione e fai clic su **Crea**.
4. Quando si apre la finestra, fai clic su **Mostra** per esaminare la chiave.
5. Copia e incolla la chiave negli appunti o scaricala.
6. Sostituisci il valore nella configurazione della toolchain `TF_VAR_ibm_cloud_api_key` con il valore che è stato generato.

#### Chiavi pubbliche e private
{: #public-key}

Perché la toolchain installi il pacchetto Debian nell'istanza del server virtuale, l'infrastruttura di distribuzione genera automaticamente una coppia di chiavi SSH privata e pubblica per trasferire i contenuti GIT all'istanza. 

Per effettuare questa operazione manualmente:
1. Nel tuo client, utilizza le seguenti istruzioni per creare una [coppia di chiavi pubblica e privata ![Icona link esterno](../icons/launch-glyph.svg)](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window}.
2. Vai alla [vista delle chiavi SSH dell'infrastruttura ![Icona link esterno](../icons/launch-glyph.svg)](https://control.bluemix.net/devices/sshkeys){: new_window}. Puoi anche fare clic su **Menu** > **Infrastruttura** > **Dispositivi** > **Gestisci** > **Chiavi SSH**.
3. Fai clic su **Aggiungi**.
4. Copia il contenuto della chiave pubblica che hai precedentemente creato e incollalo nel contenuto della chiave.
5. Assegna un nome alla chiave e fai clic su **Aggiungi**.

La chiave privata deve essere su una singola riga. Sostituisci le nuove righe con `\n`. Vedi il seguente esempio.
{: tip}

```
---------BEGIN RSA KEY----------\nasdfasdfeqwtqf13rf1eqwfwe\netq3efaewf23fa23f23f\n.....\n----------END RSA KEY-------------
```
{: screen}

#### Abilitazione dello stato di Terraform
{: #tform-state}

Terraform supporta l'archiviazione dello stato del comando `apply` di Terraform. Questo file di stato esegue il comando `apply` una seconda volta per determinare se uno qualsiasi dei file di configurazione di Terraform è stato modificato. Lo stato viene archiviato nel repository GIT in cui l'applicazione e la configurazione vengono impostate automaticamente.

Per abilitare l'archiviazione dello stato, `GIT_USER` e `GIT_PASSWORD` vengono automaticamente configurate come proprietà nelle variabili di ambiente della toolchain. Se hai bisogno di accedere a questi valori, segui queste istruzioni:

1. Dalla vista delle toolchain, accedi al repository GIT dallo strumento del codice.
2. In GIT Lab, fai clic sull'**Icona profilo** e poi su **Impostazioni**.
3. Fai clic su **Account** e copia il nome utente e sostituisci il valore `GIT_USER`.
4. Fai clic su **Access Tokens**.
5. Definisci un nome per il tuo token, seleziona un ambito e fai clic su **Create Personal Access Token**.
6. Fai clic sull'icona copia dal campo `Tuo nuovo token di accesso personale` e sostituisci il valore di `GIT_PASSWORD` nelle proprietà della toolchain.

Lo stato di Terraform viene memorizzato in un ramo denominato `terraform` e non attiva l'esecuzione della pipeline se viene modificato.

### Abilitazione delle operazioni GIT
{: #git-repo}

Quando l'applicazione viene distribuita a {{site.data.keyword.cloud_notm}}, viene creato un repository GIT Lab per ospitare il codice per la gestione del codice di origine. Puoi utilizzare le operazioni GIT per consentire ai team di lavorare e distribuire le modifiche alla tua applicazione. Le cartelle incluse in questo repository e una spiegazione del loro contenuto.

#### Cartella Debian
{: #debian-folder}

La cartella `debian` contiene la configurazione richiesta per abilitare l'impacchettamento dell'applicazione in un [pacchetto Debian. ![Icona link esterno](../icons/launch-glyph.svg)](https://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html){: new_window}

#### Cartella Terraform
{: #terraform-folder}

La cartella `terraform` contiene la configurazione dell'infrastruttura come codice che può essere utilizzato per eseguire il provisioning delle risorse dell'infrastruttura. Il file `main.tf` è l'origine principale per modificare le opzioni per la tua configurazione Terraform.

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

Puoi anche eseguire il provisioning di server bare metal con Terraform. Per ulteriori informazioni, consulta [IBM Terraform Provider Documentation ![Icona link esterno](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} e [IBM Terraform Provider GIT Repo ![Icona link esterno](../icons/launch-glyph.svg)](https://github.com/IBM-Cloud/terraform-provider-ibm){: new_window}.

`variables.tf` può essere utilizzato per modificare il data center che vuoi destinare alla creazione dell'istanza virtuale. Per visualizzare l'elenco dei data center definiti sulla piattaforma, consulta [Data Centers ![Icona link esterno](../icons/launch-glyph.svg)](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}.

Per impostazione predefinita, il file Terraform è configurato per Washington e `wdc04`.

```
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### Descrizione delle fasi della toolchain
{: #toolchain-stages}

La toolchain mostra la distribuzione dell'infrastruttura e dell'applicazione in una semplice pipeline. Suddividi l'infrastruttura come parte di codice in una pipeline e la distribuzione dell'applicazione in un'altra pipeline.

Il processo della toolchain ha cinque fasi.

1. La fase di build clona il repository GIT e assembla il codice in un pacchetto Debian.
2. La fase di pianificazione di Terraform prepara un piano Terraform.

  ```
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. La fase di applicazione di Terraform applica la configurazione Terraform e attende finché non è disponibile l'indirizzo IP del server virtuale.

  ```
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. La fase di distribuzione, installazione, avvio sposta il pacchetto Debian creato nella prima fase nel server virtuale in esecuzione, lo installa e quindi lo avvia.
5. La fase di controllo di integrità convalida che l'endpoint di integrità sia disponibile nell'applicazione e quindi completa la pipeline.

Per accedere all'applicazione dopo che è stata avviata, controlla i log della fase del controllo di integrità. Fai clic sui link URL elencati nei log che mostrano l'indirizzo IP e la porta dell'applicazione.
