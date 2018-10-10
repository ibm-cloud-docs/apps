---
copyright:

  years: 2018

lastupdated: "2018-10-02"

---

{:new_window: target="_blank"}  
{:shortdesc: .shortdesc}  
{:screen: .screen}  
{:codeblock: .codeblock}  
{:pre: .pre}
{:tip: .tip}

# Criando e implementando apps usando a CLI
{: #developing}

É possível usar a interface da linha de comandos (CLI) do {{site.data.keyword.Bluemix}} para criar e implementar o app.
{:shortdesc}

## Antes de começar
{: #prereqs}

Instale a CLI do {{site.data.keyword.Bluemix_notm}}, o plug-in da CLI do {{site.data.keyword.dev_cli_notm}} e outros plug-ins e ferramentas recomendados. Para obter mais informações, consulte [Introdução à CLI do IBM Cloud](/docs/cli/index.html). 

## Criando o app
{: #create}

É possível criar um novo app do zero ou criar um app habilitado para nuvem usando o seu código existente. 

### Criando um app do zero

1. Execute o comando [`ibmcloud dev create`](/docs/cli/idt/commands.html#create) no diretório de sua escolha.
2. Selecione **Serviço de backend/ App da web** como o tipo de aplicativo.
3. Selecione **Nó** como o tipo de linguagem.
4. Selecione **Express.js Basic (App da web)** como o kit do iniciador a ser usado.
5. Insira um nome para o app e selecione o grupo de recursos que você deseja usar (se necessário). Não inclua serviços por enquanto.
6. Selecione a opção **IBM DevOps, usando o Cloud Foundry** para criar uma cadeia de ferramentas do DevOps. Talvez seja necessário configurar as chaves SSH para concluir esta etapa.
7. Insira um nome de host exclusivo, por exemplo, `abc-devhost`. Esse nome do host é a rota do app, `abc-devhost.mybluemix.net`.

A criação do app e da cadeia de ferramentas leva alguns segundos para ser concluída. É possível monitorar o status no prompt de comandos.

### Criando um app usando o código existente

1. Clone o [app de amostra do Hello World](https://github.com/IBM-Cloud/node-helloworld) executando o comando a seguir no diretório de sua escolha.

  ```
  git clone https://github.com/IBM-Cloud/node-helloworld.git
  ```
  {: codeblock}

2. Navegue para o diretório no qual você clonou o app de amostra e execute o comando [`ibmcloud dev enable`](/docs/cli/idt/commands.html#enable).
3. Selecione para continuar sem confirmar as mudanças no GitHub por enquanto.
4. Selecione para continuar quando você for solicitado a continuar com a linguagem do Nó que for detectada.
5. Selecione o grupo de recursos que você deseja usar (se necessário). Não inclua serviços por enquanto.
6. Espere alguns segundos para que o app seja criado. 
7. É possível escolher mesclar manualmente os arquivos de implementação e de configuração que são salvos no diretório do app ao criá-lo. Ou é possível ignorar essa etapa por enquanto.

## Construindo o app e executando-o localmente
{: #build-run}

Independentemente da opção usada para criar o app, agora é possível construí-lo e executá-lo localmente.

1. Navegue para o diretório do aplicativo e assegure-se de que o Docker esteja em execução em seu sistema.
2. Execute o comando [`ibmcloud dev build`](/docs/cli/idt/commands.html#build) para construir o app.
3. Execute o comando [`ibmcloud dev run`](/docs/cli/idt/commands.html#run) para começar a executar o app localmente.
4. Visualize a execução do app localmente em `http://localhost:3000` ou em uma URL semelhante.
5. Pressione as teclas **Ctrl+C** para parar o app.

Também é possível usar [comandos compostos](/docs/cli/idt/commands.html#compound), como `ibmcloud dev build/run`, para emitir sequencialmente uma compilação seguida por uma execução.
{: tip}

## Incluindo um serviço e modificando o código
{: #add-service}

Agora que o app pode ser executado localmente, é possível incluir um serviço e modificar algum código. 

1. Execute o comando  [ ` ibmcloud dev edit ` ](/docs/cli/idt/commands.html#edit) .
2. Siga os prompts para criar e conectar um novo serviço relacionado a dados ao app, como {{site.data.keyword.cloudant_short_notm}}. Pode ser necessário selecionar uma região e um plano para o serviço.
3. É possível escolher mesclar manualmente a implementação e a configuração que são salvas no diretório do app ao criar o serviço. Ou é possível ignorar essa etapa por enquanto.
4. Faça uma mudança em seu código. Por exemplo, modifique o arquivo `/public/index.html` ou um arquivo semelhante. Se você estiver usando o aplicativo `ExpressJS` de amostra, será possível mudar o `Congratulations!` sequência para algo como  ` Hello World! `.
5. Salve todos os arquivos que você modificou.

## Implementando no  {{site.data.keyword.Bluemix_notm}}
{: #deploy}

Será possível implementar o app {{site.data.keyword.Bluemix_notm}} de uma de duas maneiras, dependendo de como ele estiver configurado. 

### Implementando o app usando uma cadeia de ferramentas do DevOps

Se você criou anteriormente uma cadeia de ferramentas do DevOps para o app, a implementação de uma nova compilação será tão simples quanto confirmar e enviar o seu código por push para o repositório em sua cadeia de ferramentas. 

1. Execute o `git add.` comando.
2. Execute o comando `git commit -m "made changes"` para confirmar mudanças.
3. Execute o comando `git push origin master` para enviar por push para a ramificação principal.
4. Visualize a cadeia de ferramentas do DevOps para o app por meio do console do {{site.data.keyword.Bluemix_notm}}. É possível visualizar a cadeia de ferramentas em um navegador da web ao executar o comando [`ibmcloud dev console`](/docs/cli/idt/commands.html#console) por meio do diretório do app e clicando em **Visualizar cadeia de ferramentas**.
5. Visualize o pipeline dentro da cadeia de ferramentas para verificar se uma nova compilação foi iniciada.

### Implementando Manualmente seu Aplicativo

É possível implementar manualmente o app usando o comando [`deploy`](/docs/cli/idt/commands.html#deploy). Por exemplo, use as etapas a seguir para implementar manualmente o app no Kubernetes.

1. Certifique-se de que  [ criou um cluster do Kubernetes ](https://console.bluemix.net/containers-kubernetes/overview).
2. Execute o comando [`ibmcloud dev deploy -t container`](/docs/cli/idt/commands.html#deploy).
3. Quando solicitado, confirme o cluster e o nome da imagem do contêiner a serem usados.
4. Espere alguns minutos para que a implementação seja concluída.

## Visualizando seu aplicativo
{: #view}

1. Para visualizar a URL do app que está em execução no {{site.data.keyword.Bluemix_notm}}, execute o comando [`ibmcloud dev view`](/docs/cli/idt/commands.html#view).
2. Para visualizar detalhes sobre as credenciais, os serviços e a cadeia de ferramentas do app por meio do console do {{site.data.keyword.Bluemix_notm}}, execute o comando [`ibmcloud dev console`](/docs/cli/idt/commands.html#console). 

