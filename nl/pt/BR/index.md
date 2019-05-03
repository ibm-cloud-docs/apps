---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-15"

keywords: apps, create apps, add resources, deploy apps

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Tutorial Introdução
{: #tutorial-getting-started}

É possível construir aplicativos móveis e da web prontos para a empresa no {{site.data.keyword.cloud}} e aproveitar as extensões de nuvem que são hospedadas pelo {{site.data.keyword.cloud_notm}}. Você tem várias opções para iniciar. Crie um app com um kit do iniciador que gerencia o processo para você ou, se você souber o que deseja, comece do zero e construa o seu app com os recursos necessários ou use o seu repositório existente e traga o seu próprio código.
{: shortdesc}

## Antes de começar
{: #prereqs-getting-started}

É possível criar o seu app usando o console ou a interface da linha de comandos (CLI) do {{site.data.keyword.cloud_notm}}. Se você desejar usar a CLI, veja as [etapas de instalação](/docs/cli?topic=cloud-cli-ibmcloud-cli).

## Etapa 1. Criar o seu app
{: #create-getting-started}

Crie um app selecionando um dos pontos de entrada a seguir:
* [Kit do iniciador](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit): crie um app por meio de uma seleção de kits do iniciador do App Service que gerenciam o processo para você.
* [Customizado](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch): se você sabe o que deseja, construa um app customizado do zero com os recursos dos quais precisa usando um kit do iniciador em branco.
* [Traga o seu próprio código](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc): traga o seu próprio código vinculando ao seu próprio repositório de conteúdo existente. O
app e a imagem do Docker devem estar localizados no mesmo repositório.
* [CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli): crie e implemente um app customizado ou do kit do iniciador usando ferramentas da CLI e do Desenvolvedor.
* [Padrões de código](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern): use um padrão de código do IBM Developer como uma base para criar o seu app.
* [Catálogo do {{site.data.keyword.cloud_notm}}](https://cloud.ibm.com/catalog){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"): é possível navegar ou procurar no catálogo os apps e os serviços que você pode criar e começar a usar hoje.

## Etapa 2. Incluir recursos
{: #resources-getting-started}

Quando você usa um kit do iniciador para criar seu app, seus serviços são criados automaticamente para você. É possível associar mais serviços ao seu app clicando em **Incluir serviço** na página **Detalhes do app** no console.

Para incluir serviços usando a CLI, execute o comando a seguir para incluir um serviço em seu app. É possível selecionar um serviço existente por meio de um serviço já ativado na sua conta ou incluir um novo serviço. 
```
ibmcloud dev edit
```
{: codeblock}

Para
obter mais informações, consulte [Incluindo um serviço no app](/docs/apps?topic=creating-apps-add-resource).

## Etapa 3. Implementar seu app
{: #deploy-getting-started}

É possível implementar o seu app usando o console ou a line da linha de comandos.

### Utilizando o Console
{: #console-getting-started}

Para implementar o seu app usando o console, conclua as etapas a seguir:

1. Na página **Detalhes do app**, clique em **Configurar entrega contínua**.
2. Selecione um destino de implementação, selecione as configurações da cadeia de ferramentas e clique em **Criar**. O {{site.data.keyword.cloud_notm}} automaticamente cria uma cadeia de ferramentas aberta e completa com um repositório Git e um pipeline de entrega contínua.
3. Abra o estágio de pipeline de sua nova cadeia de ferramentas para visualizar o processo de construção e implementação para que seja possível visualizar o seu novo app em minutos.

Para obter mais informações, consulte o índice para vários tópicos de implementação na seção "Implementando e integrando apps".

### Utilizando a linha de comandos
{: #cli-getting-started}

Para implementar o seu app usando a linha de comandos, execute o comando `ibmcloud dev deploy`. Para obter mais informações, consulte [Criando e implementando aplicativos usando a CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli).

Agora você está configurado para desenvolvimento iterativo e entrega contínua.
