---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-03-16"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# Arquiteturas comuns para apps de nuvem
{: #patterns}

Os kits do iniciador no {{site.data.keyword.cloud_notm}} ajudam a produzir apps com uma arquitetura comprovada. Os apps são todos diferentes, mas quando você baseia seu app em um padrão arquitetural conhecido, é mais fácil obter um resultado confiável rapidamente. Ao criar um projeto por meio de um kit do iniciador, você está escolhendo um dos vários tipos padrão diferentes junto com os componentes, como um tempo de execução, para preencher o padrão.
{:shortdesc}

## App da web
{: #web}

O padrão App da web produz projetos que entregam conteúdo da web, como HTML, JavaScript e folhas de estilo, para o servidor da web. Há vários kits do iniciador de App da web.

* Básico - entrega um arquivo `index.html` estático, uma folha de estilo padrão e vazia e um arquivo JavaScript.
* React - uma rica estrutura para construir interfaces com o usuário. Os arquivos de origem estão em `src/client/app` e são compilados com o WebPack e entregues no diretório público.

É possível localizar kits do iniciador para o padrão App da web no painel do desenvolvedor de Serviço de aplicativo do [{{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## Backend for Frontend
{: #bff}

O padrão Backend for Frontend (BFF) ajuda a criar código de backend que expõe dados de negócios e serviços em um modo que corresponda às expectativas do usuário para um canal de app específico, como dispositivo móvel ou web. Por exemplo, os usuários em um dispositivo móvel podem usar o controle de voz, enquanto os usuários que consomem seu app por meio do navegador da web preferem apontar e clicar. É possível construir dois BFFs, uma para o dispositivo móvel que inclui serviços como o [{{site.data.keyword.conversationfull}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/watson/developercloud/conversation.html) e um para a web que tem uma interface com o usuário mais sofisticada.

No {{site.data.keyword.cloud_notm}}, é possível construir um BFF com abordagem de programação poliglota. É possível usar Node.js Swift, Java ou Python e executá-los em um padrão com os serviços de contêiner ou usando funções sem servidor.

O BFF gerencia a persistência de dados, o armazenamento em cache e a integração com serviços de alto valor como o [{{site.data.keyword.ibmwatson}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=watson), [{{site.data.keyword.iot_short_notm}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=iot), [{{site.data.keyword.weather_short}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/services/weather-company-data?taxonomyNavigation=apps) e [{{site.data.keyword.sparks}} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://console.bluemix.net/catalog/services/apache-spark?taxonomyNavigation=apps).

O BFF expõe uma API mais comumente usando um padrão de REST, mas é possível projetar o BFF para trabalhar de uma arquitetura de sistema de mensagens usando o {{site.data.keyword.messagehub}}.

Existem vários kits do iniciador do BFF dentre os quais é possível escolher dependendo dos seus requisitos de linguagem e estrutura.  É possível localizar kits do iniciador para o padrão BFF no painel do desenvolvedor do Serviço de aplicativo do [{{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## Microsserviço
{: #microservice}

Os projetos de microsserviço fornecem a base para construir microsserviços de backend, incluindo um terminal de funcionamento básico e API de REST. Os projetos gerados contêm todas as dependências necessárias tanto para o próprio microsserviço quanto para qualquer serviço de nuvem conectado.

Há vários kits do iniciador de microsserviço dentre os quais é possível escolher dependendo de seus requisitos de linguagem e estrutura.  É possível localizar kits do iniciador para o padrão Microsserviço no painel do desenvolvedor de Serviço de aplicativo do [{{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/appservice/dashboard).

## Dispositivo móvel
{: #mobile}

Os projetos móveis são diferentes dos outros padrões porque eles têm um componente significativo do lado do cliente. O padrão pode incluir conexão direta com serviços móveis, como notificações push, autenticação e analítica móvel, conhecido como padrão Mobile Backend as a Service ou MBaaS, ou pode ter um [Backend for Frontend](#bff) dedicado.  

O {{site.data.keyword.cloud_notm}} oferece vários kits do iniciador de dispositivo móvel para iOS Swift, Android e Cordova. É possível localizar kits do iniciador para o padrão Dispositivo móvel no [painel do desenvolvedor de Dispositivo móvel do {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/developer/mobile/dashboard).

## Idiomas
{: #languages}

Os kits do iniciador que o {{site.data.keyword.cloud_notm}} fornece estão disponíveis em várias linguagens e estruturas. Por exemplo, os kits do iniciador de microsserviço em nuvem oferecer uma opção Node.js, enquanto os kits do iniciador estreitamente relacionados à análise de dados podem incluir Python ou Go. Algumas linguagens comuns usadas nos kits do iniciador do {{site.data.keyword.cloud_notm}} são discutidas.


|Linguagem de programação | Descrição | Estruturas de desenvolvimento |
|-----|-----|-----|
|Java | O [Java](../runtimes/liberty/getting-started.html) tem capacidades comprovadas para a construção de aplicativos de grau corporativo. Mas os novos recursos em Java 8, combinados com os tempos de execução mais leves, como o Liberty e estruturas, como o Spring Boot, tornam o Java perfeitamente adequado para a construção de microsserviços também.  Além disso, o Java é uma linguagem de programação popular para apps Android. | Spring, Liberty, Android |
|Swift | O [Swift](../runtimes/swift/getting-started.html) é uma linguagem de programação moderna criada pela Apple em 2014 que foi projetada para substituir o uso do Objective C e o software livre em dezembro de 2015. Hoje, ela é usada para construir iOS, macOS, serviços da web e software de sistemas nos sistemas operacionais Linux e macOS usando a x86, ARM ou z/Architecture. É escrita como uma linguagem de script, mas é compilada para obter alto desempenho como C, com baixa sobrecarga, tornando-a ideal para tempos de execução de nuvem. Usa um sistema de tipo forte e estático visto em Java, mas o estilo funcional e as rotinas assíncronas vistos em JavaScript. Funciona de forma efetiva e o código-fonte compila para código nativo usando a cadeia de ferramentas do compilador LLVM e pode usar as bibliotecas de sistema externo escritas em C facilmente.  Como o Swift pode ser usado para codificar apps do lado do cliente e do lado do servidor, os desenvolvedores usam o Swift quando eles precisam migrar facilmente as funções do cliente para o servidor e vice-versa. | Kitura, iOS|
|Node.js | O [Node.js](../runtimes/nodejs/getting-started.html) é um tempo de execução JavaScript que usa um modelo de E/S acionado por eventos e sem bloqueio, tornando-o leve e eficiente, destacando-se no rendimento e escalabilidade para aplicativos da web, padrões backend-for-frontend e microsserviços. O ecossistema de pacote do Node.js, npm, fornece acesso a uma grande coleção de módulos de software livre, fornecendo uma ampla gama de recursos para acelerar o desenvolvimento de seu aplicativo. | Express|
|JavaScript|O JavaScript cria efeitos interativos em páginas da web. O JavaScript juntamente com HTML e CSS é a base da maioria das páginas da web. Quando agrupado com um plug-in Cordova, o código JavaScript pode aproveitar totalmente as funções do dispositivo nativo. Os desenvolvedores com qualificações da web podem criar apps móveis facilmente e, quando apropriado, o código do app pode ser reutilizado na web e no dispositivo móvel.|Cordova|
|Python | O [Python](../runtimes/python/getting-started.html) é uma linguagem de programação interpretada, de propósito geral, que coloca muita ênfase na capacidade de leitura. O Python permite que os programadores implementem funções com menos linhas de código que podem ser necessárias em outras linguagens. Os recursos na linguagem tornam possível escrever código orientado a objetos, funcional ou imperativo. O Python é comumente usado para processamento de tarefas de língua natural. | Flask, Django|

