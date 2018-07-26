---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-07-12"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# Arquiteturas comuns para apps de nuvem
{: #patterns}

Os kits do iniciador no {{site.data.keyword.cloud_notm}} ajudam a produzir apps com uma arquitetura comprovada. Os apps são todos diferentes, mas quando você baseia seu app em um padrão arquitetural conhecido, é mais fácil obter um resultado confiável rapidamente. Ao criar um app por meio de um kit do iniciador, você está escolhendo um dos vários tipos padrão diferentes junto com os componentes, como um tempo de execução, para preencher o padrão.
{:shortdesc}

## App da web
{: #web}

O padrão do app da web produz apps que entregam conteúdo da web, como HTML, JavaScript e folhas de estilo, para o servidor da web. O {{site.data.keyword.cloud_notm}}  oferece vários kits do iniciador de aplicativo da web.

* Básico - entrega um arquivo `index.html` estático, uma folha de estilo padrão e vazia e um arquivo JavaScript.
* React - uma rica estrutura para construir interfaces com o usuário. Os arquivos de origem estão em `src/client/app` e são compilados com o WebPack e entregues no diretório público.

É possível localizar kits do iniciador para o padrão de app da web no [Painel de desenvolvedor do {{site.data.keyword.cloud_notm}} App Service](https://console.bluemix.net/developer/appservice/dashboard).

## Backend-for-frontend
{: #bff}

O padrão Backend-for-frontend (BFF) ajuda a criar o código de backend que expõe dados de negócios e serviços de uma maneira que corresponda às expectativas do usuário para um canal de app específico, como para dispositivos móveis ou para a web. Por exemplo, os usuários em um dispositivo móvel podem usar controle de voz, enquanto os usuários do navegador da web preferem apontar e clicar. É possível construir dois BFFs, uma para o dispositivo móvel que inclui serviços como o [{{site.data.keyword.conversationfull}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/conversation.html) e um para a web que tem uma interface com o usuário mais sofisticada.

No {{site.data.keyword.cloud_notm}}, é possível construir um BFF com abordagem de programação poliglota. É possível usar Node.js, Swift, Java ou Python e executá-los em um padrão com serviços de contêiner ou que usam funções sem servidor.

O BFF gerencia a persistência de dados, o armazenamento em cache e a integração com os serviços de alto valor a seguir.

* [ {{site.data.keyword.ibmwatson}}  ![External link icon](../icons/launch-glyph.svg "External link icon") ](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=watson)
* [{{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=iot)
* [ {{site.data.keyword.weather_short}}  ![External link icon](../icons/launch-glyph.svg "External link icon") ](https://console.bluemix.net/catalog/services/weather-company-data?taxonomyNavigation=apps)
* [ {{site.data.keyword.sparks}}  ![External link icon](../icons/launch-glyph.svg "External link icon") ](https://console.bluemix.net/catalog/services/apache-spark?taxonomyNavigation=apps).

O BFF expõe uma API mais comumente usando um padrão de REST, mas é possível projetar o BFF para trabalhar por meio de uma arquitetura de sistema de mensagens que usa o {{site.data.keyword.messagehub}}.

Escolha um kit do iniciador do BFF para seus requisitos de linguagem e estrutura. É possível localizar kits do iniciador para o padrão BFF no painel do desenvolvedor do Serviço de aplicativo do [{{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## Microsserviço
{: #microservice}

Os apps de microsserviço fornecem a base para construir microsserviços de backend, incluindo um terminal de funcionamento básico e API de REST. Os apps gerados incluem todas as dependências requeridas para o microsserviço em si e para qualquer serviço de nuvem conectado.

Escolha um iniciador de microsserviços para seus requisitos de linguagem e estrutura. É possível localizar kits do iniciador para o padrão Microsserviço no painel do desenvolvedor de Serviço de aplicativo do [{{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## Dispositivo móvel
{: #mobile}

Os apps móveis são diferentes dos outros padrões porque eles têm um componente significativo do lado do cliente. O padrão pode incluir conexão direta com serviços móveis, tais como notificações push, autenticação e análise de dados móvel. Os serviços móveis são conhecidos como Backend móvel como serviço ou padrão MBaaS. Eles também podem ter um [Backend-for-frontend](#bff) dedicado.

O {{site.data.keyword.cloud_notm}} oferece vários kits do iniciador de dispositivo móvel para iOS Swift, Android e Cordova. É possível localizar kits do iniciador para o padrão Dispositivo móvel no [painel do desenvolvedor de Dispositivo móvel do {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/mobile/dashboard).

## Idiomas
{: #languages}

Os kits do iniciador que o {{site.data.keyword.cloud_notm}} fornece estão disponíveis em várias linguagens e estruturas. Por exemplo, os kits do iniciador de microsserviço em nuvem oferecer uma opção Node.js, enquanto os kits do iniciador estreitamente relacionados à análise de dados podem incluir Python ou Go. Algumas linguagens comuns usadas nos kits do iniciador do {{site.data.keyword.cloud_notm}} são discutidas.

|Linguagem de programação | Descrição | Estruturas de desenvolvimento |
|-----|-----|-----|
|Java |O [Java](../runtimes/liberty/getting-started.html) é excelente para a construção de aplicativos de classificação corporativa. Entretanto, novos recursos em Java 8, combinados com tempos de execução mais leves, como o Liberty, e com estruturas como o Spring Boot, significam que o Java também é excelente para construir microsserviços. O Java é uma linguagem de programação popular para apps Android. | Spring, Liberty, Android |
|Swift |O [Swift](../runtimes/swift/getting-started.html) é uma linguagem de programação moderna que foi criada em 2014, projetada para substituir o Objective C e o software livre em dezembro de 2015. Hoje, ele é usado para construir serviços do iOS, do macOS, da web e software de sistemas nos sistemas operacionais Linux e macOS que usam x86, ARM ou z/Architecture. Ele é escrito como uma linguagem de script, mas é compilado para obter alto desempenho semelhante ao C com baixo uso do processador. É ideal para tempos de execução de nuvem. Usa um sistema de tipo forte e estático visto em Java, mas o estilo funcional e as rotinas assíncronas vistos em JavaScript. Ele tem um bom desempenho e a origem é compilada para o código nativo que usa a cadeia de ferramentas do compilador LLVM. Ele pode usar bibliotecas do sistema de outras linguagens que são facilmente escritas em C. Como o Swift pode ser usado para codificar apps do lado do cliente e do lado do servidor, os desenvolvedores usam o Swift quando precisam migrar facilmente as funções do cliente para o servidor e vice-versa. | Kitura, iOS|
|Node.js |O [Node.js](../runtimes/nodejs/getting-started.html) é um tempo de execução de JavaScript que usa um modelo de E/S orientado a eventos e sem bloqueio, tornando-o leve e eficiente. Ele se destaca em rendimento e escalabilidade para aplicativos da web, padrões backend-for-front-end e microsserviços. O registro do pacote do Node.js, npm, fornece acesso a uma grande coleção de módulos de software livre. Ele fornece uma ampla variedade de recursos para acelerar o desenvolvimento do seu aplicativo. | Express|
|JavaScript|O JavaScript cria efeitos interativos em páginas da web. O JavaScript juntamente com HTML e CSS é a base da maioria das páginas da web. Quando agrupado com um plug-in Cordova, o código JavaScript pode aproveitar totalmente as funções do dispositivo nativo. Os desenvolvedores com qualificações da web podem criar apps móveis facilmente e, quando apropriado, o código do app pode ser reutilizado na web e no dispositivo móvel.|Cordova|
|Python |O [Python](../runtimes/python/getting-started.html) é uma linguagem de programação interpretada de propósito geral que enfatiza a capacidade de leitura. O Python permite que programadores implementem funções com menos linhas de código do que podem ser necessárias em outras linguagens. Os recursos na linguagem tornam possível escrever código orientado a objetos, funcional ou imperativo. O Python é comumente usado para processamento de tarefas de língua natural. | Flask, Django|


