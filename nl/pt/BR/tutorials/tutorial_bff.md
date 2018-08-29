---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-08-21"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Criando uma API de backend para frontend
{: #tutorial}

É possível criar um app por meio de um iniciador de backend para frontend. Use esses iniciadores para construir APIs de backend para frontend
em Node.js, Java ou Swift usando várias estruturas: Express.js, MicroProfile/Java EE, Kitura ou Spring. É possível ver como instalar as ferramentas necessárias, criar e executar o app localmente e implantá-lo na nuvem.
{: shortdesc}

## Etapa 1. Instale as ferramentas
{: #install-tools}

Instale as [ferramentas do desenvolvedor![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/IBM-Bluemix/ibm-cloud-developer-tools){: new_window}.

O Docker é instalado como parte das ferramentas do desenvolvedor. O Docker deve estar em execução para que os comandos de construção funcionem. Deve-se criar uma conta do Docker, executar o app Docker e conectar-se.

## Etapa 2. Criar um app
{: #create-devex}

Crie um app no  {{site.data.keyword.cloud}}  {{site.data.keyword.dev_console}}.

1. Na página [Kits do iniciador ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.ng.bluemix.net/developer/appservice/starter-kits/) no {{site.data.keyword.dev_console}}, selecione um kit do iniciador para sua linguagem. Por exemplo, para um aplicativo Node.js, acesse **Backend do Express.js** e clique em **Selecionar kit do iniciador**.

2. Insira o nome de seu app. Para este tutorial, use `ExpressBackend`.

3. Insira um nome de host exclusivo, por exemplo, `abc-devhost`. Esse nome do host é a rota de seu app, `abc-devhost.mybluemix.net`
4. Selecione a linguagem e a estrutura. Alguns kits do iniciador podem estar disponíveis apenas em uma linguagem.
5. Selecione seu plano de precificação. Há uma opção grátis que pode ser usada para este tutorial.
6. Clique em **Criar**.

## Etapa 3. Incluir recursos (opcional)
{: #add-services}

É possível incluir recursos que aprimoram seu app com o poder cognitivo do Watson, incluir serviços móveis ou serviços de segurança. Para este tutorial, inclua um local para gerenciar seus dados.

1. Na janela de serviço do app, clique em **Incluir recurso**.
2. Selecione o tipo de serviço desejado. Por exemplo, selecione **Dados** > **Avançar** > **Cloudant** > **Avançar**.
3. Selecione seu plano de precificação. Há uma opção grátis que pode ser usada para este tutorial.
4. Clique em **Criar**.

## Etapa 4. Criar uma cadeia de ferramentas do DevOps
{: #add-toolchain}

A ativação de uma cadeia de ferramentas cria um ambiente de desenvolvimento baseado em equipe para seu app. Quando você cria uma cadeia de ferramentas, o serviço de app cria um repositório Git, no qual é possível visualizar o código-fonte, clonar seu app e criar e gerenciar problemas. Você também tem acesso a um ambiente de laboratório Git dedicado e a um pipeline de entrega contínua. Eles são customizados para a plataforma de implementação escolhida, seja Kubernetes ou Cloud Foundry.

A entrega contínua é ativada para alguns aplicativos. É possível ativar a entrega contínua para automatizar construções, testes e implementações por meio do Delivery Pipeline e do GitHub.

1. Na janela de serviço do app, clique em **Implementar na nuvem**.
2. Selecione um método de implementação. Configure seu método de implementação de acordo com as instruções para o método escolhido.

    * Implementar em um cluster do Kubernetes. Crie um cluster de hosts, chamados de nós do trabalhador, para implementar e gerenciar contêineres de aplicativos altamente disponíveis. É possível criar um cluster ou implementar em um cluster existente.

    * Implemente com o Cloud Foundry, no qual não é necessário gerenciar a infraestrutura subjacente.

## Etapa 5. Criando e executando o app localmente
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

6. Configure seus destinos de organização e espaço.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7.  Obtenha as credenciais.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Verifique se o Docker está executando e crie seu app em um contêiner de desenvolvimento local do diretório.

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

## Etapa 6. Implementar seu app
{: #deploy}

### Implementar usando uma cadeia de ferramentas

É possível implementar seu app no {{site.data.keyword.cloud_notm}} de várias maneiras, mas uma cadeia de ferramentas do DevOps é a melhor maneira de implementar apps de produção. Com uma cadeia de ferramentas do DevOps, é possível automatizar facilmente implementações para muitos ambientes e incluir rapidamente serviços de monitoramento, criação de log e alerta para ajudar a gerenciar seu app à medida que ele cresce.

Com uma cadeia de ferramentas configurada corretamente, um ciclo de construção-implementação se inicia automaticamente com cada mesclagem na ramificação Principal em seu repositório. Todas as cadeias de ferramentas criadas por meio de um painel do desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.

Também é possível implementar seu app manualmente por meio de sua cadeia de ferramentas DevOps:

1. Na janela Detalhes do app, clique em **Visualizar cadeia de ferramentas**.

2. Clique em **Delivery Pipeline**, no qual é possível iniciar construções, gerenciar a implementação e visualizar logs e o histórico.

### Implementar usando o {{site.data.keyword.dev_cli_short}}

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

## Etapa 7. Verificar se o app está em execução
{: #verify}

Após a implementação de seu app, o pipeline ou a linha de comandos do DevOps aponta para a URL de seu app, por exemplo, `abc-devhost.mybluemix.net`. Acesse essa URL em seu navegador.
