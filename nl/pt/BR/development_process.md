---

copyright:
  years: 2018
lastupdated: "2018-11-29"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Fases recomendadas de desenvolvimento em nuvem
{: #development_process}

Os desenvolvedores de aplicativos em nuvem passam por quatro fases fundamentais no processo de desenvolvimento: introdução, codificação, entrega e gerenciamento. O objetivo é produzir rapidamente um app de trabalho e, em seguida, usar o feedback do app de produção para iterar continuamente o código ou entregar o ciclo até que o seu app ressoe com os usuários.
{: shortdesc}

![Fluxo de desenvolvimento](images/dev_flow_overview.png "Fluxo de desenvolvimento") Figura 1. Fases do processo de desenvolvimento

Em alguns casos, `run` é chamado como uma fase separada, mas é combinado aqui com as fases de Entrega e Gerenciamento.

Vamos dar uma olhada mais de perto na melhor maneira de usar o {{site.data.keyword.cloud}} em seu fluxo de desenvolvimento.

## Introdução
{: #get_started}

Construa o seu app por meio dos painéis do {{site.data.keyword.cloud_notm}} Developer, em que é possível selecionar um kit do iniciador que está relacionado ao seu caso de uso e escolher uma linguagem de programação. O {{site.data.keyword.cloud_notm}} usa instruções do kit do iniciador para criar automaticamente os recursos de que você precisa e para criar um app específico da linguagem, independente de tempo de execução que é a base para o seu app de produção. Para concluir a fase de introdução, clique em **Implementar na nuvem** no painel do Desenvolvedor. Um clique cria uma cadeia de ferramentas do DevOps completa com um repositório de código que é preenchido com seu código-fonte do app e pipeline de implementação.

![Introdução](images/dev_get_started.png "Introdução") Figura 2. Fluxo de introdução

Quando você usar o botão **Implementar na nuvem** para configurar a sua cadeia de ferramentas do DevOps, selecione a sua plataforma de tempo de execução, como Kubernetes ou Cloud Foundry. O app do kit do iniciador que é produzido por meio do {{site.data.keyword.cloud_notm}} é independente de tempo de execução e não precisa ser modificado.
{: tip}

## Desenvolver localmente
{: #develop_locally}

Após você criar o seu app do kit do iniciador e a cadeia de ferramentas, você inicia o seu desenvolvimento localmente. Clone o código de seu repositório para uma estação de trabalho local e importe para seu IDE. Use o {{site.data.keyword.dev_cli_long}} para construir, executar e testar seu app em nuvem em sua máquina local. O {{site.data.keyword.dev_cli_notm}} cria e gerencia contêineres locais para você. Quando você estiver pronto para ver que o seu app está em execução na nuvem, envie por push para o seu repositório de nuvem e mescle as suas mudanças.

![Desenvolver localmente](images/dev_code_locally.png "Desenvolver localmente") Figura 3. Desenvolvendo o fluxo localmente

As funções básicas para o {{site.data.keyword.dev_cli_notm}} são `ibmcloud dev build` e `ibmcloud dev run`, mas a CLI oferece muito mais. Veja [{{site.data.keyword.dev_cli_notm}}](/docs/cli/index.html#overview) para obter mais detalhes.
{: tip}

## Entregar e gerenciar no {{site.data.keyword.cloud_notm}}
{: #deliver_and_manage}

A mesclagem de mudanças em seu repositório na nuvem inicia um ciclo de construção e implementação na cadeia de ferramentas do DevOps que você criou anteriormente. Seu app está em execução na nuvem após alguns minutos.

Para verificar o status de seu pipeline do DevOps, use o painel do Delivery Pipeline. Para verificar o status geral de seu app, veja o painel do {{site.data.keyword.cloud_notm}} para sua conta.
{: tip}

A cadeia de ferramentas produzida pela sua experiência de introdução possui os componentes básicos necessários para entrega contínua colaborativa e baseada em equipe. No entanto, o {{site.data.keyword.cloud_notm}} oferece um conjunto extensivo de serviços do DevOps que podem ser incluídos em sua cadeia de ferramentas para aprimorar a entrega, o monitoramento, a criação de log e o alerta.

![Entregar e gerenciar](images/dev_deliver_and_manage.png "Entregar e gerenciar") Figura 4. Entregando e gerenciamento o fluxo

Saiba mais sobre [desenvolvimento contínuo no {{site.data.keyword.cloud_notm}}](/docs/services/ContinuousDelivery/index.html#cd_getting_started).

## Colocando tudo junto

![Detalhe do processo](images/dev_process_detail.png "Detalhes do processo") Figura 5. Processo de desenvolvimento de ponta a ponta
