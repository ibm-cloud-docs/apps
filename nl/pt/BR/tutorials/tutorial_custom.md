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

# Criando um aplicativo customizado
{: #tutorial}

É possível criar um aplicativo customizado usando serviços e um tempo de execução. É possível ver como instalar as ferramentas necessárias, construir e executar o projeto localmente e implementá-lo na nuvem.
{: shortdesc}

## Etapa 1: instalar as ferramentas
{: #before-you-begin}

Instale as [ferramentas do desenvolvedor![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.

## Etapa 2: criar um projeto
{: #create-devex}

Crie um projeto no {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}:

1. Na página [Kits do iniciador ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) no {{site.data.keyword.dev_console}}, select **Criar projeto** para criar um aplicativo customizado.

2. Insira o nome do projeto. Para este tutorial, use `CustomProject`.   

3. Insira um nome de host exclusivo, tal como suas iniciais mais `-devhost`. Por
exemplo:

	```
	abc-devhost
	```

	Esse nome do host é a rota de seu projeto. Por exemplo, `abc-devhost.mybluemix.net`

4. Selecione a plataforma da linguagem. Para este tutorial, use `Node.js`.

5. (Opcional) É possível iniciar o andaime de seu backend de um documento do OpenAPI. Isso é útil para um desenvolvedor de backend que já tem seu cliente e contrato de integração de backend definido em um documento Swagger. Os tipos de arquivos **.yaml** e **.json** são suportados. Clique em **Incluir arquivo** para fazer upload de seu documento.

6. Clique em **Criar projeto**.

## Opcional: incluir recursos
{: #add-services}

1. Na visualização **Detalhes do projeto**, clique em **Incluir recurso**.

2. Selecione o tipo de serviço desejado. Para este tutorial, selecione **Dados** > **Avançar** > **Cloudant NoSQL DB** > **Avançar**.

4. Clique em **Criar**.

## Opcional: criar cadeia de ferramentas de DevOps
{: #add-toolchain}

A ativação de uma cadeia de ferramentas cria um ambiente de desenvolvimento baseado em equipe para seu projeto. Ao criar uma cadeia de ferramentas, o Serviço de Aplicativo fornecerá um repositório Git, no qual será possível visualizar o código-fonte, clonar seu projeto e criar e gerenciar problemas. Você também tem acesso a um ambiente Gitlab dedicado e um pipeline de entrega contínua que é customizado para a plataforma de implementação que você escolher, como Kubernetes ou Cloud Foundry.

A entrega contínua é ativada para alguns aplicativos. Você pode desejar ativar a entrega contínua para automatizar construções, testes e implementações por meio do Delivery Pipeline e GitHub.

1. Selecione seu projeto na página **Projetos**.

2. Clique em **Implementar na nuvem**.

3. Selecione um método de implementação. É possível optar por:

	* Implementar em um cluster do Kubernetes. Provisione um cluster de hosts, denominado nós do trabalhador, para implementar e gerenciar contêineres de aplicativos altamente disponíveis. É possível criar um cluster ou implementar em um cluster existente.

	* Implementar usando o Cloud Foundry, no qual não é necessário gerenciar a infraestrutura subjacente.

## Etapa 3: gerar seu código do projeto
{: #generate-code}

Se você criou uma cadeia de ferramentas na etapa anterior, um repositório Git foi criado para seu projeto e será possível localizar o código lá. Siga estas etapas para acessar seu repositório:

1. Selecione seu projeto na página **Projetos**.

2. Clique em **Visualizar cadeia de ferramentas**.

3. Clique no cartão **Git** sob o título **CODE** para abrir seu repositório, no qual é possível visualizar o código-fonte e clonar seu projeto.

Se uma cadeia de ferramentas não estiver ativada, será possível acessar seu código fazendo download da origem diretamente da visualização Detalhes do projeto.

1. Selecione seu projeto na página **Projetos**.

2. Clique em **Fazer download do código** para fazer download de seu archive de projeto.

## Etapa 4: começar a trabalhar em seu app
{: #code}

Comece a trabalhar com seu projeto transferido por download:

1. Expanda o arquivo arquivado.

2. Importe o projeto para seu IDE.

3. Modifique o código.

4. Use o {{site.data.keyword.dev_cli_notm}} para construir e executar seu código localmente.


## Etapa 5: construir e executar o app localmente
{: #build-run}

Inclua seu próprio código e execute o projeto. É possível executar o aplicativo localmente em seu sistema host se você instala as ferramentas de construção necessárias ou usando o suporte de contêiner disponível no {{site.data.keyword.dev_cli_notm}}.

### Usando o {{site.data.keyword.dev_cli_short}}

1. Para construir o projeto em seu diretório de projeto atual, insira o comando a seguir:

  ```
  bx dev build
  ```
  {: codeblock}

2. Para executar o projeto em seu diretório de projeto atual, insira o comando a seguir:

  ```
  bx dev run
  ```
  {: codeblock}

3. Abra seu navegador para `http://localhost:3000` (seu número da porta pode ser diferente dependendo do tempo de execução escolhido).


## Etapa 6: implementar na nuvem
{: #deploy}

### Implementar usando uma cadeia de ferramentas
Há várias maneiras de implementar seu app para {{site.data.keyword.cloud_notm}}, mas usar uma cadeia de ferramentas de DevOps é a melhor maneira de implementar apps de produção. Uma cadeia de ferramentas de DevOps permite automatizar facilmente as implementações para diversos ambientes e incluir rapidamente monitoramento, criação de log e serviços de alerta para ajudar a gerenciar seu app à medida que ele cresce.

Com uma cadeia de ferramentas configurada corretamente, um ciclo de construção-implementação se inicia automaticamente com cada mesclagem na ramificação Principal em seu repositório. Todas as cadeias de ferramentas criadas em um painel de desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.

Também é possível implementar seu app manualmente por meio de sua cadeia de ferramentas DevOps:

1. Selecione seu projeto na página **Projetos**.

2. Clique em **Visualizar cadeia de ferramentas**.

3. Visualize seu pipeline de entrega no qual é possível iniciar construções, gerenciar a implementação e visualizar logs e histórico.

### Implementar usando o {{site.data.keyword.dev_cli_short}}
Se você optar por não usar uma cadeia de ferramentas, também será possível implementar usando o {{site.data.keyword.dev_cli_short}}.

Para implementar seu projeto para Cloud Foundry, insira o comando a seguir:

  ```
  bx dev deploy
  ```
  {: codeblock}

Para implementar seu projeto para um cluster do Kubernetes, insira o comando a seguir:

```
bx dev deploy --target <container>
```
{: codeblock}

### Consulte seu app em execução
Quando o aplicativo for implementado, você verá uma URL semelhante a `abc-devhost.mybluemix.net` no pipeline do DevOps ou no terminal (se você estiver usando a linha de comandos). Visite essa URL em seu navegador.
