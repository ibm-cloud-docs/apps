---

copyright:
  years: 2016, 2017, 2018
lastupdated: "2018-11-29"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

# {{site.data.keyword.cloud_notm}} 开发者控制台说明
{: #intro}

<!--I can't see how a customer needs to be walked through the experience without performing a specific task.-->


{{site.data.keyword.cloud}} Developer Experience 支持云本机应用程序开发者通过各种入门模板工具包创建应用程序，创建并连接关键的 {{site.data.keyword.Bluemix_notm}} 优化服务，然后快速下载可正常运作的代码，或设置进行持续交付。Developer Experience 在 {{site.data.keyword.Bluemix_notm}} 中提供了一组开发者控制台，在其中您可以创建、查看、配置和管理您的应用程序，也可以将其部署到 DevOps 管道或者下载应用程序进行本地开发。

通过借助 {{site.data.keyword.cloud_notm}} 开发者控制台创建应用程序，应用程序所需的所有部件都会保留在 {{site.data.keyword.cloud_notm}} 服务器上您的帐户下。这样您就可以选择在开发者控制台 GUI 和 [{{site.data.keyword.dev_cli_notm}}](/docs/cli/idt/index.html)之间来回切换。

通过 {{site.data.keyword.cloud_notm}} 开发者控制台，可以无缝地为所选用例构建生产就绪型入门模板应用程序。现在来了解一下您在过程中可以执行的步骤。

<!-- Ready to jump in?  Visit the [{{site.data.keyword.cloud_notm}} Web App developer console](https://{DomainName}/developer/appservice) to get started.
{: tip} -->

##概述屏幕
{: #overview_screen}

“概述”屏幕提供了针对您工作所在开发者控制台的主题或通道焦点所定制的内容。在“概述”屏幕中，您可以查看文档，访问学习资源，浏览服务，查看特色入门模板工具包，或链接到入门模板工具包的更大集合。单击导航中的`入门模板工具包`以进入“入门模板工具包”视图。

![开发者控制台“概述”屏幕](images/overview_screen.png "概述屏幕") <br> *开发者控制台“概述”屏幕*

##入门模板工具包视图
{: #starter_kits_view}

“入门模板工具包”视图显示特定于某个用例区域的入门模板工具包的集合。可以单击入门模板工具包卡上的各个链接以查看演示以及更多信息。选择要移动到“新建应用程序”视图中的入门模板工具包。

在某些情况下，选择入门模板工具包将显示有关该入门模板工具包的更多详细信息。如果是这种情况，只需单击`创建`按钮即可移至“新建应用程序”视图。{: tip}

![开发者控制台“入门模板工具包”视图](images/starter_kits_view.png "入门模板工具包视图") <br> *开发者控制台“入门模板工具包”视图*

##新建应用程序视图
{: #create_new_project_view}

在“新建应用程序”视图中，您可以命名应用程序，提供部署和路由信息，并选择语言。请注意，当您创建应用程序以及每个应用程序的定价套餐和条款时，在右侧您还可以看到将自动供应的服务。单击`创建`以移至“应用程序详细信息”视图。如果您还未登录到 {{site.data.keyword.cloud_notm}}，此时需要先进行登录。

![开发者控制台“新建应用程序”视图](images/create_new_project_view.png "新建应用程序视图") <br> *开发者控制台“新建应用程序”视图*

## 应用程序详细信息视图
{: #project_details_view}

“应用程序详细信息”视图会显示为应用程序配置的服务列表。针对列表中的每项，都会显示其服务名称、有关其他信息的链接以及*操作*按钮（带有垂直对齐的三个点）。*操作*按钮选项包含以下几项：从应用程序除去服务、为应用程序打开仪表板以及删除服务。请注意，除去服务实例仅会除去与此应用程序的关联，并不会删除该服务实例。另请注意，服务凭证合并在此视图上，因此无需访问每个单独的服务实例视图来获取这些凭证。

![开发者控制台“应用程序详细信息”视图](images/project_details_view.png "“应用程序详细信息”视图") <br> *开发者控制台“应用程序详细信息”视图*

“应用程序详细信息”视图还支持将新服务或者现有服务添加到不属于原始入门模板工具包的应用程序中。单击服务列表框中的`添加资源`链接以执行此操作。可用的服务取决于应用程序类型以及在某个区域中可用的服务，所以不是所有服务都可供与所有应用程序相关联。

![开发者控制台“添加资源”对话框](images/add_resource_dialog.png "“添加资源”对话框") <br> *开发者控制台“添加资源”对话框*

在“应用程序详细信息”视图中，您可通过以下两种方式来访问代码：

*  [建议] 单击`部署到云`按钮以将代码推送到存储库，并将应用程序部署到 {{site.data.keyword.cloud_notm}}。有关 {{site.data.keyword.cloud_notm}} DevOps 工具链的更多信息，请单击[此处](/docs/services/ContinuousDelivery/toolchains_about.html#toolchains_about)。
*  要快速查看应用程序代码，请选择`下载代码`以生成并下载应用程序代码。

##应用程序列表视图
{: #project_list_view}

您可以在“应用程序列表”视图中查看已创建的所有应用程序的列表。在此处您可以重命名或删除应用程序。单击应用程序名称行可返回到“应用程序详细信息”视图。

![开发者控制台“应用程序列表”视图](images/project_list_view.png "“应用程序列表”视图") <br> *开发者控制台“应用程序列表”视图*
