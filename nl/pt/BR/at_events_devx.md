---

copyright:
  years: 2016, 2019
lastupdated: "2019-03-15"

keywords: apps, applications, activity tracking events

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:download: .download}
{:table: .aria-labeledby="caption"}

# Eventos do {{site.data.keyword.dev_console}}  {{site.data.keyword.cloudaccesstrailshort}}
{: #at_events}

Como um responsável pela segurança, auditor ou gerente, é possível usar o serviço {{site.data.keyword.cloudaccesstrailfull}} para controlar como os usuários e os aplicativos interagem com o {{site.data.keyword.dev_console}} no {{site.data.keyword.cloud}}.
{: shortdesc}

O serviço {{site.data.keyword.cloudaccesstrailfull_notm}} registra as atividades iniciadas pelo usuário que mudam o estado de um serviço no {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte  [ Sobre o  {{site.data.keyword.cloudaccesstrailshort}} ](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov).

## Onde visualizar os eventos
{: #view-events-ui}

Os eventos do {{site.data.keyword.cloudaccesstrailshort}} estão disponíveis no domínio da conta do {{site.data.keyword.cloudaccesstrailshort}} que está disponível na região do {{site.data.keyword.cloud_notm}} em que os eventos do {{site.data.keyword.dev_console}} são gerados.

Para iniciar o monitoramento de suas ações do usuário, consulte o [Tutorial de introdução](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started).

## Lista de eventos
{: #events}

A tabela a seguir lista as ações que geram um evento:

<table>
  <caption>Ações que geram eventos</caption>
  <tr>
    <th>Ações</th>
	  <th>Descrição</th>
  <tr>
  <tr>
    <td>bluemix-developer-experience.app.create</td>
	  <td>Um evento é gerado quando um usuário cria um aplicativo.</td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.read</td>
	  <td>Um evento é gerado quando qualquer uma das situações a seguir acontece: </br><ul><li>Um usuário faz download do código do aplicativo.</li> <li>Um usuário faz download do arquivo de credenciais usando a CLI do {{site.data.keyword.dev_console}}.</li> <li>A infraestrutura de experiência do desenvolvedor lê credenciais para recursos que estão associados a um aplicativo.</li> <li>Um usuário visualiza a lista de aplicativos, por exemplo, quando o usuário visualiza a lista de aplicativos no console do {{site.data.keyword.dev_console}} ou por meio da CLI do {{site.data.keyword.dev_cli_short}}.</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.update</td>
	  <td>Um evento é gerado quando qualquer uma das situações a seguir acontece: </br><ul><li>Algo sobre o aplicativo muda, por exemplo, quando um usuário modifica o nome do aplicativo. </li><li>Um novo recurso é criado e incluído em um aplicativo.</li><li>Um recurso existente é incluído em um aplicativo.</li><li>Um serviço é removido de um aplicativo.</li><li>O código é gerado para um aplicativo.</li><li>Uma cadeia de ferramentas DevOps é incluída por meio da experiência do desenvolvedor, por exemplo, selecionando *Implementar na nuvem*.</li></ul></td>
  </tr>
  <tr>
    <td>bluemix-developer-experience.app.delete</td>
	  <td>Um evento é gerado quando um usuário exclui um aplicativo.</td>
  </tr>
</table>
