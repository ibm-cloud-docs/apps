---

copyright:
  years: 2018, 2019
lastupdated: "2019-03-29"

keywords: apps, credentials, service, add service credentials, environment, deployment

subcollection: creating-apps

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:important: .important}

# 凭证概述
{: #credentials_overview}

了解如何向部署环境手动添加服务凭证。
{: shortdesc}

<!-- After PUP: Maybe provide links to the credentials section of the programming guides, such as https://cloud.ibm.com/docs/swift/cloudnative/configuration.html#configuration-->

通常，您希望应用程序逻辑可从运行应用程序的环境中获取敏感服务凭证，例如数据库 API 密钥或密码。这样，您就不用将凭证保存在源代码存储库中。持续集成环境、预生产环境和生产环境中的数据库彼此隔离。

如果使用入门模板工具包模板创建应用程序，那么将自动为您准备环境，无论您的部署目标是下列哪一项：
  * [Kubernetes](/docs/apps?topic=creating-apps-add-credentials-kube)
  * [Cloud Foundry Public 或 Cloud Foundry Enterprise Environment](/docs/apps?topic=creating-apps-add-credentials-cf)
  * [虚拟服务器实例（也是本地 Docker）](/docs/apps?topic=creating-apps-add-credentials-vsi)
  
提供了有关如何配置环境的步骤。入门模板工具包会生成使用依赖库的代码，以使代码具有可移植性，能在任何部署目标上运行。最后，没有任何分支逻辑用于检测应用程序正在哪个部署目标中运行。

接下来，管理员或 DevOps 工程师负责为环境准备相应的访问控制和配置，使应用程序所需的值可用。

“配置持续交付”是一个一次性步骤，可执行以下关键任务：
 * 为部署目标准备服务、资源和凭证。
 * 使用正确引用环境中凭证的代码，创建 DevOps 工具链以构建应用程序并将其部署到该环境中。

但是，在以下任一场景中，必须准备部署目标：
 * 自带代码。
 * 从空白入门模板工具包模板开始。
 * 在部署了服务之后，将其添加到基于入门模板工具包的应用程序。

对于与应用程序关联的所有服务的所有凭证，会始终执行环境准备，并且所有 `services` 都会列在 `manifest.yml` 中，但并非所有凭证引用都会放在 `mappings.json` 文件中。在这些情况下，您需要自行放入此类引用。决定部署目标后，并且不需要 `IBMCloudEnv` 库的抽象化处理时，请参阅与您的决策相适应的“代码 +（部署目标）”部分。
{: important}

某些入门模板工具包根本不包含对 `IBMCloudEnv` 依赖关系、`manifest.yml` 或 `mappings.json` 文件的引用。
{: important}
