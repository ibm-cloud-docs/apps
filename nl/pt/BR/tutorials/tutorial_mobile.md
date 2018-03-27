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

# Criando um aplicativo móvel com um kit do iniciador
{: #tutorial}

É possível criar um projeto móvel por meio de um iniciador básico móvel. Você verá como instalar as ferramentas necessárias e as etapas para executar o projeto no Xcode e Android Studio.
{: shortdesc}

## Instalar as ferramentas
{: #before-you-begin}

Instale as [ferramentas do desenvolvedor](/docs/cli/idt/index.html#add-cli){: new_window}.


## Escolha como criar o seu projeto
{: #choose_how}

É possível criar um projeto usando um dos métodos a seguir:
- [{{site.data.keyword.dev_console}}](#create-devex) baseado na web
- [{{site.data.keyword.dev_cli_notm}}](#create-cli) acionado por comando local


## Criando um projeto com o {{site.data.keyword.dev_console}}
{: #create-devex}

1. Crie um projeto {{site.data.keyword.dev_console}} no {{site.data.keyword.Bluemix}}.

    1. Na página [Kits do iniciador ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) no {{site.data.keyword.dev_console}}, selecione um Kit do iniciador com base nos recursos desejados. Por exemplo, para um aplicativo Watson Language, acesse **Watson Language** e clique em **Selecionar kit do iniciador**.

    2. Insira o nome do projeto. Para este tutorial, use `WatsonProject`.   

    3. Selecione a plataforma da linguagem. Para este tutorial, use `Swift`.

    4. Clique em **Criar projeto**.

### Opcional: incluir serviços
{: #add-services}

1. Selecione seu projeto na página **Projetos**.

2. Clique em **Incluir serviço**.

3. Selecione o tipo de serviço desejado. Para este tutorial, selecione **Segurança** > **Avançar** > **ID do app** > **Avançar**.

4. Insira o nome do serviço e clique em **Criar**.

5. Para obter mais informações sobre como configurar a autenticação, veja [Configurando provedores de identidade ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/appid/identity-providers.html){: new_window}.

6. Para obter mais informações sobre como configurar a analítica, veja [Introdução ao {{site.data.keyword.mobileanalytics_short}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/mobileanalytics/index.html){: new_window}.

7. Para obter mais informações sobre como configurar o {{site.data.keyword.cloudant_short_notm}}, consulte
[Introdução ao {{site.data.keyword.cloudant_short_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/Cloudant/index.html){: new_window}.

8. Para obter mais informações sobre como configurar o {{site.data.keyword.objectstorageshort}}, consulte
[Introdução ao {{site.data.keyword.objectstorageshort}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](/docs/services/ObjectStorage/index.html){: new_window}.

9. Para obter mais informações sobre como incluir notificações push, veja a [documentação de notificações](/docs/services/mobilepush/c_overview_push.html#overview-push) push.

### Gerar seu código do projeto
{: #generate-code}

1. Selecione seu projeto na página **Projetos**.

2. Clique em **Fazer download do código** para fazer download de seu archive de projeto.


### Começar a trabalhar em seu app
{: #code}

Comece a trabalhar com seu projeto transferido por download:

1. Expanda o arquivo arquivado.

2. Navegue até o novo diretório de projeto.

3. Use o {{site.data.keyword.dev_cli_notm}} para continuar.


## Criando um projeto com o {{site.data.keyword.dev_cli_notm}}
{: #create-cli}

1. Assegure-se de instalar o [{{site.data.keyword.dev_cli_short}}](/docs/cli/idt/index.html).

2. No prompt do Terminal, navegue para um diretório local de sua preferência e execute o comando a seguir.

	```
	bx dev create
	```
	{: codeblock}

3. Forneça os valores a seguir quando solicitado:

	* Selecione um tipo de projeto "Cliente móvel", opção 2
	* Selecione a linguagem de implementação como "iOS Swift", opção 3
	* Selecione kit do iniciador de "App móvel: básico", opção 1
	* Insira um nome para seu projeto: `MobileBasicProject`

    Nota: os números reais de seleção podem mudar com os aprimoramentos de ferramentas.

4. Se desejar incluir serviços no projeto, digite `y` no prompt de pergunta e responda às perguntas restantes.

5. Quando o `MobileBasicProject` for criado e salvo com êxito, navegue para a pasta `MobileBasicProject/MobileBasicProject-Swift`.

### Executando seu projeto do Swift no Xcode
{: #run_swift}

1. Abra o arquivo `README.md` em um visualizador de redução de preço para revisar as etapas para configurar seu projeto.

2. Abra seu terminal e navegue para sua pasta do projeto e execute os comandos a seguir:
    1. Execute `pod setup` se precisar configurar o repositório do CocoaPods.
    2. Execute `pod update` se precisar atualizar os pods existentes.
    3. Execute `pod install` para instalar os pods para o seu projeto.

3. Abra sua área de trabalho do Xcode `<projectname>.xcworkspace`.

4. Execute seu app.

### Executando seu projeto do Cordova no Xcode
{: #run_cordova_xcode}

Se você optar por usar o Cordova como sua linguagem de implementação, siga estas instruções.

1. Abra o arquivo `README.md` em um visualizador de Redução de preço para configurar o projeto.

2. Abra seu projeto `platforms/ios` no Xcode.

3. Execute seu app.


### Executando seu projeto do Cordova no Android Studio
{: #run_cordova_studio}

Use essa seção se você escolher usar o Cordova como plataforma do seu app móvel.

1. Extraia o arquivo `BasicProject-Cordova.zip`.

2. Abra o arquivo `README.md` em um visualizador de Redução de preço para configurar o projeto.

3. Abra seu projeto `platforms/android` no Android Studio.

4. Execute seu app.


### Executando seu projeto do Android no Android Studio
{: #run_android}

Use esta seção se você escolher usar o Android como plataforma do seu app móvel.

1. Abra o arquivo `README.md` em um visualizador de Redução de preço para configurar o projeto.

2. Abra seu projeto `BasicProject-Android` no Android Studio.

3. Execute seu app.
