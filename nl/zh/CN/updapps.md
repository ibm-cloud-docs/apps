---

copyright:
  years: 2015, 2018
lastupdated: "2018-07-02"

---

{:shortdesc: .shortdesc}
{:tip: .tip}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:screen: .screen}

# 创建并使用定制域
{: #updatingapps}

您可以使用命令行或 {{site.data.keyword.Bluemix}} Continuous Delivery 来更新 {{site.data.keyword.Bluemix_notm}} 中的应用程序。在许多情况下，即便对于 buildpack（例如 Node.js），也必须提供 -c 参数来指定用于启动应用程序的命令。
{:shortdesc}

域提供了分配给 {{site.data.keyword.Bluemix_notm}} 中组织的 URL 路径。要使用定制域，必须在公共 DNS 服务器上注册定制域，在 {{site.data.keyword.Bluemix_notm}} 中配置定制域。然后，将该定制域映射到公共 DNS 服务器上的 {{site.data.keyword.Bluemix_notm}} 系统域。定制域映射到系统域后，对定制域的请求会路由到 {{site.data.keyword.Bluemix_notm}} 中的应用程序。

可以使用 {{site.data.keyword.Bluemix_notm}} 控制台或命令行界面创建并使用定制域。

## 使用 {{site.data.keyword.Bluemix_notm}} 控制台

要使用控制台为组织创建定制域，请完成以下步骤：

1. 转至**管理** > **帐户** > **Cloud Foundry 组织**。
2. 单击要为其创建定制域的组织的名称。
3. 单击**域**选项卡。
4. 单击**添加域**，然后输入域名并选择区域。
5. 确认更新。单击**添加**。

例如，可以使用 `*.mycompany.com` 将路径 `www.mybluemix.com` 与应用程序相关联。还可以使用 `example.mycompany.com` 将路径 `www.example.mybluemix.com` 与应用程序相关联。
{: tip}

将包含定制域的路径添加到应用程序。

1. 单击**菜单**图标 ![“菜单”图标](../icons/icon_hamburger.svg) > **仪表板**，然后单击要将路径添加到的应用程序所在行。这将显示“**概述**”页面。
2. 在**路径**菜单中，选择**编辑路径**。
3. 单击**添加路径**，然后指定要用于应用程序的路径。
4. 通过单击**保存**来确认更新。

## 使用 {{site.data.keyword.Bluemix_notm}} 命令行界面

1. 通过输入以下命令，为组织创建定制域：

   ```
   ibmcloud app domain-create <your org name> mydomain
   ```

2. 将包含定制域的路径添加到应用程序。对于 CF 应用程序，请输入以下命令：

   ```
   ibmcloud app route-map myapp mydomain -n host_name

   ```

       对于容器组，请输入以下命令：


   ```
     cf ic route map -n host_name -d mydomain mycontainergroup
     ```

在 {{site.data.keyword.Bluemix_notm}} 中配置定制域后，请将该定制域映射到您注册的 DNS 服务器上的 {{site.data.keyword.Bluemix_notm}} 系统域：

1. 为 DNS 服务器上的定制域名设置“CNAME”记录。用于设置 CNAME 记录的步骤根据 DNS 提供程序而变化。例如，如果使用的是 GoDaddy，请遵循 GoDaddy 中的[域名帮助 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://www.godaddy.com/help/add-a-cname-record-19236){: new_window} 指南。
2. 将定制域名映射到运行应用程序的 {{site.data.keyword.Bluemix_notm}} 区域的安全端点。要提供分配给 {{site.data.keyword.Bluemix_notm}} 中组织的 URL 路径，请使用以下区域端点。

  * US-SOUTH - `secure.us-south.bluemix.net`
  * US-EAST - `secure.us-east.bluemix.net`
  * EU-DE - `secure.eu-de.bluemix.net`
  * EU-GB - `secure.eu-gb.bluemix.net`
  * AU-SYD - `secure.au-syd.bluemix.net`

在浏览器或命令行界面中，输入以下 URL 来访问 `myapp` 应用程序：

```
http://host_name.mydomain
```

要除去孤立的路径，请运行以下命令：

```
ibmcloud app route-delete domain -n hostname -f

```
{: tip}

在该示例中，`domain` 是域名，`hostname` 是应用程序路径的主机名。有关 `ibmcloud app route-delete` 命令的更多信息，请输入命令 `ibmcloud app route-delete -h`。
