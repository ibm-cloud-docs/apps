---

copyright:
  years: 2017, 2019
lastupdated: "2019-06-25"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# Escolhendo o ambiente de hospedagem
{: #hosting}

Se você tiver um aplicativo existente, será possível hospedá-lo no {{site.data.keyword.cloud}} com todos os serviços de infraestrutura ou de plataforma necessários.
{:shortdesc}

Com o {{site.data.keyword.cloud_notm}}, não é mais necessário fazer grandes investimentos em hardware para testar ou executar um novo app. Em vez disso, nós gerenciamos tudo por você e cobramos apenas pelo que você usa. O
ambiente do servidor em nuvem é a base da camada de infraestrutura. É possível escolher uma única opção ou uma combinação para ambientes mais complexos. 

Há várias opções para hospedar os apps, o que dá a você o máximo controle sobre a infraestrutura conforme você
deseja ou precisa. É possível executar o app de uma das maneiras a seguir:

  * Como um contêiner do Docker em um cluster do Kubernetes
  * Como um app do Cloud Foundry
  * Como uma função sem servidor
  * Como uma VMware
  * Como uma máquina virtual
  * Em {{site.data.keyword.baremetal_short}} de alto desempenho 
<!--
{{site.data.keyword.baremetal_short}} are single-tenant, physical servers that are dedicated to a single customer. You control almost everything from the server host to the RAM and storage devices. These servers are used with workloads that require compute power over a sustained time, for example, several months.

Some example workloads include e-commerce, ERP, CRM, SCM, and financial services and regulatory applications.

{{site.data.keyword.BluVirtServers_short}} can be deployed as either as public or dedicated instances. With public instances, the resources of the server are shared with other customers, also known as a multi-tenant environment. Private instances dedicate the resources of the physical server to one customer who can have one or more virtual machines on the same server. These servers are ideal for workloads that run for a limited time, for example, a couple of weeks. Some workload examples are development and testing, backup and recovery, and disaster recovery. For more information about server options, see [Bare metal servers versus virtual servers: Choosing the best option for you](https://www.ibm.com/cloud/blog/bare-metal-virtual-servers-works){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").
-->

Consulte a tabela a seguir para obter um resumo das opções de cálculo.

| Opção | Descrição | 
|--------|---------------|
| [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started) | Combina os contêineres do Docker, a tecnologia do Kubernetes, uma experiência de usuário intuitiva e a segurança e o isolamento integrados para automatizar a implementação, a operação, o ajuste de escala e o monitoramento de apps armazenados em contêiner em um cluster de hosts de cálculo. |
| [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) | Instanciação de múltiplas plataformas Cloud Foundry isoladas de classificação corporativa sob demanda. |
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-getting_started) | Uma plataforma de programação Functions-as-a-Service (FaaS) baseada no Apache OpenWhisk. |
| [{{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started) | Integração ou migração rápida e contínua das cargas de trabalho do VMware no local usando infraestrutura escalável, segura e de alto desempenho e a tecnologia de virtualização híbrida do VMware líder do mercado. |
| [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-public-virtual-servers) | Servidores virtuais escaláveis que são comprados com núcleos dedicados e alocações de memória. |
| [{{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-about-bm)  | Servidores de locatário único, por hora ou mensais, que são dedicados a você e não compartilhados em nenhuma parte, incluindo os recursos do servidor, com outros clientes. |
{: caption="Tabela 1. Opções de cálculo" caption-side="top"}

