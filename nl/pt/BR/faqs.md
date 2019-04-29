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


# FAQ
{: #apps-faq}

## Onde posso encontrar uma lista de meus apps?
{: #cf-app}
{: faq}

Sua lista de recursos no [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") fornece informações de resumo para os aplicativos que você criou. Na lista de recursos, a seção **Apps** contém todos os apps que você criou, mas *não* implementou no Cloud Foundry. A seção **Apps do Cloud Foundry** contém todos os apps que você criou e implementou no Cloud Foundry.

## Por que não posso selecionar um espaço do Cloud Foundry quando tento implementar meu app?
{: #cf-space}
{: faq}

É mais provável que você precise criar um espaço do Cloud Foundry primeiro. Se você estiver usando a interface da linha de comandos do Cloud Foundry, digite `cf create-space <space_name> -o <organization_name>`. Caso contrário, conclua estas etapas por meio do console:

1. Na barra de menus no [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"), selecione **Gerenciar** > **Conta**.
2. Selecione **Organizações do Cloud Foundry**.
3. Clique no nome da organização em que você deseja criar um espaço e clique em **Incluir um espaço**.

## Como eu excluo apps?
{: #delete-apps}
{: faq}

Para excluir um app que você criou, conclua estas etapas:

1. No [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"), clique no ícone **Menu** ![Ícone Menu](../icons/icon_hamburger.svg) e selecione **Lista de recursos**.
2. Clique no ícone **Ações** ![Ícone Ações](../icons/action-menu-icon.svg) para o app que você deseja excluir e clique em **Excluir**.

## O que são cadeias de ferramentas e como elas se relacionam com meu app?
{: #toolchains}
{: faq}

Uma cadeia de ferramentas é um conjunto de integrações de ferramenta que suporta as tarefas de desenvolvimento, implementação e operações. É possível criar uma cadeia de ferramentas a partir de seu aplicativo. A cadeia de
ferramentas pode suportar desenvolvimento, implementação e monitoramento contínuos e mais, e é associada ao seu app. Cada app pode ser
associado a uma cadeia de ferramentas. Uma cadeia de ferramentas pode ser configurada para que as mudanças na cadeia de ferramentas construam e implementem automaticamente o app. Para obter mais informações sobre as cadeias de ferramentas, consulte [Criando cadeias de ferramentas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).
