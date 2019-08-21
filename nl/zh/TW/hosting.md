---

copyright:
  years: 2017, 2019
lastupdated: "2019-06-25"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 選擇管理環境
{: #hosting}

如果您具有現有應用程式，則可以在具有所有必要基礎架構或平台服務的 {{site.data.keyword.cloud}} 上進行管理。
{:shortdesc}

使用 {{site.data.keyword.cloud_notm}}，您不需要再對硬體進行大型投資，即可測試或執行新的應用程式。相反地，我們會為您管理它，而且只會對您使用的部分進行收費。您的雲端伺服器環境是基礎架構層的基礎。您可以針對更複雜的環境選擇單一選項或一個組合。 

您有各種選項可以管理應用程式，並讓您依想要的方式或需要更深入地控制基礎架構。您可以使用下列任何方式來執行應用程式：

  * 作為 Kubernetes 叢集上的 Docker 容器
  * 作為 Cloud Foundry 應用程式
  * 作為無伺服器函數
  * 作為 VMware
  * 作為虛擬機器
  * 在高效能 {{site.data.keyword.baremetal_short}} 上 
  
<!--
{{site.data.keyword.baremetal_short}} are single-tenant, physical servers that are dedicated to a single customer. You control almost everything from the server host to the RAM and storage devices. These servers are used with workloads that require compute power over a sustained time, for example, several months.

Some example workloads include e-commerce, ERP, CRM, SCM, and financial services and regulatory applications.

{{site.data.keyword.BluVirtServers_short}} can be deployed as either as public or dedicated instances. With public instances, the resources of the server are shared with other customers, also known as a multi-tenant environment. Private instances dedicate the resources of the physical server to one customer who can have one or more virtual machines on the same server. These servers are ideal for workloads that run for a limited time, for example, a couple of weeks. Some workload examples are development and testing, backup and recovery, and disaster recovery. For more information about server options, see [Bare metal servers versus virtual servers: Choosing the best option for you](https://www.ibm.com/cloud/blog/bare-metal-virtual-servers-works){: new_window} ![External link icon](../icons/launch-glyph.svg "External link icon").
-->

如需運算選項的摘要，請查看下表。

| 選項 | 說明                                                  | 
|--------|---------------|
| [{{site.data.keyword.containerlong_notm}}](/docs/containers?topic=containers-getting-started) | 結合 Docker 容器、Kubernetes 技術、直覺式使用者體驗以及內建安全和隔離，來自動化部署、操作、調整與監視運算主機叢集中的容器化應用程式。|
| [{{site.data.keyword.cfee_full_notm}}](/docs/cloud-foundry?topic=cloud-foundry-about) | 隨需應變實例化多個隔離的企業級 Cloud Foundry 平台。|
| [{{site.data.keyword.openwhisk_short}}](/docs/openwhisk?topic=cloud-functions-getting_started) | 以 Apache OpenWhisk 為基礎的「函數即服務 (FaaS)」程式設計平台。|
| [{{site.data.keyword.vmwaresolutions_short}}](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started) | 藉由使用可擴充、安全和高效能基礎架構以及領先業界的 VMware 混合式虛擬化技術，快速且無縫地整合或移轉內部部署 VMware 工作負載。|
| [{{site.data.keyword.BluVirtServers_short}}](/docs/vsi?topic=virtual-servers-about-public-virtual-servers) | 與專用核心及記憶體配置一起購買的可擴充虛擬伺服器。|
| [{{site.data.keyword.baremetal_short}}](/docs/bare-metal?topic=bare-metal-about-bm)  | 由您專用且未與其他客戶共用任何部分（包括伺服器資源）的每小時或每月單一伺服器伺服器。|
{: caption="表 1. 運算選項" caption-side="top"}

