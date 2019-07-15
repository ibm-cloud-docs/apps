---

copyright:

  years: 2019

lastupdated: "2019-06-03"

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

## O que aconteceu com mybluemix.net?
{: #domain-change-faq}
{: faq}

Uma nova opção de nome do host `*.appdomain.cloud` está disponível em cloud.ibm.com.

Anteriormente, o domínio `mybluemix.net` era usado para hospedar aplicativos em vários destinos de implementação, como o {{site.data.keyword.containerlong_notm}} ou Cloud Foundry. Qualquer app que você hospedou em `mybluemix.net` não será impactado.

O subdomínio para apps do Cloud Foundry é `cf.appdomain.cloud`. O subdomínio para apps que você implementa no {{site.data.keyword.containerlong_notm}} é `containers.appdomain.cloud`.

Para obter mais informações, consulte [Gerenciando seus domínios](/docs/apps?topic=creating-apps-update-domain).

## Onde posso encontrar uma lista de meus apps?
{: #cf-app}
{: faq}

Sua lista de recursos no [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") fornece informações de resumo para os apps criados. Na lista de recursos, a seção **Apps** contém todos os apps que você criou, mas *não* implementou no Cloud Foundry. A seção **Apps do Cloud Foundry** contém todos os apps que você criou e implementou no Cloud Foundry.

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

## Como parar um app do Cloud Foundry em minha conta?
{: #app-stop}
{: faq}

Se desejar parar um app do Cloud Foundry, conclua as etapas a seguir:


1. No Painel, clique em **Visualizar recursos** dentro da seção Resumo de recursos.
1. Na Lista de recursos, expanda as seções e localize a instância de serviço que deseja parar.
1. Selecione o menu **Ações**![Ícone Lista de ações](../icons/action-menu-icon.svg) e, em seguida, clique em **Parar**.

## O que são cadeias de ferramentas e como elas se relacionam com meu app?
{: #toolchains}
{: faq}

Uma cadeia de ferramentas é um conjunto de integrações de ferramenta que suporta as tarefas de desenvolvimento, implementação e operações. É possível criar uma cadeia de ferramentas a partir de seu aplicativo. A cadeia de
ferramentas pode suportar desenvolvimento, implementação e monitoramento contínuos e mais, e é associada ao seu app. Cada app pode ser
associado a uma cadeia de ferramentas. Uma cadeia de ferramentas pode ser configurada para que as mudanças na cadeia de ferramentas construam e implementem automaticamente o app. Para obter mais informações sobre as cadeias de ferramentas, consulte [Criando cadeias de ferramentas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## Como mudo o domínio para meus apps do Cloud Foundry?
{: #cf-domains-faq}
{: faq}

Para apps Cloud Foundry, é possível mudar seu domínio de `mybluemix.net` para `appdomain.cloud` usando o console do {{site.data.keyword.cloud_notm}} ou a interface da linha de comandos. Para obter mais informações sobre como mudar seu domínio para `appdomain.cloud`, consulte [Atualizando seu domínio](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain).

Quando você cria novos apps, o domínio compartilhado padrão é `mybluemix.net`, mas `appdomain.cloud` é outra opção de domínio que pode ser usada.
