---

copyright:
  years: 2019
lastupdated: "2019-05-09"

keywords: developer tools, building apps, developer entry point, get started coding, starter kit

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# O que são kits do iniciador?
{: #starter-kits}

Um kit do iniciador é um padrão pronto para produção que pode ser integrado a um conjunto de serviços para gerar um ativo pronto para produção que pode ser implementado diretamente em um pipeline do DevOps e em um cluster Kubernetes. Os Kits do iniciador são ótimos para montar dinamicamente um aplicativo de produção de estrutura básica no idioma de sua escolha que está pronto para implementação na nuvem. 
{:shortdesc}

Um kit do iniciador contém metadados que descrevem o que é o kit e o que ele faz. Ele também contém informações que indicam ao {{site.data.keyword.cloud_notm}} o que produzir. O resultado é pronto para produção e pode ser iterado para aprimoramentos adicionais com base nas melhores práticas do {{site.data.keyword.cloud_notm}}. O conteúdo do kit do iniciador não é tão complexo como uma demonstração e não tão trivial como um fragmento ou amostra. Os apps são criados dinamicamente com base nos requisitos do desenvolvedor.

Cada kit do iniciador inclui um idioma, uma estrutura e um padrão para um caso de uso específico. É possível reutilizar o código em vez de reinventá-lo. Se um kit do iniciador requerer serviços específicos, os serviços fornecidos automaticamente estarão disponíveis para que as instâncias para esses serviços sejam criadas automaticamente quando você criar seu app.

## O quanto os kits do iniciador são diferentes das amostras?
{: #compare}

Os kits do iniciador são prontos para produção e focam em demonstrar uma implementação padrão de chave usando um tempo de execução (por exemplo, Node.js e Express). Em alguns casos, os kits do iniciador oferecem uma experiência do usuário simples para destacar a integração do serviço. Em outros casos, os kits do iniciador representam uma implementação customizável de um caso de uso sofisticado.

Um fragmento são algumas linhas de código frequentemente apresentadas em um IDE. Os fragmentos ajudam um desenvolvedor a integrar-se a uma sintaxe de linguagem de programação ou a suportar a integração com uma API definida. Uma demonstração é geralmente alta em qualidade e fidelidade e usa uma gama de serviços e pontos de integração. Ela geralmente requer tempo de configuração e é usada para provar um problema de negócios ou demonstrar um recurso de plataforma. É possível usá-la para avaliar os estágios de adoção de nuvem. Às vezes, esse é o código incluído no código de produção. Uma amostra é um pequeno exemplo de um recurso, uma função, um serviço ou uma jornada de usuário específicos. É possível reutilizar uma amostra ou incluí-la em um aplicativo de produção. Ela é usada geralmente para mostrar recursos técnicos e uma possível abordagem para solucionar um problema técnico.

## Código móvel
{: #portable-code}

A criação de um app por meio de um kit do iniciador cria automaticamente o código que tem um formato consistente e não é dependente do tempo de execução. É possível implementar o código em seu destino de opção, como o Kubernetes ou o Cloud Foundry, sem fazer mudanças.

O código móvel contém o código de ativação de nuvem para múltiplos ambientes de nuvem. É possível produzir código que siga as melhores práticas para um idioma específico e que seja específico para um caso de uso. 

* A lógica de caso de uso fornece funções para a função principal de um caso de uso específico. Os exemplos podem ser código para um robô de bate-papo do Watson Conversation ou código para um app de reconhecimento visual móvel.
* Componentes de linguagem são componentes de código e arquivos específicos da linguagem de programação selecionada para o kit do iniciador. Por exemplo, os programadores de node.js precisam de um arquivo package.json para o gerenciamento de dependência e esse arquivo é criado automaticamente.
* Ativação de serviço é o código que permite que seu app se conecte e use os serviços incluídos. O gerenciamento de credencial, o código de inicialização e os SDKs específicos do serviço são exemplos de itens de ativação de serviço.
* Ativação de nuvem é o código que permite que seu app seja executado no {{site.data.keyword.cloud_notm}}. Por exemplo, os gráficos Helm que permitem que seu app seja executado em um cluster do Kubernetes do {{site.data.keyword.cloud_notm}}.

É possível visualizar seu código do app clicando em **Fazer download do código** na página Detalhes do app de seu app. O código é transferido por download como um arquivo `.zip` que contém a estrutura do código do app completa. É possível extrair o arquivo e executar o código localmente usando o {{site.data.keyword.dev_cli_notm}} ou incluí-lo em seu repositório de gerenciamento de código.

Cada aplicativo inclui um arquivo leia-me que contém detalhes técnicos do app e explica o que é necessário para deixar seu app em execução caso ele não seja executado pronto para utilização.
{: tip}
