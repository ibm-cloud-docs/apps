---

copyright:
  years: 2016, 2019
lastupdated: "2019-04-30"

keywords: scratch, developer tools, custom app, app tutorial, verify app running, run app local

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Creazione di un'applicazione da zero
{: #tutorial-scratch}

Puoi creare un'applicazione personalizzata da zero utilizzando i servizi e un runtime. 
{: shortdesc}

## Prima di iniziare
{: #prereqs-scratch}

* Installa la [{{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli), che include Docker. 
* Crea un account Docker, esegui l'applicazione Docker ed esegui l'accesso. Affinché i comandi di build funzionino è necessario che Docker sia in esecuzione.
* Se intendi distribuire la tua applicazione a {{site.data.keyword.cfee_full}}, devi [preparare il tuo account {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Creazione della tua applicazione
{: #create-scratch}

1. Dal tuo [dashboard {{site.data.keyword.cloud_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}), fai clic su **Crea un'applicazione** nel widget Apps.

  Puoi anche creare un'applicazione personalizzata dalla pagina [Kit starter ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://{DomainName}/developer/appservice/starter-kits/) nella {{site.data.keyword.dev_console}}.
  {: tip}

2. Immetti un nome per la tua applicazione. Per questa esercitazione, immetti `CustomProject`.
3. Puoi, facoltativamente, fornire le tag per classificare la tua applicazione. Per ulteriori informazioni, consulta [Gestione delle tag](/docs/resources?topic=resources-tag).
4. Seleziona il linguaggio e il framework. Alcuni kit starter potrebbero essere disponibili in un solo linguaggio.
5. Seleziona il tuo piano prezzi. Per questa esercitazione, puoi usare l'opzione gratuita.
6. Fai clic su **Crea**.

## Aggiunta di servizi (facoltativo)
{: #resources-scratch}

Puoi aggiungere servizi che migliorano la tua applicazione con la potenza cognitiva di Watson, aggiungere servizi mobili o servizi per la sicurezza. Per questa esercitazione, puoi aggiungere un'ubicazione per gestire i tuoi dati.

1. Nella pagina **App details**, fai clic su **Add service**.
2. Seleziona il tipo di servizio che desideri. Ad esempio, seleziona **Data** > **Next** > **Cloudant** > **Next**.
3. Seleziona il tuo piano prezzi. Per questa esercitazione, puoi usare l'opzione gratuita.
4. Fai clic su **Crea**.

## Creazione ed esecuzione dell'applicazione localmente
{: #build-run-scratch}

Puoi anche creare l'applicazione localmente per la verifica prima di distribuirla al cloud.

1. Nella pagina **App details**, fai clic su **Download code** o **Clone your repo** per utilizzare il tuo codice localmente.
2. Importa l'applicazione nel tuo ambiente di sviluppo integrato.
3. Modifica il codice.
4. Imposta l'[autenticazione Git](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) aggiungendo un token di accesso personale.
5. Accedi all'interfaccia riga di comando (o CLI, command-line interface) {{site.data.keyword.cloud_notm}}. Se la tua organizzazione utilizza accessi federati, utilizza l'opzione `-sso`; ad esempio:

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Esegui il seguente comando per impostare le tue destinazioni di organizzazione e spazio.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. Esegui il seguente comando per richiamare le credenziali.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Assicurati che il Docker sia in esecuzione ed esegui il seguente comando per creare la tua applicazione in un contenitore di sviluppo locale dalla directory.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Esegui il seguente comando per eseguire la tua applicazione in un contenitore di sviluppo locale.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. Vai a `http://localhost:3000` nel tuo browser. Il tuo numero di porta potrebbe essere diverso a seconda del runtime scelto.

## Distribuzione della tua applicazione
{: #deploy-scratch}

Fai clic su **Configure continuous delivery** nella pagina **App details**, seleziona una destinazione di distribuzione e fai clic su **Create**. {{site.data.keyword.cloud_notm}} crea automaticamente una toolchain aperta completa di un repository Git e della pipeline di fornitura continua.

L'abilitazione di una toolchain crea un ambiente di sviluppo basato sul team per la tua applicazione. Quando crei una toolchain, il servizio dell'applicazione crea un repository Git, in cui puoi visualizzare il codice sorgente, clonare la tua applicazione e creare e gestire i problemi. Hai anche accesso a un ambiente di laboratorio Git dedicato e a una pipeline di fornitura continua. Sono personalizzati per la destinazione di distribuzione che selezioni, sia che si tratti di [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) o [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers).

Dopo che hai selezionato la tua destinazione di distribuzione, apri il componente pipeline della tua nuova toolchain per iniziare il processo iniziale di creazione e distribuzione in modo da poter vedere la tua nuova applicazione nel giro di qualche minuto.

Tutte le toolchain che vengono create da un dashboard dello sviluppatore {{site.data.keyword.cloud_notm}} sono configurate per la distribuzione automatica.
{: note}

Per distribuire la tua applicazione con la riga di comando, utilizza `ibmcloud dev deploy`. Per ulteriori informazioni, vedi [Creazione e distribuzione delle applicazioni utilizzando la CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli).

Per ulteriori informazioni sulla distribuzione della tua applicazione, vedi [Distribuzione delle applicazioni](/docs/apps?topic=creating-apps-deploying-apps).

## Verifica che la tua applicazione sia in esecuzione
{: #verify-scratch}

Dopo che hai distribuito la tua applicazione, la Delivery Pipeline o la riga di comando ti indirizzano all'URL per la tua applicazione.

1. Dalla tua toolchain DevOps, fai clic su **Delivery Pipeline** e seleziona quindi **Deploy Stage**.
2. Fai clic su **View logs and history**.
3. Nel file di log, trova l'URL dell'applicazione:

   Alla fine del file di log, cerca la parola `urls` o `view`. Ad esempio, nel file di log potresti vedere una riga simile a `urls: my-app-devhost.mybluemix.net` o `View the application health at: http://<ipaddress>:<port>/health`.

4. Vai all'URL nel tuo browser. Se l'applicazione è in esecuzione, viene visualizzato un messaggio che include `Congratulations` o `{"status":"UP"}`.

Se stai utilizzando la riga di comando, esegui il comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) per visualizzare l'URL della tua applicazione. Vai quindi all'URL nel tuo browser.

