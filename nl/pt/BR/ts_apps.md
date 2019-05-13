---

copyright:
  years: 2015, 2019
lastupdated: "2019-05-08"

keywords: apps, application, troubleshooting, debug apps, known issues, debug, help, configuration, app, troubleshoot, error, errors, failure, failed, fail, issues, applications

subcollection: creating-apps

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# Resolução de problemas para criar apps
{: #managingapps}

Problemas gerais com a criação de apps podem incluir apps que não podem ser atualizados ou caracteres de byte duplo que não são exibidos. Em muitos casos, é possível recuperar-se desses problemas seguindo algumas etapas simples.
{:shortdesc}

## Meus apps estão hospedados em domínios diferentes
{: #domains-ts}
{: troubleshoot}

Alguns de meus apps estão hospedados no domínio `mybluemix.net`, mas outros estão hospedados no domínio `appdomain.cloud`.

Meus apps existentes estão hospedados no domínio `mybluemix.net`, mas meus apps mais novos estão hospedados no domínio `appdomain.cloud`.
{: tsSymptoms}

Uma nova opção de nome do host `*.appdomain.cloud` está disponível em cloud.ibm.com.

Anteriormente, o domínio `mybluemix.net` foi usado para hospedar apps em vários destinos de implementação, como o {{site.data.keyword.containerlong_notm}} ou o Cloud Foundry. Qualquer app que você hospedou em `mybluemix.net` não será impactado.

O subdomínio para apps do Cloud Foundry é `cf.appdomain.cloud`. O subdomínio para apps que você implementa no {{site.data.keyword.containerlong_notm}} é `containers.appdomain.cloud`.

Para obter mais informações, consulte [Gerenciando seus domínios](/docs/apps?topic=creating-apps-update-domain).

## Você possui mudanças não salvas
{: #ts_unsaved_changes}
{: troubleshoot}

Ao clicar em itens na página de detalhes do app, talvez você não consiga executar nenhuma ação. Você também pode ser solicitado a salvar as mudanças antes de poder continuar.

Ao tentar verificar seu app ou serviços na página de detalhes do app, a mensagem de erro a seguir será exibida:
{: tsSymptoms}

` Você possui mudanças não salvas. Tem certeza de que deseja sair desta página?`

Ao rolar o mouse sobre os campos **INSTÂNCIAS** ou **COTA DE MEMÓRIA** na área de janela de tempo de execução, os valores mudam. Esse comportamento é definido pelo design. No entanto, você será solicitado a salvar as configurações de memória ou de instância antes de ir para outra página.
{: tsCauses}

Feche a janela de mensagem e clique em **RECONFIGURAR** em sua área de janela de tempo de execução.
{: tsResolve}

## O failover automático entre regiões do {{site.data.keyword.cloud_notm}} não está disponível
{: #ts_failover}
{: troubleshoot}

Não é possível usar failover automático entre regiões do {{site.data.keyword.cloud}}. No entanto, é possível usar um provedor DNS que suporte failover entre muitos endereços IP como uma solução alternativa.

Quando uma região do {{site.data.keyword.cloud_notm}} se torna indisponível, os apps que estão em execução nessa região também ficam indisponíveis, ainda que os mesmos apps estejam em execução em outra região do {{site.data.keyword.cloud_notm}}.
{: tsSymptoms}

O {{site.data.keyword.cloud_notm}} ainda não fornece failover automático de uma região para outra.
{: tsCauses}

É possível usar um provedor DNS que suporte failover inteligente entre vários endereços de ID e configurar manualmente suas configurações de DNS para ativar o failover automático entre regiões do {{site.data.keyword.cloud_notm}}. Os provedores de DNS com esse recurso incluem NSONE, Akamai e Dyn.
{: tsResolve}

Ao configurar suas definições de DNS, deve-se especificar os endereços IP públicos das regiões do {{site.data.keyword.cloud_notm}} em que seu apps estão em execução. Para obter o endereço IP público de uma região do {{site.data.keyword.cloud_notm}}, use o comando `nslookup`. Por exemplo, é possível digitar o comando a seguir em uma janela de linha de comandos.
```
nslookup cloud.ibm.com
```
{: codeblock}

## Não é possível acessar serviços do {{site.data.keyword.cloud_notm}} devido a erros de autorização
{: #ts_vcap}
{: troubleshoot}

Erros de autorização poderão ocorrer quando o seu app acessar um serviço do {{site.data.keyword.cloud_notm}}, se as credenciais de serviço estiverem codificadas permanentemente no app.

Depois de configurar seu app para se comunicar com um serviço {{site.data.keyword.cloud_notm}}, você implementa o app no {{site.data.keyword.cloud_notm}}. No entanto, não é possível usar o app para acessar o serviço {{site.data.keyword.cloud_notm}} e receber um erro de autorização.
{: tsSymptoms}

As credenciais codificadas permanentemente no app podem não estar corretas. Toda vez que o serviço é recriado, as credenciais para acessá-lo mudam.
{: tsCauses}

Em vez de codificar permanentemente as credenciais no app, use parâmetros de conexão a partir da variável de ambiente VCAP_SERVICES. Os métodos para usar parâmetros de conexão a partir da variável de ambiente VCAP_SERVICES variam, dependendo das linguagens do programa. Por exemplo, para apps Node.js, é possível usar o comando a seguir:
{: tsResolve}

```
process.env.VCAP_SERVICES
```

Para obter mais informações sobre os comandos que podem ser usados em outras linguagens de programa, veja [Java ](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") e [Ruby ](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

## Erros 502 Gateway inválido são recebidos
{: #ts_502_error}
{: troubleshoot}

Se você receber erros `502 Gateway Inválido` quando interagir com apps no {{site.data.keyword.cloud_notm}}, verifique a página de status do {{site.data.keyword.cloud_notm}} e, em seguida, tome as ações apropriadas.

Você recebe mensagens de erro que iniciam com 502 Gateway inválido. Por exemplo, você pode ver `502 Gateway inválido: o terminal registrado falhou em manipular a solicitação.`
{: tsSymptoms}

Um erro de Gateway inválido geralmente acontece quando você acessa um website que usa um servidor proxy para armazenar e retransmitir os dados do servidor principal que hospeda o site. O servidor principal e o servidor proxy podem não se conectar adequadamente. Então, você vê o código de status 502 do HTTP em sua janela do navegador. Esse código de status indica que o servidor principal do site não recebeu a implementação HTTP esperada do servidor proxy.
{: tsCauses}

Outras causas menos comuns de um erro de Gateway inválido são os dropouts do provedor de serviços da Internet (ISP), configurações de firewall inválidas e erros de cache do navegador.

Se você suspeitar que um serviço do {{site.data.keyword.cloud_notm}} está inativo, primeiro, verifique a página [{{site.data.keyword.cloud_notm}} status ](https://cloud.ibm.com/status){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"). Uma solução alternativa pode ser [usar o serviço em outra região do {{site.data.keyword.cloud_notm}}](/docs/resources/connect_external_app?topic=resources-externalapp){: new_window}. Se o status de serviço for normal, tente as etapas a seguir para resolver o problema:
{: tsResolve}

  * Tente novamente a ação:
    * Recarregue a página pressionando F5 em seu teclado ou clicando em **Atualizar**. Se essa etapa não funcionar, limpe o cache e os cookies de seu navegador e, em seguida, recarregue novamente.
    * Usar um navegador diferente.
    * Reinicie seu roteador, seu modem e seu computador. Reinicializar esses dispositivos pode limpar diversos erros que conduzem ao erro 502.
  * Aguardar e tentar novamente mais tarde. Problemas temporários podem ocorrer com seu provedor de serviços da Internet ou com os serviços do {{site.data.keyword.cloud_notm}}. É possível aguardar até que os problemas temporários sejam resolvidos.
  * Se o problema ainda existir, entre em contato com o suporte do {{site.data.keyword.cloud_notm}}. Veja [Entrando em contato com o {{site.data.keyword.cloud_notm}} Suporte ](/docs/get-support?topic=get-support-getting-customer-support){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") para obter mais informações.

## Apps Android não podem receber {{site.data.keyword.mobilepushshort}}
{: #ts_push}
{: troubleshoot}

Os apps Android em certas regiões em que o Google não está acessível não podem receber as notificações que você envia por meio do serviço IBM {{site.data.keyword.mobilepushshort}}. Nesse caso, uma solução alternativa é usar serviços de terceiros.

Você liga um serviço {{site.data.keyword.mobilepushshort}} para seu app do {{site.data.keyword.cloud_notm}} e envia uma mensagem para os dispositivos registrados. No entanto, os apps que são desenvolvidos no Android não podem receber suas notificações em certas regiões.
{: tsSymptoms}

O serviço IBM {{site.data.keyword.mobilepushshort}} usa o serviço Google Cloud Messaging (GCM) para despachar notificações para apps móveis que são desenvolvidos no Android. Para ativar o recebimento de notificações em apps Android, o serviço Google Cloud Messaging (GCM) deve estar acessível para apps móveis. Em regiões em que os apps Android não podem acessar o serviço GCM, os apps Android não podem receber o {{site.data.keyword.mobilepushshort}}.
{: tsCauses}

Como uma solução alternativa, use serviços de terceiros que não dependam do serviço GCM, por exemplo, [Pushy ](https://pushy.me){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"), [getui ](http://www.getui.com/){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") e [jpush ](https://www.jpush.cn/){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").
{: tsResolve}

## Caracteres de byte duplo não são exibidos de forma adequada quando os apps são enviados por push para o {{site.data.keyword.cloud_notm}}
{: #ts_doublebytes}
{: troubleshoot}

Os caracteres de byte duplo poderão não ser exibidos corretamente se o suporte Unicode não estiver configurado corretamente para os arquivos servlet ou JSP.

Quando um aplicativo é enviado por push para o {{site.data.keyword.cloud_notm}}, os caracteres de byte duplo especificados no app não são exibidos corretamente.
{: tsSymptoms}

O problema poderá ocorrer se o suporte Unicode não estiver configurado corretamente para os arquivos servlet ou JSP.
{: tsCauses}

É possível usar o código a seguir no arquivo servlet ou JSP:
{: tsResolve}

  * No arquivo de origem servlet
  ```java
	response.setContentType("text/html; charset=UTF-8");
	```
  {: codeblock}

  * No JSP
  ```jsp
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```
  {: codeblock}

## Não é possível implementar apps Node.js
{: #ts_nodejs_deploy}
{: troubleshoot}

É possível encontrar problemas ao atualizar um app Node.js ou implementar um app Node.js no {{site.data.keyword.cloud_notm}}.

Ao atualizar um app Node.js ou implementar seu app Node.js
no {{site.data.keyword.cloud_notm}},
é possível ver uma das mensagens de erro a seguir:
{: tsSymptoms}

`Um app não foi detectado com êxito por nenhum buildpack disponível.`

`A instância (índice 0) falhou ao iniciar a aceitação de conexões.`

`Não é possível obter instâncias, uma vez que a preparação falhou.`

As causas possíveis são as seguintes:
{: tsCauses}

  * O comando inicial não foi especificado.
  * Os arquivos necessários para implementar um app Node.js estão ausentes no app ou estão em uma pasta diferente do diretório-raiz.

Use um dos métodos a seguir, dependendo da causa do problema:
{: tsResolve}

  * Especifique o comando inicial por um dos métodos a seguir:
     * Use a interface da linha de comandos do Cloud Foundry. Por exemplo:
      ```
		  ibmcloud cf push MyUniqueNodejs01 -p app_path -c "node app.js"
		  ```
      {: codeblock}

    * Use o arquivo [package.json ](https://www.npmjs.com/package/jsonfile){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo"). Por
exemplo:
	    ```json
		  {
        ...
  	    "scripts": {
	 		  "start": "node app.js"
 	   }
	    }
	    ```

    * Use o arquivo `manifest.yml`. Por
exemplo:
	    ```
		  applications:
  name: MyUniqueNodejs01
  ...
      command: node app.js
  ...
      ```

  * Assegure-se de que um arquivo `package.json` exista em seu app Node.js para que o buildpack Node.js possa reconhecer o app. Assegure-se de que esse arquivo esteja no diretório-raiz de seu app.
    O exemplo a seguir mostra um arquivo `package.json` simples:
	```json
     {
        "name": "MyUniqueNodejs01",
        "version": "0.0.1",
        "description": "A sample package.json file",
        "dependencies": {
                "express": "3.4.x",
                "jade": "1.1.x"
        },
        "engines": {
                "node": "0.10.x"
        },
        "scripts": {
                  "start": "node app.js"
        }
 }
    ```

Para mais dicas sobre apps Node.js, veja [Dicas para aplicativos Node.js ](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

## Erros de configuração aparecem no arquivo `server.xml` depois de importar um app {{site.data.keyword.cloud_notm}} Liberty para o Eclipse
{: #ts_eclipse}
{: troubleshoot}

Se você vir erros de configuração no arquivo `server.xml` depois de importar um app {{site.data.keyword.cloud_notm}} Liberty para o Eclipse, poderá ser necessário remover o arquivo `server.xml` do projeto.

Depois de importar um app {{site.data.keyword.cloud_notm}} Liberty para o Eclipse, você verá erros de configuração no arquivo `server.xml` na visualização Problemas do Eclipse.
{: tsSymptoms}

O buildpack do Liberty usa o arquivo `server.xml` para configurar o app e gera um arquivo `runtime-vars.xml` quando o app Liberty é enviado por push ao {{site.data.keyword.cloud_notm}}. Quando você importa o app para o Eclipse, o arquivo `runtime-vars.xml` não existe em seu ambiente local.
{: tsCauses}

É possível resolver esse problema removendo o arquivo server.xml do projeto. O buildpack cria o arquivo `server.xml` dinamicamente quando você envia por push o app como um app WAR. Para obter mais informações, veja [Liberty for Java](/docs/runtimes/liberty?topic=liberty-liberty_runtime#liberty_runtime).
{: tsResolve}

## Os aplicativos não podem ser colocados em estágios usando buildpacks customizados
{: #ts_bp_compilation}
{: troubleshoot}

Você poderá não ser capaz de implementar um app no {{site.data.keyword.cloud_notm}} com um buildpack customizado se os scripts no buildpack não forem arquivos executáveis.

Ao implementar um app no {{site.data.keyword.cloud_notm}} com um buildpack customizado, você verá a mensagem de erro `The application failed to stage, so there are no instances to display.`
{: tsSymptoms}

Esse problema poderá ocorrer se scripts, como o script de detecção, o script de compilação e o script de liberação não forem executáveis.
{: tsCauses}

É possível usar o comando [Git update ](http://git-scm.com/docs/git-update-index){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") para mudar a permissão de cada script para executável. Por exemplo, é possível digitar `git update --chmod=+x script.sh`.
{: tsResolve}

## Não é possível implementar um app do Delivery Pipeline no {{site.data.keyword.cloud_notm}} Continuous Delivery
{: #ts_devops_to_bm}
{: troubleshoot}

 Talvez não seja possível implementar seu app com o {{site.data.keyword.deliverypipeline}} no {{site.data.keyword.contdelivery_short}} se o arquivo `manifest.yml` não estiver presente em seu app.

 Ao implementar um app com o {{site.data.keyword.deliverypipeline}} no {{site.data.keyword.contdelivery_short}}, uma mensagem de erro `Unable to detect a supported application type` pode ser exibida.
 {: tsSymptoms}

 Esse problema pode ocorrer porque o pipeline requer um arquivo `manifest.yml` para implementar um app no {{site.data.keyword.cloud_notm}}.
 {: tsCauses}

 Para resolver esse problema, você deve criar um arquivo `manifest.yml`. Para obter informações adicionais sobre como criar um arquivo `manifest.yml`,
consulte [Manifest do
aplicativo](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest).
 {: tsResolve}

## Sua cota de armazenamento foi excedida
{: #exceed_quota}

Se as tarefas de compilação ou implementação falharem e você vir a mensagem a seguir, será possível excluir suas imagens com os comandos da CLI a seguir. `Status: unauthorized: You have exceeded your storage quota. Delete one or more images, or review your storage quota and pricing plan.`

* Instale a CLI do [{{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli) se você ainda não a tiver.
* Efetue login no {{site.data.keyword.cloud_notm}} usando `ibmcloud login` e aponte-o para o espaço no espaço em que você está.
* Liste suas imagens usando `ibmcloud cr images`.
* Exclua quaisquer imagens não utilizadas por meio do comando `ibmcloud cr image-rm <respository>:<tag>`.
* Execute novamente a tarefa de compilação ou implementação que falhou.

## Acessando logs do Kubernetes
{: #access_kube_logs}

Se o aplicativo não estiver em execução e não for possível acessar o terminal de funcionamento, tente verificar os logs no cluster.
* Instale a CLI do [{{site.data.keyword.cloud_notm}}](/docs/cli?topic=cloud-cli-ibmcloud-cli) se você ainda não a tiver.
* Efetue login no {{site.data.keyword.cloud_notm}} usando `ibmcloud login` e aponte-o para o espaço no espaço em que você está.
* Liste seus clusters usando `ibmcloud cs clusters`,
* Aponte para seu cluster correspondente usando `ibmcloud cs cluster-config <cluster-name>`.
* Exporte a variável de ambiente que está listada.
* Visualize seus pods usando `kubectl get pods`. Se for necessário instalar
o `kubectl`, veja [Instalar e configurar o kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").
* É possível visualizar os logs em seu app usando o `kubectl logs <pod-name>.`

## Iniciar o `docker` falha com a mensagem "arquivo não localizado"
{: #docker_not_found}
{: troubleshoot}

Ao tentar iniciar o Docker, a mensagem de erro a seguir será exibida:
{: tsSymptoms}

```
An error exec: "docker": executable file not found in $PATH was encountered while the Docker image is building.
```
{: screen}

O cliente Docker não está instalado, ou está instalado, mas não foi iniciado.
{: tsCauses}

Assegure-se de que o [Docker](https://docs.docker.com/install/){: new_window}![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo") esteja instalado e inicie-o.
{: tsResolve}

## A compilação de um app falha com o erro do Docker
{: #build_error}
{: troubleshoot}

Ao tentar construir um app com o comando `ibmcloud dev build`, ele falha
com um erro de nome de usuário/senha do Docker. 
{: tsSymptoms}

As credenciais incorretas do Docker Hub estão sendo usadas para autenticar. 
{: tsCauses}

Efetue logout do Docker Hub no cliente do Docker.
{: tsResolve}
