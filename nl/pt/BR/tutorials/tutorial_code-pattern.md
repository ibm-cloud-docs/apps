---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-13"

keywords: apps, code pattern, DevOps, toolchain, service credentials, create app code pattern, app pattern

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# Criando um app com um padrão de código
{: #tutorial-codepattern}

É possível usar um padrão de código para criar rapidamente seu aplicativo e implementá-lo no {{site.data.keyword.cloud}}. É possível visualizar o código no GitHub ou criar e construir um app no {{site.data.keyword.cloud_notm}}, no qual é possível usar uma cadeia de ferramentas do DevOps para implementar automaticamente seu app.
{: shortdesc}

## Etapa 1. Criar um app
{: #create-codepattern}

1. Acesse o [IBM Developer ](https://developer.ibm.com/patterns/){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo") e selecione o padrão de código que você deseja. Por exemplo, é possível selecionar o padrão de código [Construir um app da web do MEAN ](https://developer.ibm.com/patterns/build-a-mean-web-app/){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo").

2. Leia a descrição do padrão de código e visualize o repositório GitHub e o arquivo `README.md`. Para visualizar o repositório, clique em **Obter o código**, que abre o repositório GitHub para o padrão de código.

3. Inicie criando um app usando uma das opções a seguir. Qualquer uma das opções abre a página **Criar app** para o padrão de código.
    * Na página de padrão de código, clique no link para construir um app no {{site.data.keyword.cloud_notm}}. 
    * No arquivo `README.md` no repositório GitHub, clique no link para usar um kit do iniciador para criar o app. 

4. Na página **Criar app**, nomeie o seu app, selecione um grupo de recursos, opcionalmente, forneça identificações e clique em **Criar**. Para obter mais informações sobre identificações, consulte [Trabalhando com identificações](/docs/resources?topic=resources-tag).

  Para voltar para o padrão de código, clique em **Visualizar padrão de código**. Verifique o arquivo `README.md` no repositório para descobrir se é necessário executar mais ações para que o seu app esteja ativo e em execução.
  {: tip}

## Etapa 2. Incluindo Serviços
{: #resources-codepattern}

É possível incluir serviços que aprimoram seu app com o poder cognitivo do Watson, incluir serviços remotos ou serviços de segurança. Esse processo cria uma instância de serviço, cria uma chave de recurso (credenciais) e liga-o ao seu app. Para este tutorial, inclua um local para gerenciar seus dados.

1. Na página **Detalhes do app**, clique em **Incluir serviço**.
2. Selecione o tipo de serviço que você deseja. 
3. Selecione seu plano de precificação. Uma opção Lite está disponível.
4. Clique em **Criar**.

## Etapa 3. Copiando credenciais de serviço para o seu ambiente

Depois de incluir um serviço em seu app, ou se algum serviço for necessário para seu app, observe que as credenciais para esse serviço são exibidas na caixa **Credenciais**. Deve-se copiar manualmente as credenciais para o seu ambiente de implementação.

Para obter mais informações sobre como copiar credenciais para o seu ambiente, consulte [Visão geral de credenciais](/docs/apps?topic=creating-apps-credentials_overview#credentials_overview).

## Etapa 4. Implementando no {{site.data.keyword.cloud_notm}}
{: #deploy-codepattern}

Quando você seleciona um destino de implementação, uma cadeia de ferramentas do DevOps é criada automaticamente para o seu app. A cadeia de ferramentas inclui um Delivery Pipeline que indica o status de implementação de seu app. O novo app gerado é enviado por push para um repositório GitLab que faz parte da cadeia de ferramentas.

A ativação de uma cadeia de ferramentas do DevOps cria um ambiente de desenvolvimento baseado em equipe para seu app. Quando você cria uma cadeia de ferramentas, o serviço de app cria um repositório Git, no qual é possível visualizar o código-fonte, clonar seu app e criar e gerenciar problemas. Você também tem acesso a um ambiente GitLab dedicado e a um pipeline de entrega contínua. Eles são customizados para o destino de implementação selecionado, seja o [Kubernetes](/docs/containers?topic=containers-getting-started), o [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), o [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) ou o [servidor virtual (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Todas as cadeias de ferramentas criadas por meio de um Painel do desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.
{: note}

Para selecionar o destino de implementação e configurar a entrega contínua, conclua estas etapas:

1. Na página Detalhes do app, clique em **Configurar entrega contínua**.
2. Selecione um destino de implementação. Configure o destino de implementação de acordo com as instruções para o destino selecionado:
  * **Implementar no [IBM Kubernetes Service](/docs/containers?topic=containers-app)**. Essa opção cria um cluster de hosts, chamados nós do trabalhador, para implementar e gerenciar contêineres de app altamente disponíveis. É possível criar um cluster ou implementar em um cluster existente.
  * **Implemente no Cloud Foundry**. Essa opção implementa o seu app nativo de nuvem sem você precisar gerenciar a infraestrutura subjacente. Se a sua conta tiver acesso ao {{site.data.keyword.cfee_full_notm}}, será possível selecionar um tipo de implementador do **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** ou do **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**, que poderá ser usado para criar e gerenciar ambientes isolados para hospedar apps do Cloud Foundry exclusivamente para a sua empresa.
  * **Implementar em um Servidor virtual**. Essa opção provisiona uma instância de servidor virtual, carrega uma imagem que inclui o seu app, cria uma cadeia de ferramentas do DevOps e inicia o primeiro ciclo de implementação para você. Para obter mais informações, consulte [Implementando apps em um servidor virtual](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server).

    A implementação de VSI está disponível para alguns kits do iniciador. Para usar esse recurso, acesse o [painel do {{site.data.keyword.cloud_notm}}](https://{DomainName}) e clique em **Criar um app** no bloco **Apps**.
    {: note}

Após a seleção e a configuração do destino de implementação, a página Detalhes do app indica que a entrega contínua está configurada. É possível visualizar o repositório que contém o código-fonte para seu app clicando em **Visualizar repositório**.

Para obter mais informações sobre como implementar seu app, consulte [Implementando apps](/docs/apps?topic=creating-apps-deploying-apps).

Para obter mais informações sobre destinos de implementação, construções e pipelines, consulte [Construindo e implementando](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).
