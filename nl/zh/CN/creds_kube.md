---

copyright:
  years: 2018
lastupdated: "2018-11-14"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}

# 向 Kubernetes 环境添加凭证
{: #add_credentials}

了解如何向 Kubernetes 部署环境添加服务凭证。
{: shortdesc}

在以下场景中，必须以手动方式将服务凭证添加到部署环境：
 * 自带代码。
 * 从空白入门模板工具包模板开始。
 * 在部署了服务_之后_，将其添加到基于入门模板工具包的应用程序。

## 代码 + Kubernetes
{: #byoc_kube}

<!-- (Refer to the ["Code it Right"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#code-it-right) and ["Prepare the Environment"](https://github.ibm.com/arf/planning-codegen/wiki/TEMP:-BYOC-UX-Docs#prepare-the-environment) sections.  But translate a bit so we're only mentioning editing a `deployment.yml` file, not the "deployment.yml section of the script in the Deploy pipeline stage configuration".) -->

### 正确编码

作为预防措施，您可以对应用程序进行编码，以确认其环境在应用程序的主入口点中已完成。您不希望将应用程序升级到环境未完成的集群中，从而导致对您的产品造成中断。应用程序可能会拒绝启动，并且 Kubernetes 配置可以自动防止此类中断。

假定您有以下两个环境变量：
* `SECRET`
* `NOT_SECRET`

对于数据库，变量可能是 `APIKEY` 和 `DB_URL`，前者是敏感变量，后者则不是。

使用 Java 时，您可能希望在主应用程序入口点编写某些内容，例如：
```java
if (System.getenv("SECRET") == null) {
    throw new RuntimeException("Environment variable 'SECRET' is not set!");
}
// and many more checks...
```
{: codeblock}

使用 Node 时，请参阅类似的示例：
```js
if (!process.env.SECRET) {
    console.error('ENVIRONMENT variable "SECRET" is not set!');
    process.exit(1);
}
// and many more checks...
```
{: codeblock}

### 准备环境

在 Kubernetes 的 `deployment.yml` 文件中，可以定义环境变量或_对集群中私钥的引用_。

#### 设置部署以从环境中获取凭证

在包含 `kind: Deployment` 的部分中，在缩进级别将以下示例代码添加到 `spec.template.spec.containers` 之后：
```yaml
env:
  - name: SECRET
    valueFrom:
      secretKeyRef:
          name: name-secret
          key: KEY_SECRET
  - name: NOT_SECRET
    value: "I'm not a secret"
```
{: codeblock}

* 单击**保存**。

配置集群，以使名称为 `name-secret` 且密钥为 `KEY_SECRET` 的 _secretKeyRef_ 解析为值。

#### 安装必备工具

使用工作站上的终端来安装以下工具：

1. 安装 [{{site.data.keyword.dev_cli_long}} CLI](/docs/cli/index.html)。
2. 使用 `ibmcloud login` 命令登录。
3. 通过运行 `ibmcloud cs cluster-config {your_cluster_name}` 来连接到集群。
4. 复制并粘贴 `export` 命令以从终端运行此命令。

#### 定义集群中的私钥

{{site.data.keyword.dev_cli_notm}} 提供了 `kubectl`，您可以运行此命令，因为您已连接到 Kubernetes 集群。

要定义可解析的私钥，请使用以下 `kubectl` 命令：
```console
echo -n 'This is the secret.  Shhhhh!' > ./KEY_SECRET
```
{: codeblock}

```console
kubectl create secret generic name-secret --from-file=./KEY_SECRET
```
{: codeblock}

既然 Kubernetes 集群已准备好可解析的私钥，那么可以更新应用程序以使用在 `deployment.yml` 文件中定义的环境变量。

## 入门模板工具包应用程序 + Kubernetes
{: #sk_kube}

1. 转至应用程序的**应用程序详细信息**页面。
2. 要创建 Cloud Object Storage 的实例，请选择**添加资源** > **存储器** > **Cloud Object Storage** > **轻量套餐（免费）** > **创建**。
3. 单击`下载代码`以使用注入的代码片段重新生成项目。
4. 要在本地访问凭证，请将新生成的 `.zip` 文件中的以下文件复制到本地 Git 克隆以进行替换，从而访问凭证。您仍必须在集群中创建 Kubernetes 私钥以托管凭证。

	- `chart/{appName}/bindings.yaml` - 在 Kubernetes 集群中生成指向私钥的环境变量。
	- `src/main/resources/localdev-config.json` - 在本地运行应用程序时访问凭证。
  - `src/main/resources/mappings.json` - 一种映射，用于提供对 [`env.getProperty()`](/docs/java-spring/configuration.html#configuration#accessing-credentials) 方法的访问，以通过代码访问环境变量。
  - `manifest.yml` - 此文件将服务绑定到 Cloud Foundry 应用程序。

如果您日后选择使用资源控制器资源（位于资源组中，而不是位于组织或空间中）部署到 Cloud Foundry 应用程序，那么必须复制上述一个或多个文件。
{: note}

5. [查看](https://cloud.ibm.com/containers-kubernetes/clusters) Kubernetes 集群和相应的区域（US-South，如果是免费的）。
6. 单击集群，然后选择右上角的 **Kubernetes 仪表板**以查看集群仪表板。
7. 向下滚动，直至看到标记为**私钥**的部分。您会看到使用约定 `binding-{appName}-{serviceName}-{timestamp}` 的 {{site.data.keyword.cloudant_short_notm}} 服务实例的私钥。在 `chart/{appName}/bindings.yaml` 文件中，您可以找到相应的 {{site.data.keyword.cloudant_short_notm}} 私钥。
8. 现在，可以使用 `chart/{appName}/bindings.yaml` 中已生成的私钥名称，为 Cloud Object Storage 实例创建相应的私钥，类似于 `binding-create-app-ktibr-cloudobjectstor-1538170732311`。
9. 转至仪表板中的**应用程序详细信息**页面，然后复制 Cloud Object Storage 实例的凭证。请参阅以下示例凭证输出：
```yaml
{
  "apikey": "hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg",
  "endpoints": "https://cos-service.bluemix.net/endpoints",
  "resource_instance_id": "crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"
}    
```
{: codeblock}

10. 确保使用 `ibmcloud cs cluster-config {your_cluster_name}` 配置了集群，并在随后的指令中导出此命令。
11. 使用 `echo` 命令将凭证放入 `binding` 文件中。
  ```console
  echo -n '{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://cos-service.bluemix.net/endpoints","resource_instance_id":"crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}' > ./binding

  ```
  {: codeblock}

12. 使用 `kubectl create secret generic binding-create-app-ktibr-cloudobjectstor-15381707323113 --from-file=./binding` 创建私钥。如果返回到 Kubernetes 集群仪表板，那么可以看到您创建的私钥。

如果要部署到 Cloud Foundry 应用程序并且使用的是资源控制器实例（如果资源位于资源组中，而不位于组织或空间中），那么您需要创建用户提供的服务。
{: note}
  
  ```console
  ibmcloud cf create-user-provided-service create-app-ktibr-cloudobjectstor-1538170732311 -p `{"name":"create-app-ktibr-cloudobjectstor-1538170732311","credentials":{"apikey":"hVi9lXHeMwvDCv7k8mOcl8h0JgqBujv8h9qHGuNl9bNg","endpoints":"https://cos-service.bluemix.net/endpoints","resource_instance_id":"crn:v1:bluemix:public:cloud-object-storage:global:a/144a947078143141bf66d9e93a2c257e:36467673-5cf2-4299-81ee-fc22ec04743a::"}}`
  ```
  {: codeblock}

  可以使用相应的实例名称在 `manifest.yml` 文件中找到用户提供的服务的名称。

13. 现在，应用程序在 Kubernetes 集群中运行时，您可以通过 `env.getProperty` 方法利用环境变量来访问自己的私钥。

### 如何准备 Kubernetes 集群

使用**部署到云**功能将应用程序部署到 IBM Containers Kubernetes 集群。该功能会为 Kubernetes 集群准备与应用程序关联的资源的凭证。您可以通过完成以下步骤来观察集群准备的结果：

1. 运行以下命令以查看结果：`kubectl get secrets`：
  ```
  NAME                                   TYPE                                  DATA      AGE
  binding-blarg-cloudant-1538408663553   Opaque                                1         13m
  bluemix-default-secret                 kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-international   kubernetes.io/dockerconfigjson        1         17d
  bluemix-default-secret-regional        kubernetes.io/dockerconfigjson        1         17d
  default-token-xfd5n                    kubernetes.io/service-account-token   3         17d
  ```
  {: screen}

  您可以查看[关于私钥的更多文档](https://kubernetes.io/docs/concepts/configuration/secret/)。
  {: tip}

2. 请注意，私钥的名称是资源名称。
3. 使用 `kubectl get secret binding-blarg-cloudant-1538408663553 -o=yaml` 来查看有关私钥的详细信息：

  ```
  apiVersion: v1
  data:
    binding: eyJhcGlrZXkiOiI4RFprT3VMVnduVkExWW1HODFnazNQMjZOeThlNWFWbjVhaFpZLVVEOHQ1NCIsImhvc3QiOiI1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJpYW1fYXBpa2V5X2Rlc2NyaXB0aW9uIjoiQXV0byBnZW5lcmF0ZWQgYXBpa2V5IGR1cmluZyByZXNvdXJjZS1rZXkgb3BlcmF0aW9uIGZvciBJbnN0YW5jZSAtIGNybjp2MTpibHVlbWl4OnB1YmxpYzpjbG91ZGFudG5vc3FsZGI6dXMtc291dGg6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzpiZmEzNDJkZC00YjZmLTRkZmUtYTM1YS05MTA4ZmIwZWM1NzE6OiIsImlhbV9hcGlrZXlfbmFtZSI6ImF1dG8tZ2VuZXJhdGVkLWFwaWtleS01MzI3ZWMxZC0wOWE1LTQyMzctOTczNS03ZTAxZmU3NDFiYzciLCJpYW1fcm9sZV9jcm4iOiJjcm46djE6Ymx1ZW1peDpwdWJsaWM6aWFtOjo6OnNlcnZpY2VSb2xlOldyaXRlciIsImlhbV9zZXJ2aWNlaWRfY3JuIjoiY3JuOnYxOmJsdWVtaXg6cHVibGljOmlhbS1pZGVudGl0eTo6YS80ODBmZDFlYzE0YWM1NDBjNWJjMzdkYTc5OWE2MzQzNzo6c2VydmljZWlkOlNlcnZpY2VJZC1mNWRhMjMwYy1kNDE0LTQ4NTQtYjE1Yi00MmJmZmRhYWVmNWIiLCJwYXNzd29yZCI6ImY4MjU2ZDJhODYyMjI5NzViZDI3Mjc1MjEzMTY4YTQyNzBhNDZmMmEyOGQ5NDkyMjRhYzFjOTc3NjMwMWNlZTYiLCJwb3J0Ijo0NDMsInVybCI6Imh0dHBzOi8vNTlhYTdiMWEtNWFhYi00ZjJkLTlhNzMtOGMzYjI5NDA4Zjk2LWJsdWVtaXg6ZjgyNTZkMmE4NjIyMjk3NWJkMjcyNzUyMTMxNjhhNDI3MGE0NmYyYTI4ZDk0OTIyNGFjMWM5Nzc2MzAxY2VlNkA1OWFhN2IxYS01YWFiLTRmMmQtOWE3My04YzNiMjk0MDhmOTYtYmx1ZW1peC5jbG91ZGFudC5jb20iLCJ1c2VybmFtZSI6IjU5YWE3YjFhLTVhYWItNGYyZC05YTczLThjM2IyOTQwOGY5Ni1ibHVlbWl4In0=
  kind: Secret
  metadata:
    annotations:
      service-instance-id: 'crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::'
      service-key-id: 5327ec1d-09a5-4237-9735-7e01fe741bc7
    creationTimestamp: 2018-10-01T15:45:02Z
    name: binding-blarg-cloudant-1538408663553
    namespace: default
    resourceVersion: "155591"
    selfLink: /api/v1/namespaces/default/secrets/binding-blarg-cloudant-1538408663553
    uid: f5e7885c-c590-11e8-ad83-8e37f3f3216f
  type: Opaque
  ```
  {: screen}

  `binding` 是私钥的 Base64 编码值。对其解码后会发现，这只是资源实例的 `credentials` 中的原始 JSON 以及一些 `iam_...` 值：
  ```
  {
    "apikey": "8DZkOuLVwnVA1YmG81gk3P26Ny8e5aVn5ahZY-UD8t54",
    "host": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "iam_apikey_description": "Auto generated apikey during resource-key operation for Instance - crn:v1:bluemix:public:cloudantnosqldb:us-south:a/480fd1ec14ac540c5bc37da799a63437:bfa342dd-4b6f-4dfe-a35a-9108fb0ec571::",
    "iam_apikey_name": "auto-generated-apikey-5327ec1d-09a5-4237-9735-7e01fe741bc7",
    "iam_role_crn": "crn:v1:bluemix:public:iam::::serviceRole:Writer",
    "iam_serviceid_crn": "crn:v1:bluemix:public:iam-identity::a/480fd1ec14ac540c5bc37da799a63437::serviceid:ServiceId-f5da230c-d414-4854-b15b-42bffdaaef5b",
    "password": "f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6",
    "port": 443,
    "url": "https://59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix:f8256d2a86222975bd27275213168a4270a46f2a28d949224ac1c9776301cee6@59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix.cloudant.com",
    "username": "59aa7b1a-5aab-4f2d-9a73-8c3b29408f96-bluemix"
  }
  ```
  {: screen}

除非 `deployment.yml` 声明了引用私钥的 `env` 值，否则应用程序代码无法检索 Kubernetes 私钥。使用入门模板工具包时，会自动生成此类代码。

### 入门模板工具包生成的代码
{: #sk_kube_generated_code}

在本例中，您是通过入门模板工具包创建的此应用程序。对于通过入门模板工具包生成的代码，可使其具有可移植性，能在本地、Cloud Foundry 或 Kubernetes 中运行。`IBMCloudEnv` 库用于在应用程序代码与检索环境变量之间提供抽象层；环境变量用于保存资源（服务实例）的凭证。

通过入门模板工具包创建的代码具有 `IBMCloudEnv` 库的依赖关系，并会生成以下输出：

* `bindings.yml` 文件，以内联方式包含在 `deployment.yml` 文件中，具有以下内容：
  ```yaml
   - name: service_cloudant
     valueFrom:
     secretKeyRef:
        name: binding-blarg-cloudant-1538408663553
        key: binding
        optional: true
  ```
  {: codeblock}

  `secretKeyRef.name` 将可由应用程序检索的已定义 Kubernetes 私钥作为应用程序代码中的简单环境变量公开。

* `IBMCloudEnv` 库的指示信息封装在 `mappings.json` 文件中，该文件位于入门模板工具包生成的代码库中。`mappings.json` 对于每个凭证都有单独的定义：
  ```json
  "cloudant_apikey": {
    "searchPatterns": [
      "user-provided:blarg-cloudant-1538408663553:apikey",
      "cloudfoundry:$['cloudant'][0].credentials.apikey",
      "env:service_cloudant:$.apikey",
      "env:cloudant_apikey",
      "file:/server/localdev-config.json:$.cloudant_apikey"
    ]
  },
  ```
  {: codeblock}

  `mappings.json` 文件使用 `jsonpath` 语法和 `searchPatterns` 数组顺序来指导 `IBMCloudEnv` 逻辑。

* 使用以下代码来检索 Cloudant API 密钥（伪码）：
  ```java
  cloudantApiKey = IBMCloudEnv.getValue('cloudant_apikey');
  ```
  {: codeblock}

`IBMCloudEnv` 库会自动检测应用程序是在 Kubernetes 中、Cloud Foundry 中还是在虚拟服务器实例（视为与本地 Docker 相同）中运行，并应用正确的 `searchPattern` 来查找要返回的值。

因此，`mappings.json` 文件将被视为包含预配置值和立即可用值的_最终列表_，这些值来自应用程序要在其中运行的环境。使用**部署到云**功能时，会在您设定为目标的集群的环境中填充这些值。

**注意**：截至编写本文档时，对于与应用程序关联的所有资源的所有凭证，会_始终_执行环境准备，但_并非所有 `env` 引用_都会放在 `bindings.yml` 文件或 `mappings.json` 文件中。在这些情况下，您必须自行放入此类引用。如果您已经决定了目标部署，并且不需要 `IBMCloudEnv` 库的抽象，请参阅与您的决策相适应的“代码 +（目标部署）”部分。

某些入门模板工具包根本不包含对 `IBMCloudEnv` 依赖关系、`manifest.yml` 或 `mappings.json` 文件的引用。
{: note}
