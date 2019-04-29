---

copyright:
  years: 2018, 2019
lastupdated: "2019-04-04"

keywords: apps, credentials, cloud foundry, environment, service, credential, vcap_services

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}

# 向 Cloud Foundry 环境添加凭证
{: #add-credentials-cf}

了解如何向 Cloud Foundry 部署环境添加服务凭证。
这些指示信息适用于 [Cloud Foundry Public](/docs/cloud-foundry-public?topic=cloud-foundry-public-about-cf) 和 [Cloud Foundry Enterprise Environment](/docs/cloud-foundry-public?topic=cloud-foundry-public-cfee)。
{: shortdesc}

缺省共享域为 `mybluemix.net`，但是，`appdomain.cloud` 是另一个可供您使用的域选项。有关迁移到 `appdomain.cloud` 的更多信息，请参阅[更新域](/docs/cloud-foundry-public?topic=cloud-foundry-public-update-domain)。
{: tip}

## 代码 + Cloud Foundry
{: #credentials-byoc-cf}

在应用程序所在的 Cloud Foundry 空间中，可以定义 Cloud Foundry 对用户提供的服务所命名的名称。用户提供的服务是字符串化 JSON，视为 Cloud Foundry 空间中的可绑定服务进行存储。您登录并连接到 Cloud Foundry 组织和空间后，请完成以下步骤来创建和绑定服务。

1. 通过运行以下命令，创建用户提供的服务：
  ```console
  cf cups customcreds -p '{"username":"Leeroy","password":"Jenkins"}'
  ```
  {: codeblock}

2. 通过将用户提供的服务添加到 services 部分，将 Cloud Foundry 应用程序配置为绑定到该服务：
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - customcreds
  ```

3. 对应用程序进行编码以读取环境变量 `VCAP_SERVICES` 的环境，将其解析为 JSON，然后找到所需的凭证（类似 node.js 的伪码）：
  ```
  // get the 'password' from "customcreds" user-provided service
  vcapServices = getEnvironment('VCAP_SERVICES');
  vcapServicesAsJSON = JSON.parse(vcapServices);
  upsArray = vcapServicesAsJSON['user-provided'];
  if (upsArray) {
      for (var i = 0, len = upsArray.length; i < len; i++) {
          if (upsArray[i].name === 'customcreds') {
              return upsArray[i].credentials.password
          }
      }
  }
  ```
{: codeblock}


## 入门模板工具包应用程序 + Cloud Foundry
{: #credentials-starterkit-cf}

### 如何准备 Cloud Foundry 空间

使用**配置持续交付**功能将应用程序部署到 Cloud Foundry 空间。

如果基于 Cloud Foundry 的服务实例与所部署的 Cloud Foundry 应用程序位于同一 Cloud Foundry 空间中，请参阅[下一部分](/docs/apps?topic=creating-apps-add-credentials-cf)。

如果基于 Cloud Foundry 的服务实例所在空间不同于 Cloud Foundry 应用程序的目标空间，请参阅[以下部分](/docs/apps?topic=creating-apps-add-credentials-cf#cf_resource_different)。

如果与应用程序关联的服务基于资源控制器，请参阅[资源控制器](/docs/apps?topic=creating-apps-add-credentials-cf#cf_resource_controller)。

#### 基于 Cloud Foundry 的服务与所部署的应用程序位于同一空间中
{: #cf_resource_same}

如果与应用程序关联的服务基于 Cloud Foundry，那么该服务在 Cloud Foundry 中“可绑定”。通过将 `cf` 命令行与正确的区域 + 组织 + 空间连接，可以在 Cloud Foundry 空间中看到该服务。创建服务时，可以判断服务是否基于 Cloud Foundry（如果系统询问您是在哪个 Cloud Foundry 组织和空间中创建服务）。

通过运行以下命令，可以查看绑定的应用程序：
```console
cf services
  ```
{: codeblock}

示例输出：
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg3-alertnotificati-1538417831070   alertnotification   authorizedusers                create succeeded
```
{: screen}

#### 基于 Cloud Foundry 的服务与所部署的应用程序位于不同空间中
{: #cf_resource_different}

Cloud Foundry 应用程序和 Cloud Foundry 服务不在同一 Cloud Foundry 空间中时，Cloud Foundry 不支持将该应用程序“绑定”到该服务。Cloud Foundry 空间必须准备好“用户提供的”服务，具体请参阅以下部分。

#### 基于资源控制器的服务与应用程序相关联
{: #cf_resource_controller}

如果与应用程序关联的服务基于资源控制器，那么该服务在 Cloud Foundry 中_不_“可绑定”。创建服务时，可以判断服务是基于资源控制器（如果系统询问您是在哪个资源组中创建服务）。Cloud Foundry 空间必须准备好服务凭证，以便应用程序可以在代码中引用这些服务凭证。这些准备工作会自动完成，您可以通过运行以下命令将 `cf` 命令行连接到空间，以观察空间准备的结果：
```console
cf services
  ```
{: codeblock}

示例输出：
```
Getting services in org test_user@us.ibm.com / space dev as test_user@us.ibm.com...

name                                   service             plan              bound apps   last operation
blarg-cloudant-1538408663553           user-provided
```
{: screen}

Cloud Foundry 不允许对 `cf service` 或 `cf services` 命令行显示任何服务凭证（已编码或其他形式的凭证）的值。在功能上，用户提供的服务是字符串化 JSON，定义为 Cloud Foundry 空间中指定名称的“服务实例”。要查看这些值，必须先通过在应用程序的 `manifest.yml` 文件的 `services` 标题下指明服务实例名称，将应用程序绑定到 Cloud Foundry 服务。然后，在 Cloud Foundry 空间中运行应用程序，并通过运行 `cf env $APP_NAME` 来获取该应用程序的环境。

幸好，通过入门模板工具包生成的代码会自动使用正确的绑定进行填充，以检索和使用在运行应用程序的 Cloud Foundry 空间中为其定义的环境中的值。

### 入门模板工具包生成的代码
{: #starterkit-generated-code-cf}

在继续操作之前，请参阅[入门模板工具包应用程序 + kube](/docs/apps?topic=creating-apps-add-credentials-kube#credentials-starterkit-kube-gencode)。然后，应用以下更改：

* 虽然生成的代码提供了 `deployment.yml`，但它不适用于部署到 Cloud Foundry 的应用程序。适用的_是_ `manifest.yml`，其内容显示为_绑定_到 Cloud Foundry 空间中创建的两个服务：
  ```yaml
  ---
  applications:
  - instances: 1
    timeout: 180
    name: Blarg3
    buildpack: sdk-for-nodejs
    command: npm start
    memory: 256MB
    domain: mybluemix.net
    host: blarg3
    services:
      - blarg3-alertnotificati-1538417831070
      - blarg-cloudant-1538408663553
  ```
  {: codeblock}

文档中先前子部分中的其余内容同样适用。`IBMCloudEnv` 库会对从运行应用程序的环境中检索到的值进行抽象化处理。

从 Cloud Foundry 中检索环境值时，该库会对部分复杂性进行抽象化处理。在 Cloud Foundry 中，会为运行中应用程序提供一个名为 `VCAP_SERVICES` 的环境变量，其值为字符串化 JSON，保存有绑定服务凭证的值，不管该服务是_位于_ Cloud Foundry 空间中的服务实例还是用户定义的服务值。`VCAP_SERVICES` 环境变量中已解析 JSON 中的顶级键是与基于 Cloud Foundry 的服务关联的 Cloud Foundry `label`，键 `user-provided` 的值用于保存所有“用户提供的”服务的凭证数组。
