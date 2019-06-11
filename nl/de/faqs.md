---

copyright:

  years: 2019

lastupdated: "2019-05-22"

keywords: apps FAQs, apps frequently asked questions, applications FAQs, applications frequently asked questions

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}


# Häufig gestellte Fragen
{: #apps-faq}

## Was ist mit 'mybluemix.net' passiert?
{: #domain-change-faq}
{: faq}

Unter 'cloud.ibm.com' ist eine neue Option `*.appdomain.cloud` für den Hostnamen verfügbar.

Zuvor wurde die Domäne `mybluemix.net` für das Hosting von Apps in unterschiedlichen Bereitstellungszielen wie beispielsweise {{site.data.keyword.containerlong_notm}} oder Cloud Foundry verwendet. Bereits unter `mybluemix.net` gehostete Apps sind nicht betroffen.

Die Unterdomäne für Cloud Foundry-Apps heißt `cf.appdomain.cloud`. Die Unterdomäne für Apps, die Sie in {{site.data.keyword.containerlong_notm}} bereitstellen, heißt `containers.appdomain.cloud`.

Weitere Informationen enthält der Abschnitt [Eigene Domänen verwalten](/docs/apps?topic=creating-apps-update-domain).

## Wo finde ich eine Liste meiner Apps?
{: #cf-app}
{: faq}

Ihre Ressourcenliste in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") enthält zusammengefasste Informationen zu den von Ihnen erstellten Anwendungen. Der Abschnitt **Apps** in der Ressourcenliste enthält alle Apps, die Sie erstellt, aber *nicht* in Cloud Foundry bereitgestellt haben. Der Abschnitt **Cloud Foundry-Apps** enthält alle Apps, die Sie erstellt und in Cloud Foundry bereitgestellt haben.

## Warum kann ich keinen Cloud-Foundry-Bereich auswählen, wenn ich versuche, meine App bereitzustellen?
{: #cf-space}
{: faq}

Sie müssen wahrscheinlich zuerst einen Cloud Foundry-Bereich erstellen. Wenn Sie die Cloud Foundry-Befehlszeilenschnittstelle verwenden, geben Sie `cf create-space <space_name> -o <organization_name>` ein. Andernfalls führen Sie die folgenden Schritte über die Konsole aus:

1. Wählen Sie in der Menüleiste der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") die Optionen **Verwalten** > **Konto** aus.
2. Wählen Sie **Cloud Foundry-Organisationen** aus.
3. Klicken Sie auf den Namen der Organisation, in der Sie einen Bereich erstellen möchten, und auf **Bereich hinzufügen**.

## Wie lösche ich Apps?
{: #delete-apps}
{: faq}

Führen Sie die folgenden Schritte aus, um eine App zu löschen, die Sie erstellt haben:

1. Klicken Sie in der [{{site.data.keyword.cloud_notm}}-Konsole](https://{DomainName}){: new_window} ![Symbol für externen Link](../icons/launch-glyph.svg "Symbol für externen Link") auf das Symbol **Menü** ![Menüsymbol](../icons/icon_hamburger.svg) und wählen Sie **Ressourcenliste** aus.
2. Klicken Sie auf das Symbol **Aktionen** ![Aktionssymbol](../icons/action-menu-icon.svg) für die zu löschende App und klicken Sie auf **Löschen**.

## Wie stoppe ich eine Cloud Foundry-App in meinen Konto?
{: #app-stop}
{: faq}

Führen Sie die folgenden Schritte aus, um eine Cloud Foundry-App zu stoppen:


1. Klicken Sie im Abschnitt für die Ressourcenzusammenfassung des Dashboards auf **Ressourcen anzeigen**.
1. Erweitern Sie die Abschnitte in der Ressourcenliste und suchen Sie die Serviceinstanz, die Sie stoppen möchten.
1. Wählen Sie im Menü **Aktionen** ![Symbol für Aktionsliste](../icons/action-menu-icon.svg) aus und klicken Sie dann auf **Stoppen**.

## Was sind Toolchains und inwiefern sind sie für meine App relevant?
{: #toolchains}
{: faq}

Eine Toolchain ist ein Satz von Toolintegrationen, die die Entwicklung, Bereitstellung sowie Operationstasks unterstützen. Sie können eine Toolchain aus Ihrer App heraus erstellen. Die Toolchain kann u.a. eine kontinuierliche Entwicklung, Bereitstellung oder Überwachung unterstützen und wird Ihrer App zugeordnet. Jede App kann einer Toolchain zugeordnet werden. Eine Toolchain kann so konfiguriert werden, dass Änderungen an der Toolchain automatisch die App erstellen und bereitstellen. Weitere Informationen zu Toolchains finden Sie unter [Toolchains erstellen](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## Wie kann ich die Domäne für meine Cloud Foundry-Apps ändern?
{: #cf-domains-faq}
{: faq}

Bei Cloud Foundry-Apps können Sie Ihre Domäne von `mybluemix.net` in `appdomain.cloud` ändern, indem Sie entweder die {{site.data.keyword.cloud_notm}}-Konsole oder die Befehlszeilenschnittstelle verwenden. Weitere Informationen zum Ändern Ihrer Domäne in `appdomain.cloud` finden Sie unter [Aktualisieren Ihrer Domäne](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).

Wenn Sie neue Apps erstellen, heißt die gemeinsam genutzte Standarddomäne `mybluemix.net`, aber `appdomain.cloud` ist eine weitere Domänenoption, die Sie verwenden können.
