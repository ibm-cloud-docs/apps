---

copyright:
  years: 2018
lastupdated: "2018-11-14"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Desenvolvimento de app
{: #intro}

O {{site.data.keyword.cloud_notm}} Developer Console ajuda os desenvolvedores a criar apps por meio de kits do iniciador, provisionar e conectar serviços chave otimizados pelo {{site.data.keyword.cloud_notm}} e, em seguida, fazer download rapidamente do código de trabalho ou configurar a entrega contínua. É possível criar, visualizar, configurar e gerenciar seu app e fazer download do código do app. O uso de kits do iniciador ajuda você a avaliar rapidamente e testar os serviços do {{site.data.keyword.cloud_notm}} com um aplicativo de amostra.
{:shortdesc}

## O que é um kit do iniciador?
{: #starter_kits}

Os kits do iniciador são ótimos para montar dinamicamente, na linguagem de sua escolha, um app de produção de estrutura básica pronto para implementação na nuvem. Cada kit do iniciador tem uma linguagem, uma estrutura e um padrão para um caso de uso real específico. É possível reutilizar o código em vez de reinventá-lo.

### Comparando amostras e kits do iniciador

Os desenvolvedores frequentemente confiam no código pré-gravado, como fragmentos, demonstrações e amostras. Como é possível dizer a diferença entre fragmentos, demonstrações e amostras e kits do iniciador do {{site.data.keyword.cloud_notm}}?

* **Fragmento** - algumas linhas do código que é frequentemente apresentado em um IDE. Os fragmentos ajudam um desenvolvedor a integrar-se a uma sintaxe de linguagem de programação ou a suportar a integração com uma API definida.

* **Demonstração** - código que é geralmente de alta qualidade, alta fidelidade e usa um intervalo de serviços e pontos de integração. Ele geralmente requer configuração e é usado para provar um problema de negócios ou demonstrar um recurso de plataforma. As demonstrações podem avaliar os estágios de adoção de nuvem. Às vezes, seu código é incluído no código de produção.

* **Amostra** - código que é um pequeno exemplo de um recurso, uma função, um serviço ou uma jornada do usuário específicos. Uma amostra pode ser reutilizada ou incluída em um aplicativo de produção. É possível usar amostras para mostrar recursos técnicos e possíveis abordagens para resolver problemas técnicos.

* **Kit do iniciador do {{site.data.keyword.cloud_notm}}** - os kits do iniciador são padrões prontos para produção que podem ser integrados a um conjunto de serviços para gerar um ativo pronto para produção. Em seguida, é possível implementá-los diretamente em um pipeline do DevOps e um cluster do Kubernetes. Um kit do iniciador tem metadados descritivos que fornecem informações suficientes para saber o que o kit é e o que ele faz. Ele também tem instruções que dizem ao {{site.data.keyword.cloud_notm}} o que produzir. A saída pode ser aprimorada ainda mais. O conteúdo do kit do iniciador não é tão complexo quanto uma demonstração, nem tão trivial como um fragmento ou uma amostra. Os kits do iniciador são criados dinamicamente com base em seus requisitos.

  Os kits do iniciador mostram a implementação de padrão de chave com um tempo de execução, por exemplo, Swift e Kitura. Eles podem incluir uma experiência do usuário simples para destacar a integração do serviço. Os kits do iniciador são implementações customizáveis de um caso de uso sofisticado.

  Os kits do iniciador incluem instruções que permitem que o {{site.data.keyword.cloud_notm}} produza automaticamente projetos de app com andaime com código móvel. Eles também especificam recursos para serem provisionados automaticamente quando você cria um projeto.

## Recursos autoprovisionados
{: #auto_privisioned_resources}

Se um kit do iniciador especifica os recursos necessários, o {{site.data.keyword.cloud_notm}} cria automaticamente as instâncias desses recursos quando você cria seu projeto. É possível provisionar recursos manualmente ou selecionar instâncias de recurso existentes para aumentar o seu projeto depois que ele é criado. É possível ver uma lista de instâncias de serviço que estão associadas ao seu projeto na visualização *Detalhes do projeto*, junto com as credenciais no caso de precisar delas.

## Gerando código móvel
{: #portable_code}

A criação de um app por meio de um kit do iniciador produz automaticamente um código com um formato consistente e independente de tempo de execução. É possível implementar o código em seu ambiente de preferência, por exemplo, Kubernetes ou Cloud Foundry, sem fazer mudanças.

O projeto inclui um arquivo `README` que tem detalhes técnicos do projeto e explica o que é necessário para que seu app esteja pronto para execução.

Para obter mais informações, veja o console do desenvolvedor do [{{site.data.keyword.cloud_notm}} para os recursos para aprendizado da Apple](https://cloud.ibm.com/developer/appledevelopment/learning-resources).
{: tip}

### Qual conteúdo do app é produzido?
{: #content}

O código que o kit do iniciador do {{site.data.keyword.cloud_notm}} produz tem quatro componentes fundamentais: lógica de caso de uso, componentes de linguagem, ativação de serviço e ativação de nuvem. Gerar esses componentes economiza um tempo valioso e assegura que você use a melhor arquitetura da classe.

* **Lógica de caso de uso** é o código para um caso de uso específico. Os exemplos incluem um código para um robô de bate-papo do Watson Conversation ou um código voltado para um app de reconhecimento visual móvel.
* **Componentes de linguagem** são componentes de código e arquivos específicos para a linguagem selecionada para o seu kit do iniciador. Por exemplo, os programadores do node.js precisam de um arquivo `package.json` para gerenciamento de dependência, e esse arquivo é criado automaticamente pelo {{site.data.keyword.cloud_notm}} Developer Experience.
* **Ativação de serviço** é o código que permite que seu app conecte o projeto e use os serviços que você incluiu nele. Exemplos de itens de ativação de serviço são gerenciamento de credencial, código de inicialização e SDKs específicos do serviço.
* **Ativação de nuvem** é o código que permite que seu app seja executado no {{site.data.keyword.cloud_notm}}. Por exemplo, os gráficos do Helm que permitem que o seu app seja executado em um cluster do Kubernetes do {{site.data.keyword.cloud_notm}} ficariam na categoria de ativação de nuvem.

O app que o {{site.data.keyword.cloud_notm}} produz é bom em relação à arquitetura e modela as melhores práticas para a linguagem escolhida para o projeto. Para ver detalhes sobre os arquivos e a estrutura de um projeto de app, veja os tópicos a seguir.

* [Arquivos de app Java](/docs/apps/projects/java_project_contents.html)
* [Arquivos de app Node.js](/docs/apps/projects/node_project_contents.html)
* [Arquivos de app Python](/docs/apps/projects/python_project_contents.html)
* [Arquivos de app Swift](/docs/apps/projects/swift_project_contents.html).
