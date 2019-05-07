---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-25"

keywords: apps, create, build, deploy, cli, web app, microservice, deploy cli, deploy command line, build app local, developer tools, ibmcloud dev create

subcollection: creating-apps

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}
{:note: .note}

# Criando e implementando apps usando a CLI
{: #create-deploy-app-cli}

É possível usar a interface da linha de comandos (CLI) do {{site.data.keyword.cloud}} para criar e implementar seu aplicativo. 

É possível criar um app iniciador do zero ou ativar o código de app existente para nuvem. 
{: note}

## Antes de começar
{: #prereqs-app-cli}

Deve-se instalar a CLI do {{site.data.keyword.cloud_notm}}, o plug-in da CLI do {{site.data.keyword.dev_cli_notm}} e outros plug-ins e ferramentas recomendados. Para obter mais informações, consulte [Introdução à CLI do IBM Cloud](/docs/cli?topic=cloud-cli-ibmcloud-cli). 

## Criando um app iniciador do zero
{: #create-app-cli}

A criação de um app do zero é útil se você ainda não tem o código existente para começar e prefere iniciar com um modelo de linguagem ou de iniciador de estrutura.

1. Execute o comando [`ibmcloud dev create`](/docs/cli/idt?topic=cloud-cli-idt-cli#create) no diretório de sua escolha.
2. Selecione **Serviço de backend/ App da web** como o tipo de aplicativo.
3. Selecione **Node** como o tipo de linguagem.
4. Selecione **Aplicativo da web do Node.js com Express.js (aplicativo da web)** como o kit do iniciador a ser usado.
5. Insira um nome para o seu app e selecione o grupo de recursos que você deseja usar (se necessário). Por enquanto, não inclua serviços.
6. Selecione a opção **IBM DevOps, implementar nos buildpacks do Cloud Foundry** para criar uma cadeia de ferramentas do DevOps. Talvez seja necessário configurar as chaves SSH para concluir esta etapa.
  Se você configurar uma passphrase para a sua chave SSH, será necessário inserir esse código.
  {: note}
7. Siga os prompts restantes para:
  * Selecionar uma região para sua cadeia de ferramentas.
  * Inserir um nome para o nome da cadeia de ferramentas do DevOps.
  * Inserir um nome para o nome do host.

A criação do app e da cadeia de ferramentas leva alguns segundos para ser concluída.

## Gerando ativos de implementação e de ativação de nuvem
{: #byoc-cli}

Essa opção poderá ser usada se você já tiver um código base existente e desejar gerar ativos de implementação e de ativação de nuvem para um único microsserviço ou aplicativo da web usando [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable). Observe que esse comando está em Beta e nem todas as linguagens e/ou estruturas do app são suportadas. As instruções a seguir ilustram como usar essa funcionalidade com um repositório de amostra, mas as etapas são mais ou menos as mesmas para o seu próprio código base.

1. Efetue login no {{site.data.keyword.cloud_notm}} executando `ibmcloud login` e, em seguida, tenha como destino uma organização e um espaço.
2. Clone o [app de amostra Hello World](https://github.com/IBM-Cloud/node-helloworld){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") executando o comando a seguir no diretório de sua escolha.

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

3. Navegue para o diretório no qual você clonou o app de amostra e execute o comando [`ibmcloud dev enable`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable).
4. Selecione para continuar sem confirmar as mudanças por enquanto (se necessário).
5. Selecione para continuar quando você for solicitado a continuar com a linguagem do Nó que for detectada.
6. Selecione o grupo de recursos que deseja usar (se necessário). 
7. Selecione a opção para criar um novo app do {{site.data.keyword.cloud_notm}} que esteja vinculado a esse repositório Git. Consulte **Notas importantes** para obter detalhes.
8. Por enquanto, não inclua serviços.
9. Aguarde alguns segundos para que as operações sejam concluídas. 
10. Depois que as operações forem concluídas, mescle manualmente os arquivos de implementação e de ativação de nuvem salvos no diretório do app. Mescle novos arquivos marcados como `.merge` usando `git diff` ou uma ferramenta semelhante.

### Notas importantes
 - Se você já criou um app do {{site.data.keyword.cloud_notm}} usando o console do {{site.data.keyword.cloud_notm}}, siga as etapas de 2 a 5 na seção prévia no diretório de aplicativos. Para a etapa 6, é possível selecionar a opção para conectar o código local a um app existente.
 - Também é possível escolher gerar arquivos de implementação e de ativação de nuvem sem se conectar a um app do {{site.data.keyword.cloud_notm}} executando [`ibmcloud dev enable --no-create`](/docs/cli/idt?topic=cloud-cli-idt-cli#enable).
 - Para configurar manualmente uma cadeia de ferramentas e arquivos de implementação, siga [o tutorial](/docs/apps/tutorials?topic=creating-apps-tutorial-byoc-kube). Isso poderá ser útil se você
estiver tentando configurar uma cadeia de ferramentas de entrega contínua para mais de um app da web ou microsserviço da
web inter-relacionado.
 - Se o código base existente ainda não estiver em um repositório Git, siga as etapas de 2 a 5 na seção anterior no diretório de aplicativos. Para a etapa 6, é possível selecionar a opção de criar um novo app do {{site.data.keyword.cloud_notm}} e implementá-lo em uma cadeia de ferramentas do DevOps (que tem um repositório GitLab recém-criado).

## Construindo o app e executando-o localmente
{: #build-run-app-cli}

Independentemente da opção usada para criar o app, agora é possível construí-lo e executá-lo localmente.

1. Navegue para o diretório do aplicativo e assegure-se de que o Docker esteja em execução em seu sistema.
2. Execute o comando [`ibmcloud dev build`](/docs/cli/idt?topic=cloud-cli-idt-cli#build) para construir o app.
3. Execute o comando [`ibmcloud dev run`](/docs/cli/idt?topic=cloud-cli-idt-cli#run) para começar a executar o app localmente.
4. Visualize o seu app que está em execução localmente em `http://localhost:3000` ou em uma URL semelhante.
5. Pressione as teclas **Ctrl+C** para parar o app.

Também é possível usar [comandos compostos](/docs/cli/idt?topic=cloud-cli-idt-cli#compound), como `ibmcloud dev build/run`, para emitir sequencialmente uma compilação seguida por uma execução.
{: tip}

## Incluindo um serviço e modificando o código
{: #resources-app-cli}

Agora que o app pode ser executado localmente, é possível incluir um serviço e modificar algum código. 

1. Execute o comando [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit).
2. Siga os prompts para criar e conectar um novo serviço relacionado a dados ao app, como {{site.data.keyword.cloudant_short_notm}}. Pode ser necessário selecionar uma região e um plano para o serviço.
3. É possível escolher mesclar manualmente os arquivos de configuração que são salvos no diretório de aplicativos ao criar o serviço. Ou é possível ignorar essa etapa por enquanto.
4. Atualize o seu código. Por exemplo, modifique o arquivo `/public/index.html` ou um arquivo semelhante. Se você estiver usando o aplicativo `ExpressJS` de amostra, será possível mudar o `Congratulations!` sequência para algo como  ` Hello World! `.
5. Salve todos os arquivos que você modificou.

## Implementando no  {{site.data.keyword.cloud_notm}}
{: #deploy-app-cli}

É possível implementar o app {{site.data.keyword.cloud_notm}} de uma de duas maneiras, dependendo da configuração do app. 

### Implementando o app usando uma cadeia de ferramentas do DevOps
Se você ainda não tiver criado uma cadeia de ferramentas do DevOps para o app e ele ainda não estiver em um repositório Git, será possível executar o comando [`ibmcloud dev edit`](/docs/cli/idt?topic=cloud-cli-idt-cli#edit). Siga os prompts para "Configurar o DevOps" e implemente em uma nova cadeia de ferramentas (e crie um novo repositório GitLab).

Após você criar uma cadeia de ferramentas do DevOps para o seu app, a implementação de uma nova construção é tão simples quanto confirmar e enviar por push o seu código para o repositório em sua cadeia de ferramentas. 

1. Execute o `git add.` comando.
2. Execute o comando `git commit -m "made changes"` para confirmar mudanças.
3. Execute o comando `git push origin master` para enviar por push para a ramificação principal.
4. Visualize a cadeia de ferramentas do DevOps para o app por meio do console do {{site.data.keyword.cloud_notm}}. É possível visualizar os detalhes da cadeia de ferramentas na página **Detalhes do app** no console do {{site.data.keyword.cloud_notm}} executando o comando [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console) no diretório do app.
5. Visualize o pipeline dentro da cadeia de ferramentas para verificar se uma nova compilação foi iniciada.

### Implementando Manualmente seu Aplicativo

É possível implementar manualmente o app usando o comando [`deploy`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy). Por exemplo, use as etapas a seguir para implementar manualmente o app no Kubernetes.

1. Assegure-se de que você [tenha criado um cluster Kubernetes](https://{DomainName}/kubernetes/overview){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").
2. Execute o comando [`ibmcloud dev deploy -t container`](/docs/cli/idt?topic=cloud-cli-idt-cli#deploy).
3. Quando solicitado, confirme o cluster e o nome da imagem do contêiner a serem usados.
4. Espere alguns minutos para que a implementação seja concluída.

## Visualizando seu aplicativo
{: #view-app-cli}

1. Para visualizar a URL do app que está em execução no {{site.data.keyword.cloud_notm}}, execute o comando [`ibmcloud dev view`](/docs/cli/idt?topic=cloud-cli-idt-cli#view).
2. Para visualizar detalhes sobre as credenciais, os serviços e a cadeia de ferramentas do app por meio do console do {{site.data.keyword.cloud_notm}}, execute o comando [`ibmcloud dev console`](/docs/cli/idt?topic=cloud-cli-idt-cli#console). 

**Para relatar problemas ou fornecer feedback, é possível usar o [{{site.data.keyword.cloud_notm}} Tech's Slack - #developer-tools channel](https://ibm-cloud-tech.slack.com/){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"). Solicite acesso de equipe [aqui](https://slack-invite-ibm-cloud-tech.mybluemix.net/){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").**
