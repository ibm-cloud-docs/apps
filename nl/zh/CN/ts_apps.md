---

copyright:
  years: 2015, 2019
lastupdated: "2019-06-17"

keywords: apps, application, troubleshooting, debug apps, known issues, debug, help, configuration, app, troubleshoot, error, errors, failure, failed, fail, issues, applications

subcollection: creating-apps

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

## 我的应用程序在不同域中托管
{: #domains-ts}
{: troubleshoot}

我的某些应用程序在 `mybluemix.net` 域中托管，其他应用程序在 `appdomain.cloud` 域中托管。

我的现有应用程序在 `mybluemix.net` 域中托管，而较新的应用程序在 `appdomain.cloud` 域中托管。
{: tsSymptoms}

在 cloud.ibm.com 上提供了新的主机名选项 `*.appdomain.cloud`。

先前，`mybluemix.net` 域用于在多个部署目标（例如，{{site.data.keyword.containerlong_notm}} 或 Cloud Foundry）中托管应用程序。在 `mybluemix.net` 上托管的任何应用程序不会受影响。

Cloud Foundry 应用程序的子域为 `cf.appdomain.cloud`。部署到 {{site.data.keyword.containerlong_notm}} 的应用程序的子域为 `containers.appdomain.cloud`。

有关更多信息，请参阅[管理域](/docs/apps?topic=creating-apps-update-domain)。

## 您有未保存的更改
{: #ts_unsaved_changes}
{: troubleshoot}

在应用程序详细信息页面上单击项时，可能无法执行任何操作。系统还可能会提示您保存更改后才能继续。

在应用程序详细信息页面上尝试检查应用程序或服务时，显示了以下错误消息：
{: tsSymptoms}

`您有未保存的更改。确定要离开此页面吗？`

在运行时窗格中的**实例**或**内存配额**字段上滚动鼠标时，值会更改。这是故意设计的行为。但是，当您要转至其他页面时，系统会提示您保存内存或实例设置。
{: tsCauses}

关闭消息窗口，然后单击运行时窗格中的**重置**。
{: tsResolve}

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

有关其他程序语言中可以使用的命令的更多信息，请参阅 [Java ](https://docs.run.pivotal.io/buildpacks/java/java-tips.html#env-var){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 和 [Ruby ](https://docs.run.pivotal.io/buildpacks/ruby/ruby-tips.html#env-var){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")。


## 收到 502 无效网关错误
{: #ts_502_error}
{: troubleshoot}

如果在与 {{site.data.keyword.cloud_notm}} 上的应用程序进行交互时收到 `502 无效网关`错误，请检查 {{site.data.keyword.cloud_notm}} 状态页面，然后采取相应的措施。

您收到以“502 无效网关”开头的错误消息。例如，您可能会看到 `502 无效网关：注册的端点未能处理请求。`
{: tsSymptoms}

通常会在以下情况下发生“无效网关”错误：您转至某个 Web 站点，该站点使用代理服务器来存储和中继来自托管该站点的主服务器中的数据。主服务器和代理服务器之间可能未正确连接。因此，您会在浏览器窗口中看到 HTTP 状态码 502。此状态码指示该站点的主服务器未收到本该从代理服务器发来的 HTTP 实现。
{: tsCauses}

其他导致“无效网关”错误的不太常见的原因包括：因特网服务提供商 (ISP) 信息遗失、防火墙配置错误以及浏览器高速缓存错误。

如果您怀疑 {{site.data.keyword.cloud_notm}} 服务已关闭，请先检查 [{{site.data.keyword.cloud_notm}} 状态 ](https://cloud.ibm.com/status){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 页面。变通方法可能是[在其他 {{site.data.keyword.cloud_notm}} 区域中使用该服务](/docs/resources/connect_external_app?topic=resources-externalapp){: new_window}。如果服务状态正常，请尝试执行以下步骤来解决问题： 
{: tsResolve}

  * 重试操作：
    * 通过按键盘上的 F5 或单击**刷新**，重新装入页面。如果此步骤无效，请清除浏览器的高速缓存和 cookie，然后再重新装入。

    * 使用其他浏览器。
    * 重新启动您的路由器、调制解调器和计算机。重新引导这些设备可以清理导致 502 错误的各种错误。

  * 稍等，然后重试。您的因特网服务提供商或 {{site.data.keyword.cloud_notm}} 服务可能发生了临时问题。您可以一直等到临时问题得到解决为止。

  * 如果问题持续存在，请联系 {{site.data.keyword.cloud_notm}} 支持。有关更多信息，请参阅[联系 {{site.data.keyword.cloud_notm}} 支持 ](/docs/get-support?topic=get-support-getting-customer-support){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")。

## Android 应用程序收不到 {{site.data.keyword.mobilepushshort}}
{: #ts_push}
{: troubleshoot}

在无法访问 Google 的某些地区，Android 应用程序收不到您通过 IBM {{site.data.keyword.mobilepushshort}} 服务发送出来的通知。在这种情况下，变通方法是使用第三方服务。

为 {{site.data.keyword.cloud_notm}} 应用程序绑定 {{site.data.keyword.mobilepushshort}} 服务，并将消息发送给已注册的设备。但是，在某些区域，Android 上开发的应用程序收不到您的通知。
{: tsSymptoms}

IBM {{site.data.keyword.mobilepushshort}} 服务使用 Google 云消息传递 (GCM) 服务将通知分派到在 Android 上开发的移动应用程序。要使 Android 应用程序能够接收通知，移动应用程序必须可以访问 Google 云消息传递 (GCM) 服务。在 Android 应用程序无法访问 GCM 服务的区域中，Android 应用程序收不到 {{site.data.keyword.mobilepushshort}}。
{: tsCauses}

作为变通方法，请使用不依赖于 GCM 服务的第三方服务，例如 [Pushy](https://pushy.me/){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 和 [jpush](https://www.jiguang.cn/en/){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")。
{: tsResolve}

## 将应用程序推送到 {{site.data.keyword.cloud_notm}} 时未正确显示双字节字符
{: #ts_doublebytes}
{: troubleshoot}

如果没有为 servlet 或 JSP 文件正确配置 Unicode 支持，那么可能未正确显示双字节字符。

将应用程序推送到 {{site.data.keyword.cloud_notm}} 时，未正确显示应用程序内指定的双字节字符。
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

    * 使用 [package.json ](https://www.npmjs.com/package/jsonfile){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 文件。例如：
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

有关 Node.js 应用程序的更多提示，请参阅 [Tips for Node.js Applications ](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")。

## 将 {{site.data.keyword.cloud_notm}} Liberty 应用程序导入到 Eclipse 之后，`server.xml` 文件中出现配置错误
{: #ts_eclipse}
{: troubleshoot}

在将 {{site.data.keyword.cloud_notm}} Liberty 应用程序导入到 Eclipse 之后，如果在 `server.xml` 文件中看到配置错误，那么可能需要从项目中除去 `server.xml` 文件。

在将 {{site.data.keyword.cloud_notm}} Liberty 应用程序导入到 Eclipse 之后，在 Eclipse“问题”视图中看到 `server.xml` 文件内的配置错误。
{: tsSymptoms}

将 Liberty 应用程序推送到 {{site.data.keyword.cloud_notm}} 时，Liberty buildpack 会使用 `server.xml` 文件来配置应用程序，并生成 `runtime-vars.xml` 文件。将应用程序导入到 Eclipse 时，本地环境中不存在 `runtime-vars.xml` 文件。
{: tsCauses}

您可以通过从项目中除去 server.xml 文件来解决此问题。将应用程序作为 WAR 应用程序进行推送时，buildpack 会动态创建 `server.xml` 文件。有关更多信息，请参阅 [Liberty for Java](/docs/runtimes/liberty?topic=liberty-liberty_runtime#liberty_runtime)。
{: tsResolve}

## 使用定制 buildpack 无法编译打包应用程序
{: #ts_bp_compilation}
{: troubleshoot}

如果定制 buildpack 中的脚本不是可执行文件，那么您可能无法使用该 buildpack 将应用程序部署到 {{site.data.keyword.cloud_notm}}。

使用定制 buildpack 将应用程序部署到 {{site.data.keyword.cloud_notm}} 时，您会看到错误消息：`应用程序未能编译打包，因此没有要显示的实例。`
{: tsSymptoms}

如果脚本（如检测脚本、编译脚本和发布脚本）不可执行，那么可能发生此问题。
{: tsCauses}

您可以使用 [Git update ](https://git-scm.com/docs/git-update-index){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 命令将每个脚本的许可权更改为可执行。例如，可以输入 `git update --chmod=+x script.sh`。
{: tsResolve}

## 无法通过 {{site.data.keyword.cloud_notm}} Continuous Delivery 中的 Delivery Pipeline 部署应用程序
{: #ts_devops_to_bm}
{: troubleshoot}

 如果应用程序中不存在 `manifest.yml` 文件，那么可能无法使用 {{site.data.keyword.contdelivery_short}} 中的 {{site.data.keyword.deliverypipeline}} 来部署应用程序。

 使用 {{site.data.keyword.contdelivery_short}} 中的 {{site.data.keyword.deliverypipeline}} 部署应用程序时，可能会显示错误消息：`检测不到支持的应用程序类型`。
 {: tsSymptoms}

 发生此问题的原因可能是管道需要使用 `manifest.yml` 文件将应用程序部署到 {{site.data.keyword.cloud_notm}}。
 {: tsCauses}

 要解决此问题，您必须创建 `manifest.yml` 文件。有关如何创建 `manifest.yml` 文件的更多信息，请参阅 [应用程序清单](/docs/cloud-foundry?topic=cloud-foundry-deploy_apps#appmanifest)。
 {: tsResolve}

## 超过了存储配额
{: #exceed_quota}

如果构建或部署作业失败，并且看到以下消息，那么可以使用以下 CLI 命令删除映像。`状态：未授权：您已超过了存储配额。请删除一个或多个映像，或者复查存储配额和价格套餐。`

* 如果尚未安装 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started)，请进行安装。
* 使用 `ibmcloud login` 登录到 {{site.data.keyword.cloud_notm}}，并将其指向您所在的空间。
* 使用 `ibmcloud cr images` 列出映像。
* 使用 `ibmcloud cr image-rm <respository>:<tag>` 删除任何未使用的映像。
* 重新运行失败的构建或部署作业。

## 访问 Kubernetes 日志
{: #access_kube_logs}

如果应用程序未在运行，并且您无法访问该运行状况端点，请尝试查看集群中的日志。
* 如果尚未安装 [{{site.data.keyword.cloud_notm}} CLI](/docs/cli?topic=cloud-cli-getting-started)，请进行安装。
* 使用 `ibmcloud login` 登录到 {{site.data.keyword.cloud_notm}}，并将其指向您所在的空间。
* 使用 `ibmcloud cs clusters` 列出集群。
* 使用 `ibmcloud cs cluster-config <cluster-name>` 指向您的相应集群。
* 导出所列出的环境变量。
* 使用 `kubectl get pods` 查看 pod。如果需要安装 `kubectl`，请参阅 [Install and set up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")。
* 可以使用 `kubectl logs <pod-name>` 来查看应用程序中的日志。

## 启动 `docker` 失败，并返回找不到文件的消息
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

确保 [Docker](https://docs.docker.com/install/){: new_window} ![外部链接图标](../icons/launch-glyph.svg "外部链接图标") 已安装并将其启动。
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
