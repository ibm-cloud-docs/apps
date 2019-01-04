---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Implementando o seu próprio código em um cluster do Kubernetes
{: #tutorial}

Aprenda a criar um app no {{site.data.keyword.cloud}} usando o repositório de app existente. É possível
conectar a cadeia de ferramentas do DevOps existente ou criar uma e entregar continuamente um app para um contêiner
seguro em um cluster do Kubernetes. Esse tutorial ajuda a configurar um pipeline do DevOps de integração contínua para
que a mudança seja construída e propagada automaticamente por todo o caminho até o app implementado no cluster do
Kubernetes.
{: shortdesc}

Quando você já tem um repositório de código-fonte com um código base para um aplicativo de back-end ativo, o {{site.data.keyword.cloud_notm}} ajuda a organizar esse ativo em uma visualização agregada de
todos os ativos que compõem a amplitude de seu produto inteiro. O {{site.data.keyword.cloud_notm}} ajuda você a começar a usar um fluxo de trabalho do DevOps escalável quando o recurso de cadeia de ferramentas do
DevOps é usado. Esse tutorial ajuda o desenvolvedor experiente ou o engenheiro do DevOps a adquirir e configurar um cluster do {{site.data.keyword.cloud_notm}} Kubernetes de destino e configurar e executar uma cadeia de ferramentas do
DevOps, tudo sob a orientação das melhores práticas de nuvem.

Um _cluster_ é um conjunto de recursos, nós de trabalhador, redes e dispositivos de armazenamento
que mantêm os apps altamente disponíveis. Depois de criar o cluster, é possível implementar os apps em contêineres.
{: tip}

## Antes de começar
{: #prereqs}

* Siga as etapas para [Criando apps por meio de seu próprio
repositório de código](/docs/apps/tutorials/tutorial_byoc.html) para criar um app.
* No painel do [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}){: new_window}, clique no ícone **Menu** ![Ícone de menu](../../icons/icon_hamburger.svg) e selecione **Contêineres** para [configurar um cluster de Kubernetes](/docs/containers/container_index.html).
* Para confirmar se o app é executado no Docker, execute os comandos a seguir:
  - `git clone git@github.com:yourrepo/spring-boot-hello-world.git`
  - `cd spring-boot-hello-world`
  - `mvn clean install  
  `
  - `docker build`
  - `docker run -e "SECRET=no" -e "NOT_SECRET=yes" -p 80:8080 {docker_image_name}`
  
* Em seguida, visite a sua URL, como `http://localhost/springboothelloworld/sayhello`.   
Pressione `Ctrl + C` para parar a execução do Docker.

## Opcional. Incluindo recursos no app
{: #add_resources}

Inclua um recurso de serviço no aplicativo e o {{site.data.keyword.cloud_notm}} cria o serviço para você. O processo de fornecimento pode ser diferente para tipos de serviços diferentes. Por exemplo, um serviço de banco de dados cria um banco de dados
e um serviço de notificação push para aplicativos móveis gera
informações de configuração. O {{site.data.keyword.cloud_notm}} fornece os recursos de um
serviço para o aplicativo usando uma instância de serviço. Uma instância de serviço pode ser compartilhada entre os aplicativos da web.

Esse processo fornece uma instância de serviço, cria uma chave de recurso (credenciais) e liga-a ao app. Para
obter mais informações, consulte [Incluindo um serviço no app](/docs/apps/reqnsi.html).

### Copiando as credenciais de serviço para o ambiente

Depois de incluir um recurso de serviço no app, observe que as credenciais para esse serviço são exibidas na
caixa **Credenciais**. Deve-se copiar as credenciais para o ambiente de implementação.

Para obter mais informações sobre a cópia de credenciais para o ambiente, consulte
[Incluindo credenciais no ambiente do Kubernetes](/docs/apps/creds_kube.html).


## Preparando o app para implementação usando uma cadeia de ferramentas do DevOps
{: #connect_toolchain}

Nessa etapa, você anexa uma cadeia de ferramentas do DevOps ao aplicativo e a configura para que seja implementada
em um cluster do Kubernetes hospedado no serviço {{site.data.keyword.cloud_notm}} Kubernetes.

A cadeia de ferramentas do DevOps é flexível o suficiente para permitir a execução gerenciada de estágios
arbitrários de execução de shell script. Em outras palavras, é possível fazer quase tudo com uma cadeia de
ferramentas do DevOps. O escopo dessa seção se concentra na implementação do app em um cluster do Kubernetes,
enquanto mantém em mente a "prova de futuro" para o DevOps escalado e as melhores práticas de nuvem.

Estabelecer um link entre o app, a cadeia de ferramentas e o repositório é uma etapa para a organização dos
ativos do produto. Isso também ajuda a agregar uma visualização do repositório de origem com o fluxo de trabalho do
DevOps, com as instâncias de app em execução e com os serviços dependentes em todos os destinos de implementação.

Na página Conectar a cadeia de ferramentas, você tem algumas opções:

* Conecte o app a uma cadeia de ferramentas existente.
* Conecte o app a uma cadeia de ferramentas existente que não contenha o seu repositório. Então, conecte
a cadeia de ferramentas ao seu repositório posteriormente.
* Conecte o app a uma nova cadeia de ferramentas.

### Conectar o app a uma cadeia de ferramentas existente
{: #connect_toolchain_repo}

Se você tiver uma ou mais cadeias de ferramentas do DevOps já conectadas ao repositório Git
especificado durante a criação do app, essas cadeias de ferramentas serão exibidas na tabela **Com repositório**. A cadeia de ferramentas deve ser configurada para recuperar a origem por meio do mesmo repositório que você
definiu no app. É mais provável que você queira selecionar uma dessas cadeias de ferramentas para conectar ao app.

### Conecte o app a uma cadeia de ferramentas existente que não contenha o seu repositório
{: #connect_toolchain_notrepo}

Se você tiver uma ou mais cadeias de ferramentas do DevOps associadas à sua conta, mas não conectadas ao
repositório Git especificado durante a criação do app, essas cadeias de ferramentas serão exibidas na
tabela intitulada **Sem o seu repositório**. É possível selecionar uma dessas cadeias de ferramentas e
conectá-la ao app, mas deve-se também incluir manualmente o seu repositório nessa cadeia de ferramentas.

Para obter mais informações sobre como incluir o repositório na cadeia de ferramentas, consulte:

 * [Configurando os
repositórios Git e o rastreamento de problema](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitbluemix)
 * [Configurando GitHub](/docs/services/ContinuousDelivery/toolchains_integrations.html#github)
 * [Configurando o GitLab](/docs/services/ContinuousDelivery/toolchains_integrations.html#gitlab)


### Conectar o app a uma nova cadeia de ferramentas
{: #create_toolchain}

Você tem essas opções para conectar o app a uma nova cadeia de ferramentas:
* Se você não desejar criar uma cadeia de ferramentas do DevOps do zero, será possível ativar o código
existente para a nuvem usando o comando [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable). 
O comando gera um modelo de cadeia de ferramentas do DevOps que você verifica no repositório. Em seguida, use esse
modelo como o conjunto de instrução para o que a cadeia de ferramentas do DevOps cria. Para obter mais informações,
consulte a [documentação da CLI](/docs/apps/create-deploy-cli.html#byoc).
* Crie uma cadeia de ferramentas do DevOps do zero dentro do console. Se você deseja controlar totalmente a
criação da cadeia de ferramentas do DevOps sem nenhuma mudança no repositório de código, crie a cadeia de
ferramentas do zero. Para obter mais informações, consulte [Criando uma cadeia
de ferramentas do DevOps do zero](#create_toolchain_scratch).

#### Criando uma cadeia de ferramentas do DevOps do zero
{: #create_toolchain_scratch}

Se você deseja criar uma cadeia de ferramentas do zero e conectá-la ao app, conclua estas etapas. Crie também
todas as integrações para construir o app e implementá-lo no cluster do Kubernetes. O recurso de cadeia de ferramentas
do DevOps oferece modelos, mas essas etapas mostram como configurar uma cadeia de ferramentas do DevOps do zero.

Ao escolher criar uma cadeia de ferramentas por meio do novo app, a página
[Criar uma cadeia de ferramentas](https://{DomainName}/devops/create) no
[Painel do DevOps](https://{DomainName}/devops/) é aberta em uma nova guia no navegador. Depois de
criar e configurar a cadeia de ferramentas nessa guia, deve-se voltar para a página **Conectar a uma cadeia
de ferramentas** no app e atualizar a página.
{:tip}

1. Na página **Criar uma cadeia de ferramentas**, clique no modelo **Construir
sua própria cadeia de ferramentas**.
2. Na página **Construir sua própria cadeia de ferramentas**, insira um nome para a
cadeia de ferramentas, selecione uma região e um grupo de recursos (padrão) e clique em **Criar**.

Uma cadeia de ferramentas vazia sem ferramentas ou integrações pré-configuradas é criada. Continue a configurar e
testar a nova cadeia de ferramentas concluindo as etapas restantes.

## Incluindo uma integração do GitHub

É possível configurar a cadeia de ferramentas do DevOps com a integração do GitHub usando as etapas a seguir:

1. No modelo de cadeia de ferramentas do DevOps, clique em **Incluir uma ferramenta**.
2. Selecione **GitHub** (se o repositório estiver realmente no GitHub público ou no
Enterprise GitHub).
3. Na página **Configurar a integração** para o GitHub, conclua estas etapas:
  * Selecione (ou insira) a URL do **Servidor GitHub**.
  * Se você vir uma mensagem "Desautorizado no GitHub", clique em **Autorizar**. Em seguida,
na página **Autorizar cadeias de ferramentas do IBM Cloud**, clique em **Autorizar IBM Cloud**. Em
seguida, insira a senha do GitHub.
  * Na página **Configurar a integração**, selecione **Existente** para o
**Tipo de repositório** para que a cadeia de ferramentas do DevOps configure o repositório
com um webhook e _não_ faça nenhuma bifurcação ou cópia do repositório.
  * Insira a **URL do repositório**. Por exemplo, `https://github.com/yourrepo/spring-boot-hello-world`).
  * Aguarde alguns instantes e você pode ser solicitado a autorizar o GitHub a conceder permissão à cadeia de
ferramentas do DevOps para usar a API de REST do GitHub para configurar o repositório com os webhooks necessários
para acionar a cadeia de ferramentas.
  * Clique em
**Criar integração**.

Você configurou essa cadeia de ferramentas do DevOps com uma integração para o repositório GitHub. Fazer isso
permite que a cadeia de ferramentas configure um webhook no repositório para que as solicitações pull e os
pushes de código nesse repositório acionem um POST para a cadeia de ferramentas. É possível consultar as configurações do
repositório para ver o novo webhook.

## Incluindo um pipeline de entrega para construir, testar e implementar o app

O pipeline de entrega é onde o trabalho acontece.

1. Clique em **Incluir uma ferramenta**.
2. Selecione **Pipeline de entrega**.
3. Na página **Configurar a integração** para o pipeline de entrega, conclua estas etapas:
 * Insira "Integração contínua" para o nome do pipeline.
 * Clique em
**Criar integração**.

Você criou um pipeline de entrega vazio. Em seguida, defina os estágios de pipeline para direcionar a entrada
(o conteúdo do repositório GitHub) para o seu destino. Como esse tutorial supõe que você tem um repositório GitHub que
produz uma imagem do Docker ativa e está destinando um cluster do IBM Containers Kubernetes, crie estágios de
pipeline com entradas, shell scripts e saídas que atinjam esse objetivo.

### Configurando o estágio de pipeline "Construir e publicar"

1. Clique no pipeline de entrega que você criou.
2. Na página Pipeline de entrega, clique em **Incluir um estágio**.
3. Na guia **Entrada** da página **Configuração de estágio**,
preencha os campos da seguinte forma:
  * Para o nome do estágio, digite **Construir e publicar imagem do Docker**.
  * **Tipo de entrada**: selecione **Repositório Git**.
  * **Repositório Git**: selecione o repositório GitHub.
  * **Ramificação**: selecione a ramificação que você usa para a integração contínua.
4. Clique na guia **Tarefas** e preencha os campos da seguinte forma:
  * Clique no ícone **Incluir tarefa '+'** e selecione **Construir** para o tipo de tarefa.
  * Insira um nome, tal como **Construir e publicar**.
  * **Tipo de construtor**: selecione **Registro de contêiner**.
  * **Região do IBM Cloud**: selecione a região em que o cluster do Kubernetes está
localizado.
  * **Chave de API**: Selecione **Inserir uma chave de API existente**. Se
você não tiver uma chave ou não souber a chave de API, será possível
[obter uma chave de API](https://{DomainName}/iam/#/apikeys) abrindo uma janela separada do navegador e
navegando para **Gerenciar** > **Segurança** > **Chaves de API da
plataforma**. Certifique-se de manter essa chave em um local seguro.
  * **Nome da conta**: esse campo é automaticamente preenchido quando você insere uma
chave de API.
  * **Namespace do registro do contêiner**: insira o [namespace do registro do contêiner](https://{DomainName}/containers-kubernetes/registry/namespaces) (É possível localizá-lo clicando no ícone **Menu** ![Ícone de menu](../../icons/icon_hamburger.svg) e selecionando **Contêineres** > **Registro** > **Namespaces**.)
  * **Nome da imagem do Docker**: Insira **contínuo** porque esse
estágio de construção de pipeline é para a construção contínua da ramificação de integração contínua do repositório.
  * **Construir script**: observe o shell script. Ele não tem as instruções de construção
do app para o _seu_ repositório. É necessário incluir uma linha ou mais após a primeira linha `#!/bin/bash`. 
Por exemplo, para um repositório que é construído usando maven, você pode incluir algumas linhas semelhantes ao exemplo
a seguir:

    ```bash
    export JAVA_HOME=/opt/IBM/java8
    # the MAVEN_OPTS, -B flag, and stopping the phases just prior to 'install' are recommended:
    export MAVEN_OPTS="-Dorg.slf4j.simpleLogger.log.org.apache.maven.cli.transfer.Slf4jMavenTransferListener=warn"
    mvn -B clean verify
    ```
    {: codeblock}
5. Clique **Salvar.** Agora, o estágio de pipeline "Construir e publicar" aparece na cadeia de ferramentas.

### Testando o estágio de pipeline "Construir e publicar"

Clique no ícone **Reproduzir** até que a compilação seja bem-sucedida. Você sabe que ela está funcional quando o estágio fica verde e a saída do script confirma as suas expectativas. O objetivo nesse estágio é publicar uma imagem do Docker em seu registro de imagem. Se o script não exibir o suficiente para a sua confiança, será possível ver o registro de imagem para confirmar a publicação clicando no ícone **Menu** ![Ícone de menu](../../icons/icon_hamburger.svg) e, então, selecionar **Contêineres** > **Registro** > **Repositórios privados**. Em
seguida, confirme se um repositório que termina com o nome `/continuous` é listado. (Lembre-se, esse
era o nome da imagem.)

### Configurando o estágio de pipeline "Implementar no cluster"

Até agora, você publicou uma imagem do Docker para o registro de imagem do Docker privado. Agora, é hora de criar
um estágio que implemente essa imagem para o cluster do Kubernetes.

1. Na página Pipeline de entrega, clique em **Incluir um estágio**.
2. Na guia **Entrada** da página **Configuração de estágio**, preencha os campos da seguinte forma:
  * **Nome**: digite **Implementar**.
  * **Tipo de entrada**: selecione **Artefatos de construção**.
  * **Estágio**: selecione **Construir e publicar imagem do Docker**.
  * **Tarefa**: selecione **Construir e publicar**.
  * **Acionador de estágio**: como esse é o pipeline de integração contínua, selecione o padrão **Executar tarefas e, em seguida, o estágio anterior será concluído**.
3. Clique na guia **Tarefas** e preencha os campos da seguinte forma:
  * Clique no ícone **Incluir tarefa '+'** e selecione **Implementar** para o tipo de tarefa.
  * Insira um nome, como **Implementar no cluster de integração contínua**.
  * **Tipo de implementador**: selecione **Kubernetes**.
  * **Região do IBM Cloud**: selecione a região em que o cluster do Kubernetes está localizado.
  * **Chave de API**: selecione **Inserir uma chave de API existente**. Se
você não tiver uma chave ou não souber a chave de API, será possível
[obter uma chave de API](https://{DomainName}/iam/#/apikeys) abrindo uma janela separada do navegador e
navegando para **Gerenciar** > **Segurança** > **Chaves de API da
plataforma**. Certifique-se de manter essa chave em um local seguro.
  * Aceite as configurações padrão restantes.
4. Clique **Salvar.** Agora, o estágio de pipeline "Implementar" aparece na cadeia de ferramentas.

### Testando o estágio de pipeline "Implementar no cluster"

Clique no ícone **Reproduzir** até que a compilação seja bem-sucedida. Você sabe que ela
está funcional quando o estágio fica verde e a saída do script confirma as suas expectativas. É possível visualizar os logs para o
estágio. Perto do final dos logs, localize um link clicável para o app em execução. No entanto, somente _você_ conhece a raiz de contexto e o caminho do seu app. Anexe
o caminho correto para confirmar se que está executado.
