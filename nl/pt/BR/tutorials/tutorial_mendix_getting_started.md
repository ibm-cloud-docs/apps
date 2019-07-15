---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-03"

keywords: apps, Mendix, starter kit, developer tools, Mendix app, create mendix app

subcollection: creating-apps

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note .note}

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

1. Se você vir esta mensagem, clique em **Vincular conta**.
  ```
  "To complete app creation, a Mendix user account is required. Would you like to link your account now?"
  ```
  {: screen}

2. Na página de confirmação do Mendix, selecione **Eu concordo com a política de privacidade e os termos do Mendix** e clique em **Confirmar**.
3. Quando solicitado, forneça o endereço de e-mail, a senha e o país e, em seguida, clique em **Criar**.
4. Na página **Autorizar acesso à conta do Mendix**, clique em **Autorizar**.

Após a conclusão da autorização, o navegador retorna ao aplicativo Mendix que você está criando. A página **Selecionar um destino de implementação** é exibida.

## Selecionando um destino de implementação para o app Mendix
{: #select-deployment}

1. Na página **Selecionar um destino de implementação**, selecione o Cloud Foundry ou um de seus clusters Kubernetes que esteja em execução no {{site.data.keyword.cloud_notm}}. Se a sua conta tiver acesso ao {{site.data.keyword.cfee_full_notm}}, será possível selecionar um tipo de implementador do Cloud Foundry de **[Public Cloud](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf)** ou **[Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)**, que poderá ser usado para criar e gerenciar ambientes isolados para hospedar apps do Cloud Foundry exclusivamente para a sua empresa.
2. Opcional. Se você não tem um cluster do Kubernetes, é possível criar um agora.
3. Na página **Configurar a cadeia de ferramentas**, selecione a região e o grupo de recursos e, em seguida, clique em **Criar**.

Uma cadeia de ferramentas do DevOps é criada. A cadeia de ferramentas integra o projeto Mendix dentro da plataforma Mendix no ambiente do {{site.data.keyword.cloud_notm}}. Um app padrão é implementado em seu destino de implementação para que seja possível verificar se o app foi implementado com êxito na conclusão da cadeia de ferramentas do DevOps.

As implementações do Mendix Cloud Foundry requerem o serviço de banco de dados PostGRES, que não tem uma camada Lite. Se desejar avaliar os kits do iniciador do Mendix usando uma conta Lite, será possível destinar um cluster do Kubernetes de teste.
{: tip}

Se você selecionou um cluster do Kubernetes para implementação, consulte o [Tutorial do Kubernetes do Mendix](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube) para saber como configurar o cluster para o uso de produção.

## Continuando o desenvolvimento do Mendix e o ciclo de vida de implementação
{: #dev-lifecycle-mendix}

Mendix é um ambiente de criação de pouco código. O ciclo de vida de desenvolvimento requer que você abra seu projeto no app de área de trabalho Mendix Modeler.

1. Em seu app {{site.data.keyword.cloud_notm}}, clique em **Editar no Mendix**.
2. No portal da web do Mendix, clique em **Editar no Desktop Modeler**.
  O app Mendix é aberto no modelador de área de trabalho.
3. Edite o aplicativo Mendix e salve as mudanças.
4. Use o menu **Executar** do app Mendix Desktop Modeler e selecione a opção **Executar**.
  O pacote de implementação é criado e transferido por upload para o Mendix. Depois que o pacote de implementação for criado, será possível implementar seu app no {{site.data.keyword.cloud_notm}}.
5. Para implementar seu app Mendix, volte para a página **Detalhes do app** no {{site.data.keyword.cloud_notm}} e clique em **Implementar**.
  Essa ação inicia a cadeia de ferramentas do DevOps do app, que puxa a implementação mais recente do Mendix e implementa-a em seu ambiente de destino. Após a implementação ser concluída, a versão mais recente de seu app é iniciada automaticamente e se torna disponível.

Todos os apps Mendix devem ser implementados no {{site.data.keyword.cloud_notm}} clicando em **Configurar entrega contínua** na página **Detalhes do app** no {{site.data.keyword.cloud_notm}}. Não chame manualmente as cadeias de ferramentas do Mendix por meio da interface do IBM DevOps. A ativação manual das cadeias de ferramentas por meio da interface do DevOps pode resultar em uma implementação com falha devido à falta de metadados necessários que são críticos para as implementações do Mendix. Dependendo do estado de seu app, uma falha durante a ativação da cadeia de ferramentas do DevOps ou um erro no app implementado pode ocorrer.

Se você ativar manualmente uma cadeia de ferramentas e experimentar uma falha, será possível restaurar a implementação do app clicando em **Configurar entrega contínua** na página **Detalhes do app** no {{site.data.keyword.cloud_notm}}. Essa ação aciona um fluxo completo do DevOps para o app Mendix, que inclui os metadados necessários.
{: tip}

## Opcional: configurando o {{site.data.keyword.cos_full_notm}} 
{: #mendix-cos}

Alguns usuários podem desejar configurar seu app Mendix implementado para usar o {{site.data.keyword.cos_full}} para uploads de armazenamento persistente e de arquivo. O {{site.data.keyword.cos_full_notm}} é um serviço de armazenamento de objeto compatível com S3. Para tirar proveito do armazenamento de arquivo compatível com S3, os apps Mendix devem definir as variáveis de ambiente a seguir para acessar uma instância do {{site.data.keyword.cos_full_notm}}, depois de ter configurado a entrega contínua:

* `S3_ACCESS_KEY_ID` - a chave S3, que faz parte das credenciais do {{site.data.keyword.cos_full_notm}}
* `S3_SECRET_ACCESS_KEY` - a chave secreta S3, que faz parte das credenciais do {{site.data.keyword.cos_full_notm}}
* `S3_BUCKET_NAME` - o depósito de armazenamento S3
* `S3_ENDPOINT` - o terminal de armazenamento S3
* `S3_USE_V2_AUTH` - o valor é `true`

Para obter mais informações sobre os depósitos e as chaves do {{site.data.keyword.cos_full_notm}}, consulte a [Documentação da API do {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-gs-dev). Para obter mais informações sobre os valores de terminais regionais e inter-regionais, consulte os [docs do {{site.data.keyword.cos_full_notm}}](/docs/services/cloud-object-storage?topic=cloud-object-storage-endpoints). Para obter mais informações sobre o suporte ao Mendix para armazenamento compatível com S3, consulte a [documentação do buildpack do Mendix](https://github.com/mendix/cf-mendix-buildpack#s3-settings){: new_window}![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo").

### Configurações do {{site.data.keyword.cos_full_notm}} para apps Cloud Foundry
{: cos-cfapps}

Conclua estas etapas para implementações do Cloud Foundry:

1. Configure estas variáveis de ambiente em implementações do Cloud Foundry usando o comando `cf set-env`:

  ```
    ibmcloud cf set-env <YOUR_APP> S3_ACCESS_KEY_ID <YOUR_KEY>
    ibmcloud cf set-env <YOUR_APP> S3_SECRET_ACCESS_KEY <YOUR_SECRET_KEY>
    ibmcloud cf set-env <YOUR_APP> S3_BUCKET_NAME <YOUR_BUCKET>
    ibmcloud cf set-env <YOUR_APP> S3_ENDPOINT s3.us-south.cloud-object-storage.appdomain.cloud
    ibmcloud cf set-env <YOUR_APP> S3_USE_V2_AUTH true
  ```

2. Depois de especificar todos esses valores, remonte seu app Cloud Foundry para que os novos valores sejam aplicados.

  ```
    ibmcloud cf restage <YOUR_APP>
  ```

### Configurações do {{site.data.keyword.cos_full_notm}} para apps do Kubernetes
{: #cos-kubeapps}

Conclua estas etapas para implementações do Kubernetes:

1. Configure as variáveis de ambiente `S3_ACCESS_KEY_ID` e `S3_SECRET_ACCESS_KEY` como valores de segredo do Kubernetes no cluster. Para obter mais informações sobre como criar segredos do Kubernetes, consulte a [documentação do {{site.data.keyword.containershort_notm}}](/docs/containers?topic=containers-service-binding#adding_app).

2. Além de qualquer valor existente, especifique as variáveis de ambiente como variáveis de ambiente adicionais no arquivo `mendix-app.yaml` dentro da pasta `chart/<appname>/templates` do repositório Git. Os nomes dos segredos devem corresponder aos nomes que foram criados na etapa anterior.

  ```
    env:
      - name: S3_ACCESS_KEY_ID
        valueFrom:
          secretKeyRef:
            name: "mendix-s3-key"
            key: db-endpoint
      - name: S3_SECRET_ACCESS_KEY
        valueFrom:
          secretKeyRef:
            name: "mendix-s3-secret-key"
            key: db-endpoint
      - name: S3_ENDPOINT
        value: "s3.us-south.cloud-object-storage.appdomain.cloud"
      - name: S3_USE_V2_AUTH
        value: "true"
  ```

3. Após as mudanças do Kubernetes serem aplicadas, reimplemente seu app navegando para a página **Detalhes do app** e clicando em **Implementar**. 

## Próximas Etapas 
{: #next-steps-mendix}

Para implementar o aplicativo para o {{site.data.keyword.containerlong_notm}}, configure-o para a implementação de produção. Para obter mais informações, consulte o [Tutorial do Mendix Kubernetes](/docs/apps/tutorials?topic=creating-apps-deploy-mendix-kube). 
