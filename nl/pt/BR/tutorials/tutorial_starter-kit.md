---

copyright:
  years: 2018, 2019
lastupdated: "2019-07-17"

keywords: apps, starter kit, create app starter kit, basic app, simple app

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}
{:note: .note}

# Criando um app com um kit do iniciador
{: #tutorial-starterkit}

É possível usar um kit do iniciador para fazer com que seu aplicativo seja iniciado rapidamente e prepará-lo para desenvolvimento futuro. Selecione o kit do iniciador e a linguagem de programação, crie um app e, em seguida, configure uma cadeia de ferramentas do DevOps para implementar automaticamente seu app.
{: shortdesc}

É possível criar um app por meio de uma seleção de kits do iniciador, incluindo um básico, se você mesmo deseja customizar as opções de construção. De qualquer maneira, uma cadeia de ferramentas do DevOps é criada
automaticamente para a implementação do app. Também é possível fazer download do código para inspeção imediata.

O {{site.data.keyword.cloud_notm}} possui Portais do Desenvolvedor em diferentes áreas de interesse (como o Watson) ou um canal digital (como móvel ou aplicativos da web). É possível acessar esses portais por meio do ícone **Menu** ![Ícone Menu](../../icons/icon_hamburger.svg).

Cada Portal do Desenvolvedor fornece kits do iniciador que são relevantes para a área de foco do portal. Os portais oferecem fluxos de trabalho consistentes e intuitivos para criar um app de trabalho pronto para produção em minutos.

Os kits do iniciador estão disponíveis em várias categorias, incluindo:
* [Watson ](https://{DomainName}/developer/watson/dashboard){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")
* [Apple ](https://{DomainName}/developer/appledevelopment/dashboard){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")
* [Móvel](https://{DomainName}/developer/mobile/dashboard){: new_window} ![ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")
* [Aplicativo da web ](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")

Consulte [O que são kits do iniciador?](/docs/apps?topic=creating-apps-starter-kits) para obter mais informações.

## Etapa 1. Instale as ferramentas
{: #prereqs-starterkit}

* Instale as [ferramentas do desenvolvedor](/docs/cli?topic=cloud-cli-getting-started).
* O Docker é instalado como parte das ferramentas do desenvolvedor. O Docker deve estar em execução para que os comandos de construção funcionem. Deve-se criar uma conta do Docker, executar o app Docker e conectar-se.
* Se você planeja implementar seu app no {{site.data.keyword.cfee_full}}, deve-se [preparar sua conta do {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Etapa 2. Criar um app
{: #create-starterkit}

Há kits do iniciador disponíveis em várias linguagens e estruturas no {{site.data.keyword.cloud_notm}} {{site.data.keyword.dev_console}}. É possível usar os filtros de categoria, como o idioma e o tipo, para limitar a seleção.

1. Na página [kits do iniciador](https://{DomainName}/developer/appservice/starter-kits){: new_window} ![External link icon](../../icons/launch-glyph.svg "External link icon") no console do {{site.data.keyword.dev_console}}, selecione um kit do iniciador e clique em **Criar app**. 

    Para ver o que está incluído no kit do iniciador, selecione o bloco e leia os detalhes. Se você deseja usar um kit do iniciador básico e customizar seu app, selecione o bloco **Criar app**.
    {: tip}

2. Nomeie o app e selecione um grupo de recursos.

3. Opcional. Forneça identificações para classificar o seu app. Para obter mais informações, consulte [Trabalhando com tags](/docs/resources?topic=resources-tag).

4. Selecione a linguagem e a estrutura. Alguns kits do iniciador podem estar disponíveis apenas em uma linguagem.

5. Clique em **Criar**.

Ótimo início! Você acabou de criar um app.

Para inspecionar seu código antes de incluir serviços ou configurar a entrega contínua, clique em **Fazer download do código** na página Detalhes do app. Verifique o arquivo `README.md` no arquivo compactado transferido por download para descobrir se é necessário executar mais ações para colocar seu app em funcionamento.
{: tip}

## Etapa 3. Incluir serviços (opcional)
{: #resources-starterkit}

Se um kit do iniciador exigir serviços específicos, as instâncias de serviço autoprovisionadas serão criadas e conectadas automaticamente ao seu aplicativo.

Também é possível incluir serviços que aprimoram seu app com o poder cognitivo do Watson, incluir serviços móveis ou serviços de segurança. Para este tutorial, inclua um local para gerenciar seus dados.

1. Na página Detalhes do app, clique em **Criar serviço** ou **Conectar serviços existentes**, dependendo de se você já tem serviços que deseja conectar a esse app.
2. Selecione o tipo de serviço que você deseja e siga os prompts para incluir um serviço existente em seu app ou criar uma instância de serviço.

Após a inclusão de todos os serviços que você deseja, eles são exibidos na página Detalhes do app.

## Etapa 4. Selecionar um destino de implementação e configurar a entrega contínua
{: #target-starterkit}

Quando você seleciona um destino de implementação, uma cadeia de ferramentas do DevOps é criada automaticamente para o seu app. A cadeia de ferramentas inclui um Delivery Pipeline que indica o status de implementação de seu app. O novo app gerado é enviado por push para um repositório GitLab que faz parte da cadeia de ferramentas.

A ativação de uma cadeia de ferramentas do DevOps cria um ambiente de desenvolvimento baseado em equipe para seu app. Quando você cria uma cadeia de ferramentas, o serviço de app cria um repositório Git, no qual é possível visualizar o código-fonte, clonar seu app e criar e gerenciar problemas. Você também tem acesso a um ambiente GitLab dedicado e a um pipeline de entrega contínua. Eles são customizados para o destino de implementação selecionado, seja o [Kubernetes](/docs/containers?topic=containers-getting-started), o [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), o [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) ou o [servidor virtual (VSI)](/docs/vsi?topic=virtual-servers-getting-started-tutorial).

Todas as cadeias de ferramentas criadas por meio de um Painel do desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.
{: note}

Para selecionar o destino de implementação e configurar a entrega contínua, conclua estas etapas:

1. Na página Detalhes do app, clique em **Configurar entrega contínua**.
2. Selecione um destino de implementação. Configure o destino de implementação de acordo com as instruções para o destino selecionado:
  * **Implementar no [IBM Kubernetes Service](/docs/containers?topic=containers-app)**. Essa opção cria um cluster de hosts, chamados nós do trabalhador, para implementar e gerenciar contêineres de app altamente disponíveis. É possível criar um cluster ou implementar em um cluster existente.
  * **Implemente no Cloud Foundry**. Essa opção implementa o seu app nativo de nuvem sem você precisar gerenciar a infraestrutura subjacente. Se a sua conta tiver acesso ao {{site.data.keyword.cfee_full_notm}}, será possível selecionar um tipo de implementador do **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-deployingapps)** ou do **[Enterprise Environment](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps)**, que poderá ser usado para criar e gerenciar ambientes isolados para hospedar apps do Cloud Foundry exclusivamente para a sua empresa.
  * **Implementar em um Servidor virtual**. Essa opção provisiona uma instância de servidor virtual, carrega uma imagem que inclui o seu app, cria uma cadeia de ferramentas do DevOps e inicia o primeiro ciclo de implementação para você. Para obter mais informações, consulte [Implementando apps em um servidor virtual](/docs/vsi?topic=virtual-servers-deploying-to-a-virtual-server).

    A implementação de VSI está disponível para alguns kits do iniciador. Para usar esse recurso, acesse o [painel do {{site.data.keyword.cloud_notm}}](https://{DomainName}) e clique em **Criar um app** no bloco **Apps**.
    {: note}

Após a seleção e a configuração do destino de implementação, a página Detalhes do app indica que a entrega contínua está configurada. É possível visualizar o repositório que contém o código-fonte para seu app clicando em **Visualizar repositório**.

## Etapa 5. Implementar seu app
{: #deploy-starterkit}

As cadeias de ferramentas do DevOps criadas por meio do painel do desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.
{: note}

Depois de selecionar seu destino de implementação, abra o componente de pipeline de sua nova cadeia de ferramentas para iniciar o processo de construção e implementação inicial para que você possa ver o seu novo app em minutos.

1. Na página Detalhes do app, clique em **Visualizar cadeia de ferramentas**.
2. Clique em **Delivery Pipeline**, no qual é possível iniciar construções, gerenciar a implementação e visualizar logs e histórico.

Com uma cadeia de ferramentas configurada corretamente, um ciclo de construção/implementação é iniciado automaticamente com cada mesclagem à ramificação principal em seu repositório. Para obter mais informações, consulte [Construindo e implementando](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-deliverypipeline_build_deploy).

É possível implementar seu app por meio da linha de comandos, executando o comando [`ibmcloud dev deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy). Para obter mais informações, consulte [Implementando apps com a CLI](/docs/apps?topic=creating-apps-deploying-apps#deploy-cli).

## Etapa 6. Verificar se o seu app está em execução
{: #verify-starterkit}

Após você implementar o seu app, o Delivery Pipeline ou a linha de comandos apontará a você a URL para o seu app.

1. Na cadeia de ferramentas do seu DevOps, clique em **Delivery Pipeline** e, em seguida, selecione **Implementar estágio**.
2. Clique em **Visualizar logs e histórico**.
3. No arquivo de log, localize a URL do app:

    No término do arquivo de log, procure a palavra `urls` ou `view`. Por exemplo, você pode ver uma linha no arquivo de log que é semelhante a `urls: my-app-devhost.mybluemix.net` ou `View the application health at: http://<ipaddress>:<port>/health`.

4. Acesse a URL em seu navegador. Se o app estiver em execução, uma mensagem que incluirá `Parabéns` ou `{"status":"UP"}` será exibida.

Se você estiver usando a linha de comandos, execute o comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para visualizar a URL de seu app. Em seguida, acesse a URL em seu navegador.
