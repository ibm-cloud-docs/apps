---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-01"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# Visão geral de credenciais
{: #credentials_overview}

Saiba como incluir manualmente as credenciais de serviço no ambiente de implementação.
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

Em geral, você deseja que a lógica de aplicativo adquira as credenciais de serviço sensíveis, como chaves de API
ou senhas do banco de dados, por meio do ambiente no qual o aplicativo é executado. Dessa forma, você não mantém as
credenciais no repositório de código-fonte. Os bancos de dados nos ambientes de integração contínua,
de pré-produção e de produção ficam em quarentena uns dos outros.

Se você criar um app usando um modelo de kit do iniciador, o ambiente será preparado automaticamente. Não importa se o destino de implementação é:
  * [Kubernetes](/docs/apps/creds_kube.html#add-credentials-kube)
  * [Cloud Foundry Public ou Cloud Foundry Enterprise Environment](/docs/apps/creds_cf.html#add-credentials-cf)
  * [Instância de servidor virtual (também docker local)](/docs/apps/creds_vsi.html#add-credentials-vsi)
  
As etapas são fornecidas para como configurar o ambiente. Os kits do iniciador geram o código que usa uma
biblioteca dependente para tornar o código móvel para execução em qualquer um dos destinos de implementação. Por último, nenhuma
lógica de ramificação é usada para detectar em qual destino de implementação o aplicativo está em execução.

O administrador ou o engenheiro do DevOps é, então, responsável por preparar os ambientes com os controles de acesso
e as configurações adequados para disponibilizar ao aplicativo os valores requeridos por ele.

"Implementar na nuvem" é uma etapa única que executa as principais tarefas a seguir:
 * Prepara o ambiente de implementação de destino com os serviços, os recursos e as credenciais.
 * Cria uma cadeia de ferramentas do DevOps para construir e implementar o app nesse ambiente usando o
código que referencia corretamente as credenciais no ambiente.

No entanto, deve-se preparar o ambiente de implementação de destino em qualquer um dos cenários a seguir:
 * Ao trazer seu próprio código.
 * Ao iniciar por meio de um modelo de kit do iniciador em branco.
 * Ao incluir um serviço em um app baseado em kit do iniciador _depois_ que ele foi implementado.




