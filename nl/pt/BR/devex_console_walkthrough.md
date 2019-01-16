---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-11-29"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Passo a passo do console do desenvolvedor do {{site.data.keyword.cloud_notm}}
{: #intro}

<!--I can't see how a customer needs to be walked through the experience without performing a specific task.-->


O {{site.data.keyword.cloud}} Developer Experience permite que um desenvolvedor de aplicativo nativo de nuvem crie um app por meio de uma variedade de kits do iniciador, crie e conecte serviços essenciais otimizados pelo {{site.data.keyword.Bluemix_notm}} e, em seguida, faça download rapidamente do código de trabalho ou configure para entrega contínua. O Developer Experience fornece um conjunto de consoles do desenvolvedor no {{site.data.keyword.Bluemix_notm}} que permitem criar, visualizar, configurar e gerenciar seu app, bem como implementá-lo em um pipeline do devops ou fazer download dele para desenvolvimento local.

Ao criar um app por meio de um console do desenvolvedor do {{site.data.keyword.cloud_notm}}, todas as partes necessárias de seu app são mantidas em sua conta no servidor {{site.data.keyword.cloud_notm}}. Assim, é possível mover-se entre a GUI do console do desenvolvedor e o [{{site.data.keyword.dev_cli_notm}}](/docs/cli/idt/index.html), caso você opte por fazer isso.

Os consoles do desenvolvedor do {{site.data.keyword.cloud_notm}} fornecem um caminho perfeito para construir um app starter pronto para produção para o caso de uso selecionado. Vamos examinar as etapas que podem ser executadas em sua jornada.

<!-- Ready to jump in?  Visit the [{{site.data.keyword.cloud_notm}} Web App developer console](https://{DomainName}/developer/appservice) to get started.
{: tip} -->

##Tela Visão geral
{: #overview_screen}

A tela Visão geral fornece conteúdo que é customizado para o foco do tópico ou do canal do console do desenvolvedor no qual você está trabalhando. Na tela Visão geral, é possível ver a documentação, acessar recursos para aprendizado, procurar serviços, ver kits do iniciador em destaque ou vincular-se a uma coleção maior de kits do iniciador. Clique em `Kits do iniciador` na navegação para entrar na visualização Kits do iniciador.

![Tela Visão geral do console do desenvolvedor](images/overview_screen.png "Tela Visão geral") <br> *Tela Visão geral do console do desenvolvedor*

##Visualização Kits de Inicialização
{: #starter_kits_view}

A visualização Starter Kits mostra a coleta de kits do iniciador específicos para uma área de caso de uso.  É possível clicar em vários links em um cartão do kit do iniciador para ver demonstrações e mais informações. Selecione um kit do iniciador para ir para a visualização Criar novo app.

Em alguns casos, a seleção de um kit do iniciador leva você para mais detalhes sobre o kit do iniciador. Caso esse seja o caso, basta clicar no botão `Criar` para ir para a visualização Criar novo app.{: tip}

![Visualização Kits do iniciador do console do desenvolvedor](images/starter_kits_view.png "Visualização Kits do iniciador") <br> *Visualização Kits do iniciador do console do desenvolvedor*

##Visualização Criar novo app
{: #create_new_project_view}

Na visualização Criar novo app, você nomeará seu app, fornecerá informações de implementação e roteamento e selecionará um idioma. Observe que, à direita, também é possível ver os serviços que serão provisionados automaticamente quando você criar seu app com os planos de precificação e os termos para cada um. Clique em `Create` para ir para a visualização Detalhes do app.  Se você ainda não estiver conectado ao {{site.data.keyword.cloud_notm}}, será necessário fazer isso neste momento.

![Visualização Criar novo app do console do desenvolvedor](images/create_new_project_view.png "Visualização Criar novo app") <br> *Visualização Criar novo app do console do desenvolvedor*

## Visualização Detalhes do Aplicativo
{: #project_details_view}

A visualização Detalhes do app exibe a lista de serviços configurados para seu app. Para cada item na lista, você vê o nome do serviço, os links para outras informações e um botão de *ações* com três pontos alinhados verticalmente. As opções do botão de *ações* são para remover o serviço do app, abrir o painel para o serviço e excluir o serviço. Observe que a remoção de uma instância de serviço remove apenas a associação a esse app e não exclui a instância de serviço. Além disso, observe que as credenciais de serviço são consolidadas nessa visualização para que você não tenha que visitar cada visualização de instância de serviço individual para chegar a ela.

![Visualização Detalhes do app do console do desenvolvedor](images/project_details_view.png "Visualização Detalhes do app") <br> *Visualização Detalhes do app do console do desenvolvedor*

A visualização Detalhes do app também permite incluir serviços novos ou existentes em seu app que não faziam parte do kit do iniciador original. Clique no link `Incluir recurso` na caixa de listagem de serviços para fazer isso. Os serviços disponíveis dependem do tipo de app e dos serviços disponíveis em uma região, portanto, nem todos os serviços estão disponíveis para associação a todos os apps.

![Diálogo Incluir recurso do console do desenvolvedor](images/add_resource_dialog.png "Diálogo Incluir recurso") <br> *Diálogo Incluir recurso do console do desenvolvedor*

Na visualização Detalhes do app, você tem acesso ao seu código de duas maneiras:

*  [Recomendado] Clique no botão `Implementar na nuvem` para enviar por push seu código para um repositório e implementar seu app no {{site.data.keyword.cloud_notm}}. Para obter mais informações sobre a cadeia de ferramentas do DevOps do {{site.data.keyword.cloud_notm}}, clique [aqui](/docs/services/ContinuousDelivery/toolchains_about.html#toolchains_about).
*  Para obter uma visão rápida de seu código de app, selecione `Fazer download do código` para produzir e fazer download do código para seu app.

##Visualização Lista de Aplicativos
{: #project_list_view}

É possível ver uma lista de todos os apps criados na visualização Lista de apps. É possível renomear ou excluir seus apps daí. Clique em uma linha de nome do app para retornar para a visualização Detalhes do app.

![Visualização Lista de apps do console do desenvolvedor](images/project_list_view.png "Visualização Lista de apps") <br> *Visualização Lista de apps do console do desenvolvedor*
