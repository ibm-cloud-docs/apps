---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-15"

keywords: apps, services, add service, application

subcollection: creating-apps

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{:note: .note}

# Incluindo um serviço em seu app
{: #add-resource}

Ao criar um app com o {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}, é possível incluir serviços da página de detalhes do app. No entanto, também é possível provisioná-los diretamente no catálogo do {{site.data.keyword.cloud_notm}}, fora do contexto de seu app.
{: shortdesc}

É possível solicitar uma instância do serviço e usá-la independentemente de seu app ou é possível incluir a instância de serviço em seu app na página de detalhes do app. É possível provisionar um tipo específico de serviço diretamente do catálogo do {{site.data.keyword.cloud_notm}}.

## Descobrindo serviço
{: #discover-resources}

É possível ver todos os serviços que estão disponíveis no {{site.data.keyword.cloud_notm}} das maneiras a seguir:

* No console do {{site.data.keyword.cloud_notm}}. Visualize o catálogo do {{site.data.keyword.cloud_notm}}.
* Por meio da linha de comandos. Use o `ibmcloud ofertas de serviço` comando.
* A partir de seu próprio aplicativo. Use a [API de serviços GET /v2/services ](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

É possível selecionar o serviço necessário ao desenvolver aplicativos. Depois de selecioná-lo, o {{site.data.keyword.cloud_notm}} provisiona o serviço. O processo de fornecimento pode ser diferente para tipos de serviços diferentes. Por exemplo, um serviço de banco de dados cria um banco de dados e um serviço de notificação push para aplicativos móveis gera informações de configuração.

O {{site.data.keyword.cloud_notm}} fornece os recursos de um
serviço para o aplicativo usando uma instância de serviço. Uma instância de serviço pode ser compartilhada entre os aplicativos da web.

É possível também usar serviços que são hospedados em outras regiões, se esses serviços estiverem disponíveis nessas regiões. Esses serviços devem ser acessíveis pela internet e possuírem terminais de API. Deve-se
codificar manualmente o aplicativo para usar esses serviços da mesma maneira que você
codifica aplicativos externos ou ferramentas de terceiros para usar os serviços
{{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Conectando serviços a apps externos](/docs/resources?topic=resources-externalapp).

## Solicitando uma nova instância de serviço
{: #request-instance}

Para solicitar uma nova instância de serviço, deve-se usar a interface com o usuário do {{site.data.keyword.cloud_notm}} ou a interface da linha de comandos do {{site.data.keyword.cloud_notm}}.

Ao especificar o nome do serviço, evite caracteres que não sejam alfabéticos ou numéricos, pois os resultados podem ser imprevisíveis.
{: note}

Se você usar a interface com o usuário do {{site.data.keyword.cloud_notm}} para solicitar uma instância de serviço, conclua as etapas a seguir:

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique no tile para o serviço que você deseja incluir. A página de detalhes do serviço é aberta.

2. Digite um nome no campo **Nome do serviço**. Um nome padrão é fornecido. É possível alterar o nome no campo ou mantê-lo inalterado.

3. Conclua mais campos ou seleções e, em seguida, clique em **CRIAR**.

Se você usar a interface da linha de comandos do {{site.data.keyword.cloud_notm}} para solicitar uma instância de
serviço, faça download do app localmente, abra a linha de comandos e mude para o diretório do app.

1. Execute o comando a seguir para incluir um serviço no app. É possível selecionar um serviço existente de um já
ativado na conta ou incluir um novo serviço.

  ```bash
  ibmcloud dev edit
  ```
  {: pre}

2. Siga os prompts para selecionar um grupo de recursos e para criar e conectar um novo serviço relacionado a dados ao
aplicativo, como o Cloudant. Pode ser necessário selecionar uma região e um plano para o serviço.
3. Quando o serviço é criado, vários arquivos, incluindo as credenciais, são incluídos no diretório do aplicativo para
ajudar você a integrar o serviço ao aplicativo. É possível mesclar manualmente quaisquer arquivos ou ignorar essa etapa por enquanto.

É possível ligar uma instância de serviço apenas àquelas instâncias do app que estão no mesmo espaço ou organização. No entanto, é possível usar instâncias de serviço de outros espaços ou organizações da mesma maneira que um app externo faz. Em vez de criar uma ligação, use as credenciais para configurar sua instância do app diretamente. Para obter mais informações sobre como os apps externos usam os serviços do {{site.data.keyword.cloud_notm}}, consulte [Ativando aplicativos externos para usar os serviços do {{site.data.keyword.cloud_notm}}](/docs/resources?topic=resources-externalapp#externalapp).

## Configurando seu aplicativo
{: #configure-app}

Depois de ligar uma instância de serviço ao aplicativo, deve-se configurar o aplicativo para interagir com o serviço.

Cada serviço pode requer um mecanismo diferente de comunicação com os aplicativos. Esses mecanismos são documentados como parte da definição de serviço para suas informações ao desenvolver aplicativos. Para consistência, os mecanismos são necessários para que seu aplicativo interaja com o serviço.

* Para interagir com os serviços de banco de dados, use as informações que o {{site.data.keyword.cloud_notm}} fornece como o ID do usuário, senha
e o URI de acesso para o aplicativo.
* Para interagir com os serviços de backend móveis, use as informações que o {{site.data.keyword.cloud_notm}} fornece, como a identidade
do aplicativo (ID do app), informações de segurança que são específicas para o cliente e o URI de acesso para
o aplicativo. Os serviços móveis geralmente funcionam em contexto entre si para que as informações de contexto, como o nome do desenvolvedor de aplicativos e o usuário que usa o aplicativo, possam ser compartilhadas em todo o conjunto de serviços.
* Para interagir com os aplicativos da Web ou código do lado do servidor para aplicativos móveis, use as
informações que o {{site.data.keyword.cloud_notm}} fornece como
as credenciais de tempo de execução no ambiente *VCAP_SERVICES* do
aplicativo. O valor da variável de ambiente *VCAP_SERVICES* é a serialização de um objeto JSON. A variável contém os dados de tempo de execução que são necessários para interagir com os serviços aos quais o aplicativo está ligado. O formato dos dados é diferente para serviços diferentes. Talvez seja necessário ler a documentação do serviço sobre o que deve-se esperar e como interpretar cada parte de informação.

Se um serviço ligado a um aplicativo ficar paralisado, o aplicativo pode ter parado de executar ou conter erros. O {{site.data.keyword.cloud_notm}} não reinicia automaticamente o aplicativo para se recuperar desses problemas. Considere codificar o aplicativo para identificar e recuperar de indisponibilidades, exceções e falhas de conexão. Para obter mais informações, consulte [Os aplicativos não serão reinicializados automaticamente](/docs/apps/troubleshoot?topic=creating-apps-managingapps#ts_apps_not_auto_restarted).

## Acessando serviços em ambientes de implementação do {{site.data.keyword.cloud_notm}}
{: #migrate_instance}

O {{site.data.keyword.cloud_notm}} oferece muitas opções de implementação e é possível acessar um serviço que está em execução em um ambiente por meio de um ambiente diferente. Por exemplo, se você tiver um serviço que está em execução no Cloud Foundry, será possível acessar esse serviço por meio de um aplicativo que está em execução em um cluster do Kubernetes.

### Exemplo: acessar um serviço do Cloud Foundry por meio de um pod do Kubernetes

Para acessar um serviço do Cloud Foundry por meio de um pod em um cluster do Kubernetes, deve-se ligar o serviço ao cluster
para armazenar as credenciais de serviço em um segredo do Kubernetes. Em seguida, é possível disponibilizar essas informações para o
app. 
{: shortdesc}

Por padrão, as credenciais de serviço armazenadas em um segredo do Kubernetes têm codificação Base64 e são criptografadas em
etcd. 

**Importante**: não faça referência nem exponha as credenciais de serviço diretamente no arquivo YAML de implementação. Por padrão, os arquivos YAML de implementação não são projetados para reter os dados sensíveis e não
criptografam as credenciais de serviço. Para armazenar e acessar adequadamente essas informações, deve-se usar um segredo do Kubernetes. 

1. [ Ligar o serviço ao seu cluster ](/docs/containers?topic=containers-integrations#adding_cluster). 
2. Para acessar as credenciais de serviço por meio do pod do app, escolha entre as opções a seguir. 
   - Monte o segredo como um volume em seu pod
   - Referencie o segredo em variáveis de ambiente

## Criando uma instância de serviço fornecida pelo usuário
{: #user_provide_services}

Você pode ter serviços que são gerenciados fora do {{site.data.keyword.cloud_notm}}. Se você tiver credenciais para acessar esses serviços externos na Internet, será possível criar instâncias de serviço fornecido pelo usuário do {{site.data.keyword.cloud_notm}} para representar e se comunicar com seus serviços externos.

Para criar uma instância de serviço fornecida pelo usuário e ligá-la a um aplicativo, conclua as etapas a seguir:

1. Crie uma instância de serviço fornecida pelo usuário usando o comando `ibmcloud service user-provided-create`:
    * Para criar uma instância de serviço fornecida pelo usuário, use a opção **-p** e separe os nomes de parâmetro com vírgulas. A interface da linha de comandos `ibmcloud`, em seguida, solicita cada parâmetro sucessivamente. Por exemplo:
        ```
        ibmcloud service user-provided-create testups1 -p "host, port, dbname, username, password"
        host> pubsub01.example.com
        port> 1234
        dbname> sampledb01
        username> pubsubuser
        password> p@$$w0rd
        Creating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * Para criar uma instância de serviço que drena informações para um software de gerenciamento de log de terceiro, use a opção `-l`. Especifique o destino que o software de gerenciamento de log de terceiros fornece. Por
exemplo:

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example.com
        Creating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

    Se desejar atualizar um ou mais parâmetros da instância de serviço fornecida pelo usuário, use o `ibmcloud service user-provided-update`.

    * Para atualizar uma instância de serviço fornecido pelo usuário geral, use a opção **-p** e especifique as chaves e os valores de parâmetro em um objeto JSON. Por
exemplo:

        ```
        ibmcloud service user-provided-update testups1 -p "{\"username\":\"pubsubuser2\",\"password\":\"p@$$w0rd2\"}"
        Updating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * Para criar uma instância de serviço que drena informações para um software de gerenciamento de log de terceiro, use a opção `-l`. Por
exemplo:

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example2.com
        Updating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

2. Ligue a instância de serviço ao seu aplicativo usando o comando `ibmcloud service bind`. Por
exemplo:

	```
	ibmcloud service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

Agora é possível configurar o seu aplicativo para usar os serviços externos. Para obter informações sobre como configurar o seu aplicativo para interagir com um serviço, consulte [Configurando seu aplicativo para interagir com um serviço](/docs/apps?topic=creating-apps-add-resource#configure-app).
