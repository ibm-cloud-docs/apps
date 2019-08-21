---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-03"

keywords: apps, services, add service, application, service, instance, ibmcloud dev edit, vcap_services, credentials

subcollection: creating-apps

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{:note: .note}

# Incluindo um serviço em seu app
{: #add-resource}

Ao criar um app com o {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}}, é possível incluir serviços da página de detalhes do app. Também é possível provisioná-los diretamente por meio do catálogo do {{site.data.keyword.cloud_notm}}, fora do contexto de seu app.
{: shortdesc}

É possível solicitar uma instância do serviço e usá-la independentemente de seu app ou é possível incluir a instância de serviço em seu app na página de detalhes do app. É possível provisionar um tipo específico de serviço diretamente do catálogo do {{site.data.keyword.cloud_notm}}.

## Serviços autoprovisionados
{: #auto-provision}

Se um kit do iniciador especificar os serviços necessários, o {{site.data.keyword.cloud_notm}} criará automaticamente instâncias desses serviços quando você criar seu app. Também é possível criar manualmente serviços ou selecionar instâncias de serviço existentes para incluir em seu app após ele ter sido criado. É possível ver uma lista de instâncias de serviço que estão associadas a seu app na página **Detalhes do app**, junto com as credenciais de serviço no caso de precisar delas posteriormente.

## Descobrindo serviços
{: #discover-resources}

É possível ver todos os serviços que estão disponíveis no {{site.data.keyword.cloud_notm}} das maneiras a seguir:

* No console do {{site.data.keyword.cloud_notm}}. Visualize o catálogo do {{site.data.keyword.cloud_notm}}.
* Por meio da linha de comandos. Use o `ibmcloud ofertas de serviço` comando.
* A partir de seu próprio aplicativo. Use a [API de serviços GET /v2/services ](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

É possível selecionar o serviço que você precisa ao desenvolver apps. Depois de selecioná-lo, o {{site.data.keyword.cloud_notm}} provisiona o serviço. O processo de fornecimento pode ser diferente para tipos de serviços diferentes. Por exemplo, um serviço de banco de dados cria um banco de dados e um serviço de notificação de push para apps móveis gera informações de configuração.

O {{site.data.keyword.cloud_notm}} fornece os recursos de um serviço para o seu app usando uma instância de serviço. Uma instância de serviço pode ser compartilhada entre aplicativos da web.

É possível também usar serviços que são hospedados em outras regiões, se esses serviços estiverem disponíveis nessas regiões. Esses serviços devem ser acessíveis pela internet e possuírem terminais de API. Deve-se codificar manualmente seu app para usar esses serviços da mesma maneira que você codifica apps externos ou ferramentas de terceiros para usar os serviços do {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte [Conectando serviços a apps externos](/docs/resources?topic=resources-externalapp).

## Solicitando uma nova instância de serviço
{: #request-instance}

Para solicitar uma nova instância de serviço, deve-se usar a interface com o usuário do {{site.data.keyword.cloud_notm}} ou a interface da linha de comandos do {{site.data.keyword.cloud_notm}}.

Ao especificar o nome do serviço, evite caracteres que não sejam alfabéticos ou numéricos, pois os resultados podem ser imprevisíveis.
{: note}

Se você usar a interface com o usuário do {{site.data.keyword.cloud_notm}} para solicitar uma instância de serviço, conclua as etapas a seguir:

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique no bloco para o serviço que você deseja incluir. A página de detalhes do serviço é aberta.

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

2. Siga os prompts para selecionar um grupo de recursos e para criar e conectar um novo serviço relacionado a dados ao seu app, como o Cloudant. Pode ser necessário selecionar uma região e um plano para o serviço.
3. Quando o serviço é criado, vários arquivos, incluindo credenciais, são incluídos em seu diretório de app para ajudá-lo a integrar o serviço a seu app. É possível mesclar manualmente quaisquer arquivos ou ignorar essa etapa por enquanto.

É possível ligar uma instância de serviço apenas àquelas instâncias do app que estão no mesmo espaço ou organização. No entanto, é possível usar instâncias de serviço de outros espaços ou organizações da mesma maneira que um app externo faz. Em vez de criar uma ligação, use as credenciais para configurar sua instância do app diretamente. Para obter mais informações sobre como os apps externos usam os serviços do {{site.data.keyword.cloud_notm}}, consulte [Ativando aplicativos externos para usar os serviços do {{site.data.keyword.cloud_notm}}](/docs/resources?topic=resources-externalapp#externalapp).

## Configurando seu app
{: #configure-app}

Depois de ligar uma instância de serviço a seu app, deve-se configurar seu app para interagir com o serviço.

Cada serviço pode precisar de um mecanismo diferente de comunicação com apps. Esses mecanismos são documentados como parte da definição de serviço para suas informações quando você desenvolve apps. Para consistência, os mecanismos são necessários para que seu app interaja com o serviço.

* Para interagir com os serviços de banco de dados, use as informações que o {{site.data.keyword.cloud_notm}} fornece, como o ID do usuário, a senha e o URI de acesso para o app.
* Para interagir com os serviços de back-end móveis, use as informações que o {{site.data.keyword.cloud_notm}} fornece, como a identidade do app (ID do app), informações de segurança que são específicas para o cliente e o URI de acesso para o app. Os serviços móveis geralmente trabalham no contexto entre si para que as informações de contexto, como o nome do desenvolvedor de app e o usuário que usa o app, possam ser compartilhadas entre o conjunto de serviços.
* Para interagir com apps da web ou código de nuvem do lado do servidor para apps móveis, use as informações que o {{site.data.keyword.cloud_notm}} fornece, como as credenciais de tempo de execução na variável de ambiente *VCAP_SERVICES* do app. O valor da variável de ambiente *VCAP_SERVICES* é a serialização de um objeto JSON. A variável contém os dados de tempo de execução que são necessários para interagir com os serviços aos quais o app está ligado. O formato dos dados é diferente para serviços diferentes. Talvez seja necessário ler a documentação do serviço sobre o que deve-se esperar e como interpretar cada parte de informação.

Se um serviço que você ligar a um app travar, o app
pode parar a execução ou ter erros. O {{site.data.keyword.cloud_notm}} não reinicia automaticamente o app para recuperar desses problemas. Considere codificar seu app para identificar e recuperar de indisponibilidades, de exceções
e de falhas de conexão.

## Acessando serviços em ambientes de implementação do {{site.data.keyword.cloud_notm}}
{: #migrate_instance}

O {{site.data.keyword.cloud_notm}} oferece muitas opções de implementação e é possível acessar um serviço que está em execução em um ambiente por meio de um ambiente diferente. Por exemplo, se você tiver um serviço que esteja em execução no Cloud Foundry, será possível acessar esse serviço por meio de um app que está em execução em um cluster Kubernetes.

### Exemplo: acessar um serviço do Cloud Foundry por meio de um pod do Kubernetes

Para acessar um serviço do Cloud Foundry por meio de um pod em um cluster do Kubernetes, deve-se ligar o serviço ao cluster
para armazenar as credenciais de serviço em um segredo do Kubernetes. Em seguida, é possível disponibilizar essas informações para o
app. 
{: shortdesc}

Por padrão, as credenciais de serviço armazenadas em um segredo do Kubernetes têm codificação Base64 e são criptografadas em
etcd. 

**Importante**: não faça referência nem exponha as credenciais de serviço diretamente no arquivo YAML de implementação. Por padrão, os arquivos YAML de implementação não são projetados para reter os dados sensíveis e não
criptografam as credenciais de serviço. Para armazenar e acessar adequadamente essas informações, deve-se usar um segredo do Kubernetes. 

1. [ Ligar o serviço ao seu cluster ](/docs/containers?topic=containers-service-binding#bind-services). 
2. Para acessar as credenciais de serviço por meio do pod do app, escolha entre as opções a seguir. 
   - Monte o segredo como um volume em seu pod
   - Referencie o segredo em variáveis de ambiente

## Criando uma instância de serviço fornecida pelo usuário
{: #user_provide_services}

Você pode ter serviços que são gerenciados fora do {{site.data.keyword.cloud_notm}}. Se você tiver credenciais para acessar esses serviços externos na Internet, será possível criar instâncias de serviço fornecido pelo usuário do {{site.data.keyword.cloud_notm}} para representar e se comunicar com seus serviços externos.

Para criar uma instância de serviço fornecida pelo usuário e ligá-la a um app, conclua as etapas a seguir:

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

2. Ligar a instância de serviço ao seu app usando o comando `ibmcloud service bind`. Por
exemplo:

	```
	ibmcloud service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

Agora é possível configurar seu app para usar os serviços externos. Para obter informações sobre como configurar seu app para interagir com um serviço, consulte [Configurando seu app](/docs/apps?topic=creating-apps-add-resource#configure-app).
