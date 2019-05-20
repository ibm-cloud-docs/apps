---

copyright:
  years: 2019
lastupdated: "2019-05-09"

keywords: developer tools, building apps, developer entry point, DevOps, toolchain, insights

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# DevOps Insights
{: #insights-overview}

{{site.data.keyword.DRA_full}} è una soluzione basata su cloud che fornisce informazioni approfondite da strumenti di integrazione continua e fornitura continua per aumentare la velocità, la qualità e il controllo delle tue applicazioni. Puoi aggiungere l'integrazione dello strumento {{site.data.keyword.DRA_short}} alla tua toolchain DevOps.
{: shortdesc}

{{site.data.keyword.DRA_short}} raccoglie e analizza i risultati di unit test, test funzionali e strumenti di code coverage per determinare se il tuo codice soddisfa i criteri predefiniti nelle porte specificate nel tuo processo di distribuzione. Se il codice non soddisfa o supera i criteri indicati, la distribuzione viene interrotta per evitare l'insorgere di rischi. Puoi utilizzare DevOps Insights come rete di sicurezza per il tuo ambiente di fornitura continua o come metodo per implementare e migliorare gli standard di qualità.

Questa integrazione dello strumento è disponibile solo su {{site.data.keyword.cloud_notm}} pubblico. È preconfigurata e non richiede alcun parametro di configurazione. Non puoi riconfigurare questa integrazione dello strumento.
{: note}

Per aggiungere l'integrazione dello strumento {{site.data.keyword.DRA_short}} alla tua toolchain DevOps, completa questa procedura:


1. [Crea la tua applicazione](/docs/apps?topic=creating-apps-tutorial-getting-started#create-getting-started).
2. Nella pagina App details, fai clic su **Configure continuous delivery** e segui le istruzioni per la configurazione di una toolchain DevOps. I passi variano a seconda di quale destinazione di distribuzione scegli.
3. Quando vedi il messaggio "Configured" sulla pagina App details, fai clic su **View toolchain**.
4. Sulla pagina della panoramica della toolchain, fai clic su **Add a Tool**.
5. Nella sezione delle integrazioni dello strumento, seleziona **{{site.data.keyword.DRA_short}}**.
6. Fai clic su **Create Integration**. {{site.data.keyword.DRA_short}} viene aggiunto alla tua toolchain.
7. Fai clic sul tile **{{site.data.keyword.DRA_short}}** per aprire la pagina Overview in cui puoi iniziare ad utilizzare **{{site.data.keyword.DRA_short}}**.

Per ulteriori informazioni, vedi l'[{{site.data.keyword.DRA_short}}Esercitazione introduttiva](/docs/services/DevOpsInsights?topic=DevOpsInsights-getting-started).
