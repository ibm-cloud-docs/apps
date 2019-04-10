---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, Mendix, starter kit, developer tools, Mendix app

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Criando os aplicativos com o Mendix
{: #create-mendix}

Mendix é um ambiente de desenvolvimento de pouco código e um conjunto de ferramentas que ajuda a entregar aplicativos com vários dispositivos mais rapidamente, com menos recursos de desenvolvimento e que executam no {{site.data.keyword.cloud}}. Ao selecionar um kit do iniciador de código baixo Mendix, você é orientado a configurar sua conta na Mendix Platform, iniciar seu projeto e selecionar o destino de implementação do Cloud Foundry ou do cluster do Kubernetes.
{: shortdesc}

## Selecionando um kit do iniciador
{: #starterkit-mendix}

1. No [painel do {{site.data.keyword.cloud_notm}} App Service](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo"), clique em **Introdução**.
2. Selecione um kit do iniciador de pouco código do Mendix em uma das seguintes categorias:
  * [Móvel](https://{DomainName}/developer/appservice/starter-kits/mendix-mobile-app){: new_window} ![ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")
  * [Aplicativo móvel ou da web do Watson ](https://{DomainName}/developer/appservice/starter-kits/mendix-web-or-mobile-app-with-watson){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")
  * [Aplicativo da web ](https://{DomainName}/developer/appservice/starter-kits/mendix-web-app){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")
3. Clique em  ** Criar app **.
4. Na página **Detalhes do app**, nomeie o seu app e, opcionalmente, forneça identificações para classificar o seu app. Para obter mais informações, consulte [Trabalhando com tags](/docs/resources?topic=resources-tag).
5. Clique em **Criar**.


## Autorizando a IBM a criar o projeto em Mendix e vincular as contas
{: #link-mendix-account}

Se você ainda não estiver usando o Mendix com o {{site.data.keyword.cloud_notm}}, será guiado para a plataforma Mendix para se inscrever e autorizar o {{site.data.keyword.cloud_notm}} a criar um novo projeto na plataforma Mendix em seu nome. Esse projeto é vinculado ao {{site.data.keyword.cloud_notm}}, portanto, as implementações são direcionadas automaticamente para o {{site.data.keyword.cloud_notm}}.

1. Se você vir esta mensagem: "Para concluir a criação do aplicativo, uma conta do usuário do Mendix é necessária. Gostaria de vincular a conta agora?", deverá clicar em **Vincular conta**.
2. Na página de confirmação do Mendix, selecione **Eu concordo com a política de privacidade e os termos do Mendix** e clique em **Confirmar**.
3. Quando solicitado, forneça o endereço de e-mail, a senha e o país e, em seguida, clique em **Criar**.
4. Na página **Autorizar acesso à conta do Mendix**, clique em **Autorizar**.

Após a conclusão da autorização, o navegador retorna ao aplicativo Mendix que você está criando. A página **Selecionar um destino de implementação** é exibida.

## Selecionando um destino de implementação para o app Mendix
{: #select-deployment}

1. Na página **Selecionar um destino de implementação**, selecione o Cloud Foundry ou um de seus clusters Kubernetes que esteja em execução no {{site.data.keyword.cloud_notm}}. Se a sua conta tiver acesso ao {{site.data.keyword.cfee_full_notm}}, será possível selecionar um tipo de implementador do Cloud Foundry do **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)** ou do **[Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**, que é possível usar para criar e gerenciar ambientes isolados para hospedar aplicativos do Cloud Foundry exclusivamente para a sua empresa.
2. Opcional. Se você não tem um cluster do Kubernetes, é possível criar um agora.
3. Na página **Configurar a cadeia de ferramentas**, selecione a região e o grupo de recursos e, em seguida, clique em **Criar**.

Uma cadeia de ferramentas do DevOps é criada. A cadeia de ferramentas integra o projeto Mendix dentro da plataforma Mendix no ambiente do {{site.data.keyword.cloud_notm}}. Um aplicativo padrão é implementado em seu destino de implementação para que seja possível verificar se o aplicativo foi implementado com êxito na conclusão da cadeia de ferramentas do DevOps.

As implementações do Mendix Cloud Foundry requerem o serviço de banco de dados PostGRES, que não tem uma camada Lite. Se desejar avaliar os kits do iniciador do Mendix usando uma conta Lite, será possível destinar um cluster do Kubernetes de teste.
{: tip}

Se você selecionou um cluster do Kubernetes para implementação, consulte o [Tutorial do Kubernetes do Mendix](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube) para saber como configurar o cluster para o uso de produção.


## Continuando o desenvolvimento do Mendix e o ciclo de vida de implementação
{: #dev-lifecycle-mendix}

Mendix é um ambiente de criação de pouco código. O ciclo de vida de desenvolvimento requer que o projeto seja aberto no aplicativo para desktop do Mendix Modeler.

1. No aplicativo {{site.data.keyword.cloud_notm}}, clique em **Editar no Mendix**.
2. No portal da web do Mendix, clique em **Editar no Desktop Modeler**.
  O aplicativo Mendix é aberto no Desktop Modeler.
3. Edite o aplicativo Mendix e salve as mudanças.
4. Use o menu **Executar** do aplicativo Mendix Desktop Modeler e selecione a opção **Executar**.
  O pacote de implementação é criado e transferido por upload para o Mendix. Após a criação do pacote de implementação, é possível implementar o aplicativo no {{site.data.keyword.cloud_notm}}.
5. Para implementar o aplicativo Mendix, volte para a página **Detalhes do app** no {{site.data.keyword.cloud_notm}} e clique em **Implementar**.
  Essa ação inicia a cadeia de ferramentas do DevOps do aplicativo, que puxa a implementação mais recente do Mendix e a implementa no ambiente de destino. Após a conclusão da implementação, a versão mais recente do aplicativo
inicia automaticamente e se torna disponível.

Todos os aplicativos Mendix devem ser implementados no {{site.data.keyword.cloud_notm}} clicando em **Configurar entrega contínua** na página **Detalhes do app** no {{site.data.keyword.cloud_notm}}. Não chame manualmente as cadeias de ferramentas do Mendix por meio da interface do IBM DevOps. A ativação manual das cadeias de ferramentas por meio da interface do DevOps pode resultar em uma implementação com falha devido à falta de metadados necessários que são críticos para as implementações do Mendix. Dependendo do estado do aplicativo, uma falha durante a ativação da cadeia de ferramentas do DevOps ou um erro no aplicativo implementado pode ocorrer. Se você ativar manualmente uma cadeia de ferramentas e tiver uma falha, será possível restaurar a implementação do aplicativo clicando em **Configurar entrega contínua** na página **Detalhes do app** no {{site.data.keyword.cloud_notm}}. Essa ação aciona um fluxo do DevOps completo para o aplicativo Mendix, que inclui os metadados necessários.
{: tip}

## Próximas Etapas 
{: #next-steps-mendix}

Para implementar o aplicativo para o {{site.data.keyword.containerlong_notm}}, configure-o para a implementação de produção. Para obter mais informações, consulte o [Tutorial do Mendix Kubernetes](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube). 
