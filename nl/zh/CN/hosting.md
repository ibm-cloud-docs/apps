---

copyright:
  years: 2017, 2019
lastupdated: "2019-03-29"

keywords: apps, application, migrating apps, hosting apps, migrating, hosting, migration

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 迁移和托管应用程序
{: #hosting}

如果您有现存的应用程序，可将其托管在包含全部所需基础架构或平台服务的 {{site.data.keyword.cloud}} 上。您还可以将应用程序以增量方式迁移到 {{site.data.keyword.cloud_notm}}，而不是一次性将应用程序整体转移到云环境。

## 迁移应用程序
{: #migrating}

如果您需要应用程序访问内部部署数据或服务，那么可以使用 [{{site.data.keyword.SecureGatewayfull}}](/docs/services/SecureGateway?topic=securegateway-getting-started-with-sg#getting-started-with-sg) 在 {{site.data.keyword.cloud_notm}} 组织和企业后端网络之间建立一条安全的隧道。有关详细信息，请参阅 [Reaching enterprise backend with {{site.data.keyword.cloud_notm}} Secure Gateway via console ](https://developer.ibm.com/bluemix/2015/04/01/reaching-enterprise-backend-bluemix-secure-gateway/){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")。

如果您需要有关迁移的帮助，可以使用 [{{site.data.keyword.cloud_notm}} Migration Services ](https://www.ibm.com/cloud/migration-services){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")。

## 托管应用程序
{: #ht_hostapp}

在 {{site.data.keyword.cloud_notm}} [目录](https://{DomainName}/catalog/?taxonomyNavigation=apps){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 中，可以选择 Kubernetes 或 Cloud Foundry 等受管环境，也可以直接在裸机服务器或虚拟服务器上托管应用程序。

在虚拟部署上，应用程序的大部分操作由 {{site.data.keyword.cloud_notm}} 管理。如果工作负载在多个地理区域之间分布，并且您想要使用 {{site.data.keyword.cloud_notm}} 管理程序来管理部署，那么[虚拟](/docs/vsi?topic=virtual-servers-about-virtual-servers#about-virtual-servers)部署是最佳选择。如果需要直接访问专用物理服务器以获得更高性能，那么[裸机](/docs/bare-metal?topic=bare-metal-bm-getting-started#getting-started)部署是最佳选择。

您还有多个选项可用于：
* 从块存储器、文件存储器或对象存储器中，选择适合您的[存储器](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slstorage){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 类型。
* 选择所需的[网络](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=slnetwork){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 类型。
* 选择[容器化 ](https://{DomainName}/catalog/?taxonomyNavigation=apps&category=containers){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 服务以利用 {{site.data.keyword.cloud_notm}} Kubernetes 技术。
