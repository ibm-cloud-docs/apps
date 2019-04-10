---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-18"

keywords: apps, mobile, mobile application, starter kit, developer tools, DevOps toolchain, toolchain, cli

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# Criando um aplicativo móvel com um kit do iniciador
{: #tutorial-mobile}

O {{site.data.keyword.cloud}} oferece kits do iniciador móvel para ajudar a criar um aplicativo móvel rapidamente. Selecione uma linguagem, uma estrutura e ferramentas dos Kits do iniciado do App Service para começar a trabalhar com um app customizado pré-configurado. Neste tutorial, é possível aprender a instalar as ferramentas necessárias, além de construir e executar o app localmente e implementá-lo na nuvem.
{: shortdesc}

## Etapa 1. Antes de Iniciar
{: #prereqs-mobile}

* Instale o [{{site.data.keyword.dev_cli_short}}](/docs/cli?topic=cloud-cli-ibmcloud-cli).
* O Docker é instalado como parte das ferramentas do desenvolvedor. O Docker deve estar em execução para que os comandos de construção funcionem. Deve-se criar uma conta do Docker, executar o app Docker e conectar-se.
* Se você planeja implementar seu app no [{{site.data.keyword.cfee_full}}](/docs/cloud-foundry?topic=cloud-foundry-about), deve-se [preparar sua conta do {{site.data.keyword.cloud_notm}}](/docs/cloud-foundry?topic=cloud-foundry-prepare).

## Etapa 2. Criar um app usando o {{site.data.keyword.dev_console}}
{: #create-mobile}

1. Crie um app {{site.data.keyword.dev_console}} no {{site.data.keyword.cloud_notm}}.
2. Na página [Kits do iniciador ](https://{DomainName}/developer/appservice/starter-kits/){: new_window} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo") no {{site.data.keyword.dev_console}}, selecione um kit do iniciador com base nos recursos desejados. Por exemplo, para um aplicativo Watson Language, selecione **Swift Kitura**.
3. Insira o nome de seu app. Para este tutorial, use `WatsonApp`.
4. Opcional. Forneça identificações para classificar o seu app. Para obter mais informações, consulte [Trabalhando com tags](/docs/resources?topic=resources-tag).
5. Selecione a plataforma da linguagem. Para este tutorial, use `Swift`.
6. Selecione a linguagem e a estrutura. Alguns kits do iniciador podem estar disponíveis apenas em uma linguagem.
7. Selecione seu plano de precificação. Há uma opção grátis que pode ser usada para este tutorial.
8. Clique em **Criar**.

## Etapa 3. Incluir serviços (opcional)
{: #resources-mobile}

É possível incluir serviços que aprimoram seu app com o poder cognitivo do Watson, incluir serviços remotos ou serviços de segurança. Para este tutorial, inclua um local para gerenciar seus dados.

1. Na página **Detalhes do app**, clique em **Incluir serviço**.
2. Selecione o tipo de serviço desejado. Por exemplo, selecione **Dados** > **Avançar** > **Cloudant** > **Avançar**.
3. Selecione seu plano de precificação. Há uma opção grátis que pode ser usada para este tutorial.
4. Clique em **Criar**.

## Etapa 4. Criar uma cadeia de ferramentas do DevOps
{: #toolchain-mobile}

A ativação de uma cadeia de ferramentas cria um ambiente de desenvolvimento baseado em equipe para seu app. Quando você cria uma cadeia de ferramentas, o serviço de app cria um repositório Git, no qual é possível visualizar o código-fonte, clonar seu app e criar e gerenciar problemas. Você também tem acesso a um ambiente de laboratório Git dedicado e a um pipeline de entrega contínua. Eles são customizados para o destino de implementação que você escolher, seja ele [Kubernetes](/docs/containers?topic=containers-getting-started), [Cloud Foundry](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf), [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry/index.html) ou [Virtual Server (VSI)](/docs/vsi?topic=virtual-servers-getting-started-with-virtual-servers).

Todas as cadeias de ferramentas criadas por meio de um Painel do desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.
{: note}

1. Na página **Detalhes do app**, clique em **Configurar entrega contínua**.
2. Selecione um destino de implementação. Configure o destino de implementação de acordo com as instruções para o destino que você seleciona:
  * **Implementar no [IBM Kubernetes Service](/docs/apps/deploying?topic=creating-apps-containers-kube)**. Essa opção cria um cluster de hosts, chamados de nós do trabalhador, para implementar e gerenciar contêineres de aplicativo altamente disponíveis. É possível criar um cluster ou implementar em um cluster existente.
  * **Implemente no Cloud Foundry**. Essa opção implementa o seu app nativo de nuvem sem você precisar gerenciar a infraestrutura subjacente. Se a sua conta tiver acesso ao {{site.data.keyword.cfee_full_notm}}, será possível selecionar um tipo de implementador do **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)** ou do **[Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**, que é possível usar para criar e gerenciar ambientes isolados para hospedar aplicativos do Cloud Foundry exclusivamente para a sua empresa.
  * **Implemente em um [Servidor virtual](/docs/apps?topic=creating-apps-vsi-deploy)**. Essa opção provisiona uma instância de servidor virtual, carrega uma imagem que inclui o seu app, cria uma cadeia de ferramentas do DevOps e inicia o primeiro ciclo de implementação para you.ture.

## Etapa 5. Criar e executar o app localmente
{: #build-run-mobile}

A implementação de seu app na nuvem na última etapa criou uma cadeia de ferramentas. Uma cadeia de ferramentas cria um repositório Git para seu app no qual é possível localizar o código. Siga estas etapas para acessar o repositório. É possível construir o app localmente para teste antes de enviá-lo por push para a nuvem.

1. Na página **Detalhes do app**, clique em **Fazer download do código** ou **Clonar seu repositório** para trabalhar com seu código localmente.
2. Importe o app para seu ambiente de desenvolvimento integrado.
3. Modifique o código.
4. Configure a [Autenticação Git](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-git_working#git_authentication) incluindo um token de acesso pessoal.
5. Efetue login na interface da linha de comandos do {{site.data.keyword.cloud_notm}}. Se a sua organização usar logins federados, use a opção `-sso`.

  ```bash
  ibmcloud login -sso
  ```
  {: pre}

6. Configure seus destinos de organização e espaço.

  ```bash
  ibmcloud target --cf
  ```
  {: pre}

7.  Obtenha as credenciais.

  ```bash
  ibmcloud dev get-credentials
  ```
  {: pre}

8. Verifique se o Docker está executando e crie seu app em um contêiner de desenvolvimento local do diretório.

  ```bash
  ibmcloud dev build
  ```
  {: pre}

9. Execute seu app em um contêiner de desenvolvimento local.

  ```bash
  ibmcloud dev run
  ```
  {: pre}

10.  Abra seu navegador para `http://localhost:3000`. Seu número de porta pode ser diferente, dependendo do tempo de execução escolhido.

### Executando seu app Swift no Xcode
{: #run_swift}

1. Abra o arquivo `README.md` em um visualizador de redução de preço para revisar as etapas para configurar seu app.
2. Abra seu terminal e navegue para sua pasta de app e execute os comandos a seguir:
    1. Execute `pod setup` se precisar configurar o repositório do CocoaPods.
    2. Execute `pod update` se precisar atualizar os pods existentes.
    3. Execute `pod install` para instalar os pods para seu app.
3. Abra sua área de trabalho do Xcode `<appname>.xcworkspace`.
4. Execute seu app.

### Executando seu app Cordova no Xcode
{: #run_cordova_xcode}

Se você optar por usar o Cordova como sua linguagem de implementação, siga estas instruções.

1. Abra o arquivo `README.md` em um visualizador de Markdown para configurar seu app.
2. Abra seu app `platforms/ios` no Xcode.
3. Execute seu app.

### Executando seu app Cordova no Android Studio
{: #run_cordova_studio}

Use essa seção se você escolher usar o Cordova como plataforma do seu app móvel.

1. Extraia o arquivo `BasicProject-Cordova.zip`.
2. Abra o arquivo `README.md` em um visualizador de Markdown para configurar seu app.
3. Abra seu app `platforms/android` no Android Studio.
4. Execute seu app.

### Executando seu app Android no Android Studio
{: #run_android}

Use esta seção se você escolher usar o Android como plataforma do seu app móvel.

1. Abra o arquivo `README.md` em um visualizador de Markdown para configurar seu app.
2. Abra seu app `BasicProject-Android` no Android Studio.
3. Execute seu app.

## Etapa 6. Implementar seu app
{: #deploy-mobile}

### Implementar usando uma cadeia de ferramentas
{: #deploy-mobile-toolchain}

É possível implementar seu app no {{site.data.keyword.cloud_notm}} de várias maneiras, mas uma cadeia de ferramentas do DevOps é a melhor maneira de implementar apps de produção. Com uma cadeia de ferramentas do DevOps, é possível automatizar facilmente implementações para muitos ambientes e incluir rapidamente serviços de monitoramento, criação de log e alerta para ajudar a gerenciar seu app à medida que ele cresce.

Com uma cadeia de ferramentas configurada corretamente, um ciclo de construção-implementação se inicia automaticamente com cada mesclagem na ramificação Principal em seu repositório. Todas as cadeias de ferramentas criadas por meio de um painel do desenvolvedor do {{site.data.keyword.cloud_notm}} são configuradas para implementação automática.

Também é possível implementar seu app manualmente por meio de sua cadeia de ferramentas DevOps:

1. Na página **Detalhes do app**, clique em **Visualizar cadeia de ferramentas**.

2. Clique em **Delivery Pipeline**, no qual é possível iniciar construções, gerenciar a implementação e visualizar logs e histórico.

### Implementar usando o {{site.data.keyword.dev_cli_short}}
{: #deploy-mobile-cli}

Para implementar seu app para o Cloud Foundry, insira o comando a seguir:

```
ibmcloud dev deploy
```
{: pre}

Para implementar seu app em um cluster do Kubernetes, insira o comando a seguir:

```
ibmcloud dev deploy --target <container>
```
{: pre}

## Etapa 7. Verificar se o app está em execução
{: #verify-mobile}

Após você implementar o seu app, o Delivery Pipeline ou a linha de comandos apontará a você a URL para o seu app.

1. Na cadeia de ferramentas do seu DevOps, clique em **Delivery Pipeline** e, em seguida, selecione **Implementar estágio**.
2. Clique em **Visualizar logs e histórico**.
3. No arquivo de log, localize a URL do aplicativo:

    No término do arquivo de log, procure a palavra `urls` ou `view`. Por exemplo, é possível que você veja uma linha no arquivo de log que seja semelhante a `urls: my-app-devhost.mybluemix.net` ou `View the application health at: http://<ipaddress>:<port>/health`.

4. Acesse a URL em seu navegador. Se o app estiver em execução, uma mensagem que incluirá `Parabéns` ou `{"status":"UP"}` será exibida.

Se você estiver usando a linha de comandos, execute o comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view) para visualizar a URL de seu app. Em seguida, acesse a URL em seu navegador.
