---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-15"

keywords: apps, services, add service, application

subcollection: creating-apps

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}
{: codeblock: .codeblock}
{:note: .note}

# 向应用程序添加服务
{: #add-resource}

使用 {{site.data.keyword.cloud}} {{site.data.keyword.dev_console}} 创建应用程序时，可以在“应用程序详细信息”页面中添加服务。但是，您也可以在应用程序上下文的外部，直接从 {{site.data.keyword.cloud_notm}}“目录”供应资源。
{: shortdesc}

您可以请求一个服务实例，然后独立于应用程序使用该实例，也可以在“应用程序详细信息”页面中将该服务实例添加到应用程序中。您可以直接在 {{site.data.keyword.cloud_notm}}“目录”中供应特定类型的服务。

## 发现服务
{: #discover-resources}

通过下列方式，您可以在 {{site.data.keyword.cloud_notm}} 中查看所有可用服务：

* 通过 {{site.data.keyword.cloud_notm}} 控制台。查看 {{site.data.keyword.cloud_notm}}“目录”。
* 通过命令行。使用 `ibmcloud service offerings` 命令。
* 从您自己的应用程序。使用 [GET /v2/services 服务 API ](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")。

在开发应用程序时，您可以选择所需的服务。选择服务后，{{site.data.keyword.cloud_notm}} 会供应该服务。对于不同类型的服务，供应过程可能会不同。例如，数据库服务会创建数据库，移动应用程序的推送通知服务会生成配置信息。

{{site.data.keyword.cloud_notm}} 通过使用服务实例来为您的应用程序提供服务的资源。一个服务实例可在多个 Web 应用程序之间共享。

您还可使用在其他区域中托管的服务（如果这些服务在这些区域中可用）。这些服务必须可从因特网访问并且具有 API 端点。必须按照与编码外部应用程序或第三方工具以使用 {{site.data.keyword.cloud_notm}} 服务相同的方式来手动编码应用程序以使用这些服务。有关更多信息，请参阅[将服务连接到外部应用程序](/docs/resources?topic=resources-externalapp)。

## 请求新的服务实例
{: #request-instance}

要请求新的服务实例，必须使用 {{site.data.keyword.cloud_notm}} 用户界面或 {{site.data.keyword.cloud_notm}} 命令行界面。

在指定服务名称时，请避免使用除字母和数字字符以外的其他字符，因为其结果可能不可预测。
{: note}

如果使用 {{site.data.keyword.cloud_notm}} 用户界面请求服务实例，请完成以下步骤：

1. 在 {{site.data.keyword.cloud_notm}}“目录”中，单击要添加的服务的磁贴。这将打开服务详细信息页面。

2. 在**服务名称**字段中输入名称。系统提供了缺省名称。您可以更改该字段中的名称，也可以保留不变。

3. 填写更多字段或完成更多选择，然后单击**创建**。

如果使用 {{site.data.keyword.cloud_notm}} 命令行界面请求服务实例，请在本地下载应用程序，然后打开命令行，并切换到应用程序目录。

1. 运行以下命令将服务添加到应用程序。您可以从已在帐户上启用的服务中选择现有服务，或添加新服务。

  ```bash
ibmcloud dev edit
```
  {: pre}

2. 按照提示选择资源组，然后创建与数据相关的新服务并将其连接到应用程序（如 Cloudant）。您可能需要选择服务的区域和套餐。
3. 创建服务时，会将若干文件（包括凭证）添加到应用程序目录，以帮助您将服务集成到应用程序中。您可以手动合并任何文件，也可以暂时跳过此步骤。

只能将服务实例绑定到位于同一空间或组织中的应用程序实例。不过，也可以按照与外部应用程序相同的方式使用其他空间或组织中的服务实例。不要创建绑定，请改用凭证来直接配置应用程序实例。有关外部应用程序如何使用 {{site.data.keyword.cloud_notm}} 服务的更多信息，请参阅[允许外部应用程序使用 {{site.data.keyword.cloud_notm}} 服务](/docs/resources?topic=resources-externalapp#externalapp)。

## 配置应用程序
{: #configure-app}

将服务实例绑定到应用程序后，必须将应用程序配置为与服务交互。

每个服务可能需要采用不同的机制与应用程序进行通信。在开发应用程序时，会记录这些机制作为服务定义的一部分以供您参阅。为了实现一致性，您的应用程序需要通过这些机制与服务进行交互。

* 要与数据库服务交互，请使用 {{site.data.keyword.cloud_notm}} 提供的信息，例如，用户标识、密码和应用程序的访问 URI。
* 要与移动后端服务交互，请使用 {{site.data.keyword.cloud_notm}} 提供的信息，例如，应用程序标识、特定于客户机的安全性信息以及应用程序的访问 URI。移动服务通常彼此配合工作，以便能够在一组服务之间共享上下文信息，例如，应用程序开发者的姓名和使用应用程序的用户。
* 要与 Web 应用程序或移动应用程序的服务器端云代码交互，请在应用程序的 *VCAP_SERVICES* 环境变量中使用 {{site.data.keyword.cloud_notm}} 提供的信息，例如，运行时凭证。*VCAP_SERVICES* 环境变量的值是序列化 JSON 对象。该变量包含与绑定应用程序的服务进行交互所需要的运行时数据。不同服务的数据格式不同。您可能需要阅读服务文档以了解预期的结果以及如何解读每条信息。

如果绑定到应用程序的服务崩溃，那么应用程序可能会停止运行或发生错误。{{site.data.keyword.cloud_notm}} 不会自动重新启动应用程序，以便从这些问题中进行恢复。在进行应用程序编码时，应考虑到识别中断、异常和连接失败以及进行恢复的问题。有关更多信息，请参阅[应用程序不会自动重新启动](/docs/apps/troubleshoot?topic=creating-apps-managingapps#ts_apps_not_auto_restarted)。

## 访问 {{site.data.keyword.cloud_notm}} 部署环境中的服务
{: #migrate_instance}

{{site.data.keyword.cloud_notm}} 提供了许多部署选项，您可以从一个环境访问在不同的环境中运行的服务。例如，如果您具有在 Cloud Foundry 中运行的服务，那么可以从在 Kubernetes 集群中运行的应用程序访问该服务。

### 示例：从 Kubernetes pod 访问 Cloud Foundry 服务

要从 Kubernetes 集群中的 pod 访问 Cloud Foundry 服务，必须将服务绑定到集群以在 Kubernetes 私钥中存储服务凭证。然后，您可以将此信息提供给应用程序。
{: shortdesc}

缺省情况下，存储在 Kubernetes 私钥中的服务凭证采用 Base64 编码并使用 etcd 加密。 

**重要信息**：请勿直接在部署 YAML 文件中引用或公开服务凭证。部署 YAML 文件并非设计为保存敏感数据，并且缺省情况下不会加密服务凭证。要正确地存储和访问此信息，必须使用 Kubernetes 私钥。 

1. [将服务绑定到集群](/docs/containers?topic=containers-integrations#adding_cluster)。 
2. 要从应用程序 pod 访问服务凭证，请在以下选项中进行选择。 
   - 将私钥作为卷安装到 pod
   - 在环境变量中引用私钥

## 创建用户提供的服务实例
{: #user_provide_services}

您可能有一些服务是在 {{site.data.keyword.cloud_notm}} 外部管理的。如果您拥有从因特网访问这些外部服务的凭证，那么可以创建用户提供的 {{site.data.keyword.cloud_notm}} 服务实例来代表外部服务并与这些服务进行通信。

要创建用户提供的服务实例并将其绑定到应用程序，请完成以下步骤：

1. 使用 `ibmcloud service user-provided-create` 命令创建用户提供的服务实例：
    * 要创建用户提供的一般服务实例，请使用 **-p** 选项，并用逗号分隔参数名称。随后，`ibmcloud` 命令行界面会依次提示您提供每个参数的值。例如：
```
        ibmcloud service user-provided-create testups1 -p "host, port, dbname, username, password"
        host> pubsub01.example.com
        port> 1234
        dbname> sampledb01
        username> pubsubuser
        password> p@$$w0rd
        Creating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * 要创建服务实例来将信息排出至第三方日志管理软件，请使用 `-l` 选项。指定第三方日志管理软件提供的目标。例如：

        ```
        ibmcloud service user-provided-create testups2 -l syslog://example.com
        Creating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

    如果要更新用户提供的服务实例的一个或多个参数，请使用 `ibmcloud service user-provided-update` 命令。

    * 要更新用户提供的常规服务实例，请使用 **-p** 选项，并在 JSON 对象中指定参数键和值。例如：

        ```
ibmcloud service user-provided-update testups1 -p "{\"username\":\"pubsubuser2\",\"password\":\"p@$$w0rd2\"}"
        Updating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * 要创建服务实例来将信息排出至第三方日志管理软件，请使用 `-l` 选项。例如：

        ```
ibmcloud service user-provided-create testups2 -l syslog://example2.com
        Updating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

2. 使用 `ibmcloud service bind` 命令将该服务实例绑定到应用程序。例如：

	```
	ibmcloud service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

现在，您可以将应用程序配置为使用外部服务。有关如何将应用程序配置为与服务进行交互的信息，请参阅[将应用程序配置为与服务进行交互](/docs/apps?topic=creating-apps-add-resource#configure-app)。
