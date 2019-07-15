---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-20"

keywords: getting started apps, create app tutorial, add services, deploy apps, create app, app tutorial

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Tutorial Introdução
{: #getting-started}

É possível construir aplicativos móveis e da web prontos para a empresa no {{site.data.keyword.cloud}} e aproveitar as extensões de nuvem que são hospedadas pelo {{site.data.keyword.cloud_notm}}. Você tem várias opções para iniciar. Crie um app com um kit do iniciador que gerencia o processo para você ou, se você souber o que deseja, comece do zero e construa o seu app com os recursos necessários ou use o seu repositório existente e traga o seu próprio código.
{: shortdesc}

Se você tiver [código existente](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc) que deseje modernizar e trazer para a nuvem ou estiver desenvolvendo um [aplicativo novo](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit), será possível acessar o ecossistema em rápido crescimento dos serviços disponíveis e estruturas de tempo de execução no {{site.data.keyword.cloud_notm}}.

Você precisa de ajuda com a decisão de onde começar? O diagrama a seguir fornece uma visão geral para criar apps, se você usa um kit do iniciador ou traz seu próprio código para o {{site.data.keyword.cloud_notm}}.

![Visão geral da experiência do desenvolvedor](images/dev-journey.png "Visão geral de criação de apps em {{site.data.keyword.cloud_notm}}")

## Antes de começar
{: #prereqs-getting-started}

É possível criar o seu app usando o console ou a interface da linha de comandos (CLI) do {{site.data.keyword.cloud_notm}}. Se você desejar usar a CLI, veja as [etapas de instalação](/docs/cli?topic=cloud-cli-getting-started).

## Etapa 1. Criar o seu app
{: #create-getting-started}

Crie um app selecionando um dos pontos de entrada a seguir:

* Os [kits do iniciador pré-configurados](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit) são específicos do caso de uso e fornecem apps prontos para produção em várias linguagens de programação e padrões arquiteturais.
* Os [kits do iniciador básico](/docs/apps/tutorials?topic=creating-apps-tutorial-scratch) permitem construir seu app selecionando o tipo de app (móvel ou back-end), a linguagem e estrutura, os serviços e o destino de implementação.
* [Traga seu próprio código](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc) vinculando a seu próprio repositório de conteúdo existente. O
app e a imagem do Docker devem estar localizados no mesmo repositório.
* A [interface da linha de comandos (CLI) do {{site.data.keyword.dev_cli_long}}](/docs/apps?topic=creating-apps-create-deploy-app-cli) permite criar e implementar seu app usando a CLI.
* Procure ou pesquise no [catálogo do {{site.data.keyword.cloud_notm}}](https://{DomainName}/catalog){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") apps e serviços que você pode criar e começar a usar hoje.
* Os [padrões de código do IBM Developer![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://developer.ibm.com/patterns/){:new_window} ajudam a criar rapidamente seu app e implementá-lo no {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Padrões de código](/docs/apps/tutorials?topic=creating-apps-tutorial-codepattern).

## Etapa 2. Incluir serviços
{: #resources-getting-started}

Ao usar um kit do iniciador para criar seu app, os serviços obrigatórios são criados automaticamente para você. É possível conectar mais serviços ao seu app no console na página **Detalhes do app**, que é exibida assim que você cria o app.

Se você desejar incluir serviços após seu app ser criado, acesse o painel do [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://{DomainName}), localize seu app e, então, clique no nome do seu app. A página
**Detalhes do app** é exibida e é possível criar uma instância de serviço ou
conectar serviços existentes.

Ou é possível executar o comando a seguir para incluir um serviço em seu app usando a CLI. É possível selecionar um serviço existente que já esteja ativado em sua conta ou incluir um serviço.
```
ibmcloud dev edit
```
{: codeblock}

Para
obter mais informações, consulte [Incluindo um serviço no app](/docs/apps?topic=creating-apps-add-resource).

## Etapa 3. Implementar seu app
{: #deploy-getting-started}

É possível implementar seu app usando o console ou a CLI.

### Utilizando o Console
{: #console-getting-started}

Para implementar o seu app usando o console, conclua as etapas a seguir:

1. Na página **Detalhes do app**, clique em **Configurar entrega contínua**.
2. Selecione um destino de implementação, selecione as configurações da cadeia de ferramentas e clique em **Criar**. O {{site.data.keyword.cloud_notm}} automaticamente cria uma cadeia de ferramentas aberta e completa com um repositório Git e um pipeline de entrega contínua.
3. Abra o estágio de pipeline de sua nova cadeia de ferramentas para visualizar o processo de construção e implementação para que seja possível visualizar o seu novo app em minutos.

Para obter mais informações, consulte  [ Implementando apps ](/docs/apps?topic=creating-apps-deploying-apps).

### Usando a CLI
{: #cli-getting-started}

Para implementar seu app usando a CLI, execute o comando `ibmcloud dev deploy`. Para obter mais informações, consulte [Criando e implementando aplicativos usando a CLI](/docs/apps?topic=creating-apps-create-deploy-app-cli).

Agora você está configurado para desenvolvimento iterativo e entrega contínua.

Para obter mais informações sobre como implementar seu app, consulte [Implementando apps](/docs/apps?topic=creating-apps-deploying-apps).

## Informações relacionadas
{: #related-getting-started}

[Guias de programação](https://{DomainName}/docs/home/build){: new_window}
![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") estão
disponíveis por linguagem para ajudá-lo a iniciar. Há muitas opções para hospedar os apps com a infraestrutura
do {{site.data.keyword.cloud_notm}} por meio do {{site.data.keyword.baremetal_short}} para executar
como uma função sem servidor.
