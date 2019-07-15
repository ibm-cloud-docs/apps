---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-20"

keywords: apps, mobile, mobile app, starter kit, developer tools, devops toolchain, toolchain, create mobile app, mobile starter kit, android, ios, swift, xcode

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Creazione di un'applicazione mobile
{: #tutorial-mobile}

{{site.data.keyword.cloud}} offre kit starter mobili per aiutarti a creare rapidamente un'applicazione mobile. Seleziona un linguaggio, un framework e gli strumenti dai kit starter mobili per iniziare a lavorare con un'applicazione preconfigurata. Oppure puoi utilizzare un kit starter di base per creare un'applicazione mobile personalizzata.
{: shortdesc}

## Prima di iniziare
{: #prereqs-mobile}

Installa la [CLI (command-line interface) {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-getting-started).

## Creazione di un'applicazione mobile con un kit starter preconfigurato
{: #create-mobile}

Per creare un'applicazione mobile utilizzando un kit starter preconfigurato, completa questa procedura:

1. Dalla pagina [Mobile Starter Kits ](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno") in {{site.data.keyword.dev_console}}, seleziona un kit starter in base alle funzioni che desideri. Ad esempio, seleziona **Watson Visual Recognition**.
2. Immetti il nome della tua applicazione. Per questa esercitazione, utilizza `WatsonApp`.
3. Facoltativo. Fornisci le tag per classificare la tua applicazione. Per ulteriori informazioni, consulta [Gestione delle tag](/docs/resources?topic=resources-tag).
4. Seleziona la tua piattaforma. Per questa esercitazione, seleziona **iOS Swift**. Alcuni kit starter potrebbero essere disponibili in un solo linguaggio.
5. Seleziona il tuo piano prezzi. Utilizza l'opzione **Lite** per questa esercitazione. Se alcuni servizi sono obbligatori, vengono automaticamente definiti nel kit starter.
6. Fai clic su **Create**.

## Creazione di un'applicazione mobile personalizzata con un kit starter di base
{: #create-mobile-basic}

Per creare un'applicazione mobile utilizzando un kit starter di base, completa questa procedura:

1. Dalla pagina [Mobile Starter Kits](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![Icona link esterno](../../icons/launch-glyph.svg "Icona link esterno") in {{site.data.keyword.dev_console}}, seleziona il tile **Create App**.
2. Immetti un nome per la tua applicazione. Per questa esercitazione, immetti `CustomMobile`.
3. Puoi, facoltativamente, fornire le tag per classificare la tua applicazione. Per ulteriori informazioni, consulta [Gestione delle tag](/docs/resources?topic=resources-tag).
4. Seleziona **Create a new app** come punto di partenza.
5. Seleziona **Mobile** come tipo di applicazione.
6. Seleziona il linguaggio e il framework. Alcuni kit starter potrebbero essere disponibili in un solo linguaggio.
7. Seleziona il tuo piano prezzi. Per questa esercitazione, puoi usare l'opzione gratuita.
8. Fai clic su **Crea**.

## Aggiunta di servizi (facoltativo)
{: #resources-mobile}

A seconda del kit starter che hai selezionato, alcuni servizi potrebbero essere già connessi alla tua applicazione. Puoi aggiungere servizi che migliorano la tua applicazione con la potenza cognitiva di Watson, aggiungere servizi mobili o servizi per la sicurezza. Per questa esercitazione, aggiungi una posizione per gestire i tuoi dati.

Per aggiungere un servizio alla tua applicazione, completa questa procedura:

1. Nella pagina **App details**, fai clic su **Create service**.
2. Seleziona il tipo di servizio che desideri. Ad esempio, seleziona **Databases** > **Next** > **Cloudant** > **Next**.
3. Seleziona il tuo piano prezzi. Utilizza l'opzione **Lite** per questa esercitazione. 
4. Fai clic su **Crea**.

## Scaricamento del codice
{: #mobile-download-code}

Per scaricare il tuo codice applicazione e utilizzarlo localmente, completa questa procedura:

1. Nella pagina **App details**, fai clic su **Download code**.
2. Importa l'applicazione nel tuo ambiente di sviluppo integrato.
3. Modifica e salva il codice.

## Esecuzione della tua applicazione mobile
{: #run-mobile-app}

### Esecuzione della tua applicazione Swift in Xcode
{: #run_swift}

Se stai utilizzando iOS Swift come tuoi linguaggi di implementazione, completa questa procedura:

1. Apri il file `README.md` in un visualizzatore Markdown per esaminare la procedura per configurare la tua applicazione.
2. Apri il tuo terminale e passa alla tua cartella dell'applicazione ed esegui i seguenti comandi:
    1. Esegui `pod setup` se hai bisogno di configurare il repository CocoaPods.
    2. Esegui `pod update` se hai bisogno di aggiornare i tuoi pod esistenti.
    3. Esegui `pod install` per installare i pod per la tua applicazione.
3. Apri il tuo progetto Xcode `<appname>.xcworkspace`.
4. Esegui la tua applicazione.

### Esecuzione della tua applicazione Android in Android Studio
{: #run_android}

Se stai utilizzando Android come piattaforma della tua applicazione mobile, completa questa procedura:

1. Apri il file `README.md` in un visualizzatore Markdown per configurare la tua applicazione.
2. Apri la tua applicazione `BasicProject-Android` in Android Studio.
3. Esegui la tua applicazione.

### Esecuzione della tua applicazione Cordova in Xcode
{: #run_cordova_xcode}

Se stai utilizzando Cordova come tuo linguaggio di implementazione, completa questa procedura:

1. Apri il file `README.md` in un visualizzatore Markdown per configurare la tua applicazione.
2. Apri la tua applicazione `platforms/ios` in Xcode.
3. Esegui la tua applicazione.

### Esecuzione della tua applicazione Cordova in Android Studio
{: #run_cordova_studio}

Se stai utilizzando Cordova come piattaforma della tua applicazione mobile, completa questa procedura:

1. Estrai il file `BasicProject-Cordova.zip`.
2. Apri il file `README.md` in un visualizzatore Markdown per configurare la tua applicazione.
3. Apri la tua applicazione `platforms/android` in Android Studio.
4. Esegui la tua applicazione.

## Informazioni correlate
{: #related-mobile}

Puoi trovare ulteriori informazioni sulle applicazioni mobili esplorando queste esercitazioni:

 * [Applicazione mobile iOS con Push Notifications](/docs/tutorials?topic=solution-tutorials-ios-mobile-push-analytics)
 * [Applicazione mobile nativa Android con Push Notifications](/docs/tutorials?topic=solution-tutorials-android-mobile-push-analytics)
 * [Applicazione mobile con un backend senza server](/docs/tutorials?topic=solution-tutorials-serverless-mobile-backend)
