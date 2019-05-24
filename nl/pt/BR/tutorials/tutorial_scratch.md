---

copyright:
  years: 2016, 2019
lastupdated: "2019-05-10"

keywords: scratch, developer tools, custom app, app tutorial, verify app running, run app local

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Criando um app do zero
{: #tutorial-scratch}

É possível criar um aplicativo customizado do zero usando serviços e um tempo de execução. 
{: shortdesc}

## Antes de começar
{: #prereqs-scratch}

* Instale o [{{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli), que inclui o Docker. 
* Crie uma conta do Docker, execute o app do Docker e conecte-se. O Docker deve estar em execução para que os comandos de construção funcionem.
* Se você planeja implementar seu app no {{site.data.keyword.cfee_full}}, deve-se [preparar sua conta do {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Criando o app
{: #create-scratch}

1. No [painel do {{site.data.keyword.cloud_notm}}![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}), clique em **Criar um app** no widget Apps.

  Também é possível criar um app customizado por meio da página [Kits do iniciador ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/developer/appservice/starter-kits/) no {{site.data.keyword.dev_console}}.
  {: tip}

2. Insira um nome para o seu app. Para este tutorial, digite `CustomProject`.
3. É possível, opcionalmente, fornecer identificações para classificar o seu app. Para obter mais informações, consulte [Trabalhando com tags](/docs/resources?topic=resources-tag).
4. Selecione a linguagem e a estrutura. Alguns kits do iniciador podem estar disponíveis apenas em uma linguagem.
5. Selecione seu plano de precificação. É possível usar a opção grátis para esse tutorial.
6. Clique em **Criar**.

## Incluindo serviços (opcional)
{: #resources-scratch}

É possível incluir serviços que aprimoram seu app com o poder cognitivo do Watson, incluir serviços remotos ou serviços de segurança. Para este tutorial, é possível incluir um local para gerenciar os seus dados.

1. Na página **Detalhes do app**, clique em **Incluir serviço**.
2. Selecione o tipo de serviço desejado. Por exemplo, selecione **Dados** > **Avançar** > **Cloudant** > **Avançar**.
3. Selecione seu plano de precificação. É possível usar a opção grátis para esse tutorial.
4. Clique em **Criar**.

## Construindo e executando o app localmente
{: #build-run-scratch}

Também é possível construir o app localmente para teste antes de implementá-lo na nuvem.

1. Na página **Detalhes do app**, clique em **Fazer download do código** ou **Clonar seu repositório** para trabalhar com seu código localmente.
2. Importe o app para seu ambiente de desenvolvimento integrado.
3. Modifique o código.
4. Configure a [Autenticação Git](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) incluindo um token de acesso pessoal.
5. Efetue login na interface da linha de comandos (CLI) do {{site.data.keyword.cloud_notm}}. Se a sua organização usar logins federados, use a opção `-sso`. Por exemplo:

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Execute o comando a seguir para configurar os seus destinos de organização e espaço.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7. Execute o comando a seguir para recuperar as credenciais.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Certifique-se de que o Docker esteja em execução e execute o comando a seguir para construir o seu app em um contêiner de desenvolvimento local por meio do diretório.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Execute o comando a seguir para executar o seu app em um contêiner de desenvolvimento local.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10. Acesse `http://localhost:3000` em seu navegador. Seu número de porta pode ser diferente, dependendo do tempo de execução escolhido.

## Implementando seu app
{: #deploy-scratch}

Quando você seleciona um destino de implementação, uma cadeia de ferramentas do DevOps é criada automaticamente para o seu app. A cadeia de ferramentas inclui um Delivery Pipeline que indica o status de implementação de seu app. O novo app gerado é enviado por push para um repositório GitLab que faz parte da cadeia de ferramentas.

A ativação de uma cadeia de ferramentas do DevOps cria um ambiente de desenvolvimento baseado em equipe para seu app. Quando você cria uma cadeia de ferramentas, o serviço de app cria um repositório Git, no qual é possível visualizar o código-fonte, clonar seu app e criar e gerenciar problemas. Você também tem acesso a um ambiente GitLab dedicado e a um pipeline de entrega contínua. Eles são customizados para o destino de implementação selecionado, seja o [Kubernetes](/docs/containers?topic=containers-getting-started), o [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), o [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) ou o [servidor virtual (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Todas as cadeias de ferramentas criadas por meio de um Painel do desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.
{: note}

Para selecionar o destino de implementação e configurar a entrega contínua, conclua estas etapas:

1. Na página Detalhes do app, clique em **Configurar entrega contínua**.
2. Selecione um destino de implementação. Configure o destino de implementação de acordo com as instruções para o destino selecionado:
  * **Implementar no [IBM Kubernetes Service](/docs/containers?topic=containers-app)**. Essa opção cria um cluster de hosts, chamados de nós do trabalhador, para implementar e gerenciar contêineres de aplicativo altamente disponíveis. É possível criar um cluster ou implementar em um cluster existente.
  * **Implemente no Cloud Foundry**. Essa opção implementa o seu app nativo de nuvem sem você precisar gerenciar a infraestrutura subjacente. Se a sua conta tiver acesso ao {{site.data.keyword.cfee_full_notm}}, será possível selecionar um tipo de implementador do **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** ou do **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**, que é possível usar para criar e gerenciar ambientes isolados para hospedar aplicativos do Cloud Foundry exclusivamente para a sua empresa.
  * **Implementar em um Servidor virtual**. Essa opção provisiona uma instância de servidor virtual, carrega uma imagem que inclui o seu app, cria uma cadeia de ferramentas do DevOps e inicia o primeiro ciclo de implementação para você.

Após a seleção e a configuração do destino de implementação, a página Detalhes do app indica que a entrega contínua está configurada. É possível visualizar o repositório que contém o código-fonte para seu app clicando em **Visualizar repositório**.

Para implementar o app com a linha de comandos, use `ibmcloud dev deploy`. Para obter mais informações, consulte [Criando e implementando aplicativos usando a CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli).

Para obter mais informações sobre como implementar seu app, consulte [Implementando apps](/docs/apps?topic=creating-apps-deploying-apps).

## Verificando se o seu app está em execução
{: #verify-scratch}

Após você implementar o seu app, o Delivery Pipeline ou a linha de comandos apontará a você a URL para o seu app.

1. Na cadeia de ferramentas do seu DevOps, clique em **Delivery Pipeline** e, em seguida, selecione **Implementar estágio**.
2. Clique em **Visualizar logs e histórico**.
3. No arquivo de log, localize a URL do aplicativo:

   No término do arquivo de log, procure a palavra `urls` ou `view`. Por exemplo, você pode ver uma linha no arquivo de log que é semelhante a `urls: my-app-devhost.mybluemix.net` ou `View the application health at: http://<ipaddress>:<port>/health`.

4. Acesse a URL em seu navegador. Se o app estiver em execução, uma mensagem que incluirá `Parabéns` ou `{"status":"UP"}` será exibida.

Se você estiver usando a linha de comandos, execute o comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para visualizar a URL de seu app. Em seguida, acesse a URL em seu navegador.

