---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, byoc, code repository, continuous delivery, cli, deploy

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note: .deprecated}

# Criando apps por meio do seu próprio repositório de código
{: #tutorial-byoc}

É possível criar um aplicativo no {{site.data.keyword.cloud}} usando o seu repositório de aplicativo existente. Basta
fornecer o link da web para o repositório durante a criação do aplicativo, continuar incluindo os recursos e,
em seguida, conectar uma cadeia de ferramentas do DevOps ao aplicativo para implementação.
{: shortdesc}

## Antes de começar
{: #prereqs-byoc}

Verifique se os pré-requisitos a seguir estão prontos:

 * Instale a [interface da linha de comandos (CLI) do {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).
 * Consulte [O que torna bom um app?](/docs/apps?topic=creating-apps-best-practice) para obter as melhores
práticas para criar apps.
 * Deve-se ter um repositório de código-fonte Git de qualquer um dos seguintes provedores: GitHub,
GitHub Enterprise, GitLab, BitBucket ou Rational.
 * Se você planeja implementar seu app no [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), deve-se [preparar sua conta do {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Etapa 1. Criar um app com um repositório existente
{: #create-byoc}

Para criar um app e conectá-lo ao repositório de origem, conclua estas etapas:

1. No [painel](https://{DomainName}){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo"), clique em **Criar um app** no bloco **Apps**.
2. Nomeie o seu app, selecione um grupo de recursos e, opcionalmente, forneça identificações para classificar o seu app. Para obter mais informações, consulte [Trabalhando com tags](/docs/resources?topic=resources-tag).
3. Selecione **Trazer seu próprio código** e forneça a URL para o seu repositório Git. O
app e a imagem do Docker devem estar localizados no mesmo repositório.
4. Clique em **Criar**. A página **Detalhes do app** é exibida.
5. Opcional. [Inclua serviços](/docs/apps?topic=creating-apps-add-resource) em seu app.
6. Opcional. Se você fornece identificações quando cria o app, é possível editá-las clicando no ícone **Editar** ![Ícone editar](../../icons/edit-tagging.svg) que está próximo às identificações exibidas.
7. Opcional. Visualize o repositório clicando em **Visualizar repositório.**

## Etapa 2. Implementar seu app
{: #toolchain-byoc}

Estabelecer um link entre o app, a cadeia de ferramentas e o repositório é uma etapa para a organização dos
ativos do produto. Isso também ajuda a agregar uma visualização da origem com o fluxo de trabalho do DevOps, as
instâncias do app em execução e os serviços dependentes em todos os destinos de implementação. Para obter mais informações, consulte [Criando cadeias de ferramentas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

É possível configurar a entrega contínua para o seu app usando o console do {{site.data.keyword.cloud_notm}} ou a CLI.

### Utilizando o Console
{: #console-byoc-toolchain}

  1. Na página **Detalhes do app**, conecte seu app a uma cadeia de ferramentas do DevOps clicando em **Configurar entrega contínua**. A página **Implementar meu app** é exibida.
  2. Se você não tiver uma cadeia de ferramentas existente, clique em **Criar uma cadeia de ferramentas**. Depois de criar a cadeia de ferramentas, use as trilhas de navegação para retornar à página **Detalhes do app**, o que indica que a entrega contínua está configurada.
  3. Se você tiver uma cadeia de ferramentas existente, selecione-a e, em seguida, clique em **Ativar implementação**. A página **Detalhes do app** é exibida, indicando que a entrega contínua está configurada.

### Usando a CLI

É possível usar o comando `ibmcloud dev enable` para gerar um modelo de cadeia de ferramentas do DevOps que você verifica em seu repositório conforme a instrução definida para o que a cadeia de ferramentas do DevOps deve criar. 

  1. Na página **Detalhes do app**, clique em **Visualizar repositório** para trabalhar com seu código localmente.
  2. Execute o seguinte comando:
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

Para obter mais informações, consulte [Criando e implementando aplicativos usando a CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli).

