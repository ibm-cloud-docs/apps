---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-15"

keywords: apps, custom domain, Kubernetes

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 添加并使用定制域
{: #updatingapps}

域提供了分配给 {{site.data.keyword.cloud}} 中组织的 URL 路径。定制域将对应用程序的请求都定向到您拥有的 URL。定制域可以是共享域、共享子域或共享域和主机。除非指定了定制域，否则 {{site.data.keyword.cloud_notm}} 会使用您应用程序路径中的缺省共享域。可以使用 {{site.data.keyword.cloud_notm}} 控制台或命令行界面创建并使用定制域。{:shortdesc}

缺省共享域为 `mybluemix.net`，但是，`appdomain.cloud` 是另一个可供您使用的域选项。有关迁移到 `appdomain.cloud` 的更多信息，请参阅[更新域](/docs/apps/tutorials?topic=creating-apps-update-domain)。
{: tip}

要使用定制域，必须在公共 DNS 服务器上注册定制域，然后在 {{site.data.keyword.cloud_notm}} 中配置定制域。然后，您必须将该定制域映射到公共 DNS 服务器上的 {{site.data.keyword.cloud_notm}} 系统域。定制域映射到系统域后，对定制域的请求会路由到 {{site.data.keyword.cloud_notm}} 中的应用程序。


## 从 {{site.data.keyword.cloud_notm}} 控制台添加定制域
{: #custom-domain-console}

要使用控制台为组织添加定制域，请完成以下步骤：

1. 转至**管理 > 帐户**，然后选择 **Cloud Foundry 组织**。
2. 单击要为其创建定制域的组织的名称。
3. 单击**域**选项卡以查看可用域列表。
4. 单击**添加域**，然后输入域名并选择区域。
5. 确认更新，然后单击**添加**。

## 将包含定制域的路径添加到应用程序

1. 在 [{{site.data.keyword.cloud_notm}} 控制台 ](https://{DomainName}){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 中，单击**菜单**图标 ![“菜单”图标](../../icons/icon_hamburger.svg)，然后选择**资源列表**。
2. 在**资源列表**页面，单击 **Cloud Foundry 应用程序**。
3. 单击要添加路径的应用程序。这将显示应用程序的**概述**页面。
4. 选择**路径**菜单，然后选择**编辑路径**。
5. 单击**添加路径**，然后指定要用于应用程序的路径。
6. 通过单击**保存**来确认更新。

例如，可以使用 `*.mycompany.com` 将路径 `www.mybluemix.net` 与应用程序相关联。还可以使用 `example.mycompany.com` 将路径 `www.example.bluemix.net` 与应用程序相关联。
{: tip}

## 从 {{site.data.keyword.cloud_notm}} 命令行界面添加定制域
{: #custom-domain-cli}

1. 对于 Cloud Foundry 应用程序，通过输入以下命令连接到目标 Cloud Foundry API 端点：
   ```
   ibmcloud target --cf-api <CF_ENDPOINT>
   ```
   
   **Cloud Foundry API 端点：**
   * US-SOUTH - `api.us-south.cf.cloud.ibm.com`
   * US-EAST - `api.us-east.cf.cloud.ibm.com`
   * EU-DE - `api.eu-de.cf.cloud.ibm.com`
   * EU-GB - `api.eu-gb.cf.cloud.ibm.com`
   * AU-SYD - `api.au-syd.cf.cloud.ibm.com`
   
2. 通过输入以下命令，为组织创建定制域：
   ```
   ibmcloud app domain-create <MY_ORGNAME> <MY_DOMAIN>
   ```

3. 将包含定制域的路径添加到应用程序。

   对于 Cloud Foundry 应用程序，请输入以下命令：
   ```
   ibmcloud app route-map <MY_APPNAME> <MY_DOMAIN> -n <MY_HOSTNAME>
   ```
   
## 将定制域映射到系统域
{: #mapcustomdomain}

在 {{site.data.keyword.cloud_notm}} 中配置定制域后，请将该定制域映射到您注册的 DNS 服务器上的 {{site.data.keyword.cloud_notm}} 系统域：

1. 为 DNS 服务器上的定制域名设置“CNAME”记录。用于设置 CNAME 记录的步骤根据 DNS 提供程序而变化。例如，如果使用的是 GoDaddy，请遵循 GoDaddy 中的[域名帮助 ](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 指南。
2. 将定制域名映射到运行应用程序的 {{site.data.keyword.cloud_notm}} 区域的安全端点。要提供分配给 {{site.data.keyword.cloud_notm}} 中组织的 URL 路径，请使用以下区域端点。例如，将 CNAME 指向 `<custom-domain>.us-east.cf.cloud.ibm.com.`

  **Cloud Foundry 端点：**
  * US-SOUTH - `custom-domain.us-south.cf.cloud.ibm.com`
  * US-EAST - `custom-domain.us-east.cf.cloud.ibm.com`
  * EU-DE - `custom-domain.eu-de.cf.cloud.ibm.com`
  * EU-GB - `custom-domain.eu-gb.cf.cloud.ibm.com`
  * AU-SYD - `custom-domain.au-syd.cf.cloud.ibm.com`

## 访问应用程序
{: #access-app}

在浏览器中，输入以下 URL 以访问应用程序，其中 `hostname` 为主机名，`mydomain` 为域名：
```
http://hostname.mydomain
```

## 除去孤立的路径
{: #remove-orphaned-route}

要除去孤立的路径，请运行以下命令：
```
ibmcloud app route-delete <MY_DOMAIN> -n <MY_HOSTNAME> -f
```
{: tip}

在该示例中，`domain` 是域名，`hostname` 是应用程序路径的主机名。有关 `ibmcloud app route-delete` 命令的更多信息，请输入命令 `ibmcloud app route-delete -h`。

## 使用 Kubernetes 应用程序的定制域
{: #kube-custom-domain}

IBM Cloud Kubernetes Service 主机名的子域为 `containers.appdomain.cloud`。缺省情况下，已为集群注册 IBM 提供的 Ingress 子域通配符 `*.<cluster_name>.<region>.containers.mybluemix.net`。IBM 提供的 TLS 证书是通配符证书，可用于通配符子域。如果要使用定制域，您必须将定制域注册为通配符域，例如 `*.custom_domain.net`。要使用 TLS，必须获取通配符证书。有关更多信息，请参阅[一个名称空间内多个域](/docs/containers?topic=containers-ingress#multi-domains)。

请查看[本教程](/docs/tutorials?topic=solution-tutorials-scalable-webapp-kubernetes)，该教程将引导您构建一个 Web 应用程序，并在本地容器中运行它，然后将其部署到使用 IBM Kubernetes Service 创建的 Kubernetes 集群中。此外，你将了解如何绑定定制域、监视环境的运行状况和扩展应用程序。
