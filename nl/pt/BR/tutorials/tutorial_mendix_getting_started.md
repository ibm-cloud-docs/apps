---

copyright:
  years: 2018
lastupdated: "2018-11-13"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Criando os aplicativos com o Mendix
{: #getting-started}

Mendix é um ambiente de desenvolvimento de pouco código e um conjunto de ferramentas que ajuda a entregar aplicativos com vários dispositivos mais rapidamente, com menos recursos de desenvolvimento e que executam no {{site.data.keyword.cloud}}. Ao selecionar um kit do iniciador de pouco código do Mendix, você é orientado para configurar da conta na plataforma Mendix, iniciar o projeto e selecionar o ambiente de implementação no cluster do Cloud Foundry ou do Kubernetes.
{: shortdesc}

## Selecionando um kit do iniciador
{: #select-a-starter-kit}

2. No painel do [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/dashboard){: new_window}, clique no ícone **Menu** ![Ícone Menu](../../icons/icon_hamburger.svg).
3. Selecione um kit do iniciador de pouco código do Mendix em uma das seguintes categorias:
  * [Móvel![ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/developer/appservice/starter-kits/mendix-mobile-app)
  * [Aplicativo móvel ou da web do Watson ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson)
  * [Aplicativo da web ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/developer/appservice/starter-kits/mendix-web-app)
4. Clique em  ** Criar app **.
5. Nomeie o aplicativo. 
6. Clique em **Criar**.

## Autorizando a IBM a criar o projeto em Mendix e vincular as contas
{: #link-mendix-account}

Se você ainda não estiver usando o Mendix com o {{site.data.keyword.cloud_notm}}, será guiado para a plataforma Mendix para se inscrever e autorizar o {{site.data.keyword.cloud_notm}} a criar um novo projeto na plataforma Mendix em seu nome. Esse projeto é vinculado ao {{site.data.keyword.cloud_notm}}, portanto, as implementações são direcionadas automaticamente para o {{site.data.keyword.cloud_notm}}.

1. Se você vir esta mensagem: "Para concluir a criação do aplicativo, uma conta do usuário do Mendix é necessária. Gostaria de vincular a conta agora?", deverá clicar em **Vincular conta**.
2. Na página de confirmação do Mendix, selecione **Eu concordo com a política de privacidade e os termos do Mendix** e clique em **Confirmar**.
3. Quando solicitado, forneça o endereço de e-mail, a senha e o país e, em seguida, clique em **Criar**.
4. Na página **Autorizar acesso à conta do Mendix**, clique em **Autorizar**.

Após a conclusão da autorização, o navegador retorna ao aplicativo Mendix que você está criando. A página **Escolher um ambiente de implementação** é exibida.

## Selecionando uma opção de implementação para o aplicativo Mendix
{: #select-deployment}

1. Na página **Escolher um ambiente de implementação**, selecione Cloud Foundry ou um dos clusters do Kubernetes que estão em execução no {{site.data.keyword.cloud_notm}}.
2. Opcional. Se você não tem um cluster do Kubernetes, é possível criar um agora.
3. Na página **Configurar a cadeia de ferramentas**, selecione a região e o grupo de recursos e, em seguida, clique em **Criar**.

Uma cadeia de ferramentas do DevOps é criada. A cadeia de ferramentas integra o projeto Mendix dentro da plataforma Mendix no ambiente do {{site.data.keyword.cloud_notm}}. Um aplicativo padrão é implementado na implementação de destino para que seja possível verificar se o aplicativo foi implementado com êxito na conclusão da cadeia de ferramentas do DevOps.

As implementações do Mendix Cloud Foundry requerem o serviço de banco de dados PostGRES, que não tem uma camada Lite. Se desejar avaliar os kits do iniciador do Mendix usando uma conta Lite, será possível destinar um cluster do Kubernetes de teste.
{: tip}

Se você selecionou um cluster do Kubernetes para implementação, consulte o [Tutorial do Kubernetes do Mendix](/docs/apps/tutorials/tutorial_mendix_kubernetes.html) para saber como configurar o cluster para o uso de produção.


## Continuando o desenvolvimento do Mendix e o ciclo de vida de implementação
{: #development-lifecycle}

Mendix é um ambiente de criação de pouco código. O ciclo de vida de desenvolvimento requer que o projeto seja aberto no aplicativo para desktop do Mendix Modeler.

1. No aplicativo {{site.data.keyword.cloud_notm}}, clique em **Editar no Mendix**.
2. No portal da web do Mendix, clique em **Editar no Desktop Modeler**.
  O aplicativo Mendix é aberto no Desktop Modeler.
3. Edite o aplicativo Mendix e salve as mudanças.
4. Use o menu **Executar** do aplicativo Mendix Desktop Modeler e selecione a opção **Executar**.
  O pacote de implementação é criado e transferido por upload para o Mendix. Após a criação do pacote de implementação, é possível implementar o aplicativo no {{site.data.keyword.cloud_notm}}.
5. Para implementar o aplicativo Mendix, volte para a página **Detalhes do aplicativo** no {{site.data.keyword.cloud_notm}} e clique em **Implementar aplicativo**.
  Essa ação inicia a cadeia de ferramentas do DevOps do aplicativo, que puxa a implementação mais recente do Mendix e a implementa no ambiente de destino. Após a conclusão da implementação, a versão mais recente do aplicativo
inicia automaticamente e se torna disponível.

Todos os aplicativos Mendix devem ser implementados no {{site.data.keyword.cloud_notm}} clicando em **Implementar aplicativo** na página **Detalhes do aplicativo** no {{site.data.keyword.cloud_notm}}. Não chame manualmente as cadeias de ferramentas do Mendix por meio da interface do IBM DevOps. A ativação manual das cadeias de ferramentas por meio da interface do DevOps pode resultar em uma implementação com falha devido à falta de metadados necessários que são críticos para as implementações do Mendix. Dependendo do estado do aplicativo, uma falha durante a ativação da cadeia de ferramentas do DevOps ou um erro no aplicativo implementado pode ocorrer. Se você ativar manualmente uma cadeia de ferramentas e tiver uma falha, será possível restaurar a implementação do aplicativo clicando em **Implementar aplicativo** na página **Detalhes do aplicativo** no {{site.data.keyword.cloud_notm}}. Essa ação aciona um fluxo do DevOps completo para o aplicativo Mendix, que inclui os metadados necessários.
{: tip}

## Próximas Etapas 
{: #next steps}

Para implementar o aplicativo para o {{site.data.keyword.containerlong_notm}}, configure-o para a implementação de produção. Para obter informações adicionais, consulte o [Tutorial do Kubernetes do Mendix](/docs/apps/tutorials/tutorial_mendix_kubernetes.html). 
