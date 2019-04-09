---

copyright:
  years: 2017, 2018
lastupdated: "2017-01-26"

---

{:shortdesc: .shortdesc}

# 托管应用程序
{: #hosting}

如果您有现有应用程序，那么可以在包含所需的全部基础架构或平台服务的 IBM Cloud 上对其进行托管。对于现有应用程序，您可以利用 {{site.data.keyword.Bluemix_notm}} 基础架构来托管已专门针对 {{site.data.keyword.Bluemix_notm}} 开发的应用程序。
{:shortdesc}

## 迁移应用程序
{: #ht_hostapp}

对于现有应用程序，您可以将应用程序以递增方式迁移到 {{site.data.keyword.Bluemix_notm}} 中，而不是将应用程序完全转移到云环境中。您可以先迁移应用程序的一部分，然后使用 Cloud Integration 服务来连接到现有数据或记录系统。

对于 {{site.data.keyword.Bluemix_notm}} 应用程序，您可能需要访问后端数据或服务，例如记录系统。在 {{site.data.keyword.Bluemix_notm}} 中，可以使用 Secure Gateway 服务在 {{site.data.keyword.Bluemix_notm}} 组织和企业后端网络之间建立一条安全的隧道。该服务支持 {{site.data.keyword.Bluemix_notm}} 上的应用程序访问后端网络的数据和服务。有关详细信息，请参阅 [Reaching enterprise backend with Bluemix Secure Gateway via console ![外部链接图标](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}。

{{site.data.keyword.Bluemix_notm}} 可以托管现有应用程序，并提供所需的所有基础架构。在[目录](https://console.bluemix.net/catalog/?taxonomyNavigation=apps)中，可以选择是在裸机服务器上还是在虚拟服务器上托管应用程序。如何需要专用物理服务器以获得较高性能，那么[裸机](../bare-metal/index.html#about-bare-metal-servers)部署是最佳选择。如果工作负载在多个地理区域之间分布，并且您想要使用 {{site.data.keyword.Bluemix_notm}} 管理程序来管理部署，那么[虚拟](/vsi/vsi_index.html#provisioning-a-virtual-server)部署是最佳选择。

可以将应用程序的各部分一次性全部迁移到 {{site.data.keyword.Bluemix_notm}}，也可以逐个组件进行迁移。迁移应用程序时，请查看我们提供的几个服务。

* 选择适用于您的[存储器](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage)类型：块存储器、文件存储器或对象存储器。
* 选择需要的[网络](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork)类型。
* 选择[容器化](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers)服务以利用 {{site.data.keyword.Bluemix_notm}} Kubernetes 技术。

## 后续步骤
{: #next-steps}

如果服务可以在多个区域中进行托管，那么可以选择要在哪里托管应用程序。为此，请注册并将应用程序的定制 URL 信息添加到 {{site.data.keyword.Bluemix_notm}} 中。然后，选择托管应用程序的区域。有关如何部署应用程序的更多信息，请参阅[更新应用程序](updapps.html)。
