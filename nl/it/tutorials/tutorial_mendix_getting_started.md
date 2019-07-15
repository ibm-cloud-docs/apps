---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-03"

keywords: apps, Mendix, starter kit, developer tools, Mendix app, create mendix app

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note .note}

# Creazione di applicazioni con Mendix
{: #create-mendix}

Mendix è un insieme di strumenti e un ambiente di sviluppo a basso codice che ti aiuta a distribuire più velocemente applicazioni multidispositivo, con meno risorse di sviluppo, che vengono eseguite su {{site.data.keyword.cloud}}. Selezionando un kit starter a basso codice Mendix, vieni guidato a configurare il tuo account sulla piattaforma Mendix, avviare il tuo progetto e selezionare la tua destinazione di distribuzione di Cloud Foundry o il tuo cluster Kubernetes.
{: shortdesc}

## Selezione di un kit starter
{: #starterkit-mendix}

1. Dal dashboard [{{site.data.keyword.cloud_notm}} App Service ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno"), fai clic su **Get Started**.
2. Seleziona un kit starter a basso codice Mendix da una delle seguenti categorie:
  * [Mobile ](https://{DomainName}/developer/appservice/starter-kits/mendix-mobile-app){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")
  * [Watson Web or Mobile App ](https://{DomainName}/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")
  * [Web App ](https://{DomainName}/developer/appservice/starter-kits/mendix-web-app){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")
3. Fai clic su **Create app**.
4. Nella pagina **App details**, denomina la tua applicazione e, facoltativamente, fornisci le tag per classificare la tua applicazione. Per ulteriori informazioni, consulta [Gestione delle tag](/docs/resources?topic=resources-tag).
5. Fai clic su **Crea**.

## Autorizzazione di IBM a creare il tuo progetto su Mendix e collegare gli account
{: #link-mendix-account}

Se non stai ancora utilizzando Mendix con {{site.data.keyword.cloud_notm}}, vieni guidato alla piattaforma Mendix per eseguire la registrazione e autorizzare {{site.data.keyword.cloud_notm}} a creare un nuovo progetto sulla piattaforma Mendix per tuo conto. Questo progetto è collegato a {{site.data.keyword.cloud_notm}}, quindi le distribuzioni sono automaticamente indirizzate a {{site.data.keyword.cloud_notm}}.

1. Se vedi questo messaggio, fai clic su **Link Account**.
  ```
  "To complete app creation, a Mendix user account is required. Would you like to link your account now?"
  ```
  {: screen}

2. Nella pagina di conferma di Mendix, seleziona **I agree to the Mendix Privacy Policy and Terms** e fai clic su **Confirm**.
3. Quando ti viene richiesto, fornisci l'indirizzo email, la password e il paese, quindi fai clic su **Create**.
4. Nella pagina **Authorize access to your Mendix account**, fai clic su **Authorize**.

Una volta completata l'autorizzazione, il tuo browser ritorna all'applicazione Mendix che stai creando. Viene visualizzata la pagina **Select a deployment target**.

## Selezione di una destinazione di distribuzione per la tua applicazione Mendix
{: #select-deployment}

1. Nella pagina **Select a deployment target**, seleziona Cloud Foundry o uno dei tuoi cluster Kubernetes in esecuzione su {{site.data.keyword.cloud_notm}}. Se il tuo account ha accesso a {{site.data.keyword.cfee_full_notm}}, puoi selezionare un tipo di deployer Cloud Foundry **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)** o **[Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**, che puoi utilizzare per creare e gestire ambienti isolati per ospitare applicazioni Cloud Foundry esclusivamente per la tua azienda. 
2. Facoltativo. Se non hai un cluster Kubernetes, puoi crearne uno ora.
3. Nella pagina **Configure toolchain**, seleziona la tua regione e il tuo gruppo di risorse e fai quindi clic su **Create**.

Viene creata una toolchain DevOps. La toolchain integra il tuo progetto Mendix nella piattaforma Mendix nel tuo ambiente {{site.data.keyword.cloud_notm}}. Un'applicazione predefinita viene distribuita alla tua destinazione di distribuzione in modo da consentirti di verificare che l'applicazione sia stata distribuita correttamente al completamento della toolchain DevOps. 

Le distribuzioni Mendix Cloud Foundry richiedono il servizio database PostGRES, che non ha un livello Lite. Se vuoi valutare i kit starter Mendix utilizzando un account lite, puoi indicare come destinazione un cluster Kubernetes di prova.
{: tip}

Se hai selezionato un cluster Kubernetes per la distribuzione, vedi l'[esercitazione Mendix Kubernetes](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube) per imparare come configurare il tuo cluster per l'uso di produzione.

## Continuazione del ciclo di vita di sviluppo e distribuzione di Mendix
{: #dev-lifecycle-mendix}

Mendix è un ambiente di creazione a basso codice. Il ciclo di vita di sviluppo richiede di aprire il tuo progetto nell'applicazione desktop Mendix Modeler.

1. Dalla tua applicazione {{site.data.keyword.cloud_notm}}, fai clic su **Edit on Mendix**.
2. Nel portale web Mendix, fai clic su **Edit in Desktop Modeler**.
  L'applicazione Mendix viene aperta nel Desktop Modeler.
3. Modifica la tua applicazione Mendix e salva le tue modifiche.
4. Utilizza il menu **Run** dell'applicazione Mendix Desktop Modeler e seleziona l'opzione **Run**.
  Il pacchetto di distribuzione viene creato e caricato su Mendix. Dopo che il pacchetto di distribuzione è stato creato, puoi distribuire la tua applicazione a {{site.data.keyword.cloud_notm}}.
5. Per distribuire la tua applicazione Mendix, torna alla tua pagina **App details** in {{site.data.keyword.cloud_notm}}, e fai clic su **Deploy**.
  Questa azione avvia la toolchain DevOps della tua applicazione, che estrae la distribuzione più recente da Mendix e la distribuisce al tuo ambiente di distribuzione. Una volta completata la distribuzione, la versione più recente della tua applicazione viene avviata automaticamente e diventa disponibile.

Tutte le applicazioni Mendix devono essere distribuite a {{site.data.keyword.cloud_notm}} facendo clic su **Configure continuous delivery** nella pagina **App details** in {{site.data.keyword.cloud_notm}}. Non richiamare manualmente le toolchain Mendix tramite l'interfaccia IBM DevOps. L'avvio manuale delle toolchain tramite l'interfaccia DevOps potrebbe causare una distribuzione non riuscita dovuta a una mancanza di metadati richiesti che sono critici per le distribuzioni Mendix. A seconda dello stato della tua applicazione, potrebbe verificarsi un malfunzionamento durante l'avvio della toolchain DevOps o un errore nell'applicazione distribuita.

Se avvii manualmente una toolchain e riscontri un malfunzionamento, puoi ripristinare la tua distribuzione dell'applicazione facendo clic su **Configure continuous delivery** nella pagina **App details** in {{site.data.keyword.cloud_notm}}. Questa azione attiva un flusso DevOps completo per l'applicazione Mendix, che include i metadati richiesti.
{: tip}

## Facoltativo: configurazione di {{site.data.keyword.cos_full_notm}} 
{: #mendix-cos}

Alcuni utenti potrebbero voler configurare la propria applicazione Mendix distribuita in modo che utilizzi {{site.data.keyword.cos_full}} per l'archiviazione persistente e i caricamenti di file. {{site.data.keyword.cos_full_notm}} è un servizio di archiviazione oggetti compatibile con S3. Per avvalersi dell'archiviazione file compatibile con S3, le applicazioni Mendix devono definire le seguenti variabili di ambiente per accedere a un'istanza {{site.data.keyword.cos_full_notm}}, dopo aver configurato la fornitura continua.

* `S3_ACCESS_KEY_ID` - La chiave S3, che fa parte delle credenziali {{site.data.keyword.cos_full_notm}}
* `S3_SECRET_ACCESS_KEY` - La chiave segreto S3, che fa parte delle credenziali {{site.data.keyword.cos_full_notm}}
* `S3_BUCKET_NAME` - Il bucket di archiviazione S3
* `S3_ENDPOINT` - L'endpoint di archiviazione S3
* `S3_USE_V2_AUTH` - Il valore è `true`

Per ulteriori informazioni sui bucket e le chiavi {{site.data.keyword.cos_full_notm}}, vedi la [Documentazione API{{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-gs-dev). Per ulteriori informazioni sui valori degli endpoint regionali e interregionali, vedi la [Documentazione {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints). Per ulteriori informazioni sul supporto Mendix per l'archiviazione compatibile con S3, vedi la [Documentazione del pacchetto di build Mendix](https://github.com/mendix/cf-mendix-buildpack#s3-settings){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno").

### Impostazioni {{site.data.keyword.cos_full_notm}} per le applicazioni Cloud Foundry
{: cos-cfapps}

Completa questa procedura per le distribuzioni Cloud Foundry:

1. Imposta queste variabili sulle distribuzioni Cloud Foundry utilizzando il comando `cf set-env`:

  ```
    ibmcloud cf set-env <YOUR_APP> S3_ACCESS_KEY_ID <YOUR_KEY>
    ibmcloud cf set-env <YOUR_APP> S3_SECRET_ACCESS_KEY <YOUR_SECRET_KEY>
    ibmcloud cf set-env <YOUR_APP> S3_BUCKET_NAME <YOUR_BUCKET>
    ibmcloud cf set-env <YOUR_APP> S3_ENDPOINT s3.us-south.cloud-object-storage.appdomain.cloud
    ibmcloud cf set-env <YOUR_APP> S3_USE_V2_AUTH true
  ```

2. Dopo aver specificato tutti questi valori, riprepara la tua applicazione Cloud Foundry in modo da applicare i nuovi valori.

  ```
    ibmcloud cf restage <YOUR_APP>
  ```

### Impostazioni {{site.data.keyword.cos_full_notm}} per le applicazioni Kubernetes
{: #cos-kubeapps}

Completa questa procedura per le distribuzioni Kubernetes:

1. Imposta le variabili di ambiente `S3_ACCESS_KEY_ID` e `S3_SECRET_ACCESS_KEY` come dei valori segreto Kubernetes nel cluster. Per ulteriori informazioni sulla creazione dei segreti Kubernetes, vedi la [Documentazione{{site.data.keyword.containershort_notm}}](/docs/containers?topic=containers-service-binding#adding_app).

2. In aggiunta a tutti i valori esistenti, specifica le variabili di ambiente come delle variabili di ambiente aggiuntive nel file `mendix-app.yaml` all'interno della cartella `chart/<appname>/templates` del repository Git. I nomi del segreto devono corrispondere a quelli che sono stati creati nel passo precedente.

  ```
    env:
      - name: S3_ACCESS_KEY_ID
        valueFrom:
          secretKeyRef:
            name: "mendix-s3-key"
            key: db-endpoint
      - name: S3_SECRET_ACCESS_KEY
        valueFrom:
          secretKeyRef:
            name: "mendix-s3-secret-key"
            key: db-endpoint
      - name: S3_ENDPOINT
        value: "s3.us-south.cloud-object-storage.appdomain.cloud"
      - name: S3_USE_V2_AUTH
        value: "true"
  ```

3. Dopo aver applicato le modifiche Kubernetes, ridistribuisci la tua applicazione andando alla pagina **App details** e facendo clic su **Deploy**. 

## Passi successivi 
{: #next-steps-mendix}

Per distribuire la tua applicazione a {{site.data.keyword.containerlong_notm}}, configura la tua applicazione per la distribuzione di produzione. Per ulteriori informazioni, vedi l'[esercitazione Mendix Kubernetes](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube). 
