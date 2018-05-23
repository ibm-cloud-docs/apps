---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-05-02"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creazione di un'applicazione mobile con un kit starter
{: #tutorial}

Puoi creare un'applicazione mobile da uno starter di base mobile. Vedrai come installare gli strumenti di cui hai bisogno e i passi per eseguire l'applicazione in Xcode e Android Studio.
{: shortdesc}

## Installa gli strumenti
{: #before-you-begin}

Installa gli [strumenti sviluppatore](/docs/cli/idt/index.html#create){: new_window}.

## Scegli come creare la tua applicazione
{: #choose_how}

Puoi creare un'applicazione utilizzando uno dei seguenti metodi:
- [{{site.data.keyword.dev_console}} basata sul web](#create-devex)
- [{{site.data.keyword.dev_cli_notm}} controllata dai comandi](#create-cli)

## Creazione di un'applicazione con la {{site.data.keyword.dev_console}}
{: #create-devex}

1. Crea un'applicazione {{site.data.keyword.dev_console}} in {{site.data.keyword.Bluemix}}.

    1. Dalla pagina dei [Starter Kits ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) in {{site.data.keyword.dev_console}}, seleziona un kit starter in base alle funzionalità che desideri. Ad esempio, per un'applicazione di linguaggio Watson, vai a **Watson Language** e fai clic su **Select Starter Kit**.

    2. Immetti il nome della tua applicazione. Per questa esercitazione, utilizza `WatsonApp`.   

    3. Seleziona la tua piattaforma di linguaggio. Per questa esercitazione, utilizza `Swift`.

    4. Fai clic su **Crea**.

### Facoltativo: aggiungi servizi
{: #add-services}

1. Seleziona la tua applicazione nella pagina **Apps**.

2. Fai clic su **Add Service**.

3. Seleziona il tipo di servizio che desideri. Per questa esercitazione, seleziona **Security** > **Next** > **App ID** > **Next**.

4. Immetti il nome del tuo servizio e fai clic su **Create**.

5. Per ulteriori informazioni sulla configurazione dell'autenticazione, consulta [Configurazione dei provider di identità ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/appid/identity-providers.html){: new_window}.

6. Per ulteriori informazioni sulla configurazione delle analisi, consulta [Introduzione a {{site.data.keyword.mobileanalytics_short}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/mobileanalytics/index.html){: new_window}.

7. Per ulteriori informazioni sulla configurazione di {{site.data.keyword.cloudant_short_notm}}, consulta [Introduzione a {{site.data.keyword.cloudant_short_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/Cloudant/index.html){: new_window}.

8. Per ulteriori informazioni sulla configurazione di {{site.data.keyword.objectstorageshort}}, consulta [Introduzione a {{site.data.keyword.objectstorageshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/ObjectStorage/index.html){: new_window}.

9. Per ulteriori informazioni sull'aggiunta di notifiche push, vedi la [documentazione delle notifiche push](/docs/services/mobilepush/c_overview_push.html#overview-push).

### Genera il tuo codice dell'applicazione
{: #generate-code}

1. Seleziona la tua applicazione nella pagina **Apps**.

2. Fai clic su **Download Code** per scaricare il tuo archivio dell'applicazione.

### Inizia ad utilizzare la tua applicazione
{: #code}

Inizia ad utilizzare la tua applicazione scaricata:

1. Espandi il file archiviato.

2. Passa alla nuova directory dell'applicazione.

3. Utilizza la {{site.data.keyword.dev_cli_notm}} per continuare.


## Creazione di un'applicazione con la {{site.data.keyword.dev_cli_notm}}
{: #create-cli}

1. Assicurati di installare la [{{site.data.keyword.dev_cli_short}}](/docs/cli/idt/index.html).

2. Nella tua finestra del terminale, passa a una directory locale di tua scelta ed esegui il seguente comando.

	```
	bx dev create
	```
	{: codeblock}

3. Fornisci i seguenti valori quando richiesto:

	* Seleziona un tipo di applicazione "Mobile Client", opzione 2
	* Seleziona che la lingua di implementazione è "iOS Swift", opzione 3
	* Seleziona il kit starter di "Mobile App: Basic", opzione 1
	* Immetti un nome per la tua applicazione: `MobileBasicProject`

    Nota: i numeri di selezione effettivi potrebbe cambiare con i miglioramenti degli strumenti.

4. Se vuoi aggiungere servizi alla tua applicazione, immetti `y` al prompt di domanda e rispondi alle rimanenti domande.

5. Quando il tuo `MobileBasicProject` è stato creato e salvato correttamente, passa alla cartella `MobileBasicProject/MobileBasicProject-Swift`.

### Esecuzione della tua applicazione Swift in Xcode
{: #run_swift}

1. Apri il file `README.md` in un visualizzatore markdown per esaminare la procedura per configurare la tua applicazione.

2. Apri il tuo terminale e passa alla tua cartella dell'applicazione ed esegui i seguenti comandi:
    1. Esegui `pod setup` se hai bisogno di configurare il repository CocoaPods.
    2. Esegui `pod update` se hai bisogno di aggiornare i tuoi pod esistenti.
    3. Esegui `pod install` per installare i pod per la tua applicazione.

3. Apri il tuo progetto Xcode `<appname>.xcworkspace`.

4. Esegui la tua applicazione.

### Esecuzione della tua applicazione Cordova in Xcode
{: #run_cordova_xcode}

Se hai scelto di utilizzare Cordova come il tuo linguaggio di implementazione, segui queste istruzioni.

1. Apri il file `README.md` in un visualizzatore Markdown per configurare la tua applicazione.

2. Apri la tua applicazione `platforms/ios` in Xcode.

3. Esegui la tua applicazione.

### Esecuzione della tua applicazione Cordova in Android Studio
{: #run_cordova_studio}

Utilizza questa sezione se scegli di utilizzare Cordova come piattaforma della tua applicazione mobile.

1. Estrai il file `BasicProject-Cordova.zip`.

2. Apri il file `README.md` in un visualizzatore Markdown per configurare la tua applicazione.

3. Apri la tua applicazione `platforms/android` in Android Studio.

4. Esegui la tua applicazione.

### Esecuzione della tua applicazione Android in Android Studio
{: #run_android}

Utilizza questa sezione se scegli di utilizzare Android come piattaforma della tua applicazione mobile.

1. Apri il file `README.md` in un visualizzatore Markdown per configurare la tua applicazione.

2. Apri la tua applicazione `BasicProject-Android` in Android Studio.

3. Esegui la tua applicazione.
