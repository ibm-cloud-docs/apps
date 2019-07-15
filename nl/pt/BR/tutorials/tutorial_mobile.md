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

# Criando um app móvel
{: #tutorial-mobile}

O {{site.data.keyword.cloud}} oferece kits do iniciador móvel para ajudar a criar um aplicativo móvel rapidamente. Selecione uma linguagem, estrutura e ferramentas por meio dos kits do iniciador móvel para começar a trabalhar com um app pré-configurado. Ou, é possível usar um kit do iniciador básico para criar um app móvel customizado.
{: shortdesc}

## Antes de começar
{: #prereqs-mobile}

Instale a [interface da linha de comandos (CLI) do {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-getting-started).

## Criando um app móvel com um kit do iniciador pré-configurado
{: #create-mobile}

Para criar um app móvel usando um kit do iniciador pré-configurado, conclua estas etapas:

1. Na página [Kits do iniciador móvel](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo") no {{site.data.keyword.dev_console}}, selecione um kit do iniciador baseado nos recursos desejados. Por exemplo, selecione **Watson Visual Recognition**.
2. Insira o nome de seu app. Para este tutorial, use `WatsonApp`.
3. Opcional. Forneça identificações para classificar o seu app. Para obter mais informações, consulte [Trabalhando com tags](/docs/resources?topic=resources-tag).
4. Selecione sua plataforma. Para este tutorial, selecione **iOS Swift**. Alguns kits do iniciador podem estar disponíveis apenas em uma linguagem.
5. Selecione seu plano de precificação. Use a opção **Lite** para este tutorial. Se quaisquer serviços forem necessários, eles serão definidos automaticamente no kit do iniciador.
6. Clique em **Criar**.

## Criando um app móvel customizado com um kit do iniciador básico
{: #create-mobile-basic}

Para criar um app móvel usando um kit do iniciador básico, conclua estas etapas:

1. Na página [Kits do iniciador móvel](https://{DomainName}/developer/mobile/starter-kits){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo") no {{site.data.keyword.dev_console}}, selecione o bloco **Criar app**.
2. Insira um nome para o seu app. Para esse tutorial, digite `CustomMobile`.
3. É possível, opcionalmente, fornecer identificações para classificar o seu app. Para obter mais informações, consulte [Trabalhando com tags](/docs/resources?topic=resources-tag).
4. Selecione **Criar um novo app** como um ponto de início.
5. Selecione **Móvel** como o tipo de app.
6. Selecione a linguagem e a estrutura. Alguns kits do iniciador podem estar disponíveis apenas em uma linguagem.
7. Selecione seu plano de precificação. É possível usar a opção grátis para esse tutorial.
8. Clique em **Criar**.

## Incluindo serviços (opcional)
{: #resources-mobile}

Dependendo do kit do iniciador que você selecionou, alguns serviços podem já estar conectados a seu app. É possível incluir serviços que aprimoram seu app com o poder cognitivo do Watson, incluir serviços remotos ou serviços de segurança. Para este tutorial, inclua um local para gerenciar seus dados.

Para incluir um serviço em seu app, conclua estas etapas:

1. Na página **Detalhes do app**, clique em **Criar serviço**.
2. Selecione o tipo de serviço desejado. Por exemplo, selecione **Bancos de dados** > **Avançar** > **Cloudant** > **Avançar**.
3. Selecione seu plano de precificação. Use a opção **Lite** para este tutorial.
4. Clique em **Criar**.

## Fazendo download do código
{: #mobile-download-code}

Para fazer download de seu código de app e trabalhar com ele localmente, conclua estas etapas:

1. Na página **Detalhes do app**, clique em **Fazer download do código**.
2. Importe o app para seu ambiente de desenvolvimento integrado.
3. Modifique e salve o código.

## Executando seu app móvel
{: #run-mobile-app}

### Executando seu app Swift no Xcode
{: #run_swift}

Se você estiver usando o iOS Swift como sua linguagem de implementação, conclua estas etapas:

1. Abra o arquivo `README.md` em um visualizador de Markdown para revisar as etapas para configurar seu app.
2. Abra seu terminal e navegue para sua pasta de app e execute os comandos a seguir:
    1. Execute `pod setup` se precisar configurar o repositório do CocoaPods.
    2. Execute `pod update` se precisar atualizar os pods existentes.
    3. Execute `pod install` para instalar os pods para seu app.
3. Abra sua área de trabalho Xcode `<appname>.xcworkspace`.
4. Execute seu app.

### Executando seu app Android no Android Studio
{: #run_android}

Se você estiver usando o Android como a plataforma de seu app móvel, conclua estas etapas:

1. Abra o arquivo `README.md` em um visualizador de Markdown para configurar seu app.
2. Abra seu app `BasicProject-Android` no Android Studio.
3. Execute seu app.

### Executando seu app Cordova no Xcode
{: #run_cordova_xcode}

Se você estiver usando o Cordova como seu linguagem de implementação, conclua estas etapas:

1. Abra o arquivo `README.md` em um visualizador de Markdown para configurar seu app.
2. Abra seu app `platforms/ios` no Xcode.
3. Execute seu app.

### Executando seu app Cordova no Android Studio
{: #run_cordova_studio}

Se você estiver usando o Cordova como a plataforma de seu app móvel, conclua estas etapas:

1. Extraia o arquivo `BasicProject-Cordova.zip`.
2. Abra o arquivo `README.md` em um visualizador de Markdown para configurar seu app.
3. Abra seu app `platforms/android` no Android Studio.
4. Execute seu app.

## Informações relacionadas
{: #related-mobile}

É possível aprender mais sobre apps móveis explorando estes tutoriais:

 * [Aplicativo móvel iOS com Push Notifications](/docs/tutorials?topic=solution-tutorials-ios-mobile-push-analytics)
 * [Aplicativo móvel nativo Android com Push Notifications](/docs/tutorials?topic=solution-tutorials-android-mobile-push-analytics)
 * [Aplicativo móvel com um back-end serverless](/docs/tutorials?topic=solution-tutorials-serverless-mobile-backend)
