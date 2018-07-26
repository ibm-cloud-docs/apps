---

copyright:
  years: 2015, 2018
lastupdated: "2018-06-26"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}

# Incluindo um serviço em seu app
{: #add_service}

Ao criar um aplicativo com o {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.dev_console}}, é possível incluir recursos por meio da página de visão geral do aplicativo. No entanto, também é possível provisioná-los diretamente no catálogo do {{site.data.keyword.Bluemix_notm}}, fora do contexto de seu app.
{: shortdesc}

É possível solicitar uma instância do recurso e usá-la independentemente de seu app ou incluir a instância de recurso em seu app da página de visão geral do app. É possível provisionar um tipo específico de recurso (um serviço) diretamente do catálogo do {{site.data.keyword.Bluemix_notm}}.

## Descobrindo serviços
{: #discover_services}

É possível ver todos os serviços que estão disponíveis no {{site.data.keyword.Bluemix_notm}} das maneiras a seguir:

* No console do {{site.data.keyword.Bluemix_notm}}. Visualize o catálogo do {{site.data.keyword.Bluemix_notm}}.
* Na interface de linha de comandos ibmcloud. Use o `ibmcloud ofertas de serviço` comando.
* A partir de seu próprio aplicativo. Use a [API de serviços GET /v2/services ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window}.

É possível selecionar o serviço necessário ao desenvolver aplicativos. Depois de selecioná-lo, o {{site.data.keyword.Bluemix_notm}} provisiona o serviço. O processo de fornecimento pode ser diferente para tipos de serviços diferentes. Por exemplo, um serviço de banco de dados cria um banco de dados e um serviço de notificação push para aplicativos móveis gera informações de configuração.

O {{site.data.keyword.Bluemix_notm}} fornece os recursos de um serviço para o aplicativo usando uma instância de serviço. Uma instância de serviço pode ser compartilhada entre os aplicativos da web.

É possível também usar serviços que são hospedados em outras regiões, se esses serviços estiverem disponíveis nessas regiões. Esses serviços devem ser acessíveis pela internet e possuírem terminais de API. Deve-se codificar manualmente o aplicativo para usar esses serviços da mesma maneira que você codifica aplicativos externos ou ferramentas de terceiros para usar os serviços {{site.data.keyword.Bluemix_notm}}. Para obter informações adicionais, veja [Permitindo que aplicativos externos e ferramentas de terceiros usem os serviços do {{site.data.keyword.Bluemix_notm}}](#accser_external).

## Solicitando uma nova instância de serviço
{: #req_instance}

Para solicitar uma nova instância de serviço, deve-se usar a interface com o usuário do {{site.data.keyword.Bluemix_notm}} ou a interface da linha de comandos do {{site.data.keyword.Bluemix_notm}}.

**Nota:** ao especificar o nome do serviço, evite caracteres que não sejam alfabéticos ou numéricos, pois os resultados podem ser imprevisíveis.

Se você usar a interface com o usuário do {{site.data.keyword.Bluemix_notm}} para solicitar uma instância de serviço, conclua as etapas a seguir:

1. No catálogo do {{site.data.keyword.Bluemix_notm}}, clique no tile para o serviço que você deseja incluir. A página de detalhes do serviço é aberta.

2. Digite um nome no campo **Nome do serviço**. Um nome padrão é fornecido. É possível alterar o nome no campo ou mantê-lo inalterado.

3. Conclua mais campos ou seleções e, em seguida, clique em **CRIAR**.

Se você usar a interface da linha de comandos do {{site.data.keyword.Bluemix_notm}} para solicitar uma instância de serviço, conclua as etapas a seguir:

1. Use o comando `ibmcloud service offerings` para localizar o nome e o plano do serviço que você requer.

2. Use o comando a seguir para criar uma instância de serviço, em que service_name é o nome do serviço, service_plan é o plano do serviço e service_instance é o nome que você deseja usar para essa instância de serviço.

```
Ibmcloud create service_name service_plan service_instance de serviço
```

3. Use o comando a seguir para ligar a instância de serviço a um aplicativo, em que *appname* é o nome do aplicativo e service_instance é o nome da instância de serviço.

```
Service bind appname service_instance ibmcloud
```

É possível ligar uma instância de serviço apenas àquelas instâncias do app que estão no mesmo espaço ou organização. No entanto, é possível usar instâncias de serviço de outros espaços ou organizações da mesma maneira que um app externo faz. Em vez de criar uma ligação, use as credenciais para configurar sua instância do app diretamente. Para obter mais informações sobre como os aplicativos externos usam os serviços do {{site.data.keyword.Bluemix_notm}}, consulte [Ativando aplicativos externos para usar os serviços do {{site.data.keyword.Bluemix_notm}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](#accser_external){: new_window}.

## Configurando seu aplicativo
{: #config}

Depois de ligar uma instância de serviço ao aplicativo, deve-se configurar o aplicativo para interagir com o serviço.

Cada serviço pode requer um mecanismo diferente de comunicação com os aplicativos. Esses mecanismos são documentados como parte da definição de serviço para suas informações ao desenvolver aplicativos. Para consistência, os mecanismos são necessários para que seu aplicativo interaja com o serviço.

* Para interagir com os serviços de banco de dados, use as informações que o {{site.data.keyword.Bluemix_notm}} fornece como o ID do usuário, senha e o URI de acesso para o aplicativo.
* Para interagir com os serviços de backend móveis, use as informações que o {{site.data.keyword.Bluemix_notm}} fornece, como a identidade do aplicativo (ID do app), informações de segurança que são específicas para o cliente e o URI de acesso para o aplicativo. Os serviços móveis geralmente funcionam em contexto entre si para que as informações de contexto, como o nome do desenvolvedor de aplicativos e o usuário que usa o aplicativo, possam ser compartilhadas em todo o conjunto de serviços.
* Para interagir com os aplicativos da Web ou código do lado do servidor para aplicativos móveis, use as informações que o {{site.data.keyword.Bluemix_notm}} fornece como as credenciais de tempo de execução no ambiente *VCAP_SERVICES* do aplicativo. O valor da variável de ambiente *VCAP_SERVICES* é a serialização de um objeto JSON. A variável contém os dados de tempo de execução que são necessários para interagir com os serviços aos quais o aplicativo está ligado. O formato dos dados é diferente para serviços diferentes. Talvez seja necessário ler a documentação do serviço sobre o que deve-se esperar e como interpretar cada parte de informação.

Se um serviço ligado a um aplicativo ficar paralisado, o aplicativo pode ter parado de executar ou conter erros. O {{site.data.keyword.Bluemix_notm}} não reinicia automaticamente o aplicativo para recuperar desses problemas. Considere codificar o aplicativo para identificar e recuperar de indisponibilidades, exceções e falhas de conexão. Para obter mais informações, consulte [Os aplicativos não serão reinicializados automaticamente](/docs/troubleshoot/ts_apps.html#ts_apps_not_auto_restarted).

## Acessando serviços em ambientes de implementação do {{site.data.keyword.Bluemix_notm}}
{: #migrate_instance}

O {{site.data.keyword.Bluemix_notm}} oferece muitas opções de implementação e é possível acessar um serviço que está em execução em um ambiente por meio de um ambiente diferente. Por exemplo, se você tiver um serviço que está em execução no Cloud Foundry, será possível acessar esse serviço por meio de um aplicativo que está em execução em um cluster do Kubernetes.

### Exemplo: acessar uma instância de serviço do Compose no Cloud Foundry por meio de um pod do Kubernetes

Qualquer instância de serviço do Compose, como o {{site.data.keyword.composeForMongoDB}} ou o {{site.data.keyword.composeForRedis}}, é uma instância paga. Depois que você se sentir confortável com o uso de sua instância de serviço do Compose, como o {{site.data.keyword.composeForMongoDB}} no Kubernetes, poderá importar as credenciais da instância fornecida pelo Compose no Cloud Foundry.

1. Acesse **Credenciais** e recupere as suas credenciais da instância.

2. Abra o arquivo `values.yml` por meio do seu diretório de gráficos, por exemplo, `chart/project/`.

3. Configure os valores que são referenciados em seus ambientes de serviço. Por exemplo, no {{site.data.keyword.composeForMongoDB}}:

  ```
  services:
    mongo:
       url: {uri}
       dbName: {dbname}
       ca: {ca_certificate_base64}
       username: {username}
       password: {password}
       env: production

  ```

4. Abra o arquivo `bindings.yml` por meio do seu diretório de gráficos, por exemplo, `chart/project/`.

5. Inclua as referências de valores da chave definidas no arquivo `values.yml` no final da parte em que o bloco `env` é definido.

  ```
    env:
      - name: MONGO_URL
        value: {{ .Values.services.mongo.url }}
      - name: MONGO_DB_NAME
        value: {{ .Values.services.mongo.name }}
      - name: MONGO_USER
        value: {{ .Values.services.mongo.username }}
      - name: MONGO_PASS
        value: {{ .Values.services.mongo.password }}
      - name: MONGO_CA
        value: {{ .Values.services.mongo.ca }}
  ```

6. Em seu aplicativo, use suas variáveis de ambiente para iniciar o SDK do serviço que é fornecido para você.

  ```javascript
    const serviceManger = require('./services/serivce-manage.js');
    const mongoURL = process.env.MONGO_URL || 'localhost';
    const mongoUser = process.env.MONGO_USER || '';
    const mongoPass = process.env.MONGO_PASS || '';
    const mongoDBName = process.env.MONGO_DB_NAME || 'comments';
    const mongoCA = [new Buffer(process.env.MONGO_CA || '', 'base64')]

    const options = {
        useMongoClient: true,
        ssl: true,
        sslValidate: true,
        sslCA: mongoCA,
        poolSize: 1,
        reconnectTries: 1
    };

    const mongoDBClient = serviceManger.get('mongodb');
  ```

### Segredos (opcional)
{: #migrate_secrets_optional}

Não exponha as suas credenciais em seus arquivos `deployment.yml` ou `values.yml`. É possível usar uma sequência codificada Base64 ou criptografar as suas credenciais com uma chave. Para obter mais informações, consulte [Criando um segredo usando kubectl create secret ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://kubernetes.io/docs/concepts/configuration/secret/#creating-your-own-secrets) e [Como criptografar os seus dados ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://kubernetes.io/docs/tasks/administer-cluster/encrypt-data/)

## Ativando aplicativos externos
{: #accser_external}

Pode haver aplicativos que foram criados e executados fora do {{site.data.keyword.Bluemix_notm}} ou é possível usar ferramentas de terceiros. Se os serviços do {{site.data.keyword.Bluemix_notm}} fornecerem chaves de serviço acessíveis pela internet, será possível usar esses serviços com apps locais ou ferramentas de terceiros.

Os serviços a seguir fornecem chaves de serviço para você usar externamente:

* {{site.data.keyword.amashort_old}} <!--Advanced Mobile Access-->
* {{site.data.keyword.alchemyapishort}} <!--AlchemyAPI-->
* {{site.data.keyword.alertnotificationshort}} <!--Alert Notification-->
* {{site.data.keyword.sparks}} <!--Analytics for Apache Spark-->
* {{site.data.keyword.appseccloudshort}} <!--Application Security on Cloud-->
* {{site.data.keyword.blockchain}} <!--Blockchain-->
* {{site.data.keyword.cloudant}} <!--Cloudant&reg; NoSQL DB-->
* {{site.data.keyword.iotmapinsights_short}} <!--Context Mapping-->
* {{site.data.keyword.conversationshort}} <!--Conversation-->
* {{site.data.keyword.dashdbshort}} <!--dashDB-->
* {{site.data.keyword.discoveryshort}} <!--Discovery-->
* {{site.data.keyword.documentconversionshort}} <!--Document Conversion-->
* {{site.data.keyword.iotdriverinsights_short}} <!--Driver Behavior-->
* {{site.data.keyword.geospatialshort_Geospatial}} <!--Geospatial Analytics-->
* {{site.data.keyword.GlobalizationPipeline_short}} <!--Globalization Pipeline-->
* {{site.data.keyword.appconserviceshort}} <!--IBM&reg; App Connect-->
* {{site.data.keyword.dataworks_short}} <!--IBM&reg; Data Connect-->
* {{site.data.keyword.graphshort}} <!--IBM&reg; Graph-->
* {{site.data.keyword.iotelectronics_full}} <!--IBM&reg; IoT for Electronics-->
* {{site.data.keyword.twittershort}} <!--Insights for Twitter-->
* {{site.data.keyword.iot4auto_short}} <!--IoT for Automotive-->
* {{site.data.keyword.iotinsurance_short}} <!--IoT for Insurance-->
* {{site.data.keyword.languagetranslatorshort}} <!--Language Translator-->
* {{site.data.keyword.dwl_short}} <!--Lift-->
* {{site.data.keyword.messagehub}} <!--Message Hub-->
* {{site.data.keyword.mobileanalytics_short}} <!--Mobile Analytics-->
* {{site.data.keyword.nlclassifiershort}} <!--Natural Language Classifier-->
* {{site.data.keyword.objectstorageshort}} <!--Object Storage-->
* {{site.data.keyword.personalityinsightsshort}} <!--Personality Insights-->
* {{site.data.keyword.HybridConnect_short}} <!--Product Insights-->
* {{site.data.keyword.mobilepush}} <!--Push-->
* {{site.data.keyword.retrieveandrankshort}} <!--Retrieve and Rank-->
* {{site.data.keyword.speechtotextshort}} <!-- Speech to Text-->
* {{site.data.keyword.streaminganalyticsshort}} <!--Streaming Analytics-->
* {{site.data.keyword.texttospeechshort}} <!--Text to Speech-->
* {{site.data.keyword.toneanalyzershort}} <!--Tone Analyzer-->
* {{site.data.keyword.tradeoffanalyticsshort}} <!--Tradeoff Analytics-->
* {{site.data.keyword.weather_short}} <!--Weather Company Data-->
* {{site.data.keyword.workloadscheduler}} <!--Workload Scheduler-->

Para ativar um app externo ou ferramenta de terceiro para usar um serviço do {{site.data.keyword.Bluemix_notm}}, conclua as etapas a seguir:

1. Solicite uma instância do serviço.
    1. No Painel na interface com o usuário do {{site.data.keyword.Bluemix_notm}}, clique em **Criar recurso**. O catálogo é exibido.
    2. No catálogo, selecione o serviço desejado clicando no tile do serviço. A página de detalhes do serviço é aberta.
    3. Na janela de serviço, deixe a seleção de lista padrão **Conectar-se a:** como **Deixar desvinculado**. Essa seleção significa que o serviço não está conectado a um app {{site.data.keyword.Bluemix_notm}}.
    4. Faça qualquer outra seleção conforme necessário. Em seguida, clique em **Criar**. Uma instância de serviço é criada e o Painel de serviço é exibido.
2. No Painel de serviço, é possível selecionar **Credenciais de serviço** para visualizar ou incluir credenciais no formato JSON. Selecione um conjunto de credenciais e clique em **Visualizar credenciais** na coluna Ações. Use a chave de API que é exibida como as credenciais para se conectar à instância de serviço.

Seu aplicativo que é executado fora do {{site.data.keyword.Bluemix_notm}} agora poderá acessar o serviço do {{site.data.keyword.Bluemix_notm}}.

**Nota:** Se desejar excluir instâncias de serviço ou verificar as informações de faturamento, deve-se voltar para o Painel na interface com o usuário para gerenciar as instâncias de serviço.

## Criando uma instância de serviço fornecida pelo usuário
{: #user_provide_services}

Você pode ter serviços que são gerenciados fora do {{site.data.keyword.Bluemix_notm}}. Se você tiver credenciais para acessar esses serviços externos na Internet, será possível criar instâncias de serviço fornecido pelo usuário do {{site.data.keyword.Bluemix_notm}} para representar e se comunicar com seus serviços externos.

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

2. Bind the service instance to your application by using the `ibmcloud service bind` command. Por
exemplo:

	```
	ibmcloud service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

Agora é possível configurar o seu aplicativo para usar os serviços externos. Para obter informações sobre como configurar o seu aplicativo para interagir com um serviço, consulte [Configurando o seu aplicativo para interagir com um serviço ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](#config){: new_window}.

