---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-07-23"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Criando um aplicativo móvel com um kit do iniciador
{: #tutorial}

O {{site.data.keyword.Bluemix}} oferece kits móveis do iniciador para ajudar a criar um app móvel rapidamente. Escolha uma linguagem, uma estrutura e ferramentas dos Kits do iniciador do Serviço de app para começar a trabalhar com um app customizado pré-configurado. Neste tutorial, é possível aprender a instalar as ferramentas necessárias, além de construir e executar o app localmente e implementá-lo na nuvem.
{: shortdesc}

## Etapa 1: instalar as ferramentas
{: #install-tools}

Instale as [ferramentas do desenvolvedor![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.

O Docker é instalado como parte das ferramentas do desenvolvedor. O Docker deve estar em execução para que os comandos de construção funcionem. Deve-se criar uma conta do Docker, executar o app Docker e conectar-se.

## Etapa 1: Criando um app com o {{site.data.keyword.dev_console}}
{: #create-devex}

1. Crie um app {{site.data.keyword.dev_console}} no {{site.data.keyword.Bluemix}}.
2. Na página [Kits do iniciador ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) no {{site.data.keyword.dev_console}}, selecione um kit do iniciador com base nos recursos desejados. Por exemplo, para um aplicativo Watson Language, selecione **Swift Kitura**.
3. Insira o nome de seu app. Para este tutorial, use `WatsonApp`.
4. Selecione a plataforma da linguagem. Para este tutorial, use `Swift`.
5. Selecione sua linguagem e estrutura. Alguns kits do iniciador podem estar disponíveis apenas em uma linguagem.
6. Selecione seu plano de precificação. Há uma opção grátis que pode ser usada para este tutorial.
7. Clique em **Criar**.

## Etapa 3: Incluir recursos (opcional)
{: #add-services}

É possível incluir recursos que aprimoram seu app com o poder cognitivo do Watson, incluir serviços móveis ou serviços de segurança. Para este tutorial, inclua um local para gerenciar seus dados.

1. Na janela de serviço do app, clique em **Incluir recurso**.
2. Selecione o tipo de serviço desejado. Por exemplo, selecione **Dados** > **Avançar** > **Cloudant** > **Avançar**.
3. Selecione seu plano de precificação. Há uma opção grátis que pode ser usada para este tutorial.
4. Clique em **Criar**.

## Etapa 4: criar uma cadeia de ferramentas do DevOps
{: #add-toolchain}

A ativação de uma cadeia de ferramentas cria um ambiente de desenvolvimento baseado em equipe para seu app. Quando você cria uma cadeia de ferramentas, o serviço de app cria um repositório Git, no qual é possível visualizar o código-fonte, clonar seu app e criar e gerenciar problemas. Você também tem acesso a um ambiente de laboratório Git dedicado e a um pipeline de entrega contínua. Eles são customizados para a plataforma de implementação escolhida, seja Kubernetes ou Cloud Foundry.

A entrega contínua é ativada para alguns aplicativos. É possível ativar a entrega contínua para automatizar construções, testes e implementações por meio do Delivery Pipeline e do GitHub.

1. Na janela de serviço do app, clique em **Implementar na nuvem**.
2. Selecione um método de implementação. Configure seu método de implementação de acordo com as instruções para o método escolhido.

    * Implementar em um cluster do Kubernetes. Crie um cluster de hosts, chamados de nós do trabalhador, para implementar e gerenciar contêineres de aplicativos altamente disponíveis. É possível criar um cluster ou implementar em um cluster existente.

    * Implemente com o Cloud Foundry, no qual não é necessário gerenciar a infraestrutura subjacente.

## Etapa 5: Construindo e executando o app localmente
{: #build-run}

A implementação de seu app na nuvem na última etapa criou uma cadeia de ferramentas. Uma cadeia de ferramentas cria um repositório Git para seu app no qual é possível localizar o código. Siga estas etapas para acessar o repositório. É possível construir o app localmente para teste antes de enviá-lo por push para a nuvem.

1. Na janela de serviço do app, clique em **Fazer download do código** ou **Clonar seu repositório** para trabalhar com seu código localmente.
2. Importe o app para seu ambiente de desenvolvimento integrado.
3. Modifique o código.
4. Configure a [Autenticação Git](/docs/services/ContinuousDelivery/git_working.html#git_authentication) incluindo um token de acesso pessoal.
5. Efetue login na interface da linha de comandos do {{site.data.keyword.Bluemix}}. Se a sua organização usar logins federados, use a opção `-sso`.

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Configure seus destinos org e space.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7.  Obtenha as credenciais.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Certifique-se de que o Docker esteja em execução e construa seu app em um contêiner de desenvolvimento local por meio do diretório.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Execute seu app em um contêiner de desenvolvimento local.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10.  Abra seu navegador para `http://localhost:3000`. Seu número de porta pode ser diferente, dependendo do tempo de execução escolhido.

### Executando seu app Swift no Xcode
{: #run_swift}

1. Abra o arquivo `README.md` em um visualizador de redução de preço para revisar as etapas para configurar seu app.
2. Abra seu terminal e navegue para sua pasta de app e execute os comandos a seguir:
    1. Execute `pod setup` se precisar configurar o repositório do CocoaPods.
    2. Execute `pod update` se precisar atualizar os pods existentes.
    3. Execute `pod install` para instalar os pods para seu app.
3. Abra sua área de trabalho do Xcode `<appname>.xcworkspace`.
4. Execute seu app.

### Executando seu app Cordova no Xcode
{: #run_cordova_xcode}

Se você optar por usar o Cordova como sua linguagem de implementação, siga estas instruções.

1. Abra o arquivo `README.md` em um visualizador de Markdown para configurar seu app.
2. Abra seu app `platforms/ios` no Xcode.
3. Execute seu app.

### Executando seu app Cordova no Android Studio
{: #run_cordova_studio}

Use essa seção se você escolher usar o Cordova como plataforma do seu app móvel.

1. Extraia o arquivo `BasicProject-Cordova.zip`.
2. Abra o arquivo `README.md` em um visualizador de Markdown para configurar seu app.
3. Abra seu app `platforms/android` no Android Studio.
4. Execute seu app.

### Executando seu app Android no Android Studio
{: #run_android}

Use esta seção se você escolher usar o Android como plataforma do seu app móvel.

1. Abra o arquivo `README.md` em um visualizador de Markdown para configurar seu app.
2. Abra seu app `BasicProject-Android` no Android Studio.
3. Execute seu app.

## Etapa 6: implementar na nuvem
{: #deploy}

### Implementar usando uma cadeia de ferramentas

É possível implementar seu app no {{site.data.keyword.cloud_notm}} de várias maneiras, mas uma cadeia de ferramentas do DevOps é a melhor maneira de implementar apps de produção. Com uma cadeia de ferramentas do DevOps, é possível automatizar facilmente implementações para muitos ambientes e incluir rapidamente serviços de monitoramento, criação de log e alerta para ajudar a gerenciar seu app à medida que ele cresce.

Com uma cadeia de ferramentas configurada corretamente, um ciclo de construção-implementação se inicia automaticamente com cada mesclagem na ramificação Principal em seu repositório. Todas as cadeias de ferramentas criadas por meio de um painel do desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.

Também é possível implementar seu app manualmente por meio de sua cadeia de ferramentas DevOps:

1. Na janela Detalhes do app, clique em **Visualizar cadeia de ferramentas**.

2. Clique em **Delivery Pipeline**, no qual é possível iniciar construções, gerenciar a implementação e visualizar logs e o histórico.

### Implemente usando o  {{site.data.keyword.dev_cli_short}}

Para implementar seu app para o Cloud Foundry, insira o comando a seguir:

```
ibmcloud dev deploy
```
{: pre}

Para implementar seu app em um cluster do Kubernetes, insira o comando a seguir:

```
ibmcloud dev deploy --target <container>
```
{: pre}

## Etapa 7: Verificar se seu app está em execução
{: #verify}

Após a implementação de seu app, o pipeline ou a linha de comandos do DevOps aponta para a URL de seu app, por exemplo, `abc-devhost.mybluemix.net`. Acesse essa URL em seu navegador.
