---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-02"

keywords: apps, deploy, deploying apps, toolchains, cli, cloud

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}

# Implementando apps
{: #deploying-apps}

É possível implementar seus aplicativos com uma cadeia de ferramentas do DevOps ou a interface da linha de comandos (CLI). Uma cadeia de ferramentas do DevOps é um conjunto de integrações de ferramentas. A CLI é uma maneira simples de implementar seus apps e instâncias de serviço.
{: shortdesc}

## Implementando apps usando cadeias de ferramentas do DevOps
{: #toolchain-deploy-apps}

As cadeias de ferramentas abertas estão disponíveis nos ambientes Public e Dedicated no {{site.data.keyword.Bluemix}}. Com uma cadeia de ferramentas configurada corretamente, a implementação do app é fácil. Um ciclo de implementação de construção é iniciado automaticamente com cada mesclagem na ramificação principal em seu repositório.

É possível criar uma cadeia de ferramentas destas maneiras:
* Crie uma cadeia de ferramentas por meio de um app. Para obter mais informações, consulte [Implementando seu app](/docs/apps?topic=creating-apps-tutorial-scratch#deploy-scratch).
* Use um modelo para criar uma cadeia de ferramentas. Para obter mais informações, consulte [Criando cadeias de ferramentas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).

## Implementando apps usando a CLI
{: #cli-deploy-apps}

O {{site.data.keyword.cloud_notm}} fornece uma CLI robusta, além de plug-ins e extensões de ferramentas do desenvolvedor que se integram à CLI.

Antes de iniciar, [faça download e instale a CLI do {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).

A CLI não é suportada pelo Cygwin. Use a ferramenta em uma janela diferente da janela de linha de comandos do Cygwin.
{: important}

  1. Faça download do código do app em um novo diretório para configurar seu ambiente de desenvolvimento.

  2. Mude para o diretório no qual o seu código está localizado.

  3.  Atualize seu código de app. Por exemplo, se você estiver usando um aplicativo de amostra do {{site.data.keyword.cloud_notm}} e seu app contiver o arquivo `src/main/webapp/index.html`, será possível modificá-lo e editar a linha `Thanks for creating...`. Assegure-se de que o app seja executado localmente antes de implementá-lo no {{site.data.keyword.cloud_notm}}.

    Anote o arquivo `manifest.yml`. Quando você implementa seu app no {{site.data.keyword.cloud_notm}}, esse arquivo é usado para determinar a URL de seu aplicativo, a alocação de memória, o número de instâncias e outros parâmetros cruciais.

    Revise também o arquivo `README.md`, que contém detalhes, tais como instruções de construção.

    Caso seja um app Liberty, deve-se construí-lo antes que seja novamente implementado.
    {: note}

  4. Efetue login na CLI do {{site.data.keyword.cloud_notm}} com seu IBMid. Se você tiver múltiplas contas, deverá selecionar qual conta usar. Se você não especificar uma região com a sinalização `-r`, deverá também escolher uma região.
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    Se as suas credenciais forem rejeitadas, talvez você esteja usando um ID federado. Para efetuar login com uma identidade federada, use a sinalização `--sso`. Para obter mais informações, consulte [Efetuando login com um ID federado](/docs/iam/federated_id?topic=iam-federated_id#federated_id).
    {: tip}

  5. Em seu novo diretório, implemente seu app no {{site.data.keyword.cloud_notm}} usando o comando [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).
    ```
    ibmcloud dev deploy <APP_NAME>
    ```
    {: codeblock}

  6. Acesse seu app executando o comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para visualizar a URL de seu app. Em seguida, acesse a URL em seu navegador.
