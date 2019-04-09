---

copyright:
  years: 2017, 2018
lastupdated: "2018-01-18"

---

{:shortdesc: .shortdesc}

# 托管应用程序
{: #hosting}

如果您有现有应用程序，那么可以在包含所需的全部基础架构或平台服务的 IBM Cloud 上对其进行托管。您还可以利用 {{site.data.keyword.Bluemix_notm}} 基础架构来托管已专门针对 {{site.data.keyword.Bluemix_notm}} 开发的应用程序。
{:shortdesc}

## 迁移应用程序
{: #ht_hostapp}

您可以将应用程序以递增方式迁移到 {{site.data.keyword.Bluemix_notm}} 中，而不是将应用程序完全转移到云环境中。您可以先迁移应用程序的一部分，然后使用 Cloud Integration 服务来连接到现有数据或记录系统。

对于 {{site.data.keyword.Bluemix_notm}} 应用程序，您可能需要访问后端数据或服务，例如记录系统。在 {{site.data.keyword.Bluemix_notm}} 中，可以使用 Secure Gateway 服务在 {{site.data.keyword.Bluemix_notm}} 组织和企业后端网络之间建立一条安全的隧道。该服务支持 {{site.data.keyword.Bluemix_notm}} 上的应用程序访问后端网络的数据和服务。有关详细信息，请参阅 [Reaching enterprise backend with Bluemix Secure Gateway via console ![外部链接图标](../icons/launch-glyph.svg)](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window}。

{{site.data.keyword.Bluemix_notm}} 可以托管现有应用程序，并在 {{site.data.keyword.Bluemix_notm}} 中提供所有基础架构。在[目录](https://console.bluemix.net/catalog/?taxonomyNavigation=apps)中，可以选择是在云上的裸机服务器上还是在虚拟服务器上托管应用程序。

可以将应用程序的各部分一次性全部迁移到 {{site.data.keyword.Bluemix_notm}}，也可以逐个组件进行迁移。迁移应用程序时，请查看我们提供的几个服务。

* 选择适用于您的[存储器](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slstorage)类型：块存储器、文件存储器或对象存储器。
* 选择需要的[网络](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=slnetwork)类型。
* 选择[容器化](https://console.bluemix.net/catalog/?taxonomyNavigation=apps&category=containers)服务以利用 {{site.data.keyword.Bluemix_notm}} Kubernetes 技术。

## 后续步骤
{: #next-steps}

如果服务可以在多个区域中进行托管，那么可以选择要在哪里托管应用程序。在[更新应用程序](updapps.html)中，可以选择托管应用程序的区域，并编辑定制 URL。
