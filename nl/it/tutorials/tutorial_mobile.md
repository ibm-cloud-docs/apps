---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-03-16"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creazione di un'applicazione mobile con un kit starter
{: #tutorial}

Puoi creare un progetto mobile da uno starter di base mobile. Vedrai come installare gli strumenti di cui hai bisogno e i passi per eseguire il progetto in Xcode e Android Studio.
{: shortdesc}

## Installa gli strumenti
{: #before-you-begin}

Installa gli [strumenti sviluppatore](/docs/cli/idt/index.html#add-cli){: new_window}.


## Scegli come creare il tuo progetto
{: #choose_how}

Puoi creare un progetto utilizzando uno dei seguenti metodi:
- [{{site.data.keyword.dev_console}} basata sul web](#create-devex)
- [{{site.data.keyword.dev_cli_notm}} controllata dai comandi](#create-cli)


## Creazione di un progetto con la {{site.data.keyword.dev_console}}
{: #create-devex}

1. Crea un progetto {{site.data.keyword.dev_console}} in {{site.data.keyword.Bluemix}}.

    1. Dalla pagina dei [Starter Kits ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) in {{site.data.keyword.dev_console}}, seleziona un kit starter in base alle funzionalità che desideri. Ad esempio, per un'applicazione di linguaggio Watson, vai a **Watson Language** e fai clic su **Select Starter Kit**.

    2. Immetti il nome del tuo progetto. Per questa esercitazione, utilizza `WatsonProject`.   

    3. Seleziona la tua piattaforma di linguaggio. Per questa esercitazione, utilizza `Swift`.

    4. Fai clic su **Create Project**.

### Facoltativo: aggiungi servizi
{: #add-services}

1. Seleziona il tuo progetto nella pagina **Projects**.

2. Fai clic su **Add Service**.

3. Seleziona il tipo di servizio che desideri. Per questa esercitazione, seleziona **Security** > **Next** > **App ID** > **Next**.

4. Immetti il nome del tuo servizio e fai clic su **Create**.

5. Per ulteriori informazioni sulla configurazione dell'autenticazione, consulta [Configurazione dei provider di identità ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/appid/identity-providers.html){: new_window}.

6. Per ulteriori informazioni sulla configurazione delle analisi, consulta [Introduzione a {{site.data.keyword.mobileanalytics_short}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/mobileanalytics/index.html){: new_window}.

7. Per ulteriori informazioni sulla configurazione di {{site.data.keyword.cloudant_short_notm}}, consulta [Introduzione a {{site.data.keyword.cloudant_short_notm}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/Cloudant/index.html){: new_window}.

8. Per ulteriori informazioni sulla configurazione di {{site.data.keyword.objectstorageshort}}, consulta [Introduzione a {{site.data.keyword.objectstorageshort}} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno")](/docs/services/ObjectStorage/index.html){: new_window}.

9. Per ulteriori informazioni sull'aggiunta di notifiche push, vedi la [documentazione delle notifiche push](/docs/services/mobilepush/c_overview_push.html#overview-push).

### Genera il tuo codice del progetto
{: #generate-code}

1. Seleziona il tuo progetto nella pagina **Projects**.

2. Fai clic su **Download Code** per scaricare il tuo archivio del progetto.


### Inizia ad utilizzare la tua applicazione
{: #code}

Inizia ad utilizzare il tuo progetto scaricato:

1. Espandi il file archiviato.

2. Passa alla nuova directory del progetto.

3. Utilizza la {{site.data.keyword.dev_cli_notm}} per continuare.


## Creazione di un progetto con la {{site.data.keyword.dev_cli_notm}}
{: #create-cli}

1. Assicurati di installare la [{{site.data.keyword.dev_cli_short}}](/docs/cli/idt/index.html).

2. Nella tua finestra del terminale, passa a una directory locale di tua scelta ed esegui il seguente comando.

	```
	bx dev create
	```
	{: codeblock}

3. Fornisci i seguenti valori quando richiesto:

	* Seleziona un tipo di progetto "Mobile Client", opzione 2
	* Seleziona che la lingua di implementazione è "iOS Swift", opzione 3
	* Seleziona il kit starter di "Mobile App: Basic", opzione 1
	* Immetti un nome per il tuo progetto: `MobileBasicProject`

    Nota: i numeri di selezione effettivi potrebbe cambiare con i miglioramenti degli strumenti.

4. Se vuoi aggiungere servizi al tuo progetto, immetti `y` quando viene domandato e rispondi alle rimanenti domande.

5. Quando il tuo `MobileBasicProject` è stato creato e salvato correttamente, passa alla cartella `MobileBasicProject/MobileBasicProject-Swift`.

### Esecuzione del tuo progetto Swift in Xcode
{: #run_swift}

1. Apri il file `README.md` in un visualizzatore markdown per rivedere le istruzioni per configurare il tuo progetto.

2. Apri il tuo terminale e passa alla tua cartella del progetto ed esegui i seguenti comandi:
    1. Esegui `pod setup` se hai bisogno di configurare il repository CocoaPods.
    2. Esegui `pod update` se hai bisogno di aggiornare i tuoi pod esistenti.
    3. Esegui `pod install` per installare i pod per il tuo progetto.

3. Apri il tuo progetto Xcode `<projectname>.xcworkspace`.

4. Esegui la tua applicazione.

### Esecuzione del tuo progetto Cordova in Xcode
{: #run_cordova_xcode}

Se hai scelto di utilizzare Cordova come il tuo linguaggio di implementazione, segui queste istruzioni.

1. Apri il file `README.md` in un visualizzatore Markdown per configurare il tuo progetto.

2. Apri il tuo progetto `platforms/ios` in Xcode.

3. Esegui la tua applicazione.


### Esecuzione del tuo progetto Cordova in Android Studio
{: #run_cordova_studio}

Utilizza questa sezione se scegli di utilizzare Cordova come piattaforma della tua applicazione mobile.

1. Estrai il file `BasicProject-Cordova.zip`.

2. Apri il file `README.md` in un visualizzatore Markdown per configurare il tuo progetto.

3. Apri il tuo progetto `platforms/android` in Android Studio.

4. Esegui la tua applicazione.


### Esecuzione del tuo progetto Android in Android Studio
{: #run_android}

Utilizza questa sezione se scegli di utilizzare Android come piattaforma della tua applicazione mobile.

1. Apri il file `README.md` in un visualizzatore Markdown per configurare il tuo progetto.

2. Apri il tuo progetto `BasicProject-Android` in Android Studio.

3. Esegui la tua applicazione.
