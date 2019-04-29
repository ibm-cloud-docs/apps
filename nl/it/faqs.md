---

copyright:

  years: 2019

lastupdated: "2019-04-03"

keywords: apps FAQs, apps frequently asked questions, applications FAQs, applications frequently asked questions

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}


# Domande frequenti
{: #apps-faq}

## Dove posso trovare un elenco delle mie applicazioni?
{: #cf-app}
{: faq}

Il tuo elenco di risorse nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno") fornisce informazioni di riepilogo per le applicazioni che hai creato. Nell'elenco di risorse, la sezione **Applicazioni** contiene tutte le applicazioni che hai creato ma *non* distribuito a Cloud Foundry. La sezione **Applicazioni Cloud Foundry** contiene tutte le applicazioni che hai creato e distribuito a Cloud Foundry.

## Perché non posso selezionare uno spazio Cloud Foundry quando provo a distribuire la mia applicazione?
{: #cf-space}
{: faq}

È molto probabile che tu debba prima creare uno spazio Cloud Foundry. Se stai utilizzando l'interfaccia di riga di comando Cloud Foundry, digita `cf create-space <space_name> -o <organization_name>`. Altrimenti, completa questa procedura dalla console:

1. Dalla barra dei menu nella [console {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno"), seleziona **Gestisci** > **Account**.
2. Seleziona **Organizzazioni Cloud Foundry**.
3. Fai clic sul nome dell'organizzazione in cui vuoi creare uno spazio e seleziona **Aggiungi uno spazio**.

## Come posso eliminare le applicazioni?
{: #delete-apps}
{: faq}

Per eliminare un'applicazione che hai creato, completa questa procedura:

1. Dalla [console {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Icona link esterno](../icons/launch-glyph.svg "Icona link esterno"), fai clic sull'icona **Menu** ![Icona Menu](../icons/icon_hamburger.svg) e seleziona **Elenco risorse**.
2. Fai clic sull'icona **Azioni** ![Icona Azioni](../icons/action-menu-icon.svg) per l'applicazione che vuoi eliminare e fai clic su **Elimina**.

## Cosa sono le toolchain e in che modo sono correlate alla mia applicazione?
{: #toolchains}
{: faq}

Una toolchain è un insieme di integrazioni degli strumenti che supportano attività di sviluppo, distribuzione e operative. Puoi creare una toolchain dalla tua applicazione. La toolchain può supportare lo sviluppo continuo, la distribuzione, il monitoraggio e altro ancora ed è associata alla tua applicazione. Ogni applicazione può essere associata a una toolchain. Una toolchain può essere configurata in modo tale che le modifiche apportate alla toolchain creino e distribuiscano automaticamente l'applicazione. Per ulteriori informazioni sulle toolchain, vedi [Creazione delle toolchain](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).
