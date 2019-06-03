---

copyright:

  years: 2019

lastupdated: "2019-05-22"

keywords: apps FAQs, apps frequently asked questions, applications FAQs, applications frequently asked questions

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:faq: data-hd-content-type='faq'}


# 常见问题
{: #apps-faq}

## mybluemix.net 发生了什么？
{: #domain-change-faq}
{: faq}

在 cloud.ibm.com 上提供了新的主机名选项 `*.appdomain.cloud`。

先前，`mybluemix.net` 域用于在多个部署目标（例如，{{site.data.keyword.containerlong_notm}} 或 Cloud Foundry）中托管应用程序。在 `mybluemix.net` 上托管的任何应用程序不会受影响。

Cloud Foundry 应用程序的子域为 `cf.appdomain.cloud`。部署到 {{site.data.keyword.containerlong_notm}} 的应用程序的子域为 `containers.appdomain.cloud`。

有关更多信息，请参阅[管理域](/docs/apps?topic=creating-apps-update-domain)。

## 在哪里可以找到我的应用程序的列表？
{: #cf-app}
{: faq}

[{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 中的资源列表提供了所创建应用程序的摘要信息。在资源列表中，**应用程序**部分包含已创建但*未*部署到 Cloud Foundry 的所有应用程序。**Cloud Foundry 应用程序**部分包含已创建并部署到 Cloud Foundry 的所有应用程序。

## 为什么无法在尝试部署应用程序时选择 Cloud Foundry 空间？
{: #cf-space}
{: faq}

很可能是需要先创建 Cloud Foundry 空间。如果使用的是 Cloud Foundry 命令行界面，请输入 `cf create-space <space_name> -o <organization_name>`。否则，请从控制台完成以下步骤：

1. 从 [{{site.data.keyword.cloud_notm}} 控制台](https://{DomainName}){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")中的菜单栏，选择**管理** > **帐户**。
2. 选择 **Cloud Foundry 组织**。
3. 单击要在其中创建空间的组织的名称，然后单击**添加空间**。

## 如何删除应用程序？
{: #delete-apps}
{: faq}

要删除已创建的应用程序，请完成以下步骤：

1. 在 [{{site.data.keyword.cloud_notm}} 控制台 ](https://{DomainName}){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 中，单击**菜单**图标 ![“菜单”图标](../icons/icon_hamburger.svg)，然后选择**资源列表**。
2. 针对要删除的应用程序，单击**操作**图标 ![“操作”图标](../icons/action-menu-icon.svg)，然后单击**删除**。

## 如何在我的帐户中停止 Cloud Foundry 应用程序？
{: #app-stop}
{: faq}

如果要停止 Cloud Foundry 应用程序，请完成以下步骤：


1. 在“仪表板”中，单击“资源摘要”部分中的**查看资源**。
1. 在“资源”列表中，展开这些部分并找到要停止的服务实例。
1. 选择**操作** ![“操作列表”图标](../icons/action-menu-icon.svg) 菜单，然后单击**停止**。

## 哪些是工具链以及工具链是如何与我的应用程序关联的？
{: #toolchains}
{: faq}

工具链是一组工具集成，用于支持开发、部署和操作任务。可以通过应用程序来创建工具链。工具链可以支持持续开发、部署、监视等操作，并且与应用程序相关联。每个应用程序可以与一个工具链相关联。可以配置工具链，以便对工具链进行的更改可自动构建和部署应用程序。有关工具链的更多信息，请参阅[创建工具链](/docs/services/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started)。

## 如何更改我的 Cloud Foundry 应用程序的域？
{: #cf-domains-faq}
{: faq}

对于 Cloud Foundry 应用程序，可以通过使用 {{site.data.keyword.cloud_notm}} 控制台或命令行界面将域从 `mybluemix.net` 更改为 `appdomain.cloud`。
有关将域更改为 `appdomain.cloud` 的更多信息，请参阅[更新域](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain)。


创建新的应用程序时，缺省共享域为 `mybluemix.net`，但是，`appdomain.cloud` 是另一个可供您使用的域选项。

