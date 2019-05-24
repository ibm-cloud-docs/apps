---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-10"

keywords: apps, credentials, service, add service credentials, environment, deployment

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# Incluindo manualmente as credenciais de serviço em seu ambiente de implementação
{: #credentials_overview}

Você deseja que sua lógica de aplicativo adquira credenciais de serviço sensíveis, como chaves de API do banco de dados ou senhas, por meio do ambiente no qual o aplicativo é executado. Dessa forma, você não precisa manter as credenciais no repositório de código-fonte.
{: shortdesc}

Se você criar um app usando um kit do iniciador, o ambiente será preparado para você automaticamente. Quando você conecta um serviço ao seu kit do iniciador antes de implementar seu app, as credenciais de serviço são automaticamente incluídas em seu ambiente.
{ :dica}

Deve-se incluir manualmente as credenciais de serviço em seu ambiente de implementação em qualquer um dos cenários a seguir:

 * Ao trazer seu próprio código.
 * Você inclui um serviço em um app baseado em kit do iniciador depois que o app é implementado.

O processo para incluir as credenciais de serviço depende de seu destino de implementação e de sua linguagem de programação. Para obter mais informações sobre como configurar as credenciais de serviço para o destino de implementação, consulte a documentação que é específica para o seu ambiente de hospedagem:

  * [{{site.data.keyword.containershort}}](/docs/containers?topic=containers-service-binding#adding_app)
  * Cloud Foundry Public ou {{site.data.keyword.cfee_full}}
  * Instância do servidor virtual (contêiner de docker local)

Muitas linguagens e estruturas fornecem bibliotecas padrão para configurações específicas do aplicativo e específicas do ambiente. Para obter mais informações, consulte os guias de programação a seguir:

* [Java: Trabalhando com credenciais de serviço](/docs/java?topic=cloud-native-configuration)
* [Configurando o ambiente Node.js](/docs/node?topic=nodejs-configure-nodejs)
* [Configurando o ambiente Spring](/docs/java?topic=java-spring-configuration)
* [Configurando o ambiente Swift](/docs/swift?topic=swift-configuration)
* [Configurando o ambiente do Go](/docs/go?topic=go-configure-go-env)
