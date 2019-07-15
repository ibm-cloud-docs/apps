---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-20"

keywords: supported architecture, supported languages cloud, web app, microservices, mobile, programming languages, app types, common architecture, cloud app, developer console, app service

subcollection: creating-apps

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:note:.deprecated}

# Arquiteturas comuns para apps de nuvem
{: #patterns}

Os kits do iniciador no {{site.data.keyword.cloud_notm}} ajudam a produzir aplicativos com uma arquitetura comprovada. Os apps são todos diferentes, mas quando você baseia seu app em um padrão arquitetural conhecido, é mais fácil obter um resultado confiável rapidamente. Ao criar um app por meio de um kit do iniciador, você está escolhendo um dos vários tipos padrão diferentes junto com os componentes, como um tempo de execução, para preencher o padrão.
{:shortdesc}

## Apps da web
{: #web}

O padrão do app da web produz apps que entregam conteúdo da web, como HTML, JavaScript e folhas de estilo, para o servidor da web. O {{site.data.keyword.cloud_notm}}  oferece vários kits do iniciador de aplicativo da web.

* Básico - entrega um arquivo `index.html` estático, uma folha de estilo padrão e vazia e um arquivo JavaScript.
* React - uma rica estrutura para construir interfaces com o usuário. Os arquivos de origem estão em `src/client/app` e são compilados com o WebPack e entregues no diretório público.

É possível localizar kits do iniciador para o padrão de app da web no [console do desenvolvedor do {{site.data.keyword.cloud_notm}} App Service](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

## Apps de microsserviço
{: #microservice}

Os apps de microsserviço fornecem a base para construir microsserviços de backend, incluindo um terminal de funcionamento básico e API de REST. Os apps gerados incluem todas as dependências requeridas para o microsserviço em si e para qualquer serviço de nuvem conectado.

Escolha um kit do iniciador de microsserviço para seus requisitos de linguagem e estrutura. É possível localizar kits do iniciador para o padrão de Microsserviço no [console do desenvolvedor do {{site.data.keyword.cloud_notm}} App Service](https://{DomainName}/developer/appservice/dashboard){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

## Apps móveis
{: #mobile}

Os apps móveis são diferentes dos outros padrões porque eles têm um componente significativo do lado do cliente. O padrão pode incluir conexão direta com serviços móveis, tais como notificações push, autenticação e análise de dados móvel. Os serviços móveis são conhecidos como Backend móvel como serviço ou padrão MBaaS. Eles também podem ter um Back-end para front-end dedicado.

O {{site.data.keyword.cloud_notm}} oferece vários kits do iniciador de dispositivo móvel para iOS Swift, Android e Cordova. É possível localizar kits do iniciador para o padrão de Dispositivo Móvel no [console do desenvolvedor do {{site.data.keyword.cloud_notm}} Mobile](https://{DomainName}/developer/mobile/dashboard){: new_window} ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo").

Além disso, é possível criar um app móvel customizado usando um kit do iniciador básico e selecionando o tipo de app móvel. Para obter mais informações, consulte [Criando um app móvel](/docs/apps?topic=creating-apps-tutorial-mobile).

## Apps baseados em linguagem
{: #languages}

Os kits do iniciador que o {{site.data.keyword.cloud_notm}} fornece estão disponíveis em várias linguagens e estruturas. Por exemplo, os kits do iniciador de microsserviço em nuvem oferecem uma opção Node.js, enquanto os kits do iniciador que estão estreitamente relacionados à análise de dados podem incluir Python ou Go. Algumas linguagens comuns usadas nos kits do iniciador do {{site.data.keyword.cloud_notm}} são discutidas.

|Linguagem de programação | Descrição | Estruturas de desenvolvimento |
|-----|-----|-----|
|Java | O [Java](/docs/runtimes/liberty?topic=liberty-getting-started) é ótimo para construir apps de classificação corporativa. Entretanto, novos recursos em Java 8, combinados com tempos de execução mais leves, como o Liberty, e com estruturas como o Spring Boot, significam que o Java também é excelente para construir microsserviços. O Java é uma linguagem de programação popular para apps Android. | Spring, Liberty, Android |
|Swift | O [Swift](/docs/runtimes/swift?topic=Swift-getting-started) é uma linguagem de programação moderna que foi criada em 2014, projetada para substituir o Objective C e o software livre em dezembro de 2015. Hoje, ele é usado para construir serviços do iOS, do macOS, da web e software de sistemas nos sistemas operacionais Linux e macOS que usam x86, ARM ou z/Architecture. Ele é escrito como uma linguagem de script, mas é compilado para obter alto desempenho semelhante ao C com baixo uso do processador. É ideal para tempos de execução de nuvem. Usa um sistema de tipo forte e estático visto em Java, mas o estilo funcional e as rotinas assíncronas vistos em JavaScript. Ele tem um bom desempenho e a origem é compilada para o código nativo que usa a cadeia de ferramentas do compilador LLVM. Ele pode usar bibliotecas do sistema de outras linguagens que são facilmente escritas em C. Como o Swift pode ser usado para codificar apps do lado do cliente e do lado do servidor, os desenvolvedores usam o Swift quando precisam migrar facilmente as funções do cliente para o servidor e vice-versa. | Kitura, iOS|
|Node.js | O [Node.js](/docs/runtimes/nodejs?topicid=Nodejs-getting-started) é um tempo de execução de JavaScript que usa um modelo de E/S orientado a eventos e sem bloqueio, tornando-o leve e eficiente. Ele se destaca no rendimento e escalabilidade para apps da web, padrões de back-end para front-end e microsserviços. O registro do pacote do Node.js, npm, fornece acesso a uma grande coleção de módulos de software livre. Ele fornece uma ampla gama de recursos para acelerar seu desenvolvimento de app. | Express|
|JavaScript|O JavaScript cria efeitos interativos em páginas da web. O JavaScript juntamente com HTML e CSS é a base da maioria das páginas da web. Quando agrupado com um plug-in Cordova, o código JavaScript pode aproveitar totalmente as funções do dispositivo nativo. Os desenvolvedores com qualificações da web podem criar apps móveis facilmente e, quando apropriado, o código do app pode ser reutilizado na web e no dispositivo móvel.|Cordova|
|Python | O [Python](/docs/runtimes/python?topic=Python-getting_started) é uma linguagem de programação interpretada de propósito geral que enfatiza a capacidade de leitura. O Python permite que programadores implementem funções com menos linhas de código do que podem ser necessárias em outras linguagens. Os recursos na linguagem tornam possível escrever código orientado a objetos, funcional ou imperativo. O Python é comumente usado para processamento de tarefas de língua natural. | Flask, Django |
{: caption="Tabela 1. Linguagens que são usadas em kits do iniciador" caption-side="top"}
