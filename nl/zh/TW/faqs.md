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


# 常見問題
{: #apps-faq}

## 我可以在何處找到應用程式清單？
{: #cf-app}
{: faq}

[{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 中的資源清單提供您所建立之應用程式的摘要資訊。在資源清單中，**應用程式**區段包含您已建立但*未* 部署至 Cloud Foundry 的所有應用程式。**Cloud Foundry 應用程式**區段包含您已建立且已部署至 Cloud Foundry 的所有應用程式。

## 為何我嘗試部署應用程式時無法選取 Cloud Foundry 空間？
{: #cf-space}
{: faq}

您很有可能需要先建立一個 Cloud Foundry 空間。如果您使用 Cloud Foundry 指令行介面，請鍵入 `cf create-space <space_name> -o <organization_name>`。否則，請從主控台完成下列步驟：

1. 從 [{{site.data.keyword.cloud_notm}} 主控台](https://{DomainName}){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示") 的功能表列中，選取**管理** > **帳戶**。
2. 選取 **Cloud Foundry 組織**。
3. 按一下要在其中建立空間的組織名稱，然後按一下**新增空間**。

## 如何刪除應用程式？
{: #delete-apps}
{: faq}

若要刪除您建立的應用程式，請完成下列步驟：

1. 從 [{{site.data.keyword.cloud_notm}} 主控台 ](https://{DomainName}){: new_window} ![外部鏈結圖示](../icons/launch-glyph.svg "外部鏈結圖示")，按一下**功能表**圖示 ![「功能表」圖示](../icons/icon_hamburger.svg)，然後選取**資源清單**。
2. 按一下您要刪除之應用程式的**動作**圖示 ![動作圖示](../icons/action-menu-icon.svg)，然後按一下**刪除**。

## 何謂工具鏈，以及它們與我的應用程式的關係？
{: #toolchains}
{: faq}

工具鏈是一組整合的工具，支援開發、部署及操作作業。您可以從應用程式建立工具鏈。工具鏈可以支援連續開發、部署、監視及其他作業，且與您的應用程式相關聯。每個應用程式都可以與工具鏈相關聯。工具鏈可以配置為使工具鏈的變更自動建置及部署應用程式。如需工具鏈的相關資訊，請參閱[建立工具鏈](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)。
