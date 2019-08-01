---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-29"

keywords: apps, serverless, serverless app, functions, cli, api, sdk, create serverless app, serverless app tutorial

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Criando apps sem servidor
{: #serverless}

Para o desenvolvimento sem servidor, é possível usar o {{site.data.keyword.openwhisk}}, que é a oferta IBM functions-as-a-service (FaaS). É possível executar a lógica de aplicativo com o {{site.data.keyword.openwhisk_short}} em resposta a eventos ou chamadas diretas de apps da web ou móveis sobre HTTP sem provisionar ou gerenciar servidores. O {{site.data.keyword.openwhisk_short}} executa a administração do sistema, como auto-scaling, gerenciamento de disponibilidade e manutenção, para que você, como desenvolvedor, possa se concentrar na gravação da lógica de app.
{:shortdesc}

É possível desenvolver apps sem servidor usando um dos métodos a seguir:
* Interface com o usuário (IU) do {{site.data.keyword.openwhisk_short}}.
* Interface da linha de comandos (CLI) do {{site.data.keyword.openwhisk_short}}, que fornece mais controle sobre sua implementação e operações.
* Kit do iniciador do {{site.data.keyword.openwhisk_short}}, no qual é possível configurar a entrega contínua usando uma cadeia de ferramentas do DevOps e um Delivery Pipeline.

Para obter informações mais detalhadas sobre o {{site.data.keyword.openwhisk_short}}, verifique a [documentação](/docs/openwhisk?topic=cloud-functions-getting_started).


## Desenvolvendo com a IU do {{site.data.keyword.openwhisk_short}}
{: #serverless-apps-ui}

Experimente o {{site.data.keyword.openwhisk_short}} em seu [navegador](https://{DomainName}/functions/actions){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")}. Acesse a página [Conceitos ](https://{DomainName}/functions/learn){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") para obter um tour rápido da interface com o usuário do {{site.data.keyword.openwhisk_short}}.

## Desenvolvendo com a CLI
{: #openwhisk_start_configure_cli}

Para saber mais sobre como instalar e desenvolver com a CLI do {{site.data.keyword.openwhisk_short}}, consulte [Configurando a CLI do {{site.data.keyword.openwhisk_short}}](https://{DomainName}/functions/cli){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

## Expondo APIs e conjuntos de dados como ações da web
{: #expose-actions}

Por padrão, o {{site.data.keyword.openwhisk_short}} define ações que requerem uma chave de autenticação. Em ambientes de dispositivo móvel de produção, muitas vezes é necessário autorizar clientes móveis com base em fluxos OAuth para expor APIs e conjuntos de dados específicos.

O {{site.data.keyword.openwhisk_short}} permite que os desenvolvedores exponham suas funções como ações da web, que são anotadas, para construir rapidamente os apps baseados na web. É possível programar a lógica de back-end com ações anotadas que seu app da web pode acessar anonimamente, sem requerer uma chave de autenticação do {{site.data.keyword.openwhisk_short}}.

Para expor uma ação como uma ação da web, acesse a guia **Terminais** de sua ação e selecione **Ativar como ação da web**.

Agora, os usuários podem acessar a ação por meio de um navegador ou solicitação cURL, por exemplo:
```
curl https://openwhisk.cloud.ibm.com/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron
```
{: codeblock}

Saída:
```json
{
    message: "Hello aaron!"
}
```
{: screen}

### SDK
{: #sdk}

O {{site.data.keyword.openwhisk_short}} fornece um [SDK móvel](/docs/openwhisk?topic=cloud-functions-pkg_mobile_sdk) para dispositivos iOS e watchOS que permite que os apps móveis enviem facilmente acionadores remotos e chamem ações remotas.

## Criando apps sem servidor usando um kit do iniciador
{: #serverless-starter}

É possível usar um kit do iniciador para criar um app sem servidor, como o Python Example Serverless App. Para localizar os kits do iniciador, conclua estas etapas:

1. Acesse a página [Kits do iniciador do serviço de app](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") no console do {{site.data.keyword.dev_console}}.
2. Digite `serverless` na barra de procura para filtrar a lista de kits do iniciador.
3. Selecione um kit do iniciador sem servidor, como o Python Example Serverless App.
4. Nomeie o app e selecione um grupo de recursos.
5. Opcional. Forneça identificações para classificar o seu app. Para obter mais informações, consulte [Trabalhando com tags](/docs/resources?topic=resources-tag).
6. Crie ou selecione uma instância de serviço existente do Cloudant.
7. Opcional. Para inspecionar seu código antes de incluir mais serviços ou implementar seu app, clique em **Visualizar código-fonte**. Verifique o arquivo `README.md` para descobrir se é necessário executar mais ações para que o seu app funcione.
8. Clique em **Criar**.

Ótimo início! Você acabou de criar um app.

## Incluir serviços (opcional)
{: #serverless-services}

Se um kit do iniciador requerer serviços específicos, os serviços fornecidos automaticamente estarão disponíveis para que as instâncias para esses serviços sejam criadas automaticamente quando você criar seu app.

1. Na página Detalhes do app, clique em **Criar serviço** ou **Conectar serviços existentes**, dependendo de se você já tem serviços que deseja conectar a esse app.
2. Selecione o tipo de serviço que você deseja e siga os prompts para incluir um serviço existente em seu app ou criar uma instância de serviço.

Após a inclusão de todos os serviços desejados, eles serão exibidos na página Detalhes do app.

## Implementar seu app
{: #serverless-deploy}

Para implementar seu app, conclua estas etapas:

1. Na página Detalhes do app, clique em **Implementar**.
2. Selecione **Implementar no Cloud Functions** e clique em **Avançar**.
3. Na página Configurar cadeia de ferramentas, insira um nome de cadeia de ferramentas, selecione uma região e clique em **Criar**. Após a seleção e a configuração do destino de implementação, a página Detalhes do app indica que a entrega contínua está configurada.
4. Opcional. Revise as ações no console do {{site.data.keyword.openwhisk_short}} clicando no ícone Ações ![Ícone Mais ações](../icons/action-menu-icon.svg) e selecionando **Abrir o Cloud Functions**.
5. Opcional. Visualize o repositório que contém o código gerado para seu app e serviços clicando em **Visualizar repositório**.

## Verificando se o seu app está implementado
{: #serverless-verify}

Com uma cadeia de ferramentas configurada corretamente, um ciclo de construção/implementação é iniciado automaticamente com cada mesclagem à ramificação principal em seu repositório. Para obter mais informações, consulte [Construindo e implementando](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

Para verificar se o seu app foi implementado com êxito, conclua estas etapas:

1. Na página Detalhes do app, clique em **Visualizar cadeia de ferramentas**.
2. Clique em **Delivery Pipeline**, no qual é possível iniciar construções, gerenciar a implementação e visualizar logs e histórico.
3. Se a implementação for bem-sucedida, cada estágio de pipeline indicará **Estágio aprovado**.
4. Para visualizar as informações de ação e de API, clique em **Visualizar logs e histórico** no quadro **Implementar estágio**.
