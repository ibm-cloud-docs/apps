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

# Distribuzione a un server virtuale 
{: #vsi-deploy}

Distribuisci le applicazioni {{site.data.keyword.cloud}} [App Service ![Icona link esterno](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window} nelle istanze del server virtuale per consentire alle attività di sviluppo dell'infrastruttura e della piattaforma di collaborare e aumentare la flessibilità e il controllo dell'applicazione.
{: shortdesc}

Un'istanza del server virtuale offre trasparenza, prevedibilità e automazione migliori per tutti i tipi di carico di lavoro quando confrontata con altre configurazioni. Combinala con un server bare metal per creare combinazioni di carico di lavoro uniche. Ad esempio, puoi creare una logica di database ad elevate prestazioni o il machine learning con le configurazioni bare metal e GPU in esecuzione su un sistema basato su Linux Debian.

## Prima di iniziare
Per utilizzare le istanze virtuali, il tuo account {{site.data.keyword.cloud_notm}} deve essere abilitato per l'infrastruttura. Per ulteriori informazioni, consulta [Esegui l'aggiornamento all'infrastruttura ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno")](https://console.bluemix.net/dashboard/ibm-iaas-g1){: new_window}.

## Distribuzione tramite Terraform 
Tutti i kit starter del servizio dell'applicazione possono essere distribuiti in un'istanza virtuale creata dinamicamente tramite [Terraform ![Icona link esterno](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window}, un'infrastruttura open source come framework del codice. Per ulteriori informazioni, consulta [Terraform Documentation ![Icona link esterno](../icons/launch-glyph.svg)](https://www.terraform.io/docs/index.html){: new_window}.

## Abilitazione della tua distribuzione della pipeline 

Quando crei un kit starter che utilizza {{site.data.keyword.cloud_notm}} [App Service ![Icona link esterno](../icons/launch-glyph.svg)](https://console.bluemix.net/developer/appservice/starter-kits){: new_window}, viene abilitata l'istanza del server virtuale. Dopo aver creato l'applicazione, puoi scegliere dove vuoi distribuirla. I kit starter sono abilitati per supportare la distribuzione utilizzando una toolchain di fornitura continua. I kit starter possono avere come destinazione istanze di Virtual Server, Kubernetes, e Cloud Foundry. La toolchain include un repository del codice di origine e una pipeline di distribuzione.

L'opzione del server virtuale funziona a fasi. Per prima cosa, il codice dell'applicazione viene preparato e memorizzato in un repository GITLab Git e il codice di origine crea una toolchain con una pipeline. La pipeline viene definita per creare il codice e impacchettarlo in un formato del gestore pacchetti Debian. Quindi, Terraform fornisce un'istanza virtuale. Infine, l'applicazione viene distribuita, installata e avviata all'interno dell'immagine virtuale in esecuzione e il relativo stato di integrità viene convalidato. 

La pipeline ha un errore al primo utilizzo perché richiede che una serie di proprietà dell'account utente vengano configurate manualmente. Queste proprietà non possono essere trasferite nella toolchain che utilizza il codice di origine GIT per motivi di sicurezza. Devi configurare manualmente questi valori per consentire il completamento corretto della toolchain. 

Segui questa procedura per ottenere la vista delle proprietà dell'ambiente e abilitare la tua pipeline con le tue proprietà dell'account utente. 

1. Dalla pagina dei dettagli dell'applicazione, fai clic su **Visualizza toolchain**.
2. Fai clic sul tile **Delivery Pipeline**.
3. Fai clic su **Configura fase** nella fase di build.
4. Fai clic sulla scheda **Variabili di ambiente** per visualizzare le proprietà.
5. Modifica queste proprietà nella scheda Variabili di ambiente per consentire l'esecuzione corretta della toolchain. 

| Proprietà   | Descrizione   |
|---|---|
| `TF_VAR_ibm_sl_api_key` | La [chiave API dell'infrastruttura](#iaas-key) viene dalla console dell'infrastruttura. |
| `TF_VAR_ibm_sl_username` | Il [nome utente dell'infrastruttura](#user-key) che identifica l'account dell'infrastruttura. |
| `TF_VAR_ibm_cloud_api_key` | La [chiave API della piattaforma](#platform-key) {{site.data.keyword.cloud_notm}} viene utilizzata per abilitare la creazione del servizio. |
| `PUBLIC_KEY` | La [chiave pubblica](#public-key) definita per abilitare l'accesso all'istanza del server virtuale. |
| `PRIVATE_KEY` | La [chiave privata](#public-key) definita per abilitare l'accesso all'istanza del server virtuale. |
| `VI_INSTANCE_NAME` | Il nome generato automaticamente per l'istanza del server virtuale. |
| `GIT_USER` | Se imposti lo [stato Terraform](#tform-state) per memorizzare lo stato del comando applicato, è obbligatorio il nome utente GITLab. |
| `GIT_PASSWORD` | Se imposti lo [stato Terraform](#tform-state) per memorizzare lo stato del comando applicato, è obbligatoria la password GITLab. |
{: caption="Tabella 1. Variabili di ambiente da modificare per l'abilitazione" caption-side="top"}

### Richiamo della chiave API dell'infrastruttura 
{: #iaas-key}

Terraform richiede una chiave API dell'infrastruttura per creare le risorse dell'infrastruttura. Segui questa procedura per richiamare una chiave dell'infrastruttura. 

1. Passa all'[elenco utenti dell'infrastruttura ![Icona link esterno](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window} o **Menu** > **Infrastruttura** > **Account** > **Elenco utenti**.
2. Trova i dettagli dell'utente che sta creando la toolchain e fai clic su `Visualizza` nella colonna della chiave API o su `Genera`, entrambi i passi visualizzano la chiave API in una finestra di dialogo.
3. Copia la chiave API e sostituisci il valore nella configurazione della toolchain `TF_VAR_ibm_sl_api_key`.

### Richiamo del nome utente dell'infrastruttura
{: #user-key}

Per richiamare il nome utente dell'infrastruttura, attieniti alla seguente procedura. 

1. Passa all'[elenco utenti dell'infrastruttura ![Icona link esterno](../icons/launch-glyph.svg)](https://control.bluemix.net/account/users){: new_window} o **Menu** > **Infrastruttura** > **Account** > **Elenco utenti**.
2. Fai clic sull'utente per cui vuoi creare la toolchain.
3. Scorri verso il basso fino alla proprietà **Nome utente VPN**.
4. Taglia e incolla questo valore e sostituisci la configurazione della toolchain `TF_VAR_ibm_sl_username`.

### Richiamo della chiave API della piattaforma 
{: #platform-key}

Per consentire a Terraform di creare i servizi al livello della piattaforma come i database e i servizi Compose, è obbligatoria la chiave API della piattaforma. Segui questa procedura per richiamare una chiave della piattaforma. 

1. Fai clic su **Menu** > **Dashboard** per assicurarti che l'utente sia nel dashboard della piattaforma.
2. Fai clic su **Gestisci** > **Sicurezza** > **Chiavi API della piattaforma**.
3. Fai clic su **Create**.
4. Immetti un nome e una descrizione e fai clic su **Crea**.
5. Quando si apre la finestra di dialogo, fai clic su *Mostra* per controllare la chiave.
6. Copia e incolla la chiave negli appunti o scaricala. 
7. Sostituisci il valore nella configurazione della toolchain `TF_VAR_ibm_cloud_api_key` con il valore che è stato generato.

### Generazione della chiave pubblica e privata 
{: #public-key}

Per consentire alla toolchain di installare l'impacchettamento Debian nell'istanza di Virtual Server, segui questa procedura.

1. Nel tuo calcolo del client, utilizza le seguenti istruzioni per creare una [coppia di chiavi privata e pubblica ![Icona link esterno](../icons/launch-glyph.svg)](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/){: new_window}.
2. Passa alla [Vista delle chiavi SSH dell'infrastruttura ![Icona link esterno](../icons/launch-glyph.svg)](https://control.bluemix.net/devices/sshkeys){: new_window} o **Menu** > **Infrastruttura** > **Dispositivi** > **Gestisci** > **Chiavi SSH**.
3. Fai clic su **Aggiungi**.
4. Copia il contenuto della chiave privata che hai precedentemente creato e incollalo nel contenuto della chiave. 
5. Assegna un nome alla chiave e fai clic su **Aggiungi**.

### Abilitazione dello stato di Terraform 
{: #tform-state}

Terraform supporta l'archiviazione dello stato del comando `apply` di Terraform. Questo file di stato esegue il comando `apply` una seconda volta per determinare se uno dei file di configurazione terraform è stato modificato. Puoi memorizzare lo stato nel repository GIT gestito dall'applicazione e dalla configurazione.

Per abilitare l'archiviazione dello stato, configura le proprietà `GIT_USER` e `GIT_PASSWORD` nelle variabili di ambiente della toolchain. Per richiamare i valori, completa la seguente procedura:

1. Dalla vista Toolchain, accedi al repository GIT dallo strumento del codice. 
2. In GIT Lab, fai clic sull'icona **Icona profilo** e poi su **Impostazioni**.
3. Fai clic su **Account** e copia il nome utente e sostituisci il valore `GIT_USER`.
4. Fai clic su **Token di accesso**.
5. Definisci un nome per il tuo token, quindi fai clic su **Crea token di accesso personale**.
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

La cartella `terraform` contiene la configurazione dell'infrastruttura come codice che può essere utilizzato per eseguire il provisioning delle risorse dell'infrastruttura. Il file `main.tf` è l'origine principale per modificare le opzioni per la tua configurazione terraform.

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

Puoi anche eseguire il provisioning dei server bare metal con terraform. Per ulteriori informazioni, consulta [IBM Terraform Provider Documentation ![Icona link esterno](../icons/launch-glyph.svg)](https://ibm-cloud.github.io/tf-ibm-docs/v0.10.0/){: new_window} e [IBM Terraform Provider GIT Repo ![Icona link esterno](../icons/launch-glyph.svg)](https://github.com/IBM-Cloud/terraform-provider-ibm){: new_window}.

`variables.tf` può essere utilizzato per modificare il data center che vuoi destinare alla creazione dell'istanza virtuale. Per visualizzare l'elenco dei data center definiti sulla piattaforma, consulta [Data Centers ![Icona link esterno](../icons/launch-glyph.svg)](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}.

Per impostazione predefinita, il file terraform è configurato per Washington e `wdc04`.

```
variable "datacenter" {
  description = "Washington"
  default = "wdc04"
}
```

### Descrizione delle fasi della toolchain 
{: #toolchain-stages}

La toolchain mostra la distribuzione dell'infrastruttura e dell'applicazione in una semplice pipeline. Suddividi l'infrastruttura come parte di codice in una pipeline e la distribuzione dell'applicazione in un'altra pipeline. 

La toolchain viene suddivisa nelle seguenti fasi: 

1. La fase di build clona il repository GIT e impacchetta il codice in un pacchetto Debian.
2. La fase del piano Terraform prepara un piano terraform.

  ```
  terraform init -input=false
  terraform validate
  terraform plan -var "ssh_public_key=$PUBLIC_KEY" -input=false -out tfplan
  ```

3. La fase di applicazione di Terraform applica la configurazione terraform e attende finché l'indirizzo IP del server virtuale è disponibile.

  ```
  terraform apply -auto-approve -input=false tfplan
  terraform output "host ip" > hostip.txt
  ```

4. La fase di distribuzione, installazione e avvio sposta il pacchetto Debian creato nella prima fase nel server virtuale in esecuzione, lo installa e avvia.
5. La fase del controllo di integrità, convalida l'endpoint di integrità disponibile sull'applicazione e poi completa la pipeline.

Per accedere all'applicazione dopo che è stata avviata, controlla i log della fase del controllo di integrità. Fai clic sui link URL elencati nei log che mostrano l'indirizzo IP e la porta dell'applicazione.
