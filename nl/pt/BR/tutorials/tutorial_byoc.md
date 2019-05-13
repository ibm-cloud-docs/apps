---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-30"

keywords: byoc, code repository, continuous delivery, cli, deploy, create app custom repo, custom repo, existing repo, custom code

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

Se você tiver um aplicativo em um repositório existente, será possível usar um kit do iniciador vazio para criar um registro de app no {{site.data.keyword.cloud_notm}} e conectar o app a seu repositório de origem e à sua cadeia de ferramentas do DevOps.
{: shortdesc}

É possível iniciar por meio do painel do {{site.data.keyword.cloud_notm}} ou de qualquer kit do iniciador em branco. Depois
de nomear o app e selecionar um grupo de recursos, selecione o ponto de início
**Trazer seu próprio código**, forneça a URL do repositório Git que contém o código e clique em **Criar**.

É possível conectar sua cadeia de ferramentas do DevOps existente ou criar uma e entregar continuamente seu app ao destino de implementação de sua escolha, como Kubernetes ou Cloud Foundry.

## Antes de começar
{: #prereqs-byoc}

Verifique se os pré-requisitos a seguir estão prontos:

 * Instale a [interface da linha de comandos (CLI) do {{site.data.keyword.dev_cli_long}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).
 * Consulte [O que torna bom um app?](/docs/apps?topic=creating-apps-best-practice) para obter as melhores
práticas para criar apps.
 * Deve-se ter um repositório de código-fonte Git de qualquer um dos seguintes provedores: GitHub,
GitHub Enterprise, GitLab, BitBucket ou Rational.
 * Se você planeja implementar seu app no [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), deve-se [preparar sua conta do {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Criando um app com um repositório existente
{: #create-byoc}

Para criar um app e conectá-lo ao repositório de origem, conclua estas etapas:

1. No [console do {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window}![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo"), clique em **Criar um app** no tile **Apps**.
2. Nomeie o seu app, selecione um grupo de recursos e, opcionalmente, forneça identificações para classificar o seu app. Para obter mais informações, consulte [Trabalhando com tags](/docs/resources?topic=resources-tag).
3. Selecione **Trazer seu próprio código** e forneça a URL para o seu repositório Git. O
app e a imagem do Docker devem estar localizados no mesmo repositório.
4. Clique em **Criar**. A página **Detalhes do app** é exibida.
5. Opcional. [Inclua serviços](/docs/apps?topic=creating-apps-add-resource) em seu app.
6. Opcional. É possível incluir tags nesse app clicando em **Incluir tags** ou é possível editar tags clicando no ícone **Editar** ![Ícone Editar](../../icons/edit-tagging.svg) que está próximo às tags exibidas.
7. Opcional. Visualize o repositório clicando em **Visualizar repositório.**

## Implementando seu app
{: #toolchain-byoc}

Estabelecer um link entre o app, a cadeia de ferramentas e o repositório é uma etapa para a organização dos
ativos do produto. Isso também ajuda a agregar uma visualização da origem com o fluxo de trabalho do DevOps, as
instâncias do app em execução e os serviços dependentes em todos os destinos de implementação. Para obter mais informações, consulte [Criando cadeias de ferramentas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

É possível configurar a entrega contínua para o seu app usando o console do {{site.data.keyword.cloud_notm}} ou a CLI.

### Utilizando o Console
{: #console-byoc-toolchain}

#### Se você já tiver uma cadeia de ferramentas do DevOps que desejar conectar a seu app, conclua estas etapas:

1. Na página **Detalhes do app**, clique em **Configurar entrega contínua**. A página **Implementar meu app** é exibida.
2. Selecione a cadeia de ferramentas que você deseja conectar a seu app e clique em **Ativar implementação**. A página **Detalhes do app** é exibida, indicando que a entrega contínua está configurada.

#### Se você não tiver uma cadeia de ferramentas do DevOps para esse app, conclua estas etapas:

1. Na página **Detalhes do app**, clique em **Criar cadeia de ferramentas do DevOps.** A página **Criar uma cadeia de ferramentas** será exibida.
2. [Crie a cadeia de ferramentas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).
3. Use as trilhas de navegação na janela do navegador para retornar para a página **Detalhes do app**, que indica que a entrega contínua está configurada.

### Usando a CLI
{: #cli-byoc-toolchain}

É possível usar o comando `ibmcloud dev enable` para gerar um modelo de cadeia de ferramentas do DevOps que você verifica em seu repositório conforme a instrução definida para o que a cadeia de ferramentas do DevOps deve criar. 

  1. Na página **Detalhes do app**, clique em **Visualizar repositório** para trabalhar com seu código localmente.
  2. Execute o seguinte comando:
    
    ```
    Ibmcloud dev enable
    ```
   {: codeblock}

Para obter mais informações sobre como implementar seu app, consulte [Implementando apps](/docs/apps?topic=creating-apps-deploying-apps).

## Verificando se o seu app está em execução
{: #verify-byoc-app}

O Delivery Pipeline ou a linha de comandos aponta você para a URL para seu app.

1. Na cadeia de ferramentas do seu DevOps, clique em **Delivery Pipeline** e, em seguida, selecione **Implementar estágio**.
2. Clique em **Visualizar logs e histórico**.
3. No arquivo de log, localize a URL do aplicativo. No término do arquivo de log, procure a palavra `urls` ou `view`. Por exemplo, você pode ver uma linha no arquivo de log que é semelhante a `urls: my-app-devhost.mybluemix.net` ou `View the application health at: http://<ipaddress>:<port>/health`.
4. Acesse a URL em seu navegador. Se o app estiver em execução, uma mensagem que incluirá `Parabéns` ou `{"status":"UP"}` será exibida.

Se você estiver usando a linha de comandos, execute o comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para abrir a página de um app implementado manualmente em seu navegador padrão.
