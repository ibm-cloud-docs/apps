---

copyright:
  years: 2019
lastupdated: "2019-04-15"

keywords: developer tools, building apps, developer entry point, get started coding, starter kit

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Kits iniciadores
{: #starter-kits}

Os Kits do iniciador são ótimos para montar dinamicamente um aplicativo de produção de estrutura básica no idioma de sua escolha que está pronto para implementação na nuvem. Cada kit do iniciador inclui um idioma, uma estrutura e um padrão para um caso de uso específico. É possível reutilizar o código em vez de reinventá-lo.
{:shortdesc}

Se um kit do iniciador requerer serviços específicos, nenhum problema. Com os serviços autoprovisionados, o {{site.data.keyword.cloud_notm}} cria automaticamente instâncias para esses serviços quando você cria seu app. É possível acessar kits do iniciador por meio do painel do {{site.data.keyword.cloud_notm}} ou da interface da linha de comandos.

## O que é um kit do iniciador?
{: #starter_kits}

Um kit do iniciador é um padrão pronto para produção que pode ser integrado a um conjunto de serviços para gerar um ativo pronto para produção que pode ser implementado diretamente em um pipeline do DevOps e em um cluster Kubernetes. Um kit do iniciador contém metadados descritivos que fornecem ao usuário informações suficientes para saber o que o kit é e faz. Ele também contém instruções que indicam ao {{site.data.keyword.cloud_notm}} o que produzir. A saída está pronta para uso de produção e pode ser iterada para aprimoramentos adicionais, com base nas melhores práticas do {{site.data.keyword.cloud_notm}}. O conteúdo do kit do iniciador não é tão complexo como uma demonstração e não tão trivial como um fragmento ou amostra. Ele é criado dinamicamente com base nos requisitos do desenvolvedor.

Confira as instruções para [criar um app com um kit do iniciador](/docs/apps?topic=creating-apps-tutorial-starterkit).

## O quanto os kits do iniciador são diferentes das amostras?
Os kits do iniciador são prontos para produção e focam em demonstrar uma implementação padrão de chave usando um tempo de execução (por exemplo, Node.js e Express). Em alguns casos, os kits do iniciador oferecem uma experiência do usuário simples para destacar a integração do serviço. Em outros casos, os kits do iniciador representam uma implementação customizável de um caso de uso sofisticado.

* Um fragmento são algumas linhas de código frequentemente apresentadas em um IDE. Os fragmentos ajudam um desenvolvedor a integrar-se a uma sintaxe de linguagem de programação ou a suportar a integração com uma API definida.
* Uma demonstração é geralmente alta em qualidade e fidelidade e usa uma gama de serviços e pontos de integração. Ela geralmente requer tempo de configuração e é usada para provar um problema de negócios ou demonstrar um recurso de plataforma. É possível usá-la para avaliar os estágios de adoção de nuvem. Às vezes, esse é o código incluído no código de produção.
* Uma amostra é um pequeno exemplo de um recurso, uma função, um serviço ou uma jornada de usuário específicos. É possível reutilizar uma amostra ou incluí-la em um aplicativo de produção. Ela é usada geralmente para mostrar recursos técnicos e uma possível abordagem para solucionar um problema técnico.

## Código móvel
{: #portable-code}

A criação de um app por meio de um kit do iniciador cria automaticamente o código que tem um formato consistente e não é dependente do tempo de execução. É possível implementar o código em seu destino de opção, como o Kubernetes ou o Cloud Foundry, sem fazer mudanças.

É possível dar uma olhada rápida em seu código de app clicando em **Fazer download do código** na página **Detalhes do app** de seu app. O código é transferido por download como um arquivo `.zip` que contém a estrutura do código do app completa. É possível extrair facilmente o arquivo e executar o código localmente usando o {{site.data.keyword.dev_cli_notm}} ou incluí-lo em seu repositório de gerenciamento de código.

### Qual código é criado?
{: #what-code}

Quando você cria um app diretamente ou com a ajuda de um kit do iniciador, o app contém um código móvel. O código móvel contém o código de ativação de nuvem para múltiplos ambientes de nuvem. Então, é possível produzir o código
em quatro áreas fundamentais:
* Código que segue as melhores práticas de um idioma específico
* Código que permite que o app seja executado na nuvem
* Código que é inicializado para se conectar aos serviços de nuvem
* Código que é específico para um caso de uso

Gerar esses componentes economiza tempo valioso e assegura que você esteja usando uma arquitetura de ponta.

* A lógica de caso de uso fornece funções para a função principal de um caso de uso específico. Os exemplos podem ser código para um robô de bate-papo do Watson Conversation ou código para um app de reconhecimento visual móvel.
* Componentes de linguagem são componentes de código e arquivos específicos da linguagem de programação selecionada para o kit do iniciador. Por exemplo, os programadores de node.js precisam de um arquivo package.json para o gerenciamento de dependência e esse arquivo é criado automaticamente.
* Ativação de serviço é o código que permite que seu app se conecte e use os serviços incluídos. O gerenciamento de credencial, o código de inicialização e os SDKs específicos do serviço são exemplos de itens de ativação de serviço.
* Ativação de nuvem é o código que permite que seu app seja executado no {{site.data.keyword.cloud_notm}}. Por exemplo, os gráficos Helm que permitem que seu app seja executado em um cluster do Kubernetes do {{site.data.keyword.cloud_notm}}.

Ao criar um app por meio de um kit do iniciador do {{site.data.keyword.cloud_notm}}, ele é iniciado com arquitetura comprovada que também reflete as melhores práticas do idioma selecionado.

Cada aplicativo inclui um arquivo leia-me que contém detalhes técnicos do app e explica o que é necessário para deixar seu app em execução caso ele não seja executado pronto para utilização.
{: tip}
