---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# Criando um app com um padrão de código
{: #tutorial-codepattern}

É possível usar um padrão de código para criar rapidamente seu app e implementá-lo no {{site.data.keyword.cloud}}. É possível visualizar o código no GitHub ou criar e construir um app no {{site.data.keyword.cloud_notm}}, no qual é possível usar uma cadeia de ferramentas do DevOps para implementar automaticamente seu app.
{: shortdesc}

## Etapa 1. Criar um app
{: #create-codepattern}

1. Acesse o [IBM Developer ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/patterns/){:new_window} e selecione o padrão de código que você deseja. Por exemplo, é possível selecionar o padrão de código [Construir um app da web do MEAN ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/patterns/build-a-mean-web-app/){:new_window}.

2. Leia a descrição do padrão de código e visualize o repositório GitHub e o arquivo `README.md`. Para visualizar o repositório, clique em **Obter o código**, que abre o repositório GitHub para o padrão de código.

3. Inicie criando um app usando uma das opções a seguir. Qualquer uma das opções abre a página **Criar app** para o padrão de código.
    * Na página de padrão de código, clique no link para construir um app no {{site.data.keyword.cloud_notm}}. 
    * No arquivo `README.md` no repositório GitHub, clique no link para usar um kit do iniciador para criar o app. 

4. Na página **Criar app**, nomeie o seu app, selecione um grupo de recursos, opcionalmente, forneça identificações e clique em **Criar**. Para obter mais informações sobre identificações, consulte [Trabalhando com identificações](/docs/resources/tagging_resources.html#tag).

  Para voltar para o padrão de código, clique em **Visualizar padrão de código**. Verifique o arquivo `README.md` no repositório para descobrir se é necessário executar mais ações para que o seu app esteja ativo e em execução.
  {: tip}

## Etapa 2. Incluindo recursos
{: #resources-codepattern}

É possível incluir recursos que aprimoram seu app com o poder cognitivo do Watson, incluir serviços móveis ou serviços de segurança. Esse processo fornece uma instância de serviço, cria uma chave de recursos (credenciais) e liga-a ao seu app. Para este tutorial, inclua um local para gerenciar seus dados.

1. Na página **Detalhes do app**, clique em **Incluir recurso**.
2. Selecione o tipo de recurso que você deseja. 
3. Selecione seu plano de precificação. Uma opção Lite está disponível.
4. Clique em **Criar**.

## Etapa 3. Copiando credenciais de serviço para o seu ambiente

Após você incluir um recurso em seu app ou se algum serviço for necessário para o seu app, observe que as credenciais para esse serviço são exibidas na caixa **Credenciais**. Deve-se copiar manualmente as credenciais para o seu ambiente de implementação.

Para obter mais informações sobre como copiar credenciais para o seu ambiente, consulte [Visão geral de credenciais](/docs/apps/creds_overview.html).

## Etapa 4. Implementando no {{site.data.keyword.cloud_notm}}
{: #deploy-codepattern}

É possível implementar seu app no {{site.data.keyword.cloud_notm}} de várias maneiras, mas uma cadeia de ferramentas do DevOps é a melhor maneira de implementar apps de produção. Com uma cadeia de ferramentas do DevOps, é possível automatizar facilmente implementações para muitos ambientes e incluir rapidamente serviços de monitoramento, criação de log e alerta para ajudar a gerenciar seu app à medida que ele cresce.

A ativação de uma cadeia de ferramentas cria um ambiente de desenvolvimento baseado em equipe para seu app. Quando você cria uma cadeia de ferramentas, o serviço de app cria um repositório Git, no qual é possível visualizar o código-fonte, clonar seu app e criar e gerenciar problemas. Você também tem acesso a um ambiente de laboratório Git dedicado e a um pipeline de entrega contínua. Eles serão customizados para o ambiente de implementação que você escolher, quer ele seja [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) ou [Virtual Server (VSI)](/docs/vsi/vsi_index.html).}

1. Na página **Detalhes do app**, clique em **Implementar na nuvem**.
2. Selecione um método de implementação e clique em **Criar**. O {{site.data.keyword.cloud_notm}} automaticamente cria uma cadeia de ferramentas aberta e completa com um repositório Git e um pipeline de entrega contínua.
3. Abra o estágio de pipeline de sua nova cadeia de ferramentas para visualizar o processo de construção e implementação para que seja possível visualizar o seu novo app em minutos.

Para obter mais informações sobre métodos de implementação, construções e pipelines, consulte [Construindo e implementando](/docs/services/ContinuousDelivery/pipeline_build_deploy.html#deliverypipeline_build_deploy).
