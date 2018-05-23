---

copyright:
  years: 2015, 2016, 2017, 2018
lastupdated: "2018-05-02"

---

{: new_window: target="_blank"}
{:shortdesc: .shortdesc}

# 向应用程序添加服务
{: #add_service}

如果使用 {{site.data.keyword.Bluemix_notm}} {{site.data.keyword.dev_console}} 创建了应用程序，那么您有机会在应用程序概述页面中添加资源。但是，您也可以在应用程序上下文的外部，直接从 {{site.data.keyword.Bluemix_notm}}“目录”供应资源。
{: shortdesc}

您可以请求一个资源实例，然后独立于应用程序使用该实例，也可以在应用程序概述页面中将资源实例添加到应用程序中。您可以直接在 {{site.data.keyword.Bluemix_notm}}“目录”中供应特定类型的资源（服务）。

##发现服务
{: #discover_services}

通过下列方式，您可以在 {{site.data.keyword.Bluemix_notm}} 中查看所有可用服务：

* 通过 {{site.data.keyword.Bluemix_notm}} 控制台。查看 {{site.data.keyword.Bluemix_notm}}“目录”。
* 通过 bluemix 命令行界面。使用 `bluemix service offerings` 命令。
* 从您自己的应用程序。使用 [GET /v2/services Services API](http://apidocs.cloudfoundry.org/197/services/list_all_services.html){: new_window}。

在开发应用程序时，您可以选择所需的服务。选择服务后，{{site.data.keyword.Bluemix_notm}} 会供应该服务。对于不同类型的服务，供应过程可能会不同。例如，数据库服务会创建数据库，移动应用程序的推送通知服务会生成配置信息。

{{site.data.keyword.Bluemix_notm}} 通过使用服务实例来为您的应用程序提供服务的资源。可以跨 Web 应用程序共享服务实例。

您还可使用在其他区域中托管的服务（如果这些服务在这些区域中可用）。这些服务必须可从因特网访问并且具有 API 端点。必须按照与编码外部应用程序或第三方工具以使用 {{site.data.keyword.Bluemix_notm}} 服务相同的方式来手动编码应用程序以使用这些服务。有关更多信息，请参阅[允许外部应用程序和第三方工具使用 {{site.data.keyword.Bluemix_notm}} 服务](#accser_external)。

## 请求新的服务实例
{: #req_instance}

要请求新的服务实例，必须使用 {{site.data.keyword.Bluemix_notm}} 用户界面或 {{site.data.keyword.Bluemix_notm}} 命令行界面。

**注：**指定服务名称时，请避免使用非字母或数字字符，因为结果可能难以预料。

如果使用 {{site.data.keyword.Bluemix_notm}} 用户界面请求服务实例，请完成以下步骤：

1. 在 {{site.data.keyword.Bluemix_notm}}“目录”中，单击要添加的服务的磁贴。这将打开服务详细信息页面。

2. 在**服务名称**字段中输入名称。系统提供了缺省名称。您可以更改该字段中的名称，也可以保留不变。

3. 填写更多字段或完成更多选择，然后单击**创建**。

如果使用 {{site.data.keyword.Bluemix_notm}} 命令行界面请求服务实例，请完成以下步骤：

1. 使用 `bluemix service offerings` 命令查找所需服务的名称和套餐。

2. 使用以下命令创建服务实例，其中 service_name 是服务的名称；service_plan 是服务的套餐；service_instance 是您希望用于此服务实例的名称。

```
bluemix service create service_name service_plan service_instance
```

3. 使用以下命令将服务实例绑定到应用程序，其中 *appname* 是应用程序的名称；service_instance 是服务实例的名称。

```
bluemix service bind appname service_instance
```

只能将服务实例绑定到位于同一空间或组织中的应用程序实例。不过，也可以按照与外部应用程序相同的方式使用其他空间或组织中的服务实例。不要创建绑定，请改用凭证来直接配置应用程序实例。有关外部应用程序如何使用 {{site.data.keyword.Bluemix_notm}} 服务的更多信息，请参阅[允许外部应用程序使用 {{site.data.keyword.Bluemix_notm}} 服务](#accser_external){: new_window}。

## 配置应用程序
{: #config}

将服务实例绑定到应用程序后，必须将应用程序配置为与服务交互。

每个服务可能需要采用不同的机制与应用程序进行通信。在开发应用程序时，会记录这些机制作为服务定义的一部分以供您参阅。为了实现一致性，您的应用程序需要通过这些机制与服务进行交互。

* 要与数据库服务交互，请使用 {{site.data.keyword.Bluemix_notm}} 提供的信息，例如，用户标识、密码和应用程序的访问 URI。
* 要与移动后端服务交互，请使用 {{site.data.keyword.Bluemix_notm}} 提供的信息，例如，应用程序标识、特定于客户机的安全性信息以及应用程序的访问 URI。移动服务通常彼此配合工作，以便能够在一组服务之间共享上下文信息，例如，应用程序开发者名称和使用应用程序的用户。
* 要与 Web 应用程序或移动应用程序的服务器端云代码交互，请在应用程序的 *VCAP_SERVICES* 环境变量中使用 {{site.data.keyword.Bluemix_notm}} 提供的信息，例如，运行时凭证。*VCAP_SERVICES* 环境变量的值是序列化 JSON 对象。该变量包含与绑定应用程序的服务进行交互所需要的运行时数据。不同服务的数据格式不同。您可能需要阅读服务文档以了解预期的结果以及如何解读每条信息。

如果绑定到应用程序的服务崩溃，那么应用程序可能会停止运行或发生错误。{{site.data.keyword.Bluemix_notm}} 不会自动重新启动应用程序，以便从这些问题中进行恢复。在进行应用程序编码时，应考虑到识别中断、异常和连接失败以及进行恢复的问题。有关更多信息，请参阅[应用程序不会自动重新启动](/docs/troubleshoot/ts_apps.html#ts_apps_not_auto_restarted)故障诊断主题。

## 启用外部应用程序
{: #accser_external}

您可能会有在 {{site.data.keyword.Bluemix_notm}} 外部创建和运行的应用程序，或者，您可能会使用第三方工具。如果 {{site.data.keyword.Bluemix_notm}} 服务提供可从因特网访问的服务密钥，那么您可以通过本地应用程序或第三方工具来使用这些服务。

以下服务提供服务密钥供您在外部使用：

* {{site.data.keyword.amashort_old}} <!--Advanced Mobile Access-->
* {{site.data.keyword.alchemyapishort}} <!--AlchemyAPI-->
* {{site.data.keyword.alertnotificationshort}} <!--Alert Notification-->
* {{site.data.keyword.sparks}} <!--Analytics for Apache Spark-->
* {{site.data.keyword.appseccloudshort}} <!--Application Security on Cloud-->
* {{site.data.keyword.blockchain}} <!--Blockchain-->
* {{site.data.keyword.cloudant}} <!--Cloudant&reg; NoSQL DB-->
* {{site.data.keyword.iotmapinsights_short}} <!--Context Mapping-->
* {{site.data.keyword.conversationshort}} <!--Conversation-->
* {{site.data.keyword.dashdbshort}} <!--dashDB-->
* {{site.data.keyword.discoveryshort}} <!--Discovery-->
* {{site.data.keyword.documentconversionshort}} <!--Document Conversion-->
* {{site.data.keyword.iotdriverinsights_short}} <!--Driver Behavior-->
* {{site.data.keyword.geospatialshort_Geospatial}} <!--Geospatial Analytics-->
* {{site.data.keyword.GlobalizationPipeline_short}} <!--Globalization Pipeline-->
* {{site.data.keyword.appconserviceshort}} <!--IBM&reg; App Connect-->
* {{site.data.keyword.dataworks_short}} <!--IBM&reg; Data Connect-->
* {{site.data.keyword.graphshort}} <!--IBM&reg; Graph-->
* {{site.data.keyword.iotelectronics_full}} <!--IBM&reg; IoT for Electronics-->
* {{site.data.keyword.twittershort}} <!--Insights for Twitter-->
* {{site.data.keyword.iot4auto_short}} <!--IoT for Automotive-->
* {{site.data.keyword.iotinsurance_short}} <!--IoT for Insurance-->
* {{site.data.keyword.languagetranslatorshort}} <!--Language Translator-->
* {{site.data.keyword.dwl_short}} <!--Lift-->
* {{site.data.keyword.messagehub}} <!--Message Hub-->
* {{site.data.keyword.mobileanalytics_short}} <!--Mobile Analytics-->
* {{site.data.keyword.nlclassifiershort}} <!--Natural Language Classifier-->
* {{site.data.keyword.objectstorageshort}} <!--Object Storage-->
* {{site.data.keyword.personalityinsightsshort}} <!--Personality Insights-->
* {{site.data.keyword.HybridConnect_short}} <!--Product Insights-->
* {{site.data.keyword.mobilepush}} <!--Push-->
* {{site.data.keyword.retrieveandrankshort}} <!--Retrieve and Rank-->
* {{site.data.keyword.speechtotextshort}} <!-- Speech to Text-->
* {{site.data.keyword.streaminganalyticsshort}} <!--Streaming Analytics-->
* {{site.data.keyword.texttospeechshort}} <!--Text to Speech-->
* {{site.data.keyword.toneanalyzershort}} <!--Tone Analyzer-->
* {{site.data.keyword.tradeoffanalyticsshort}} <!--Tradeoff Analytics-->
* {{site.data.keyword.weather_short}} <!--Weather Company Data-->
* {{site.data.keyword.workloadscheduler}} <!--Workload Scheduler-->

要允许外部应用程序或第三方工具使用 {{site.data.keyword.Bluemix_notm}} 服务，请完成以下步骤：

1. 请求服务的实例。
    1. 在 {{site.data.keyword.Bluemix_notm}} 用户界面中的“仪表板”上，单击**创建资源**。这将显示“目录”。
    2. 在“目录”中，通过单击相应服务磁贴来选择所需的服务。这将打开服务详细信息页面。
    3. 在“服务”窗口中，将缺省**连接到：**列表选择保留为**保持未绑定**。此选择意味着该服务不会连接到 {{site.data.keyword.Bluemix_notm}} 应用程序。
    4. 根据需要进行任何其他选择。然后，单击**创建**。这将创建服务实例，并显示服务“仪表板”。
2. 在服务仪表板中，可以选择**服务凭证**来查看或添加 JSON 格式的凭证。选择一组凭证，然后单击“操作”列中的**查看凭证**。使用显示的 API 密钥作为凭证来连接到服务实例。

在 {{site.data.keyword.Bluemix_notm}} 外部运行的应用程序现在可以访问 {{site.data.keyword.Bluemix_notm}} 服务。

**注：**如果想要删除服务实例或检查记帐信息，必须返回到用户界面中用于管理服务实例的“仪表板”。

## 创建用户提供的服务实例
{: #user_provide_services}

您可能有一些服务是在 {{site.data.keyword.Bluemix_notm}} 外部管理的。如果您拥有从因特网访问这些外部服务的凭证，那么可以创建用户提供的 {{site.data.keyword.Bluemix_notm}} 服务实例来代表外部服务并与这些服务进行通信。

要创建用户提供的服务实例并将其绑定到应用程序，请完成以下步骤：

1. 使用 `bluemix service user-provided-create` 命令创建用户提供的服务实例：
    * 要创建用户提供的一般服务实例，请使用 **-p** 选项，并用逗号分隔参数名称。随后，`bx` 命令行界面会依次提示您提供每个参数的值。例如：
        ```
        bluemix service user-provided-create testups1 -p "host, port, dbname, username, password"
        host> pubsub01.example.com
        port> 1234
        dbname> sampledb01
        username> pubsubuser
        password> p@$$w0rd
        Creating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * 要创建服务实例来将信息排出至第三方日志管理软件，请使用 `-l` 选项，然后指定第三方日志管理软件提供的目标。例如：

        ```
        bluemix service user-provided-create testups2 -l syslog://example.com
        Creating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

    如果要更新用户提供的服务实例的一个或多个参数，请使用 `bluemix service user-provided-update` 命令。

    * 要更新用户提供的常规服务实例，请使用 **-p** 选项，并在 JSON 对象中指定参数键和值。例如：

        ```
        bluemix service user-provided-update testups1 -p "{\"username\":\"pubsubuser2\",\"password\":\"p@$$w0rd2\"}"
        Updating user provided service testups1 in org my-org / space dev as user@sample.com...
        OK
        ```

    * 要创建服务实例来将信息排出至第三方日志管理软件，请使用 `-l` 选项。例如：

        ```
        bluemix service user-provided-create testups2 -l syslog://example2.com
        Updating user provided service testups2 in org my-org / space dev as user@sample.com...
        OK
        ```

2. 使用 `bluemix service bind` 命令将该服务实例绑定到应用程序。例如：

	```
	bluemix service bind myapp testups1
	Binding service testups1 to app myapp in org my-org / space dev as user@sample.com...
	OK
	```

现在，您可以将应用程序配置为使用外部服务。有关如何将应用程序配置为与服务进行交互的信息，请参阅[将应用程序配置为与服务进行交互](#config){: new_window}。
