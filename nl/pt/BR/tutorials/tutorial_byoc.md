---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

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

 * Instale a interface da linha de comandos (CLI) do [{{site.data.keyword.dev_cli_long}}](/docs/cli/index.html#overview).
 * Consulte [O que torna bom um app?](/docs/apps/best-practice.html#best-practice) para obter as melhores
práticas para criar apps.
 * Deve-se ter um repositório de código-fonte Git de qualquer um dos seguintes provedores: GitHub,
GitHub Enterprise, GitLab, BitBucket ou Rational.
 * Se você planeja implementar o seu app no [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry/index.html#about), deverá [preparar a sua conta do {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry/prepare-account.html#prepare).

## Etapa 1. Criar um app com um repositório existente
{: #create-byoc}

Para criar um app e conectá-lo ao repositório de origem, conclua estas etapas:

1. No painel do [ ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}){: new_window}, clique em **Criar um app** no bloco **Apps**.
2. Nomeie o seu app, selecione um grupo de recursos e, opcionalmente, forneça identificações para classificar o seu app. Para obter mais informações, consulte [Trabalhando com tags](/docs/resources/tagging_resources.html#tag).
3. Selecione **Trazer seu próprio código** e forneça a URL para o seu repositório Git. O
app e a imagem do Docker devem estar localizados no mesmo repositório.
4. Clique em **Criar**.

A página **Detalhes do app** é exibida. Nela, é possível:
* [Incluir recursos](/docs/apps/reqnsi.html#add-resource) (opcional).
* Se você fornece identificações quando cria o app, é possível editá-las clicando no ícone **Editar** ![Ícone editar](../../icons/edit-tagging.svg) que está próximo às identificações exibidas.
* Conectar o app a uma cadeia de ferramentas do DevOps clicando em **Conectar à cadeia de ferramentas do DevOps**. Se você ainda não tiver uma cadeia de ferramentas, a página **Conectar a cadeia de ferramentas do DevOps** será aberta. Clique em **Criar cadeia de ferramentas do DevOps**. Nesse ponto, a página
[Criar uma cadeia de ferramentas](https://{DomainName}/devops/create) no
[Painel do DevOps](https://{DomainName}/devops/) se abre em uma nova guia do navegador. Depois de criar
e configurar a cadeia de ferramentas nessa guia, deve-se voltar para a página **Conectar a uma cadeia de
ferramentas** no app e atualizar a página.
* Visualize o repositório clicando em **Visualizar repositório.**
* Saiba mais sobre as cadeias de ferramentas ou a experiência de criação do app clicando em qualquer um dos links
relacionados na página **Detalhes do app**.

## Etapa 2. Conectar o app a uma cadeia de ferramentas do DevOps
{: #toolchain-byoc}

Estabelecer um link entre o app, a cadeia de ferramentas e o repositório é uma etapa para a organização dos
ativos do produto. Isso também ajuda a agregar uma visualização da origem com o fluxo de trabalho do DevOps, as
instâncias do app em execução e os serviços dependentes em todos os destinos de implementação. Para obter mais informações, consulte [Criando cadeias de ferramentas](/docs/services/ContinuousDelivery/toolchains_working.html#toolchains_getting_started).

É possível conectar o app a uma cadeia de ferramentas do DevOps usando o console do {{site.data.keyword.cloud_notm}} ou a CLI.

### Utilizando o Console
{: #console-byoc-toolchain}

  1. Conecte o app a uma cadeia de ferramentas do DevOps clicando em **Conectar à cadeia de ferramentas do DevOps**. 
  
    Se você não tem uma cadeia de ferramentas existente, clique em **Criar cadeia de ferramentas do
DevOps**. 
    
  2. Após criar e configurar a cadeia de ferramentas, volte para a página Conectar uma cadeia de
ferramentas no app e atualize a página. 

### Usando a CLI

É possível usar o comando `ibmcloud dev enable` para gerar um modelo de Cadeia de ferramentas do DevOps que você registra em seu repositório como o conjunto de instruções para o que a Cadeia de ferramentas do DevOps deve criar. 

  1. Na janela App Service, clique em **Fazer download do código** ou **Clonar seu
repositório** para trabalhar com o código localmente.
  2. Execute o seguinte comando:
    
    ```
    ibmcloud dev enable`
    ```
   {: codeblock}

Para obter mais informações, consulte [Criando e implementando aplicativos usando a CLI](/docs/apps/create-deploy-cli.html#create-deploy-app-cli).

## Etapa 3. Implementar seu app
{: #deploy-byoc}

Depois de anexar uma cadeia de ferramentas do DevOps ao app, conclua as etapas a seguir para implementá-lo no {{site.data.keyword.cloud_notm}}: 

1. Na página Detalhes do app, clique em **Implementar na nuvem**.
2. Selecione um método de implementação. Configure o método de implementação de acordo com as instruções para o método escolhido:
  * **Implemente no [Kubernetes](/docs/apps/deploying/containers.html#containers)**. Essa opção cria um cluster de hosts, chamados de nós do trabalhador, para implementar e gerenciar contêineres de aplicativo altamente disponíveis. É possível criar um cluster ou implementar em um cluster existente.
  * **Implemente no Cloud Foundry**. Essa opção implementa o seu app nativo de nuvem sem você precisar gerenciar a infraestrutura subjacente. Se a sua conta tiver acesso ao {{site.data.keyword.cfee_full_notm}}, será possível selecionar um tipo de implementador do **[Public Cloud](/docs/cloud-foundry-public/about-cf.html#about-cf)** ou do **[Enterprise Environment](/docs/cloud-foundry-public/cfee.html#cfee)**, que é possível usar para criar e gerenciar ambientes isolados para hospedar aplicativos do Cloud Foundry exclusivamente para a sua empresa.
  * **Implemente em um [Servidor virtual](/docs/apps/vsi-deploy.html#vsi-deploy)**. Essa opção provisiona uma instância de servidor virtual, carrega uma imagem que inclui o seu app, cria uma cadeia de ferramentas do DevOps e inicia o primeiro ciclo de implementação para você.


