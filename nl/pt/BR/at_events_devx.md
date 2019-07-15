---

copyright:
  years: 2016, 2019
lastupdated: "2019-06-04"

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
{:deprecated: .deprecated}
{:table: .aria-labeledby="caption"}

# Eventos do {{site.data.keyword.dev_console}}  {{site.data.keyword.cloudaccesstrailshort}}
{: #at_events}

Como um responsável pela segurança, auditor ou gerente, é possível usar o serviço {{site.data.keyword.cloudaccesstrailfull}} para controlar como os usuários e os aplicativos interagem com o {{site.data.keyword.dev_console}} no {{site.data.keyword.cloud}}.
{: shortdesc}

O {{site.data.keyword.cloudaccesstrailfull}} foi descontinuado. A partir de 9 de maio
de 2019, não será possível provisionar novas instâncias do {{site.data.keyword.cloudaccesstrailshort}} e
o acesso às instâncias do plano *Lite* será removido. As instâncias existentes do plano premium são suportadas até 30 de setembro de 2019. Para continuar o monitoramento da atividade de sua conta do {{site.data.keyword.cloud_notm}}, provisione uma instância do [{{site.data.keyword.at_full}}](/docs/services/Activity-Tracker-with-LogDNA?topic=logdnaat-getting-started#getting-started).
{: deprecated}

O serviço {{site.data.keyword.cloudaccesstrailfull_notm}} registra as atividades iniciadas pelo usuário que mudam o estado de um serviço no {{site.data.keyword.cloud_notm}}. Para obter mais informações, consulte  [ Sobre o  {{site.data.keyword.cloudaccesstrailshort}} ](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-activity_tracker_ov).

## Onde visualizar os eventos
{: #view-events-ui}

Os eventos do {{site.data.keyword.cloudaccesstrailshort}} estão disponíveis no domínio da conta do {{site.data.keyword.cloudaccesstrailshort}} que está disponível na região do {{site.data.keyword.cloud_notm}} em que os eventos do {{site.data.keyword.dev_console}} são gerados.

Para iniciar o monitoramento de suas ações do usuário, consulte o [Tutorial de introdução](/docs/services/cloud-activity-tracker?topic=cloud-activity-tracker-getting-started).

## Lista de eventos
{: #events}

A tabela a seguir lista as ações que geram um evento:

|Ações	|Descrição	|
|-----|-------------|
|bluemix-developer-experience.app.create |Um evento é gerado quando um usuário cria um app.|
|bluemix-developer-experience.app.read |Um evento é gerado quando qualquer uma das situações a seguir acontece:<br><br>Um usuário faz download do código do app.<br><br>Um usuário faz download do arquivo de credenciais usando a CLI do {{site.data.keyword.dev_console}}.<br><br>A infraestrutura do {{site.data.keyword.cloud_notm}} lê credenciais para serviços que estão associados a um app.<br><br>Um usuário visualiza a lista de apps. Por exemplo, um usuário visualiza a lista de apps no console do {{site.data.keyword.dev_console}} ou por meio da CLI do {{site.data.keyword.dev_cli_short}}.|
|bluemix-developer-experience.app.update |Um evento é gerado quando qualquer uma das situações a seguir acontece:<br><br>Algo sobre as mudanças de app. Por exemplo, um usuário modifica o nome do app.<br><br>Um novo serviço é criado e incluído em um app.<br><br>Um serviço existente é incluído em um app.<br><br>Um serviço é removido de um app.<br><br>O código é gerado para um app.<br><br>Uma cadeia de ferramentas do DevOps é incluída por meio do console do {{site.data.keyword.cloud_notm}}. Por exemplo, um usuário seleciona **Configurar entrega contínua** na página Detalhes do app.|
|bluemix-developer-experience.app.delete |Um evento é gerado quando um usuário exclui um app. |
{: caption="Tabela 1. Ações que geram eventos" caption-side="top"}
