---

copyright:
  years: 2015, 2019
lastupdated: "2019-02-01"

---

{:tsSymptoms: .tsSymptoms}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:tip: .tip}
{:new_window: target="_blank"}
{:troubleshoot: data-hd-content-type='troubleshoot'}

# 有关创建应用程序的故障诊断
{: #managingapps}

有关创建应用程序的一般问题可能包括：无法更新应用程序或未显示双字节字符。在许多情况下，只需执行几个简单的步骤即可解决这些问题。
{:shortdesc}

## 您有未保存的更改
{: #ts_unsaved_changes}
{: troubleshoot}

在应用程序详细信息页面上单击项时，可能无法执行任何操作。系统还可能会提示您保存更改后才能继续。

在应用程序详细信息页面上尝试检查应用程序或服务时，显示了以下错误消息：
{: tsSymptoms}

`您有未保存的更改。确定要离开此页面吗？`

在运行时窗格中的**实例**或**内存配额**字段上滚动鼠标时，值会更改。这是故意设计的行为。但是，当您要转至其他页面时，系统会提示您保存内存或实例设置。
{: tsCauses}

关闭消息对话框，然后单击运行时窗格中的**重置**。
{: tsResolve}

## {{site.data.keyword.cloud_notm}} 区域之间的自动故障转移不可用
{: #ts_failover}
{: troubleshoot}

无法使用 {{site.data.keyword.cloud}} 区域之间的自动故障转移。但是，可以使用支持在多个 IP 地址之间故障转移的 DNS 提供程序来作为变通方法。

当某个 {{site.data.keyword.cloud_notm}} 区域变为不可用时，在该区域中运行的应用程序也不可用，即使在另一个 {{site.data.keyword.cloud_notm}} 区域中有相同的应用程序正在运行，也是如此。
{: tsSymptoms}

{{site.data.keyword.cloud_notm}} 尚不提供从一个区域到另一个区域的自动故障转移。
{: tsCauses}

您可以使用支持在多个 IP 地址间进行智能故障转移的 DNS 提供程序，然后手动配置 DNS 设置以启用 {{site.data.keyword.cloud_notm}} 区域间的自动故障转移。具有此功能的 DNS 提供程序包括 NSONE、Akamai 和 Dyn。
{: tsResolve}

配置 DNS 设置时，必须指定应用程序运行所在 {{site.data.keyword.cloud_notm}} 区域的公共 IP 地址。要获取 {{site.data.keyword.cloud_notm}} 区域的公共 IP 地址，请使用 `nslookup` 命令。例如，可以在命令行窗口中键入以下命令。
```
nslookup cloud.ibm.com
```
{: codeblock}


## 无法复用已删除应用程序的名称
{: #ts_reuse_appname}
{: troubleshoot}

删除应用程序之后，您仅可以在删除应用程序路径之后复用应用程序名称。

尝试复用应用程序名称时，您会收到以下消息：
{: tsSymptoms}

`名称已经由其他应用程序使用。`

删除应用程序时，不会自动删除其作为应用程序 URL 的路径，并且此路径不可复用。您必须转至创建应用程序的空间，删除路径，以便可以对其进行复用。
{: tsCauses}

完成以下步骤以删除未用的路径：
{: tsResolve}

  1. 通过输入以下命令，检查路径是否属于当前空间：
     ```
    ibmcloud cf routes
    ```
    {: codeblock}

  2. 如果路径不属于当前空间，请通过输入以下命令，切换到其所属的空间或组织：
     ```
    ibmcloud cf target -o org_name -s space_name
    ```
    {: codeblock}

  3. 通过输入以下命令，删除应用程序路径：
     ```
    ibmcloud cf delete-route domain_name -n host_name
    ```
    {: codeblock}

  例如：
  ```
  ibmcloud cf delete-route cf.cloud.ibm.com -n app001
  ```
  {: codeblock}

## 无法在组织中检索空间
{: #ts_retrieve_space}
{: troubleshoot}

如果当前组织没有与其相关联的空间，那么无法创建应用程序或服务。

尝试在 {{site.data.keyword.cloud_notm}} 中创建应用程序时，您会看到以下错误消息：
{: tsSymptoms}

`BXNUI0515E: 未检索到组织中的空间。发生了网络连接问题，或者当前组织没有与其相关联的空间。`

在尚未创建空间的情况下，第一次尝试通过目录创建应用程序或服务时，通常会发生此错误。
{: tsCauses}

请确保在当前组织中已创建空间。要创建空间，请使用以下某种方法： 
{: tsResolve}

* 在菜单栏中，单击**管理 > 帐户**，然后选择 **Cloud Foundry 组织**。选择要在其中创建空间的组织，然后单击**创建空间**。
* 在 Cloud Foundry 命令行界面中，输入 `cf create-space <space_name> -o <organization_name>`.

请重试。如果再次出现此消息，请转至 [{{site.data.keyword.cloud_notm}} 状态 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://ibm.biz/bluemixstatus){: new_window} 页面，检查服务或组件是否存在问题。

## 无法执行请求的操作
{: #ts_authority}
{: troubleshoot}

如果没有相应的访问权限，那么无法完成操作。

尝试对服务实例或应用程序实例执行操作时，无法完成请求的操作，并看到以下其中一条错误消息：
{: tsSymptoms}

`BXNUI0514E: 您不是 <orgName> 组织中任何空间的开发者。`

`服务器错误，状态码：403，错误代码：10003，消息：您无权执行请求的操作。`

您没有执行操作所需的相应级别的权限。
{: tsCauses}

要获取相应级别的权限，请使用以下其中一种方法。
{: tsResolve}

* 选择您具有其开发者角色的另一个组织和空间。
* 请求组织管理者将您的角色更改为开发者，或者创建空间，然后为您分配开发者角色。有关详细信息，请参阅[管理组织和空间](/docs/admin/orgs_spaces.html#orgsspacesusers)。

## 由于授权错误而无法访问 {{site.data.keyword.cloud_notm}} 服务
{: #ts_vcap}
{: troubleshoot}

应用程序访问 {{site.data.keyword.cloud_notm}} 服务时，如果服务凭证是硬编码到应用程序中的，那么可能会发生授权错误。

将应用程序配置为与 {{site.data.keyword.cloud_notm}} 服务通信后，将应用程序部署到 {{site.data.keyword.cloud_notm}}。但是，无法使用应用程序来访问 {{site.data.keyword.cloud_notm}} 服务，并且会收到授权错误。
{: tsSymptoms}

硬编码到应用程序中的凭证可能不正确。每次重新创建服务时，用于访问该服务的凭证都会改变。
{: tsCauses}

不要将凭证硬编码到应用程序中，请改用 VCAP_SERVICES 环境变量中的连接参数。具体如何使用 VCAP_SERVICES 环境变量中的连接参数取决于程序语言。例如，对于 Node.js 应用程序，可以使用以下命令：
{: tsResolve}

```
process.env.VCAP_SERVICES
```

有关其他程序语言中可以使用的命令的更多信息，请参阅 [Java ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} 和 [Ruby ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window}。


## 收到 502 无效网关错误
{: #ts_502_error}
{: troubleshoot}

如果在与 {{site.data.keyword.cloud_notm}} 上的应用程序进行交互时收到 `502 无效网关`错误，请检查 {{site.data.keyword.cloud_notm}} 状态页面，然后采取相应的措施。

您收到以“502 无效网关”开头的错误消息。例如，您可能会看到 `502 无效网关：注册的端点未能处理请求。`
{: tsSymptoms}

通常会在以下情况下发生“无效网关”错误：您转至某个 Web 站点，该站点使用代理服务器来存储和中继来自托管该站点的主服务器中的数据。主服务器和代理服务器之间可能未正确连接。因此，您会在浏览器窗口中看到 HTTP 状态码 502。此状态码指示该站点的主服务器未收到本该从代理服务器发来的 HTTP 实现。
{: tsCauses}

其他导致“无效网关”错误的不太常见的原因包括：因特网服务提供商 (ISP) 信息遗失、防火墙配置错误以及浏览器高速缓存错误。

如果您怀疑 {{site.data.keyword.cloud_notm}} 服务已关闭，请先检查 [{{site.data.keyword.cloud_notm}} 状态 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://ibm.biz/bluemixstatus){: new_window} 页面。变通方法可能是[在其他 {{site.data.keyword.cloud_notm}} 区域中使用该服务](/docs/resources/connect_external_app#externalapp){: new_window}。如果服务状态正常，请尝试执行以下步骤来解决问题： 
{: tsResolve}

  * 重试操作：
    * 通过按键盘上的 F5 或单击**刷新**，重新装入页面。如果此步骤无效，请清除浏览器的高速缓存和 cookie，然后再重新装入。

    * 使用其他浏览器。
    * 重新启动您的路由器、调制解调器和计算机。重新引导这些设备可以清理导致 502 错误的各种错误。

  * 稍等，然后重试。您的因特网服务提供商或 {{site.data.keyword.cloud_notm}} 服务可能发生了临时问题。您可以一直等到临时问题得到解决为止。

  * 如果问题持续存在，请联系 {{site.data.keyword.cloud_notm}} 支持。有关更多信息，请参阅[联系 {{site.data.keyword.cloud_notm}} 支持 ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](/docs/support/index.html#contacting-bluemix-support){: new_window}。

## 超出磁盘配额
{: #ts_disk_quota}
{: troubleshoot}

如果磁盘空间不足，可以手动修改磁盘配额来获取更多的磁盘空间。

磁盘空间不足时，可能会看到一条消息，指示超过磁盘配额。为了解决该问题，您可能尝试了通过扩展应用程序实例来获取更多的磁盘空间。例如，您可能更改了应用程序详细信息页面上的内存配额，将大小从 256 MB 扩展到 1256 MB。但是，由于磁盘配额依然未变，所以您并没有获得更多的磁盘空间。
{: tsSymptoms}

为应用程序分配的缺省磁盘配额为 1 GB。如果您需要更多的磁盘空间，必须手动指定磁盘配额。 
{: tsCauses}

使用以下某个方法可指定磁盘配额。可指定的最大磁盘配额为 2 GB。如果 2 GB 仍不够，请尝试外部服务，例如[对象存储](/docs/services/ObjectStorage/index.html)。
{: tsResolve}

  * 在 manifest.yml 文件中，添加以下项：
    
  ```yaml
	disk_quota: <disk_quota>
	```
  * 在用于将应用程序推送到 {{site.data.keyword.cloud_notm}} 的 `ibmcloud cf push` 命令中使用 **-k** 选项：
    ```
	ibmcloud cf push appname -p app_path -k <disk_quota>
	```
  {: codeblock}

## Android 应用程序收不到 {{site.data.keyword.mobilepushshort}}
{: #ts_push}
{: troubleshoot}

在无法访问 Google 的某些地区，Android 应用程序收不到您通过 IBM {{site.data.keyword.mobilepushshort}} 服务发送出来的通知。在这种情况下，变通方法是使用第三方服务。

为 {{site.data.keyword.cloud_notm}} 应用程序绑定 {{site.data.keyword.mobilepushshort}} 服务，并将消息发送给已注册的设备。但是，在某些区域，Android 上开发的应用程序收不到您的通知。
{: tsSymptoms}

IBM {{site.data.keyword.mobilepushshort}} 服务使用 Google 云消息传递 (GCM) 服务将通知分派到在 Android 上开发的移动应用程序。要使 Android 应用程序能够接收通知，移动应用程序必须可以访问 Google 云消息传递 (GCM) 服务。在 Android 应用程序无法访问 GCM 服务的区域中，Android 应用程序收不到 {{site.data.keyword.mobilepushshort}}。
{: tsCauses}

作为变通方法，请使用不依赖于 GCM 服务的第三方服务，例如 [Pushy ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://pushy.me){: new_window}、[getui ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://www.getui.com/){: new_window} 和 [jpush ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://www.jpush.cn/){: new_window}。
{: tsResolve}

## 超过组织的服务限制
{: #ts_servicelimit}
{: troubleshoot}

如果您是轻量帐户用户，那么可能无法在超过组织服务限制的情况下在 {{site.data.keyword.cloud_notm}} 中创建应用程序。

尝试在 {{site.data.keyword.cloud_notm}} 中创建应用程序时，显示了以下错误消息：
{: tsSymptoms}

`BXNUI2032E: 未创建 <service_instances> 资源。联系 Cloud Foundry 来创建资源时，发生了错误。Cloud Foundry 消息：“已超过组织的服务限制。”`

在已超过您帐户可拥有的服务实例数的限制时，会发生此错误。
{: tsCauses}

删除不需要的任何服务实例，或者除去您可拥有的服务实例数的限制。
{: tsResolve}

  * 要删除服务实例，可以使用 {{site.data.keyword.cloud_notm}} 控制台或命令行界面。

    要使用 {{site.data.keyword.cloud_notm}} 控制台来删除服务实例，请完成以下步骤：
	  1. 在资源列表中，单击要删除的服务的**操作**菜单。
	  2. 单击**删除服务**。系统会提示您重新编译打包服务实例所绑定到的应用程序。

    要使用命令行界面删除服务实例，请完成以下步骤：
	  3. 取消服务实例与应用程序的绑定。输入 `cf unbind-service <appname> <service_instance_name>`.
	  4. 删除该服务实例。输入 `cf delete-service <service_instance_name>`.
	  5. 删除服务实例后，可能需要重新编译打包该服务实例所绑定到的应用程序。输入 `cf restage <appname>`.

  * 要除去您可拥有的服务实例数的限制，请将轻量帐户升级到计费帐户。有关更多信息，请参阅[升级帐户](/docs/account/index.html#upgrade-to-paygo)。

## 无法在 {{site.data.keyword.cloud_notm}} 上运行可执行文件
{: #ts_executable}
{: troubleshoot}

如果可执行文件是在不同环境中开发和构建的，那么可能无法在 {{site.data.keyword.cloud_notm}} 上运行这些可执行文件。

如果可执行文件是在不同环境中开发和构建的，那么无法在 {{site.data.keyword.cloud_notm}} 上运行这些可执行文件。
{: tsSymptoms}

如果要推送到 {{site.data.keyword.cloud_notm}} 的内容已经是可执行文件，那么该内容是先前构建的，不需要在 {{site.data.keyword.cloud_notm}} 上进行构建。在此情况下，无需任何 buildpack，可执行文件就可以在 {{site.data.keyword.cloud_notm}} 上运行。您必须向 {{site.data.keyword.cloud_notm}} 明确指示不需要 buildpack。
{: tsCauses}

在将可执行文件推送到 {{site.data.keyword.cloud_notm}} 时，必须指定 `null-buildpack`，它指示不需要 buildpack。指定 `null-buildpack` 的方法是使用带 **-b** 选项的 `ibmcloud cf push` 命令：
{: tsResolve}

```
ibmcloud cf push appname -p app_path -c <start_command> -b <null-buildpack>
```
{: codeblock}

例如：
```
ibmcloud cf push appname -p app_path -c ./RunMeNow -b https://github.com/ryandotsmith/null-buildpack
```
{: codeblock}

## 超过组织的内存限制
{: #ts_outofmemory}
{: troubleshoot}

如果您是轻量帐户用户，那么可能无法在超过组织内存限制的情况下将应用程序部署到 {{site.data.keyword.cloud_notm}}。您可以减少应用程序使用的内存，或者增加您帐户的内存配额。轻量帐户的最大内存配额为 256 MB，要增大内存配额，只能升级到计费帐户。

将应用程序部署到 {{site.data.keyword.cloud_notm}} 时，显示了以下错误消息：
{: tsSymptoms}

`失败 服务器错误，状态码：400，错误代码：100005，消息：您已超过组织的内存限制。`

当组织的剩余内存量低于您要部署的应用程序所需的内存量时，会发生此错误。轻量帐户的最大内存配额为 256 MB。
{: tsCauses}

您可以增加帐户的内存配额，或者减少应用程序使用的内存。
{: tsResolve}

  * 要增加帐户的内存配额，请将轻量帐户升级到计费帐户。有关更多信息，请参阅[升级帐户](/docs/account/index.html#upgrade-to-paygo)。
  * 要减少应用程序使用的内存，请使用 {{site.data.keyword.cloud_notm}} 控制台或 Cloud Foundry 命令行界面。

    如果使用 {{site.data.keyword.cloud_notm}} 控制台，请完成以下步骤：

    1. 在资源列表中选择您的应用程序。这将打开应用程序详细信息页面。

    2. 在运行时窗格中，可以减少应用程序的最大内存限制和/或应用程序实例数。 
	

    如果使用命令行界面，请完成以下步骤：

    1. 检查应用程序使用了多少内存：
  	  ```
	    ibmcloud cf list
	  ```
      {: codeblock}

	    `ibmcloud cf list` 命令会列出当前空间中部署的所有应用程序。还会显示每个应用程序的状态。


    2. 要减少应用程序使用的内存量，请减少应用程序实例数和/或最大内存限制：
	    ```
	    ibmcloud cf push appname -p app_path -i instance_number -m memory_limit
      ```
      {: codeblock}

    3. 重新启动应用程序以使更改生效。

## 应用程序不会自动重新启动
{: #ts_apps_not_auto_restarted}
{: troubleshoot}

当绑定到应用程序的服务停止工作时，该应用程序不会自动重新启动。

当绑定到应用程序的服务崩溃时，应用程序可能会发生如中断、异常和连接失败等问题。 {{site.data.keyword.cloud_notm}} 不会自动重新启动应用程序以从这些问题中恢复。
{: tsSymptoms}

此行为是 Cloud Foundry 故意为之。
{: tsCauses}

您可以通过在命令行界面中输入以下命令来手动重新启动应用程序：
{: tsResolve}

```
ibmcloud cf push appname -p app_path
```
{: codeblock}

此外，还可以对应用程序进行编码，以识别如中断、异常和连接失败等问题，并从这些问题中进行恢复。



<!-- begin STAGING ONLY -->

## {{site.data.keyword.cloud_notm}} Live Sync“调试”功能无法通过命令行启动
{: #ts_no_debug}
{: troubleshoot}

您使用命令行为应用程序启用了 {{site.data.keyword.cloud_notm}} Live Sync“调试”功能，但是您无法访问“调试”界面。

您通过设置 **BLUEMIX_APP_MGMT_ENABLE** 环境变量启用了应用程序的“调试”功能。但是，您无法在 `app_url/bluemix-debug/manage` 处访问“调试”用户界面。
{: tsSymptoms}

在以下几种情况下，无法启用“调试”功能：
{: tsCauses}

  * `manifest.yml` 包含命令属性时
  * 使用 **-c** 选项将应用程序推送至 {{site.data.keyword.cloud_notm}} 时

使用以下其中一个选项可解决该问题：
{: tsResolve}

  * 建议的做法是使用 IBM Node.js buildpack 启动应用程序。有关更多信息，请参阅[将 Node.js 应用程序部署至 {{site.data.keyword.cloud_notm}}](/docs/runtimes/nodejs/index.html#nodejs_runtime) 主题的“启动命令”部分。
  * 通过将 `manifest.yml` 中的 command 属性修改为 command: null，或通过编辑 push 命令以包含 `-c null`，禁用现有应用程序的命令。
  * 从 `manifest.yml` 中除去 **command** 属性。然后，从 {{site.data.keyword.cloud_notm}} 中删除当前应用程序，并重新推送应用程序。

<!-- end STAGING ONLY -->

## 在 {{site.data.keyword.cloud_notm}} 上找不到组织
{: #ts_orgs}
{: troubleshoot}

在 {{site.data.keyword.cloud_notm}} 区域上工作时，可能在 {{site.data.keyword.cloud_notm}} 上找不到组织。

您可以成功登录到 {{site.data.keyword.cloud_notm}} 控制台，但不能使用 Cloud Foundry 命令行界面来推送应用程序。
{: tsSymptoms}

尝试使用 Cloud Foundry 命令行界面将应用程序推送到 {{site.data.keyword.cloud_notm}} 时，您会看到以下某条错误消息（消息中指定了组织名称）：

`查找组织时出错`

`找不到组织`

发生此问题的原因是您要使用的区域的 API 端点未指定，并且您要查找的组织可能位于其他区域中。
{: tsCauses}

如果要使用 Cloud Foundry 命令行界面将应用程序推送到 {{site.data.keyword.cloud_notm}}，请输入 `cf api` 命令并指定区域的 API 端点。例如，输入以下命令以连接到 {{site.data.keyword.cloud_notm}} 欧洲英国区域：
{: tsResolve}

```
cf api https://api.eu-gb.cf.cloud.ibm.com
```
{: codeblock}


## 无法创建应用程序路径
{: #ts_hostistaken}
{: troubleshoot}

将应用程序部署到 {{site.data.keyword.cloud_notm}} 时，如果您所指定的主机名已在使用，那么无法创建该应用程序的路径。

将应用程序部署到 {{site.data.keyword.cloud_notm}} 时，您会看到以下错误消息：
{: tsSymptoms}

`正在创建路径 hostname.domainname ... 失败 服务器错误，状态码：400，错误代码：210003，消息：所采用的主机为：hostname`

如果您所指定的主机名已在使用，那么会发生此问题。
{: tsCauses}

您所指定的主机名在您所使用的域中必须是唯一的。要指定不同的主机名，请使用以下某个方法：
{: tsResolve}

  * 如果使用 `manifest.yml` 文件来部署应用程序，请在 host 选项中指定主机名。
    ```yaml
    host: host_name
	  ```

  * 如果从命令提示符部署应用程序，请使用带有 **-n** 选项的 `ibmcloud cf push` 命令。
    ```
    ibmcloud cf push appname -p app_path -n host_name
    ```
    {: codeblock}

## 无法使用 ibmcloud cf push 命令推送 WAR 应用程序
{: #ts_cf_war}
{: troubleshoot}

如果未正确指定应用程序位置，那么可能无法使用 `ibmcloud cf push` 命令将归档的 Web 应用程序部署到 {{site.data.keyword.cloud_notm}}。

使用 `ibmcloud cf push` 命令将 WAR 应用程序上传到 {{site.data.keyword.cloud_notm}} 时，您会看到以下错误消息：
{: tsSymptoms}
`编译打包错误：由于编译打包失败，无法获取实例。`

如果未指定 WAR 文件，或者未指定 WAR 文件的路径，那么可能会发生此问题。
{: tsCauses}

使用 **-p** 选项来指定 WAR 文件或将路径添加到 WAR 文件。例如：
{: tsResolve}

```
ibmcloud cf push MyUniqueAppName01 -p app.war
```
{: codeblock}

```
ibmcloud cf push MyUniqueAppName02 -p "./app.war"
```
{: codeblock}

有关 `ibmcloud cf push` 命令的更多信息，请输入 `ibmcloud cf push -h`。

## 将应用程序推送到 {{site.data.keyword.cloud_notm}} 时未正确显示双字节字符
{: #ts_doublebytes}
{: troubleshoot}

如果没有为 servlet 或 JSP 文件正确配置 Unicode 支持，那么可能未正确显示双字节字符。

将应用程序推送到 {{site.data.keyword.cloud_notm}} 时，未正确显示在应用程序内指定的双字节字符。
{: tsSymptoms}

如果没有为 servlet 或 JSP 文件正确配置 Unicode 支持，那么可能发生该问题。
{: tsCauses}

您可以在 servlet 或 JSP 文件内使用以下代码：
{: tsResolve}

  * 在 servlet 源文件中，
    
  ```java
	response.setContentType("text/html; charset=UTF-8");
	```
  {: codeblock}

  * 在 JSP 中
  ```jsp
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
	```
  {: codeblock}

## 无法部署 Node.js 应用程序
{: #ts_nodejs_deploy}
{: troubleshoot}

您在更新 Node.js 应用程序或将 Node.js 应用程序部署到 {{site.data.keyword.cloud_notm}} 时可能会遇到问题。

您在更新 Node.js 应用程序或将 Node.js 应用程序部署到 {{site.data.keyword.cloud_notm}} 时，可能会看到以下其中一条错误消息：
{: tsSymptoms}

`任何可用 buildpack 均未成功检测到应用程序。`

`实例（索引 0）未能开始接受连接。`

`由于编译打包失败，无法获取实例。`

可能的原因如下所示：
{: tsCauses}

  * 未指定启动命令。
  * 部署 Node.js 应用程序所需的文件在应用程序中缺失，或者位于非根目录的文件夹中。

根据问题原因，使用以下其中一种方法：
{: tsResolve}

  * 通过以下其中一种方法来指定启动命令：
     * 使用 Cloud Foundry 命令行界面。例如：
        ```
		  ibmcloud cf push MyUniqueNodejs01 -p app_path -c "node app.js"
		```
      {: codeblock}

    * 使用 [package.json ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://www.npmjs.com/package/jsonfile){: new_window} 文件。例如：
     ```json
		  {
        ...
  	    "scripts": {
	 		 "start": "node app.js"
 	   }
	}
	    ```

    * 使用 `manifest.yml` 文件。例如：
     ```
		  applications:
  name: MyUniqueNodejs01
  ...
      command: node app.js
  ...
      ```

  * 确保 Node.js 应用程序中存在 `package.json` 文件，这样 Node.js buildpack 才能识别该应用程序。确保此文件位于应用程序的根目录中。	
    以下示例显示简单的 `package.json` 文件：
	```json
	{
        "name": "MyUniqueNodejs01",
        "version": "0.0.1",
        "description": "A sample package.json file",
        "dependencies": {
                "express": "3.4.x",
                "jade": "1.1.x"
        },
        "engines": {
                "node": "0.10.x"
        },
        "scripts": {
                  "start": "node app.js"
        }
 }
    ```

有关 Node.js 应用程序的更多提示，请参阅 [Tips for Node.js Applications ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window}。

## 将 {{site.data.keyword.cloud_notm}} Liberty 应用程序导入到 Eclipse 之后，`server.xml` 文件中出现配置错误
{: #ts_eclipse}
{: troubleshoot}

在将 {{site.data.keyword.cloud_notm}} Liberty 应用程序导入到 Eclipse 之后，如果在 `server.xml` 文件中看到配置错误，那么可能需要从项目中除去 `server.xml` 文件。

在将 {{site.data.keyword.cloud_notm}} Liberty 应用程序导入到 Eclipse 之后，在 Eclipse“问题”视图中看到 `server.xml` 文件内的配置错误。
{: tsSymptoms}

将 Liberty 应用程序推送到 {{site.data.keyword.cloud_notm}} 时，Liberty buildpack 会使用 `server.xml` 文件来配置应用程序，并生成 `runtime-vars.xml` 文件。将应用程序导入到 Eclipse 时，本地环境中不存在 `runtime-vars.xml` 文件。
{: tsCauses}

您可以通过从项目中除去 server.xml 文件来解决此问题。将应用程序作为 WAR 应用程序进行推送时，buildpack 会动态创建 `server.xml` 文件。有关更多信息，请参阅 [Liberty for Java](/docs/runtimes/liberty/index.html)。
{: tsResolve}

## 使用定制 buildpack 无法编译打包应用程序
{: #ts_bp_compilation}
{: troubleshoot}

如果定制 buildpack 中的脚本不是可执行文件，那么您可能无法使用该 buildpack 将应用程序部署到 {{site.data.keyword.cloud_notm}}。

使用定制 buildpack 将应用程序部署到 {{site.data.keyword.cloud_notm}} 时，您会看到错误消息：`应用程序未能编译打包，因此没有要显示的实例。`
{: tsSymptoms}

如果脚本（如检测脚本、编译脚本和发布脚本）不可执行，那么可能发生此问题。
{: tsCauses}

您可以使用 [Git update ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](http://git-scm.com/docs/git-update-index){: new_window} 命令将每个脚本的许可权更改为可执行。例如，可以输入 `git update --chmod=+x script.sh`。
{: tsResolve}

## 无法通过 {{site.data.keyword.cloud_notm}} Continuous Delivery 中的 Delivery Pipeline 部署应用程序
{: #ts_devops_to_bm}
{: troubleshoot}

 如果应用程序中不存在 `manifest.yml` 文件，那么可能无法使用 {{site.data.keyword.contdelivery_short}} 中的 {{site.data.keyword.deliverypipeline}} 来部署应用程序。

 使用 {{site.data.keyword.contdelivery_short}} 中的 {{site.data.keyword.deliverypipeline}} 部署应用程序时，可能会显示错误消息：`检测不到支持的应用程序类型`。
 {: tsSymptoms}

 发生此问题的原因可能是管道需要使用 `manifest.yml` 文件将应用程序部署到 {{site.data.keyword.cloud_notm}}。
 {: tsCauses}

 要解决此问题，您必须创建 `manifest.yml` 文件。有关如何创建 `manifest.yml` 文件的更多信息，请参阅 [应用程序清单](/docs/manageapps/depapps.html#appmanifest)。
 {: tsResolve}

## 无法推送 Meteor 应用程序
{: #ts_meteor}
{: troubleshoot}

如果未正确指定 buildpack，那么可能无法将 Meteor 应用程序推送到 {{site.data.keyword.cloud_notm}}。

将 Meteor 应用程序部署到 {{site.data.keyword.cloud_notm}} 时，您可能会看到错误消息：`应用程序未能编译打包，因此没有要显示的实例。`
{: tsSymptoms}

发生此问题的原因是没有可用于 Meteor 应用程序的内置 buildpack。必须使用定制 buildpack。
{: tsCauses}

要对 Meteor 应用程序使用定制 buildpack，请使用以下其中一种方法：
{: tsResolve}

  * 如果使用 `manifest.yml` 文件来部署应用程序，请使用 buildpack 选项来指定定制 buildpack 的 URL 或名称。例如：
  ```yaml
buildpack: https://github.com/Sing-Li/bluemix-bp-meteor 
  ```

  * 如果从命令提示符部署应用程序，请使用 `ibmcloud cf push` 命令并通过 **-b** 选项来指定定制 buildpack。例如：
  ```
	ibmcloud cf push appname -p app_path -b https://github.com/Sing-Li/bluemix-bp-meteor
	```
  {: codeblock}

## 超过了存储配额
{: #exceed_quota}

如果构建或部署作业失败，并且看到以下消息，那么可以使用以下 CLI 命令删除映像。`状态：未授权：您已超过了存储配额。请删除一个或多个映像，或者复查存储配额和价格套餐。`

* 如果尚未安装 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html)，请进行安装。
* 使用 `ibmcloud login` 登录到 {{site.data.keyword.cloud_notm}}，并将其指向您所在的空间。
* 使用 `ibmcloud cr images` 列出映像。
* 使用 `ibmcloud cr image-rm <respository>:<tag>` 删除任何未使用的映像。
* 重新运行失败的构建或部署作业。

## 访问 Kubernetes 日志
{: #access_kube_logs}

如果应用程序未在运行，并且您无法访问该运行状况端点，请尝试查看集群中的日志。
* 如果尚未安装 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli/index.html#overview)，请进行安装。
* 使用 `ibmcloud login` 登录到 {{site.data.keyword.cloud_notm}}，并将其指向您所在的空间。
* 使用 `ibmcloud cs clusters` 列出集群。
* 使用 `ibmcloud cs cluster-config <cluster-name>` 指向相应的集群。
* 导出所列出的环境变量。
* 使用 `kubectl get pods` 查看 pod。如果需要安装 `kubectl`，请参阅[安装和设置 kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)。
* 可以使用 `kubectl logs <pod-name>` 来查看应用程序中的日志。`


## 启动 `docker` 失败，并返回“找不到文件”消息
{: #docker_not_found}
{: troubleshoot}

尝试启动 Docker 时，显示了以下错误消息：
{: tsSymptoms}

```
在构建 Docker 映像时遇到了错误：exec: "docker": 在 $PATH 中找不到可执行文件。
```
{: screen}

Docker 客户机未安装，或者已安装但未启动。
{: tsCauses}

确保 [Docker](https://docs.docker.com/install/) 已安装，并将其启动。
{: tsResolve}

  ## 构建应用程序失败，并返回 Docker 错误
{: #build_error}
{: troubleshoot}

尝试使用 `ibmcloud dev build` 命令构建应用程序时，该命令失败，并返回 Docker 用户名/密码错误。
{: tsSymptoms}

用于认证的 Docker Hub 凭证不正确。
{: tsCauses}

请在 Docker 客户机中从 Docker Hub 注销。
{: tsResolve}

  


