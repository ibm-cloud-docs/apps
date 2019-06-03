---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-06"

keywords: apps, deploy, deploying apps, toolchain, cli, cloud, devops, deployment, git, push

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

É possível implementar seu aplicativo no {{site.data.keyword.cloud}} usando uma cadeia de ferramentas do DevOps. Com uma cadeia de ferramentas do DevOps, é possível automatizar implementações para muitos ambientes e incluir rapidamente os serviços de monitoramento, de criação de log, de insights e de alerta para ajudar a gerenciar o app à medida que ele cresce. É possível configurar a entrega contínua e implementar seu app usando o console da web ou a interface da linha de comandos (CLI) do {{site.data.keyword.cloud_notm}}.
{: shortdesc}

Uma cadeia de ferramentas do DevOps fornece um ambiente de desenvolvimento baseado em equipe para seu app. Quando você cria uma cadeia de ferramentas, o serviço de app cria um repositório Git, no qual é possível visualizar o código-fonte, clonar seu app e criar e gerenciar problemas. Você também tem acesso a um ambiente GitLab dedicado e a um pipeline de entrega contínua. Eles são customizados para o destino de implementação selecionado, seja o [Kubernetes](/docs/containers?topic=containers-getting-started), o [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), o [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) ou o [servidor virtual (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Todas as cadeias de ferramentas criadas por meio do painel do Desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.
{: note}

## Usando o console {{site.data.keyword.cloud_notm}}
{: deploy-console}

O {{site.data.keyword.cloud_notm}} fornece um console da web no qual é possível configurar a entrega contínua e implementar seu app usando uma cadeia de ferramentas do DevOps.

### Antes de começar
{: deploy-console-before}

Antes de iniciar, use o [painel do {{site.data.keyword.cloud_notm}}](https://{DomainName}){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") para [criar seu app](/docs/apps?topic=creating-apps-tutorial-getting-started#create-getting-started) e [incluir serviços](/docs/apps?topic=creating-apps-tutorial-getting-started#resources-getting-started).

### Implementando seu app automaticamente
{: deploy-console-auto}

1. Na página **Detalhes do app**, clique em **Configurar entrega contínua**.
2. Selecione um destino de implementação. Configure o destino de implementação de acordo com as instruções para o destino selecionado:
  * **Implementar no IBM Kubernetes Service**. Essa opção cria um cluster de hosts, chamados de nós do trabalhador, para implementar e gerenciar contêineres de aplicativo altamente disponíveis. É possível criar um cluster ou implementar em um cluster existente. Para obter mais informações, consulte [Implementando apps em clusters do Kubernetes](/docs/containers?topic=containers-app).
  * **Implemente no Cloud Foundry**. Essa opção implementa o seu app nativo de nuvem sem você precisar gerenciar a infraestrutura subjacente. Se a sua conta tiver acesso ao {{site.data.keyword.cfee_full_notm}}, será possível selecionar um tipo de implementador do **Public Cloud** ou do **Enterprise Environment**, que é possível usar para criar e gerenciar ambientes isolados para hospedar aplicativos do Cloud Foundry exclusivamente para a sua empresa. Para obter mais informações, consulte [Implementando apps no Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps) e [Implementando apps no {{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps).
  * **Implementar em um Servidor virtual**. Essa opção provisiona uma instância de servidor virtual, carrega uma imagem que inclui o seu app, cria uma cadeia de ferramentas do DevOps e inicia o primeiro ciclo de implementação para você. Para obter mais informações, consulte [Implementando apps em um servidor virtual](/docs/apps?topic=creating-apps-vsi-deploy).

### Implementando seu app manualmente
{: deploy-console-manual}

Com uma cadeia de ferramentas configurada corretamente, um ciclo de construção/implementação é iniciado automaticamente com cada mesclagem à ramificação principal em seu repositório. 

Também é possível implementar seu app manualmente por meio de sua cadeia de ferramentas DevOps:

1. Na página **Detalhes do app**, clique em **Visualizar cadeia de ferramentas**.
2. Clique em **Delivery Pipeline**, no qual é possível iniciar construções, gerenciar a implementação e visualizar logs e histórico.

A entrega contínua é ativada automaticamente para alguns aplicativos. É possível ativar a entrega contínua para automatizar construções, testes e implementações por meio do Delivery Pipeline e do GitHub.

Para obter informações
adicionais, consulte:
* [Construindo e implementando](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy)
* [Criando cadeias de ferramentas](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)

## Usando o {{site.data.keyword.dev_cli_short}} CLI
{: #deploy-cli}

O {{site.data.keyword.cloud_notm}} fornece uma CLI robusta e plug-ins para ajudar a simplificar o fluxo de trabalho do desenvolvedor. É possível implementar o app {{site.data.keyword.cloud_notm}} de uma de duas maneiras, dependendo da configuração do app.

### Antes de começar
{: #deploy-cli-before}

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

  4. Efetue login na CLI do {{site.data.keyword.cloud_notm}} com seu IBMid. Se você tiver múltiplas contas, deverá selecionar qual conta usar. Se você não especificar uma região com o sinalizador `-r`, deverá também selecionar uma região.
    ```
    ibmcloud login
    ```
    {: codeblock}
  
    Se as suas credenciais forem rejeitadas, talvez você esteja usando um ID federado. Para efetuar login com uma identidade federada, use a sinalização `--sso`. Para obter mais informações, consulte [Efetuando login com um ID federado](/docs/iam/federated_id?topic=iam-federated_id#federated_id).
    {: tip}

### Implementando seu app automaticamente
{: #deploy-cli-auto}

Se você não criou uma cadeia de ferramentas do DevOps para o app e ele ainda não está em um repositório Git, será possível executar o comando [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit). Siga os prompts para "Configurar o DevOps" e implemente em uma nova cadeia de ferramentas (e crie um novo repositório GitLab).

Após você criar uma cadeia de ferramentas do DevOps para o seu app, a implementação de uma nova construção é tão simples quanto confirmar e enviar por push o seu código para o repositório em sua cadeia de ferramentas. 

1. Prepare as mudanças a serem confirmadas.
    ```
    git add .
    ```
2. Confirme as mudanças com uma mensagem breve.
    ```
    git commit -m "made changes"
    ```
3. Envie por push as confirmações na ramificação principal para o repositório remoto.
    ```
    git push origin master
    ```
4. Visualize a cadeia de ferramentas do DevOps para o app por meio do console do {{site.data.keyword.cloud_notm}}. É possível visualizar os detalhes da cadeia de ferramentas na página **Detalhes do app** no console do {{site.data.keyword.cloud_notm}} executando o comando [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) no diretório do app.
5. Visualize o pipeline dentro da cadeia de ferramentas para verificar se uma nova compilação foi iniciada.

### Implementando seu app manualmente
{: #deploy-cli-manual}

É possível implementar manualmente seu app no {{site.data.keyword.cloud_notm}} usando o comando [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).

  ```
  ibmcloud dev deploy <APP_NAME>
  ```
  {: codeblock}

### Informações relacionadas
{: #deploy-cli-related}

Para obter mais informações sobre como implementar seu app no {{site.data.keyword.cloud_notm}} usando a CLI, consulte:

* [Implementando em ambientes do IBM Cloud com a CLI do {{site.data.keyword.dev_cli_short}}](https://www.ibm.com/cloud/blog/deploying-to-ibm-cloud-environments-with-ibm-cloud-developer-tools-cli){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")
