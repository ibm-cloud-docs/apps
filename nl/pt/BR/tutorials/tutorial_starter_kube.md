---

copyright:
  years: 2018
lastupdated: "2018-11-26"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Implementando um app do kit do iniciador para um cluster do Kubernetes
{: #tutorial}

Aprenda a criar um app no {{site.data.keyword.cloud}} usando um kit de iniciador em branco e uma cadeia
de ferramentas do Kubernetes e entregue continuamente o app para um contêiner seguro em um cluster do Kubernetes. O
pipeline do DevOps de integração contínua pode ser configurado para que suas mudanças de código sejam construídas
automaticamente e propagadas para o app que está no cluster do Kube. Se você já tiver um pipeline, será possível
conectá-lo ao app.
{: shortdesc}

O {{site.data.keyword.cloud_notm}} oferece kits do iniciador que ajudam a construir a base de um app
que é executado no Kubernetes. Ao usar um kit do iniciador, será fácil seguir um modelo de programação nativo de nuvem que usa as {{site.data.keyword.cloud_notm}} melhores práticas para o desenvolvimento de app. Os kits do iniciador geram apps que seguem o modelo de programação nativo de nuvem e incluem casos de teste, verificação
de funcionamento e métricas em cada linguagem de programação. Também é possível fornecer serviços de nuvem que são,
então, inicializados no aplicativo gerado.

Esse tutorial usa a opção de implementação do Kubernetes. Nesse tutorial, estamos criando um aplicativo por meio
de um kit iniciador básico usando Java + Spring, incluindo uma instância de serviço do Cloudant nele e implementando-o no {{site.data.keyword.cloud_notm}} usando um ambiente do Kubernetes.

Primeiramente, consulte o diagrama de fluxo do iniciador a seguir e suas etapas de visão geral correspondentes.

![Fluxograma do kit do iniciador](../images/starterkit-flow.png) 

## Antes de começar
{: #prereqs}

* Crie um app **Java + Spring** usando um [kit do iniciador](/docs/apps/tutorials/tutorial_starter-kit.html).
* Instale a CLI do [{{site.data.keyword.cloud_notm}} ](/docs/cli/index.html).
* Configure o [Docker
![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.docker.com/get-started){: new_window}.

## Incluindo recursos no app
{: #add_resources}

Inclua um recurso de serviço do {{site.data.keyword.cloud_notm}} no aplicativo. As etapas a seguir
fornecem uma instância do Cloudant, criam uma chave de recurso (credenciais) e conecte-a ao app.

1. Na página **Detalhes do app**, clique em **Incluir recurso**.
2. Selecione **Dados** e clique em **Avançar**.
3. Selecione **Cloudant** e clique em **Avançar**.
4. Na página **Incluir Cloudant**, selecione a região (Sul dos EUA), o grupo de recursos
(padrão) e o plano de precificação (Lite, uma instância grátis).
5. Clique **Criar**. A página **Detalhes do app** é exibida e a
instância do Cloudant é fornecida e ligada ao app. Observe que a chave de recursos do Cloudant (credenciais) é
incluída no campo **Credenciais**.
6. Opcional. Se desejar dar uma olhada rápida no código do app depois de incluir os recursos, clique em **Fazer download do código**. O código é transferido por download como um arquivo `.zip` que contém a estrutura completa do código do app. É possível extrair facilmente o arquivo e executar o código localmente usando o {{site.data.keyword.dev_cli_notm}} ou incluí-lo em seu repositório de gerenciamento de código.

## Implementando o app usando uma cadeia de ferramentas do DevOps
{: #deploy_app}

Conecte uma cadeia de ferramentas do DevOps ao aplicativo e configure-a para ser implementada em um cluster do
Kubernetes hospedado no serviço {{site.data.keyword.cloud_notm}} Kubernetes.

1. Na página **Detalhes do app**, clique em **Implementar na nuvem**.
2. Na página **Escolher um ambiente de implementação **, selecione **Implementar
no Kubernetes**.
3. Selecione uma região e um cluster. Se você não tiver um cluster do Kubernetes, clique em **Criar cluster**.
  * Na página **Criar novo cluster**, selecione o local, o tipo de cluster (grátis), insira
um nome de cluster e, em seguida, clique em **Criar cluster**.
  * Se necessário, siga as instruções na tela para obter acesso ao cluster.
  * Aguarde até que o cluster indique **PRONTO** para criar a cadeia de ferramentas. Com a
região **Sul dos EUA**, é possível fornecer um cluster grátis.
  * Retorne para a página **Escolher um ambiente de implementação**.
4. Clique em **Avançar**. A página **Configurar cadeia de ferramentas** é exibida.
5. Na página **Configurar cadeia de ferramentas**, insira um nome da cadeia de ferramentas,
selecione uma região, selecione um grupo de recursos e, em seguida, clique em **Criar**. A página **Detalhes do app** é exibida, juntamente com as informações de implementação sobre a cadeia de ferramentas.

## Visualizando o repositório
{: #view_repo}

1. Na página **Detalhes do app**, clique em **Visualizar repositório**. O
repositório Git que o kit do iniciador gerou é exibido.
2. Opcional. Configure o SSH na área de trabalho seguindo as instruções na tela.
3. Opcional. Crie um token de acesso pessoal em sua conta, seguindo as instruções na tela.

## Visualizando as ferramentas, os logs e o histórico da cadeia de ferramentas
{: #view_logs}

1. Quando o estágio de implementação for concluído, a página **Detalhes do app** será exibida, juntamente com as informações de implementação sobre a cadeia de ferramentas.
2. Acesse a cadeia de ferramentas clicando em **Visualizar cadeia de ferramentas**. A guia **Visão geral** da página da cadeia de ferramentas é exibida, que mostra as ferramentas que são
incluídas com a cadeia de ferramentas. Esse exemplo inclui as seguintes ferramentas que foram pré-selecionadas no kit do
iniciador quando a cadeia de ferramentas foi criada:
  * Um rastreador de problemas para rastrear as atualizações e as mudanças do projeto.
  * Um repositório Git que contém o código-fonte do aplicativo.
  * Uma instância do Eclipse Orion, que é um IDE baseado na web para editar o aplicativo.
  * Um Delivery Pipeline que consiste em uma construção customizável e um estágio de implementação.
	 * O estágio CONSTRUÇÃO insere o app em contêiner. Mais especificamente, o estágio de construção:
	   * Clona o repositório GitLab.
	   * Constrói o app.
	   * Constrói a imagem do Docker.
	   * Publica a imagem no registro de contêiner privado.
	 * O estágio IMPLEMENTAÇÃO recupera a imagem do contêiner do registro de contêiner e, em seguida,
implementa-a no cluster do Kubernetes.
3. Clique em **Delivery Pipeline**. Os estágios de pipeline são exibidos.
4. No estágio IMPLEMENTAÇÃO, clique em **Visualizar os logs e o histórico**.
5. No final do log, procure por `VIEW THE APPLICATION AT: http://<ipaddress>:<port>`, que é a
URL na qual é possível acessar o aplicativo.
6. Acesse o terminal `/health` em `http://<ipaddress>:<port>/health`. Se o
aplicativo estiver em execução no cluster, uma mensagem que inclui `{"status":"UP"}` será exibida.

Se você encontrar erros com a implementação, verifique o tópico de resolução de problemas para problemas
conhecidos como [cota de armazenamento excedida](/docs/apps/ts_apps.html#exceed_quota) ou saiba
como [acessar os logs do Kubernetes](/docs/apps/ts_apps.html#access_kube_logs) para procurar erros.

## Próximas Etapas
{: #next_steps notoc}

* Acesse a configuração de serviço no código:
	- É possível usar a anotação _@Value_ ou usar o método _getProperty()_ da classe de
ambiente Spring Framework. Para obter mais informações, consulte
[Acessando as credenciais](/docs/java-spring/configuration.html#configuration#accessing-credentials).

* Inclua novas credenciais no ambiente do Kubernetes:
	- Ao incluir outro serviço no aplicativo depois que a cadeia de ferramentas do DevOps é criada, essas
credenciais de serviço não serão automaticamente atualizadas para o aplicativo implementado e o repositório GitLab. Deve-se [incluir manualmente as credenciais](/docs/apps/creds_kube.html#sk_kube) no ambiente de
implementação.
