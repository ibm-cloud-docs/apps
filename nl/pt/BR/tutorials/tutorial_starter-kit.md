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

# Criando um app com um kit do iniciador
{: #tutorial-starterkit}

É possível usar um kit do iniciador para iniciar rapidamente o seu app e prepará-lo para desenvolvimento futuro. Escolha um kit do iniciador e uma linguagem de programação, crie um app e, em seguida, configure uma cadeia de ferramentas do DevOps para implementar automaticamente seu app. Também é possível fazer download do código para inspeção imediata.
{: shortdesc}

É possível criar um app de uma seleção de kits do iniciador, incluindo um espaço em branco, se você
mesmo deseja customizar as opções de construção. De qualquer maneira, uma cadeia de ferramentas do DevOps é criada
automaticamente para a implementação do app. Também é possível fazer download do código para inspeção imediata.

Os kits do iniciador estão disponíveis em várias categorias, incluindo:
* [Watson ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/developer/watson/dashboard){:new_window}
* [Apple ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/developer/appledevelopment/dashboard){:new_window}
* [Móvel![ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/developer/mobile/dashboard){:new_window}
* [Aplicativo da web ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/developer/appservice/dashboard){:new_window}
* [Segurança ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/developer/security/dashboard){:new_window}
* [Finanças ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/developer/finance/dashboard){:new_window}

## Etapa 1. Criar um app
{: #create-starterkit}

1. No painel do [{{site.data.keyword.cloud}}](https://{DomainName}), clique no ícone
**Menu** ![Ícone de menu](../../icons/icon_hamburger.svg) > **Apps
da web**.

2. Clique em **Introdução** na seção **Iniciar na web**.

3. Selecione um kit do iniciador de sua escolha, leia os detalhes e clique em **Criar**.
    
    Para ver o que está incluído no kit do iniciador, expanda o bloco no painel
[Kits do iniciador do App Service
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}/developer/appservice/starter-kits){:new_window}. A opção do kit do iniciador "Criar app" pode ser usada como um app iniciador em branco e customizado adicionalmente para corresponder às suas necessidades.
    {: tip}

4. Nomeie o seu app, selecione um grupo de recursos, opcionalmente, forneça identificações, selecione a sua linguagem e clique em **Criar**.
    
    Ótimo início! Você acabou de criar um app.

Para inspecionar seu código, clique em **Fazer download do código** na página de detalhes do app. Verifique o arquivo `README.md` no arquivo compactado transferido por download para descobrir se é necessário executar mais ações para colocar o app Starter em funcionamento.
{: tip}

Para obter mais informações, consulte os seguintes tópicos:
 * [Criando um app básico da web com um kit do iniciador](/docs/apps/tutorials/tutorial_web.html#tutorial-webapp)
 * [Trabalhando com tags](/docs/resources/tagging_resources.html#tag)

## Etapa 2. Incluindo recursos
{: #resources-starterkit}

É possível incluir recursos que aprimoram seu app com o poder cognitivo do Watson, incluir serviços móveis ou serviços de segurança. Para este tutorial, inclua um local para gerenciar seus dados.

1. Na janela de serviço do app, clique em **Incluir recurso**.
2. Selecione o tipo de serviço desejado. Por exemplo, selecione **Dados** > **Avançar** > **Cloudant** > **Avançar**.
3. Selecione seu plano de precificação. Há uma opção grátis que pode ser usada para este tutorial.
4. Clique em **Criar**.

## Etapa 3. Implementar no {{site.data.keyword.cloud_notm}}
{: #deploy-starterkit}

Clique em **Implementar na nuvem** na página Detalhes do app, selecione um ambiente de implementação e clique em **Criar**. O {{site.data.keyword.cloud_notm}} automaticamente cria uma cadeia de ferramentas aberta e completa com um repositório Git e um pipeline de entrega contínua.

A ativação de uma cadeia de ferramentas cria um ambiente de desenvolvimento baseado em equipe para seu app. Quando você cria uma cadeia de ferramentas, o serviço de app cria um repositório Git, no qual é possível visualizar o código-fonte, clonar seu app e criar e gerenciar problemas. Você também tem acesso a um ambiente de laboratório Git dedicado e a um pipeline de entrega contínua. Eles serão customizados para o ambiente de implementação que você escolher, quer ele seja [Kubernetes](/docs/containers/container_index.html#container_index), [Cloud Foundry](/docs/cloud-foundry-public/about-cf.html#about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html#about) ou [Virtual Server (VSI)](/docs/vsi/vsi_index.html).

Após você selecionar o seu ambiente de implementação, abra o componente de pipeline de sua nova cadeia de ferramentas para iniciar o processo de construção e implementação inicial para que você possa ver o seu novo app em minutos.

Todas as cadeias de ferramentas criadas por meio de um Painel do desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.
{: note}

Para implementar o app com a linha de comandos, use `ibmcloud dev deploy`. Para obter mais informações, consulte [Criando e implementando aplicativos usando a CLI](/docs/apps/create-deploy-cli.html#create-deploy-app-cli).
