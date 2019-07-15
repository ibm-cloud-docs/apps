---

copyright:
  years: 2017, 2019
lastupdated: "2019-06-25"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 选择托管环境
{: #hosting}

如果您有现有应用程序，可将其托管在包含全部所需基础架构或平台服务的 {{site.data.keyword.cloud}} 上。
{:shortdesc}

借助 {{site.data.keyword.cloud_notm}}，您无需再对硬件进行大笔投资来测试或运行新应用程序。我们会为您管理一切，并且只对您使用的内容收取费用。云服务器环境是基础架构层的基础。您可以为更复杂的环境选择单个选项或选项组合。 

您有多种选项可用于托管应用程序，这使您可以拥有所需的基础架构掌控力。可以使用以下任何一种方法来运行应用程序：

  * 作为 Kubernetes 集群上的 Docker 容器
  * 作为 Cloud Foundry 应用程序
  * 作为无服务器功能
  * 作为 VMware
  * 作为虚拟机
  * 在高性能 {{site.data.keyword.baremetal_short}} 上运行 
<!--
{{site.data.keyword.baremetal_short}} are single-tenant, physical servers that are dedicated to a single customer. You control almost everything from the server host to the RAM and storage devices. These servers are used with workloads that require compute power over a sustained time, for example, several months.

Some example workloads include e-commerce, ERP, CRM, SCM, and financial services and regulatory applications.

{{site.data.keyword.BluVirtServers_short}} can be deployed as either as public or dedicated instances. With public instances, the resources of the server are shared with other customers, also known as a multi-tenant environment. Private instances dedicate the resources of the physical server to one customer who can have one or more virtual machines on the same server. These servers are ideal for workloads that run for a limited time, for example, a couple of weeks. Some workload examples are development and testing, backup and recovery, and disaster recovery. For more information about server options, see [Bare metal servers versus virtual servers: Choosing the best option for you](https://www.ibm.com/cloud/blog/bare-metal-virtual-servers-works){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").
-->

请查看下表以获取计算选项的摘要。

|选项|描述
| 
|--------|---------------|
| [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started) |将 Docker 容器、Kubernetes 技术、直观的用户体验和内置安全性与隔离功能组合在一起，自动对计算主机集群中的容器化应用程序进行部署、操作、扩展和监视。|
| [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) |按需实例化多个隔离的企业级 Cloud Foundry 平台。|
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-getting_started) |基于 Apache OpenWhisk 的函数即服务 (FaaaS) 编程平台。|
| [{{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started) |使用安全、可扩展的高性能基础架构和行业领先的 VMware 混合虚拟化技术，快速无缝地集成或迁移内部部署 VMware 工作负载。|
| [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-public-virtual-servers) |可扩展的虚拟服务器，随专用核心和内存分配一起购买。|
| [{{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-about-bm)  |专供您使用的按小时或按月计费的单租户服务器，任何部分（包括服务器资源）都不会与其他客户共享。|
{: caption="表 1. 计算选项" caption-side="top"}

