---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-06-26"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Criando uma API de backend para frontend
{: #tutorial}

É possível criar um app de um iniciador de backend para frontend. Use esses iniciadores para construir APIs de backend para frontend no Node.js, Java ou Swift usando uma variedade de estruturas: Express.js, MicroProfile/Java EE, Kitura ou Spring. É possível ver como instalar as ferramentas necessárias, construir e executar o app localmente e implementá-lo na nuvem.
{: shortdesc}

## Etapa 1: instalar as ferramentas
{: #before-you-begin}

Instale as [ferramentas do desenvolvedor![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.

## Etapa 2: Criar um app
{: #create-devex}

Crie um app no {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}.

1. Na página [Kits do iniciador ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) no {{site.data.keyword.dev_console}}, selecione um kit do iniciador para sua linguagem. Por exemplo, para um aplicativo Node.js, acesse **Backend do Express.js** e clique em **Selecionar kit do iniciador**.

2. Insira o nome de seu app. Para este tutorial, use `ExpressBackend`.

3. Insira um nome de host exclusivo, tal como suas iniciais mais `-devhost`. Por
exemplo:

   ```
   abc-devhost
   ```

   Esse nome do host é a rota de seu app. Por exemplo, `abc-devhost.mybluemix.net`

4. Selecione a plataforma da linguagem. Para este tutorial, use `Node.js`.

5. Clique em **Criar**.

## Etapa 3: opcional - incluir recursos
{: #add-services}

1. Na visualização **Detalhes do app**, clique em **Incluir recurso**.

2. Selecione o tipo de serviço desejado. Para este tutorial, selecione **Dados** > **Avançar** > **Cloudant NoSQL DB** > **Avançar**.

3. Clique em **Criar**.

## Etapa 4: opcional - criar a cadeia de ferramentas do DevOps
{: #add-toolchain}

A ativação de uma cadeia de ferramentas cria um ambiente de desenvolvimento baseado em equipe para seu app. Quando você criar uma cadeia de ferramentas, o Serviço de app fornecerá um repositório Git, no qual será possível visualizar o código-fonte, clonar seu app e criar e gerenciar problemas. Você também tem acesso a um ambiente Gitlab dedicado e um pipeline de entrega contínua que é customizado para a plataforma de implementação que você escolher, como Kubernetes ou Cloud Foundry.

A entrega contínua é ativada para alguns aplicativos. Você pode desejar ativar a entrega contínua para automatizar construções, testes e implementações por meio do Delivery Pipeline e GitHub.

1. Selecione seu app na página **Apps**.

2. Clique em **Implementar na nuvem**.

3. Selecione um método de implementação. É possível optar por:

	* Implementar em um cluster do Kubernetes. Provisione um cluster de hosts, denominado nós do trabalhador, para implementar e gerenciar contêineres de aplicativos altamente disponíveis. É possível criar um cluster ou implementar em um cluster existente.

	* Implementar usando o Cloud Foundry, no qual não é necessário gerenciar a infraestrutura subjacente.

## Etapa 5: gerar o seu código de aplicativo
{: #generate-code}

Se você tiver criado uma cadeia de ferramentas na etapa anterior, um repositório Git terá sido criado para seu app e será possível localizar o código lá. Siga estas etapas para acessar seu repositório:

1. Selecione seu app na página **Apps**.

2. Clique em **Visualizar cadeia de ferramentas**.

3. Clique no cartão **Git** sob o título **CODE** para abrir seu repositório, no qual é possível visualizar o código-fonte e clonar seu app.

Se uma cadeia de ferramentas não estiver ativada, será possível acessar seu código fazendo download da origem diretamente da visualização Detalhes do app.

1. Selecione seu app na página **Apps**.

2. Clique em **Código do download** para fazer download do archive do app.

## Etapa 6: começar a trabalhar em seu aplicativo
{: #code}

Comece a trabalhar com seu app transferido por download:

1. Expanda o arquivo arquivado.

2. Importe o app para seu IDE.

3. Modifique o código.

4. Use o {{site.data.keyword.dev_cli_notm}} para construir e executar seu código localmente.

## Etapa 7: construir e executar o aplicativo localmente
{: #build-run}

Inclua seu próprio código, a compilação e execute o app. É possível executar o aplicativo localmente em seu sistema host se você instala as ferramentas de construção necessárias ou usando o suporte de contêiner disponível no {{site.data.keyword.dev_cli_notm}}.

### Usando o {{site.data.keyword.dev_cli_short}}

1. Para construir o app no diretório de app atual, insira o comando a seguir:

   ```
   ibmcloud dev build
   ```
   {: codeblock}

2. Para executar o app no diretório de app atual, insira o comando a seguir:

   ```
   ibmcloud dev run
   ```
   {: codeblock}

3. É possível executar curl em seu servidor com:

   ```
   curl http://localhost:3000
   ```
   {: codeblock}

4. É possível visualizar o documento da API em seu servidor em:

   ```
   http://localhost:3000/swagger/api
   ```
   {: codeblock}

5. É possível explorar a API em seu servidor em:

   ```
   http://localhost:3000/explorer
   ```
   {: codeblock}

## Etapa 8: implementar para a nuvem
{: #deploy}

### Implementar usando uma cadeia de ferramentas
Há várias maneiras de implementar seu app para {{site.data.keyword.cloud_notm}}, mas usar uma cadeia de ferramentas de DevOps é a melhor maneira de implementar apps de produção.  Uma cadeia de ferramentas de DevOps permite automatizar facilmente as implementações para diversos ambientes e incluir rapidamente monitoramento, criação de log e serviços de alerta para ajudar a gerenciar seu app à medida que ele cresce.

Com uma cadeia de ferramentas configurada corretamente, um ciclo de construção-implementação se inicia automaticamente com cada mesclagem na ramificação Principal em seu repositório. Todas as cadeias de ferramentas criadas em um painel de desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.

Também é possível implementar seu app manualmente por meio de sua cadeia de ferramentas DevOps:

1. Selecione seu app na página **Apps**.

2. Clique em **Visualizar cadeia de ferramentas**.

3. Visualize seu pipeline de entrega no qual é possível iniciar construções, gerenciar a implementação e visualizar logs e histórico.

### Implementar usando o {{site.data.keyword.dev_cli_short}}
Se você optar por não usar uma cadeia de ferramentas, também será possível implementar usando o {{site.data.keyword.dev_cli_short}}.

Para implementar seu app para o Cloud Foundry, insira o comando a seguir:

```
ibmcloud dev deploy
```
{: codeblock}

Para implementar seu app em um cluster do Kubernetes, insira o comando a seguir:

```
ibmcloud dev deploy --target <container>
```
{: codeblock}

### Consulte seu app em execução
Quando o aplicativo for implementado, você verá uma URL semelhante a `abc-devhost.mybluemix.net` no pipeline do DevOps ou no terminal (se você estiver usando a linha de comandos). Visite essa URL em seu navegador.
