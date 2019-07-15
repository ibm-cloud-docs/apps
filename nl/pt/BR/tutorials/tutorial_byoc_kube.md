---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-05"

keywords: apps, deploy, deploy to kubernetes, cluster, delivery pipeline, toolchain, kube, deployment, custom code, kubernetes

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Implementando o seu próprio código em um cluster do Kubernetes
{: #tutorial-byoc-kube}

Saiba como criar um aplicativo no {{site.data.keyword.cloud}} usando seu repositório de app existente. É possível
conectar a cadeia de ferramentas do DevOps existente ou criar uma e entregar continuamente um app para um contêiner
seguro em um cluster do Kubernetes. Esse tutorial ajuda a configurar um pipeline do DevOps de integração contínua para
que a mudança seja construída e propagada automaticamente por todo o caminho até o app implementado no cluster do
Kubernetes.
{: shortdesc}

Quando você já tiver um repositório de código-fonte com um código base para um app de back-end funcional, o {{site.data.keyword.cloud_notm}} ajudará a organizar esse ativo em uma visualização agregada de todos os ativos que compõem a amplitude de seu produto inteiro. O {{site.data.keyword.cloud_notm}} ajuda você a começar a usar um fluxo de trabalho do DevOps escalável quando o recurso de cadeia de ferramentas do
DevOps é usado. Este tutorial ajuda o desenvolvedor experiente ou o engenheiro do DevOps a adquirir e configurar um {{site.data.keyword.containerlong}} de destino e configurar e executar uma cadeia de ferramentas do DevOps, tudo sob a orientação das melhores práticas de nuvem.

Um _cluster_ é um conjunto de recursos, nós de trabalhador, redes e dispositivos de armazenamento
que mantêm os apps altamente disponíveis. Depois de criar o cluster, é possível implementar os apps em contêineres.
{: tip}

## Antes de começar
{: #prereqs-byoc-kube}

* [Crie um app por meio de seu próprio repositório de código](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc).
* No [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo"), clique no ícone **Menu** ![ícone Menu](../../icons/icon_hamburger.svg) e selecione **Contêineres** para [configurar um cluster Kubernetes](/docs/containers?topic=containers-getting-started).
* Confirme se seu app é executado no Docker. Os comandos a seguir são exemplos, não necessariamente etapas que existem em seu app:
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install  
  `
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* Em seguida, acesse sua URL, como `http://localhost/springboothelloworld/sayhello`. Pressione Ctrl + C para parar a execução do Docker.

## Incluindo serviços em seu app (opcional)
{: #resources-byoc-kube}

Depois de criar seu app, é possível incluir um serviço em seu app por meio da página **Detalhes do app**. O {{site.data.keyword.cloud_notm}} cria a instância de serviço para você. O processo de fornecimento pode ser diferente para tipos de serviços diferentes. Por exemplo, um serviço de banco de dados cria um banco de dados e um serviço de notificação de push para apps móveis gera informações de configuração. O {{site.data.keyword.cloud_notm}} fornece os recursos de um serviço para o seu app usando uma instância de serviço. Uma instância de serviço pode ser compartilhada entre aplicativos da web.

Esse processo fornece uma instância de serviço, cria uma chave de recurso (credenciais) e liga-a ao app. Para
obter mais informações, consulte [Incluindo um serviço no app](/docs/apps?topic=creating-apps-add-resource).

Depois de incluir um serviço em seu app, deve-se [copiar as credenciais para o serviço em seu ambiente de implementação](/docs/apps?topic=creating-apps-credentials_overview).

## Preparando seu app para implementação
{: #deploy-byoc-kube}

Nesta etapa, você conecta uma cadeia de ferramentas do DevOps ao app e configura-a para ser implementada em um cluster Kubernetes que está hospedado no {{site.data.keyword.containerlong}}.

A cadeia de ferramentas do DevOps é flexível o suficiente para permitir a execução gerenciada de estágios
arbitrários de execução de shell script. Em outras palavras, é possível fazer quase tudo com uma cadeia de
ferramentas do DevOps. O escopo dessa seção se concentra na implementação do app em um cluster do Kubernetes,
enquanto mantém em mente a "prova de futuro" para o DevOps escalado e as melhores práticas de nuvem.

Estabelecer um link entre o app, a cadeia de ferramentas e o repositório é uma etapa para a organização dos
ativos do produto. Isso também ajuda a agregar uma visualização do repositório de origem com o fluxo de trabalho do
DevOps, com as instâncias de app em execução e com os serviços dependentes em todos os destinos de implementação.

### Conectando uma cadeia de ferramentas do DevOps existente

Se você já tiver uma cadeia de ferramentas do DevOps, conclua estas etapas:

1. Na página **Detalhes do app**, clique em **Configurar entrega contínua**. A página **Implementar meu app** é exibida.
2. Selecione a cadeia de ferramentas que você deseja conectar a seu app e clique em **Ativar implementação**. A página **Detalhes do app** é exibida, indicando que a entrega contínua está configurada.

Se você não desejar criar uma cadeia de ferramentas do DevOps do zero, será possível ativar o código existente para a nuvem usando o comando [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable). O comando gera um modelo de cadeia de ferramentas do DevOps que você verifica no repositório. Em seguida, use esse
modelo como o conjunto de instrução para o que a cadeia de ferramentas do DevOps cria. Para obter mais informações,
consulte a [documentação da CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli#byoc-cli).
{: tip}

### Criando uma cadeia de ferramentas do DevOps

Se você deseja controlar totalmente a
criação da cadeia de ferramentas do DevOps sem nenhuma mudança no repositório de código, crie a cadeia de
ferramentas do zero. Crie também
todas as integrações para construir o app e implementá-lo no cluster do Kubernetes. 

1. Na página **Detalhes do app**, clique em **Criar cadeia de ferramentas do DevOps.** A página **Criar uma cadeia de ferramentas** será exibida.
2. Selecione o modelo **Construir sua própria cadeia de ferramentas**.
3. Na página **Construir sua própria cadeia de ferramentas**, insira um nome para a
cadeia de ferramentas, selecione uma região e um grupo de recursos (padrão) e clique em **Criar**.
4. Use as trilhas de navegação na janela do navegador para retornar para a página **Detalhes do app**, que indica que a entrega contínua está configurada.
5. Na página **Detalhes do app**, clique em **Visualizar cadeia de ferramentas** para configurar sua nova cadeia de ferramentas do DevOps.

### Incluindo uma integração do GitHub
{: #github-byoc-kube}

Configure a cadeia de ferramentas do DevOps com uma integração para o seu repositório GitHub para a cadeia de ferramentas. Isso configura um webhook em seu repositório para que as solicitações pull e pushes de código nesse repositório enviem um POST para a cadeia de ferramentas.

1. Em seu modelo de cadeia de ferramentas do DevOps vazio, clique em **Incluir uma ferramenta**.
2. Selecione **GitHub** se o repositório estiver no GitHub público ou no GitHub corporativo.
3. Selecione ou insira a URL do servidor GitHub.
4. Uma mensagem `Unauthorized on GitHub` pode ser exibida. Nesse caso, clique em **Autorizar**. Em seguida, na página Autorizar cadeias de ferramentas do IBM Cloud, clique em **Autorizar o IBM Cloud** e insira sua senha do GitHub.
5. Na página Configurar a integração, selecione **Existente** para o tipo de repositório para que a cadeia de ferramentas do DevOps configure o repositório com um webhook e não faça nenhuma bifurcação ou cópia de seu repositório.
6. Insira a URL do repositório, por exemplo, `https://github.com/yourrepo/spring-boot-hello-world`.
7. Depois de alguns instantes, é possível que você seja solicitado a autorizar o GitHub a conceder permissão à cadeia de ferramentas do DevOps para que ela use a API de REST do GitHub para configurar seu repositório com os webhooks necessários para acionar a cadeia de ferramentas.
8.  Clique em
**Criar integração**.

É possível visualizar o novo webhook nas configurações do repositório.

### Incluindo um pipeline de entrega
{: #pipeline-byoc-kube}

1. Clique em **Incluir uma ferramenta**.
2. Selecione **Pipeline de entrega**.
3. Insira `Continuous Integration` para o nome do pipeline e clique em **Criar integração**.

### Configurando os estágios do pipeline
{: #pipelineconfig-byoc-kube}

Configure os estágios do pipeline para direcionarem sua entrada (os conteúdos do repositório GitHub) para o destino correto. Como este tutorial supõe que existe um repositório GitHub que produz uma imagem do Docker funcional e está destinando um {{site.data.keyword.containerlong}}, você cria estágios de pipeline com entradas, shell scripts e saídas que atingem esse objetivo.

1. Configure seu estágio de pipeline `build and publish`.
  1. Selecione o pipeline de entrega criado e clique em **Incluir um estágio**.
  2. Clique na guia **Entrada** e preencha os campos conforme a seguir:
    * Insira `build and publish Docker image` para o nome do estágio.
    * Selecione **Repositório Git** para o tipo de entrada.
    * Selecione seu repositório GitHub.
    * Selecione a ramificação usada para integração contínua.
  3.  Clique na guia **Tarefas** e, em seguida, clique em **Incluir Tarefa '+'** e preencha os campos conforme a seguir:
    * Selecione **Construir** para o tipo de tarefa.
    * Insira `build and publish` para o nome.
    * Selecione **Registro de contêiner** para o tipo de construtor.
    * Selecione a região na qual o cluster do Kubernetes está localizado.
    * Selecione **Inserir uma chave de API existente**. Se você não tiver uma chave de API, consulte [Criando uma chave de API](/docs/iam?topic=iam-userapikey#create_user_key). 
    * Insira o namespace de registro de contêiner, que é possível localizar clicando no ícone **Menu** ![Ícone Menu](../../icons/icon_hamburger.svg) e selecionando **Contêineres** > **Registro** > **Namespaces**.
    * Para o nome da imagem do Docker, insira `continuous` porque esse estágio de construção de pipeline é para a construção contínua da ramificação de integração contínua de seu repositório.
    * Edite o script de construção incluindo uma linha ou mais depois da primeira linha `#!/bin/bash`. Por exemplo, para um repositório que é construído usando maven, você pode incluir algumas linhas semelhantes ao exemplo
a seguir:

      ```bash
      export JAVA_HOME=/opt/IBM/java8
      # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
      export MAVEN_OPTS="-  
      Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
      mvn -B clean verify
      ```
      {: codeblock}
  4. Clique em **Salvar**. 
2. Teste seu estágio de pipeline `build and publish` clicando no ícone **Reproduzir** até que a construção seja bem-sucedida. Um estágio de verde indica que a construção foi bem-sucedida. 
3. Configure o estágio de pipeline `deploy to cluster` para implementar a imagem do Docker em seu cluster do Kubernetes. 
  1. Na página Pipeline de entrega, clique em **Incluir um estágio**.
  2. Clique na guia **Entrada** e preencha os campos conforme a seguir:
    * Insira `deploy to cluster` para o nome.
    * Selecione **Construir artefatos** para o tipo de entrada.
    * Selecione **Construir e publicar imagem do Docker** para o estágio.
    * Selecione **Construir e publicar** para a tarefa.
    * Como esse é seu pipeline de integração contínua, aceite a opção padrão para o acionador de estágio.
  3. Clique na guia **Tarefas** e, em seguida, clique em **Incluir Tarefa '+'** e preencha os campos conforme a seguir:
    * Insira `deploy to continuous integration cluster` para o nome.
    * Selecione **Kubernetes** para o tipo de implementador.
    * Selecione a região na qual o cluster do Kubernetes está localizado.
    * Insira sua chave de API existente. 
  4. Clique em **Salvar**.
4. Teste seu estágio de pipeline `deploy to cluster` clicando no ícone **Reproduzir** até que a construção seja bem-sucedida. Um estágio de verde indica que a construção foi bem-sucedida.

## Verificando se o seu app está em execução
{: #verify-byoc-kube}

O Delivery Pipeline ou a linha de comandos aponta você para a URL para seu app.

1. Na cadeia de ferramentas do seu DevOps, clique em **Delivery Pipeline** e, em seguida, selecione **Implementar estágio**.
2. Clique em **Visualizar logs e histórico**.
3. No arquivo de log, localize a URL do app. No término do arquivo de log, procure a palavra `urls` ou `view`. Por exemplo, você pode ver uma linha no arquivo de log que é semelhante a `urls: my-app-devhost.mybluemix.net` ou `View the application health at: http://<ipaddress>:<port>/health`.
4. Acesse a URL em seu navegador. Se o app estiver em execução, uma mensagem que incluirá `Parabéns` ou `{"status":"UP"}` será exibida.

Se você estiver usando a linha de comandos, execute o comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para abrir a página de um app implementado manualmente em seu navegador padrão.

## Informações relacionadas

 * [Criando cadeias de ferramentas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)
 * [Configurando os
repositórios Git e o rastreamento de problema](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#grit)
 * [Configurando GitHub](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#github)
 * [Configurando o GitLab](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-integrations#gitlab)
