---

copyright:
  years: 2019
lastupdated: "2019-06-03"

keywords: apps, custom, domain, kubernetes, cloud foundry, add, subdomain, custom domain, dns, domainname, domain name, endpoint, update, migrate

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 管理域
{: #update-domain}

域提供了分配给 {{site.data.keyword.cloud}} 中组织的 URL 路径。定制域将对应用程序的请求都定向到您拥有的 URL。定制域可以是共享域、共享子域或共享域和主机。除非指定了定制域，否则 {{site.data.keyword.cloud_notm}} 会使用您应用程序路径中的缺省共享域。管理域的过程取决于部署目标，例如 {{site.data.keyword.containershort}} 和 Cloud Foundry 等。
{:shortdesc}

要使用定制域，必须在公共 DNS 服务器上注册定制域，然后在 {{site.data.keyword.cloud_notm}} 中配置定制域。然后，您必须将该定制域映射到公共 DNS 服务器上的 {{site.data.keyword.cloud_notm}} 系统域。定制域映射到系统域后，对定制域的请求会路由到 {{site.data.keyword.cloud_notm}} 中的应用程序。


## 更改 Kubernetes 应用程序的域
{: #update-domain-kube}

{{site.data.keyword.containershort_notm}} 主机名的子域为 `containers.appdomain.cloud`。缺省情况下，已为集群注册 IBM 提供的 Ingress 子域通配符 `*.<cluster_name>.<region>.containers.appdomain.cloud`。IBM 提供的 TLS 证书是通配符证书，可用于通配符子域。有关更多信息，请参阅[一个名称空间内多个域](/docs/containers?topic=containers-ingress#multi-domains)。

## 使用 Kubernetes 应用程序的定制域
{: #custom-domain-kube}

如果要使用定制域，您必须将定制域注册为通配符域，例如 `*.custom_domain.net`。要使用 TLS，必须获取通配符证书。有关更多信息，请参阅[一个名称空间内多个域](/docs/containers?topic=containers-ingress#multi-domains)。

请查看[本教程](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes)，该教程将引导您搭建一个 Web 应用程序的脚手架，并在容器中本地运行该应用程序，然后将其部署到使用 IBM Kubernetes Service 创建的 Kubernetes 集群中。此外，该教程说明了如何绑定定制域、监视环境的运行状况以及缩放应用程序。

## 更改 Cloud Foundry 应用程序的域
{: #update-domain-cf}

对于 Cloud Foundry 应用程序，可以通过使用 {{site.data.keyword.cloud_notm}} 控制台或命令行界面将域从 `mybluemix.net` 更改为 `appdomain.cloud`。
有关将域更改为 `appdomain.cloud` 的更多信息，请参阅[更新域](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain)。


缺省共享域为 `mybluemix.net`，但是，`appdomain.cloud` 是另一个可供您使用的域选项。
{: tip}

## 使用 Cloud Foundry 应用程序的定制域
{: #custom-domain-cf}

对于 Cloud Foundry 应用程序，可以使用 {{site.data.keyword.cloud_notm}} 控制台或命令行界面创建并使用定制域。有关更多信息，请参阅[添加和使用定制域](/docs/cloud-foundry-public?topic=cloud-foundry-public-custom-domains)。
