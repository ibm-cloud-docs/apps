---

copyright:
  years: 2019
lastupdated: "2019-03-15"

keywords: apps, domain, Kubernetes, Cloud Foundry, cli

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 更新域
{: #update-domain}

域提供了分配给 {{site.data.keyword.cloud}} 中组织的 URL 路径。对于 Cloud Foundry 应用程序，可以通过使用 {{site.data.keyword.cloud_notm}} 控制台或命令行界面将域从 `mybluemix.net` 迁移至 `appdomain.cloud`。
{:shortdesc}

## 从 {{site.data.keyword.cloud_notm}} 控制台更新域
{: #update-domain-console}

缺省共享域为 `mybluemix.net`，但是，`appdomain.cloud` 是另一个可供您使用的域选项。
{: tip}

要使用控制台为 Cloud Foundry 组织更新域，请完成以下步骤：

1. 在 [{{site.data.keyword.cloud_notm}} 控制台 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://{DomainName}){: new_window} 中，单击**菜单**图标 ![“菜单”图标](../icons/icon_hamburger.svg)，然后选择**资源列表**。
2. 在**资源列表**页面，单击 **Cloud Foundry 应用程序**。
3. 单击要为其更改域的应用程序。这将显示应用程序的**概述**页面。
4. 选择**路径**菜单，注意当前域，例如 `<myapp.mybluemix.net>`，然后单击**编辑路径**。
5. 选择域列表，然后单击您想要使用的域，例如 `us-south.cf.appdomain.cloud`。
6. 通过单击**保存**来确认更新。
7. 确认您想要替换的旧域，然后单击**除去**。
8. 要验证新路径是否正常运行，请单击**访问应用程序 URL**。

## 从 {{site.data.keyword.cloud_notm}} 命令行界面更新域
{: #update-domain-cli}

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

2. 输入以下命令，将包含新域的路径添加到应用程序：
   ```
   ibmcloud app route-map APP_NAME DOMAIN -n HOSTNAME
   ```

## 更新 Kubernetes 应用程序的域
{: #update-domain-kube}

{{site.data.keyword.containerlong}} 主机名的子域为 `containers.appdomain.cloud`。缺省情况下，已为集群注册 IBM 提供的 Ingress 子域通配符 `*.<cluster_name>.<region>.containers.appdomain.cloud`。IBM 提供的 TLS 证书是通配符证书，可用于通配符子域。有关更多信息，请参阅[一个名称空间内多个域](/docs/containers?topic=containers-ingress#multi-domains)。
