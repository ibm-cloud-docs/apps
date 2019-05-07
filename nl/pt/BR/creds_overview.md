---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-25"

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

# Incluindo credenciais de serviço em seu ambiente de implementação
{: #credentials_overview}

Saiba como incluir manualmente as credenciais de serviço no ambiente de implementação.
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

Em geral, você deseja que a lógica de aplicativo adquira as credenciais de serviço sensíveis, como chaves de API
ou senhas do banco de dados, por meio do ambiente no qual o aplicativo é executado. Dessa forma, você não mantém as
credenciais no repositório de código-fonte. Os bancos de dados nos ambientes de integração contínua,
de pré-produção e de produção ficam em quarentena uns dos outros.

Se você criar um app usando um modelo de kit do iniciador, o ambiente será preparado automaticamente. Não importa se o destino de implementação é:
<!-- Add links to the new topics in the /docs/resources repo when available-->
  * Kubernetes
  * Cloud Foundry Public ou Cloud Foundry Enterprise Environment
  * Instância de servidor virtual (também o Docker local)
  
As etapas são fornecidas para como configurar o ambiente. Os kits do iniciador geram o código que usa uma
biblioteca dependente para tornar o código móvel para execução em qualquer um dos destinos de implementação. Por último, nenhuma
lógica de ramificação é usada para detectar em qual destino de implementação o aplicativo está em execução.

O administrador ou o engenheiro do DevOps é, então, responsável por preparar os ambientes com os controles de acesso
e as configurações adequados para disponibilizar ao aplicativo os valores requeridos por ele.

"Configurar entrega contínua" é uma etapa única que executa as tarefas principais a seguir:
 * Prepara o destino de implementação com os serviços, os recursos e as credenciais.
 * Cria uma cadeia de ferramentas do DevOps para construir e implementar o app nesse ambiente usando o
código que referencia corretamente as credenciais no ambiente.

No entanto, deve-se preparar o destino de implementação em qualquer um dos cenários a seguir:
 * Ao trazer seu próprio código.
 * Ao iniciar por meio de um modelo de kit do iniciador em branco.
 * Ao incluir um serviço em um app baseado em um kit do iniciador após ele ter sido implementado.

A preparação do ambiente é sempre executada para todas as credenciais para todos os serviços que estão associados a um app, e todos os `serviços` são listados no `manifest.yml`, mas nem todas as referências de credencial são colocadas no arquivo `mappings.json`. Nesses casos, é necessário que você mesmo coloque essas referências. Depois de decidir sobre um destino de implementação e não precisar da abstração da biblioteca `IBMCloudEnv`, consulte a seção "Seu código + (destino de implementação)" que se ajusta à sua decisão.
{: important}

Alguns kits do iniciador não incluem de forma alguma a referência para a dependência `IBMCloudEnv`, para `manifest.yml` ou para os arquivos `mappings.json`.
{: important}
