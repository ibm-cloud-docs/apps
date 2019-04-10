---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, starter kit, Kubernetes, cluster

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Implementando um app do kit do iniciador para um cluster do Kubernetes
{: #tutorial-starterkit-kube}

Saiba como criar um aplicativo no {{site.data.keyword.cloud}} usando um kit do iniciador vazio e uma cadeia de ferramentas do Kubernetes e entregue continuamente o app para um contêiner seguro em um cluster do Kubernetes. O
pipeline do DevOps de integração contínua pode ser configurado para que suas mudanças de código sejam construídas
automaticamente e propagadas para o app que está no cluster do Kube. Se você já tiver um pipeline, será possível
conectá-lo ao app.
{: shortdesc}

O {{site.data.keyword.cloud_notm}} oferece kits do iniciador que ajudam a construir a base de um app
que é executado no Kubernetes. Ao usar um kit do iniciador, será fácil seguir um modelo de programação nativo de nuvem que usa as {{site.data.keyword.cloud_notm}} melhores práticas para o desenvolvimento de app. Os kits do iniciador geram apps que seguem o modelo de programação nativo de nuvem e incluem casos de teste, verificação
de funcionamento e métricas em cada linguagem de programação. Também é possível fornecer serviços de nuvem que são,
então, inicializados no aplicativo gerado.

Este tutorial usa o destino de implementação do Kubernetes. Neste tutorial, estamos criando um aplicativo por meio de um kit do iniciador básico usando Java + Spring, incluindo uma instância de serviço do Cloudant nele e implementando-o no {{site.data.keyword.cloud_notm}} usando o IBM Kubernetes Service.

Primeiramente, consulte o diagrama de fluxo do iniciador a seguir e suas etapas de visão geral correspondentes.

![Fluxograma do kit do iniciador](../images/starterkit-flow.png) 

## Antes de começar
{: #prereqs-starterkit-kube}

* Crie um app **Java + Spring** usando um [kit do iniciador](/docs/apps/tutorials?topic=creating-apps-tutorial-starterkit).
* Instale a [CLI do {{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).
* Configure o [Docker](https://www.docker.com/get-started){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo").

## Incluindo serviços em seu app
{: #resources-starterkit-kube}

Inclua um serviço {{site.data.keyword.cloud_notm}} em seu aplicativo. As etapas a seguir
fornecem uma instância do Cloudant, criam uma chave de recurso (credenciais) e conecte-a ao app.

1. Na página **Detalhes do app**, clique em **Incluir serviço**.
2. Selecione **Dados** e clique em **Avançar**.
3. Selecione **Cloudant** e clique em **Avançar**.
4. Na página **Incluir Cloudant**, selecione a região (Sul dos EUA), o grupo de recursos
(padrão) e o plano de precificação (Lite, uma instância grátis).
5. Clique em **Criar**. A página **Detalhes do app** é exibida, e a instância do Cloudant é provisionada e ligada a seu app. Observe que a chave de recursos do Cloudant (credenciais) é
incluída no campo **Credenciais**.
6. Opcional. Se você desejar dar uma olhada rápida no código do app depois de incluir serviços, clique em **Fazer download do código**. O código é transferido por download como um arquivo `.zip` que contém a estrutura do código do app completa. É possível extrair facilmente o arquivo e executar o código localmente usando o {{site.data.keyword.dev_cli_notm}} ou incluí-lo em seu repositório de gerenciamento de código.

## Implementando o app usando uma cadeia de ferramentas do DevOps
{: #deploy-starterkit-kube}

Conecte uma cadeia de ferramentas do DevOps ao aplicativo e configure-a para ser implementada em um cluster do
Kubernetes hospedado no serviço {{site.data.keyword.cloud_notm}} Kubernetes.

1. Na página **Detalhes do app**, clique em **Configurar entrega contínua**.
2. Na página **Selecionar um destino de implementação**, selecione **Implementar no IBM Kubernetes Service**.
3. Selecione uma região e um cluster. Se você não tiver um cluster do Kubernetes, clique em **Criar cluster**.
  * Na página **Criar novo cluster**, selecione o local, o tipo de cluster (grátis), insira
um nome de cluster e, em seguida, clique em **Criar cluster**.
  * Se necessário, siga as instruções na tela para obter acesso ao cluster.
  * Aguarde até que o cluster indique **PRONTO** para criar a cadeia de ferramentas. Com a
região **Sul dos EUA**, é possível fornecer um cluster grátis.
  * Retorne para a página **Selecionar um destino de implementação**.
4. Clique em **Avançar**. A página **Configurar cadeia de ferramentas** é exibida.
5. Na página **Configurar cadeia de ferramentas**, insira um nome da cadeia de ferramentas,
selecione uma região, selecione um grupo de recursos e, em seguida, clique em **Criar**. A página **Detalhes do app** é exibida, juntamente com as informações de implementação sobre sua cadeia de ferramentas.

## Visualizando o repositório
{: #view-repo-starterkit-kube}

1. Na página **Detalhes do app**, clique em **Visualizar repositório**. O
repositório Git que o kit do iniciador gerou é exibido.
2. Opcional. Configure o SSH na área de trabalho seguindo as instruções na tela.
3. Opcional. Crie um token de acesso pessoal em sua conta, seguindo as instruções na tela.

## Visualizando as ferramentas, os logs e o histórico da cadeia de ferramentas
{: #view-logs-starterkit-kube}

1. Quando o estágio de implementação é concluído, a página **Detalhes do app** é exibida, juntamente com as informações de implementação sobre sua cadeia de ferramentas.
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
4. No bloco **Implementar estágio**, clique em **Visualizar logs e histórico**.

## Verificando se o seu app está em execução
{: #verify-starterkit-kube}

Após você implementar o seu app, o Delivery Pipeline ou a linha de comandos apontará a você a URL para o seu app.

1. Na cadeia de ferramentas do seu DevOps, clique em **Delivery Pipeline** e, em seguida, selecione **Implementar estágio**.
2. Clique em **Visualizar logs e histórico**.
3. No arquivo de log, localize a URL do aplicativo:

    No término do arquivo de log, procure `View the application health at: http://<ipaddress>:<port>/health`.

4. Acesse a URL em seu navegador. Se o app estiver em execução, uma mensagem que incluirá `Parabéns` ou `{"status":"UP"}` será exibida.

Se você estiver usando a linha de comandos, execute o comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para visualizar a URL de seu app. Em seguida, acesse a URL em seu navegador.

## Próximas Etapas
{: #next-steps-startkit-kube notoc}

* Se você encontrar erros com a implementação, verifique o tópico de resolução de problemas para problemas
conhecidos como [cota de armazenamento excedida](/docs/apps?topic=creating-apps-managingapps#exceed_quota) ou saiba
como [acessar os logs do Kubernetes](/docs/apps?topic=creating-apps-managingapps#access_kube_logs) para procurar erros.

* Acesse a configuração de serviço no código:
	- É possível usar a anotação _@Value_ ou usar o método _getProperty()_ da classe de
ambiente Spring Framework. Para obter mais informações, consulte
[Acessando as credenciais](/docs/java-spring?topic=java-spring-configuration#accessing-credentials).

* Inclua novas credenciais no ambiente do Kubernetes:
	- Ao incluir outro serviço no aplicativo depois que a cadeia de ferramentas do DevOps é criada, essas
credenciais de serviço não serão automaticamente atualizadas para o aplicativo implementado e o repositório GitLab. Deve-se [incluir manualmente as credenciais](/docs/apps?topic=creating-apps-add-credentials-kube) no ambiente de
implementação.
