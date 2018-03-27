---

copyright:
  years: 2018
lastupdated: "2018-03-16"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Fases recomendadas de desenvolvimento em nuvem
{: #development_process}

Os desenvolvedores de aplicativos em nuvem passam por quatro fases fundamentais no processo de desenvolvimento: introdução, codificação, entrega e gerenciamento. O fluxo é interativo e rápido. O objetivo é produzir rapidamente um app mínimo viável e, em seguida, usar o feedback do app de produção para iterar continuamente o ciclo de código ou entrega até que seu app ressoe com usuários.
{: shortdesc}

![Fluxo de desenvolvimento](images/dev_flow_overview.png "Fluxo de desenvolvimento") Figura 1. Fases do processo de desenvolvimento

Em alguns casos, a "execução" é chamada como uma fase separada, mas nós a combinamos aqui com as fases Entregar e Gerenciar.

Vamos dar uma olhada mais de perto na melhor maneira de usar o {{site.data.keyword.cloud_notm}} em seu fluxo de desenvolvimento.

##Introdução
{: #get_started}

Comece a construir seu app por meio dos painéis de desenvolvedor do {{site.data.keyword.cloud_notm}}, nos quais é possível selecionar um kit do iniciador relacionado ao seu caso de uso e escolher uma linguagem de programação. O {{site.data.keyword.cloud_notm}} usa instruções do kit do iniciador para provisionar automaticamente os recursos que você precisa e para criar um projeto de app agnóstico de tempo de execução e específico da linguagem que é a base para seu app de produção. Para concluir a fase de introdução, clique em **Implementar no Cloud** no painel de desenvolvedor. Um clique cria uma cadeia de ferramentas do DevOps completa com um repositório de código que é preenchido com seu código-fonte de app e pipeline de implementação.

![Introdução](images/dev_get_started.png "Introdução") Figura 2. Fluxo de introdução

Quando você usar o botão **Implementar no Cloud** para configurar sua cadeia de ferramentas do DevOps, selecione sua plataforma de tempo de execução, por exemplo, Kubernetes ou Cloud Foundry. O app de iniciador produzido por meio do {{site.data.keyword.cloud_notm}} é agnóstico de tempo de execução e não precisa ser modificado.
{: tip}

##Desenvolver localmente
{: #develop_locally}

Depois de criar seu projeto de app de iniciador e cadeia de ferramentas, você inicia seu desenvolvimento localmente. Clone o código de seu repositório para uma estação de trabalho local e importe para seu IDE. Use o {{site.data.keyword.dev_cli_notm}} para construir, executar e testar seu app em nuvem em sua máquina local. O {{site.data.keyword.dev_cli_notm}} cria e gerencia um contêiner local para você. Quando você estiver pronto para ver seu app em execução na nuvem, envie por push para seu repositório na nuvem e mescle suas mudanças.

![Desenvolver localmente](images/dev_code_locally.png "Desenvolver localmente") Figura 3. Desenvolvendo o fluxo localmente

As funções básicas para o {{site.data.keyword.dev_cli_notm}} são `bx dev build` e `bx dev run`, mas a CLI oferece muito mais. Veja [{{site.data.keyword.dev_cli_notm}}](../cli/idt/index.html) para obter mais detalhes.
{: tip}

##Entregar e gerenciar no {{site.data.keyword.cloud_notm}}
{: #deliver_and_manage}

A mesclagem de mudanças em seu repositório na nuvem inicia um ciclo de construção e implementação na cadeia de ferramentas do DevOps que você criou anteriormente. Seu app está em execução na nuvem após alguns minutos.

Para verificar o status de seu pipeline do DevOps, use o painel do Delivery Pipeline. Para verificar o status geral de seu app, veja o painel do {{site.data.keyword.cloud_notm}} para sua conta.
{: tip}

A cadeia de ferramentas produzida pela sua experiência de introdução tem os componentes básicos que você precisa para entrega colaborativa e contínua baseada em equipe. No entanto, o {{site.data.keyword.cloud_notm}} oferece um conjunto extensivo de serviços do DevOps que podem ser incluídos em sua cadeia de ferramentas para aprimorar a entrega, o monitoramento, a criação de log e o alerta.

![Entregar e gerenciar](images/dev_deliver_and_manage.png "Entregar e gerenciar") Figura 4. Entregando e gerenciamento o fluxo

Saiba mais sobre [desenvolvimento contínuo no {{site.data.keyword.cloud_notm}}](../services/ContinuousDelivery/index.html#cd_getting_started).

## Colocando tudo junto

![Detalhe do processo](images/dev_process_detail.png "Detalhes do processo") Figura 5. Processo de desenvolvimento de ponta a ponta
